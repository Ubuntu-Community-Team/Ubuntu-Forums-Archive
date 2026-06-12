---
title: "Which to install.. Ubuntu 9.10 Alpha 6 or Windows 7?"
date: 2009-09-19
forum: The Cafe
---

### Post by gymophett on 2009-09-19
I have both the Ubuntu and Windows 7 cd's in front of me at the moment. Which should I install? Should I install Windows 7 running Ubuntu via virtualbox or vice versa? Thank you.

---

### Post by hoppipolla on 2009-09-19
I dunno man depends what you want from an OS :)

Personally, I would dual boot :)

---

### Post by nowin4me on 2009-09-19
...Your asking a Ubuntu forum.

I would say Ubuntu 9.10 Alpha 6 it need's as much help as it can get!
Windows 7 has finished it's BETA stages and it's just going into production while Ubuntu 9.10 is still being developed.

---

### Post by chriskin on 2009-09-19
in windows 7 i didn't find anything new (worthy at least)
in ubuntu 9.10 i got my camera working (it does't work on windows 7)

so i give a point to ubuntu

---

### Post by gymophett on 2009-09-19
I dont have my hard drives partitioned correctly. I have 2 partitions. One is a shared one. The other is a Windows Vista one. Should I shrink the Windows Vista one. Make an Ubuntu partition. Then dual boot?

---

### Post by gymophett on 2009-09-19
Also. Is Ubuntu Alpha 6 stable enough yet? When beta is released, do I just do an upgrade or do I have to reinstall all over again?

---

### Post by hoppipolla on 2009-09-19
> **gymophett said:**
> I dont have my hard drives partitioned correctly. I have 2 partitions. One is a shared one. The other is a Windows Vista one. Should I shrink the Windows Vista one. Make an Ubuntu partition. Then dual boot?

Would you rather have Vista than 7 on there?

> **gymophett said:**
> Also. Is Ubuntu Alpha 6 stable enough yet? When beta is released, do I just do an upgrade or do I have to reinstall all over again?

I don't think it will be AMAZINGLY stable...

It should all upgrade fine though :)

If it were me I'd just use Jaunty!

---

### Post by chriskin on 2009-09-19
> **gymophett said:**
> I dont have my hard drives partitioned correctly. I have 2 partitions. One is a shared one. The other is a Windows Vista one. Should I shrink the Windows Vista one. Make an Ubuntu partition. Then dual boot?

that sounds good enough, but i would propose defragmenting first. shrinking would take a lot less time if you defragment vista. 

also, vista has a known bug of messing up icons after shrinking. it hasn't happened to me but i have seen it happening more than once in other computers - watch out for this one

---

### Post by NormanFLinux on 2009-09-19
I'd wait til next month to install Karmic Koala. The alpha still has bugs in it.

---

### Post by Bigtime_Scrub on 2009-09-19
Why compromise? Just dual boot. I would install Windows 7 and wait until karmic is released and then I would it install that side by side.

---

### Post by hoppipolla on 2009-09-19
> **Bigtime_Scrub said:**
> Why compromise? Just dual boot. I would install Windows 7 and wait until karmic is released and then I would it install that side by side.

Actually yeah maybe waiting for Karmic would be good as opposed to putting Jaunty on there, as for one thing then you would get ext4, which is something I missed out on by going for Jaunty.

---

### Post by gymophett on 2009-09-19
But I'm a person who likes to test! :) I'm not patient enough either.
So I'll do all the partitioning tonight, Install Karmic on one partition, then tomorrow, upgrade to Windows 7 on my Vista partition. Sounds good! :D

---

### Post by hoppipolla on 2009-09-19
> **gymophett said:**
> But I'm a person who likes to test! :) I'm not patient enough either.
So I'll do all the partitioning tonight, Install Karmic on one partition, then tomorrow, upgrade to Windows 7 on my Vista partition. Sounds good! :D

Good bet :)

Just be careful with ol' Karmic! Hope it works for you ^_^

---

### Post by HappyFeet on 2009-09-19
> **hoppipolla said:**
> as for one thing then you would get ext4, which is something I missed out on by going for Jaunty.

If you do manual partition, ext4 is one of the options in jaunty. ;)

---

### Post by purgatori on 2009-09-19
I don't really understand the dilemma.... but if you play games on your PC, then installing Windows 7 and running Ubuntu on top of it probably makes more sense than going the other way.

---

### Post by hoppipolla on 2009-09-19
> **HappyFeet said:**
> If you do manual partition, ext4 is one of the options in jaunty. ;)

I tried that, but I really didn't see the option. I could have been missing something but I'm fairly sure ext4 in Ubuntu is new for Karmic.

---

### Post by HappyFeet on 2009-09-19
> **gymophett said:**
> Also. Is Ubuntu Alpha 6 stable enough yet?

I'm using it right now with no problems *yet*, but you never know. But I have 2 drives going, one with jaunty (production) and the other karmic (testing/bug reporting). I would wait until the beta comes out then do a clean install if I were you.

---

