---
title: "Looking for an outlook replacement"
date: 2007-10-25
forum: Windows
---

### Post by aquavitae on 2007-10-25
I've had a look but I haven't found exactly what I'm looking for - a replacement for outlook that's fully compatible with outlook.  The problem is we use outlook at work and I'm trying to persuade the company to move away from microsoft.  My idea is if I can start replacing the software I use with FOSS software, I'll be able to persuade them that all is not Windows.  So I need something to replace outlook, but that will be able to handle things like emailed meeting requests sent from outlook. Obviously I'm looking for something that will run on windows and linux.

Any suggestions?

---

### Post by inversekinetix on 2007-10-25
maybe this

[http://www.mozilla.com/en-US/thunderbird/all.html](http://www.mozilla.com/en-US/thunderbird/all.html)

---

### Post by igknighted on 2007-10-25
What do you use Outlook for?  Do you have an exchange server?  Do you just use it as an email client, or do you also use it for the PIM and Calendaring functions?

Unfortunately, there isn't a lot that can do exchange/PIM.  There is a beta of Evolution for windows, but it really isn't good.  There should be a Kontact port soon, but it's a KDE4 project and not done yet (could be up to a year or more away).  Thunderbird does not connect to exchange (mapi), although with sunbird it does have nice PIM functions and there are alternatives (ical?).

Honestly, the best non-microsoft solutions going are either a Zimbra or Scalix server or a Domino/Lotus setup.  Don't know if I would trust Zimbra or Scalix in a large corporate setting (I've tried, its touchy), but if you buy the support (or the Xandros server) it might be worth it.  Lotus Notes is an awesome program, and IBM is pretty OSS friendly even if Domino/Notes are not OSS, so that would be worth a shot too.

---

### Post by angryfirelord on 2007-10-25
If it's pop or imap, T-Bird can get to it. If it's an Exchange server, then you're stuck with Outlook. :(

---

### Post by aquavitae on 2007-10-26
Thanks for the replies.

Its exchange I'm afraid... and I do use the calender.  I guess I'm stuck with outlook then.  And trying to get them to change the server will be impossible I think - emails don't come through half the time anyway!

---

### Post by nutter78 on 2007-11-20
there are some exchange connectors that are free - can't remember them now - but do a google for free exchange connectors, & this should give u a good starting point!

---

### Post by ephro on 2007-11-20
What you are looking for is Evolution, which is available in Ubuntu. It allows you to connect to the exchange server, lookup names in the company address book, use the calendar features (including free/busy), and almost every other Exchange feature.

Use your package manager to install the Evolution email client and the extra exchange plugins.



Ephro

---

### Post by igknighted on 2007-11-20
> **ephro said:**
> What you are looking for is Evolution, which is available in Ubuntu. It allows you to connect to the exchange server, lookup names in the company address book, use the calendar features (including free/busy), and almost every other Exchange feature.

Use your package manager to install the Evolution email client and the extra exchange plugins.



Ephro

Did you read the original post?  He is looking for open-source software for WINDOWS.  There is a development version of Evolution for windows, but I have used it, and it isn't very good.  I think Kontact is his best bet, but I haven't the foggiest idea when the KDE project will have their windows ports available, as the linux versions aren't even done yet.

---

### Post by theundecided on 2008-11-20
I don't know if you have found it yet...but this may help... I have yet to try it...but I am looking for the same thing...and this is what I came up with...it looks like it will work on all platforms

[http://www.spicebird.com/](http://www.spicebird.com/)

---

### Post by Captonkirk on 2008-11-25
This may help

[http://ubuntuforums.org/showthread.php?t=956654](http://ubuntuforums.org/showthread.php?t=956654)

---

### Post by HermanAB on 2008-11-25
Your options are better if you also get rid of Exchange.  Exchange has a horrible database.  You can literally replace dozens of Exchange servers with a single Zimbra or Citadel server.

[http://www.bynari.net/](http://www.bynari.net/)
[http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

Using the Bynari connector, you can use Outlook with Citadel, but I prefer the Thunderbird & Songbird combo since those are cross platform and don't need a connector.

Cheers,

Herman

---

