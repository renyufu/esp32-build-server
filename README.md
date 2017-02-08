# esp32-build-server
A esp32 build server docker image.

# Usage

```
sudo docker run -d --name espbuild -it -v /path/to/your/project:/proj -e TOKEN=yourtoken -e CMDS="make,make all,make app" -p 8080:80 renyufu/espbuild

sudo docker run -d --name espbuild -it -v /path/to/your/project:/proj -v /path/esp:/esp -e TOKEN=yourtoken -e CMDS="make,make all,make app" -p 8080:80 renyufu/espbuild
```

# Get started

1. clone repo
  ```
  cd
  git clone https://github.com/espressif/esp-idf.git
  ```
  
2. run esp32 build server
  ```
  sudo docker run -d --name espbuild -it -v /path/to/esp-idf/examples/get-started/hello_world:/proj -e TOKEN=yourtoken -e CMDS="make,make all,make app" -p 8080:80 renyufu/espbuild
  ```

3. request to build
  ```
  curl -s -k -H 'Content-Type: application/json' -H 'X-Auth-Token: yourtoken' -d '{"command": "make"}' https://localhost:8080/execute
  ```

4. get bin
  ```
  curl -s -k -H 'X-Auth-Token: yourtoken' https://localhost:8080/build/hello-world.bin -o hello-world.bin
  ```
