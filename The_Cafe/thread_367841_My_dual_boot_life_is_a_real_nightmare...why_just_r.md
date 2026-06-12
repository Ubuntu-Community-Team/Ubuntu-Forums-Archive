---
title: "My dual boot life is a real nightmare...why? just read"
date: 2007-02-22
forum: The Cafe
---

### Post by Gargamella on 2007-02-22
maybe you would ask me: why you still dual boot if you like ubuntu so much?

well the reason is totally absurd.

I do everything with ubuntu from surfing the net, writing.... till burning DVDs but WinXP is still inside my case because off a game: Wolfestein Return to the Castle:Enemy Territory.

It is a linux perfectly supported game, but when I run it:black screen and no more.
It is because off my video card drivers on linux i think (it runs great on winxp with and intel 900 video card)

This fantastic and very addicting game (sometimes i played it from midnight to 4 am, and once I also began again at 12 when I got up) is saving Windows presence on my laptop...


isn't it a nightmare?...I think yes

---

### Post by halfvolle melk on 2007-02-22
> **Gargamella said:**
> when I run it:black screen and no more.
It is because off my video card drivers on linux i think (it runs great on winxp with and intel 900 video card)
Are you sure it's not Beryl or something like that?

---

### Post by Zimmer on 2007-02-22
> **Gargamella said:**
> 
but when I run it:black screen and no more.
It is because off my video card drivers on linux i think (it runs great on winxp with and intel 900 video card)
.
isn't it a nightmare?...I think yes

What is the result  of entering this at the Terminal ?
  glxinfo |grep direct  

If this reports Direct Rendering enabled then it may not be a video issue.

I had a similar experience with a black screen, even swapped video cards to test it, and it was a SOUND problem..

Run ET from the terminal , use the key to bring down the in-game console and type quit, then have a look at the terminal contents to look for clues... (post it here and I will see if I can help)
Also have a look at this thread.... 
[http://ubuntuforums.org/showthread.php?t=80926&page=2](http://ubuntuforums.org/showthread.php?t=80926&page=2)

The problem for the person posting was that he had not followed the instructions properly for installing the Game, regarding changing permissions on the install file ..  

once you have ET running...  bye bye WinXP....

Regards
Zimmer

---

### Post by Gargamella on 2007-02-23
I do not use beryl...now going to try what zimmer said

---

### Post by Gargamella on 2007-02-23
here it is my result:

andrea@andrea-laptop:~$ glxinfo |grep direct 
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes


do you think it's all right?

---

### Post by Zimmer on 2007-02-23
> **Gargamella said:**
> here it is my result:

andrea@andrea-laptop:~$ glxinfo |grep direct 
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes


do you think it's all right?

Well, I have searched for similar error messages and there are a few of those about. However, if Direct rendering is working I would try running ET from the terminal and copying the text from the terminal afterwards  to look at the error messages....

---

### Post by Mateo on 2007-02-23
the reason I still dual boot is for media center.  ATI drivers aren't very good so overscan makes mythtv look bad.  Also mythvideo isn't a very good product (it only launches mplayer, doesn't use it's own GUI as a mplayer frontend, can't change zoom ratio on-the-fly).

---

