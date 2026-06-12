---
title: "VLC 2.0.3 (ubuntu latest version) has serious security vulnerability"
date: 2012-12-01
forum: Security
---

### Post by LABcqX on 2012-12-01
According to VLC site, they are urging everyone to update to 2.0.4.
[http://www.videolan.org/news.html](http://www.videolan.org/news.html) (security advisory 1203)

Will the ubuntu update soon? I'm uneasy using it with a serious security vulnerability. I'm surprised the ubuntu hasn't already updated itself.

---

### Post by MadmanRB on 2012-12-01
Well if you are using Ubuntu 12.04 I guess you can use the version for 12.10 if you are that worried (also it may come anyway if the security risk is that high)
You could just use this repo for VLC updates:

deb [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) quantal main

---

### Post by haqking on 2012-12-01
> **LABcqX said:**
> According to VLC site, they are urging everyone to update to 2.0.4.
[http://www.videolan.org/news.html](http://www.videolan.org/news.html) (security advisory 1203)

Will the ubuntu update soon? I'm uneasy using it with a serious security vulnerability. I'm surprised the ubuntu hasn't already updated itself.

install 2.0.4 then.

---

### Post by LABcqX on 2012-12-01
> **haqking said:**
> install 2.0.4 then.

synaptic says 2.0.3 is hte latest version. there is no 2.0.4 install option.

---

### Post by haqking on 2012-12-01
> **LABcqX said:**
> synaptic says 2.0.3 is hte latest version. there is no 2.0.4 install option.

```
sudo add-apt-repository ppa:videolan/stable-daily
sudo apt-get update
sudo apt-get install vlc
``` 

I am running 2.0.5

---

### Post by LABcqX on 2012-12-01
This seems to indicate I'd be receiving DAILY updates. Why would I want that? I just want to get the security updates that 2.0.4 bring. Why doesn't the ubuntu repository that gives VLC just update to 2.0.4 and solve the problem?

---

### Post by haqking on 2012-12-01
> **LABcqX said:**
> This seems to indicate I'd be receiving DAILY updates. Why would I want that? I just want to get the security updates that 2.0.4 bring. Why doesn't the ubuntu repository that gives VLC just update to 2.0.4 and solve the problem?


The updates will also bring vulnerabilities that will be updated in 2.0.5 which will bring vulnerabilities that will need updating to 2.0.6 ad anuseum ad infinitum

Dont do that then and download source for 2.0.4

As for why, VLC is one of thousands of applications in the repos that are not built by Canonical, they are third party tools, if you want the latest install it yourself.

You seem overly worried about this particular vulnerability like there it is the only one on your machine...LOL I am pretty confident you have many more in different services and applications.

---

### Post by 0011235813 on 2012-12-01
> **LABcqX said:**
> This seems to indicate I'd be receiving DAILY updates. Why would I want that? I just want to get the security updates that 2.0.4 bring. Why doesn't the ubuntu repository that gives VLC just update to 2.0.4 and solve the problem?
That's because Ubuntu isn't a rolling release distro, so they couldn't update their repositories for the newest VLC version. The best solution is to use the PPA as suggested... Or else another video player!
EDIT: VideLAN doesn't state what platforms this affects, so it's quite possible Ubuntu and other Linux-based OS' will remain unaffected. Anyway, it's a vulnerability, not an exploit &#8211; there are currently no known sites that distribute infected files for VLC, and now that it's fixed, there likely won't be any developed. You're being paranoid.

---

### Post by haqking on 2012-12-01
> **0011235813 said:**
> That's because Ubuntu isn't a rolling release distro, so they couldn't update their repositories for the newest VLC version. The best solution is to use the PPA as suggested... Or else another video player!
EDIT: VideLAN doesn't state what platforms this affects, so it's quite possible Ubuntu and other Linux-based OS' will remain unaffected. Anyway, it's a vulnerability, not an exploit – there are currently no known sites that distribute infected files for VLC, and now that it's fixed, there likely won't be any developed. You're being paranoid.

+1 there are vulnerabilities in most things, it doesnt mean it can be exploited.  Also you seem overly worried like this is the only vulnerability on your machine, i can bet you have many others.

If you want a certain version then install it, change to a rolling release distro or as said use a different player if you are uncomfartable with VLC.

---

### Post by Hungry Man on 2012-12-01
VLC, like many programs, takes in input. Just as PDF readers can take in malformed PDFs and be exploited, so can a media player.

I would highly suggest setting up AppArmor for situations like this - I think I have one if anyone would like it, but it's one of my 'messing around' profiles, so it's not perfect.

You're unlikely to run into:
1) this exploit in the wild
2) a payload that runs on Linux

