---
title: "Making a home media server from &quot;Ubuntu Server edition&quot;?"
date: 2009-09-03
forum: Server Platforms
---

### Post by NinjaNumberNine on 2009-09-03
Hi, everyone. Is it possible to use ubuntu server as a LAN media server to all my windows computers?  More specifically, could I use it as a semi-normal desktop with the xfce display manager (I already know how to install it in ubuntu server) and have a few small programs as well as watch my TV card AND ALL on 2gb of RAM? Basically I want the following:
#1: It needs to be a usable computer in itself.
#2: It must share my 250gb external usb HDD with read-write access to everyone on the network.
#3: It needs to be fast.
#4: It needs to have a few simple applications, like Firefox for browsing the web, Evolution for email, and a few others (text editors, image viewers etc)
#5: If at all possible, it needs to have a good quality tv viewing AND capturing application. (preferably not xawtv or those ugly ones :D)

Anyway I hope someone can help!


 Thanks, 
 

  NinjaNumberNine

---

### Post by NinjaNumberNine on 2009-09-03
[*cry* nobody ever answers this kind of posts!]("http://ubuntuforums.org/showthread.php?p=7876661#post7876661") :(

---

### Post by snowman4839 on 2009-09-03
First, don't cry in forums... makes ya seem desperate :D but i'm gonna try to help you anyway.

Going line by line of what you said...

Solving 1 = To make it a usable computer install x window system and gnome or xfce. (usable is very vague... do you mean usable to a smart person or to the average computer illiterate?)

Solving 2 = Samba would make file sharing with windows computer easy. It allows the use of SMB/CIFS on Linux which is the file sharing method of Windows. Google around for tutorials

Solving 3 = Fast... AT LEAST 2.0Ghz+ processor with 1GB of RAM but that is so cheap I would go with a dual core 3.0Ghz and 2GB and that would be plenty. (fast is vague too)

Solving 4 = Apparently you already have most of the applications in mind

Solving 5 = Not really sure... Good capture card maybe? I really don't know. I've never had to do that.


TBH, this would be a lot easier by using Ubuntu Desktop edition... Most of the things you are asking for are more geared towards the desktop edition. Ubuntu Server is not really meant for graphical interfaces and flipdidis and flopdidos... just server... I mean desktop already has all of the applications you would need, a GUI (graphical user interface (Gnome)), its "fast" :P ,and easy use of Samba which is 4/5 thing you asked for already there...

Hope that helps :D
Stay Frosty...

---

### Post by NinjaNumberNine on 2009-09-03
> First, don't cry in forums... makes ya seem desperate :grin:But i am desperate! :biggrin:

---

### Post by NinjaNumberNine on 2009-09-03
>  Do you mean usable to a smart person or to the average computer illiterate?
-Definately the average computer idiot.
> Samba would make file sharing with windows computer easy.
From experience with Kubuntu, I'd have to say Samba was a nightmare. But before you reply, let me tell you where I am now: 
I installed the latest Ubuntu Server 32bt version as the only OS on the internal hard drive (40gb).
Then, I installed gnome, the x-server and ubuntu-desktop on my computer and rebooted. (It worked, and I am in typing this from Ubuntu > Firefox.) Next, I ```
sudo apt-get install samba
```
and then went in Add/Remove Programs to installed the program "Samba" (A simple configuration program, not the actual samba system).
That ran fine, I loaded it when it finished installing, set my computer to the right workgroup, loaded Places>Network>Windows Network>MSHOME and my computer was listed. A little more config and I now have a read-write share being hosted on the network!


Which means:

#1: It needs to be a usable computer in itself.
<SOLVED>
#2: It must share my 250gb external usb HDD with read-write access to everyone on the network.
<SOLVED>
#3: It needs to be fast.
<NOTHING TO DISPROVE THIS AS OF YET>
#4: It needs to have a few simple applications, like Firefox for browsing the web, Evolution for email, and a few others (text editors, image viewers etc)
<UBUNTU'S GOT EM ALL>
#5: If at all possible, it needs to have a good quality tv viewing AND capturing application. (preferably not xawtv or those ugly ones :grin:)
<OH YEAH, TVTIME, MYTHTV>
#6  I have to love ubuntuforums in the end of it all.
<TOTALLY ABSOLUTELY NUTS OVER IT>


I.E. My problems have been vanquished as of yet. I will post any problems or progress here.
Once again, thanks, mr snowman! ;-)

---

### Post by snowman4839 on 2009-09-03
> **NinjaNumberNine said:**
> -Definately the average computer idiot.

From experience with Kubuntu, I'd have to say Samba was a nightmare. But before you reply, let me tell you where I am now: 
I installed the latest Ubuntu Server 32bt version as the only OS on the internal hard drive (40gb).
Then, I installed gnome, the x-server and ubuntu-desktop on my computer and rebooted. (It worked, and I am in typing this from Ubuntu > Firefox.) Next, I ```
sudo apt-get install samba
```and then went in Add/Remove Programs to installed the program "Samba" (A simple configuration program, not the actual samba system).
That ran fine, I loaded it when it finished installing, set my computer to the right workgroup, loaded Places>Network>Windows Network>MSHOME and my computer was listed. A little more config and I now have a read-write share being hosted on the network!


Which means:

#1: It needs to be a usable computer in itself.
<SOLVED>
#2: It must share my 250gb external usb HDD with read-write access to everyone on the network.
<SOLVED>
#3: It needs to be fast.
<NOTHING TO DISPROVE THIS AS OF YET>
#4: It needs to have a few simple applications, like Firefox for browsing the web, Evolution for email, and a few others (text editors, image viewers etc)
<UBUNTU'S GOT EM ALL>
#5: If at all possible, it needs to have a good quality tv viewing AND capturing application. (preferably not xawtv or those ugly ones :grin:)
<OH YEAH, TVTIME, MYTHTV>
#6  I have to love ubuntuforums in the end of it all.
<TOTALLY ABSOLUTELY NUTS OVER IT>


