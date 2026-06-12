---
title: "Newbie needs help finding virtual C drive"
date: 2009-07-18
forum: Wine
---

### Post by maca on 2009-07-18
I'm using ubuntu and have successfully installed several windows programs using wine.  But one program failed to make a shortcut when I installed it, so I can't start the program.  When I go to wine and select "browse virtual c drive", nothing happens.  How can I access the virtual drive to try and run this program?  I gather through my searching that it's supposed to be at home/username/wine, but when I try to go there the wine directory is invisible.  Thanks for any help.

-------------------------------------------------
edit: just answered my own question; figured out to select "show hidden files".

---

### Post by llamakc on 2009-07-18
> **maca said:**
> I'm using ubuntu and have successfully installed several windows programs using wine.  But one program failed to make a shortcut when I installed it, so I can't start the program.  When I go to wine and select "browse virtual c drive", nothing happens.  How can I access the virtual drive to try and run this program?  I gather through my searching that it's supposed to be at home/username/wine, but when I try to go there the wine directory is invisible.  Thanks for any help.

-------------------------------------------------
edit: just answered my own question; figured out to select "show hidden files".

```


cd ~/.wine


```

---

### Post by DanYoSon on 2009-07-18
also ctrl+H works in nautilus (file browser)

---

### Post by maca on 2009-07-18
Thanks for the replies.  Turns out the program won't work in wine; I've had the same problem on other distros of Linux but the wine on ubuntu seems so much more intuitive that I was hoping for a better result.  Guess this is just one of those windows programs that doesn't like wine.

---

### Post by andrea000 on 2009-07-20
Do you have a error message maybe it would be
simple to work out.Did you have the software
installed before that would tell me why it isn't
showing up

---

### Post by MadJerry on 2009-09-08
> **maca said:**
> When I go to wine and select "browse virtual c drive", nothing happens.  How can I access the virtual drive to try and run this program?  

-------------------------------------------------
edit: just answered my own question; figured out to select "show hidden files".

I have this same problem but I dont know where to select show hidden files...

---

