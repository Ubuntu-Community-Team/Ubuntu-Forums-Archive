---
title: "CINELERRA Video Editor Program"
date: 2008-06-06
forum: Ubuntu Studio
---

### Post by Ashejoe on 2008-06-06
I've finally  found a Linux program that "appears" to be almost on-par with my favorite Windows video editor Pinnacle Studio. 

The program is called CINELERRA  and can be downloaded at [http://www.heroinewarrior.com/cinelerra.php3](http://www.heroinewarrior.com/cinelerra.php3)

Now here's my problem:  Like many Linux programs that are not "main line", Cinelerra is not in any Ubuntu or Debian respository that I could find.  All I can get is the binary code off the [http://www.heroinewarrior.com/cinelerra.php3](http://www.heroinewarrior.com/cinelerra.php3) website.

Can someone tell me how to load this program so that Ubuntu 8.04 will execute it ?

I also downloaded the Beta of OpenOffice 3 and couldn't load that either for the same reason.

Thanks

---

### Post by cotcot on 2008-06-07
[[COLOR="Red"]Here[/COLOR]]("http://akiradproject.net/repository") is repository information for ubuntu. Compiling cinelerra yourself is not that difficult neither.

You might check the Video Sequence Editor of Blender 2.46 as well. It is not very well known as video editor but very good and stable.

---

### Post by Ashejoe on 2008-06-07
Thank You cotcot for your response to my inquiry on how to load Cinelerra. 

Unfortunately, when I clicked on your embedded link, I got a "page not found" error ??

I've really come to love Ubuntu 8.04.  I just wish software that is available in binary wasn't so hard to install.  I guess I'll learn with time and practice ??

But thanks again for trying.

Joe Ashe

---

### Post by purplepaint on 2008-06-07
I installed Cinelerra via the Synaptic Package Manager; it ended up being about the only thing that went smoothly!  As far as I'm aware, most people experience problems with it, but I seemed to have more than most.

I read somewhere on the forums that there was a more easy to use fork of it in development.  Until then, maybe I'll give Blender a try...

---

### Post by cotcot on 2008-06-08
I do not know why the link is not working. Go to [COLOR="Red"]http://akiradproject.net/repository[/COLOR] or google on 'cinelerra akirad'.

---

### Post by cotcot on 2008-06-08
> **purplepaint said:**
> I installed Cinelerra via the Synaptic Package Manager; it ended up being about the only thing that went smoothly!  As far as I'm aware, most people experience problems with it, but I seemed to have more than most.

I read somewhere on the forums that there was a more easy to use fork of it in development.  Until then, maybe I'll give Blender a try...

That is correct. A new developer team is working on a fork called Cin-3.  [[COLOR="Red"]Here[/COLOR]]("http://www.linux.com/feature/126441") is a link to the information.

---

### Post by purplepaint on 2008-06-09
One program that I keep trying is Kdenlive.

It was fine when I first installed it, but now it seems to crash a lot.  Also, I've somehow managed to make the timeline appear in a separate window to the rest of the program and I can't seem to find a way to "connect" it again.  Could anyone possibly help?  Other than that, I'm fairly convinced that it's pretty good for anyone who wants relatively easy, but not patronising, video editing.

---

### Post by cotcot on 2008-06-10
It is a pity that the kdenlive website does not show a lot of development activity.

---

### Post by BigRedButton on 2008-06-15
I really want to install Cinerella on my Hardy system, bu I've tried to get the akirad repositories through the terminal and I keep getting this error:

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.

I'm pretty sure this is just my network settings (I'm really new to Linux:confused:) but I would like to know how to compile the source for it... I'm pretty sure that would work just fine.

---

### Post by Chrisj303 on 2008-06-16
Cinelerra will not install via synaptic - I've wasted hours of my life trying to install this.

---

### Post by Creative2 on 2008-06-16
.... wel if you have not repository you can't if you add correctly repository you'll

:) i prefer blender too :D but i have seen on mov file i get crash with 2.46 insstead with 2.45 no mah :D

---

### Post by noobuntu_ger on 2008-06-16
I installed cinelerra via synaptic. I used the guide of there site
> 8.04 Hardy Heron

