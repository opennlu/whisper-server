# Whisper Server

Whisper Server is a package designed to deploy and utilize the Whisper speech recognition model efficiently. Whisper is a versatile speech recognition model trained on a vast and diverse dataset of audio samples. It boasts the capability to handle various tasks such as multilingual speech recognition, speech translation, and language identification simultaneously.

## Features

- **State-of-the-Art Speech Recognition**: Whisper utilizes advanced machine learning techniques to provide accurate and reliable speech recognition.
- **Multilingual Support**: With its multitasking capabilities, Whisper can recognize speech in multiple languages.
- **Speech Translation**: Whisper can translate recognized speech into different languages, facilitating communication across linguistic barriers.
- **Language Identification**: Identify the language of the spoken input accurately, enabling dynamic language switching.

## Installation

To install Whisper Server, follow these steps:

1. Clone the repository from GitHub:

```bash
git clone https://github.com/opennlu/whisper-server.git
```

2. Navigate to the directory:

```bash
cd whisper-server
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

## Usage

To start Whisper Server from the command line, execute the following command:

```bash
python whisper_server.py
```

## API Documentation

### Process Audio File

Endpoint: `POST http://localhost:28466/whisper`

This endpoint allows users to submit an audio file for processing. The audio file should be sent as form-data in the request body.

Request Parameters:

- `file`: The audio file to be processed. Required.
- `language`: The returning language to be used. Optional.

```
curl -X POST \
  -F "file=@/path/to/your/audio/file.mp3" \
  http://localhost:28466/whisper
```

## Docker

> [!CAUTION]  
> This is experimental, as it will always pull the model files when using `docker run`, as there is still no volume mount.

### CPU only

```
docker run -d -p 28466:28466 opennlu/whisper-server
```

### Nvidia GPU

1. Install the [Nvidia container toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#installation).
2. Run Whisper Server inside a Docker container

```
docker run -d --gpus=all -p 28466:28466 opennlu/whisper-server
```

## Contribution

Contributions to Whisper Server are welcome! If you find any bugs or have suggestions for improvements, please open an issue or submit a pull request on GitHub.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- The Whisper team for developing and open-sourcing this powerful speech recognition model.
- Contributors who help improve and maintain Whisper Server.
