---
title: "Installing GNOME in Arch Linux problem"
date: 2009-07-24
forum: The Cafe
---

### Post by Jimleko211 on 2009-07-24
I'm having a problem installing GNOME in a virtual machine with Arch Linux on it.  I'm following the guide at [http://wiki.archlinux.org/index.php/GNOME ]("http://http//wiki.archlinux.org/index.php/GNOME")

Things ran pretty smoothly in the beginning.  I had to reinstall the gnome-extra package a few times to fill in the stuff that I missed and to redownload a corrupted package, but I thought I got everything right.  I go down to the part where I have to add the Fuse module to /etc/rc.conf.  I find the Module=() section, and I add in fuse, but unlike the guide, usblp is not in there.  I didn't add it since I didn't want to break anything.

I try to launch the gnome-desktop, and it gives me this error message:
** (gnome-session: 1584): WARNING **: Cannot open display:

Did I do anything wrong?  I'm posting here on UF because it seems like Arch users have a significant minority, and they seem pretty knowledable.

---

### Post by CJ Master on 2009-07-24
Drop back to terminal and remove fuse. Does it work now?

---

### Post by Jimleko211 on 2009-07-24
By removing fuse, do you mean taking it out of /etc/rc.conf?  If so, I did as you said, and I still get the same error message.

---

### Post by CJ Master on 2009-07-24
Yes, that's what I meant. X runs fine, right? You mentioned you launced gnome-desktop, did you do it through K/X/GDM? Can you think of anything you've done that might have caused this?

---

### Post by Jimleko211 on 2009-07-24
No, X doesn't work fine.  I just typed the command "gnome-session" into the terminal, and it gives me that error.  I'm sorry, I should have been clearer.

---

### Post by CJ Master on 2009-07-24
Oh! So X is broken!

What happens if you type startx in the terminal? The same error you get when you run GNOME? Have you installed HAL?

---

### Post by Icehuck on 2009-07-24
Are you creating your own xorg.conf or are you going without it? If you have a xorg.conf file, what does  "X -config /etc/X11/xorg.conf" result in?

---

### Post by Jimleko211 on 2009-07-24
I think what happened is that I didn't install Xorg.  I'm doing it now, hoping it works.
> 
Are you creating your own xorg.conf or are you going without it? If you have a xorg.conf file, what does "X -config /etc/X11/xorg.conf" result in? 

A blank screen.

> 
What happens if you type startx in the terminal? The same error you get when you run GNOME? Have you installed HAL? 

I believe I installed HAL, yes.  When I type in startx...now I get a bunch of windows.  Maybe I should try GNOME again.

---

### Post by Jimleko211 on 2009-07-24
Gnome only works after I type in startx, but then the whole area looks weird o.o

---

### Post by CJ Master on 2009-07-24
> **Jimleko211 said:**
> I think what happened is that I didn't install Xorg.  I'm doing it now, hoping it works.


A blank screen.



I believe I installed HAL, yes.  When I type in startx...now I get a bunch of windows.  Maybe I should try GNOME again.

If you get a bunch of windows then you have, in fact, installen X.org.

Can you move your mouse and type in X? Is it in your monitors resolution?

---

### Post by CJ Master on 2009-07-24
> **Jimleko211 said:**
> Gnome only works after I type in startx, but then the whole area looks weird o.o

Need moar detail.

---

### Post by Jimleko211 on 2009-07-24
> **CJ Master said:**
> If you get a bunch of windows then you have, in fact, installen X.org.

Can you move your mouse and type in X? Is it in your monitors resolution?
Yeah, that works.  It allowed me to launch gnome through that, but it's kinda weird because it seems like whenever I launch something in Gnome, I have to place it manually through X?  And there are a bunch of Xorg stuff on the top and bottom.

---

### Post by Jimleko211 on 2009-07-24
> **CJ Master said:**
> Need moar detail.
See post above.

---

### Post by CJ Master on 2009-07-24
> **Jimleko211 said:**
> Yeah, that works.  It allowed me to launch gnome through that, but it's kinda weird because it seems like whenever I launch something in Gnome, I have to place it manually through X?  And there are a bunch of Xorg stuff on the top and bottom.

I'm afraid I don't get what you mean. Can you take a screenshot?

---

### Post by LookTJ on 2009-07-24
Just wondering, did you include hal and fam in rc.conf?

---

### Post by justsomedude on 2009-07-24
Look here:


[http://wiki.archlinux.org/index.php/Gnome#Running_the_GNOME_Desktop](http://wiki.archlinux.org/index.php/Gnome#Running_the_GNOME_Desktop)

---

### Post by Jimleko211 on 2009-07-24
> **CJ Master said:**
> I'm afraid I don't get what you mean. Can you take a screenshot?
Absolutely.

> **LookTJ said:**
> Just wondering, did you include hal and fam in rc.conf?
I did.

---

### Post by Barrucadu on 2009-07-24
Add "exec gnome-session" to your .xinitrc file.

---

### Post by Jimleko211 on 2009-07-24
> **Barrucadu said:**
> Add "exec gnome-session" to your .xinitrc file.
Did that and now X won't start.
EDIT: And now when I go back to remove it it's not there...

---

### Post by Jimleko211 on 2009-07-24
Well, I went back and added it again, and now whenever I launch startx, it launches Gnome.  Thanks!

---

### Post by kk0sse54 on 2009-07-24
This entire thread sounds like it could have been solved if you followed the [Beginners Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide"). The fantastic documentation is there for a reason ;)

---

### Post by Jimleko211 on 2009-07-24
Yeah, I agree, that's how I mostly solved the problem.  I honestly didn't know it existed, I just googled "GNOME in Arch Linux".  Sorry.

---

### Post by CJ Master on 2009-07-24
> **Jimleko211 said:**
> Well, I went back and added it again, and now whenever I launch startx, it launches Gnome.  Thanks!

So Gnome is normal and doesn't have that X stuff?

---

### Post by Jimleko211 on 2009-07-24
> **CJ Master said:**
> So Gnome is normal and doesn't have that X stuff?
Correct!  I still gotta find out how to make it start on default (and how to add users), but I'll figure it out in due time.

---

### Post by unknownPoster on 2009-07-24
> **Jimleko211 said:**
> Correct!  I still gotta find out how to make it start on default (and how to add users), but I'll figure it out in due time.

All of which are in [The Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide")

---

### Post by kk0sse54 on 2009-07-24
> **unknownPoster said:**
> All of which are in [The Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide")

/offtopic 

I didn't know you were incognito on this forum :)

---

### Post by unknownPoster on 2009-07-24
> **C!oud said:**
> /offtopic 

I didn't know you were incognito on this forum :)


/offtopic

I'm ***everywhere***... :twisted:


/on-topic

Actually, now that I think about it. There's really nothing that you have to figure out by yourself if you use Arch. Almost everything you could think of is on the wiki. 

However, if you run [Testing] or are intentionally trying to break your system, you're on your own. :P

---

### Post by Jimleko211 on 2009-07-24
Wow, this beginner's guide has everything o.o  Arch is gonna rock once I get my external hard drive to back up all my data! :D

---

### Post by terminhell on 2009-10-02
A lot of your problems will be solved by starting gnome or any other DE this way:
 
```
exec ck-launch-session  gnome-session
```

---

