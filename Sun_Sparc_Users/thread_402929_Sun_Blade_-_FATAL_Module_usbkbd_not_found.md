---
title: "Sun Blade - FATAL: Module usbkbd not found"
date: 2007-04-06
forum: Sun Sparc Users
---

### Post by incubus on 2007-04-06
Hi everybody,

Long story short, somehow I received a Sun Blade 150 to play with.  I downloaded the beta image for Feisty Fawn and after going through the usual tricks, including cold boot and ide=nodma, I finally get to the installation screen.

However, I get these error messages:
```

FATAL: Module usbkbd not found.                                                 
FATAL: Module usbhid not found.                                                 
FATAL: Module usbserial not found. 

```

Unfortunately I only have a USB keyboard and it stops working.  So I can't select anything and can't install Ubuntu.  I googled around and I found another person with a similar problem:
[http://drwetter.org/coolthreads/t2000.Ubuntu_vs_Solaris10_1.html](http://drwetter.org/coolthreads/t2000.Ubuntu_vs_Solaris10_1.html)

Do you have any suggestion before I try to install via network or try Edgy?

Thanks,
incubus

PS: It doesn't seem to be a CD problem.  I checked the md5 hash and burned at 4x.

---

### Post by incubus on 2007-04-07
I'd like to add that I've installed Solaris 10 and upgraded OBP.  Still no go.

I tried Edgy, but it's actually worse.  The image starts to load, there's a screen refresh (as if it was changing resolution), and it hangs up there.  No error message at all.

Is netinstall my only option left?

I'm surprised nobody except for me had this problem.

incubus

---

### Post by incubus on 2007-04-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/99790](https://bugs.launchpad.net/ubuntu/+bug/99790) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ah, I found another "ubuntero" with this problem:

[https://bugs.launchpad.net/ubuntu/+bug/99790](https://bugs.launchpad.net/ubuntu/+bug/99790)

I'll post there.  I hope somebody comes up with an idea.

incubus

---

### Post by incubus on 2007-04-08
As I mentioned on launchpad, I dist-upgraded from Dapper to Feisty and I must say I'm surprised the process wasn't as painful as I was expecting.  I was able to do this because the keyboard was working on Dapper.

Three big issues caught my attention:
1. A configuration menu asks me for the keyboard model.  I have almost Zero experience with Sun machines, so I thought I had to choose Sun Type 4 or 5.  Alas, bad idea.  Doing that was giving me "can not found (sic) sun5 ..." error messages.  By the way, we have to correct the English in that message.  The solution was to run:
```

$ sudo dpkg-reconfigure console-setup

```
and revert to Generic PC104 Keys

2. Scary errors about mdadm.  In my case, I don't use it, so I uninstalled it and upgraded initramfs.  If you search the forums, you will find some horror stories about that.

3. The worst one was this: after booting, I had no TTYs.  That's right.  It's a known bug and you have to manually edit and correct  the last line in:
```

/etc/event.d/tty1 # from 1 to 6

```

Unfortunately, I still have the same keyboard problem: it simply doesn't work.  I suspect, then, it's really related to the new kernel modules, not just to the Ubuntu installer.  I'm thinking about compiling the kernel and modules now.

incubus

---

### Post by sandpiper on 2007-04-11
FYI: Came across this info held in the directory /etc/modprobe.d in a file called "Blacklist"

"usbkbd and usbmouse are blacklisted. HID drivers are preferred"

This may explain the FATAL error message because presumably blacklisting means "not allowed". However I am only a linux newbie so not at all sure.. Chris

---

### Post by ubu_for_umm on 2007-06-14
I am replying while my installation proceeds ... am trying to install 7.04 on a Sun Blade 150. Installation actually proceeded well after the usual process of updating the OBP and ide=nodma. Got the point where I had to select a keyboard. Now I own a Sun 6 USB keyboard and the only "Sun" choices were Sun 4 and Sun 5. The moron that I am, I selected Sun 5 thinking "hey thats as close as I can get". Needless to say, wierd characters were appearing when it asked me for choices and soon the installation got stuck while "configuring usbutils". Anyway, after a cold boot and resttarting the installation, I came back to the keyboard selection screen. This time, I searched for a specific "USB" option and selected "Dell USB Multimedia Keyboard". 

Well ... currently, installation is complete, the machine rebooted fine, the keyboard worked fine during the installation process and I am stuck at the "Loading please wait ..." screen.

:popcorn:

---

### Post by jdeisenberg on 2007-06-14
>>Now I own a Sun 6 USB keyboard and the only "Sun" choices were Sun 4 and Sun 5.
>> The moron that I am, I selected Sun 5 thinking "hey thats as close as I can get".

Try choosing PC-104 key; that worked for me and a lot of other people.  I know it sounds like it shouldn't work, but it does.

---

