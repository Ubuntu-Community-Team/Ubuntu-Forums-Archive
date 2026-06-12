---
title: "Skype 2.2 beta released for linux!"
date: 2011-04-06
forum: The Cafe
---

### Post by rajeev1204 on 2011-04-06
After a long long time indeed.

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)




enjoy.

---

### Post by Random_Dude on 2011-04-06
Nice. :)
I'm gonna test this one today.

Wasn't the last version also a beta? When will appear a stable version for Linux?

---

### Post by kk0sse54 on 2011-04-06
Finally a 64 bit version

---

### Post by NightwishFan on 2011-04-06
Oh, cool. Installers for Debian. =D

Edit: doesn't follow my gtk theme like the static file one. :/

---

### Post by youbuntu on 2011-04-06
Great! How does this differ from the previous (2.1 beta) version? It looks the same (just installed it)...

---

### Post by Random_Dude on 2011-04-06
> **glossywhite said:**
> Great! How does this differ from the previous (2.1 beta) version? It looks the same (just installed it)...

It says improved audio and video quality, not sure if true...

---

### Post by youbuntu on 2011-04-06
> **Random_Dude said:**
> It says improved audio and video quality, not sure if true...

We could verify that if the source were viewable :lol:

They say a lot of things. I cannot believe that they *still* haven't got video calling to Android yet... and iPhone 4 has it. Silly old them.

---

### Post by mikewhatever on 2011-04-06
> **glossywhite said:**
> Great! How does this differ from the previous (2.1 beta) version? It looks the same (just installed it)...

Here are the release notes.
[http://blogs.skype.com/garage/2011/04/skype_22_beta_for_linux_with_s.html?cm_mmc=PXBL|0700_B6-_-linux-20110406](http://blogs.skype.com/garage/2011/04/skype_22_beta_for_linux_with_s.html?cm_mmc=PXBL|0700_B6-_-linux-20110406)

---

### Post by xc3RnbFO8P on 2011-04-06
Just like 2.1 beta, no one wants to talk to me :)

---

### Post by dh04000 on 2011-04-06
This won't install on natty.

---

### Post by NightwishFan on 2011-04-06
> **dh04000 said:**
> This won't install on natty.
It is a known issue. There is a workaround mentioned on the blog posted above.

> **Ringi said:**
> Just like 2.1 beta, no one wants to talk to me :)
I have a Skype but I only use it for my friends in NZ and Severed Fifth.

---

### Post by sdowney717 on 2011-04-06
skype video only works for me if I run it like this
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

Why cant that line work in the command for a launcher? I had top create an executable text file to run skype.

---

### Post by MadCow108 on 2011-04-06
why do they put amd64 in the package name when:
$ file /usr/bin/skype
/usr/bin/skype: ELF **32-bit** LSB executable

...

---

### Post by rudihawk on 2011-04-06
*Busy downloading now*

---

### Post by mikewhatever on 2011-04-06
> **sdowney717 said:**
> skype video only works for me if I run it like this
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

Why cant that line work in the command for a launcher? I had top create an executable text file to run skype.

Sure it can:
```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype'
```

---

### Post by beew on 2011-04-06
I will wait. Right now Skype is working nicely on 10.10 and I don't want to f it up. :)

---

### Post by Random_Dude on 2011-04-06
> **beew said:**
> I will wait. Right now Skype is working nicely on 10.10 and I don't want to f it up. :)

I though the same, but then the temptation was too much...
Luckily it seems to be working, which is amazing considering my previous luck with skype. :D 

Cheers :cool:

---

### Post by false truths on 2011-04-06
I noticed a very important feature that's been added in 2.2 that I was really unhappy about not getting. Conference calling now works in Skype for linux. You can access it from the menu button in the bottom right corner.

---

### Post by mikewhatever on 2011-04-06
> **Random_Dude said:**
> I though the same, but then the temptation was too much...
Luckily it seems to be working, which is amazing considering my previous luck with skype. :D 

Cheers :cool:

...plus, you can still download the previous version from the partner repository.
[http://archive.canonical.com/pool/partner/s/skype/](http://archive.canonical.com/pool/partner/s/skype/)

---

### Post by beew on 2011-04-06
I will test in on my external drive installation first. :)

