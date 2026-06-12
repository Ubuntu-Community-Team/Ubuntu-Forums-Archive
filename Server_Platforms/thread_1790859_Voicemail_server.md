---
title: "Voicemail server"
date: 2011-06-25
forum: Server Platforms
---

### Post by 110686 on 2011-06-25
Hello,

I've got a Dell Dimension 5150c acting as a home server. It is running Ubuntu 10.04. The PC has connector for a phoneline built in. Is there any way that I can turn this machine into a voicemail server (perhaps with email notification when voicemail was used)?

---

### Post by drdos2006 on 2011-06-25
Try this:
[http://www.asterisk.org/](http://www.asterisk.org/)

regards

---

### Post by volkswagner on 2011-06-25
I believe you need a phone card, not a standard modem, which is likely installed.

Once you look into Asterix, find the supported hardware, it is not cheap.

---

### Post by rubylaser on 2011-06-26
All you need as an FXS to FXO adapter.  This will convert the POTS line into an ethernet jack.  A Sipura 3000 is on example of this.
[http://www.convertermarts.com/servlet/the-520/Linksys-SPA-dsh-3000/Detail]("http://www.convertermarts.com/servlet/the-520/Linksys-SPA-dsh-3000/Detail")

I would use PBX in a Flash if you want to setup a PBX. (It's very easy to setup a functional Asterisk PBX)
[http://pbxinaflash.net/]("http://pbxinaflash.net/")

It isn't too expensive to setup a PBX, but it seems like massive overkill just for voicemail. If you're going this route, you might as well go for a PBX and cut the phone line all together.

This is a great site for all things Asterisk PBX [http://nerdvittles.com/]("http://nerdvittles.com/")

---

