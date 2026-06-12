---
title: "How do I download and ubuntu iso remotely via putty"
date: 2011-03-27
forum: Server Platforms
---

### Post by kodb on 2011-03-27
Thanks in advance as I have been searching for the last hour to try to find a solution.

I am trying to download ubuntu 10.04.02 desktop iso to my work server.  The work server is a 10.04.02 and I am logging in from home via ssh (pUtty).  I can login and access the command line and do whatever I need to do.  I can't seem to find the combination of ftp command and site to allow me to download the image to the server so I can proceed with installing Lucid on some of the work clients.  I'd rather the iso download directly to the work server vs downloading here and burning a cd to take back to the office with me.

Thanks for any direction as I am still working on learning to be more facile with the cli on the servers.

Bob

---

### Post by jramshu on 2011-03-27
I'm still learning too. Change to the directory you want to download it to, then this.

```
sudo wget http://releases.ubuntu.com/lucid/ubuntu-10.04.2-alternate-i386.iso
```

I would see what some others say before doing what I say though.:P:P

---

### Post by R.Bucky on 2011-03-27
try not to use sudo for a simple wget command. otherwise, you are golden

---

### Post by jramshu on 2011-03-27
> **R.Bucky said:**
> try not to use sudo for a simple wget command. otherwise, you are golden

I'm still learning when to and when not to use sudo, help me out a little. 

Thanks R. Bucky

---

### Post by Dark_Stang on 2011-03-27
> **jramshu said:**
> I'm still learning when to and when not to use sudo, help me out a little. 

Thanks R. Bucky

Sudo is only used when you need root access for something.
Downloading a file to your home directory - no sudo.
Downloading a file to /etc or another non-home directory - yes sudo.
Installing software for the system - yes sudo.
Starting a service - yes sudo.
Running a piece of user software (firefox) - no sudo.
Running a piece of system software (Synaptic) - yes sudo.

---

### Post by jramshu on 2011-03-28
Thanks, much appreciated. I have a lot of reading to do. I am like an addict when it comes to Ubuntu and Linux.

---

### Post by kodb on 2011-03-28
Thanks for all of the above but somehow I am still screwing this up.
when i use the command
 ```
wget [URL="http://www.releases.ubuntu.com/lucid/ubuntu-10.04.02-desktop-amd64.iso"]http://www.releases.ubuntu.com/lucid/ubuntu-10.04.02-desktop-amd64.iso
```[/URL]
it connects to the server but then returns an
 ```
ERROR 404: Not Found
```
Any ideas why??  I just ran this about 10 times with same result.
When I use firefox from my desktop the file is there and attempts to download via the browser???

Thanks in advance for all the help as I continue to learn
Bob

---

### Post by falko on 2011-03-28
Try
```
wget http://www.releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-amd64.iso
```
instead.

---

### Post by BkkBonanza on 2011-03-28
If that address doesn't work then copy working the link from the browser and paste into your wget command. Ctrl-C in browser, Ctrl-Shift-V in ssh terminal.

(The one you were trying has ... in the middle so can't possibly work)

---

### Post by kodb on 2011-03-28
> **BkkBonanza said:**
> If that address doesn't work then copy working the link from the browser and paste into your wget command. Ctrl-C in browser, Ctrl-Shift-V in ssh terminal.

(The one you were trying has ... in the middle so can't possibly work)
 
Thanks, worked like a charm!  Not sure how the ... came to be in the middle because I hand typed exactly the cut and paste code that worked.
Many thanks for all your help; sometimes even the most trivial cli things are a great learning experience!
Bob

---

### Post by Z.K. on 2011-03-29
I am not fond of putty in linux.  It is a bit limited compared to the windows version.  I use ssh in a standard terminal and that works a lot better for my use.  I ssh to my server a lot and putty does not allow cutting and pasting very easily so I use a terminal.  wget though is probably the best way to get the iso or use a web browser if you have the desktop installed.

---

