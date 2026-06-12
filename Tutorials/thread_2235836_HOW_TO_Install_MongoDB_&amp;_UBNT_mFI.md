---
title: "HOW TO: Install MongoDB &amp; UBNT mFI"
date: 2014-07-23
forum: Tutorials
---

### Post by Gareth_2007 on 2014-07-23
Before you start login as root

```
sudo su
```

Step 1: Add APT Repository

First import public key of 10gen repository in our system

```
$ apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
```

Lets add 10 gen MongoDB APT repository url in /etc/apt/sources.list.d/mongodb.list.

```
$ echo 'deb [http://downloads-distro.mongodb.org/repo/ubuntu-upstart](http://downloads-distro.mongodb.org/repo/ubuntu-upstart) dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list
```

After adding required APT repositories, use following commands to install MongoDB in your systems. It will also install all dependent packages required for mongodb.

```
$ apt-get update
```
```
$ apt-get install mongodb-org
```

Step 3: Start/Stop MongoDB Service

Start/Stop MongoDB using Init script. Below are the example commands to do it.

```
# service mongod stop
```
```
# service mongod start
```

Step 4: Verify MongoDB Installation

Use following command to check installed mongodb version

$ ```
mongo --version

```
Step 5: Initialise and test the database

$ ```
mongod
```

MongoDB shell version: 2.6.3
Connect MongoDB using command line and execute some test commands for checking proper working.

```
$ mongo
```
```
> db.test.save( { admintest: 100 } )
```
```
> db.test.find()
```

```
  { "_id" : ObjectId("52b0dc8285f8a8071cbb5daf"), "admintest" : 100 }
```

Step 6: Install of the mFI Controller

You'll need to add the repo to the sources list

```
$ nano /etc/apt/sources.list
```

Scroll to the bottom and add the following line

```
deb http://www.ubnt.com/downloads/mfi/distros/deb/ubuntu ubuntu ubiquiti
```

Step 7: add GPG Key

```
 apt-key adv --keyserver keyserver.ubuntu.com --recv C0A52C50
```


Step 8: Install mFI Controller

Update packet list:

```
$ apt-get update

```

Install:

```
$ apt-get install mfi
```


Step 8: Test

The mFi webUI can be reached via the local machines ip address  [https://192.168.1.10:6443/](https://192.168.1.10:6443/)

Change the ip to match your machine.

---

### Post by Vagelism_Meintasis on 2015-05-23
When I type [COLOR=#000000][FONT=Ubuntu Mono]mongo
I got the following error.
[/FONT][/COLOR]MongoDB shell version: 2.4.9
connecting to: test
Sat May 23 22:52:21.026 Error: couldn't connect to server 127.0.0.1:27017 at src/mongo/shell/mongo.js:145
exception: connect failed

---

### Post by fredrikwe on 2015-05-30
mFi failed to install due to two packes "damaged":
mongodb-10gen and mongodb-server

How to proceed?

---

