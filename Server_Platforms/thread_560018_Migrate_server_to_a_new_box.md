---
title: "Migrate server to a new box?"
date: 2007-09-25
forum: Server Platforms
---

### Post by falcon15500 on 2007-09-25
Hi all,

  I have been running a server (LTS server) for a while now on a spare desktop box at home.  It is running LAMP, postfix, spamassassin, squirrelmail, BIND, NTP and a few other odds and ends.  Been working solidly since I managed to get it all working.

  I have purchased an old Compaq Proliant 5500 quad P3 xeon box (for the princely sum of $72 aussie dollars) and would like to migrate my server over to this new box.  I don't really want to go through the hassle of installing everything from scratch again.  What would be the best way to go about this?

  I have installed the same distro version, updated to the same packages.  I have then installed the same packages on the new box, that are installed on the old box.  So theoretically things should be quite close in terms of what is installed.  So, I should just need to copy over the data and configs to be current?

falc

---

### Post by HermanAB on 2007-09-25
Theoretically yes.  In practise, you may have better luck by making a disk image and installing it on VMware on the new server.

---

### Post by falcon15500 on 2007-09-25
> **HermanAB said:**
> Theoretically yes.  In practise, you may have better luck by making a disk image and installing it on VMware on the new server.

Hmmm... Thanks for the input - I don't _really_ want to go down that path, but I will keep it in mind.

falc

---

### Post by HermanAB on 2007-09-26
Well, the advantage of a VMware disk image is that once you went through the pain, you can move it to another bigger better machine again and again.  

Here is a guide: [http://blogs.techrepublic.com.com/networking/?p=148](http://blogs.techrepublic.com.com/networking/?p=148)

---

### Post by netlogic on 2007-09-26
benefits of VM are many
1. portable - if you deployed SAN in your network, VM is tiny.  These days, OS and few apps can't be more than 3 gigs to 10gigs without the data partitions. Working late at work? Why don't you dump that to your laptop and work during dinner while your wife or girlfriend throw shits at your face for not paying attention to her?
2. It saves headache of installation and backup - They are just files. Don't have to repartition.
3. You can separate production and testing on the same box.
4. RAM is dirt cheap.
I remember paying $300 for 4megs when I was a child. I worked entire summer to buy RAM. What a freaking nerd I was...
5. Why bother do apache virtual hosting? Give everyone their own virtual machine.  They will call you less.
6. Have fun building a custom VM that you can carry with you. Linux is very portable. Make a virtual router, tor server, proxy, whatever you want... Carry it in your laptop, pen drive, ipod, etc.
7. Women LOVE It. Trust me. She loves it when I yell, I am going to VM you bi*c*.
Actually, she just bi*c* slap me.

---

### Post by djchandler on 2007-09-26
I have no idea if this would work or not. The only server I use is built into my router (DHCP). But wouldn't the configuration files for all these processes be in the home directory of the account you log in under to run these servers? (No offense, but they're probably in hidden folders.) I've done re-installs of Linux before, and all I needed to do to restore my settings was to back up my home directory, including hidden folders, then copy them back into my new user account's home folder after the (re)install.

---

### Post by netlogic on 2007-09-26
1) Alright. I would say VM is so much fun, but if you want an old fashion server.

You got many options. 

2) You can tar and compress all the partitions and use a live cd  to move it. You can create your filesystem by using cfdisk, parted, or gparted. Make sure you untar and uncompress at / level. 

3) automated clean installation. Another option is just create a script to output your permission settings to a txt file. 

You can also output the package listing by 

**sudo dpkg --get-selections > pkg.lst**

and use this file to install everything after the default installation.

4) also try mondo rescue
it makes iso images for you and install the exact image from the iso.

---

