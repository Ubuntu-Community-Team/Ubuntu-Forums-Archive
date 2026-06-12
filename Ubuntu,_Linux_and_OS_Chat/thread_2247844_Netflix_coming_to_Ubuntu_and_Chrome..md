---
title: "Netflix coming to Ubuntu and Chrome."
date: 2014-10-10
forum: Ubuntu, Linux and OS Chat
---

### Post by Michael_McKenney on 2014-10-10
[http://www.pcworld.com/article/2824623/ubuntu-linux-gets-netflix-without-weird-workarounds.html](http://www.pcworld.com/article/2824623/ubuntu-linux-gets-netflix-without-weird-workarounds.html)

---

### Post by Vladlenin5000 on 2014-10-10
[http://www.omgubuntu.co.uk/2014/10/psa-netflix-ubuntu-now-working-box](http://www.omgubuntu.co.uk/2014/10/psa-netflix-ubuntu-now-working-box)

A very interesting ongoing discussion in the comments section.

---

### Post by myacct on 2014-10-10
Does anyone have this up and running successfully?  It didn't work for me.  When attempting to start playing a video I'm prompted to download and install Silverlight.

Netflix preferences:
1) Playback settings: Prefer HTML5 instead of Silverlight

System info:
1) ubuntu 14.04 - packages up to date
2) nss3 version:  2:3.17.1-0ubuntu0.14.04.1 
3) google-chrome-stable : 38.0.2125.101-1 
5) User agent settings:

[TABLE="class: ua_list_sub_table, width: 800"]
[TR]
[TD]Netflix Linux
[/TD]
[TD]Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko)
[/TD]
[TD]Replace  IE9
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by sammiev on 2014-10-10
> **myacct said:**
> Does anyone have this up and running successfully?  It didn't work for me.  When attempting to start playing a video I'm prompted to download and install Silverlight.

Netflix preferences:
1) Playback settings: Prefer HTML5 instead of Silverlight

System info:
1) ubuntu 14.04 - packages up to date
2) nss3 version:  2:3.17.1-0ubuntu0.14.04.1 
3) google-chrome-stable : 38.0.2125.101-1 
5) User agent settings:

[TABLE="class: ua_list_sub_table, width: 800"]
[TR]
[TD]Netflix Linux
[/TD]
[TD]Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko)
[/TD]
[TD]Replace  IE9
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

Been using it for months now. Working great here.

[This]("http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins") is the setup I used.

---

### Post by Vladlenin5000 on 2014-10-10
Sorry, can't help you with that. I don't use the service and probably never will.

---

### Post by Rob Sayer on 2014-10-12
> **myacct said:**
> Does anyone have this up and running successfully?  It didn't work for me.  When attempting to start playing a video I'm prompted to download and install Silverlight.

Netflix preferences:
1) Playback settings: Prefer HTML5 instead of Silverlight

System info:
1) ubuntu 14.04 - packages up to date
2) nss3 version:  2:3.17.1-0ubuntu0.14.04.1 
3) google-chrome-stable : 38.0.2125.101-1 
5) User agent settings:

[TABLE="class: ua_list_sub_table, width: 800"]
[TR]
[TD]Netflix Linux[/TD]
[TD]Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko)[/TD]
[TD]Replace  IE9[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]


You seem to be trying to do this in Firefox ... as the title of this thread indicates, Chrome (not chromium) is implementing netflix support, not mozilla.  I used Firefox for years but now just use Chrome.  IMHO Mozilla has turned Firefox into a real turd in the last few versions.  Too bad.

---

