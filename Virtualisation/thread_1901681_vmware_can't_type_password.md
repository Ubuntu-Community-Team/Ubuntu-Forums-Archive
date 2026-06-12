---
title: "vmware can't type password"
date: 2011-12-29
forum: Virtualisation
---

### Post by SMario92 on 2011-12-29
Hi all I just joined these forums. 

I have never used a Linux OS before I installed the Ubuntu 11.10 sever using vmware (version 7.0.0) the installation completed successfully, but my issue is when it reboots after the install and then goes to black screen then asks me to login I'm able to type in my username but when I try to type in my password it just says blank I am not able to type the password. Just to clarify I did a manual install in vmware does anyone have a solution to this issue? I have been researching it for two hours now and my brain's fried :confused: Anyone's input would be greatly appreciated thank you

P.S If I am able to login successfully will I then be able to access the graphical OS? (sorry if I sound like a noob)

---

### Post by lisati on 2011-12-29
If you are logging on via a command line, it is normal for the password to stay blank. Just type it in as normal.

---

### Post by SMario92 on 2011-12-29
> **lisati said:**
> If you are logging on via a command line, it is normal for the password to stay blank. Just type it in as normal.

ok if thats true how do I get to the main login screen?

---

### Post by haqking on 2011-12-29
> **SMario92 said:**
> ok if thats true how do I get to the main login screen?

You said in first post that you installed Ubuntu server ? Server does not have a GUI by default.

IF you want one then you can install one with

```
sudo apt-get install ubuntu-desktop
```

However it is rather heavy, probably better with something like xfce, that being said for a server OS you dont really need or should want a GUI

---

