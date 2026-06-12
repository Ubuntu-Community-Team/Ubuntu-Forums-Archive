---
title: "A plea and a sad day"
date: 2010-04-05
forum: Testimonials &amp; Experiences
---

### Post by andyp6 on 2010-04-05
Dear All,

This is not meant to start of a flame war and I am not a troll looking start a fight, I am providing what I think is a valid opinion and feedback. 

My story.....

For the past 12 months I've been an Ubuntu only household (not inc the good lady), a desktop PC running as a server, print server and storage device on Ubuntu 9.04 until 4 days ago. I also have an HP laptop  that I converted from vista to Ubuntu 9.04 then 9.10 when it was released. I did originally try to upgrade the server but the network printing was messed up and didn't work so I stayed at 9.04 for the server. Both units access my wireless access point and I have an in home wireless network at the end of a very fast cable connection. 

I work in sales and am also a freelance trainer in sales and management development, therefore the server and laptop are the tools of my trade. My main use is office (open office mostly) and communications. I also had a virtual box install of windows xp for those times when i_just_had_to use M$. 

So, 4 days ago I upgraded the disks in my server to give me more storage and to be able to hold more backups from not only mine but the good lady's laptop. I took the chance and upgraded to 9.10 as the initial printing issues should have been sorted by now....

H/w upgrade ok, whilst the s/w upgrade was progressing I got down up updating a 156 slide training course I'm delivering this week to a bunch of corporate customers. This took some time, updates complete and presentation finished....click print....zzzzz I wait, and wait, and wait...I see that the local processor is processing the print job...wait for it to be sent wirelessly …..see it received on the server and processed...an hour had passed now and I'm getting concerned as I actually need 16 copies of this and I've loaded up with printer spares and paper. 

The server prints 1 and a half pages and stops indicating job complete but at a 90% proc load. (printer is an hp2575 nothing special). I investigate, try again...try printing locally, try printing directly from the laptop as I also have the latest drivers and hplip (plus gui) loaded on that....the same...why oh why did I bother to trust 9.10 I ask myself. 

As I'm semi literate technically I initially start to investigate the problem but all points back to 9.10 as an issue...I search these forums and more and find other have had similar printing or long OO processing times on 9.10. As it is absolutely essential that I have this presentation printed out for my students I cannot waste more time investigating....these are tools I need to work. I almost cry as I make the decision......

Back up my data again and ditch 9.10 on the laptop and go back to XP. Also downgrade 9.10 on the server to 9.04. I install xp and office (not inc windows updates) including a reformat of the laptop hdd from ext4 to ntfs I load my printer drivers, finish my presentation in powerpoint and print it...16 times, first time, no issue, job done

I test 9.04 printing over the network and it works although the processing on ubuntu is much slower than on xp, at least it worked. 

Now let me say, I'm a linux fan...a user not a hacker, but a fan nonetheless. I promote it, show off about it and get people to try it...but just_when_I_need_it it fails me. M$ just_worked...no fuss or hassle...it solved my problem. If the wider world and user community is going to take us linux fans seriously something has to be done about usability....it_needs_to_just_work. I appeal here to developers...please please fix the printing in 9.10 its a basic function that just needs to work...not be configured or messed with, just work. Please also consider compatibility and usability. I know great strides are being taken but there is a long way to go.

Now I'm back on 9.04 for my server and back to xp for the time being as I don't have the time (time is money for me) to “fiddle” around with my OS...I expect it to serve me and do what I need it to. I hate to say it but it looks like I'll be on xp on the laptop for a while :( (sad here)

Cheers for listening.

Andy

---

### Post by pricetech on 2010-04-05
Just do what works for you and be happy.

---

### Post by meho_r on 2010-04-05
If I were you, I'd stick with LTS for business use.

---

### Post by p0rnflake on 2010-04-05
You probably wont get to many people agreeing with you here Andy ;) But for what it's worth I can totally relate.

I've actually done the switch a couple of times - migrating all my PC's from Windows to Linux - But I always end up back on Windows for reason much like those you describe.

Today I use Windows on all systems except my home server - I'm running Xubuntu 9.10 on this one and though I've been let down by linux as a desktop OS - I couldn't ask for a better OS for my home server (I choose Xubuntu over Ubuntu-server because I use the box for some light internet access aswell).

So IMHO linux beats Windows hands down as a server OS - the flexibility you get with linux is amazing - but with flexibility comes increased complexity - and this is what (for me) makes linux a no-go on my desktops - I don't have time to spend hours troubleshooting strange issues after upgrading to a new kernel or having to read through a ton of forum posts to figure out how to sync my ipod.

---

### Post by lancest on 2010-04-06
> **andyp6 said:**
> 

Now I'm back on 9.04 for my server and back to xp for the time being as I don't have the time (time is money for me) to &#8220;fiddle&#8221; around with my OS...
Andy

