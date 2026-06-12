---
title: "Samba Shares with Antivirus"
date: 2011-09-06
forum: Server Platforms
---

### Post by PierreRobiquet on 2011-09-06
Hello,

I'm wondering what the best product would be to get an anti-virus that will run a daemon and scan the files in the shares only in real time? I've seen Samba-Vscan but it hasn't been updated since 2005 and I'm wondering if someone has a better suggestion.

---

### Post by stmiller on 2011-09-06
clamav is what you are after. 

```

sudo apt-get install clamav

```

It is command line-only though a few guis exist for it. I'll try to get a write up on my blog soon.

Edit: whoops, looks like for real-time you need [http://svs.sourceforge.net/](http://svs.sourceforge.net/) - though you have to compile samba. hmmm

---

### Post by PierreRobiquet on 2011-09-06
I'm just running Ubuntu Server without a DE anyway so everything I do is in the CLI. 

With ClamFS is it possible to only scan certain file locations? I have a separate folder set up for all the Samba shares and I would rather just have it scan that then the whole file system.

---

