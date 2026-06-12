---
title: "Change virtual disk type without a re-install ?"
date: 2014-01-19
forum: Virtualisation
---

### Post by shearer4 on 2014-01-19
I may post this in another appropriate forum also. I hope that's okay?   I have installed two instances of Ubuntu on VBox using a dynamic VDD setting. Now, I find out through research and advice here, that I may get better performance by allocating a fixed amount of disk space, say 12gigs to each VDisk.   Is there a way to change this setting without mirroring the drive, which I don't really follow, or deleting and re-installing the whole VM? 

Thanks

AS

---

### Post by Frogs Hair on 2014-01-19
Please don't post duplicate threads as it divides the efforts of those attempting to aid you. Your thread can be moved if needed.

---

### Post by Elfy on 2014-01-20
*Thread moved to **Virtualisation**.*

edited thread title to be more specific

---

### Post by shearer4 on 2014-01-20
Got it, understood.  Thank you.

---

### Post by ibjsb4 on 2014-01-20
I have not tried that, but I have ran both dynamic and fixed and really have not noticed a performance difference.  This could be because I do not run any taxing loads in a VM.  I do usually take the time to do fixed disk, I think it speeds up initial install time, but on my old machines its a slow process either way.

Googling around, it looks that cloning is the way to go.

[http://brainwreckedtech.wordpress.com/2012/01/08/howto-convert-vdis-between-fixed-sized-and-dynamic-in-virtualbox/](http://brainwreckedtech.wordpress.com/2012/01/08/howto-convert-vdis-between-fixed-sized-and-dynamic-in-virtualbox/)

---

### Post by shearer4 on 2014-01-20
Thanks.  I tried to google, but probably didn't enter the right search terms. I read on another thread that if you have the space, which I do, this is a good way to improve performance. But, I've also read that some people don't see a difference.

---

### Post by ibjsb4 on 2014-01-20
> **shearer4 said:**
> Thanks.  I tried to google, but probably didn't enter the right search terms.

You could also try a different search engine.

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by shearer4 on 2014-01-20
Thanks again.  I meant that I had tried google before posting my original question. The link you provided took me to the right page for this. I'm a little reluctant to take this on that is; cloning and changing sizes and so forth.  I'm going to have to get used to a little bit of sluggish behavior. My MacPro, even though older, is so fast to react, I'm spoiled by that.  

Thanks again for your advice  and links.

---

### Post by ibjsb4 on 2014-01-20
One last thought

You could try running a different desktop, may speed it up.

```
sudo apt-get install gnome-panel
```

Reboot and at login, click on the icon in the login window to change desktops.

---

### Post by shearer4 on 2014-01-20
I ran this in terminal, installed gnome panel, no problem. When I restarted, I got no login window. I checked, I have auto-login OFF.  I shut down and restarted and will see what I get. It seems like it wants to open to the default desktop?  So, when I started back up again, it locked and will not completely boot. Just get a blinking cursor.  Not a problem. I will figure out to fix it. Not sure what I did?

---

### Post by ibjsb4 on 2014-01-20
Not sure whats going on either.  Can you get to console (tty)?  Ctrl + Alt + F1

If so, try giving your display manager (lightdm) a kick start with the command:

```
startx
```

About lightdm

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

You do have a vBox snapshot for backup, right?

---

### Post by shearer4 on 2014-01-20
Thanks:  No, I removed 13.10, at least for now. I have 12.04LTS and Xubuntu on here also. They work just fine. I am really just trying new things to learn without disrupting my main MacOS.  I'm going to re-install 13.10 at some point and see if I can do a better install. 

Not a problem. I was close to uninstalling it anyway.  Curious though, what does Gnome desktop look like or do? Less graphics, I'm guessing so it runs faster?

---

### Post by ibjsb4 on 2014-01-20
> Curious though, what does Gnome desktop look like or do? Less graphics, I'm guessing so it runs faster? 

[https://www.google.com/search?q=gnome+fallback+pics&client=ubuntu&hs=CRJ&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=A1DdUrK-AarHsASruIDYAQ&ved=0CC0QsAQ&biw=960&bih=457](https://www.google.com/search?q=gnome+fallback+pics&client=ubuntu&hs=CRJ&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=A1DdUrK-AarHsASruIDYAQ&ved=0CC0QsAQ&biw=960&bih=457)

And it can have more (compiz) or less (metacity) graphics, depends on which window manager you are running.

[http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

[http://en.wikipedia.org/wiki/Metacity](http://en.wikipedia.org/wiki/Metacity)

The Unity desktop also uses compiz.

---

### Post by shearer4 on 2014-01-20
Great information.  Thank you.  I will try reinstalling 13.10, just to see if I can get it to work. Appreciate your help and direction to good information.  Sorry to take up so much time.

Thanks again.

---

### Post by ibjsb4 on 2014-01-20
You will find a lot of helpful people here :)

Happy Hunting

---

### Post by shearer4 on 2014-01-20
I see that.  Thanks again. How does one mark this thread SOLVED?

---

### Post by ibjsb4 on 2014-01-20
So a reinstall was the solution?

 [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by shearer4 on 2014-01-20
Nope.  Not yet anyway.  Now I can't get a clean re-install of 13.10?  I had similar problems the first time.  I downloaded Ubuntu 13. again. I think somehow the .iso file gets corrupted. If I get a fresh copy it seems to work?  Not sure why that would be except that I am installing from my Mac Disk .iso image.  I have not been able to get a usable DVD image of the ubuntu.iso disks? I'm working on that one also.  Will keep posted.  

AS

---

