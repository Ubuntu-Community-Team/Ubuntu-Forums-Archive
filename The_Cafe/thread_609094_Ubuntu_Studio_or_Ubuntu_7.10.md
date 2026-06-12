---
title: "Ubuntu Studio or Ubuntu 7.10"
date: 2007-11-10
forum: The Cafe
---

### Post by GinKen on 2007-11-10
Greetings to this forum.  Recently I installed Ubuntu Studio on a Dell Inspiron 1721 and it stalls as timidity tries to load, which I have reported here in General forums:
[http://ubuntuforums.org/showthread.php?p=3745711#post3745711](http://ubuntuforums.org/showthread.php?p=3745711#post3745711)
Basically I wanted to help a friend who would like to get into multimedia and was excited when I mentioned Ubuntu Studio.  He had only known Windows.  But, as I mentioned in other post, having lots of problems with Alsa recognizing sound card.  Also, I noticed Ubuntu Studio takes a lot of time to startup.  
What I would like to ask in this forum is for advice on whether to stick to Ubuntu Studio, with the rt kernel, or simply install Gusty with generic kernel (doesn't need to load timidity) and build a suitable multimedia workship from there.
Any advice is welcome, as I would like to get this computer back to my friend so he gets a good impresson of Ubuntu.
Thanks!

---

### Post by Samhain13 on 2007-11-10
I haven't tried installing/using Ubuntu Studio but I do have 7.10 with a real-time kernel. Haven't experienced any major glitches, and to think I'm using three year old hardware. So I guess that's one vote for "Gutsy and build a suitable multimedia workshop from there".

Anyway, just for added information about my set-up, if you're interested:
1. Real-Time Kernel from the Repos installed.
2. Followed the instructions here on setting up TiMiDiTy: [http://www.cs.cornell.edu/w8/~djm/ubuntu/feisty/#timidity](http://www.cs.cornell.edu/w8/~djm/ubuntu/feisty/#timidity) (instructions are for Feisty but it still worked in Gutsy)
3. Rosegarden from the Repos. (Haven't tried using a controller though, I just write notes.)
4. Cinelerra from [http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)
5. Installed a couple of other things like GTKRecordMyDesktop, FFMpeg and FFMpeg2Theora

:)

---

### Post by GinKen on 2007-11-10
Thanks, Samhain13
I'm beginning to lean to building one step at a time as it's easier to troubleshoot.  One thing I'd like to ask, when you installed the rt kernel did you remove the generic or keep it?  Also, do you find the rt boots slow?  I have a new but basic Dell, and I find rt boots very slooow in Ubuntu Studio.

---

### Post by Samhain13 on 2007-11-11
I kept it but I boot to the RT by default. To be honest, I don't even know whether I should still keep the Generic or not, but I guess I have the drive space anyway so it stays.

RT booting slow? I don't notice if it does. But then I'm on a desktop so that may make some difference, or not. I do notice the thing people say about applications being more responsive when you're using RT. However, it's just pretty much ocular observation.

---

