---
title: "Running Paltalk Scene on Ubuntu (updated again)"
date: 2010-12-23
forum: Wine
---

### Post by dekinstoke on 2010-12-23
Paltalk is a popular chat/messaging service that runs on Unix servers and yet they have no Linux version of the software. Which seems a bit daft. Paltalk Scene WILL work under wine with a few "tweaks", listed below

Ok here we go

Get Wine1.3 installed first: in Terminal

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3

Now get the winetricks script, save to Home folder as winetricks.txt

[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

You will need to make the script executable by right clicking winetrick.txt, Properties, check the "make executable" box. OK out.

Ok now run winetricks ...just double click it and select Run.

You need to install IE7 and richedit30 with winetricks. Do that then.

Now download and install MSN Messenger 7 :

[http://www.oldversion.com/download_MSN_Messenger_7.0.html](http://www.oldversion.com/download_MSN_Messenger_7.0.html)

Install it using right click and "open with Wine windows program loader".

Download Paltalk and install it.

Done.

Fonts look a bit weird your end and smilies do not show on your end, however everything looks ok in the rooms. Sound seems to work fine too. 6130

---

### Post by bou3lam on 2011-01-14
and its working ?

---

### Post by dekinstoke on 2011-01-15
Would I post the thread if it WASN'T working? Bit of an oxymoron that really ....

---

### Post by big macc on 2011-04-22
still crashes alot if there is any other solution like a plugin for pidgin or anything to run paltalk on linux . if you know any other successful methods please help. i hate *indows and i want to use paltalk.

---

