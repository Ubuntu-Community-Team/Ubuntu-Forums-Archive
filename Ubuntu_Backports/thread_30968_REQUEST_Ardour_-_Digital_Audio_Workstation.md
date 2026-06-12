---
title: "REQUEST: Ardour - Digital Audio Workstation"
date: 2005-05-01
forum: Ubuntu Backports
---

### Post by MetalMusicAddict on 2005-05-01
I was trained as a Recording Engineer with Pro Tools. Since moving to Ubuntu I was looking into a good multi-track recording app.

I found [Ardour](http://ardour.org/) through some links here. 

[IMG]http://ardour.org/img/ardour-full-session-thumb.png[/IMG]
[BIGGER](http://ardour.org/img/ardour-full-session.png)

I would LOVE to use this. If this could be added to the repo or a HOWTO would be great. :)

---

### Post by jdong on 2005-05-02
This is a part of Ubuntu Universe already.


The latest version in Hoary is 0.9beta2, which is the most current version available.

---

### Post by MetalMusicAddict on 2005-05-02
IM SO SORRY. :) It was under "ardour-gtk". Sorry. I didnt mean to fill up the fourm with requests for existing apps. Your a busy and hard working guy jdong. ;)

Please delete this if needed.

---

### Post by jdong on 2005-05-02
That's ok :)

A packages.debian.org search is pretty disheartening, but "apt-cache search" is your friend :)

---

### Post by James Deakin on 2005-06-06
How do i get and install this software i have been trawling forums and serching the web for hours on this subject. I would love to use Ardor on Ubuntu.

I just dont understand how. It is not listed in the package manager. I have downloaded a debian binary but i have no idea how to install it or if it is compatible. 

How should i be going about this?

I belive I the target audience for ubuntu. IE I am a computer user desperatly trying to migrate to linux. I have 15 years of experience on other platforms including osx the older mac systems, dos, windows, the amiga and before that various other 16 bit systems. I am a programmer (PHP, ActionScript, javaScript etc). PLEASE PLEASE HELP. 

Apart from this Ubuntu has done a great job it was easy to install. And in normal usage it was easy to understand the apps are good  etc. it runs perfectly on all the systems i have installed it on including some very rough old PCs. 

I just cant get past this problem though

---

### Post by MetalMusicAddict on 2005-06-06
Ive read lots of things saying that the normal Debian kernel isnt great for audio recording. Needs to be low latentcy. Also I couldnt get it to work with Ubuntu. :) So I looked around and found Demudi and Remudi. Both are distros with recording in mind. Look [HERE](http://www.agnula.org/download/).

---

### Post by fishfork on 2005-06-06
[QUOTE=James Deakin]How do i get and install this software i have been trawling forums and serching the web for hours on this subject.[/QUOTE]

You need to enable the universe repository. See [here](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto/view?searchterm=repositories). Then you should be able to find it in synaptic.

---

### Post by fishfork on 2005-06-06
[QUOTE=MetalMusicAddict]Ive read lots of things saying that the normal Debian kernel isnt great for audio recording. Needs to be low latentcy. Also I couldnt get it to work with Ubuntu. :) So I looked around and found Demudi and Remudi. Both are distros with recording in mind. Look [HERE](http://www.agnula.org/download/).[/QUOTE]

Hope you had fun with Agnula - I keep meaning to give it a go some time. Wrt real time kernel patches, someone seems to have done some of the work already. Have you seen [this thread](http://www.ubuntuforums.org/showthread.php?t=38439)? It'd be great if the modified kernel got into universe.

---

### Post by MetalMusicAddict on 2005-06-09
That would be nice. :) For now Im going to dual-boot XP/Demudi. I took Ubuntu off my main PC and put it on my laptop. :) For all the day-to-day stuff.

Im gonna look around alot. I think if Im REALLY gonna use Ardour Im gonna have to buy another HD, soundcard and mixer. Maybe a little Mackie.

Gotta do some reading up. Alot has changed since my Pro-Tool days. :)

---

### Post by artsci2 on 2008-03-14
I'm having trouble getting Ardor to run in both Ubuntu 7.10 and ubuntu-studio.Ardor starts and flashes a latency report then gives a "can't initialize Jack" message. I went ti the add/remove programs menu and loaded every program that refered to Jack in hopes that Jack would be installed for sure with the dependency detection of the add program process. Then Ardor gave the same result.

Assuming Jack is indeed installed. How do I check to see if Jack is active and available?

---

### Post by saunders on 2008-03-14
You'll need to have Jack running before you start Ardour.

Start Jack audio control (I think...I'm not at my Linux box and am in the process of setting up audio processing myself on Linux - it may be a case of the blind leading the blind here!), when the application appears you then need to click 'start'. This'll start the jack audio server.

You can then start Ardour.

---

### Post by MetalMusicAddict on 2008-03-14
Please do not dig up 2.5 year old threads. Especially to turn it off topic. This was a backport request. Not a support thread.

Mods please close.

PS: Man. I sure have come a long way. :P

---

### Post by carusoswi on 2009-09-19
> **MetalMusicAddict said:**
> Please do not dig up 2.5 year old threads. Especially to turn it off topic. This was a backport request. Not a support thread.

Mods please close.

PS: Man. I sure have come a long way. :P

Whatever, I wish you had not discouraged further discussion in this thread - I'm looking to solve the same problem this morning - can't start ardor-gdk2 - complains that it cannot start Jack.  Have Jack running.  Will keep browsing for a solution.

Caruso

---