but if you'd like to be safe it's not hard.

---

### Post by Cheesemill on 2012-12-01
If you read the security advisory properly then you can see how small of an issue this is.

An attacker would have to trick you into opening a specially crafted PNG image with VLC. Even if this happens they will only succeed in crashing VLC, they can't do anything else or gain access to your system.

As others have said these sort of vunerabilities are common, there is no point worrying yourself about them.

---

### Post by thnewguy on 2012-12-01
Indeed, it seems highly unlikely this bug will actually affect end users. Which raises the question why the VLC developers posted the strongly worded warning on their blog. This looks like a niche annoyance which may cause a crash, not an exploit. I wouldn't be in a rush to upgrade.

---

### Post by Stonecold1995 on 2012-12-01
From [http://www.videolan.org/security/sa1203.html](http://www.videolan.org/security/sa1203.html):

> Because the overflow occurs while reading a buffer, rather than writing, it is believed that this issue cannot lead to arbitrary code execution.

---

### Post by DukeOfMixture on 2012-12-01
> **haqking said:**
> I am running 2.0.5

I thought I had him beat. I'm running 2.0.4 and I'm using Xubuntu, but I'm not sure that should make a difference.

---

### Post by LABcqX on 2012-12-02
Thanks guys. I'm new to ubuntu and don't know these things about it.

But a bug that causes a program to crash is bad news because a remote code execution is very possible from this response of the program. That is why VLC worded it so strongly.

App Armor sounds good. I wish the ubuntu developers would release a profile for it because it is too hard for me to configure right. I wish VLC was something the developers put some attention to because it works so much better than the Totem player.

---

### Post by 0011235813 on 2012-12-02
> **Hungry Man said:**
> VLC, like many programs, takes in input. Just as PDF readers can take in malformed PDFs and be exploited, so can a media player.

I would highly suggest setting up AppArmor for situations like this - I think I have one if anyone would like it, but it's one of my 'messing around' profiles, so it's not perfect.

You're unlikely to run into:
1) this exploit in the wild
2) a payload that runs on Linux

but if you'd like to be safe it's not hard.
Just a note; comparing this to malicious PDF files isn't a valid comparison – PDFs contain executable JavaScript code in them, whereas media files (excluding the ones made by Microsoft) do not. It is considerably harder to infect something with a bunch of media files than it is with a PDF (why is the Adobe PDF plugin the most exploited on the Internet after all?).

---

### Post by andrew.46 on 2012-12-04
> **haqking said:**
> I am running 2.0.5

Running 2.1.0 here:

```

andrew@corinth:~$ vlc --version | head -n 1
VLC media player 2.1.0-git Rincewind (revision 8fec577)
VLC version 2.1.0-git Rincewind (8fec577

```

:)

---

### Post by Hungry Man on 2012-12-04
> Just a note; comparing this to malicious PDF files isn't a valid comparison &#8211; PDFs contain executable JavaScript code in them, whereas media files (excluding the ones made by Microsoft) do not. It is considerably harder to infect something with a bunch of media files than it is with a PDF (why is the Adobe PDF plugin the most exploited on the Internet after all?).
It's not really much harder. PDF is a poor example because the format is fairly dangerous in itself, but Javascript doesn't play into it. It's all about providing information to a program that the program can't handle. Big complex data types like PDF, DOC, or MOV are all going to let attackers fill them with tons of data - great for exploiting the complex backend systems.

