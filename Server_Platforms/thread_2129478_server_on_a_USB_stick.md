---
title: "server on a USB stick ?"
date: 2013-03-26
forum: Server Platforms
---

### Post by ghat on 2013-03-26
So one of my new purchases is a X9SCM-iiF supermicro motherboard, to implement a media server to serve me for the next few years.

The host is all setup and working with LTS+zfs (some issues still remain) but thats not what this thread is about. 
I have a 160GB system disk and all the rest (upto 12) drives are for zfs...

The motherboard has a onboard USB2.0 type A socket, and I am incling on installing a USB stick there and run the system from the USB stick, which
would free up my 160GB slot for a spare drive on the zfs...

My question to the guru's here is 
1. Is this a good idea ?
2. Should I run a Live-USB system with persistence OR a vanilla system install on the USB stick
  [ By Live USB I mean a customized version from the Ubuntu Repos, not a ready-made one. ]

I can probably also write some scripts which would keep a updated build on the server as it runs, 
and dump an image to the storage and possibly another USB stick connected to the machine. 

I can also dump the running system on to another USB stick for backup every night, so on case something goes wrong, I can 
just swap out the sticks and the system can be easily recovered. 

I plan to run this server 24x7 and would primaraily serve as a NFS/SAMBA share and occasionally at times
do some video and voip stuff over it. 

G

---

### Post by GreenTaurus on 2013-03-26
I tried this and had no success with my X7DA8 supermicro board -- but I wanted to subscribe in case you decided to go for it.

---

### Post by sanderj on 2013-03-26
Yes, run a Live-USB system with persistence.

It should work. And make it so, that it is easy to replace the USB-stick with another USB-stick with a fresh install.

---

### Post by thapeliMat on 2013-03-27
Hi guys,
I hope this isn't a wrong thread.
I just wanted to know if live USB's can get viruses or not.

Say I use Ubuntu or Tails OS on a live USB so I can boot it from other comuters,if the Pc from which I boot has a virus,will the OS on the liveUSB be affected/infected in anyway? If so,how can that be handled?

---

### Post by ghat on 2013-03-27
> **thapeliMat said:**
> Hi guys,
I hope this isn't a wrong thread.
I just wanted to know if live USB's can get viruses or not.

Say I use Ubuntu or Tails OS on a live USB so I can boot it from other comuters,if the Pc from which I boot has a virus,will the OS on the liveUSB be affected/infected in anyway? If so,how can that be handled?

Yes wrong thread.... 

Virus's are hard to get on any Linux/Unix/Mac as the process' are run with user permissions, even if you get a virus at most it may damage the files in your home directory which will not affect the system. 
If you insert the tails/ubuntu/USB stick into a running windows operating system it can potentially infact the USB drive and make the tails/ubuntu install on it useless, but it cannot infect the tails/ubuntu OS. 
If you booted ubuntu/tails then there is no way a virus on the HDD can infect the live linux.. 

in Linux/Unix based devices always remember..

1. ALWAYS CHANGE the default password to something you know. 
    If you install Ubuntu/or any distribution, the first thing to do is make sure the "super user" (the one user it tells you to setup) has a password which is setup by YOU, 
    the second (AND MOST IMPORTANT THING) is to login to that account, and change the root password with [FONT=courier new]"$>sudo passwd root[/FONT]" to something what you (and only you) know. 
    The root account is disabled in a canonical/Ubuntu-live-cd, but you cannot trust "any" liveCD like that, if you dont want to enable the root account at a minimum you should do 
    ```

$> sudo passwd root 
(setup some simple passwd 123456 say)
$> sudo passwd -dl root 
Make sure the passwd is deleted and the root account is locked
$> sudo rm -rf /root/.ssh* /root/.rhosts 

```
    
2. Use a password with 10+ characters, and a good mix of numbers, caps and special characters..
    One hint is Write down the FULLname of the first person you had sex with in your life. Insert the 2 char year when you had that incident, after the first name, add some simple special characters in the beginning and end of that word
  e.g.  ^Sandra98Bullock- OR &Angelina99Jolie&

It will be extremely hard to crack that password, and you can still remember it... 

G ;-)

---

### Post by ghat on 2013-03-27
> **GreenTaurus said:**
> I tried this and had no success with my X7DA8 supermicro board -- but I wanted to subscribe in case you decided to go for it.

No success ? Why ?

setting up a custom live USB is probably PITA especially with ZFS etc...

---