---

### Post by Random_Dude on 2011-04-06
> **mikewhatever said:**
> ...plus, you can still download the previous version from the partner repository.
[http://archive.canonical.com/pool/partner/s/skype/](http://archive.canonical.com/pool/partner/s/skype/)

My problem is that I had to do some work with the previous version because my camera was upside down, and I was afraid of letting all that effort go to waste. But whatever I did, also seems to be working on this version.

Cheers :cool:

---

### Post by sdowney717 on 2011-04-06
> **mikewhatever said:**
> Sure it can:
```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype'
```

thanks that works. 
I would think everyone would have this issue using VFL2

---

### Post by kk0sse54 on 2011-04-06
> **MadCow108 said:**
> why do they put amd64 in the package name when:
$ file /usr/bin/skype
/usr/bin/skype: ELF **32-bit** LSB executable

...

I noticed that too, so much for my initial hopes of finally forsaking multilib

---

### Post by user1397 on 2011-04-06
The only difference I can tell so far is that any right click menu integrates well with the default maverick theme (which I use), unlike 2.1 where I could only see items in the right click menu if I hovered my mouse on them.

---

### Post by NightwishFan on 2011-04-06
Well, in Debian packages designed for amd64 systems (even 32-bit ones) use amd64 in the name.

---

### Post by areteichi on 2011-04-06
> **mikewhatever said:**
> Sure it can:
```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype'
```

The strange thing is that, as far as I know, this was the only fix Canonical was adding to the official Skype builds. Now they seem to have reintroduced this issue in this latest version...

I hope they'll provide a quick update.

> **dh04000 said:**
> This won't install on natty.

It seems to work fine for me (both official Skype and Canonical version) aside from the minor annoyance mentioned above.

The [release note]("http://blogs.skype.com/garage/2011/04/skype_22_beta_for_linux_with_s.html?cm_mmc=PXBL|0700_B6-_-linux-20110406") does list Natty Beta as one of the known issues. It might have worked for me because I already had GDebi installed as mentioned here: [https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/712377](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/712377)

---

### Post by doorknob60 on 2011-04-06
> **sdowney717 said:**
> skype video only works for me if I run it like this
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

Why cant that line work in the command for a launcher? I had top create an executable text file to run skype.

It should work if you put env before it:
env LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

---

### Post by beew on 2011-04-08
I installed Skype from the Partner's repo rather than downloading from Skype. Today I got an upgrade automatically through Synaptic. :)

It seems to be working, going to call my parents in the weekend to field test it. :) 

Some differences I notice: It connects much faster. The test call voice now actually speaks English, before it was a man's voice which speaks some kind of Slavic language (it greeted me with "Dobileedan" ) On the voice test window there is a box telling me pulse audio is activated and if I want to change the settings I should go to pulse audio volume control. As someone said above conference call in now available, haven't had an occasion to use it though, maybe next week I will have a chance at work..

---

### Post by treesurf on 2011-04-08
I also got an update through the Update Manager.  The new version definitely seems to have better quality sound and video, and the small changes to the UI are nice.  I haven't had any of the video problems that others have noted, thankfully.

---

### Post by NMFTM on 2011-04-08
> **NightwishFan said:**
> Well, in Debian packages designed for amd64 systems (even 32-bit ones) use amd64 in the name.
So, when I apt-get install packages, not all of them are actually for amd64? I thought as long as the source was available, all you had to do was build it with the amd64 switches turned on and that was that.

---

### Post by NightwishFan on 2011-04-08
> **NMFTM said:**
> So, when I apt-get install packages, not all of them are actually for amd64? I thought as long as the source was available, all you had to do was build it with the amd64 switches turned on and that was that.

Some packages are 32-bit, such as flash in Ubuntu (which depends on the 64-bit wrapper), and 32-bit libraries.

---

### Post by Tsu jan on 2011-07-01
Here too, in Debian Wheezy 64bit, it works well and in fact, better than before.

If I didn't try this version, I wouldn't believe that Microsoft (the new owner of Skype) would make any non-Windows version. However, I'm not too optimistic about the future of Skype outside Windows. Although for audio-video chats I prefer to use Google Talk, its audio quality isn't as good as Skype's yet.

---

