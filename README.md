install-node-npm-etc
====================

Notes for myself to ease the install process.

You can download the binary and copy it over to a location that makes sense on your OS. These instructions walk through compiling from source and installing npm properly, so your modules get installed in userspace instead of using ```sudo``` in front of your npm install commands.

These instructions assume a linux based operating system, specifcally Ubuntu and using bash in the terminal.

## Doing It

[download the latest tarball from nodejs.org](http://nodejs.org/)


```
sudo apt-get install git-core curl build-essential openssl libssl-dev
cd $HOME
mkdir build && cd $_
wget http://nodejs.org/dist/v0.10.28/node-v0.10.28.tar.gz
tar xzvf node-v0.10.28.tar.gz
cd node-v0.10.28
./configure
make
sudo make install
cd ..
```

Check to see node is installed properly:

```
node -v
```

Now install npm:

```
wget http://npmjs.org/install.sh
sudo sh install.sh
```

Check to see npm was installed properly:

```
npm -v
```

This part is important because it will allow the npm packages to install in user space:

```
echo prefix = ~/.node >> ~/.npmrc
export PATH="$PATH":~/.node/bin
```

Now try to install an npm package, yoeman's pretty cool:

```
npm install -g yo
```

Now you should be ready to go!


## Generating a Website with yo

Lets start with the [generator-angular-fullstack](https://www.npmjs.org/package/generator-angular-fullstack)

```npm install -g generator-angular-fullstack```

Create the site:

```
mkdir $HOME/yo-sites && cd $_
mkdir my-new-project && cd $_
yo angular-fullstack sweet-site
```

Say no to all the options for this test.

After it generates, run it:

```
grunt serve
```
