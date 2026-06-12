---
title: "How is Feisty going to deal with the Java/Flash/Media codecs problem?"
date: 2007-01-30
forum: The Cafe
---

### Post by Extreme Coder on 2007-01-30
Hi all,
I was wondering if Feisty will be different than Edgy and Dapper in regards to Java, Flash and the media codecs.

I'm almost sure I read Java changed license to GPL, and became completely free(not sure at all though, and net is too slow now to make sure)

What I want to know is that will the Flash and media codecs be easier to install for the end user? For example if you enter a website with flash in it, and the yellow bar in Firefox to "Install missing Plugins" appears, if you click the button, it fails for no clear reason. There could be a code modification in Firefox to make the button install the Flash plugin from the Ubuntu repositories, and there could be a Flash plugin and Flash player items in the Add/Remove programs list.

And about the codecs, how is that going to be dealed with? Will they be installed by default? Or will they be installed on demand if you play a file which needs those codecs, like what Amarok does?(Thanks Aysiu for letting me know about that) And I guess w32codecs aren't going to be available in ANY way, or will they? I know if MPlayer replaced all media players(or used it as a back-end for Totem and Rhythmbox and all other media apps) we wouldn't have any media-related problem :P (Just joking, GStreamer and Xine are the future of server of media apps and most apps are using them already)

I hope nobody takes this post or me as being "out of the line" or negative, I was just asking how is this issue gonna be dealed with in Feisty and my own opinions of how they COULD be tackled. Ubuntu is an excellent distro but this one stupid issue puts people down about Ubuntu, and I think it can be solved without the need to include the codecs at the same time.

Extreme Coder

---

### Post by Artemis3 on 2007-01-30
[http://www.digg.com/linux_unix/New_OFFICIAL_Ubuntu_package_auto_installs_codecs_Flash_Java_MS_Fonts](http://www.digg.com/linux_unix/New_OFFICIAL_Ubuntu_package_auto_installs_codecs_Flash_Java_MS_Fonts)

---

### Post by Stemp on 2007-01-30
Feisty is a beta, so w32codecs and others proprietary stuffs are not the major concern.

---

### Post by kuja on 2007-01-30
As for Java, what I heard is that they GPL'd the Java 7 branch, which isn't going to be released for a while yet. Probably not in time for Feisty, maybe in time for Feisty+1 or the next LTS.

---

### Post by kuja on 2007-01-30
> **Stemp said:**
> Feisty is a beta, so w32codecs and others proprietary stuffs are not the major concern.

alpha, actually.

---

### Post by Stemp on 2007-01-30
> alpha, actually.

Yes you're right ;)

---

### Post by Extreme Coder on 2007-01-30
Thanks Artemis3 for the link, so all I written was for naught I guess :(
Anyway, I will be trying Feisty soon to check the all new cool stuff :D

---

### Post by macogw on 2007-01-30
Extreme Coder, the only "new cool" I'm seeing in Feisty (running it now) is some new logos on apps and that Beryl works.  Beryl core dumps on Edgy for me with the latest updates.   Actually, after the Python upgrade to 2.5 instead of 2.4 it might stop working on Feisty too.....I'll have to watch that when these updates finish.  I think most stuff isn't so noticeable, and wireless sure doesn't seem to be in by default yet.  And I had to install Beryl myself, so that part hasn't come to fruition either.

---

### Post by mr.blacke on 2007-02-10
The problems I've seen till now is not w32 codecs whose i installed from a .deb file.
I'm not having problem with flash either. Instead I'm having trouble with Java sdk. I cannot setup environment variables in /et/profile. I'm still googling...

---

### Post by tageiru on 2007-02-10
> **Extreme Coder said:**
> And I guess w32codecs aren't going to be available in ANY way, or will they?

w32codecs can be purchased for gstreamer from fluendo. [https://shop.fluendo.com/](https://shop.fluendo.com/)

---

