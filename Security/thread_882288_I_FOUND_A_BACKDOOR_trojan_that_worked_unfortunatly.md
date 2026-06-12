---
title: "I FOUND A BACKDOOR trojan that worked unfortunatly?"
date: 2008-08-06
forum: Security
---

### Post by adn258 on 2008-08-06
Well it's crazy becasue it's actually an old windows backdoor trojan beast 2.07 but unfortunately if you click the server and you have wine running it works I tested it.  Wine says nothing and nothing pops up so someone could running ubuntu infect themselves.  The uppit link bellow has a download to the file.  I didn't upload it it was the person from the youtube video bellow which is why this has been downloaded so many times.  Note the download is just the client you build the server with the client.  Anyway both the client and the server work on ubuntu 8.04 with the latest version of wine and when you click the server port 6666 will be listening for a connection on your computer I tried netstat -tlp so it's confirmed.  Anyway what should we do?  It annoys me that something is out there that works on ubuntu lol.  I got rid of it BTW the Dll's that make it work are in the wine folder but yeah.  What do people here think? BTW  I connected to myself AFTER I downloaded it  



<snip>

[http://www.youtube.com/watch?v=NGxwfv_lzMM](http://www.youtube.com/watch?v=NGxwfv_lzMM)

---

### Post by mb_webguy on 2008-08-06
No one ever said that Linux was bulletproof, only that it doesn't get viruses.  It can still have other kinds of security vulnerabilities.  If you run Windows under Linux, whether in a VM or Wine, you risk falling victim to Windows' security flaws.  

In Wine, at least, programs don't run themselves, which is part of the reason you don't have to worry much about viruses even when running Wine.  The viruses can't install themselves and replicate.  You have to choose to run a particular program.  But if you do choose to run a program, and that program is designed to do nasty things to your computer, it will likely do nasty things to your computer -- within the confines of Wine or your VM.

Even the backdoor trojan you found shouldn't allow hackers to do much outside of your Wine installation.

---

### Post by PmDematagoda on 2008-08-06
adn258:- Please do not post such links to files that may potentially harm a user(I'm talking about a Windows user), just a description of your problem along with the description of the trojan should be more than enough.

---

### Post by adn258 on 2008-08-06
> **PmDematagoda said:**
> adn258:- Please do not post such links to files that may potentially harm a user(I'm talking about a Windows user), just a description of your problem along with the description of the trojan should be more than enough.

Sorry and yes unfortunatly you can get too stuff outside the wine part of the system take a look at the PHOTO of it on my computer it says connected which it is and the file manager part can get too anything BUT the person above me is right when you restart the system port 6666 isn't listening anymore so that is good news but this shows that even we are vulnerable check the photo in the link bellow.  

Peace


[http://img299.imageshack.us/my.php?image=screenshottu6.png](http://img299.imageshack.us/my.php?image=screenshottu6.png)

---

### Post by The Tronyx on 2008-08-06
> 
Sorry and yes unfortunatly you can get too stuff outside the wine part of the system take a look at the PHOTO of it on my computer it says connected which it is and the file manager part can get too anything BUT the person above me is right when you restart the system port 6666 isn't listening anymore so that is good news but this shows that even we are vulnerable check the photo in the link bellow.

/me yawns

On a less sarcastic note, what this tool does is establish a listening connection which is exactly what the program is intended to do.  It's not just virii that will do this, if you downloaded a game server for windows to allow other people to game with you, it too would open a listening connection.  Your title is humorously misleading.  You ran this program under WINE and it worked (which is what wine is supposed to do) and this is somehow problematic...

I am not trying to come off as incredibly rude, but from what I can tell you aren't aware enough of how this stuff works to really understand what is happening.  If you wanted to take a closer look at just what the program is doing you could try using Wireshark.

If you don't want ports to listen, just stealth them dude.

---

