# Greyscale Image Processor (Sketch Generator)

This repository takes an image as input and outputs a greyscale "sketch" of the image. It provides a web-based HTML endpoint for easy testing.

## Features
- Upload an image via the web interface or API.
- Converts the image to a greyscale sketch.
- Downloads processed images as a ZIP file.
- Gpu docker container setup
- PreFlask endpoint setup

# Architecture
![Alt text](assets/1.png)
![Alt text](assets/2.Flask-endpoint png)

# Flask-endpoint API Endpoints

## 1. `/` (GET)
- **Description**: Serves the homepage.
- **Response**: Renders `index.html`.

---

## 2. `/process` (POST)
- **Description**: Accepts an image file, processes it, and returns a URL to download the resulting `.zip` file.
- **Request**:
  - **Method**: `POST`
  - **Content-Type**: `multipart/form-data`
  - **Body**: 
    - **Key**: `image`
    - **Value**: An image file (e.g., `.jpg`, `.png`).

- **Response**:
  - **Success (200)**:
    ```json
    {
      "zip_file_url": "/download/<generated-zip-file-name>.zip"
    }

## Source
This repository is a clone of [https://github.com/Chanuku/semi_ref2sketch_code](https://github.com/Chanuku/semi_ref2sketch_code).


## How to Run

### 1. Clone the Repository
```bash
git clone <repository-url>
cd <repository-name>

# Set Up a Python Environment
Run Docker Container:
- pip install -r requirements.txt
- docker build -t img2skch .
- docker run --gpus all -p 5000:5000 -it img2skch
