---
title: "HP ASM SMH DL320 DL3x0 Servers Fan control"
date: 2010-03-05
forum: Server Platforms
---

### Post by phillips321 on 2010-03-05
Controlling Fan speed on HP servers (This applies to the DL320).
HOW-TO Install:

This post is the continuation from this old post: [http://ubuntuforums.org/showthread.php?t=521911]("http://ubuntuforums.org/showthread.php?t=521911") as i have changed the location of the packages

first of all this was tested on a fresh build of 6.06LTS so dont go crying if it dont work on your system.

install fakeroot and rcconf

```
sudo apt-get install fakeroot rcconf
```
Now download the 2 packages we need

New package locations are here: [www.phillips321.co.uk/apps/HP_DL320_G2]("www.phillips321.co.uk/apps/HP_DL320_G2")

```
wget http://www.phillips321.co.uk/apps/HP_DL320_G2/hpasm_7.6.0-112_i386.deb
wget http://www.phillips321.co.uk/apps/HP_DL320_G2/hpsmh_2.1.6-156_i386.deb
```
now install both of the packages

```
sudo dpkg -i hpasm_7.6.0-112_i386.deb
sudo dkpg -i hpsmh_2.1.6-156_i386.deb
```
once they have both installed go into rcconf and activate them so they start at boot

```
sudo rcconf
```
now reboot and you should be done

Problems....if hpsmh keeps looking for a user called hpsmh and a group calld hpsmh

Error message output is

```
chown: 'root:hpsmh' : invalid group
chown: 'hpsmh:hpsmh' : invalid user
```
then you need to add the user hpsmh
```
sudo useradd hpsmh
```

---

### Post by David Tomic on 2010-04-01
Thanks for the post! ;)

I've got the hpasm package installed, and it works fine, except that it doesn't start automatically when the system boots.

I have to manually open up terminal and execute 'sudo /etc/init.d/hpasm start', and then everything runs fine [until the next reboot].

I've checked that it's set selected using rcconf, but still no joy.

Any ideas what my problem might be?

---

### Post by stoneattic on 2010-07-24
I've got the same thing going on.  I need to run "sudo /etc/init.d/hpasm start" after a reboot.  Any one have any ideas?

---

### Post by mallegonian on 2010-08-14
I think you need to run "hpasm activate" or something like that.

---

### Post by hunterhdolan on 2010-09-21
Great post!!!

---

### Post by RavonTUS on 2010-09-30
Greetings,

I tried this on my HP DL380 G3 with ubuntu 10.4 server.  I keep ending up with the following message...
```

sudo /etc/init.d/hpasm/start

/etc/init.d/hpasm: line 9: /etc/init.d/functions: No such file or directory

```

Any suggestions on how to fix it?

-Ravon

---

### Post by RavonTUS on 2010-10-04
Greetings,

I found that HP now has a "[HP ProLiant Support Pack CD for dpkg-based distributions]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=1121516&swItem=MTX-aa33f3378fc04981981e73c5a6&prodNameId=3288134&swEnvOID=4093&swLang=8&taskId=135&mode=4&idx=1")".  It appears to support Ubuntu 10.04 LTS and contains the HP System Health Application and Command line Utilities.

I installed it following their directions and I can do the follow command and get this response...

```

sudo hplog -f

```
```

ID     TYPE        LOCATION      STATUS  REDUNDANT FAN SPEED
 1  Var. Speed   Processor Zone  Normal     Yes     Low    (  8)
 2  Var. Speed   Processor Zone  Normal     Yes     Low    (  8)
 3  Var. Speed   I/O Zone        Absent     No      Unknown
 4  Var. Speed   I/O Zone        Normal     Yes     Low    ( 15)
 5  Var. Speed   Processor Zone  Normal     Yes     Low    (  8)
 6  Var. Speed   Processor Zone  Normal     Yes     Low    (  8)
 7  Var. Speed   Pwr. Supply Bay Normal     Yes     Low    ( 20)
 8  Var. Speed   Pwr. Supply Bay Absent     No      Unknown

```

So, it appears my fans are running as low as they will go, however, this server is still too noisy for a small office.  

As you can see, I removed two of the redundant fans, unplugged the backup power supply and closed the server cabinet door.  Still this unit is loud.  HP was definitely not designing this beast to be used in doors.

Next step?  Maybe cut the voltage to each fan?  Just add a resistor in-line?  I don't know if I'm that daring just yet.

Let me know if you come up with something better.

-Ravon

---

### Post by RainyCity on 2010-11-02
Fresh install of 10.04 and neither the install or normal operation would work until I pointed /bin/sh to /bin/bash.

sudo mv /bin/sh /bin/sh.bak
sudo ln -s /bin/bash /bin/sh

---

### Post by freechelmi on 2011-07-12
Hi, do we finally have a solution for making the fan working at "normal speed" .

I installed all the Red hat packages through alien , and launching the services does nothing ...

 I really regret to have bought such a noisy server ....

---

### Post by S1gurd on 2011-07-14
I am having this issue as well.  10.04 LTS.  No joy using the HP tool above.  I cannot even get this to install, nevermind what HP claims.

---

### Post by freechelmi on 2011-07-14
> **S1gurd said:**
> I am having this issue as well.  10.04 LTS.  No joy using the HP tool above.  I cannot even get this to install, nevermind what HP claims.

There is an easier way than getting the CD , there is an apt repo : 

You run this sh which just add the repo in your sources list 

[http://downloads.linux.hp.com/SDR/downloads/bootstrap.sh](http://downloads.linux.hp.com/SDR/downloads/bootstrap.sh)

The repo is for lucid 

deb [http://downloads.linux.hp.com/SDR/downloads/ProLiantSupportPack](http://downloads.linux.hp.com/SDR/downloads/ProLiantSupportPack) lucid/current non-free


However I stil can find how to get the hpasm , which to do the trick for others above.

I got hp-health service running but my fans are still 90 % speed

---

### Post by enderox on 2012-01-26
> **RavonTUS said:**
> ```

sudo hplog -f

```
```

ID     TYPE        LOCATION      STATUS  REDUNDANT FAN SPEED
 1  Var. Speed   Processor Zone  Normal     Yes     Low    (  8)
 2  Var. Speed   Processor Zone  Normal     Yes     Low    (  8)
 3  Var. Speed   I/O Zone        Absent     No      Unknown
 4  Var. Speed   I/O Zone        Normal     Yes     Low    ( 15)
 5  Var. Speed   Processor Zone  Normal     Yes     Low    (  8)
 6  Var. Speed   Processor Zone  Normal     Yes     Low    (  8)
 7  Var. Speed   Pwr. Supply Bay Normal     Yes     Low    ( 20)
 8  Var. Speed   Pwr. Supply Bay Absent     No      Unknown

```

So, it appears my fans are running as low as they will go, however, this server is still too noisy for a small office.  
-Ravon

digging up an old thread as I'm contemplating the purchase of a DL320s.

Does hplog show anything different if all fans are present. In my experience with many brands, redundant fans configurations wont always run quiet if any fan is missing. I have a PE2850 here that I cant shut up as it is missing two chassis fans :(  

Does hplog show fan speed low when all fans are present ?
do the fans ramp up if any fan is removed ? what does hplog show during all this ?

many thanks in advance.

---

