---
title: "Amateur radio, need to give a presentation re: Ubuntu"
date: 2014-12-21
forum: Ubuntu, Linux and OS Chat
---

### Post by techee1 on 2014-12-21
I may be tasked with a presentation regarding Ubuntu for our Amateur Radio Club. I'm a firm believer in "Google it", or search for your question before asking. This time I don't even know which questions to use. Is there anyone here that can direct me?  I am able to teach installation, dual boot, and many exclusive features, but want to help members get the most out of the old laptop in the closet. 
At the informal meeting I attended, a couple of the members said they like 10.04, and didn't like the new iterface of 14.04.1
While my dad and I were swimming at our vacation cabin, he said, "Don't go near the water until you learn to swim" 
One of the best aspects of Ubuntu is the support community. I must tell everyone about the "Free" aspect, free beer vs. freedom!
Thank you to anyone who is willing to take the time to help. AC9JZ Mike Proctor, Rockford, IL

---

### Post by DuckHook on 2014-12-21
Welcome to the forums, techee1.

I'm not sure what you are asking. If you are asking about Ubuntu in relation to amateur radio, then that is way out of my league and only other highly technical radio experts or hobbyists can help you. On the other hand, if your intent is just to present Ubuntu and/or Linux as an alternative general operating system, then there are plenty of resources that we can direct you to.

Assuming it's the latter, then try the following:

"Linux is not Windows" intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

General Ubuntu Intro:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://owlcroft.com/ubuntu/](http://owlcroft.com/ubuntu/)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

Linux Distros:

[http://linuxfreedom.com/Distros/](http://linuxfreedom.com/Distros/)

RE: 10.04

This is by now an ancient OS that reached end-of-life in summer of 2013. It is no longer supported and is therefore a huge security risk. The recent news about the Heartbleed and Shellshock bugs should give anyone still running dead versions the willies. Your members are just asking for trouble if they continue to stick to 10.04. Many people don't like the look of Unity. If so, then Xubuntu or Lubuntu are flavours that may be more to their liking. All flavours of 14.04 are LTS, so will be supported for years. For info on security, try:

Basic Security:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

Advanced Security:

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
all stickies in:
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)
in particular:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
and anything by bodhi.zazen, Dangertux, Ms Daisy, the forum admins and mods.

Hope this helps.

---

### Post by ajgreeny on 2014-12-21
I would say that you should ignore the link above to [http://linuxfreedom.com/Distros/](http://linuxfreedom.com/Distros/) as it is many years out of date on at least some of the distros available, though I did not follow its links to many from there.
A much better source of info on the availability of distros is [DistroWatch.com]("http://distrowatch.com/")

---

### Post by DuckHook on 2014-12-21
> **ajgreeny said:**
> I would say that you should ignore the link above to [http://linuxfreedom.com/Distros/](http://linuxfreedom.com/Distros/) as it is many years out of date on at least some of the distros available, though I did not follow its links to many from there.
A much better source of info on the availability of distros is [DistroWatch.com]("http://distrowatch.com/")Thanks, aj.

---

### Post by mörgæs on 2014-12-21
I believe in "show it, don't tell it". 

Make it live - that's what the live boot is for. Let people bring some old iron and you can show how to make it spin again.

---

### Post by DuckHook on 2014-12-21
> **mörgæs said:**
> I believe in "show it, don't tell it". 

Make it live - that's what the live boot is for. Let people bring some old iron and you can show how to make it spin again.+1

Just make sure you spin both 32-bit and 64-bit and do them on CD/DVD and USB media. Some older HW will only take 32-bit and others won't boot on USB.

---

### Post by techee1 on 2014-12-22
Thank you to all who replied. This gives me a head start, now my homework begins. The presentation will probably be the 2nd Friday of February, or March, plus I have time off during the week between the holidays, so I will have time to prepare. I also can post an article in our monthly "Hamrag" online newsletter. My newsletter article will show how to enter bios, and choose boot order, also how to save computer specifications. Then I will allow each person interested to send me that information. I may even be able to setup a router in repeater mode, with ethernet for anyone who may have wireless issues.
One question, is there any stripped down version of Ubuntu 14.04.1 that will fit on a CD rather than DVD, and then let them do the updates online? I'm thinking about older hardware here.
Also, if using USB Flash Drive, I believe ther is a way to add a partition to allow saving settings/files using the live distro before installation, or for portable use on other computers. Can you recommend a tuorial for this?
Thank you again, and happy holidays to all!

---

### Post by DuckHook on 2014-12-22
> **techee1 said:**
> ...is there any stripped down version of Ubuntu 14.04.1 that will fit on a CD rather than DVD, and then let them do the updates online? I'm thinking about older hardware here.Given the HW uncertainties, I would strongly suggest Lubuntu. As the lightest distro, it will give you the most flexibility to tackle old HW that might not work with more resource-intensive flavours. I believe that it still fits on a CD, but you would have to check that on the download site. It is also laid out in a way the will be familiar to Windows users, with a "start" button on the lower left, etc. The only drawback to Lubuntu is that, in its default configuration, it is spartan and rather... well... ugly. There are wallpapers and alternate themes that can improve it almost immediately, but these require you to replace the settings post-install, which is something you might want to avoid in an installfest. A further suggestion, I've found that a helper who is even somewhat familiar with Linux is very useful in these situations. They can work with individuals while you are handling the larger presentation. Perhaps one of your fellow members would be happy to assist.> Also, if using USB Flash Drive, I believe ther is a way to add a partition to allow saving settings/files using the live distro before installation, or for portable use on other computers. Can you recommend a tuorial for this?You are referring to a "persistent USB pendrive" and the tutorial is [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").

Good luck with your presentation!

---

### Post by techee1 on 2014-12-22
Great ideas have been given, and I am not surprised. The only thing better than Ubuntu is the community/forums, and the people who share their knowledge. It's kind of like what you put into your coffee to make it special!
Thanks again, and happy holidays. I may post again as I formulate the plans, and get some feedback on what the members want.

---

### Post by mörgæs on 2014-12-23
It's targeting a bigger event than yours but maybe you can find some inspiration anyway:
[http://tldp.org/HOWTO/Installfest-HOWTO/](http://tldp.org/HOWTO/Installfest-HOWTO/)

Good luck and merry Christmas.

---

### Post by Bucky Ball on 2014-12-23
If you are intending this to be about resurrecting old computers from the closet, then don't use a straight Ubuntu. The recent versions probably won't run on old hardware anyway. Avoid Unity desktop (which it sounds like they don't like) and go with Lubuntu or Xubuntu (my preference is Xubuntu although it is a little 'heavier' than Lubuntu). This will give a more familiar desktop environment as well as being likely to run on old hardware.

---

