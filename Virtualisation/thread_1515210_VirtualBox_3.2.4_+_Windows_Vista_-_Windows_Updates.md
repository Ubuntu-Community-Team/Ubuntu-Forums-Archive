---
title: "VirtualBox 3.2.4 + Windows Vista - Windows Updates"
date: 2010-06-22
forum: Virtualisation
---

### Post by JustinR on 2010-06-22
Hey everybody!


(Background Info)
I installed VirtualBox 3.2.4 (the latest release) on Ubuntu 10.04 32bit and I'm using my existing Windows Vista Home Premium 32bit installation according to the how-to in the VirtualBox Manual. After figuring out a Windows activation problem everything works until it wanted to install Windows Vista SP1 (which I thought I already installed). So I went ahead and said okay to the update while Windows was running in VirtualBox. Well it failed with an error, I restarted Windows natively the process "Jusched.exe" told me "C:\Users\Justin Reno" was corrupt - all of my documents and downloads were which was good so I ran chkdsk on the next bootup to repair any other directories within my home folder. Well chkdsk seemed to work, it gave some errors but now has left around 2GB of recovered files in the .SDB format - which I don't know what to do with (there all dated specific dates). Well anyways everything still seems to be working and I'm going to try to install Vista SP1 natively.

Question: So what can I do with these .SDB files? Are they like archives? I tried looking them up and I can't find much about them. I need to check if I have 7zip installed and I'll post back.
And why would this happen virtualizing Vista?

Thanks.

---

### Post by wilee-nilee on 2010-06-22
The .sdb files are MS not Vbox you might try a Vista forum for help on this if nobody answers here.;)

Also make sure you have the video memory set to 128 MB

---

### Post by JustinR on 2010-06-23
Yep I tried to look the files up nothing really came up so I don't know why Chkdsk creates them. I tried to install Vista SP1 natively and it still errored so I ended up reinstalling and reconfiguring Vista on my hard drive and remembered that I forgot to disable my internet security suite which was actively replacing the registry keys the service pack was changing in the previous installation. Ugh...
:lolflag: Well now everything is installed and working fine, including SP1. So I guess this thread is solved now!

---