Why is Adobe Reader so exploited? Well, it isn't very much anymore to the same extent, but that's due to its popularity. It's installed on tons of machines and, as I said, there are a few inherently dangerous areas of PDFs.

But I'd say infecting VLC is just as easy as Word, and there have been Word exploits in the wild before.

---

### Post by 0011235813 on 2012-12-04
> **Hungry Man said:**
> It's not really much harder. PDF is a poor example because the format is fairly dangerous in itself, but Javascript doesn't play into it. It's all about providing information to a program that the program can't handle. Big complex data types like PDF, DOC, or MOV are all going to let attackers fill them with tons of data - great for exploiting the complex backend systems.

Why is Adobe Reader so exploited? Well, it isn't very much anymore to the same extent, but that's due to its popularity. It's installed on tons of machines and, as I said, there are a few inherently dangerous areas of PDFs.

But I'd say infecting VLC is just as easy as Word, and there have been Word exploits in the wild before.
PDF is definitely a very poor format in this regard. But to your point of installed base – here is something to consider; the adobe flash plugin, widely known for being terrible at security, is actually *less* exploited than Reader. And *that* is installed on even more machines. 

Your point about the size and complexity of formats is interesting. While that's certainly true theoretically, in practise it is much easier to infect DOCs, PDFs etc. At the end of the day, WebM files don't run ActiveX or JavaScript on the machine, so you're much safer.

Just look at the facts. How many media players get infected? Not very many. Hardly any in fact. You could say, “well, installed user base blah blah blah” but if you think about it, most people use only a few media players – WMP, VLC, Quicktime and not much else. That's certainly a large installed user base! In fact, it's the same amount of major PDF viewers available... (Adobe Reader, Evince and Okular, oh and Preview)

Huh. That's actually more PDF viewers than media players in popular use. That's not even considering browser viewers like Chrome's...

With regards to MS Word documents, LO is used by a significant number of users, yet it doesn't get infected much at all. Why? No executable rabble thrown into a static file.

---

### Post by Hungry Man on 2012-12-04
Flash is exploited less than Reader because of the sandbox. Just as Reader 11 has only been exploited once in the wild so far, due to its sandbox. The Flash sandbox is probably a lot stronger.

JavaScript doesn't really play into it. The Reader exploit that bypasses the sandbox doesn't use JavaScript. JavaScript is a nice way to break out of the sandbox because there's a renderer that'll have to do things like eval() and it's directly dealing with attacker controlled data. But the entire PDF has to be rendered and the entire PDF is attacker controlled data, so they can do it with or without JavaScript.

> Just look at the facts. How many media players get infected? Not very many. Hardly any in fact. You could say, &#8220;well, installed user base blah blah blah&#8221; but if you think about it, most people use only a few media players &#8211; WMP, VLC, Quicktime and not much else. That's certainly a large installed user base! In fact, it's the same amount of major PDF viewers available... (Adobe Reader, Evince and Okular, oh and Preview)
The user base for video players is far more split up than the user base for PDF readers. Reader has by far a larger userbase than VLC, and that really is the big difference here.

There are a million video players and a million PDF readers, what's important is which ones hold top market share and how much that is and how much effort it takes to infect it.

If VLC were very popular we'd see attacks on it.

LO as in LibreOffice? It's not used by a significant number of users.

Millions of people don't matter. Attackers like easy targets that 90% of the population will run. anything difficult to attack or anything with 30% of the population doesn't matter.

There are loads of terribly insecure programs that could be exploited but they're just not popular enough to warrant the attention. 

In the case of VLC it's not terribly insecure, I haven't really thought about how practical infecting it is (though, again, it's a matter of running VLC content on a page for remote exploits or telling a user to run the local file) but I don't see it as any less practical than infecting MS Word, Libre Office, or anything else.

---

