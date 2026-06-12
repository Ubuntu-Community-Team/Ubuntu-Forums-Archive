---
title: "64-bit download link is down"
date: 2020-04-13
forum: Ubuntu, Linux and OS Chat
---

### Post by ladrano on 2020-04-13
[http://cdimage.ubuntu.com/lubuntu/releases/19.04/release/lubuntu-19.04-desktop-amd64.isoThis](http://cdimage.ubuntu.com/lubuntu/releases/19.04/release/lubuntu-19.04-desktop-amd64.isoThis) one. Can't download the file.

---

### Post by wildmanne39 on 2020-04-13
That is because 19.04 has reached EOL. try:

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

Select a supported version of ubuntu.

The link you posted is broken probably because "this" is also highlighted as part of the url.

---

### Post by ladrano on 2020-04-13
Unfortunately I have a 1ghz processor, and Ubuntu 18.04.4 LTS may be a little to much for my machine. Such a pitty to know that lubuntu has gone EOL.

---

### Post by ladrano on 2020-04-13
And I am sorry. [http://cdimage.ubuntu.com/lubuntu/releases/19.04/release/lubuntu-19.04-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/19.04/release/lubuntu-19.04-desktop-amd64.iso) is broken also.

---

### Post by wildmanne39 on 2020-04-13
lubuntu 19.10 can be downloaded from.

[https://lubuntu.me/](https://lubuntu.me/)

Edit:

Moved to Ubuntu, Linux and OS Chat since this is not a support request.

---

### Post by DuckHook on 2020-04-13
> **ladrano said:**
> &#8230;Such a pitty to know that lubuntu has gone EOL.
:confused:

Lubuntu 18.04 has not reached EoL. It has a year left on it whereas 19.10 only has another 3 months.

My recommendation: install 18.04, then upgrade to 20.04 at the first point release. Sticking to LTS releases will provide you with more stability. If you use wildmanne39's link, it will lead you to 18.04 as well.

---

### Post by deadflowr on 2020-04-13
It's probably because you're looking at the lubuntu.net.
Use lubuntu.me here:
[https://lubuntu.me/downloads/]("https://lubuntu.me/downloads/")

Edit:I didn't realize wildmanne already posted a link to lubuntu.me.
ftr, lubuntu.net only has a link for 19.04 as the latest release, so it hasn't been updated in almost a year now.

[lubuntu.me vs lubuntu.net]("https://askubuntu.com/questions/1029381/which-lubuntu-website-is-the-correct-one")
for a quick reference as to why two different sites.

---

### Post by mörgæs on 2020-04-14
> **ladrano said:**
> Unfortunately I have a 1ghz processor...

Aye you sure that it is 64 bit?

---

### Post by DuckHook on 2020-04-14
> **mörgæs said:**
> Aye you sure that it is 64 bit?
Good catch.

---

### Post by guiverc on 2020-04-14
> **DuckHook said:**
> :confused:
My recommendation: install 18.04, then upgrade to 20.04 at the first point release. Sticking to LTS releases will provide you with more stability. 

If you're using a x86 (32-but or i386/i686) machine, then I'd suggest Lubuntu 18.04 LTS as well.  (*19.04 & later releases weren't available in anything but amd64 [ignoring alphas]*).

If you're using x86_64 (or amd64) and your machine is capable of 64-bit, then you have a decision.

Lubuntu 18.04 LTS uses the LXDE desktop, and a upgrade to a more modern LXQt desktop will require a re-install, so selecting 18.04 will mean you'll need to re-install if you plan on using your system past 2021-April (EOL for Lubuntu 18.04 LTS which is 3 years being a flavor) because of the change in desktop.

Yes it's possible to force upgrade (*I did for the box I'm replying on*), but you'll have problems which is beyond most non-technical users, which is why it's unsupported. *I may be able to point to some documentation on upgrading to 18.10 but it'll be out-of-date and wasn't perfect thus was never officially published*.

So if you want an upgrade path without re-install, the Lubuntu 19.10 path (even with it's ~3 months of supported life) is the better choice, if you can use amd64.  For x86 it's 18.04 LTS (*as 19.04 is now EOL and was the last with x86 support*)

---

### Post by mörgæs on 2020-04-14
IF you have a 32 bit processor I recommend [Debian]("https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890") over Lubuntu 18.04.

---