Funny, that's why I don't use Windows for my affairs.
 (Sorry its the truth)
Since you are a business you must operate your IT like one.
1. Never upgrade without a testing run.
2. Why risk network upgrade? Use clean install.
3. Don't upgrade without good reason. 
   (Coming from a guy who loves testing releases) 

With sympathy I have to say it's your fault.
This is why experienced IT staff are valuable. 
Good luck in future.

---

### Post by mastablasta on 2010-04-06
> **lancest said:**
> 
With sympathy I have to say it's your fault.

 
I disagree to a point.
 
If something worked before what kind of system makes it not work with an upgrade? Even more there is also no fix after months and months... Is Lucid going to work in this case?
 
I also agree toa point that if system is important using LTS would be a way to go and not to upgrade or use some testing versions. But sitll even LTS has a limited support time.

---

### Post by darrenn on 2010-04-06
> Now I'm back on 9.04 for my server and back to xp for the time being as I don't have the time (time is money for me) to &#8220;fiddle&#8221; around with my OS...I expect it to serve me and do what I need it to. I hate to say it but it looks like I'll be on xp on the laptop for a while  (sad here)

Why didn't you setup a dual boot with your laptop? You would still be using ubuntu if you did. Anyway, your setup is a little bit complicated considering your linux experience. My rule is to keep your setup as simple as possible so that you don't run into problems. An example of this is people who try to install onto a raid consisting of ide and sata hard drives and then they wonder why the install fails. The more complicated your setup the less your chance of success. Also make sure your hardware is fully supported and if it's not sell it and buy some that does. 

One more thing to add. You should always do a clean install never upgrade.

---

### Post by Linuxforall on 2010-04-06
For all my enterprise and business I only use and recommend LTS and nothing else, the reason being surprises, six month distros are fine on cutting edge home PCs but not for bread and butter PCs, if I need latest hardware or software support, I rely on PPA or compile it myself, plain and simple.

---

### Post by kelvin spratt on 2010-04-06
No sympathy at all you should be using Debian/Redhat/Cent, for your business not Ubuntu. sacrificing stability for instability is never a wise move in business.  Ubuntu is a great system for the market it is aimed at. The LTS, is now mature but nearing the end of its life the next LTS will take 1 year to mature.

---

### Post by lancest on 2010-04-06
Where does it say that doing an net upgrade is guaranteed to work?
Based on that I'd say it's unwise to take such a risk if it disrupts your business or even your mental state.

---

### Post by Tamlynmac on 2010-04-06
> andyp6

Thank You for sharing your experience.

I believe pricetech says it all:
> Just do what works for you and be happy. 	

Based on this sections guidelines (not to be used for debate), I will not comment on your opinions. However, I do wish you Good Luck with whichever OS meets your needs/expectations.

---

### Post by NightwishFan on 2010-04-06
Hardy is not too near to end of life, especially on servers. I would use that until the Lucid .1 release.

---

### Post by armandh on 2010-04-06
too many changes [at once] on mission critical equipment 
and not pre-tested
what were you thinking

my wifes laptop runs 8.04 and it is not broken.

---

### Post by andyp6 on 2010-04-06
Hi All,

Whilst I agree with some of the comments, yes I should not have upgraded without testing first on a second server or dual boot system...fair points, but why then have an "Upgrade Manager" if you should not use it? Ok comment made like a simpleton...I'm not that naive. 

Anyway, perhaps you chaps were right in this, I should have...but one would expect that such basic functions such as printing works. I cannot see why my set up is complex though...dual booting etc is far more complex than what I had. As for the comment re a proper IT dept...well I'm a one man band so I'm my own IT dept, and finance, and sales, and delivery depts...hence I was able to recover quickly...good backup policy :-)

I will keep on 9.04 for my server but I'm afraid I'll not be evangelising about Ubuntu anymore...a loss as being a salesman I had actually converted some people over. I haven't tried debian or the other distros suggested so perhaps I'll come back to it in the future for my laptop...maybe.

I would say though, thank you for the comments, glad to know that people have been through similar and sympathise but what is it with some of you...."it's my fault" for an OS upgrade that is supposed to be a released, stable, tested and well promoted product not being able to handle printing properly? Yes I'm guilty I suppose of trusting Ubuntu and the community and having faith that it would work, some new apps I would expect to be buggy or not fully featured, however what I am talking about isn't that. Oh well off the high horse now. 

Thanks again for the comments, I hope that my small comments help someone in a small way, even if its a lesson in how to (or not to) upgrade (oxymoron?) 

At least I'm still using it, even just as a file and print server....

Cheers

Andy

---

### Post by howefield on 2010-04-06
> **andyp6 said:**
> So, 4 days ago I upgraded the disks in my server to give me more storage and to be able to hold more backups from not only mine but the good lady's laptop. I took the chance and upgraded to 9.10 as the initial printing issues should have been sorted by now....

