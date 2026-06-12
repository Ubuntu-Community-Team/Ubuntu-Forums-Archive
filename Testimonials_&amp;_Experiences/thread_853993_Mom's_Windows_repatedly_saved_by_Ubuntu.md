---
title: "Mom's Windows repatedly saved by Ubuntu"
date: 2008-07-09
forum: Testimonials &amp; Experiences
---

### Post by fsando on 2008-07-09
Hi just wanted to share this little story.

Now, I've been used to be the one in the family who helped out whenever somebody's windows mysteriously went haywire. 

It usually goes like this, a phone call from my mom, some generalities about my wellbeing etc. and then it comes: the prospect of a long frustrating afternoon in front of her pc. At the end we decide that it's easier to try and rescue her data out of the ruins and reinstall. I do the rescuing she does the reinstall herself the following days accompanied by numerous conversations on the phone.

I started to use ubuntu a little under two years ago. Half a year back the situation arose again. This time I tried a new approach. I gave her the Ubuntu live cd, I didn't even instruct her how to use it apart from 'drop it in, boot'. She figured everything out herself, got her data out to an external hd, reinstalled windows and was up and running within a couple of days. I was, of course, being kept meticulously updated ;)

Now it happened again. This time she specifically asked me for the live cd as this seems to her the easiest route to a working system: Use the live cd to rescue data, reinstall windows. :lolflag:

---

### Post by lisati on 2008-07-09
That's great! Next step, if she's interested, make a dual-boot system for her to play with..... and from there, who knows?

---

### Post by fsando on 2008-07-09
> **lisati said:**
> That's great! Next step, if she's interested, make a dual-boot system for her to play with..... and from there, who knows?

That's what I've told her many times. And she is beginning to contemplate that option. There is one snag though that I have to agree with. She makes extensive use of mail-merge in Word, Openoffice's mail-merge ranges somewhere between awful and unusable (and the bug about this has sat in Ooo's bug tracker for several years),  this is the main issue holding her back. Any of her other anxieties about switching can be easily overcome.

---

### Post by michaelkahl on 2008-07-09
I recently had a similar experience with my Mom.  I maintain their PC, and after the last virus I said next one gets you Linux or I'm not working on it.  She was more than fine with that.

---

### Post by Canis familiaris on 2008-07-10
> **fsando said:**
> That's what I've told her many times. And she is beginning to contemplate that option. There is one snag though that I have to agree with. She makes extensive use of mail-merge in Word, Openoffice's mail-merge ranges somewhere between awful and unusable (and the bug about this has sat in Ooo's bug tracker for several years),  this is the main issue holding her back. Any of her other anxieties about switching can be easily overcome.

If she has reasonably powerful PC (preferably 1GB RAM), I would recommend she gets rid of Windows and install Ubuntu and install Windows in Virtualbox in Ubuntu.
This way she could run her MS Office as well. And save her documents in a shared folder b/w Virtual Windows and Ubuntu. She could create a perfect setting of XP Virtual Machine, save a snapshot of the Virtual Machine Windows XP, and if something goes wrong wih XP, then restore to the perfect system with few clicks.

---

### Post by fsando on 2008-07-10
> **Anurag_panda said:**
> If she has reasonably powerful PC (preferably 1GB RAM), I would recommend she gets rid of Windows and install Ubuntu and install Windows in Virtualbox in Ubuntu.
This way she could run her MS Office as well. And save her documents in a shared folder b/w Virtual Windows and Ubuntu. She could create a perfect setting of XP Virtual Machine, save a snapshot of the Virtual Machine Windows XP, and if something goes wrong wih XP, then restore to the perfect system with few clicks.

Well, I've thought about that. I don't know about 8.04 but I've been there before myself with 6.10, 7.04 and 7.10 and I have to say the experience was not exactly a pleasure. I tried vmware, virtualbox qemu/kvm. The one that worked best for me was virtualbox but it had major issues with communicating across to linux hd, certain character combinations in filenames created the weirdest errors LOL (or perhaps not?).

I also never got vmware to communicate across - had to use external usb drive, then logout,login (or was it umnount/mount?) to get data back and forth. qemu/kvm never got off the ground for me.

So unless it has changed substantially in 8.04 I foresee even more support for the virtual than for the real one ;/ Another issue is that her windows came with the laptop so it's not really installable that way. 

What about Wine?

For myself I don't need windows on an everyday basis anymore so when I need it I boot into the real thing and live with it for the few hours it's needed.

