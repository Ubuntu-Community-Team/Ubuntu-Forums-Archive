---
title: "Announcement: BaShare, an easy to use file transfer program"
date: 2009-05-01
forum: The Cafe
---

### Post by guiodic on 2009-05-01
[SIZE="4"]Hi guys![/SIZE]

[SIZE="4"]I'm proud to announce the first public version of **BaShare**.[/SIZE]

[IMG]http://guiodic.wordpress.com/files/2009/04/schermata.png[/IMG]

BaShare (Basic Share) is a very simply and user-friendly file sharing tool over the Internet and private LAN too.

**Basically BaShare is a http server with a graphical user interface (GUI).** Select a file, give the link to your friends and they will be able to download the file from you speedily (or not, as you wish :-) ) BaShare is very useful during chat sessions!

It support UPnP so you can "jump" your firewall.

It is written in GAMBAS an amazing Visual Basic-like language for GNU/Linux.

Features:

1.It works over the Internet and LAN

2.upnp support, so you can &#8220;jump&#8221; your firewall in the router

3.very easy to use

4.qt and gtk, no problem!

5.A nice tray icon to control the program

6.you can dynamically change bandwidth

7.Send large files to your friends quickly while chat with them over every IM! No more trouble with aMSN or Emesene slowness

8.Easy to install: Ubuntu, Debian, Fedora, OpenSuse, etc. packages

9.It is free/open source software under GNU GPL v3 license

10. English and Italian translation. 

INSTRUCTIONS:

