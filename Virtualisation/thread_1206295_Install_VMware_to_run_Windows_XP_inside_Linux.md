---
title: "Install VMware to run Windows XP inside Linux"
date: 2009-07-07
forum: Virtualisation
---

### Post by aaronsol on 2009-07-07
I'm hoping someone can help me because I've looked through these Forums a dozen times and only found information that either doesn't work or just isn't helpful. 

I'm trying to get any and all of the different pieces of VMware to be installed on my OS so that I can run Windows XP so that I can play Lineage 1 without having to dual boot. Because if I have to dual boot I'm just going to get rid of Linux because it just defeats the purpose for me but I like Linux better. 

Anyway, I downloaded the .rpm for the VMware player from their website and converted it to a .deb and installed. It says it was successfully installed but I can't find the program to run it in any of the menus. 

I've also tried doing this with VirtualBox, I got XP installed no problem except when I try to run the game it gets to the login screen then just locks up. 

I'm so lost, please send help.

Edit: Please do not tell me to just dual boot. I know this can be done because I play Lineage with some people that tell me they run it through VMware on Linux. They just don't really have the time to help me with it.

---

### Post by veloce on 2009-07-07
I suggest you try vmware server 1.07.

Here's a link to the howto:

[http://ubuntuforums.org/showthread.php?t=966070]("http://ubuntuforums.org/showthread.php?t=966070")

If you want to try something different, have a look at the virtualisation mega thread. (It's the second sticky).

---

### Post by RealG187 on 2009-07-07
Ya, Bodi.Zazen has some good tutorials on VMWare server.

You can also install VirtualBox from a deb.

Once you have rhe virtualization software installed and a boot device/ISO selected installing an OS is easy, just like on a real computer...

---

### Post by aaronsol on 2009-07-07
I got VMware server installed just fine but when I try to run the program, it acts like it's going to start, then just shuts back down.

---

### Post by veloce on 2009-07-07
> **aaronsol said:**
> I got VMware server installed just fine but when I try to run the program, it acts like it's going to start, then just shuts back down.

Sounds like it hasn't generated the kernel specific files (i.e. you haven't got it fully installed.)

Try running it from a terminal - that will tell you what the error is:

```
vmware
```

Seriously, the howtos that link from the mega thread go through all of this.

---

### Post by RealG187 on 2009-07-07
Did you run vmware-config.pl?

---

### Post by fjgaude on 2009-07-08
You might have to run vmware from the commandline as root the first time around. Then you can use the regular GUI to handle it.

---

