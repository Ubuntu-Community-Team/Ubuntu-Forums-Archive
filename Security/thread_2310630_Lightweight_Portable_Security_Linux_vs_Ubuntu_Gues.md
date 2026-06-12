---
title: "Lightweight Portable Security Linux vs Ubuntu Guest Session"
date: 2016-01-20
forum: Security
---

### Post by olie2 on 2016-01-20
Hello all, 

In terms of doing financial transactions online, I've heard that it is usually better to use a LiveCD/USB to perform any transactions to prevent access to data.  Is there a significant difference between using a hardened liveCD/USB like LPS (linux distro issued by the US Government) versus using the Guest Session on Ubuntu?  Both erase the session data upon logging out, however LPS runs in RAM and I'm not sure if the Guest Session does or does not, but I believe that the data is erased anyway.

Thanks all.

---

### Post by patrikmellq on 2016-01-21
I just want to stay thank you for mention LPS linux distribution :-)

 Cheers

---

### Post by bashiergui on 2016-01-21
The drawback with live CDs is that they can't be updated. IMO the biggest threats for online banking are:

[LIST]
[*]Banking from an malware-infected machine (if you're using linux then the risk is very minimal)
[*]Clicking on a link to your bank in an email (Don't. Ever.)
[*]Surfing to your bank site while you're surfing all over the internet. Clear your internet history & cookies before banking. Then when done, clear history & cookie again.
[*]Banking on public wifi. If you have no choice, at least use a VPN when on public wifi.
[/LIST]
Anything more is superfluous.

---

### Post by olie2 on 2016-01-23
> **bashiergui said:**
> The drawback with live CDs is that they can't be updated. IMO the biggest threats for online banking are:

[LIST]
[*]Banking from an malware-infected machine (if you're using linux then the risk is very minimal) 
[*]Clicking on a link to your bank in an email (Don't. Ever.) 
[*]Surfing to your bank site while you're surfing all over the internet. Clear your internet history & cookies before banking. Then when done, clear history & cookie again. 
[*]Banking on public wifi. If you have no choice, at least use a VPN when on public wifi. 
[/LIST]
Anything more is superfluous.

Thanks for the response.  I'd like to keep this discussion going if that's alright...


[LIST]
[*]The live CD for LPS is updated approximately every quarter.  In December 2015 it was updated faster, I would guess because of a new security update.  An update every quarter/3 months is not as good as say an update as soon as the bug/hole is found.  I will give you that.
[*]Your first point about banking on a malware-infected machine is not an issue with a live distro, since it runs in RAM.  That being said, the ability to update the system is the major flaw.
[*]If you simply login to a session on a live CD and go straight to your financial institution's website, doesn't that minimize the chance of attack via one of the security holes?
[*]Since it is a minimal live distro, aren't there less security flaws (theoretically) simply because of the lesser amount of programs within the system?
[*]Again, what is the difference between the guest session on Ubuntu vs a live CD session?  Is there no way to retrieve data from a guest session in Ubuntu?
[/LIST]

As an alternative to my points, could someone simply do a minimal Debian or Ubuntu install, secure the firewall, block ssh connections, and then install a web browser such as chromium or firefox?  Maybe a stable window manager or desktop environment as well?  And then use that computer as a standalone financial computer?

Thanks

---

### Post by Nuno_Abreu on 2016-01-23
Live CDs save data temporarily on RAM, being volatile - this is a less of a security risk, because data can be unciphered if saved on a drive without a strong encryption.
Now, like said before, this method has the problem of not receiving updates regularly, unless you try encrypted persistence with LUKS.

There are a lot of tutorials for it, and most of the Debian based distros support this feature. This is the method for the common known** Kali Linux** distro (the process is the same or identical):
[http://docs.kali.org/downloading/kali-linux-live-usb-persistence](http://docs.kali.org/downloading/kali-linux-live-usb-persistence)

---

### Post by sudodus on 2016-01-23
If you want the best of a live system and a daily updated system, you can download / update the daily iso file (with rsync or zsync) of the developing Ubuntu version (now Xenial Xerus to become 16.04 LTS in April).

+ it will be up to date

+ it is live

- sometimes it will be broken (not working) because of conflicts between new versions of some program packages. (This happens, but very seldom, less than once per month, and it is likely to be fixed within a day or two. When it happens, you can use some other version of a live system.)

- updating/upgrading and rebooting takes longer than the corresponding update/upgrade in an installed system, but still within a few minutes if you have a fast internet connection. A fast USB 3 pendrive makes things faster even when connected to a USB 2 port.

-o-

See the following link. Notice that the flavour Lubuntu is by far the lightest one, and Xubuntu and Ubuntu MATE are medium light, while the other flavours have more demanding and therefore slower desktop environments. Lubuntu has the smallest iso file, which makes it easiest and fastest to rsync to keep up to date.

If you get the system according to the following link

[A compressed image file with a persistent live system of Lubuntu 14.04.3 LTS (32-bit) and mkusb version 10.4](http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13399888#post13399888)

you can get it up to date inside itself (booted from its own USB pendrive) by the following commands

```
cd /isodevice
sudo -H ./links2check    # to ***[COLOR="#0000FF"]get[/COLOR] a new iso file*** (for example Lubuntu Xenial), and ***in a second run to [COLOR="#0000FF"]link[/COLOR] to it***.
sudo -H ./links2update   # to ***[COLOR="#0000FF"]update[/COLOR]*** to a new daily version of an existing iso file (for example Lubuntu Xenial)
```

Reboot and select a live session (not persistent live) if you want high security for financial transactions online!

-o-

When you find a bug, you are very welcome to report it at Launchpad and in the iso tracker - this way you will 'pay back' by helping us develop the new version :-)

[https://launchpad.net/](https://launchpad.net/)

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

---

### Post by sudodus on 2016-01-23
> **olie2 said:**
> 
[*]Again, what is the difference between the guest session on Ubuntu vs a live CD session?  Is there no way to retrieve data from a guest session in Ubuntu?
[/LIST]


The data of the guest session are deleted at log out. Maybe they can be retrieved by advanced methods. I think it is rather safe, but not as safe as a live system.

But remember that ***most of us use standard installed systems for banking and similar tasks***. If we avoid porn and other dangerous websites, avoid javascript except in trusted websites, and avoid clicking on attached files in emails unless we know what it is, it should be rather safe, definitely safer than using mobile phones, which is rather common today. (A lot of the malware attacks Windows, but a fair share attacks via the web browser and is independent of the operating system.)

---

### Post by bashiergui on 2016-01-23
> If you simply login to a session on a live CD and go straight to your financial institution's website, doesn't that minimize the chance of attack via one of the security holes?[/COLOR]Yes unless you're on public wifi.> Since it is a minimal live distro, aren't there less security flaws (theoretically) simply because of the lesser amount of programs within the system?Debatable if the minimal software includes flash. And what vulnerabilities there are that haven't been patched. > Again, what is the difference between the guest session on Ubuntu vs a live CD session? Is there no way to retrieve data from a guest session in Ubuntu?
yes there is. Guest sessions log everything a regular user does.Browsers have the same data especially if not private browsing.

---

### Post by patrikmellq on 2016-01-24
Help me understand:

1) are we talking about general banking security for home users when paying bills each month using the internet bank? 
2) or are we talking about banking when trading stocks and deal with larger amount of money using trade-company-bank-online? 

If (1) then you are saying is not safe using your home ubuntu desktop system to pay your bills each month! that sucks big time.
I mean i run UFW, VPN, LOGWATCH and been feeling pretty safe using internet banking online paying my bills each month.
If i am wrong with my assumptions i will start using LPS distro ....

Cheers

---

### Post by sudodus on 2016-01-24
***I think*** an installed Ubuntu system is safe enough for paying bills each month using the internet bank, if you avoid 'risky' browsing and keep your system up to date (install the security updates when they arrive). I would not use a system that has passed end of life, and I avoid 'risky' browsing.

See this link (a little old now, but the advice is generally valid), [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Nuno_Abreu on 2016-01-25
> **sudodus said:**
> If you want the best of a live system and a daily updated system, you can download / update the daily iso file (with rsync or zsync) of the developing Ubuntu version (now Xenial Xerus to become 16.04 LTS in April).

+ it will be up to date

+ it is live

- sometimes it will be broken (not working) because of conflicts between new versions of some program packages. (This happens, but very seldom, less than once per month, and it is likely to be fixed within a day or two. When it happens, you can use some other version of a live system.)

- updating/upgrading and rebooting takes longer than the corresponding update/upgrade in an installed system, but still within a few minutes if you have a fast internet connection. A fast USB 3 pendrive makes things faster even when connected to a USB 2 port.

-o-

See the following link. Notice that the flavour Lubuntu is by far the lightest one, and Xubuntu and Ubuntu MATE are medium light, while the other flavours have more demanding and therefore slower desktop environments. Lubuntu has the smallest iso file, which makes it easiest and fastest to rsync to keep up to date.

If you get the system according to the following link

[A compressed image file with a persistent live system of Lubuntu 14.04.3 LTS (32-bit) and mkusb version 10.4]("http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13399888#post13399888")

you can get it up to date inside itself (booted from its own USB pendrive) by the following commands

```
cd /isodevice
sudo -H ./links2check    # to ***[COLOR=#0000FF]get[/COLOR] a new iso file*** (for example Lubuntu Xenial), and ***in a second run to [COLOR=#0000FF]link[/COLOR] to it***.
sudo -H ./links2update   # to ***[COLOR=#0000FF]update[/COLOR]*** to a new daily version of an existing iso file (for example Lubuntu Xenial)
```

Reboot and select a live session (not persistent live) if you want high security for financial transactions online!

-o-

When you find a bug, you are very welcome to report it at Launchpad and in the iso tracker - this way you will 'pay back' by helping us develop the new version :-)

[https://launchpad.net/](https://launchpad.net/)

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

This is very interesting - thank you for the share!

Would this be any faster than persistence, even on a USB 3.0? I still have bottlenecks with a speedy USB 3.0 flash drive and I would like to know it. And is this only applied to Debian systems or Linux in general?

---

### Post by sudodus on 2016-01-25
Live-only is faster than persistent live. If there is enough RAM, you can use the boot option **toram**, which makes the booting slower, but after that the system will be very fast. But I can't tell you if it will be fast enough for you with a fast USB 3 pendrive (for example Sandisk Extreme). Try it :-)

If you want a really fast system, you can connect an SSD via USB 3 or eSATA or even run it via an internal SATA connection.

-o-

The particular system, that I made is designed for Ubuntu and the Ubuntu flavours, but the method is general, and you can make it work with other linux distros too. You have to find the web address for the daily iso file you want, and you have to modify the boot system (the grub.cfg file and maybe some automation of the daily modification with a shell-script).

---

