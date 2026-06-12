---
title: "Encrypted Home folder"
date: 2012-02-25
forum: Security
---

### Post by octaviuos on 2012-02-25
i bought a mini laptop to use for online banking only (my main computer is windows and really unsafe.somebody stolen my bank account recently)
i installed ubuntu on my new laptop. (11.10) when i installed the ubuntu selected encrypt my home folder.
i always use truecrypt as i always store my very important information on my hard drive to encrypt my hard drive. but seems TC is not good for ubuntu ...
well i have some questions
1-What is home folder ?
2- now ubuntu really encrypted my Home folder and nobody can access my files which i put there ?
3-most important thing is my internet activity to be encrypted (firefox/chrome). now how i can understand those info in on Home folder or somewhere else ?

:confused:

---

### Post by aeronutt on 2012-02-25
> **octaviuos said:**
> ... but seems TC is not good for ubuntu 
I run and use truecrypt in Ubuntu religiously. It works fine.

> **octaviuos said:**
> 
1-What is home folder ?

It's a folder located at /home/<username>, and is where (by default) many of your user specific configurations are stored, and where 'home' is, for no better explaination. Default directories such as 'Documents', 'Videos', personalized to the <username> are there.

> **octaviuos said:**
> 
2- now ubuntu really encrypted my Home folder and nobody can access my files which i put there ?
It's as secure as your password when it's encrypted (when you're logged off).

> **octaviuos said:**
> 
3-most important thing is my internet activity to be encrypted (firefox/chrome). now how i can understand those info in on Home folder or somewhere else ?

Internet security/activity is mostly independant of encryption of your home folder.  But yes, by default, your bookmarks, history, etc are stored in your homefolder, and will be encrypted when you're not logged on.

---

### Post by ztux on 2012-02-25
Your home folder is where ALL of your files go. It's the only place you have write permission by default. Unless you ran something as root, it goes here. This is in contrast to Windows' virtual folders which can redirect legacy programs to write somewhere outside of your home directory.

The home folder encryption does what it says, it encrypts the entire home folder. No exceptions. All your personal files are safe.

Unless the thief can crack your login password or recover from /tmp, all your personal files are safe and completely inaccessible.

---

### Post by Porcini M. on 2012-02-25
Note that it will not be encrypted when you are logged on, though. For that, truecrypt does work as the above mentioned (and there are other similar apps IIRC). I use the command-line "ccrypt" utility for me (I just have a text file with sensitive info in it), called via gksudo from within a script.

---

### Post by aeronutt on 2012-02-25
> **ztux said:**
> Your home folder is where ALL of your files go. It's the only place you have write permission by default. Unless you ran something as root, it goes here. This is in contrast to Windows' virtual folders which can redirect legacy programs to write somewhere outside of your home directory.

The home folder encryption does what it says, it encrypts the entire home folder. No exceptions. All your personal files are safe.

Unless the thief can crack your login password or recover from /tmp, all your personal files are safe and completely inaccessible.

Saying ALL is a bit misleading. As you say, between /tmp, /media (say if you mount a USB drive, etc), /proc, lost+found's , etc....it can be a bit tricky to say ALL for all of the time.

---

### Post by octaviuos on 2012-02-25
1-ok so you guys say my Home folder is really encrypted and safe now ? (how i can understand its really encrypted ? there is no sign ...) - i don't need TC then ?
2-i downloaded Firefox 10.0.2. it didn't asked for an install. its just a folder on Downloads folder and i open it there everytime. so my internet activity is now totally in Home folder and safe ?
3-
> Unless the thief can crack your login password or recover from /tmp
i have a good password i think but what is /tmp story ?!
4-
> I run and use truecrypt in Ubuntu religiously. It works fine.
on windows TC have an option to encrypt hard drive. but @ubuntu there is no such option. there is just 500 fake drive (I J X Y W ...) and i have no Idea where are they from !

---

### Post by Porcini M. on 2012-02-25
> **octaviuos said:**
> 1-ok so you guys say my Home folder is really encrypted and safe now ? (how i can understand its really encrypted ? there is no sign ...) - i don't need TC then ?


Only when you're not logged in. If malware is running while you're logged in, or somebody gets access to your computer while logged in (say you step away from it & somebody else uses your computer), then the data is available.

To verify your home folder is encrypted while not logged in, boot your computer from a live CD, mount the machine's hard drive, and attempt to read the contents of the home folder (you shouldn't be able to without providing your password for decryption).

---

### Post by aeronutt on 2012-02-25
Best if you install firefox from the repositories. That way all security and updates will be automatic (as you run update manager).

Go to software manager, featured, and see if firefox is installed. If not, install from there, if so, firefox can/should be run from the menu's.

(Or install synaptic, and check if firefox is installed from there).

As far as truecrypt, did you create a truecypt volume?  I'd recommend you read the online manual for truecrypt.

---

### Post by octaviuos on 2012-02-25
> Only when you're not logged in. If malware is running while you're logged in, or somebody gets access to your computer while logged in (say you step away from it & somebody else uses your computer), then the data is available.
well i think TC is same too .. When you enter the pass after it all is decrypted .. if not then if email a text file your friend can't read it !

> Best if you install firefox from the repositories. That way all security and updates will be automatic (as you run update manager).
you had to tell me this sooner.. i put several hours on its setting. i don't want remove it and install again.. (however i didn't installed it. its like a portable software i think)
also i think even it show popup or something if a new update come 

---------
-also somebody sais my password can cracked from /tmp /media . what is that mean !

---

### Post by aeronutt on 2012-02-25
> **octaviuos said:**
> well i think TC is same too .. When you enter the pass after it all is decrypted .. if not then if email a text file your friend can't read it !


you had to tell me this sooner.. i put several hours on its setting. i don't want remove it and install again.. (however i didn't installed it. its like a portable software i think)
also i think even it show popup or something if a new update come 

---------
-also somebody sais my password can cracked from /tmp /media . what is that mean !


You may get updates for THAT verions of firefox, but you won't get updated versions. Again, best if you install from repositories, or else everytime you want to update to a new version, you will have to re-do all your work.

Your password won't get cracked from anything installed by default in Ubuntu.

---

### Post by octaviuos on 2012-02-26
if i install from repositories then its in Home folder and encrypted then ?

---

### Post by Porcini M. on 2012-02-26
> **octaviuos said:**
> if i install from repositories then its in Home folder and encrypted then ?

The user-specific data for firefox is put in the user's home folder (specifically in the .mozilla folder) - things like bookmarks, cache, history, etc.

---

