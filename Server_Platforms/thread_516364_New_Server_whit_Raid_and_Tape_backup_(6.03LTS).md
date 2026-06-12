---
title: "New Server whit Raid and Tape backup (6.03LTS)"
date: 2007-08-03
forum: Server Platforms
---

### Post by Roman78 on 2007-08-03
I'm planned to reinstall my server (now running windows 2000 server). I planned to install 6.03 or 7.04 server (i prever 6.03). Now i want to make a Raid whit 2x200Gb harddisk and want to use a DDS-4 tape device on a SCSI card to backup my data.

Now the questions:

1. Making a raid is simple, but what does ubuntu do when one harddisk 
crached?

2. what program can i use to make a backup from my data? Is there a client/server program like ArcServ (novell) or Retrospect (Mac). Is it possible to backup my workstation data (windows/Mac) to the tape device in the ubuntu server? Or should i make the device extern?

Server spec: Siemens Mainboard, Intel Celeron 1100 Mhz (planned to upgrade to Pentium III 1.13 or 1.2 ghz) 512 Mb Kingston 133 Mhz. 2 x maxtor 200 gb harddisk (i know... maxtor is not the best but i have those, so i use them. Now you know why the raid LOL). Sony DDS-4 and a lots of tapes...

---

### Post by kidders on 2007-08-04
Hi there,

> **Roman78 said:**
> 1. Making a raid is simple, but what does ubuntu do when one harddisk crached?It doesn't necessarily do anything, really. Depending on what you set up, you can have your box automatically switch to a spare device, mail a warning to your phone, etc. It's up to you.

> **Roman78 said:**
> 2. what program can i use to make a backup from my data?There is a huge variety of backup apps available, all with different levels of sophistication, and different ways of doing things. My best suggestion is to do some reading & try one or two of them out.

---