You upgraded to 9.10 4 days or so ago having wrote this in November.....

> I solved the issue be reverting back to 9.04 and cups 1.3.9. All works perfectly there. The problem needs proper resolution before I upgrade again, reliable printing is a capability we shouldn't have to question, it should just work.

Your faith in believing the issues that you knew about would be resolved when you had to print 16 copies of a 156 page slide show is touching.

I am glad you have a robust backup policy :)

Don't forget about 10.04 which seems to be shaping up very nicely, as an LTS version it should be worth giving a go and it might do you till the next LTS.

---

### Post by aysiu on 2010-04-06
> **NightwishFan said:**
> Hardy is not too near to end of life, especially on servers. I would use that until the Lucid .1 release. *Especially* on servers? I thought LTS got 3 years of support on the desktop and 5 years on the server.

---

### Post by NightwishFan on 2010-04-06
That is what I am saying. Hardy is not end of life right when the next LTS is released, and Servers are supported longer. What did you garner from my post?

---

### Post by aysiu on 2010-04-06
> **NightwishFan said:**
> That is what I am saying. Hardy is not end of life right when the next LTS is released, and Servers are supported longer. What did you garner from my post?
Oops. I misread. Didn't see the *not* in there. Sorry.

---

### Post by NightwishFan on 2010-04-06
^_^ its fine, I have to re-read my own stuff twice before I get it sometimes.

---

### Post by MarcusW on 2010-04-06
> **meho_r said:**
> If I were you, I'd stick with LTS for business use.

+1, or Debian stable.

---

### Post by ubunterooster on 2010-04-06
Ubuntu has changed, a lot. It is not everybodies cup of tea and I recently found it may not be mine. Debian will likely run our file server as I am beginning to find there to be too many changes, too often. I like where it is going for the mainstream audience, but stability needs to be more of a concern than a more innovative user interface, lest it become like unto vista. 

Try debian.

---

### Post by stalkingwolf on 2010-04-07
I have one laptop that is running and probably will continue to run 8.04
as I dont seem to be able to find the magick spell to configure the via
graphics in any other release.

---

### Post by andyp6 on 2010-04-08
All, I'm quite annoyed to say that now I find M$ (XP flavour) gives me at least 1 hour longer battery life on the laptop! 

Being objective for a moment, what would be the reason?....access to lower level control functions, driver detail, proprietary code for h/w layers????? 

Thoughts?...blimey  this was unexpected...and also gets me thinking that why do Canonical not give over 3 hours life per standard battery on the same config laptop at full brightness that I only got 1.5/2 hours life on 9.10!!! Now as a Linux fan I feel really naffed....

Sorry

Andy

PS. Honest I am <i>not</i> a plant..I really do love linux, but I have just discovered this!

---

### Post by -humanaut- on 2010-04-08
You never explained why you risked an upgrade with a known printing problem moments before you started a mission critical print-job? That's seriously just stupid considering you already knew of the printing problem but just decided it would be safe.

---

### Post by cariboo on 2010-04-08
> **ubunterooster said:**
> Ubuntu has changed, a lot. It is not everybodies cup of tea and I recently found it may not be mine. Debian will likely run our file server as I am beginning to find there to be too many changes, too often. I like where it is going for the mainstream audience, but stability needs to be more of a concern than a more innovative user interface, lest it become like unto vista. 

Try debian.

The LTS server version is supported for 5 years, that doesn't sound like a lot of changes to me.

---

### Post by andyp6 on 2010-04-09
> **-humanaut- said:**
> You never explained why you risked an upgrade with a known printing problem moments before you started a mission critical print-job? That's seriously just stupid considering you already knew of the printing problem but just decided it would be safe.

Firstly this forum as far as I understand it isn't to insult people...no need for the stupid comment. I know I'm not stupid, holding 2 degrees, one a masters.

The upgrade was a concurrent upgrade with hardware...a new disk for which my goal was to have a fully upgraded system and use ext4 by default. My laptop was already running happily on 9.10 and cups behaved fine locally and with the raft of distro upgrades and all the posts on the net mentioning that the problems with printing were fixed, I (agree foolishly) made the assumption that this meant that the printing problems were fixed and thus the upgrade would succeed fully. This was the basis for the what should have been a simple upgrade.

A good lesson learnt though :)

Andy

---

### Post by lancest on 2010-04-09
With other Linux distro's like Arch they warn you to check the known issues in their forums before running upgrades.

It would be a good idea to Google on your problem beforehand.

You could find issues like that in any OS.
None of them are perfect.

It's good that you are being open about your problems by posting. Your knowledge will grow.
And will be able to give good advice to other budding Ubuntu users in the future. 
(12 million users by last estimate)

---