### Post by SeijiSensei on 2014-10-12
I just use [Pipelight](http://pipelight.net/cms/install/installation-ubuntu.html).  You do need to add a [plugin]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") to Firefox that spoofs your User-Agent string to look like you're running on Windows.

---

### Post by mikodo on 2014-10-14
> **SeijiSensei said:**
> I just use [Pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html").  You do need to add a [plugin]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") to Firefox that spoofs your User-Agent string to look like you're running on Windows.

Older thread now, but ...

I wonder, (for in the future, when I am retired), could I use this for ["Rogers Game Centre Live"]("https://gamecentrelive.rogers.com/")? (Streaming live on internet). Or, another solution, native to linux, rather than using Windows natively? (I haven't read about it too much yet, [brand new agreement with the NHL, for 11 years], but I think it is for now, only for "Windows". Again, I am not sure).

I would want this on a desktop machine, connected to LCD TV ...

           [* "*]("https://gamecentrelive.rogers.com/getting-started")[[URL="https://gamecentrelive.rogers.com/getting-started"]*All fans can get Rogers NHL GameCentre Live&#8482; regardless of what wireless or cable provider they are currently with."*]("https://gamecentrelive.rogers.com/getting-started")
[/URL]

---

### Post by geronl on 2014-10-15
I also just discovered Pipelight and it works! I use Ubuntu 12.4 LTS
I am able to watch my cable on my laptop through the internet now.

---

### Post by sammiev on 2014-10-15
Did 3 fresh installs over the last 24 hrs. No problems with netflix at all using [this]("http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins") method.

---

### Post by SeijiSensei on 2014-10-15
> **mikodo said:**
> I wonder, (for in the future, when I am retired), could I use this for ["Rogers Game Centre Live"]("https://gamecentrelive.rogers.com/")?

The website provides no useful informationi on the technologies involved other than to say "select" PCs and Macs.  Who knows what differentiates the "select" from the ordinary "rabble."  If they use Silverlight DRM, then you can probably use Pipelight.  If they use some other technology, I have no idea.  You could call Rogers and ask, I suppose, though most tech support people at cable operators hear Linux and throw up their hands.

I didn't see an option for any sort of trial period either, which is pretty annoying.

---

### Post by oldrocker99 on 2014-10-15
On an Acer C7 running Chrubuntu 12.04, Netflix via Chrome worked perefectly for me just today. I watched "The Day of The Doctor" with nary a hiccup, except when I delberately exited and tried again to see if it picked up where it left off, which it did. If it'll run on a netbook, it should run just fine for anyone with anything more robust than my little slab.

I will say that I do not use Chrome as a regular browser for the memory hogging (open 10 tabs in Firefox and check memory usage, then close Firefox and do the same thing with Chrome and look at the memory usage0, but not needing to use a kludge to use Netflix is **HUGE.**

---

### Post by jawilljr2 on 2014-10-15
> **sammiev said:**
> Did 3 fresh installs over the last 24 hrs. No problems with netflix at all using [this]("http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins") method.

That is the old way, [here is the new way.]("http://www.omgubuntu.co.uk/2014/10/psa-netflix-ubuntu-now-working-box"):

> **Netflix now works on Ubuntu out of the box — no hacks, plugins or [user-agent switching]("http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins") workaround required.**All you need is the Latest Chrome stable, Tell Netflix to use HTML5 vs. Silverlight, and an updated Ubuntu system. An updated Ubuntu will get you libnss3 ver 3.17. The link you gave only has libnss3 ver 3.16. Also no UA hacks is required. In fact I uninstalled my UA Switcher.

Below is my default UA for Chrome:

```
Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.104 Safari/537.36
```

Says I am using Linux, not Windows...works for Netflix.

---

### Post by mikodo on 2014-10-16
> **SeijiSensei said:**
> The website provides no useful informationi on the technologies involved other than to say "select" PCs and Macs.  Who knows what differentiates the "select" from the ordinary "rabble."  If they use Silverlight DRM, then you can probably use Pipelight.  If they use some other technology, I have no idea.  You could call Rogers and ask, I suppose, though most tech support people at cable operators hear Linux and throw up their hands.

I didn't see an option for any sort of trial period either, which is pretty annoying.

SeijiSensei. Thank you, for your efforts of investigating what information there is, in an attempt to answer my question.  I appreciate your response/insights. Your statement about  Silverlight DRM, gives me hope. I will look into this later.

Please, have a pleasant day.

---

### Post by Kale_Freemon on 2014-10-16
Meh. I'm quite content using Pipelight in both my Ubuntu 14.04 installs. Chrome has become way too bloated of a browser for me. I wound up switching back to Firefox full time after a few years of watching Chrome turn into a clunky and slow browser (it slows down everything on both my computers).

But, it is nice to see that Netflix is becoming more friendly to Linux users.

---

### Post by sammiev on 2014-10-16
> **jawilljr2 said:**
> That is the old way, [here is the new way.]("http://www.omgubuntu.co.uk/2014/10/psa-netflix-ubuntu-now-working-box"):

All you need is the Latest Chrome stable, Tell Netflix to use HTML5 vs. Silverlight, and an updated Ubuntu system. An updated Ubuntu will get you libnss3 ver 3.17. The link you gave only has libnss3 ver 3.16. Also no UA hacks is required. In fact I uninstalled my UA Switcher.

Below is my default UA for Chrome:

```
Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.104 Safari/537.36
```

Says I am using Linux, not Windows...works for Netflix.

I will try it later today without UA.
Thanks

---

### Post by trivialpackets on 2014-10-16
It is working for me and has been for a little while now without the UA hack.  I'm very happy for this progress.

---

