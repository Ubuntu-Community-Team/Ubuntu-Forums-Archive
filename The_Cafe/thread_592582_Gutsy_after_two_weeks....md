---
title: "Gutsy after two weeks..."
date: 2007-10-26
forum: The Cafe
---

### Post by kripkenstein on 2007-10-26
Ok, I've been running Gutsy for two weeks now, since the RC. Initially I really liked it. However, a few issues have been nagging at me.

1. I have 512MB of RAM, and on Feisty and previous versions of Ubuntu this was enough. My computer runs 24/7 (I never turn it off), and every few days I would logout and logon to free memory, otherwise I would run into hundreds of megs of swap memory being used. But now in Gutsy, I need to logout-logon at least once a day. I am using the same apps - and I am **not** using desktop effects, nor Tracker - as on Feisty, but my memory usage climbs up much faster.

Typically I have a few Nautilus windows, a few gnome terminals, gedit, firefox, utorrent on wine, and xpdf (the last two chosen because they take less memory than Azureus and Evince, respectively). Yet right now, after 10 hours of use, I am utilizing 220 megs of user memory and 200 megs of swap. That is a lot of swap. And this is right **after** closing and re-opening firefox, which frees up memory (I have only 3 tabs open in firefox, nothing heavy).

2. Firefox 2.0.0.6 on Gutsy is less responsive than on Feisty. When I open multiple tabs at the same time I get 100% cpu usage for a few seconds, then it works fine. Also editing text in a text box with a lot of text in it is slow. These are the exact same tasks I did on Feisty (same websites, etc.), and supposedly the same version of Firefox, but it is very noticably slower here.


I don't know what to do about this, both of these issues make my daily life quite annoying on Gutsy. Are other people experiencing these issues? I've been a long-time Ubuntu user, but this last release is making me consider switching.

---

### Post by wolfen69 on 2007-10-26
it sounds obvious to me. go back to feisty.

---

### Post by blithen on 2007-10-26
I have the same amount of RAM and I experience no problems like this on gutsy. Maybe check for RAM errors with memtest, or something. But I have Desktop effects on minimal and have firefox up a few gnome terminals and maybe in a game on the side and I have no problems.

---

### Post by jrharvey on 2007-10-26
Thats weird. I saw a performance increase on a dell inpiron with 512 memory. Then again I do not leave my computer running 24/7. I usually log out once a day. ill leave it running for a couple of days and see what happens.

---

### Post by Sunforge on 2007-10-26
I have to say that I've got gutsy running in an acceptable amount of RAM but memory consumption goes up quite a bit if I turn on all the eye candy at once. 

This machine has been on all day and at the moment has Firefox, thunderbird and Rhythm box open and it's at 609.8 Mb, which is certainly more than I'd expect on an XP machine but less than something more Vista shaped.

---

### Post by kripkenstein on 2007-10-26
Thanks for the responses so far.

Well, from reading more, it seems I am not the only one with these issues. One suggestion was that the flash plugin was to blame (leaking pixmaps in Xorg). So I uninstalled flash, and I'll try to go a day without YouTube, see how that affects memory usage ;)

But it also seems most people these days have 1GB of ram (or more), and my computer is simply getting too old for modern OSes. Ah well.

---

### Post by Sunforge on 2007-10-26
I can certainly confirm the flash plugin, installed via the whizzy new firefox add-on thingy.

---

### Post by kripkenstein on 2007-10-31
Well, I ran without flash for a day or so - no improvement. Disappointing.

I installed Xubuntu instead of Ubuntu, in hopes that this will work on my 512MB of RAM. So far (a few hours) so good, but I'll only know in a few days.

Side note: Wow, what an amazing default theme in Xubuntu! Much nicer than Ubuntu :)

---