for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
deb [http://repository.akirad.net](http://repository.akirad.net) akirad-hardy main
Installation notes:
- To add this repository in your sources list use the following terminal command:
sudo wget [http://repository.akirad.net/dists/hardy.list](http://repository.akirad.net/dists/hardy.list) -O /etc/apt/sources.list.d/akirad.list
- Installations from this repository need an authentication key. Add it by typing in your terminal the following command: 
wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
- Cinelerra package is available in 5 variants:
cinelerra (x86 and x86_64 without opengl 2.0 video card)
cinelerra-generic (all x86 and x86_64 with opengl 2.0 video card)
cinelerra-k7 (amd32 without opengl 2.0 video card)
cinelerra-k7gl (amd32 with opengl 2.0 video card)
cinelerra-k8 (amd k8 optimized with opengl 2.0 video card)
- Cinelerra must be set to work with PulseAudio. Open Cinelerra and go to Settings->Preferences->Playback->Audio Driver. Select ESound and set the following parameters:
Server: 
Port: 7007 
- These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
- Please, report any package bug to akir4d at gmail dot com
7.10 Gutsy Gibbon

for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
deb [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main
Installation notes:
- To add this repository in your sources list use the following terminal command:
sudo wget [http://repository.akirad.net/dists/gutsy.list](http://repository.akirad.net/dists/gutsy.list) -O /etc/apt/sources.list.d/akirad.list
- Installations from this repository need an authentication key. Add it by typing in your terminal the following command: 
wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
- Cinelerra package is available in 5 variants:
cinelerra (all x86 and x86_64 without opengl 2.0 video card)
cinelerra-generic (all x86 and x86_64 with opengl 2.0 video card)
cinelerra-k7 (all amd32 without opengl 2.0 video card)
cinelerra-k7gl (all amd32 with opengl 2.0 video card)
cinelerra-k8 (all amd64 with opengl 2.0 video card)
- These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
- Please, report any package bug to akir4d at gmail dot com
for i386 (not working on amd 32 bits), by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

for AMD64 (and also Core Duo Intel64), by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
Installation note:
- If your package manager complains that it does not have the right version of libfaac (1.25) you can try installing libfaac0.
7.04 Feisty Fawn

optimised for UbuntuStudio, with OpenGL, by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntuopengl/](http://giss.tv/~vale/ubuntuopengl/) ./

for AMD64 (and also Core Duo Intel64), by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./

for 64 bits with OpenGL disabled, by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntu64NOopengl/](http://giss.tv/~vale/ubuntu64NOopengl/) ./

for i386, by muzzol:
deb [http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/](http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/) ./

for i686, by Jure Cuhalev:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./

for athlonxp, by Jure Cuhalev:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./

for pentium4, by Jure Cuhalev:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./


It worked fine. But i had problems with the program itself. I couldn't figure out how to extend the duration of a picture at the time line. Then i switched to kdenlive. Unforunately it started to crash a lot. Now i'm using blender. Blender appears to be the best solution.

---

### Post by 0olong on 2008-07-27
I seem to have installed Cinelerra successfully, via Synaptic.

Following the instructions from the Cinelerra site to add the repository via the terminal didn't work at all (I got the exact error talked about above with the 8080), but adding the repository via Synaptic worked perfectly - just go to Repositories/Add and paste in this as the 'apt line':
```
deb http://akirad.cinelerra.org akirad-hardy main
```

---

### Post by Ashejoe on 2008-07-27
I experienced the same thing as Oolong.

How do you do a "REPOSITORY ADD" ??

Thanks

---

### Post by cotcot on 2008-07-27
```
sudo gedit /etc/apt/sources.list
``` will give you a text file. Add the repository valid for your system at the bottom and save.
Then ```
sudo apt-get update
sudo apt-get install cinelerra
```

---

### Post by purplepaint on 2008-07-27
I've been using LiVES for the past week or so after not being able to get Cinelerra to work as it should.  I would certainly recommend it to anyone who wants a semi-professional editor.  It's only at beta stage but it works perfectly for me and it's quite easy to get the hang of.

---

### Post by Ashejoe on 2008-07-27
WOW,..... I don't know if I should be thanking OoLong or CotCot... but.... I FINALLY GOT CINELERRA WORKING ON MY SYSTEM !!!!

   :guitar::lolflag::mrgreen:=D>

Don't ask me how ?  All I can say, is that I followed their advice and it's finally working !!!!  AWESOME..... thank you !!!

I also attempted to load the LiVES that PurplePaint suggested, but so far, I have not been able to install it.

Thanks All !!!

---

### Post by cotcot on 2008-07-28
Happy you get it running.
I hope it has OpenGL enabled. You can see this by starting Cinelerra and going to --> Settings --> Preferences --> Playback --> Video. The video driver select box will give you the possibility to select X11-OpenGL.

---

### Post by purplepaint on 2008-07-28
> **Ashejoe said:**
> I also attempted to load the LiVES that PurplePaint suggested, but so far, I have not been able to install it.

According to the downloads section of the LiVES website:

> Ubuntu users can install LiVES simply by clicking on: [http://www.getdeb.net/app.php?name=lives](http://www.getdeb.net/app.php?name=lives)
Thanks to Joao Pinto !

I tried it just now, and the link doesn't seem to be working, but that's where I got it from.

---

