---
title: "Logged in as root"
date: 2009-08-12
forum: The Cafe
---

### Post by frt975 on 2009-08-12
:lolflag:
How to reproduce:
Remove the top panel.
Run ```
sudo debconf gnome-panel
```

---

### Post by 3rdalbum on 2009-08-13
Or you could do:

```
sudo killall gdm
```

And then, at the text terminal:

```
sudo startx
```

It's not like it's a security flaw, as you need to be a sudoer in order to start Gnome Panel as root.

---

### Post by Barrucadu on 2009-08-13
Or even fiddle with the GDM settings to let you log in as root&#8230;

---

### Post by frt975 on 2009-08-13
Once you run it any script can do anything. I was able to edit menu.lst without sudo.

---

### Post by JillSwift on 2009-08-13
> **frt975 said:**
> Actually yes it is, I was able to edit menu.lst without sudo.
See that bit where you invoked sudo to start the panel?

That's why it's not a security flaw. You **did** have to use sudo, you just used it earlier.

---

### Post by Barrucadu on 2009-08-13
> **frt975 said:**
> Actually yes it is, I was able to edit menu.lst without sudo.

Well of course you were. You had the panel running as root, so any subprocesses were run as root. It's not a security flaw though, only a sudo-user could do that.

---

### Post by frt975 on 2009-08-13
I would be one if one of the few viruses infected the computer or I did something stupid like delete a important system file by accident.

---

### Post by Trison on 2009-08-13
So what happens when some clever shrew finds a security breach in firefox (or any other web-connected app) that you're conveniently running as root?

---

### Post by Barrucadu on 2009-08-14
> **frt975 said:**
> I would be one if one of the few viruses infected the computer or I did something stupid like delete a important system file by accident.

If you think you're at risk of deleting important files by accident, running a file manager as root is not for you :P

> **Trison said:**
> So what happens when some clever shrew finds a security breach in firefox (or any other web-connected app) that you're conveniently running as root?

This too. Running things as root is just *bad*.

---

### Post by gnuvistawouldbecool on 2009-08-14
> **Barrucadu said:**
> If you think you're at risk of deleting important files by accident, running a file manager as root is not for you :P

This is why windows is insecure.

That said, why anyone would ever delete a folder called '/usr' or 'WINDOWS' is beyond me...

---

### Post by Copernicus1234 on 2009-08-14
> **gnuvistawouldbecool said:**
> This is why windows is insecure.

That said, why anyone would ever delete a folder called '/usr' or 'WINDOWS' is beyond me...

To be fair, its been more secure since Vista. I dont use it, but at least I know that these days the default user doesnt have root anymore. Even a crap OS such as Windows is sometimes taking a step forward. :)

---

### Post by Zack McCool on 2009-08-14
> **frt975 said:**
> I would be one if one of the few viruses infected the computer or I did something stupid like delete a important system file by accident.

No, it still wouldn't be a flaw.  You would be the flaw.  Any number of problems can be caused by bad user practices, but they are not system flaws.

You called the panel as root.  You intentionally broke the security model.  That's not a flaw in the model, but rather a strength of linux, in that it will let you do pretty much anything you want, even if it isn't the smartest thing to do.

---

### Post by cmannnn on 2009-08-14
Isent like that in most aspects of life tho cars dont crash them selvs you know

---

### Post by lisati on 2009-08-14
We might laugh about being able to bypass security and other precautions or brush them aside as inconsequential - until we make a big muck-up that takes several hours to fix. And that's before we figure in the possibility of leaving ourselves vulnerable to mischief done by others.......

---

### Post by gnuvistawouldbecool on 2009-08-14
> **Copernicus1234 said:**
> I dont use it, but at least I know that these days the default user doesnt have root anymore. Even a crap OS such as Windows is sometimes taking a step forward. :)

Yes, one now has to click a yes/no dialog to delete stuff as root instead, no password needed.  At least, thats what Win 7 did for me, not that I  tried to delete it like that.

---

### Post by Barrucadu on 2009-08-14
> **gnuvistawouldbecool said:**
> Yes, one now has to click a yes/no dialog to delete stuff as root instead, no password needed.  At least, thats what Win 7 did for me, not that I  tried to delete it like that.

Better than nothing. Hopefully it will cause people to think. If not, at least us geeks will be able to say "Well, it did warn you that deleting it could mess up your computer&#8230;" when they seek our help.

---

