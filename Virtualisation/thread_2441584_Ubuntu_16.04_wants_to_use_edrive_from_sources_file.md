---
title: "Ubuntu 16.04 wants to use e:drive from sources file for libvert"
date: 2020-04-24
forum: Virtualisation
---

### Post by fahrbach on 2020-04-24
Apologies if this is the wrong forum but I'm trying to get KVM installed and Ubuntu keeps telling me:  E: Unable to locate package libvert-bin.  I went into the sources file and put # in front of DVD line and still did not work.  I then went into software updates and got rid of the CD-ROM choice.  The sources file even updated getting rid of the DVD line entirely still wants to use E: drive.  I think this is a bug but don't know how to get around it.

---

### Post by wildmanne39 on 2020-04-24
The E just stands for error, the package you need it not being found in the repositories make sure you have all repos enabled, main, universe, restricted and multiverse, then reload the repositories or run ```
sudo apt update && sudo apt upgrade 
``` then try to install the software again. No you do not want the CD Rom option check marked, I always install synaptic package manager first thing when I do a new install because there are many applications I can not find using software center, I almost 100 percent use the terminal to install these days unless I do not know the complete name of the application I want to install.

---

### Post by Doug S on 2020-04-25
> **fahrbach said:**
> E: Unable to locate package [COLOR="#FF0000"]libvert-bin[/COLOR].The package name is [COLOR="#FF0000"]libvirt-bin[/COLOR]

---

### Post by fahrbach on 2020-04-27
Thanks, Wildman.  Personally I think that that the sources.list file is incorrect.  I have removed every # in the file and still get the error.  I even upgraded to 19.10 which uses a different libvert bin and got TWO errors.  I then tried to load the libvert bin package from the Debian site but Ubuntu didn't like that.  I have QEMU-KVM running on another machine running 16.04 and a) it works just fine and b) I compared the sources.list file between both machines and they're identical.  My only conclusion is that the sources.list is pointing to invalid URLs.

---

### Post by deadflowr on 2020-04-27
> Thanks, Wildman. Personally I think that that the sources.list file is incorrect. I have removed every # in the file and still get the error. 
Hard to know without seeing what the sources.list looks like.

---

