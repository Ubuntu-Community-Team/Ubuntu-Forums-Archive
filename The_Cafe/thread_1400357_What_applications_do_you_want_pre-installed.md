---
title: "What applications do you want pre-installed?"
date: 2010-02-06
forum: The Cafe
---

### Post by Warpnow on 2010-02-06
So, we inevitably face this problem in the linux world. The distro has X music app, you prefer Y, you want A, they have B. 

Which of the following application types would you want pre-included, even if it was not the one you personally prefer, and which of them would you prefer be left out all together, so you can install your own?

Feel free to add to the list.

Accessories
-Text Editor
-Basic Calculator
-Scientific Calculator
-Note Software
-Screenshot Application
-Dock
-Terminal Emulator
-Encrypted Volume Manager (Mount encrypted files as directories easily)
-Archive Manager

Games
-Basic Set
-Intermediate Set
-Advanced Set
-Specific 3D Games

Graphics
-Gimp
-Image Viewer
-ComicBook Viewer
-Basic MSPaint style Application

Multimedia
-DVD/CD Ripper
-DVD/CD Burner
-Music Manager
-Basic Music Player
-Video Player
-Media Center Application

Internet
-Gecko Browser
-Webkit Browser
-Mail Client
-Torrent Client
-Instant Messaging Client
-FTP Client
-Text Based Game Client
-Web Page Editor/Composer
-Standalone IRC Client

Office
-Dictionary
-Word Processor
-Spreadsheet
-Presentations
-OpenOffice Complete Suite
-Ebook Reader
-Mind Mapping
-Distraction Free Writing Program

Utilities
-Command Line System Monitor (aking to Htop)
-GUI System Monitor
-Software Center
-Bootup Manager (BUM)
-Firestarter Firewall GUI
-Software Center
-Wine

---

### Post by Roasted on 2010-02-06
As long as they're in the repos, I don't really care. There's a lot of stuff I install that I prefer over top of the default application in Ubuntu, but it's never bothered me because it's so easy to get it.

Pidgin over Empathy.
Thunderbird over Evolution.
Exaile over Rhythmbox.

etc...

---

### Post by dcommini on 2010-02-06
Personally I would like to see WINE and Firestarter come included. WINE makes it easier when I switch people over from Windows and they still want to use many Windows only products. Firestarter just because I like knowing that a firewall that I can configure is already there with out much searching.

---

### Post by Warpnow on 2010-02-06
> **dcommini said:**
> Personally I would like to see WINE and Firestarter come included. WINE makes it easier when I switch people over from Windows and they still want to use many Windows only products. Firestarter just because I like knowing that a firewall that I can configure is already there with out much searching.

I've always found it odd that it isn't included by default.

---

### Post by juancarlospaco on 2010-02-06
I got my own meta-packages, fixed for me.

---

### Post by phillychease on 2010-02-06
> **dcommini said:**
> Personally I would like to see WINE and Firestarter come included. WINE makes it easier when I switch people over from Windows and they still want to use many Windows only products. Firestarter just because I like knowing that a firewall that I can configure is already there with out much searching.

just like what roasted said...some programs are easy to get.
WINE has a deb and firestarter is in the ubuntu software center.
just a few clicks then you have it!

---

### Post by lovinglinux on 2010-02-06
> **dcommini said:**
> Personally I would like to see WINE and Firestarter come included. WINE makes it easier when I switch people over from Windows and they still want to use many Windows only products. Firestarter just because I like knowing that a firewall that I can configure is already there with out much searching.

Firestarter is just a frontend GUI designed to create rules for the real firewall framework (iptables + netfilter), which comes with the kernel. So it shouldn't be called a "Firewall", but a "Firewall Manager" or something like that.

You don't need Firestarter to use the firewall in Ubuntu, as long as you know the iptables commands or if use use another firewall manager. For instance, Ubuntu comes with a firewall manager installed by default, called UFW. The graphical interface for UFW, called GUFW does not come installed, but can be easily added from the repositories. It is newer, better maintained and simpler to use than Firestarter.