In all honesty I think ooo/sun should get their act together on that point as it is repeatedly being asked for over several years, there even is a page somewhere called something along the lines of 'Open office - the missing mail merge' that takes you through the convoluted process of doing a simple mail merge. Though it works its capabilities are very weak, the process is complicated and prone to absolute disaster. 

At one time I (and my mom) spend two full days not making it work and the better part of a week afterwards confirming that our findings were indeed true. Actually every time Ooo comes up even just as a modest hint with no intentions she gets quite agitated. So I'm not quite sure how to go on from here.

Anyway as the viruses, general failures or whatever it is slowly get to her I feel that even Ooo begins to look like an acceptable compromise.

Anyway thanks for the answer.

---

### Post by Malac on 2008-07-10
MS Office/Word 2000 works fine under WINE for me when I particularly need something.
 
Slight bug with clipart every now and again.
 
Try that and see what she thinks.

---

### Post by fsando on 2008-07-10
> **Malac said:**
> MS Office/Word 2000 works fine under WINE for me when I particularly need something.
 
Slight bug with clipart every now and again.
 
Try that and see what she thinks.

That's great. I'll be sure to test it :guitar:
Thanks

---

### Post by stalkingwolf on 2008-07-10
There is also crossover linux as an option.  It will run
office2000 .

---

### Post by kaitwospirit on 2008-07-11
OpenOffice will be upgrading to a new version in a couple months. Maybe they'll fix mail merge - a lot of people seem to be asking them to.

---

### Post by hyper_ch on 2008-07-11
vbox --> install guest additions, then make a shared folder from the VM properties, then connect it as drive in the vmed windows (I use x:)

---

### Post by fsando on 2008-07-11
> **hyper_ch said:**
> vbox --> install guest additions, then make a shared folder from the VM properties, then connect it as drive in the vmed windows (I use x:)

Hi Hyper
I did that before but certain character combinations in filenames would confuse vbox and produce real strange results. 
It made for quite a few laughs for me and my more nerdy friends to try out char-combinations. Of course the apps using those files would fail and crash.

Anyway I use windows so rarely these days that__ it's not worth the trouble. I've set aside 10 Gb for windows and that's it. Eventually that's probably gonna go too. 

I don't expect to keep windows on my next laptop, that's assuming I can't get one without windows. I'm dragging my feet right now to see if any of the high end laptops come in a 'clean' version as the 'cleanness' seems to be moving up the ladder ever so slowly.

---

### Post by fsando on 2008-07-11
> **kaitwospirit said:**
> OpenOffice will be upgrading to a new version in a couple months. Maybe they'll fix mail merge - a lot of people seem to be asking them to.

I seriously dobt it. I think the design philosophy somehow prevents that. I would expect a plugin coming along soon though.

The philosophy is that the data for the merge must come from a native ooo database format. This means that whatever the original data it must be imported to a ooo-db and then the mail-merge must be done from this db.

Therefore anyone doing a mail-merge will have to deal with fairly advanced db-issues, not in detail but if anything goes even slightly wrong you will find yourself in the 'advanced trouble shooting'. I don't think that's the proper way for a general purpose app like an office word processor.

My suggestion was, and is, that mail-merge should be able to take any table as input, create a temporary data source transparent to the user and go ahead with the merge.

The table could come from within the same document (ie. a list of names and addresses you just created), from a spreadsheet or from a company data base. The ordinary user should never have to worry about databases or anything.

---

### Post by wolfen69 on 2008-07-11
> **fsando said:**
> 

I don't expect to keep windows on my next laptop, that's assuming I can't get one without windows. I'm dragging my feet right now to see if any of the high end laptops come in a 'clean' version as the 'cleanness' seems to be moving up the ladder ever so slowly.

see [this]("http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs")

---

### Post by fsando on 2008-07-14
Hi wolfen
> **wolfen69 said:**
> see [this]("http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs")

Yes I've been thinking about a Dell with Ubuntu, they're just not really in Europe yet. There's another one though that has me sort of drooling. It's the toshiba R500 12s it has a *transflective* screen which should mean that you can use the sun as light source and turn its own source off completely. It would set me back a bit though - 4600 $ to be exact ;D Don't know if it will run Linux but older versions of it seems to do.

I've really been waiting for a laptop for years that you can take out into the sun just as you you used to do with liquid crystal screens (or whatever they were) back then. My first Palm had something like that.

---

### Post by armandh on 2008-07-14
set it up dual boot
just no network connection on the win side
now that is safe

---

