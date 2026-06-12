---
title: "Help installing XBMC"
date: 2012-02-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by slayner117 on 2012-02-08
I followed the small tutorial here: [http://www.noobslab.com/2011/12/install-xbmc-on-ubuntu-1204-precise.html](http://www.noobslab.com/2011/12/install-xbmc-on-ubuntu-1204-precise.html)

And when I get down to the third code it comes with the error. E: Unable to locate package xbmc

Any help would be much appreciated.

---

### Post by grahammechanical on 2012-02-08
First of all, open Update Manager and click on Settings. Then go to the Other Software tab and see if this is listed as a ppa

> [http://ppa:nathan-renniewaldock/xbmc-stable](http://ppa:nathan-renniewaldock/xbmc-stable)

The third instruction or command is telling the apt-get utility to go to the web server at [http://ppa:nathan-renniewaldock/xbmc-stable](http://ppa:nathan-renniewaldock/xbmc-stable) and downlaod and install XBMC. The error message is telling you that the apt-get utility cannot find XBMC. Now why is this?

Did you type the first command correctly? That is what we need to find out. Is that ppa part of your Software Sources?

There could be another reason for the failure. That link might be incorrect. Check this out. Yes, I know that it is in German but you might be downloading a beta version. do you want to do that?

[http://www.loggn.de/ubuntu-xbmc-repository-10-1-dharma-und-11-0-eden-mit-und-ohne-pvr/]("http://www.loggn.de/ubuntu-xbmc-repository-10-1-dharma-und-11-0-eden-mit-und-ohne-pvr/")

You might be better off using this

> sudo add-apt-repository ppa:nathan-renniewaldock/xbmc-old-stable



Regards.

---

### Post by slayner117 on 2012-02-08
When I look at my 'Other software' in my software sources through the update manager. I see four different PPA's these are the PPA's 

[http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu](http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu)
[http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu](http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu)
[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu)
[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu)


Those are exactly how they are - directly copied and pasted. 

On a side note, if you watch the video that is on my original link. That is exactly what I did, except when I get to sudo apt-get install xbmc I get the E: Unable to locate package xbmc

---

### Post by effenberg0x0 on 2012-02-08
> **slayner117 said:**
> When I look at my 'Other software' in my software sources through the update manager. I see four different PPA's these are the PPA's 

[http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu](http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu)
[http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu](http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu)
[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu)
[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu)


Those are exactly how they are - directly copied and pasted. 

On a side note, if you watch the video that is on my original link. That is exactly what I did, except when I get to sudo apt-get install xbmc I get the E: Unable to locate package xbmc

It's not your fault: The package is not there. See for yourself.
```
$ sudo add-apt-repository ppa:nathan-renniewaldock/xbmc-stable
[sudo] password for ahsl: 
You are about to add the following PPA to your system:
 Stable releases of XBMC.
 More info: https://launchpad.net/~nathan-renniewaldock/+archive/xbmc-stable
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.0WydbFcn8J --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 428926204FE30238F00B98224CDB129629A4B41A
gpg: requesting key 29A4B41A from hkp server keyserver.ubuntu.com
gpg: key 29A4B41A: public key "Launchpad PPA for Nathan Rennie-Waldock" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

[01:06 AM][ahsl:AL-DESK:~]
$ sudo apt-get update
[Lots of updating repos cut out]
$ sudo apt-get install xbmc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xbmc
$ sudo cat /etc/apt/sources.list.d/nathan-renniewaldock-xbmc-stable-precise.list 
deb http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu precise main
deb-src http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu precise main
wget http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu/dists/precise/main/binary-i386/Packages -O /tmp/test.test && grep -i "xbmc" /tmp/test.test
```Or just open [http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu/dists/precise/main/binary-i386/Packages) in your browser.


Why? Simple: Go to [https://launchpad.net/~nathan-renniewaldock/+archive/xbmc-stable/+packages]("https://launchpad.net/%7Enathan-renniewaldock/+archive/xbmc-stable/+packages") and scroll down. You'll see that the Precise branch of XBMC in this PPA failed to build for i386 and amd64.

When this happens, the developer receives an email from Launchpad and will look at the compiler logs to see what happened, fix it (missing headers/libs, typos or errors in code, etc) and once the code compiles OK again it will be available in there.

So the only thing you can do is wait and eventually run sudo apt-get update && sudo apt-get install xbmc or visit that Launchpad page to see if it built correctly.

Regards,
Effenberg

---

### Post by cariboo on 2012-02-08
I'd suggest using this ppa:

[https://launchpad.net/~team-xbmc/+archive/unstable](https://launchpad.net/~team-xbmc/+archive/unstable)

the packages are about the latest you can get. Even though the ppa is labelled unstable, I've been using it with zero problems.

---

### Post by papibe on 2012-02-08
> **cariboo907 said:**
> I'd suggest using this ppa:

[https://launchpad.net/~team-xbmc/+archive/unstable](https://launchpad.net/~team-xbmc/+archive/unstable)

the packages are about the latest you can get. Even though the ppa is labelled unstable, I've been using it with zero problems.

+1

The version on that ppa is a [beta 2]("http://xbmc.org/natethomas/2012/01/22/xbmc-11-0-eden-beta-2-available-now/"). I've been also using it without any problem.

Regards.

---

### Post by slayner117 on 2012-02-08
> **cariboo907 said:**
> I'd suggest using this ppa:

[https://launchpad.net/~team-xbmc/+archive/unstable](https://launchpad.net/~team-xbmc/+archive/unstable)

the packages are about the latest you can get. Even though the ppa is labelled unstable, I've been using it with zero problems.

I don't mean to sound like such a beginner, But I am pretty sure I did this without fault. I added the ppa exactly how it was up there 
ppa:team-xbmc/unstable then ran sudo apt-get update and finally sudo apt-get install xbmc and the same thing is happening. Is there anything I am doing wrong here?

---

### Post by slayner117 on 2012-02-08
effenberg0x0


I may wind up doing that. At least I wasn't severely messing up. Thank you for the help.

---

### Post by papibe on 2012-02-08
I just realize that the unstable ppa does not contain a version for Precise. You can use the trick on post #2 of this [thread]("http://ubuntuforums.org/showthread.php?t=1766855&highlight=xbmc") (changing the repository names accordingly) to install it from that ppa.

Hope it helps.
Regards.

---

### Post by cariboo on 2012-02-08
One thing to check is to open software sources in either the software center, or synaptic, and make sure you have the distribution set to oneiric, instead of precise.

Even using the apt-add-repository command, you may have to change it to oneiric. in /etc/apt/sources.list.d/team-xbmc-unstable-precise.list

---

### Post by slayner117 on 2012-02-08
sudo apt-get install xbmc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xbmc : Depends: xbmc-bin (>= 2:11.0~git20120207.1fef727-0ubuntu1~ppa1~maverick) but it is not going to be installed
        Depends: xbmc-bin (< 2:11.0~git20120207.1fef727-0ubuntu1~ppa1~maverick.1~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by slayner117 on 2012-02-08
It doesn't seem to be working by using that solution either. I'm not in any huge hurry I don't mind waiting, considering it is in the alpha. If anyone can get this to work, I would appreciate it though. 

And thank you everyone for your help so far.

---

### Post by papibe on 2012-02-08
In your case you need to change it to 'precise' not maverick.
Regards.

---

### Post by slayner117 on 2012-02-08
I actually tried (in this order) 

Precise 
Natty
Maverick


At post #11 the same happened using Natty. 

But when I use precise it still comes up as unable to locate package.

---

### Post by effenberg0x0 on 2012-02-08
**_[COLOR=Red][It is not there. It failed to build.]("http://ubuntuforums.org/showpost.php?p=11674647&postcount=4")[/COLOR]_**
Once it is fixed and built, you will be able to download it, without making any change to the added ppa or anything else in your system.

---

### Post by slayner117 on 2012-02-09
I have tried the stable and unstable, and a few different tutorials. I don't mean to sound like such an amateur on this chances are I am doing something very simple wrong. 

I do appreciate all the help, if anyone can walk me through step by step or at least Private message me when it is actually working I would greatly appreciate it.

---

### Post by cariboo on 2012-02-09
Until last night I've never had a problem installing XBMC, I perviuosly used the official [wiki ]("http://wiki.xbmc.org/?title=XBMC_Online_Manual")for installation instructions, instead of relying on other random sites.

---

