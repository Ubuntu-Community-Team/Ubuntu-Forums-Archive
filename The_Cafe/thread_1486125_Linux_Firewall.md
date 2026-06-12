---
title: "Linux Firewall?"
date: 2010-05-17
forum: The Cafe
---

### Post by McRat on 2010-05-17
I read somewhere about somebody using a Linux machine as a dedicated internet firewall.

My neighbor wants to share my internet connection, but I don't want them to see my network.

Does anyone has some advice or experiences with this?  I'm thinking I'd just put two network cards in the box, and somehow have Linux isolate the two, and replace my existing internet firewall.

---

### Post by 98cwitr on 2010-05-17
here's what you're looking for

[http://www3.untangle.com/](http://www3.untangle.com/)

---

### Post by anomie on 2010-05-17
Assuming you don't want to roll your own solution, a couple other free beer possibilities are: 
[list]
[*] IPcop
[*] Smoothwall Express
[/list]

---

### Post by CharlesA on 2010-05-17
PFsense is pure win.

Of course there are other ones too.

---

### Post by McRat on 2010-05-17
Thanks!

Well the Untangle seems to be overkill and underkill at the same time.  I thinks it's more focused on controlling your employee behavior on the internet, than internet sharing.  It's a monthly subscription service? as far as I can tell, but does not support throttling (necessary when sharing) or a usage meter.

We are in an internet "dead zone" in the middle of a high population region (Southern California).  The fastest advertised speeds we can get are 1.5mbps down, and 384kbps up, but it's not reliable at those speeds.  3G cellphones are faster than our DSL or Satellite.  No cable possible, even though it's right at the sidewalk.  Times Warner doesn't want to hook it up at any price.

I figured out a way to get broadband into the building and wanted to help the other businesses, but it's now looking like a huge hassle.  I can't figure out how to isolate our LAN from others if I give them internet access. 

I need to learn how to say "no".  I already spent 40 hours and $1000 trying to set up a second path into the building but failed.  That's enough charity. 

I'll look at IPCop and Smoothwall express.

---

