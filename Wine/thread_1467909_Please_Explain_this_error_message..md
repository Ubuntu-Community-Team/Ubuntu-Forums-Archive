---
title: "Please Explain this error message."
date: 2010-05-01
forum: Wine
---

### Post by xDarkicex on 2010-05-01
```
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

I do not know what to do to fix this.

What went wrong
I installed the latest Update to wine thinking all would be good, then I found out I needed 1.1.17 to properly run Photoshop CS4, so I removed it from my system using the software manager, then installed the older AMD64bit 1.1.17 from here
```
http://wine.budgetdedicated.com/archive/index.html
```
Which was going fine but froze halfway through install Mainly I think because I had way to much stuff going on at one time form my laptop. 

So then to night I get home boot up and had a big red warning button on taskbar saying to run package manager update it shows wine 1.1.43*I think. Is broken So I removed it no problem but when I tried replacing it thats when I got the install error.

hope thats enough details.

---

### Post by P4man on 2010-05-01
Its not really an error, more a warning that it can not verify the signature. Either because you didnt import the key of that repository (from medibuntu) or because the keyserver is overloaded. The only effect is that ubuntu can not guarantee the download has not been tampered with.

Try this:

```
sudo apt-get install medibuntu-keyring
sudo apt-get update
```

Should take care of it, unless medibuntu's keyserver is not available (which may well be possible with a gazillion people installing Lucid and adding the medibuntu repository).

BTW, photoshop CS4 really doesnt run well on wine. I would strongly suggest you give gimp a fair chance.

---

### Post by xDarkicex on 2010-05-01
I have Used GIMP I Really hate it plus I spent 400$ on Photoshop but I can live with out It on my laptop.

And I tried running said command and got this error.
```
[B]xdarkicex@ubuntu:~$ sudo apt-get install medibuntu-keyring
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
[/B]

---

### Post by P4man on 2010-05-01
You have to close synaptic / software center or any other program that is locking dpkg. Then try again.

But really, photoshop on ubuntu is not going to give very satisfactory results, if you can get it to work at all. If you just "hate" gimp because of the interface, try 2.7 which has a unified interface like photoshop. If you gotta use photoshop, use it on windows, thats my advice.

---

### Post by xDarkicex on 2010-05-01
No I hate Gimp because I found it seriously lacked the Filters, masking, and general graphic editing ability of Photoshop plus I am just used to Ps been using it since Ps7 so yeah sort of bias I guess though I haven't tried out Gimp for like 4 years.

Thanks I just choose to uninstall Wine and be rid of the problem, and Run Ps on my Win7 partition, thanks for helping me not waste my time with this.

---

### Post by P4man on 2010-05-01
If you have enough RAM, you may want to run photoshop on a virtualmachine that has  a windows guest installed. That does work fairly well and avoids dual booting.

---

### Post by xDarkicex on 2010-05-01
only 1GB here not even close, side question whats root?
I got this when trying to install GIMP
```
xdarkicex@ubuntu:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

---

### Post by lisati on 2010-05-01
> **xDarkicex said:**
> only 1GB here not even close, side question whats root?
I got this when trying to install GIMP
```
xdarkicex@ubuntu:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

Use **sudo:**
```
sudo apt-get install gimp
```

For more information about sudo, see here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by xDarkicex on 2010-05-01
Wow Thanks Worked Perfectly I will read that along with my new Books Linux Bible 2009, Wiley Ubuntu Linux secrets and Using Linux Book hopefully by the end of this I will not be such a gear noob, anyway Thanks you guys are extremely helpful way better then windows tech support.

---

### Post by P4man on 2010-05-01
those books are outdated (and/or not ubuntu specific) As books about computers so often are. May I strongly recommend the newly released ubuntu manual:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Its excellent for new users. you can buy a hardcopy for $10 and support ubuntu. or just use the PDF for free.

---

### Post by xDarkicex on 2010-05-01
P4man Thanks for the Tip, and yes they are outdated but I still hope they can teach the basics, I will check out the Ubuntu Manuel Thanks.

---

