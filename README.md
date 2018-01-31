# Building Instructions

The Dockerfile here will build the experiment from the repository, along with
a simple test task. This image is also an automated build on [Docker Hub](https://hub.docker.com/r/vanessa/rstudio-neuro/)
if you don't want to build locally (it takes a bit of time!).

```
git clone https://www.github.com/vsoch/rstudio-neuro
cd rstudio-neuro
docker build -t vanessa/rstudio-neuro .
```

Don't forget the `.` at the end! It means the present working directory. And the image knows WHAT'S UP.

```
...
Removing intermediate container 8d4fef74f7ea
Step 36/36 : RUN cat /hello.txt
 ---> Running in d33b4e507d04

  ____       _     _                _    _       _        _____ _______        ___ 
 |  _ \ ___ | | __| |_ __ __ _  ___| | _| | __ _| |__    |  ___|_   _\ \      / / |
 | |_) / _ \| |/ _` | '__/ _` |/ __| |/ / |/ _` | '_ \   | |_    | |  \ \ /\ / /| |
 |  __/ (_) | | (_| | | | (_| | (__|   <| | (_| | |_) |  |  _|   | |   \ V  V / |_|
 |_|   \___/|_|\__,_|_|  \__,_|\___|_|\_\_|\__,_|_.__( ) |_|     |_|    \_/\_/  (_)
                                                     |/                            
 ---> 3a874bc1da02
Removing intermediate container d33b4e507d04
Successfully built 3a874bc1da02
Successfully tagged vanessa/rstudio-neuro:latest
```

# Running

The image `vanessa/rstudio-neuro` can be run as follows. In the example, we want to mount the directory where data has been downloaded (`/data`) to a directory on our host, and we want to expose port `8787` where rstudio server is running.

```
# Without mounting the data folder
docker run -p 8787:8787 vanessa/rstudio-neuro

# Mounting the data folder
docker run -v $PWD:/data -p 8787:8787 vanessa/rstudio-neuro
```

Then visit [http://localhost:8787](http://localhost:8787) in your browser. You need to login with:

 - username: rstudio
 - password: rstudio
