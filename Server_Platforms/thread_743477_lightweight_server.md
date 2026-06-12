---
title: "lightweight server"
date: 2008-04-02
forum: Server Platforms
---

### Post by happypig on 2008-04-02
I've got an old 500mhz pentium III machine that I'd like to use as a lightweight server. 
I'm thinking of installing ubuntu and samba (and anything else I find out I need as I go along). 
Once installed and working it's probably going to go into the garage (I will administer it using VNC)and I'd like it to be as frugal as possible; would it be possible to remove the graphics card to save power and for it still to work ?

---

### Post by netlogic on 2008-04-02
> **happypig said:**
> I've got an old 500mhz pentium III machine that I'd like to use as a lightweight server. 
I'm thinking of installing ubuntu and samba (and anything else I find out I need as I go along). 
Once installed and working it's probably going to go into the garage (I will administer it using VNC)and I'd like it to be as frugal as possible; would it be possible to remove the graphics card to save power and for it still to work ?

It depends on your bios. Some bios have option for do not halt on any errors. You will need to change your bios setting in case of the drive failure, so have your video card around.

**VNC isn't frugal. ** Command line is your friend. I really don't understand why everyone is going gui with servers in the last few years. It only causes miserable server administration experiences.

---

### Post by kerry_s on 2008-04-02
debian is your friend, net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

when it comes to package selection check the server stuff you want. 
uncheck the desktop, if you want gui, you can grab something light.
example:
apt-get install xorg fluxbox mc
exit
log in as your regular user
startx

---

