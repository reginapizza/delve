# Installation on Linux

Please use the following steps to build and install Delve on Linux.

There are two ways to install on Linux. 

First is the standard `go get` method:

```
go get github.com/go-delve/delve/cmd/dlv
```

Note: if you are using Go in modules mode you must execute this command outside of a module directory or Delve will be added to your project as a dependency.

Alternatively make sure $GOPATH is set (e.g. as `~/.go`) and:

```
$ git clone https://github.com/go-delve/delve.git $GOPATH/src/github.com/go-delve/delve
$ cd $GOPATH/src/github.com/go-delve/delve
$ make install
```

Ensure that `dlv` is running correctly with: 
```
dlv version
```

Note: After trying these methods and running `dlv version`, if you get an error saying `bash: dlv: command not found...`, try these additional steps:

1. `cd $GOPATH/bin`
2. `ls -a` (you should see that `dlv` executable is not present in files)
3. `cd $GOPATH/src/github.com/go-delve/delve`
4. `make install`
    
    The output for this should be:
    ```
    go install "-ldflags=-X main.Build=328cf87808822693dc611591519689dcd42696a3" github.com/go-delve/delve/cmd/dlv
    ```
5. `make build`
6. `ls -a` (now you should see `dlv` executable in files)
7. (from the `/delve` folder) `sudo cp dlv /usr/local/bin`
8. `dlv version`
    
    Your final, expected output will be:
    ```
    Delve Debugger
    Version: 1.5.0
    Build: 328cf87808822693dc611591519689dcd42696a3
    ```
    Now you're ready to start debugging!
