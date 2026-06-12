---
title: "So Comcast sucks..."
date: 2007-10-05
forum: The Cafe
---

### Post by blithen on 2007-10-05
Everytime I download an ISO it ALWAYS no matter WHAT comes up corrupt. Now matter what distro. I've downloaded slackware and zenwalk, and debian at least 5 times, and each are corrupt. Anyone else with comcast have this problem?

---

### Post by Presto123 on 2007-10-05
> **blithen said:**
> Everytime I download an ISO it ALWAYS no matter WHAT comes up corrupt. Now matter what distro. I've downloaded slackware and zenwalk, and debian at least 5 times, and each are corrupt. Anyone else with comcast have this problem?

Odd...I don't have it, but that shouldn't be caused by the provider. Should it?

Are you using a download manager? I'm using Free Download Manager on Windows and you can see the progress and other people's opinions on the download. Try using that so that you can resume if there are any problems.

This may be utterly useless, but it almost looks like it's something with programs getting broken by stoppage.

---

### Post by fwojciec on 2007-10-05
Sounds more like a problem with your computer - memory perhaps?

---

### Post by buzzmandt on 2007-10-05
I use comcast and freeloader for a simple download manager, supports resume and such and have had no problem with any iso downloads.....

Side note:  I dislike comcast because I use to work for them and give them problems every chance I get, but their service has been pretty good.

---

### Post by Frak on 2007-10-05
Use DownThemAll! instead, also, Comcast is not near as bad as AT&T/SBC.

---

### Post by eljoeb on 2007-10-05
I've never had a problem with Comcast.  Sorry I can't jump on the evil corporation bandwagon.  Are you sure its not your computer?

---

### Post by p_quarles on 2007-10-05
There are a bunch of graphical download managers for Linux (WxDownloader, KGet, others). And then there's the CLI wget:
```
wget *url*
```
If the connection times out at any point, or you end up with a corrupted file, just enter the command again and it will automically resume the download.

---

### Post by RAV TUX on 2007-10-05
> **blithen said:**
> Everytime I download an ISO it ALWAYS no matter WHAT comes up corrupt. Now matter what distro. I've downloaded slackware and zenwalk, and debian at least 5 times, and each are corrupt. Anyone else with comcast have this problem?Comcast is corrupt, they are the Evil Empire!(one of many)

---

### Post by jimrz on 2007-10-05
> **eljoeb said:**
> I've never had a problem with Comcast.  Sorry I can't jump on the evil corporation bandwagon.  Are you sure its not your computer?

+1 ... have other issues with them, ie capping dl speed on torrent traffic on a rolling basis, but nothing like that. Try using a torrent for your dl's, as they perform hash checks as they go.

---

### Post by Crashmaxx on 2007-10-05
> **p_quarles said:**
> There are a bunch of graphical download managers for Linux (WxDownloader, KGet, others). And then there's the CLI wget:
```
wget *url*
```
If the connection times out at any point, or you end up with a corrupted file, just enter the command again and it will automically resume the download.

Actually you need to add the -c option for it to resume. Otherwise it makes a new file.

---

### Post by p_quarles on 2007-10-05
> **Crashmaxx said:**
> Actually you need to add the -c option for it to resume. Otherwise it makes a new file.
That's not what the man page says. If you're in the same session and dl'ing the same file, it will resume by default. 

My connection is really reliable, though, so I can't say I've had to test this (i.e., the man page could be wrong).

---

### Post by Incense on 2007-10-05
I'm on Comcast, and my ISO's download fine, via Bit-Torrent. Every night around 10 MST though, I'm unable to access anything Google related on any of my machines unless I set up an open DNS. Don't really know if that's Comcast or what, but it kind of really sucks.

---

### Post by Presto123 on 2007-10-05
> **jimrz said:**
> +1 ... have other issues with them, ie capping dl speed on torrent traffic on a rolling basis, but nothing like that. Try using a torrent for your dl's, as they perform hash checks as they go.

Well...quit using Hash then! ---Har, har, har.

I know, I know: super corny.

---

### Post by RAV TUX on 2007-10-06
My primary problem with Comcast is the super slow speeds on cable...aweful!

---

### Post by blithen on 2007-10-06
> **Incense said:**
> I'm on Comcast, and my ISO's download fine, via Bit-Torrent. Every night around 10 MST though, I'm unable to access anything Google related on any of my machines unless I set up an open DNS. Don't really know if that's Comcast or what, but it kind of really sucks.
Woah thought I was the only one with this problem. exact same thing happens to me.

---

### Post by blithen on 2007-10-06
> **fwojciec said:**
> Sounds more like a problem with your computer - memory perhaps?
I just ran memtest+86 for like 2 hours.
And I still have problems, so it is comcast...gaaah.

---

### Post by Incense on 2007-10-06
> **blithen said:**
> Woah thought I was the only one with this problem. exact same thing happens to me.

Sweet. Glad I'm not alone as well. Just using an open DNS will fix it. I'm just trying a torrent and it wouldn't go through until I clicked the encryption box in ktorrent. So much for net neutrality. :(

---

