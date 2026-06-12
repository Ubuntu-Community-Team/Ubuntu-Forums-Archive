---
title: "System 76 Laptop Drivers in HH"
date: 2008-08-17
forum: System76 Support
---

### Post by dmengum on 2008-08-17
When I upgraded to Hardy Heron my sound and optical drive drivers stopped working.  Is there a new way to get at the system 76 drivers?  I am operating currently under 8.04 Ubuntu.

Thank you for any help
David

---

### Post by thomasaaron on 2008-08-18
From a command line, enter:
sudo wget [http://planet76.com/repositories/system76-driver-2.2.2.deb](http://planet76.com/repositories/system76-driver-2.2.2.deb)
sudo dpkg -i system76-driver-2.2.2.deb

Then go to System > Administration > System 76 Driver
Click the restore tab and restore button.

---

### Post by dmengum on 2008-08-23
thank you for your response.  when I enter command into terminal I receive the below error message.  Did I do something wrong?

--20:41:49--  [http://planet76.com/repositories/sys...iver-2.2.2.deb](http://planet76.com/repositories/sys...iver-2.2.2.deb)
           => `sys...iver-2.2.2.deb'
Resolving planet76.com... 207.57.2.228
Connecting to planet76.com|207.57.2.228|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:41:49 ERROR 404: Not Found.

---

### Post by williumbillium on 2008-08-24
It looks like the url was reformatted when Thomas posted it.  The correct command should be:

```
sudo wget http://planet76.com/repositories/system76-driver-2.2.2.deb
```

---

### Post by thomasaaron on 2008-08-24
Thanks, williumbillium.

I hate it when it does that.

---

### Post by dmengum on 2008-08-24
Thank you for the new address.  I received no errors but no results as to funtionality of sound or cd drives.  Any guesses?

---

### Post by thomasaaron on 2008-08-25
Actually, yes.

We've seen this before in the past. When upgrading from Feisty to Gutsy, the problem was practically epidemic. We only saw a few cases of it from Gutsy to Hardy.

It seems that there is a bug of some kind in Update Manager that hoses the alsa modules and the cd drive. The only real cure we ever found was a clean install. Once the basic install was finished, we had them update with...

sudo apt-get update && sudo apt-get --assume-yes dist-upgrade

...from the command line.

---

### Post by dmengum on 2008-09-05
I have finally backed up my home directory, can some one point me to a guide to do a clean install?  Googling about seems to not have pointed to a clear guide yet.

---

### Post by darkknight045 on 2008-09-08
Get yourself a copy of the Live CD from Ubuntu.com; pop it in, and boot!

From there select either Install Ubuntu or enter the live environment.  I reccomend the latter as it allows you to test to make sure everything is working.  Once you are ready double-click install and follow the guided process.

---

### Post by thomasaaron on 2008-09-08
If you want to send an email to support(at)system76(dot)com, I'll send you full written instructions (including installing and running the System 76 driver).

---

