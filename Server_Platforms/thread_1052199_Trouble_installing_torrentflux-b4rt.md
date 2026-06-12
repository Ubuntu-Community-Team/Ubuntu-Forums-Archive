---
title: "Trouble installing torrentflux-b4rt"
date: 2009-01-27
forum: Server Platforms
---

### Post by nault31 on 2009-01-27
I hate to start a new thread but searching here and google hasn't helped.

I installed torrentflux 2.4 logged in via ssh from my laptop last night and all is well, but it is not up to my standards so I thought I'd try torrentflux-b4rt

I am installing according to this thread:
[http://ubuntuforums.org/showthread.php?t=848138]("http://ubuntuforums.org/showthread.php?t=848138")

I get to the part that says "let that churn away for a bit then run setup.php from a web browser of your choice from the torrentflux/html folder." and I am having trouble.  The local ip to my server is 192.168.1.115, I run firefox from my laptop and I cannot get the syntax correct.  I have tried "http://192.168.1.115/var/www/torrentflux/html/setup.php", "http://192.168.1.115/torrentflux/setup.php" "http://192.168.1.115/setup.php" and many other variants to try to run setup.php but I'm obviously guessing.  Any suggestions?

---

### Post by redroad55 on 2009-01-28
Hi try this threads
[https://help.ubuntu.com/8.04/serverguide/C/php5.html]("https://help.ubuntu.com/8.04/serverguide/C/php5.html")

---

### Post by nault31 on 2009-01-29
Thanks but it didn't help, php5 is installed ok but I don't know how to log in from my browser,


I logged on via ssh, cd to the torrentflux/html folder and ran "php setup.php" and it seemed to start the script because it shows 

"<p>Welcome to the installation script for torrentflux-b4rt. In the following pages you will be guided through the steps necessary to get your 
installation of torrentflux-b4rt up and running, including database configuration and initial torrentflux-b4rt system configuration file creation.</p>"

but nothing else happens.

---

### Post by nault31 on 2009-01-30
So I have it working.

I went back to where I was by removing and reinstalling LAMP (to clear the databases as well), and I essentially followed this guide:

[http://tech-newbie.blogspot.com/2008/05/installing-torrentflux-b4rt-on.html](http://tech-newbie.blogspot.com/2008/05/installing-torrentflux-b4rt-on.html)

The only difference is that when it logged in ([http://my](http://my) server ip/torrentflux/), I had to click on the /html folder to start the setup script so I have a feeling something is wrong there but at least I have it up and running.

---

### Post by kustomjs on 2009-01-30
you need the root document something like this: var/www/torrentflux/html  or something on that line.

---

### Post by Zillion on 2009-02-01
I have these 3 errors :

1. **transmissioncli** : Executable is not TorrentFlux-bundled transmissioncli  

Does someone have this file for me for Transmission 1.42 (I think)

2. **cksfv** : Path is not valid

It is not in the repository. What to do??

3. **VLC** : Path is not valid

I did apt-get install VLC but still this error??


I run Ubuntu server without X

thanks!!

---

### Post by Badjaccur on 2009-02-27
1. You don't need transmission. Without it you can still use TF.

2. In *ubuntu ckfv was replaced by cfv. Install it by doing ```
sudo apt-get install cfv
```
Do ```
whereis cfv
``` 
to find that the path to cfv is /usr/bin/cfv 

3. Do 
```
whereis vlc
```
to find that the path to vlc is /usr/bin/vlc

Succes! ;)

---

