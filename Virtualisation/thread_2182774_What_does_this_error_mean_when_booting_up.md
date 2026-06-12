---
title: "What does this error mean when booting up?"
date: 2013-10-22
forum: Virtualisation
---

### Post by linuxguru43 on 2013-10-22
[IMG]http://i44.tinypic.com/29243ex.png[/IMG]

---

### Post by pqwoerituytrueiwoq on 2013-10-22
the OS is complaining about the virtualbox BIOS, just ignore it
that is in the dmesg output BTW

---

### Post by linuxguru43 on 2013-10-22
Thanks.. It stayed at that screen for a few minutes until it booted up completely. They need to change the compiz default back to non-compiz window dressing effects at first bootup. Virtualbox is taking forever to load the new Ubuntu release and this is a design problem for virtualbox users like myself since plenty of users use virtuabox on a daily-basis. Hopeful you guys can fix this somehow?

---

### Post by linuxguru43 on 2013-10-22
Oh my goodness, now I have a new problem. After waiting what felt like an eternity to get Ubuntu 13.10 to install in virtualbox now I am stuck at this screen. The dots are lighting up and the screen is black like this and they have been doing this for the last few minutes.. Nothing else is happening. What am I doing wrong here? Does this look correct to you guys??? Is there an advisory about virtualbox and Ubuntu 13.10 I should have read??  What should I tell my boss about this? I'm just wasting time this morning.[IMG]http://i41.tinypic.com/25g5pw3.png[/IMG]

---

### Post by Cavsfan on 2013-10-22
You could try pressing ALT+Cntl+F7 and see if the login screen comes up.

---

### Post by zika on 2013-10-22
Aren't You linuxguru...? ;)
Try turning off splash and quiet switches in order to get better insight in what is happening...

---

### Post by Cavsfan on 2013-10-22
> **zika said:**
> Aren't You linuxguru...? ;)
Try turning off splash and quiet switches in order to get better insight in what is happening...

I never claimed to be a Linux guru. That has worked for me before maybe under different circumstances.

Are you the linuxguru? ;) BTW is that your real picture? :P

---

### Post by deadflowr on 2013-10-22
> **zika said:**
> Aren't You linuxguru...? ;)
Try turning off splash and quiet switches in order to get better insight in what is happening...

lol.
This tries to explain what that means, and how to fix it
[http://fintastical.blogspot.com/2010/11/virtualbox-piix4smbus-error.html](http://fintastical.blogspot.com/2010/11/virtualbox-piix4smbus-error.html)

---

### Post by cariboo on 2013-10-22
Moved to Virtualization, as this has nothing to do with Trusty development.

---

### Post by linuxguru43 on 2013-10-22
Thank you for all the kind answers... I still can't get Ubuntu 13.10 to run in virtualbox. I'm currently running Ubuntu 12.04 LTS which is running perfectly btw. Nothing has changed. I can't seem to get behind the dots to tell me what is going on. So I take it that this is a new issue? Does anyone else have trouble using Ubuntu 13.10 in virtualbox besides myself? Thanks.

PS why is compiz enabled by default? why would you want window dressing instead of universal system functionality on all kinds of hardware? Not everyone wants/needs special effects. I just want this to run in virtualbox for testing. 13.10 was running so slow when I did get it to work. Is there someway to disable compiz before booting Ubuntu 13.10? There instead should be some sort of series of questions for new users when they are installing Ubuntu and allow them to decide if they want special effects or not. I don't need compiz but since it is installed by default I have to use Additional Guest packages in Virtualbox to get it to run faster. What a headache.

---

### Post by deadflowr on 2013-10-22
Compiz is the window manager that unity runs on.


I don't know if unity will load with another WM.
Unity2d, which is still around for 12.04, uses metacity.
But the code for unity2d was merged with unity after that, so...

The Fu posted about Virtualbox on another thead I ended up reading and post his link 
[http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

I find some of the solutions might be quite helpful for you.

---

### Post by zika on 2013-10-23
> **Cavsfan said:**
> I never claimed to be a Linux guru. That has worked for me before maybe under different circumstances.

Are you the linuxguru? ;) BTW is that your real picture? :PNo, I'm not the linuxguru, I'm zika...
It is for You to decide if that is my real picture... I'm too old to see differencies... ;)
Boy, this lis like a field-trip for me, out of U+1... ;)

---

### Post by linuxguru43 on 2013-10-23
Are you guys all smart asses or are you seriously going to answer my questions? I don't need people making a joke about my ID handle. Sheish. I used to come to these forums and users here were so polite and very helpful. Now you guys act like snobs and plainly don't give a damn. You think it is funny to mod or help newbies with that kind of attitude? I'm going to switch to some other distro if that is the case. Even howie is blaming everything on my hardware specs, and that excuse is a load of crap. 

TL;DR I didn't have this problem before. I have been using Ubuntu 12.04 LTS in virtualbox perfectly fine and it will install the way I expect (just tested it today). If you don't have a suggestion please don't comment on my request for help. There is something wrong with Ubuntu 13.10 and virtualbox. This installation is taking much longer than normal and I am receiving errors (see attachments in OP). Please advise. Thank you.

---

### Post by deadflowr on 2013-10-24
> **linuxguru43 said:**
> Are you guys all smart asses or are you seriously going to answer my questions? I don't need people making a joke about my ID handle. Sheish. I used to come to these forums and users here were so polite and very helpful. Now you guys act like snobs and plainly don't give a damn. You think it is funny to mod or help newbies with that kind of attitude? I'm going to switch to some other distro if that is the case. Even howie is blaming everything on my hardware specs, and that excuse is a load of crap. 

TL;DR I didn't have this problem before. I have been using Ubuntu 12.04 LTS in virtualbox perfectly fine and it will install the way I expect (just tested it today). If you don't have a suggestion please don't comment on my request for help. There is something wrong with Ubuntu 13.10 and virtualbox. This installation is taking much longer than normal and I am receiving errors (see attachments in OP). Please advise. Thank you.

Did you read either of my posts?

Sure, i laughed at a another post, but I also tried pointing you to potential solutions.

---

### Post by linuxguru43 on 2013-10-24
Yes, thank you I tried your solution. It didn't help at all. Yes, some of these other users I can't figure out why you would let them respond to user questions like that. I think some of the mods here do a really crappy job too. This is no help to me. I'm probably going to switch to some other disto because this is a joke. At least the Fedora will run in virtualbox with no problem right now. I don't have this problem with F19 either FYI. Why do you have window dressing enabled by default in Ubuntu 13.10? Why would anyone want that if they didn't need it anyways? I can't boot. It takes forever to load when it does boot in virtualbox. You guys don't even care to test it? What is up with that? Seriously? I would love to recommend ubuntu 13.10 to other users and clients, but this support has gotten pretty lousy. Do you expect to gain positive reviews from other developers with this when it is almost completely unfunctional in virtualbox and VMware visualization? 

Is Ubuntu 13.10 just for netbook installations? Should I just use the server installation ISO instead??? Is it that bad?

TL;DR Your kind suggestions didn't help. Please advise.

---

### Post by linuxguru43 on 2013-10-27
Bump!

---

### Post by linuxguru43 on 2013-10-27
Nobody here uses virtualbox SO I AM GOING TO CLOSE THIS THREAD. Going black to slack. Bye.

---

