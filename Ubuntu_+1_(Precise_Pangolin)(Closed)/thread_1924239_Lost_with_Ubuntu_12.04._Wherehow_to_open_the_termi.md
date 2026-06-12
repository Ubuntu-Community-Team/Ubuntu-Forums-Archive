---
title: "Lost with Ubuntu 12.04. Where/how to open the terminal?"
date: 2012-02-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Nightkitten on 2012-02-12
Hello :)


Since I have no idea whom else to ask, I thought I'd try it here.

I got a new laptop and my bf installed Ubuntu 12.04 for me, since (if I recall properly) the older versions had problems with my graphic card (no drivers available?!) Heck, I dont know.

Now I'd like to install Adobe Flash, which is only possible if done by hand, and now the problem:

On this stupid user-unfriendly layout I cant find where to open the terminal :( Do you have any idea how to do that?

And when I'm already on it: I was very fond of Ubuntu 10.04 on my old laptop, do you know if there is a possibility to get the user surface of 10.04 in 12.04? In my gaming-partition I could change the Windows 7 "Design" to the old standard one. Is this possible with Ubuntu too? I need a taskbar back :(


Please don't say something like: just install Lucid again, if that would be working my bf would have done that. And btw no I cant ask him, he went skiing. -.-

Oh and to save you some time: Yes I am a newbie, yes I am unexperienced, but I am not stupid, and I would very much apreciate your help! :D


Nightkitten

---

### Post by Nightkitten on 2012-02-12
Ok never mind, stupid me! -.-

Found the terminal, but still curious about changing the interfaces. :)

---

### Post by grahammechanical on 2012-02-12
It is all there. It just a different way of doing things. You can read this link:

[http://ubuntuforums.org/showthread.php?t=1859961]("http://ubuntuforums.org/showthread.php?t=1859961")

How valuable that information will be for 12.04 I cannot say. Are you sure your bf installed 12.04? It is still in alpha stage testing. It is stable. I use it every day but we would not recommend installing it unless it was for testing. And one of the things I am testing is, can I set it up to work the way I want it to work? 

I do not have the same taste as you so that link is the best that I can offer. I now, can also offer this:

[http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html]("http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html")

Regards.

P.S. You might want to mark this thread as solved as you have now found the terminal and start a new thread for your second issue. You will not get very far with that problem with this thread title.

---

### Post by oldos2er on 2012-02-12
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by Gregory Lee on 2012-02-12
That's why I'm here, too, using 12.04 instead of the current release 11.10.  I bought a new computer and found I couldn't install 11.10 on it, probably because of the graphics card (ATI Radeon HD 6550D).  But I could install 12.04 (though it wasn't completely straightforward).

I never used Ubuntu before, so I have no ideas about your nostalgia for your old desktop.

---

### Post by alphacrucis2 on 2012-02-12
The best way to handle adobe flash is probably to install using the flashaid firefox addonn.

---

### Post by Gregory Lee on 2012-02-12
> **alphacrucis2 said:**
> The best way to handle adobe flash is probably to install using the flashaid firefox addonn.
There is a notation for this on the add-on page for it saying it is not available for Firefox 11.0.  But (after upgrades) 11.0 is the version I have.

---

### Post by Nightkitten on 2012-02-12
Thank you all for your responses. :) The links look very helpful and I will definitelly try that out tomorrow! :KS

@gregory: same here. Installation wasn't smooth but at least possible (as oposed to the other versions) I have a GTX 570M, in case anyone stumbles on the same problem.
Also had the problem with Adobe telling me there's no avaiable version, so I tried it like this:

[http://gamblis.com/2011/12/03/how-to-install-flash-player-on-ubuntu-12-04-alpha-1/](http://gamblis.com/2011/12/03/how-to-install-flash-player-on-ubuntu-12-04-alpha-1/)

Did not work for me so far, as I get a weird error message, but I will look into that tomorrow, too. Now off to sleep zZz zZz

---

### Post by screaminj3sus on 2012-02-12
> **alphacrucis2 said:**
> The best way to handle adobe flash is probably to install using the flashaid firefox addonn.

That seems overkill to me, when installing flash simply involves copying one .so file to ~/.mozilla/plugins

People really tend to over complicate installing flash. No need for repos or firefox extensions. Download the .tar.gz for your architecture and copy the .so file inside it over. Bam it works in all my browsers :)

---

### Post by kaldor on 2012-02-12
See [here]("http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html#more") regarding the desktop environment. It's not entirely identical to 10.04 but it's quite familiar. Hopefully by the time 12.04 is released, the Classic session will be much more complete.

Note that you may have to hold the Alt key while right-clicking on the panel. I actually like this more because it's less prone to mis-clicks.

---

### Post by Gregory Lee on 2012-02-13
> **screaminj3sus said:**
> People really tend to over complicate installing flash. No need for repos or firefox extensions. Download the .tar.gz for your architecture and copy the .so file inside it over. Bam it works in all my browsers :)
Installing that way in my last system (Fedora 6) led to many crashes of the Adobe flash plugin.  Here in 12.04 earlier today, I installed the version of the flash plugin I found in the Software Center, and it worked pretty well, but eventually it did crash under stress, which was a youtube HD video playing in full screen for about 10 minutes.  (Rather, I had to crash it by killing its process, after it froze.)  So it is worthwhile looking for an improvement.

---

