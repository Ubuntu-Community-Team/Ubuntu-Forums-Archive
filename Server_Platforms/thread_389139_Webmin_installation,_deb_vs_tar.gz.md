---
title: "Webmin installation, deb vs tar.gz"
date: 2007-03-20
forum: Server Platforms
---

### Post by hotani on 2007-03-20
I went to the [webmin download](http://www.webmin.com/download.html) page and found there was a .deb file. After downloading and running it, the instructions said to go to localhost:10000 and log in. But it wasn't running. I tried http, https, messed with the firewall, opened ports (although this is all local so it shouldn't matter), no effect. 

Then I decided to try and find out if it was actually running:
ps -ef | grep web

and nothing. So I tried to figure out how to start it. There are *hundreds* of files and directories in at least 2 separate webmin locations. 

So I downloaded the tar.gz, unpacked, ran setup.sh and was using webmin in under a minute. 

Just FYI.

---

### Post by Aberrix on 2007-03-20
did you try to access webin locally? or remotely?

locally you'd use localhost:10000

remotely you'd use 192.168.0.1:10000 (or whatever the ip of the box is)

---

### Post by hotani on 2007-03-20
yes, I was local--but the process was not running. The .deb never started it. Rather than spend an hour finding out why, or figure out where the start/stop command lived, I ran the "manual" install which started it all up as expected. After that, I went to localhost:10000 and was greeted by the webmin login screen. At which point I could not log in, but that is [a different problem](http://ubuntuforums.org/showthread.php?p=2081627)...

---

### Post by Brazen on 2007-03-20
I use the deb to install Webmin and it has always started fine, but I have not used it on Edgy.  Only Ubuntu Dapper, Debian Sarge, and Debian Etch.  Never had a problem.

---

### Post by curuxz on 2007-03-21
The deb method is far faster, i suspect you have made a rather simple mistake. 

When you install the deb file it often installs but does not work because of dependancies, if you click on the deb file then after it installs go into synaptic and click fix broken packages then apply it should will be working 100% by far the quickest way to do it and I should know I use webmin on multiple production servers for the last 4-5 years and have installed it loads of times this always happens.

Just FYCI

---

### Post by Brazen on 2007-03-21
> **curuxz said:**
> The deb method is far faster, i suspect you have made a rather simple mistake. 

When you install the deb file it often installs but does not work because of dependancies, if you click on the deb file then after it installs go into synaptic and click fix broken packages then apply it should will be working 100% by far the quickest way to do it and I should know I use webmin on multiple production servers for the last 4-5 years and have installed it loads of times this always happens.

Just FYCI

I thought about that too, but webmin will not give the "installation complete, browse to [https://localhost:10000](https://localhost:10000) blah blah blah" message until the dependencies are met.

---

### Post by hotani on 2007-03-21
If I was intent on doing things via the GUI (usually I am), then hunting for broken packages after installing a .deb that *appeared* to install successfully would be the way to go. But in this case the setup.sh script from the tar.gz package handled everything lickety split and left me with a working, running webmin. This was on Edgy, BTW. 

As an aside, I have installed webmin on Dapper and Edgy in the past but this was the first time I ran into the 'unable-to-login' issue. I think the previous installs asked me for a password during the install process where this time it did not. This was remedied after running the fix in the thread linked above, but I'm not sure why I had the problem this time and not in the past.

---

### Post by benanzo on 2007-03-25
I've never had trouble installing webmin using the deb, until now.  I've recently installed it on a couple Edgy machines with no problems.  But then I got hold of Feisty Herd 5 and had the same problem described here.  The deb *seemed* to install fine but after it told me to go to [https://localhost:10000](https://localhost:10000) to log in, I couldn't, it wasn't running.

So I did ```
sudo /etc/init.d/webmin restart
``` only to find that the script didn't exist.  I reinstalled a few times with no luck.  So I uninstalled and downloaded the tar.gz. I ran the setup.sh and installed it to /opt/webmin_1.330 which worked wonderfully.  However, for the life of me I cannot get webmin to start at boot.  The init.d script is there and executing it after boot works, but it will not start at boot time.  Any ideas?  Thanks.

---