Install Bashare package and miniupnpc package for your distribution from here: [http://code.google.com/p/bashare/downloads/list](http://code.google.com/p/bashare/downloads/list)

The tray icon:

[IMG]http://guiodic.files.wordpress.com/2009/02/schermata.png[/IMG]

Links:

Project home on Google code: [http://code.google.com/p/bashare/](http://code.google.com/p/bashare/)
Downloads: [http://code.google.com/p/bashare/downloads/list](http://code.google.com/p/bashare/downloads/list)
My blog (in Italian): [http://guiodic.wordpress.com/](http://guiodic.wordpress.com/)

---

### Post by Polygon on 2009-05-02
hmm, seems very interesting. I will have to try it out. but with whom....

---

### Post by MaxIBoy on 2009-05-02
There are quite a few contingencies for which this could come in handy.

Good work! I'll probably install this.

---

### Post by Orlsend on 2009-05-02
This is Awesome! Have you though making a account on Launchpad for the translation of this app? I think we a little more language support this could easily get in the repos!

---

### Post by FuturePilot on 2009-05-02
Wow, this is pretty cool. I can think of a number of instances where this could come in handy.

---

### Post by 3rdalbum on 2009-05-02
Very nice; I could have done with this program years ago on the Mac OS! Good work and good luck for the future of this very promising project.

---

### Post by billgoldberg on 2009-05-02
Thanks, will come in handy.

---

### Post by guiodic on 2009-05-02
> **Orlsend said:**
> This is Awesome! Have you though making a account on Launchpad for the translation of this app? I think we a little more language support this could easily get in the repos!

Oh, yes, surely I'll open a launchpad account soon.

Thank you.

---

### Post by Polygon on 2009-05-02
doesn't work for me =/

```
mark@Humboldti:~$ /usr/bin/BaShare.gambas
IP Adress: 68.84.199.230
Error: impossible to bind socket
upnpc : miniupnpc library test client. (c) 2006-2008 Thomas Bernard
Go to http://miniupnp.free.fr/ or http://miniupnp.tuxfamily.org/
for more information.
No IGD UPnP Device found on the network !
IP Adress: 68.84.199.230
Error: impossible to bind socket
mark@Humboldti:~$ 

```

---

### Post by days_of_ruin on 2009-05-02
I think you need to change the icon.I don't know what country
you are from but here in the US bs stands for bull****

---

### Post by Spiritous on 2009-05-02
> **days_of_ruin said:**
> I think you need to change the icon.I don't know what country
you are from but here in the US bs stands for bull****

Why does it matter :p

---

### Post by ubuntu27 on 2009-05-02
> **guiodic said:**
> Oh, yes, surely I'll open a launchpad account soon.

Thank you.

That will be nice.
That way we can all translate the software.


Will you be using [LaunchPad.net]("https://launchpad.net/") for [Bug Report and Management]("https://bugs.launchpad.net/") also?

---

### Post by guiodic on 2009-05-02
> **Polygon said:**
> doesn't work for me =/

```
mark@Humboldti:~$ /usr/bin/BaShare.gambas
IP Adress: 68.84.199.230
Error: impossible to bind socket
upnpc : miniupnpc library test client. (c) 2006-2008 Thomas Bernard
Go to http://miniupnp.free.fr/ or http://miniupnp.tuxfamily.org/
for more information.
No IGD UPnP Device found on the network !
IP Adress: 68.84.199.230
Error: impossible to bind socket
mark@Humboldti:~$ 

```

What kind of connection?
Router? Adsl Modem? other? Are you on-line?

---

### Post by guiodic on 2009-05-02
> **ubuntu27 said:**
> 
Will you be using [LaunchPad.net]("https://launchpad.net/") for [Bug Report and Management]("https://bugs.launchpad.net/") also?

I'm not sure. It seems that launchpad discourages non-ubuntu users.

On the other hand, ubuntu users are discouraged by other bug trackers... and I am an Ubuntu user! :)

I'm reflecting on. :-k

---

### Post by ubuntu27 on 2009-05-03
> **guiodic said:**
> I'm not sure. It seems that launchpad discourages non-ubuntu users.

On the other hand, ubuntu users are discouraged by other bug trackers... and I am an Ubuntu user! :)

I'm reflecting on. :-k

How about [SourceForge.net]("http://sourceforge.net/")?

---

### Post by Polygon on 2009-05-03
> **guiodic said:**
> What kind of connection?
Router? Adsl Modem? other? Are you on-line?

I am using cable, but i am connected via wireless to a wireless router, which in turn connects to our modem. To be honest, i dont think upnp works very well for ANY program on linux, as deluge torrent claims to have it, but i get very slow upload speeds there as well.

---

### Post by guiodic on 2009-05-03
> **ubuntu27 said:**
> How about [SourceForge.net]("http://sourceforge.net/")?

I prefer Google Code.

---

### Post by guiodic on 2009-05-03
> **Polygon said:**
> I am using cable, but i am connected via wireless to a wireless router, which in turn connects to our modem. To be honest, i dont think upnp works very well for ANY program on linux, as deluge torrent claims to have it, but i get very slow upload speeds there as well.

Well, you are in right. BaShare uses the Transmission's library for upnp.

But the biggest problem is the bind error.

---

### Post by guiodic on 2009-06-01
I released a new version of BaShare: 0.4.2.

You can dowsload it at: [http://code.google.com/p/bashare/](http://code.google.com/p/bashare/)

This is the changelog:

* Mon Jun 01 2009 Guido Iodice <guido.iodice@gmail.com> 0.4.2
- a nicer icon, thanks to sentinella86

* Thu May 21 2009 Guido Iodice <guido.iodice@gmail.com> 0.4.1 - internal release
- some correction to avoid problems on non-http request
- statusbar for log messages
- if miniupnp is not installed, suggests to install it in Settings Form
- detect if there is a new version
- buttons for visit BaShare website and bug tracker in about form
- band limit is 2MB/s now
- corrected a typo
- Initial Spanish and BR Port. translation

----------------------------------

---

### Post by guiodic on 2009-11-21
BaShare 0.5.0 brings new improvements:

- BaShare can receive files too :D
- English is now the default language, but there are more translations
- launchpad integration
- various bugfixes
- note: the author thanks Emilien Klein. Most improvement was not possible without his help.

You can get BaShare from getdeb:

[http://www.getdeb.net/updates/bashare](http://www.getdeb.net/updates/bashare)

or from it's ppa repo:

[https://launchpad.net/~bashareteam/+archive/bashare](https://launchpad.net/~bashareteam/+archive/bashare)

---

### Post by ubuntu27 on 2009-11-22
THank you for the update guiodic :)

---

### Post by earthpigg on 2009-11-22
ooo i like the look of this.

considered an OS X and Windows port?

---

### Post by guiodic on 2009-11-23
> **earthpigg said:**
> ooo i like the look of this.

considered an OS X and Windows port?

No, because Gambas is not supported on Windows.
On Windows you can use hsf.

[http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/)

---

### Post by kpholmes on 2009-11-23
is it like rapid share where the file is hosted on your server? or is it like a p2p kinda share?

---

### Post by guiodic on 2009-11-23
> **kpholmes said:**
> is it like rapid share where the file is hosted on your server? or is it like a p2p kinda share?

basically it is a web server. Other users can download files from you with a web browser.

---

### Post by Enigmapond on 2009-12-06
Just had to say I just started using this programme and it is so very useful! Thank you for releasing this...it's brilliant!! Worked right away...I just forwarded the port on my wireless router and made the proper rules in ufw...didn't know whether had to but...it works so very well and can literally SHOOT files across the globe!

Cheers!!:guitar:

---

### Post by 3rdalbum on 2009-12-06
I used to run a web server on my old Mac so people could download files from me... but are you worried about Opera Unite taking away your marketshare? :-)

---

### Post by Enigmapond on 2009-12-06
I have a question regarding receiving files. How is this possible? How can someone without this application, on a Windoze OS, transfer a file to Bashare on my end? I have looked for some documentation for this but have found none. If there IS a way, can you explain how?

Thank you in advance...

Cheers!

---

### Post by aktiwers on 2009-12-06
Looks great!
Just installed it. My link does not seam to work though?

Edit: oh I properly need to open ports..

---

### Post by Enigmapond on 2009-12-09
Oh...please disregard my last request...I see how it works now! It would however, be a good thing to have it state, when receiving, the speep and progress as it does when sending...but it wokrs well..:)

Thank you!

---

### Post by Hrodebert on 2010-01-06
Small bump just because I wanted to say thanks for this great program.
It made my life a lot easier and it works perfectly. Keep up the excellent work.

---

### Post by Enigmapond on 2010-01-27
Hi.

I posted this in General Help but seems I'm not getting any response and hope I will in this thread. I've been using this Bashare for awhile now and I really like it however, I'm not able to receive files. The sending goes very well but everytime I try to receive files by sending my link to another person, it starts then suddenly quits. I have both ports 65000 and 65001 forwarded and have made rules in ufw to accomodate however this is still happening. Any suggestions?

Thank You!

---

### Post by Enigmapond on 2010-01-27
Bump for help......

---