I.E. My problems have been vanquished as of yet. I will post any problems or progress here.
Once again, thanks, mr snowman! ;-)

np ninja. We all start somewhere right? You should've seen me when I first started in Linux :P.

---

### Post by NinjaNumberNine on 2009-09-04
Upgrade: I installed the normal Ubuntu Desktop Edition because the server had several system folders missing and the home folder was somewhat scrambled. However, I set everything up and this will do just as well! (And probably better) :D

---

### Post by distortedecho on 2009-09-04
I have a question please, as I am too considering making a media centre for TV capturing.

When you record TV, will you be able to burn, convert, transfer those recordings to "anything"? I've always been curious how TV shows appear on YouTube or Torrent sites in good quality (and not recorded from a camera phone).

If I knew this answer - my next weekend project would be in planning phase. Not that I want to upload TV to YouTube, but that I want to be able to put it onto other devices.

---

### Post by NinjaNumberNine on 2009-09-04
First thing you'd need is a good media center and supported card. If you have a card, which one is it? If not, consider getting something like this: (please don't everybody buy all these, I haven't got one yet and I don't want 'em going out of stock!)
[WinTV-PVR-500]("http://www.getpartsonline.com/wintv-pvr-500.html?source=googlebase&code=wintv-pvr-500")
[WinTV-PVR-150 MCE]("http://www.compuvest.com/Search.jsp?Search=26552&advsite=froogle&dtm=20090901&sku=332000584-31")
That's the best prices out there- (I wouldn't trust eBay even if they have it cheaper. :D )

Anyway, once you have a card and installed it, (how to install depends entirely on your card) I would suggest you install MythTV. It's in all the Package Managers i.e. adept, Add-Remove, and so on .  Then, after configuring Myth for you card, if it works then MythTV is great at recording shows. After that, get a good convertor software, (I recommend WinFF for linux and Format Factory for windows) and convert 'em to whatever format you need, they might already be in the right format.

 Have fun!

P.S. Don't let the MCE (windows media center edition) fool you- Hauppage does mention on their site that their cards work on linux.

---

### Post by DJJo on 2009-09-04
I got home (media) server my self.

I juse webmin to control it. it is easy and you do not need a screen(keybord) for the server and a  [graphical user interface]("http://en.wikipedia.org/wiki/Graphical_user_interface") so it is faster. jou just run it in a webbrowser from a nother pc.

i started with a 500gb of storage. but lader on it was not enough. 

so i just LVM to combine the partitions to together. with XFS file system.
nou al i need to do is run a couple commands and i got a lager partition.

and i do not record tv but i download it. with SABnzbd. jou also run it from a webbrowser

---

### Post by Udayakiran on 2009-09-16
Why doesn't anyone consider mythbuntu? It satisfies the OPs requirements.

---

### Post by NinjaNumberNine on 2009-09-16
I know. I do like Mythbuntu, I have resorted to it several times, but I don't like their default desktop environment, XFCE. Too ugly... I figure it's easier to install MythTV from Kubuntu than KDE from Mythbuntu lol... Also I seem to remember that XFCE does not have network support, you can't even browse in in thunar.

---

### Post by ChumleyEX on 2009-09-16
Check out something called Ushare.. This allows your xbox, ps3 and newer versions of Windows Media player to stream movies/music from your linux box. 


Also I think there is a media version of ubuntu out there somewhere.

---

### Post by roundhay on 2009-09-16
You can install the gnome desktop in mythbuntu, just down load it using synaptic

---

### Post by NinjaNumberNine on 2009-09-16
I know. :)

---

### Post by Udayakiran on 2009-09-16
> **NinjaNumberNine said:**
> I know. I do like Mythbuntu, I have resorted to it several times, but I don't like their default desktop environment, XFCE. Too ugly... I figure it's easier to install MythTV from Kubuntu than KDE from Mythbuntu lol... Also I seem to remember that XFCE does not have network support, you can't even browse in in thunar.
I've used thunar only for opening files on the same machine. I'm not sure the OP needs to browse shares on other computers, so i dont think its a deal breaker.

XFCE IS ugly, but it is also light. KDE can knock the breath out of most low end systems. I consider it the aero of linux.

And yea, most gurus recommend installing the desktop version of ubuntu first and then installing mythTV later. I've never tried it that way. What i like about mythbuntu is that u need almost zero effort to install and configure it. Just point and click and u have it running.

---

### Post by Udayakiran on 2009-09-16
> **ChumleyEX said:**
> Check out something called Ushare.. This allows your xbox, ps3 and newer versions of Windows Media player to stream movies/music from your linux box. 


Also I think there is a media version of ubuntu out there somewhere.

Yea, it is called mythbuntu ([http://www.mythbuntu.org/](http://www.mythbuntu.org/)) It is despised by ubuntu gurus as much as linux die-hards hate sudo. :P

---

### Post by NinjaNumberNine on 2009-09-17
> **Udayakiran said:**
> KDE can knock the breath out of most low end systems. I consider it the aero of linux.
I know.. I was awed when I first changed over from gnome! I really think that the future of linux operating systems lies in KDE. People go after style for the most part, and KDE has Gnome and CERTAINLY XFCE beat black and blue,(or should I say orange and black) over looks. I like your wording, "the aero of linux" 
-I may put that in my sig sometime.. :)

---

