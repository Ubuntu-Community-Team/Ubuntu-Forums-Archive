---
title: "sudo apt-get install ubuntu-mobile"
date: 2008-06-25
forum: The Cafe
---

### Post by Mateo on 2008-06-25
Anyone done this?  If so, what is your thoughts?  Thinking about doing it on my Eee.

---

### Post by fatality_uk on 2008-06-25
Let me know what happens. I got my Eee here ready to fire up :D

---

### Post by zmjjmz on 2008-06-25
IMO it'd be better on the Wibrain B1, but that uses Via chipsets :/

---

### Post by Mateo on 2008-06-25
> **fatality_uk said:**
> Let me know what happens. I got my Eee here ready to fire up :D

I'm wondering how best to do this is.  I was thinking about getting ubuntu server edition and installing that first... but then i won't have internet to install ubuntu-mobile.  is there any command-line wifi?

---

### Post by zmjjmz on 2008-06-25
There is, but I forget the commands D:

---

### Post by frup on 2008-06-25
> **Mateo said:**
> I'm wondering how best to do this is.  I was thinking about getting ubuntu server edition and installing that first... but then i won't have internet to install ubuntu-mobile.  is there any command-line wifi?

find what debs are pulled for your wifi or use ndiswrapper and then learn about ifconfig and /etc/network/interfaces etc.

that should help :)

---

### Post by cardinals_fan on 2008-06-25
> **zmjjmz said:**
> There is, but I forget the commands D:
ifconfig
iwconfig
dhcpcd
ping
netstat

---

### Post by myusername on 2008-06-26
netstat? why? just try an download the file...it skips a step so its faster

---

### Post by frup on 2008-06-26
wget may be useful too and knowing how to use one of the CLI browsers come to think of it.

---

### Post by legolas_w on 2008-06-26
What will happen if I execute this command?
will it replace ubuntu 8.04 with the ubuntu mobile?
can someone please explain, I saw the MID screenshots but I do not know how i can test it myself.

Thanks

---

### Post by frup on 2008-06-26
If it's the same as installing Ubuntu-desktop or Kubuntu-desktop it should just provide a login option to use ubuntu-mobile packages as a session, otherwise I have no idea.

The best way to check would be to install either in a spare partition or in a virtual machine, the virtual machine is probably the safest and least hassle.

---

### Post by legolas_w on 2008-06-27
Does anyone did this?
will it remove current gnome desktop?

Thanks.

---

### Post by paul101 on 2008-06-27
oooooh i shall have to try this when i get my ubuntu up and running :D

---

### Post by fatality_uk on 2008-06-27
Nope, couldn't nick one of the sales peoples eeepc to try it :| DAMN!! :|

---

### Post by paul101 on 2008-06-27
i wonder if it would be good on my thinkpad x61? (using touchscreen)

---

### Post by legolas_w on 2008-06-27
I execute the order :-D
I will let you know whether it kills the gnome and ubuntu and all my configuration or not :D

---

### Post by fatality_uk on 2008-06-27
legolas_w how did it go??

---

### Post by fatality_uk on 2008-06-27
[https://wiki.ubuntu.com/Testing/Cases/UMEinstall](https://wiki.ubuntu.com/Testing/Cases/UMEinstall)

---

