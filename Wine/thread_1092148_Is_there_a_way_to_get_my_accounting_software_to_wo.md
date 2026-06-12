---
title: "Is there a way to get my accounting software to work on ubuntu?"
date: 2009-03-10
forum: Wine
---

### Post by Solorflare on 2009-03-10
I have wine installed on my ubuntu computer and I have 
Quickbooks accounting 2008/09.

I am wondering if it is posible to install the software onto my ubuntu computer?

I have tried to install it myself but when the install gets up to installing the ".net 1" it stops.  :(

---

### Post by hikaricore on 2009-03-10
You may wanna check the info others have written on the WINE AppDB: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=107](http://appdb.winehq.org/objectManager.php?sClass=application&iId=107)
Between 2008 and 2009 there are 6 versions of Quicken, some seem to run better than others.

Another thing you may want to consider is running native accounting software such as GNUCash.

---

### Post by betrunkenaffe on 2009-03-10
Google Nola Pro, that may also do what you want. I've never used it but someone mentioned it.

QUickbooks installing into Linux sucks. From everything I've read, you'd have more success with turning water into wine...

---

### Post by Solorflare on 2009-03-10
> **hikaricore said:**
> You may wanna check the info others have written on the WINE AppDB: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=107](http://appdb.winehq.org/objectManager.php?sClass=application&iId=107)
Between 2008 and 2009 there are 6 versions of Quicken, some seem to run better than others.

Another thing you may want to consider is running native accounting software such as GNUCash.

Is GNUCash compatible with the Australian Tax System?

---

### Post by Solorflare on 2009-03-10
> **betrunkenaffe said:**
> Google Nola Pro, that may also do what you want. I've never used it but someone mentioned it.

QUickbooks installing into Linux sucks. From everything I've read, you'd have more success with turning water into wine...

Will have a look

---

### Post by joeandrews0826 on 2009-03-10
Could try running natively from windoze in Virtualbox.

Joe

---

### Post by old fert on 2009-03-10
If you figure it out, let me know.  I've only been using linux for about a month.  The high cost of qb and related support is what got me started looking for business software alternatives in Ubuntu.

GNU cash works well, but it is more equivalent to Quicken than qb.  NolaPro downloads and works well in Windows and looks like a heavy duty program.  To date, I haven't been able to get it to function in Linux (actually, I haven't been able to get it installed).  

I'm not too bright on installing software without package managers.  It would be great if we could make the switch to Linux, but the business software for dummies (me) just isn't out there yet.

---

### Post by betrunkenaffe on 2009-03-11
From what I read of Nola Pro, you need an Apache server set up on your machine and then you will be loading it from localhost (or the servername..).

How did you get it running on Windows without Apache?

---

### Post by old fert on 2009-03-12
I just downloaded and installed.  It installed apache and everything came up.  It is on my(dual boot) vista machine.

I guess I have to say I haven't got a clue.

---

### Post by yochaigal on 2009-03-16
You can get firefox to handle quickbooks online natively.

in linux or mac, install the user agent switcher from here:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

then go to tools > user agent switcher > options > options

then do add:

Description : Firefox 3 (Windows XP)

User Agent: Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6

App Name: Mozilla Firefox

App Version:  5.0 (Windows; en-US)

Platform:  Win32


Then switch to it from tools, and go

---

### Post by buldozerceto on 2009-03-16
you can install vmware player install xp and boot xp whenever you like and use your almost any windows software while on ubuntu.

---

### Post by desertboy on 2009-03-17
I have to use sage which doesn't work in wine and at the moment I have it booting into a virtual machine for sage only, I like the convenience but 3 times it's failed to boot and I've had to boot an earlier backup so if you do go the virtual machine route I would make sure I took daily USB backups.

As soon as I get 5 minutes I'm going to install windows just for sage as it's too important to me and the only reason I've found (For me personally) other than games to boot windows.

---

