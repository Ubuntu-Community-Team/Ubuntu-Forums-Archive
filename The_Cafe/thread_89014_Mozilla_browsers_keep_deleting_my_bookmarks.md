---
title: "Mozilla browsers keep deleting my bookmarks"
date: 2005-11-11
forum: The Cafe
---

### Post by BWF89 on 2005-11-11
So I've been useing Firefox since November 2004. Starting during the summer Firefox lost my bookmarks & settings due to a corrupt file 3 or more times. So I switched to SeaMonkey (an offshoot of the discountinued Mozilla Suite) and used it for about a week. It worked just fine. Today when I clicked on the bookmarks button everything was gone.

I'm useing Windows XP on a Compaq Precario. What's going on?

---

### Post by blastus on 2005-11-11
I've never had this problem and I've been using FireFox (previously Firebird) since 2003. You can (and probably should) backup your bookmarks from time to time anyway. On Linux just backup the bookmarks.bak and bookmarks.html files in your profile. These files will be in a subdirectory in the ~/.mozilla/firefox/ directory. On Windows these two files will be nested somewhere in the "Documents and Settings" directory--I don't remember exactly where but they are easy to find. You can backup your whole profile if you want but I find it easier just to backup the bookmarks.bak and bookmarks.html files.

---

### Post by BWF89 on 2005-11-11
All I found was Bookmarks.HTML. But I'm useing Windows so it might be different that what your have.

Still, I don't know why it keeps doing this. Mabye it's a problem with Windows. I last installed it Christmas of last year.

---

### Post by blastus on 2005-11-11
I not sure why your profile is getting corrupted--I've never had that problem on Windows (or Linux.) The Mozilla forums may shed some more light on this issue.

The nice thing about the bookmarks.bak and bookmarks.html files in your Mozilla profile, is that you can transfer them from Firefox on Windows to Firefox on Linux no problem. This is how I got all my bookmarks from Firefox on Windows to Firefox on Linux. I didn't bother with the rest of my Mozilla profile as the bookmarks were the most important to me and I can change all the settings I want in a couple of minutes in a new profile.

---

### Post by BWF89 on 2005-11-11
It's not just the fact that **I could** backup my bookmarks which I could easily do. But the fact that I would feel bad reccomending Mozilla products over MS ones when they don't work right for me.

I think looseing my bookmarks might have something to do with my illegually shutting down my computer. Sometimes my PC freezes up and I need to hit the switch or sometimes I just need to shut it down really fast because my parents need me in the car to go somewhere fast and they don't like the PC on while their not useing it.

But if I need to illegually shut down my PC I always log out of the browser first. Or does your browser run for a minute after you log out of it?

---

### Post by bored2k on 2005-11-11
Whatever happened to making the bookmark directory READ only?

---

### Post by TravisNewman on 2005-11-11
if it was read only, how would you add new bookmarks?

I've been using firefox since it was phoenix, then firebird, then firefox. Its been my default browser since the pre-pre-alpha developer preview, because I've never had any crippling bugs crop up. Until I lost everything in a computer crash, I had a bookmarks.html that had lasted all through those alphas, betas, and the final.

I have heard of this happening, however, because of not adequately shutting down firefox or the pc.

---

### Post by Bairsairk on 2005-11-11
Use Bookmarks Synchroniser extension to save your bookmars to a xml file on a ftp.
I used it to backup my bookmarks, it works on windows and ubuntu :)

---

### Post by wmcbrine on 2005-11-11
When I read about this problem on the Mozillazine forums, there was a strong correlation with improper shutdowns. It only happened on Windows, AFAICT. My guess was that FF was opening the bookmarks file at startup and keeping it open, instead of opening it only when needed.

[quote=BWF89]sometimes I just need to shut it down really fast because my parents need me in the car to go somewhere fast and they don't like the PC on while their not useing it.[/quote]
I think this is pretty silly. Does it take that long to shut down? Get your parents to either give you the few extra seconds to shut it down properly, or to let you leave it on. Explain to them what happens when you don't.

---

