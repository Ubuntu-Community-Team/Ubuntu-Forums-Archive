---
title: "Creating a local update repository"
date: 2004-12-12
forum: Repositories &amp; Backports
---

### Post by mousematt on 2004-12-12
Greetings

I have just migrated to Ubuntu after years and years with Mandrakelinux. I am very impressed and slowly getting used to GNOME instead of KDE, neutral browns instead of blues, and synaptic and apt-get instead of urpmi  :smile: 

I have updated my workstation using synaptic, but would like to create a single installable update CD for my other machines. Under Mandrake this is easy: I just download the entire update folder off the FTP mirror, setup URPMI and burn the CD. Can I do something similar with Ubuntu?

Unfortunately, I have cleared all installed packages from my /var/cache/apt/archives folder (playing with synaptic). What do I need to do to get all of the security updates into a local folder and onto a CD-R.

Thankyou.

---

### Post by orestis82 on 2004-12-13
chech here:

[http://ubuntuforums.org/showthread.php?t=7455](http://ubuntuforums.org/showthread.php?t=7455)

---

### Post by mousematt on 2004-12-13
[QUOTE=orestis82]chech here:

[http://ubuntuforums.org/showthread.php?t=7455](http://ubuntuforums.org/showthread.php?t=7455)[/QUOTE]
 Thanks for the suggestion, but that doesn't answer my question at all. I only want to download the security updates for Ubuntu. 

When I was using Mandrakelinux, all I needed to do was download the updates folder from a Mandrake mirror. 

How do I do this in Ubuntu without downloading each individual package? Thankyou

---

### Post by orestis82 on 2004-12-14
[QUOTE=mousematt]Thanks for the suggestion, but that doesn't answer my question at all. I only want to download the security updates for Ubuntu. 

When I was using Mandrakelinux, all I needed to do was download the updates folder from a Mandrake mirror. 

How do I do this in Ubuntu without downloading each individual package? Thankyou[/QUOTE]
 I think that the thread I linked describes exactly your situation. You have to download each individual package, since you deleted your package cache. 

You can automate the procedure, since you can export the urls into a file, format it, then use some script to wget everything. Or in windows, using a download manager.

---

### Post by mousematt on 2004-12-14
Okay. Yes your thread did explain how-to get the updates. Although, your answer did not tell me thats the only way I can do it...

Thankyou for your help. I am somewhat disappointed, I had hoped there was another way. However, this is how Debian works. I can't, and shouldn't, expect apt-get to be urpmi.

Thanks for your help.

---

### Post by tomchuk on 2004-12-14
Try:

```

sudo apt-get intsall apt-show-versions
sudo apt-get clean
sudo apt-get -d --reinstall install `apt-show-versions | egrep 'updates|security' | sed 's/\/warty.*$//g'`
mkdir ~/apt-updates
cp /var/cache/apt/archives/*.deb ~/apt-updates 

```

Burn the contents of ~/apt-updates to a CD and then run "apt-cdrom add" with the cd in the target computer.

---

