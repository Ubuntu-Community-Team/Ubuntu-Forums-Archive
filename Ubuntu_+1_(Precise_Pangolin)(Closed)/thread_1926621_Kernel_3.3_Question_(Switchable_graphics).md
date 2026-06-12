---
title: "Kernel 3.3 Question (Switchable graphics)"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jackmusick on 2012-02-16
Hey guys,

Sorry if I'm asking in the wrong forum, but I have a quick question about the 3.3 kernel that (I hear) is supposed to be released in April. 

Well, I've heard here and there that 3.3 is supposed to fix a bunch of power management issues and support switchable graphics much better. I was wondering if anyone could elaborate on that.

See, the problem for Linux and me is that I like it, but it doesn't like my Radeon HD 6630M card very much. The bigger issue is that Dell doesn't offer a bios that lets me switch to that permanently so I can use the Catalyst driver.

If anyone can elaborate on how 3.3 supports switchable graphics (if it does at all) and maybe even explain to me how it works, that would be sweet. I'd be forever grateful. Heck, if you have time and know of a solution, let me know how I can get my card working in my machine with straight 11.10. I'm on a Vostro 3450, by the way.


Thanks!!

---

### Post by dino99 on 2012-02-16
[http://askubuntu.com/questions/102500/vgaswitcheroo-with-kernel-3-3](http://askubuntu.com/questions/102500/vgaswitcheroo-with-kernel-3-3)
[http://ubuntuforums.org/showthread.php?t=1911985](http://ubuntuforums.org/showthread.php?t=1911985)
[https://lkml.org/lkml/2012/2/8/517](https://lkml.org/lkml/2012/2/8/517)

---

### Post by jackmusick on 2012-02-16
Yeah, I've seen that link but that more or less just says that someone is having a problem using switcheroo in 3.3, not what 3.3 is supposed to do to address the switchable graphics problem.

I'm wanting to know what the goal is for 3.3 in addressing switchable graphics. Is it just a more advanced switcheroo that I have to command then restart my x server, or is it a whole new solution to integrate the technology into the kernel?

---

### Post by cariboo on 2012-02-16
What you are asking, is a beyond what this sub-forum is for. For more info on hybrid graphics, have a look [here]("https://launchpad.net/~hybrid-graphics-linux")

---

### Post by kaldor on 2012-02-16
Just a note about how Ubuntu works with kernel stuff. 

Even though Ubuntu will use 3.2 for the LTS, a lot of things will get backported. I am unsure whether or not the graphics stuff will be, but new hardware support does get backported. Don't let the title of the kernel fool you :)

---

### Post by jackmusick on 2012-02-16
So you're saying that the features of 3.3 will probably be ported to 3.2?

---

### Post by kaldor on 2012-02-16
Not all, but some will. 

For example, wireless support for some devices was backported to Natty after I bought this PC. I bought a PC in July and had no wireless. By August the kernel was updated with Linux 3.0 wireless support on Natty's 2.6.38 kernel. 

Also, my laptop's webcam didn't work on Lucid. By 10.04.2 it worked out of the box due to kernel updates.

Since 12.04 is going to be an LTS I think that hardware support is going to be more important than regular releases.

---

### Post by jackmusick on 2012-02-16
Very nice! I look forward to using it... I'll be setting up a dual boot environment tonight so I can keep using Windows for work and get familiar with Linux again. Really excited to join the community. The Official Ubuntu Server book I bought on my Nook has got me pumped :-)

Thanks for all of your help! I hope to join the development soon.

---

### Post by kaldor on 2012-02-16
> **jackmusick said:**
> Very nice! I look forward to using it... I'll be setting up a dual boot environment tonight so I can keep using Windows for work and get familiar with Linux again. Really excited to join the community. The Official Ubuntu Server book I bought on my Nook has got me pumped :-)

Thanks for all of your help! I hope to join the development soon.

This is a development release, so maybe a dual boot won't be the best idea. If you want to get more familiar with linux, install Precise inside Virtualbox on Windows. This pretty much eliminates any dangers of dual booting (especially with a development release). 

Once you feel competent enough (or once Precise hits Beta) then dual booting would probably be less daunting. However, if you want to dive right in then that's great too :)

---

### Post by jackmusick on 2012-02-16
Ah. Sorry, I meant that I'm going to boot into 11.10. I posted this thread in this section because it was about 3.3 and I thought this would be the place to post that question. :)

---

### Post by Gregory Lee on 2012-02-16
> **jackmusick said:**
> 
See, the problem for Linux and me is that I like it, but it doesn't like my Radeon HD 6630M card very much.
So, you're not using Ubuntu 12.04, is that right?  I don't know anything about the kernel and switchable graphics, but it might be relevant that Ubuntu 11.10 would not boot up for me because, probably, it didn't know what to do about my Radeon HD 6650D card.  However, I was able to boot up and install 12.04, so maybe it would be worth your time to try out 12.04, if you haven't done that yet.  (But my machine is HP, not Dell.)

---

### Post by jackmusick on 2012-02-17
Actually, I just installed 11.10 and updated to 12.04. It was really buggy, of course and I was still able to see my environment, but I couldn't switch to the ATI card. If I take this to the next step, I'll be installing an open source driver and trying out switcheroo. However, I assume that the performance won't be great and therefor won't be able to use Ubuntu as a desktop OS full time. So, I'll either buy a cheapo laptop just for Ubuntu that's compatible or suffer through VBox. :)

---

### Post by ELD on 2012-02-17
I would keep an eye out on The Bumblebee Project, they are the main ones working on hybrid graphics support, they are the ones who got this into the Kernel as it was part of their project to behin with.
 
They currently only supporting switching from intel to nvidia but i beleive they are working on AMD support too.
 
I use TBP on my laptop as it uses nvidia Optimus and it works flawlessly.

---

### Post by lucazade on 2012-02-17
> **ELD said:**
> I would keep an eye out on The Bumblebee Project, they are the main ones working on hybrid graphics support, they are the ones who got this into the Kernel as it was part of their project to behin with.
 
They currently only supporting switching from intel to nvidia but i beleive they are working on AMD support too.
 
I use TBP on my laptop as it uses nvidia Optimus and it works flawlessly.

It would work flawlessly if I could use the nvidia card for both gnome-shell and unity-3d.. instead i have to employ the intel one.. grrr!

---

### Post by Alexislavie on 2012-02-23
Check this post : [ http://ubuntuforums.org/showthread.php?p=11712748]("http://ubuntuforums.org/showthread.php?p=11712748") Hybrid graphics for ATI/AMD

---

### Post by onefthemany on 2012-03-20
check out this thread:

[http://ubuntuforums.org/showthread.php?p=11780425#post11780425](http://ubuntuforums.org/showthread.php?p=11780425#post11780425)

good luck

---

