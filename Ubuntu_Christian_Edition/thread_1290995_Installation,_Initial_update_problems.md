---
title: "Installation, Initial update problems"
date: 2009-10-14
forum: Ubuntu Christian Edition
---

### Post by atyar on 2009-10-14
I had Linux Mint (also based on Ubuntu) running fine on my IBM Thinkpad T40 laptop, but when I came across Ubuntu CE, I wanted to try it.  The installation goes through like normal, but when I try to run the 'automated' updates to get it up-to-date, it fails to find a bunch of them.  I let it continue with what updates it had, rebooted, and tried the update again, but it continues to fail "to find" the remaining updates.  Any ideas??

Also, I was going to post about this last night from my laptop(at home), but when I tried to register, that over-zealous built-in internet filter blocked it, saying it fell under the category of pornography :confused:  Any ideas on that one?

Thanks!

---

### Post by david_kt on 2009-10-14
> **atyar said:**
> I had Linux Mint (also based on Ubuntu) running fine on my IBM Thinkpad T40 laptop, but when I came across Ubuntu CE, I wanted to try it.  The installation goes through like normal, but when I try to run the 'automated' updates to get it up-to-date, it fails to find a bunch of them.  I let it continue with what updates it had, rebooted, and tried the update again, but it continues to fail "to find" the remaining updates.  Any ideas??

Also, I was going to post about this last night from my laptop(at home), but when I tried to register, that over-zealous built-in internet filter blocked it, saying it fell under the category of pornography :confused:  Any ideas on that one?

Thanks!

How do you install it? Is it using ISO file? If it is using iso file, please follow below link to upgrade:

[http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)

If dansguardian is running, please stop it first using dansguardian gui to make sure all updates are completed. After that you should run dansguardian gui again and choose auto configuration.

DK

---

### Post by atyar on 2009-10-14
I did download the iso file yesterday and burn an installation cd.  Am I misunderstanding the 'convert' link - isn't that just for taking a standard ubuntu install and converting it to CE?  I downloaded the ce iso - so my desktop, etc., is already CE.

I did look for that filtering program in the menu, but couldn't find it.  Could you please give me some details on how to stop and/or preferably uninstall it? (this is my personal laptop - my kids never use it)

Thanks!

---

### Post by david_kt on 2009-10-14
> **atyar said:**
> I did download the iso file yesterday and burn an installation cd.  Am I misunderstanding the 'convert' link - isn't that just for taking a standard ubuntu install and converting it to CE?  I downloaded the ce iso - so my desktop, etc., is already CE.

I did look for that filtering program in the menu, but couldn't find it.  Could you please give me some details on how to stop and/or preferably uninstall it? (this is my personal laptop - my kids never use it)

Thanks!

To stop dansguardian:

```
System >> Administration >> Dansguardian GUI
```

key in your password when requested, and then choose stop dansguardian.

The iso file is beta release, I plan to release the production release soon. To convert from beta to production release, follow the instruction on the link. In addition to that, you should do also:

```
sudo apt-get dist-upgrade
```

DK

---

### Post by atyar on 2009-10-14
Got it - I'll give it a shot tonight and let you know...
Thanks!

---

### Post by atyar on 2009-10-14
distro-update did the trick....thanks!

---

