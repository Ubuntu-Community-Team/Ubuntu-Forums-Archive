---
title: "Thin clients"
date: 2012-10-04
forum: Virtualisation
---

### Post by DieEier on 2012-10-04
Hi there

I am almost sure that what I want to do is possible, but I am stuck.

Here's the situation. I run the network at our school and as such get called to fix a lot of software problems on windows pc's that get wrecked by users (software). What I want to do is set up a single ubuntu server and host several windows pc's on this server that users can then log into and use (like a thin client)

Ideally  I want to set up 1 standard virtual windows pc for users to log  in as if they had windows loaded on their desktop (preferably running  linux) and then just have the standard snapshot restored every morning. 
No more messy desktops, no virus problems ! Voila.

This should enable us to use low cost workstations. 
I know how to set  up virtual machines on virtual box, but I get stuck on how to make them available on a the network.

Any advice will be much appreciated ;)

Ideally  I want to set up 1 standard virtual windows pc for users to log in as if they had windows loaded on their desktop (preferably running linux) and then just have the standard snapshot restored every morning. 
No more messy desktops, no virus problems ! Voila.

---

### Post by Lars Noodén on 2012-10-04
Why not think about a long term solution and turn to Edubuntu or LTSP or K12-LTSP instead?

[http://www.edubuntu.org/](http://www.edubuntu.org/)
[http://www.ltsp.org/](http://www.ltsp.org/)
[https://fedorahosted.org/k12linux/](https://fedorahosted.org/k12linux/)

That will get you easy to manage thin clients without having Windows get in the way.  If Windows is needed for ideological or other reasons it could be quarantined in a virtual machine using Virtualbox and a fresh, clean snapshot used for each session.

Edubuntu and the others are growing in popularity and you can find testimonials or case studies if needed.

---

### Post by 1clue on 2012-10-04
I would be strongly inclined to follow Lars Noodén's recommendations.

You could use Linux to install Windows images as either a thin client or a thick client, but you run into issues.

Chances are every PC you're dealing with uses an OEM Windows image.  Those images are generally limited to install on very few PCs.  One time we tried to get new images from the manufacturer, and they said their images were limited to 50 boxes before they changed a serial number.  So any image CD from this manufacturer would only install onto 50 distinct pieces of hardware.  Number 51, even if the hardware were otherwise identical, has a different identifier built into it and needs a different CD.  I'm sure every manufacturer has different specs regarding that but I doubt there's a manufacturer who just lets one CD install onto any of its products.

If your school is like every other place that uses computers, you didn't buy them all at the same time.  You bought them 10 at a time or even less, and from whoever had the best price at the time.

So in order to do this with Windows, you'll need to buy appropriate licenses for however many copies of Windows, not an OEM variety but a full version.  Even if you get a site license of some sort, that's gonna be a significant cash outlay that I doubt your bean counters will like.

There are specific licenses for Windows and this sort of scenario, and you'll probably need to get that.  There's a Microsoft number you can call to get an idea, they're very helpful and since they don't actually sell the licenses you can ask them all sorts of crazy questions and they'll probably be much more helpful than you imagine.  They know that if you're calling them, you're TRYING to be legal, which makes you one of the good guys as far as they're concerned.  If they don't know, then they don't know.

All that said, and having jumped through some of those Windows hoops, I recommend starting with 10 boxes you get from your school (or maybe a classroom), install one of the scenarios Lars gave and show your school a pilot of what you intend.

---

### Post by DieEier on 2012-10-05
Thank you both for your responses.

I would love to get all non open source software out of my life, so yes edubuntu would be great. My problem lies in the cirriculum which still prescribes windows and msoffice :confused:

Looks like making a virtual machine on each pc individually will have to be the way to go. I am very fortunate in that all 4 of our labs have the same hardware in that particular lab, so mostly I just prepare 1 machine and clone.
Still like to save the school some money by working out the thin client set up. This has the potential of helping some of the other schools in our rural areas that barely have money to keep their doors open. 
As far as licensing goes we are well covered by the ms schools program, so no legal problems at least.

Thanks to everyone who has replied and may still reply. The people who share and want to help and learn are the heart of foss and thats why I love it. You rock!:guitar:

---

### Post by 1clue on 2012-10-05
The VM does not have to be the way it goes.  Google on PXE network boot.  Works with Linux or Windows.  Or Mac, I think.

You might choose to have a thick client setup though.

Thin clients get the entire OS from the network, and do not necessarily have any sort of hard drive.  This puts a pretty big strain on the network when people start coming in and turning things on.

Thick clients have a hard drive, which all your systems do.  They store the last image they loaded on the disk.  They boot up, check the PXE server for a new version, and if there isn't one they load the pristine image from last time just as though it were a net boot.  If there's a new image it acts just like PXE only it stores that image on the disk.

Another thing that might help is to go to a Terminal Services environment.  This uses a Microsoft server, and a bunch of clients which could be PXE thin/thick clients and could run edubuntu or similar, because Linux has a great Terminal Services app.

In this case, everything Windows is on the server.  The kids might mount a flash drive for their take-home assignments.

---

### Post by DC80 on 2012-10-10
Hi!

I did this a while ago but at the time with Windows Servers and Terminal servers. We had them running with thin clients. If you look for software take a look here: [www.2x.com](www.2x.com). This is for the thinclients. It takes an image from the 2x server via PXE. From there you can automaticly connect to your "terminal server".

Be it windows or linux, it does work well.

Be aware: because 2x is getting the image via the network it will generate some traffic. Although, you may choose to install a local copy.

---

