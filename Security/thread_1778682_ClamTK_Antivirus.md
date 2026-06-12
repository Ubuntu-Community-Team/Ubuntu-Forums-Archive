---
title: "ClamTK Antivirus"
date: 2011-06-09
forum: Security
---

### Post by birkopf on 2011-06-09
Hi,

Did anyone managed to successfully update "Antivirus Engine" on ClamTk on Ubuntu ?  

This is well known issue... unfortunately.

I don't manage to do that even with compiling from sources :(

---

### Post by seawolf167 on 2011-06-09
I haven't had a problem with it updating. I installed it through the repos on 10.04 LTS

```
sudo apt-get install clamtk
```

---

### Post by pqwoerituytrueiwoq on 2011-06-09
i think the update command is [FONT=Courier New]sudo freshclam[/FONT] it may need a dash

---

### Post by birkopf on 2011-06-09
> **pqwoerituytrueiwoq said:**
> i think the update command is [FONT=Courier New]sudo freshclam[/FONT] it may need a dash

Sorry - forgot to mention that freshclam doesn't do the trick. 

BTW - Did you manually configured sources for updates or freshclam just run on default options ?

---

### Post by linuxinstalledfromhdd on 2011-06-09
You can try using bitdefender for Ubuntu:

[https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

---

### Post by pqwoerituytrueiwoq on 2011-06-10
> **birkopf said:**
> Sorry - forgot to mention that freshclam doesn't do the trick. 

BTW - Did you manually configured sources for updates or freshclam just run on default options ?
i have the ppa setup for clam av
[http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu)
is on my software sources

---

### Post by smithark on 2011-06-11
sorry, I'm not an expert in linux. But why do you need an antivirus for linux?

---

### Post by slooksterpsv on 2011-06-11
My updates are downloading and installing. Just ran sudo freshclam - you may want to purge clamtk and then reinstall.


EDIT: OHHH Engine, dunno about engine, I didn't do the engine lol sorry I misread

---

### Post by linuxinstalledfromhdd on 2011-06-11
The user is talking about the engine.  The repo is slightly behind the released source on their web site. If you want the latest engine and everything else, you will need to compile it from that source file from their web site.  Honestly, it works fine with updating the engine though. :)

---

### Post by uRock on 2011-06-11
I update the GUI via the ClamTK site. [http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/) Just download the .deb and let Ubuntu Software Center install it. 

@smithark It is recommended to scan shared folders to prevent sharing viruses with other systems. It does scan for a few Linux viruses as well.

Moved to ***Security Discussions***

---

### Post by birkopf on 2011-06-11
>  
i have the ppa setup for clam av
[http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu)
is on my software sources


- Could you please provide full source line to this PPA please ?

> 
sorry, I'm not an expert in linux. But why do you need an antivirus for
linux? 

- You're right, on Linux I don't need, but Clam is best with Windows
  viruses. I do lots of stuff for friends+contractors who have Windowses,
  as well as I download a lot, and by politeness I want to pre-scan
  everything before it leaves my machine for Win. You probably know that
  most (99%) Windows users are "panickly" scared of viruses, but if you'd
  ask any one of them what is a virus than... nobody knows what they're so
  scared of ;)

> 
My updates are downloading and installing. Just ran sudo freshclam - you
may want to purge clamtk and then reinstall. EDIT: OHHH Engine, dunno
about engine, I didn't do the engine lol sorry I misread 

Though - I cannot find anywhere configuration and that's what I get for
after freshclam:

ERROR: Please edit the example config file /usr/local/etc/freshclam.conf
ERROR: Can't open/parse the config file /usr/local/etc/freshclam.conf


Yep, GUI and Engine are totally different ;)

All in all after speaking with Clams developers - it's all fine. Here's
why: 

1) Repos are providing latest stable version for you system = fine
2) Clam AV (= Engine) is non graphical antivir software
3) Clam TK (=GUI) is just graphical interface, to ease process 
4) Clam AV doest get updates as often as Clam TK... thus problem

Maybe I will compile all from sources like advised. I like when all works
to full potential on my system.

---

### Post by the_phenom on 2011-06-11
ClamAV (the engine) just released 0.97.1, so it's a waiting game until all the distributions (Ubuntu, Fedora, etc) release packaged versions of it.

---

### Post by uRock on 2011-06-11
> **the_phenom said:**
> ClamAV (the engine) just released 0.97.1, so it's a waiting game until all the distributions (Ubuntu, Fedora, etc) release packaged versions of it.
Which will be included in Ubuntu 11.10, unless another version is released before then.

---

### Post by pqwoerituytrueiwoq on 2011-06-12
> - Could you please provide full source line to this PPA please ?
googled "ppa ubuntu-clamav" (just took parts from the url i gave you) and came up with
[https://launchpad.net/~ubuntu-clamav/+archive/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ppa)

---

