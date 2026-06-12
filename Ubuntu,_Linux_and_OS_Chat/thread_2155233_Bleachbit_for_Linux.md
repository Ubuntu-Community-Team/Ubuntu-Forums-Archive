---
title: "Bleachbit for Linux"
date: 2013-06-17
forum: Ubuntu, Linux and OS Chat
---

### Post by user_of_gnomes on 2013-06-17
What do you think of Bleachbit for Linux?
I've always shunned automatic cleaners for Windows although Ccleaner was one of the few helpful tools I've used to quickly put things in order. 

I've been experimenting a bit with Bleachbit and I was hoping it could run during boot but even though the option is present, it doesn't seem to do anything. 
The other options seem useful although I don't know why you'd expect to find any thumbs.db or .DS_STORE on Linux.

---

### Post by rrich1974 on 2013-06-17
i just use 
> sudo apt-get autoremove
sudo apt-get autoclean

some people do not recommend using cleaning tools for linux.

---

### Post by ajgreeny on 2013-06-17
My only advice would be to look very carefully at the list of items to be removed as bleachbit can sometimes suggest removal of files or applications that you have installed by means other than from the official repos.

Don't simply say yes to everything or you may have to re-install some things you really want. Apart from that I fully agree with rrich1974

---

### Post by monkeybrain2012 on 2013-06-17
Have been using it since 10.04, never had a problem. Just make sure the boxes you check for removal are things you intend to remove (e.g you probably don't want to clean session restore in your browser and probably don't want to remove passwords) and click "preview" to see what it is going to delete before you hit the delete button. All is fine. I know some people advise against it but judging from their posts they have never used it.

Sure you can use the command line to autoclean and clean cache and other things in your home directory manually. But computer is a labour saving device so why do it the long way when you have an automatic tool?

 I don't see how it is 'unsafe" and how it would be safer to run "sudo apt-get autoremove" instead. Now on my Debian sid there are a bunch of software it says are autoremovable but I don't trust it (sid is kind of unstable so do everything carefully when it tries to remove something), but bleachbit never "autoremove" if you don't check the box.

Now another program, debprphan, is dangerous even though it is in repo also, I would advise against using it cause it considers "orphan" anything that isn't installed as a dependency of something else and it removed my entire 10.04 installed when I was new to Ubuntu.

EDITED: That says, it is not essential that you clean your Linux install. I use bleachbit a lot because I have multiple Linux installed and some testing ones are on fairly small partitions (less than 10Gs) and I need the room.

---

### Post by monkeybrain2012 on 2013-06-17
> **ajgreeny said:**
> My only advice would be to look very carefully at the list of items to be removed as bleachbit can sometimes suggest removal of files or applications that you have installed by means other than from the official repos.



It doesn't suggset removing applications unless apt-get says they are autoremovable. Running sudo apt-get autoremove would have exactly the same effect. It is not like deborphan.

---

### Post by kurt18947 on 2013-06-17
I use bleachbit and haven't had it bork a system - yet.  Computer Janitor on the other hand .......

---

### Post by ajgreeny on 2013-06-18
Seeing kurt18947's post reminds me, slightly shamefaced, that it was not bleachbit that caused my potential problem but computer-janitor.

But whatever it was that I used, I have no further reason at the moment to bother with any of them, as I have a nice big hard drive and masses of empty space,and extra libraries and applications that are just sitting there, unused, do not slow down a Linux system as they can in Windows.

---

### Post by user_of_gnomes on 2013-06-18
> But whatever it was that I used, I have no further reason at the moment to bother with any of them, as I have a nice big hard drive and masses of empty space,and extra libraries and applications that are just sitting there, unused, do not slow down a Linux system as they can in Windows. 

I had a problem with a Ubuntu 13.04 installation where it refused to load the display manager because the filesystem partition was full. Had to run apt-get clean before it'd let me in again. I can't really have that sort of thing happening when I'm not around. It seems like the default size (guided formatting with LVM) for the filesystem partition is only 255MB which may be too small? However, I think that even if I were to make it larger, it'd just take longer for the problem to rear its head again ... 

It seems that when you tell Bleachbit to run at start-up it doesn't actually perform the routines you previously ticked the boxes of. Why is that option there at all, does anyone know?

---

### Post by 2Stoned on 2013-07-08
The best way is to do this from the terminal in my experience. Or use ubuntu-tweak instead of bleachbit. The best cleaning tool for ubuntu imo.
To install ubuntu-tweak: 

```
sudo add-apt-repository ppa:Tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

---

### Post by mardybear on 2013-07-08
I've used bleachbit for a while and it helps get rid of junk, just be careful what you remove. I also use Ubuntu-tweak to periodically remove old kernel updates from my system. Agree, CCleaner is great for a windows based OS.

mardybear

---

