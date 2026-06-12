---
title: "My Linux/Windows conundrum"
date: 2007-02-24
forum: The Cafe
---

### Post by zeroblitzt on 2007-02-24
Well, here I sit, not knowing what to do.


Linux has almost fully replaced my Windows set up. There are still a few choice things though (games, certain applications) that I can't replace (yet...). So, instead of just settling for having a dual boot, I looked into things like VMware. But this is where I hit a snag.


If I installed VMware and it ran totally fine, I think I'd be inclined to totally delete Windows. But I'm kind of nervous at going that far. I mean, what if theres a major breakdown in my Ubuntu box? I know you're probably thinking "the same thing can happen on Windows", its just its a little more nerveracking for me on Linux (i'm no n00b but im no expert either). 

And even if I didnt go that far and left it at a dual boot, I'd like to format my /dev/hdb1, which is 80 gigs of all my music and programs for Windows. That way I can free up more space for Linux programs and such.

I'm not sure what to do here. I don't need technical help, I need plain old psych. advice. What do you think I should do?

---

### Post by insane_alien on 2007-02-24
i'd say keep on dual booting. if you're not so confident on linux yet then just wait. took me months to fully go over to linux.

---

### Post by antenna on 2007-02-24
VMware works great, but Just be aware that 3D acceleration is not available in it so more than likely you still have to find a different solution for your games. 

Personally I got rid of Windows after about a month, and sure I wasn't an expert with Linux but I had the basics down, and could get online without a GUI, etc.  I don't think you have a whole lot to worry about, particularly if you have a Live CD around or some other means of connecting to the internet and so can find out how to fix major problems. 

Having said that, there's not much harm in dual booting.

---

### Post by chewearn on 2007-02-24
I have the same dilemma a while back, but after weighing the options, I go against dual boot.  There is just too much tinkering of partitions, mbr, etc required, especially when you need to reinstall Windows now and again.  In addition, there is also occasional ubuntu downtime after some borked kernel, video driver, etc updates. 

Instead, I settle for multiple harddisks; one for each OS, and another for data, physically swapping them when required.  Recently, I upgraded to a second PC (they are so cheap nowadays, as long as you avoid the latest and greatest).

---

### Post by zeroblitzt on 2007-02-24
Well, I told myself once I got a new PC I'd instantly put Ubuntu on there. It's just kind of tough now, seeing as im using my current PC.

---

### Post by aysiu on 2007-02-24
> **zeroblitzt said:**
> I mean, what if theres a major breakdown in my Ubuntu box? I know you're probably thinking "the same thing can happen on Windows", its just its a little more nerveracking for me on Linux (i'm no n00b but im no expert either).

I agree with antenna: > **antenna said:**
> I don't think you have a whole lot to worry about, particularly if you have a Live CD around As long as you have the Desktop CD around (also known as the live CD), then a crashed or broken-down Ubuntu installation shouldn't be a problem.

Just boot up the live CD, log on to the forums, and ask people how to fix it. If it can't be fixed for whatever reason, people on the forums can at least tell you how to save your data before you reinstall.

---

### Post by thomasaaron on 2007-02-24
I hear ya.

In my case, I had my whole life invested in Windows but wanted to go to Linux. I backed up all of my important stuff on an external hard drive and tried a dual boot.

Something went wrong and I lost Windows completely. I could find the key codes for my Microsoft Office CD's.

So, I just put myself on the fast track to learning linux, asked a LOT of questions on the forum, and now you couldn't pay me to return to Windows. Too much free software.

I was never really a gamer, so that wasn't an issue. And I've not really found anything missing in Linux that a) I could not find another way to accomplish, or b) I couldn't live without.

I make my living on my laptop with Ubuntu. No complaints whatsoever.

Maybe you should have an accident!

Best,
Tom

---

### Post by Medieval_Creations on 2007-02-24
Another app to look at is VirtualBox.  I've had better results with it than VMWare & it's opensource, which = free.  :)  I've gotten everything else to work no problems so far application wise. *(Dreamweaver, Office 2003, & PhotoShop CS)*

Thread: [http://www.ubuntuforums.org/showthread.php?t=338931](http://www.ubuntuforums.org/showthread.php?t=338931)
HomePage: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by The Noble on 2007-02-24
You could also try making a separate /home partition if you want. I myself prefered an extra partition that I mounted in /etc/fstab as /stuff. So even if my main system imploded, I can just install over the swap and /, while leaving the extra partition. Once you learn a little more about partitions and how you want your system set up, another partition will be second nature. So far, it has saved me over 6 hours every re/install.

---

### Post by Mateo on 2007-02-24
> **The Noble said:**
> You could also try making a separate /home partition if you want. I myself prefered an extra partition that I mounted in /etc/fstab as /stuff. So even if my main system imploded, I can just install over the swap and /, while leaving the extra partition. Once you learn a little more about partitions and how you want your system set up, another partition will be second nature. So far, it has saved me over 6 hours every re/install.

that's a good idea, but there are still a lot of stuff that gets stored in your hard drive  that isn't /home stuff.  like custom scripts that you place in /usr/bin/.  that can be a pain to hunt down all of those (plus any icons you might have put in /usr/share/pixmaps/ or /usr/share/icons/).  reinstalling is never hassle free, unfortunately.

---