The only reason why people coming from Windows (myself included when I switched to Linux) like Firestarter is because it has connection monitoring features, which are just a waste of time and only helps to feed the paranoia.

Linux is not Windows and you probably don't even need a Firewall. If you are behind a router, you are already protected. Even if you don't have a router a Firewall is only needed on special circumstances, when you want to limit traffic on a certain port to some machines, while allowing others to connect. For example when opening a port with ssh server, but allowing only machines in your lan to connect to it.

Most of the time, a firewall won't be needed, because if you don't have any server (web server, ssh, BitTorrent...) running, then all ports are already closed and any unrequested connections from the outside (assuming they can pass through the router) will be refused. So using a Firewall to block those connections is just a waste of resources. If you have a server, you will need a firewall only if you need to be selective about which machines are allowed to connect. For example, if you are using a Bittorrent client you will need to allow anybody, so using a firewall in this situation is also useless.

---

### Post by Uncle Spellbinder on 2010-02-06
I'm not greedy. Only a few. If I had my way, I'd like to see these installed by default...


AWN
SeaMonkey (Current, Stable)
Virtualbox
Guayadeque Music Player
Exaile
Mediainfo
gThumb
AbiWord

---

### Post by lovinglinux on 2010-02-06
> **Uncle Spellbinder said:**
> I'm not greedy. Only a few. If I had my way, I'd like to see these installed by default...


AWN
SeaMonkey (Current, Stable)
Virtualbox
Guayadeque Music Player
Exaile
Mediainfo
gThumb
AbiWord

I really don't care what comes installed by default, because since Karmic alpha I'm installing a command-line only Ubuntu from alternate CD and then install just what I want, starting with kde-minimal :) I couldn't be happier.

---

### Post by Stan_1936 on 2010-02-06
Things I would Remove and/or Not want PRE-LOADED:
> **Warpnow said:**
> ..
Accessories
**[COLOR="blue"]-Note Software<-- a Word Processor would do the necessary job[/COLOR]**

Games
.**[COLOR="blue"]..the first thing I do, after a fresh install, is REMOVE THEM ALL....sorry, but I do NOT want any of these preloaded[/COLOR]**

Graphics
[B][COLOR="blue"]-ComicBook Viewer
-Basic MSPaint style Application<-- GIMP is sufficient[/COLOR][/B]

Internet
[B][COLOR="blue"]-Webkit Browser
-Torrent Client<---NO!
-Instant Messaging Client
-Text Based Game Client
-Standalone IRC Client
[/COLOR][/B]

Office
[B][COLOR="blue"]-Ebook Reader
-Mind Mapping
-Distraction Free Writing Program<--I would find this USELESS!!![/COLOR][/B]

Utilities
[B][COLOR="blue"]-Command Line System Monitor (aking to Htop)
-Wine<--- NO!!!  NOT NEEDED by DEFAULT![/COLOR][/B]

Things I would want PRE-LOADED:
**[COLOR="Red"]LyX[/COLOR]**

---

### Post by Warpnow on 2010-02-06
> **Stan_1936 said:**
> Things I would Remove and/or Not want PRE-LOADED:


Things I would want PRE-LOADED:
**[COLOR="Red"]LyX[/COLOR]**

I wasn't suggesting those applications. I made a list of all application types I could think of off the top of my head, so that there was a basis of referrence.

---

### Post by AllRadioisDead on 2010-02-06
Dear God I hope half that crap never makes it into the official release. This is why we have repositories.

---

### Post by Stan_1936 on 2010-02-06
> **Warpnow said:**
> I wasn't suggesting those applications. I made a list of all application types I could think of off the top of my head, so that there was a basis of referrence.

I know.  I decided to yuse your list anyway.

---

