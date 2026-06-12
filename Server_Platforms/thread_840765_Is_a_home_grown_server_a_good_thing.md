---
title: "Is a home grown server a good thing?"
date: 2008-06-25
forum: Server Platforms
---

### Post by the lemming on 2008-06-25
I have Ubuntu running on my laptop while I have Vista running on my Desktop.

The plan was to store all my movies and music on my Desktop which has a shed load of Hard drive space and then get the laptop to access those files so that I can then watch a movie or listen to my music around the house or in the garden.

That was the plan but then I got fed up trying to get both computers to talk to each other so I had the idea of storing my media externally so that both my Vista box and Ubuntu laptop could access the data as and when they needed to.

Is such a set-up possible?

If it is then what would I need, with the emphasis on a tight budget rather than paying hundreds or thousands of pounds, to get this little project to work?

Cheers

---

### Post by adza on 2008-06-25
Hi Lemming, i have a similar setup at home (although i don't run vista!) with an xbox media centre. I had a need for centralised content to be stored so that the media centre, the xbox and my laptop (over the wireless network) could all access this content. A quick browse on ebay and i secured a SUN Ultra 60 server for $120 AUD, a second purchase of a 70GB SCSI drive ($70) saw my storage needs covered (not that much content required i guess).. I installed ubuntu server on the SUN machine, configured a samba share and the rest, as they say, is history. All told, it cost me $200 AUD, although you could get any old server to do the trick or convert an old desktop machine... Admittedly, my project was mainly for the 'fun' of it, but such a setup would work for you :)

---

### Post by bloodniece on 2008-06-25
I second Adza, I have a couple Ubuntu servers setup at home (an ubuntu fiend)

One is my Samba (SMB) server for media (audio and video) and also does NFS exports for my OSX machine. The other is an LAMP server and Icecast machine.  Both were built using a celeron 700mhz and a pentium 3 1.0ghz respectively. So, basically any old heap can be a Samba server - you just need a big HD for media/files

---

