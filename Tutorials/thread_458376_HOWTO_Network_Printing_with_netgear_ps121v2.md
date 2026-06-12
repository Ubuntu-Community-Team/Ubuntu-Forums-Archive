---
title: "HOWTO: Network Printing with netgear ps121v2"
date: 2007-05-29
forum: Tutorials
---

### Post by n8dude on 2007-05-29
Hey guys, i've recently bought one of these
[http://netgear.com/Products/PrintServers/WiredPrintServers/PS121.aspx](http://netgear.com/Products/PrintServers/WiredPrintServers/PS121.aspx)
and i've been messing around in CUPS to get it to work.
And i've found a way to get it to work. So i'm posting this how-to.

First, get into cups by using this url: [http://localhost:631/]("http://localhost:631/")

and get to the page where you set up new printers.
  
Type in the Name that you want the printer to be, the location (like if its in your basement, type basement) and the description.Once thats all done click continue. Once on the next page, Appsocket/Hp Jetdirect. Then for the  
uri, type this into the bar: lpd://(print servers ip goes here)/PS1B88CD_P1

Then select your make and then model, and click next. Then test your setup and let me how it goes!;)

                                                                                                                                                          --- n8dude---

---

### Post by Kabamaru on 2007-09-11
Thanks for the quick howto, it worked wonderfully ^_^

---

### Post by chanders on 2007-09-12
Perfect. Thanks!

---

### Post by kenlyle on 2007-10-12
Yeah, awesome!  One tiny thing, the string like PS1B88CD_P1 is the Device Name of the underside of the print server.

Thanks!
K

---

### Post by JCoster on 2008-01-20
I know this is kind of bringing the thread back from the dead but I'm experiencing a few problems whilst trying to get this to work on Gutsy with my Netgear PS121v2 and Epson Stylus Photo R265.

Basically, I can print off a few documents but after these have finished it will just print off page after page of strange characters...  They're pretty much the typical characters you get when printing goes wrong.

I can scan in a page if you like but I'm sure you know what i mean.

But yeah, the only way I can stop this is by resetting the PS121v2.  Then I can print a few things again but then come the characters...

I've deleted and readded the printer following instructions down to the finest detail but still get this problem.

Has anyone else had the same trouble?

Thanks.
JC

---

### Post by rmcalister on 2008-02-12
dude,
 ps121v1 setup works fine -w- HP Photosmart C3180
Thanks, Robert

---

### Post by sbrandon on 2008-03-08
Was able to setup with instructions as above and print once but then nothing.  Instructions worked great but am stumped now> any ideas???

---

### Post by Hatfield on 2008-07-26
> **n8dude said:**
> ...
Type in the Name that you want the printer to be, the location (like if its in your basement, type basement) and the description.Once thats all done click continue. Once on the next page, Appsocket/Hp Jetdirect. Then for the  
uri, type this into the bar: lpd://(print servers ip goes here)/[COLOR="Red"]PS1B88CD[/COLOR]_P1
...

This worked for me and thank you!

But while trying to configure my Macbook OS using the same technique, I may have stumbled across something that needs clarification.

I'm pretty sure the item above I highlighted in red is the Print Server Name that may be different from one PS121 to another.  For instance, my PS121's print server name was "PS3B4066" which is very similar to the original poster's "PS1B88CD".

So the URI should read: lpd://(print server ip goes here)/(print server name goes here)_P1
without the parentheses.

My Linux box accepted the "wrong" name just fine and printed, but the Macbook OS didn't which led me this conclusion.

Just something to consider.

---

### Post by zizuza on 2008-12-27
Hello,
I've try to install a printer following the  instruction but don't work correctly. When print a test-page on [http://localhost:631/](http://localhost:631/) the process run correctly (I see spooling process and results), but the printer don't print.

I've Ubuntu 8.04 (hardy)
model of my network printing: PS121v2
firmware version: 1.0.07
ip address: 192.168.1.104
Server Name: STAMPANTE.
model printer: HP Laserjet 1020
I've use this driver: HP LaserJet 1020 Foomatic/foo2zjs (recommended)

I've try to use this URL: lpd://(print servers ip goes here)/PS1B88CD_P1
and also lpd://(print servers ip goes here)/STAMPANTE_P1 but the result it's always the same.
please can you help me?

---

### Post by Uig on 2009-01-28
That was very cool, I'm new to Ubuntu and Linux and even I could do that. Thanks a million. For the record my home system is made up as follows. 1 Dell laptop and  2 other desktops runing Ubuntu 8.04, and one Dell laptop running XP with Zone Alarm security suit. Printer is Canon MP780 connected to Netgear PS121 via ethernet hub and Netgear wireless router DG834Gv2. The Dell laptop running Ubuntu is conected to the Netgear wireless router DG834Gv2 by wireless conection.

Once again thanks for tip.

---

### Post by gordonh on 2009-02-28
My problem is that I can't see the PS121 print server on the network.

There's been a problem for a week or so now.  Initially jobs were failing occasionally, and then usually.

I had to have the printer plugged directly into the windows machine my wife uses (I almost never print anything).

I've a bit of time now to look into it.

The wireless router into which the PS121 is plugged doesn't show it as connected

PING of 192.168.0.147 (where the printer was originally installed) and so far (about an hour later) there's no response.

Other than a dead PS121 does anyone have any idea what's happening here?

---

### Post by Browner87 on 2010-03-07
Worked flawlessly for me! Thanks a million! I can't get a version of the printing tools for Windows 7 so I just host it on my linux server as a shared printer. It may sound dumb to host a network shared printer from a central server, but for love nor money could I make Linux print reliably to my specific printer, but this print server works great!

Thanks!

---

### Post by manco1911 on 2011-11-21
Exelent !  

this just worked flawlessly running Uuntu 11.10 (oneric ocelot) x64. 
just to keep records of success..

Testing on 32 bit right now.. 
its giving a bit of trouble.. maybe some dependencies?.. will check on that and update my post.
[UPDATE]
haha, nope, no extra dependencies needed.. it seems that if you dont configure the right IP address it wont work.. :D

Worked great again. +1 !

---

