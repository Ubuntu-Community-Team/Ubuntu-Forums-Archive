---
title: "SSH and PuTTY: Odd Characters"
date: 2006-04-26
forum: Server Platforms
---

### Post by charlie. on 2006-04-26
I am using PuTTY on my Windows XP machine to connect to my Ubuntu server. I keep observing some very funny characters on the screen. These do not look right. It is as if the font used by PuTTY does not support the character set that it is running in - I have left the PuTTY display settings set to their defaults.

Attached is a screenshot of this problem, showing the error in a man page. I have also seen it in aptitude and other areas. Please take a look and comment on this problem.

---

### Post by xenmax on 2006-04-27
Is this problem only for man pages?
I was recently looking on this problem as the terminal i prefer, mrxvt also does not display man pages correctly, where as it is fine in xterm and gnome-terminal. From my searching, what i concluded (could be wrong) was that this is related to UTF-8 character encoding which mrxvt currently does not support.

I dont use Putty much. But i just had a look at it and "man grep" would display similar odd characters as you described. I then logged out, changed character encoding to UTF-8 and it was solved!! Although not entirely, some characters were still being displayed as recatngular blocks.

Try this, it may help -> When you launch putty, you have on left side various config options - in that, go to Windows -> Translation -> Has a drop down menu for character set - mine default was some ISO blahblah - change it to UTF-8 and hopefully your problem (part of it atleast) should be solved.

Hope this helps.

---

### Post by charlie. on 2006-04-27
Thanks, xenmax. I will try changing PuTTY's character encoding as you suggest. I would not be surprised to find that this IS a UTF8 problem

I have seen this in many MAN pages, APTITUDE and other applications. It is much more prevalent if I change the width of my PuTTY window to something other than the default width.

---

### Post by charlie. on 2006-04-28
I changed my language to UTF8 in PuTTY's settings. This fixed the problem that I showed with the 'apt-cache' man page. I also get funny square boxes in man pages now. I think that they are line continuation characters or something.

Alternatively, they could be caused by missing glyphs in the Windows font.

---

### Post by mdecler2 on 2006-07-25
I also have had funny characters in my man pages, including empty boxes as charlie has stated, but also a's with circumflexes on them.

I was using rxvt-xterm, but no longer! I've decided to switch back to xterm.
That seemed to solve the problem.

As for puTTY, I also use puTTY to SSH to my Ubuntu machine. I found similar circumflexed a's in the man pages, but surprisingly the UTF8 setting in the Translations menu only turned the strange a's into a combined AE character (I do not know what that character is called).
Upon changing the font to Lucida Console, the strange characters died, so puTTY with Lucida Console and UTF encoding works well.

Thanks for all your help!

---

### Post by skullforger on 2006-11-15
Hi all,

I had exactly the same PUTTY problem as charlie : odd characters, often unnecessary circumflexes in man pages but also in applications like BitchX or in the output of lm-sensors. Changing the translation to UTF-8, as xenmax suggested, worked very well for me, and it works with all of the fonts I tried.

Thanks for the help!

---

### Post by fakie_flip on 2007-06-06
I have the same problem but worse except that its not with putty. It happens when I push control alt f1 to go to a linux console and run mc (midnight commander) or finch (text based pidgin). Maybe it has something to do with ncurses. Does anyone know how to fix it?

---

### Post by cong06 on 2007-12-06
I've got a similar problem with finch and PuTTY....

No problems when I use ssh instead of PuTTY though...

---

### Post by Endolith on 2008-05-02
I use fish as my default shell, and I saw these characters all the time when accessing it through PuTTY SSH.  Changing to UTF-8 seems to fix it (the â¦ is actually supposed to be an ellipsis: …)

---

