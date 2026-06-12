---
title: "Transmission SVN script!"
date: 2007-12-28
forum: The Cafe
---

### Post by Sockerdrickan on 2007-12-28
:popcorn:Enjoy

```
#!bin/sh
cd

echo "\nThis script will download & compile Transmission to your home dir.\n"
echo -n "Downloading latest Transmission trunk..."
svn -q co svn://svn.m0k.org/Transmission/trunk transmission-svn
echo " Done"

cd transmission-svn
sh autogen.sh
./configure -q
make -s

echo -n "\nMoving binary to /home/`whoami` and removing svn dir..."
mv gtk/transmission ../transmission
cd
rm -rf transmission-svn
echo " Done"

echo "\nTransmission has been built from SVN. Have a nice day `whoami`."
```

[SIZE="4"]NOTE: The script doesn't install libs needed if you havn't got those. The reason is because this will only have to be done one time. Not each time you want a new transmission binary.[/SIZE]

---

### Post by cwej on 2007-12-29
Thanks, but what does "Transmission" do, please?

---

### Post by Sockerdrickan on 2007-12-29
The best bittorrent client, if you ask me ;) MUCH better than the one that comes with Ubuntu

---

### Post by John.Michael.Kane on 2007-12-29
> **cwej said:**
> Thanks, but what does "Transmission" do, please?

Transmission is a lightweight BitTorrent client, It is one of many bittorrent programs available for linux. 

Some others include
BitTornado
Deluge
KTorrent
rTorrent

---

