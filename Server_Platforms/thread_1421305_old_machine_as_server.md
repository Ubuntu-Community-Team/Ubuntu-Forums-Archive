---
title: "old machine as server"
date: 2010-03-04
forum: Server Platforms
---

### Post by ushills on 2010-03-04
I have an old PIII 600Mhz with 384Mb of ram that I would like to use as an email server, running squirrelmail and perhaps as a file server as well.  Would this be sufficient a spec to do this, it is above the minimum.  Alternatively I would use a vps but would prefer to have full control over access to data. Currently I have hosted email with google apps.

---

### Post by i.r.id10t on 2010-03-04
Way more than enough...   I'd get a pci SATA card and a couple of 1tb drives and set up software raid for your data storage... put the OS on a stand alone drive.  If it dies, reinstall - use the raid for data storage only (and perhaps the occasional backup of the OS drive)

---

### Post by R.Bucky on 2010-03-04
System Requirements ([https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)) are low for Ubuntu. Your experience may not be a happy one with a GUI installation, but the Server edition may function well if you limit your applications. I have found that once you install the mail and begin using your box for files that you will want more applications (e.g. Apache).

---

### Post by tlsarles on 2010-03-04
depends on number of users, if your only serving a few, you should be cool, but as stated, I wouldn't install the GUI

---

### Post by ushills on 2010-03-04
Thanks for the confirmation, I was going to run it headless anyway.

Only 4 family mail users, have a VM setup at the moment running squirrelmail, spamassasin and clamAV for virus detection in mail accounts using 384Mb of ram but cannot check processor in VM.  May consider connecting additonal drives and using it as a NFS plus as a web-server for my personal hosted website (may leave that with blogger for now).

Can I isolate the machine from my internal IP range if necessary or what attack vectors do I need to be concerned about after securing SSH with keys.

---

### Post by pawan_lal on 2010-03-04
i had configured postfix on ubuntu 8.04 lts. for web access i am using squirrellmail. i am easily able to send and receive emails by my POSTFIX mail server. i am facing problem in configuring 
 
[B]amavisd
spamassasin
clamav [/B]
 
plz guide me for that.
thx

---

