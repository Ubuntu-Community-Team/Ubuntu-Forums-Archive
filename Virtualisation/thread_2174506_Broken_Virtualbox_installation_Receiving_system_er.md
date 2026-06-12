---
title: "Broken Virtualbox installation? Receiving system errors"
date: 2013-09-14
forum: Virtualisation
---

### Post by AliPM on 2013-09-14
Hi, I tried installing Virtualbox yesterday via the software centre but my wireless connection died part-way through installation. Fixed the wireless issues since then but I still can't get Virtualbox working, I've tried various things to try and get it back but nothing seems to work. Tried

sudo apt-get remove virtualbox
sudo apt-get install virtualbox 

and then install dkms. Installed generic headers as per lots of recommendations but no joy.

Tried uninstalling from terminal and then running the installer from Oracle's website but it says "breaks existing package that conflicts: 'virtualbox'"

If anyone can give me any advice it would be very welcome. Thanks

---

### Post by Jonathan Precise on 2013-09-14
```
sudo apt-get purge virtualbox.
```

Then try the one in oracle's website.

---

### Post by ibjsb4 on 2013-09-14
```
gksudo nautilus
```

Then go to your FileSystem and do a search on "virtualbox" and remove all leftovers.  Then install from the site.

---

### Post by QIII on 2013-09-14
To be sure everything that could be problematic is gone before reinstalling, don't forget to delete the .Virtualbox folder in your /home.

---

### Post by AliPM on 2013-09-15
Thanks all for your quick replies. It's now a moot point actually - after posting last night I extended my Windows system partition into some empty space before the Ubuntu partition, and for some reason Windows saw fit to remove the partition. But not the swap partition after it(?).

Annoying but not a big deal as nothing of importance was saved on the Ubuntu partition. I installed Mint instead and have installed VBox without any problems... so far.

---

### Post by ibjsb4 on 2013-09-15
Thats one way to fix it :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