### Post by Sockerdrickan on 2007-12-31
No one else found this useful? :( :lolflag:

---

### Post by smartboyathome on 2007-12-31
I may find a use for it someday, but right now I am happy with the one that comes with Opera.

---

### Post by Perci on 2008-01-01
Tux0r,

That script looks great and I've been searching for a way to install transmission on ubuntu edgy 6.10.  Could you please tell me if your script will work well on edgy?  I'm a bit stuck.  What do I save this transmission.sh script to and how can I do that?  After I save transmission.sh to something, then do I type: 

sudo ./transmission.sh

and that's it?    

I'm a bit confused because I also saw another example of a shell script in which someone advised that it be run like:

$  chmod 777 checksplash.sh
then fire the script
$ ./checksplash

But in this case, can you confirm that I don't need the chmod 777 line?
Since I am using 6.10 (edgy), I believe that I am using the dash shell.  Is this a dash or bash script and how can I use it using dash?

And after the script runs and transmission is installed, can I find transmission in my home folder (from "places" at the top menu)?

Since I'm on edgy, do I have to worry about dependency problems when running this?

Thanks in advance for helping me out.  I just installed ubuntu a few days ago but I'll be reading more linux books in the future.

-perci

---

### Post by Laterix on 2008-01-01
Thanks for the script! Transmission is a good bittorrent client.

---

### Post by Sockerdrickan on 2008-01-01
> **Perci said:**
> 
transmission.sh to something, then do I type: 

sudo ./transmission.sh

and that's it?

You can save it anywhere and start it in a terminal with sh transmission.sh
When it is done you will have a transmission binary file in your home dir!

This script doesn't install libs that you may need, so watch where it stops if it fails.

---

### Post by Perci on 2008-01-01
I saved transmission.sh to a folder in my home folder.
Then I opened terminal:

user1@user1-desktop:~$ sh transmission.sh
sh: Can't open transmission.sh
user1@user1-desktop:~$ sudo ./transmission.sh
Password:
sudo: ./transmission.sh: command not found
user1@user1-desktop:~$ sudo sh transmission.sh
sh: Can't open transmission.sh
user1@user1-desktop:~$ 

I don't understand why I'm not able to execute this script.
Please help?

Thanks,
Perci

---

### Post by Perci on 2008-01-01
TuxOr,

I think I'm good when it comes to dependencies b/c I got this from
[http://www.transmissionbt.com/development.php](http://www.transmissionbt.com/development.php)

#  GTK

    * A version of the `getopt' library with getopt_long(). Most systems already have this.
    * intltool 0.23 or later
    * gettext 0.14.1 or later
    * OpenSSL 0.9.8 or later. (See note)
    * GTK+ 2.6 or later. (See note)
    * Note: if installing OpenSSL or GTK+ from a package manager, you'll also need to install their corresponding development packages. These are usually named $PACKAGENAME-devel or $PACKAGENAME-dev, depending on which distribution and/or repository you use.

I used this command to check each item:
dpkg -l | grep gettext

All were good except
When typing:
dpkg -l | grep getopt
nothing happened.  It just skipped down to another prompt.  But I figure I probably have that one since I had the others (at later versions).

So if you could let me know how to execute the script I think I'll be cool.

---

### Post by Sockerdrickan on 2008-01-02
chmod +x transmission.sh
sh transmission.sh

---

### Post by Perci on 2008-01-02
I still get an error message when trying to run the script:

user1@user1-desktop:~$ sh transmission.sh
sh: Can't open transmission.sh
user1@user1-desktop:~$ chmod +x transmission.sh
chmod: cannot access `transmission.sh': No such file or directory
user1@user1-desktop:~$

Help, I'm failing at life!

---

### Post by rabid9797 on 2008-01-02
im sorry, maybe im missing something here. whats the point of downloading and compiling this if its already in the repos? :confused:

---

### Post by Perci on 2008-01-02
I switched to Xubuntu 7.04 feisty and I still can't get the script to run.

TuxOr,
I tried your last commands in Xubuntu 7.04 and it doesn't run.
I'm sorry to bother you, but could you please help me out a bit more?

Thanks.

---

### Post by Perci on 2008-01-02
Rabid9797,

user1@user1-desktop:~$ aptitude show transmission
Package: transmission
State: not installed
Version: 0.91.dfsg-1~feisty1
Priority: optional
Section: net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 53.2k
Depends: transmission-cli (>= 0.91.dfsg-1~feisty1), transmission-gtk (>=
         0.91.dfsg-1~feisty1)
Description: free, lightweight BitTorrent client
 Transmission is a simple BitTorrent client. It features a very simple,
 intuitive interface (gui and command-line) on top on an efficient,
 cross-platform back-end. 
 
 Homepage: [http://transmission.m0k.org/](http://transmission.m0k.org/)

user1@user1-desktop:~$

Only a really old version appears to be in the repos and I heard the latest versions are great

---

### Post by Sockerdrickan on 2008-01-02
You have to make sure you have set the script up like this: right click the sh file choose properties then rights and check allow this to be run as a program now you can sh transmission.sh if you are in the right dir.

---

### Post by Perci on 2008-01-02
OK, I did what you said and checked off "allow this file to be run as a program."  So that's good.  But in terminal, I still get the same error messages I just got.  But I noticed that in the file manager on the desktop I had another option by right-clicking the file like I did to get to permissions and there is an execute command when I right click the file.  But I get this error message from clicking execute:

Failed to execute "transmission.sh".

Failed to execute child process "home/user1/Apps_temp/transmission.sh" (No such file or directory).

That's weird.  user1 is just my account I created when installing xubuntu and Apps_temp is just a folder I created in home to store this script.

Also, this is what my permissions tab in the transmission.sh properties thing looks like:

Owner:  namelater (user1)
Access:  read & write

Group:  user1
Access:  read only

Others:  read only

Program:  and here I checked to allow it to run as a program

For all the access options I can choose: read & write, read only, write only, or none

---

### Post by Sockerdrickan on 2008-01-03
Hm ok looks like you have problems. Here is the latest SVN compiled as a binary only for you, Hope things work out!

Transmission from SVN 0.96+ (BUILD 4435) compiled for Ubuntu 7.04 or later.

---

### Post by Perci on 2008-01-04
Thanks, man!

---

### Post by swoll1980 on 2008-01-04
why ./n ?

---