### Post by HappyFeet on 2009-09-19
> **hoppipolla said:**
> I tried that, but I really didn't see the option. **I could have been missing something** but I'm fairly sure ext4 in Ubuntu is new for Karmic.

Yes, you *did* miss it, because I'm using ext4 in jaunty.

---

### Post by hoppipolla on 2009-09-19
> **HappyFeet said:**
> Yes, you *did* miss it, because I'm using ext4 in jaunty.

Damn! I would have used that lol

---

### Post by HappyFeet on 2009-09-19
Here's my fstab in jaunty:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=66dacb76-4b2a-4025-90a1-e9a8a56a428b /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff877344-ca9f-4113-b217-8cbc5cf62a4f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by HappyFeet on 2009-09-19
> **hoppipolla said:**
> Damn! I would have used that lol

You missed out on the extra speed and efficiency. :P That, with 64bit, is unbeatable.

---

### Post by hoppipolla on 2009-09-19
> **HappyFeet said:**
> You missed out on the extra speed and efficiency. :P That, with 64bit, is unbeatable.

Don't worry I don't think I'm gonna lose sleep or anything xD

Would have been nice to have though :)

---

### Post by gymophett on 2009-09-19
> **hoppipolla said:**
> Don't worry I don't think I'm gonna lose sleep or anything xD

Would have been nice to have though :)

You can actually convert to EXT4 after installing Jaunty. I did previously. Google it.

---

### Post by stmiller on 2009-09-19
I wouldn't use ext4 on anything less than a 2.6.30 kernel.

---

### Post by misfitpierce on 2009-09-19
Depends how much you choose to use windows apps over Ubuntu apps. Honestly there is an app for everything in Ubuntu, no slow down from malware and or viruses/spyware/adware... and easier to maintain ubuntu. So Ubuntu has better infrastructure but windows is needed by some people reliant upon windows apps and/or games. I dont know how reliant you are on those. If not then I say vice versa with Ubuntu as main OS and dual booting win7 or virtual machining Win7.

---

### Post by Exodist on 2009-09-19
I would go with Ubuntu 9.10alpha6 and help test the distro. Mind you its going to be unstable but testing it and submitting every little issue and bug you find helps us all and it also can be self rewarding when 9.10 comes out rock stable.

But if you want to test Win7 then all your doing is helping capitalist billionaires get more rich while us less then financially gifted keep getting poorer. Yes I know Mark has plenty of cash but hes not greedy like that ******* Steve Ballmer.

So it boils down to moral. Ubuntu or M$.

---

### Post by Bucky Ball on 2009-09-19
Alpha 6 not stable. Karmic is testing, not released yet. If you want your system to break with updates (and sometimes get fixed) and report your adventure then go for it.

If you want a stable system then 8.04 LTS (rock solid) or 9.04 (getting there).

---

### Post by Woormy on 2009-09-19
> **Exodist said:**
> But if you want to test Win7 then all your doing is helping capitalist billionaires get more rich while us less then financially gifted keep getting poorer. Yes I know Mark has plenty of cash but hes not greedy like that ******* Steve Ballmer.

So it boils down to moral. Ubuntu or M$.

By that thinking he should install Ubuntu, but not on a computer because computer companies are run by capitalist billionaires.

---

### Post by Exodist on 2009-09-19
> **Woormy said:**
> By that thinking he should install Ubuntu, but not on a computer because computer companies are run by capitalist billionaires.
I have my Ubuntu running on a cornflake box.. :-)

Sad but true you are just as right. But to the best of my knowledge I have never read anything about the CEO at biostar, amd, coolermaster, PNY or creative labs ever choking a worker out because they put in a two week notice. Mind you I have no issues with Steve Jobs, but Steve Ballmer is just a rich fat disgusting pig that hell will have to construct a special place for when he dies. I also have no issues with Bill Gates, mind you he is just a spokemen for M$ now and not the CEO.

If you support windows you support this fatass with the tung sticking out!
[http://www.google.com/imgres?imgurl=http://www.maximumpc.com/files/u46168/ballmer.jpg&imgrefurl=http://www.maximumpc.com/tags/steve_ballmer&h=400&w=660&sz=45&tbnid=XFiDJ97wMzczuM:&tbnh=84&tbnw=138&prev=/images%3Fq%3Dsteve%2Bballmer&usg=__qOY9PLSmFtHd5rfovH3OuFuIJSI=&ei=6aK1SqnbNamw8QaP0MmTDw&sa=X&oi=image_result&resnum=7&ct=image](http://www.google.com/imgres?imgurl=http://www.maximumpc.com/files/u46168/ballmer.jpg&imgrefurl=http://www.maximumpc.com/tags/steve_ballmer&h=400&w=660&sz=45&tbnid=XFiDJ97wMzczuM:&tbnh=84&tbnw=138&prev=/images%3Fq%3Dsteve%2Bballmer&usg=__qOY9PLSmFtHd5rfovH3OuFuIJSI=&ei=6aK1SqnbNamw8QaP0MmTDw&sa=X&oi=image_result&resnum=7&ct=image)

---

