---
title: "Finding the bottleneck"
date: 2013-04-11
forum: Server Platforms
---

### Post by Derlux on 2013-04-11
Today I realised that my server can only upload and download with a 11 mb/s max. I have been searching for the bottleneck what causes it to this limit, but I am now really out idea's.

First I thought it was the network card, I checked it and it appears to be a Gigabit lan card. The orange light is off when it doesn't copy or paste any files, but as soon I start uploading a file it starts blinking, so it appears it uses it's gigabit lan.
Then I thought I could be the hard disk drive but that one is recently bought and a 1 TB drive. This can't  be the problem.
Then I suspected the raid controller; it is an adaptec 2410SA: [http://www.adaptec.com/en-us/support/raid/sata/aar-2410sa/](http://www.adaptec.com/en-us/support/raid/sata/aar-2410sa/) This could still be it but it's specs say otherwise.

My server is a Dell Poweredge 1800. Does someone have advice for me?

---

### Post by Toxic64 on 2013-04-11
not much infos here.
what's your average download speed on other machines?

---

### Post by gordintoronto on 2013-04-11
What do you use for your Internet connectiom?

You mentioned a RAID controller and buying "a" hard drive. What level of RAID are you using? What drives? (brand and model)

Cable lengths and cable clutter can have an effect. It's quite unusual to see upload and download both running at the same limit, which raises a red flag about the cables.

Upload and download to where?

---

### Post by Toxic64 on 2013-04-12
Could also be QoS with speed restrictions I guess. In fact, it could be a lot of things.

---

