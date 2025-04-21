### pgloader Docker Image for ARM64

This project addresses the absence of official arm64 Docker images by providing a dedicated image for the arm64 architecture. This image is built using official files to ensure compatibility and reliability.

[![Build Status](https://travis-ci.org/dimitri/pgloader.svg?branch=master)](https://travis-ci.org/dimitri/pgloader)
[![Join the chat at https://gitter.im/dimitri/pgloader](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/dimitri/pgloader?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Read The Docs Status](https://readthedocs.org/projects/pgloader/badge/?version=latest&style=plastic)](http://pgloader.readthedocs.io/en/latest/)

#### Overview



> Source files: [https://github.com/dimitri/pgloader](https://github.com/dimitri/pgloader)


#### Image Information

*   **Image Name:** `ghcr.io/notagshen/pgloader-arm64:latest`
*   **Base Image:** `ubuntu-24.04-arm`
*   **Included Components:** Contains all necessary dependencies required for seamless execution on ARM64-based systems.

#### Usage

Our goal is to deliver an ARM64 image that mirrors the official x86_64 version in functionality. You can deploy this image just as you would the standard release.

*   **Command-line Installation:**

    ```bash
    docker pull ghcr.io/notagshen/pgloader-arm64:latest
    docker run --rm -it ghcr.io/notagshen/pgloader-arm64:latest pgloader --version
    ```
*   **Dockerfile Integration:**

    ```dockerfile
    FROM ghcr.io/notagshen/pgloader-arm64:latest
    ```

#### Acquiring the Image

##### Downloading Pre-built Images

We have been consistently compiling pre-built ARM64 images. You can find the complete range of versions on the GitHub Container Registry.



## PGLoader Usage Instructions

pgloader is a data loading tool for PostgreSQL, using the `COPY` command.

Its main advantage over just using `COPY` or `\copy`, 和 over using a
*Foreign Data Wrapper*, is its transaction behaviour, where *pgloader*
will keep a separate file of rejected data, but continue trying to
`copy` good data in your database.

The default PostgreSQL behaviour is transactional, which means that
*any* erroneous line in the input data (file or remote database) will
stop the entire bulk load for the table.

pgloader also implements data reformatting, a typical example of that
being the transformation of MySQL datestamps `0000-00-00` and
`0000-00-00 00:00:00` to PostgreSQL `NULL` value (because our calendar
never had a *year zero*).

## Documentation

Full documentation is available online, including manual pages of all the
pgloader sub-commands. Check out
[https://pgloader.readthedocs.io/](https://pgloader.readthedocs.io/en/latest/)。

```
$ docker run --rm -it ghcr.io/notagshen/pgloader-arm64:latest pgloader --help
pgloader [ option ... ] SOURCE TARGET
  --help -h                       boolean  Show usage and exit.
  --version -V                    boolean  Displays pgloader version and exit.
  --quiet -q                      boolean  Be quiet
  --verbose -v                    boolean  Be verbose
  --debug -d                      boolean  Display debug level information.
  --client-min-messages           string   Filter logs seen at the console (default: "warning")
  --log-min-messages              string   Filter logs seen in the logfile (default: "notice")
  --summary -S                    string   Filename where to copy the summary
  --root-dir -D                   string   Output root directory. (default: #P"/tmp/pgloader/")
  --upgrade-config -U             boolean  Output the command(s) corresponding to .conf file for v2.x
  --list-encodings -E             boolean  List pgloader known encodings and exit.
  --logfile -L                    string   Filename where to send the logs.
  --load-lisp-file -l             string   Read user code from files
  --dry-run                       boolean  Only check database connections, don't load anything.
  --on-error-stop                 boolean  Refrain from handling errors properly.
  --no-ssl-cert-verification      boolean  Instruct OpenSSL to bypass verifying certificates.
  --context -C                    string   Command Context Variables
  --with                          string   Load options
  --set                           string   PostgreSQL options
  --field                         string   Source file fields specification
  --cast                          string   Specific cast rules
  --type                          string   Force input source type
  --encoding                      string   Source expected encoding
  --before                        string   SQL script to run before loading the data
  --after                         string   SQL script to run after loading the data
  --self-upgrade                  string   Path to pgloader newer sources
  --regress                       boolean  Drive regression testing
```

## Usage

 see the
[pgloader quick start](https://pgloader.readthedocs.io/en/latest/tutorial/tutorial.html#pgloader-quick-start) 
<https://pgloader.readthedocs.io> for more details.
