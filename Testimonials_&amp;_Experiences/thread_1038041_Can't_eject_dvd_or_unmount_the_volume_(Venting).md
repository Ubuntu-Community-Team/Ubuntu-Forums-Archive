---
title: "Can't eject dvd or unmount the volume (Venting)"
date: 2009-01-12
forum: Testimonials &amp; Experiences
---

### Post by iNeeed on 2009-01-12
I going to say it.

Ubuntu is great until I have to use it for something.

Its fantastic to browse the web until I want to watch something on netflix.
Its great for music until I need to update my Iphone(No linux for itunes) I actually had to erase and reinstall my iphone while trying to use it with ubuntu and lost all of my data.  before you gave a smart answer I did back it up using itunes on vmware, but that crashed in the process and the whole thing fried. 
Its great for word processing, until you need to write something and it starts crashing everytime.
Or browsing the web, til you try to do it in a coffee shop and then you have to go home and spend 3 hours setting up the wiresless card.
ABSOLUTLEY everyting I've tried to do on this thing I have been unable to.  I then have to dedicate at least a couple of hours if not DAYS to finding an explanation and an answer.  DAYS!
I am a noob.  
I can undeerstand being passionate about someting.  something like computers.  I unfortunatley have other passions which occupy my time and can not dedicate my life to this thing.  
Today I burned a data dvd and then tried to eject the disk.  

CAN NOT UNMOUNT VOLUME.  what a surprise!!  CAN NOT EJECT.  A real shocker there.  so now its been about 1 hour and I'm searching through posts and can't find an answer but I 'm so damn frustrated I don't even want one, so I reboot into vista and POOF my eject button works.  See people, this is what people pay money for.  so when they push the button it works.  To think that this will tae off with the general public is laughable at this point.  I would love to believe that.  I really really would.  I HATE windwos, but I am completely sick and tired of ubuntu.

---

### Post by LowSky on 2009-01-12
Way to vent....

I love how most of you issues are cause by your ignorance. iPhone has never worked, and wireless cards have always been an issue, and both have been documented in numerous posts all over the web.

Try, just try to install Windows for yourself. Just try to install your iPhone or your Wireless card without the drivers that are supplied by the manufacturer, or any other driver that windows can't find without you possessing the install CD.

As for your DVD and word processing issue, that was most likely casue by some glitch, which has even occured to me in Windows, not to mention have you tried using other word processors  or updating? MS Word is one of the worst written pieces of software I have ever used. It cant handle a file size over a few MB's. Try importing a picture and it goes to poop.

Linux wasn't made to replace Windows. It was made to be an availible option that was different then Windows. this mentality applies to Ubuntu.

---

### Post by iNeeed on 2009-01-12
I am aware of my ignorance. Thank you for your astute observation.  


> **LowSky said:**
> Way to vent....

I love how most of you issues are cause by your ignorance. iPhone has never worked, and wireless cards have always been an issue, and both have been documented in numerous posts all over the web.

Try, just try to install Windows for yourself. Just try to install your iPhone or your Wireless card without the drivers that are supplied by the manufacturer, or any other driver that windows can't find without you possessing the install CD.

As for your DVD and word processing issue, that was most likely casue by some glitch, which has even occured to me in Windows, not to mention have you tried using other word processors  or updating? MS Word is one of the worst written pieces of software I have ever used. It cant handle a file size over a few MB's. Try importing a picture and it goes to poop.

Linux wasn't made to replace Windows. It was made to be an availible option that was different then Windows. this mentality applies to Ubuntu.

---

### Post by iNeeed on 2009-01-12
What I am saying is Ubuntu/Linux is not ready for the average windows user.  People have lives.  They have jobs, passions, activities.  Yours is computers.  I understand that.  That is great. I have one too.  It is not computers.  I am saying this because this is how ubuntu was "sold" to me.  To say that I should have known about the iphone and wireless problems is ridiculous.  I thought it was safe to assume that some of the biggest products and devices in the world would be compatible.  Maybe I should not assume that the keyboard will work either and I'll have to somehow mentally project my thoughts in some sort of code to get that set up?

> **LowSky said:**
> Way to vent....

I love how most of you issues are cause by your ignorance. iPhone has never worked, and wireless cards have always been an issue, and both have been documented in numerous posts all over the web.

Try, just try to install Windows for yourself. Just try to install your iPhone or your Wireless card without the drivers that are supplied by the manufacturer, or any other driver that windows can't find without you possessing the install CD.

As for your DVD and word processing issue, that was most likely casue by some glitch, which has even occured to me in Windows, not to mention have you tried using other word processors  or updating? MS Word is one of the worst written pieces of software I have ever used. It cant handle a file size over a few MB's. Try importing a picture and it goes to poop.

Linux wasn't made to replace Windows. It was made to be an availible option that was different then Windows. this mentality applies to Ubuntu.

---

### Post by philinux on 2009-01-12
Open a terminal from applications>accessories. Post the output of this.

```
cat /etc/fstab
```

Also, if you say put a paid for dvd in can you eject it?

---

### Post by Hospadar on 2009-01-12
You suould just use another OS. It's not a crime to use windows or a different distro. Come back in 6 months or a year and see if your problems are fixed. Use the best tool for the job.

---

### Post by iNeeed on 2009-01-12
> **philinux said:**
> Open a terminal from applications>accessories. Post the output of this.

```
cat /etc/fstab
```

Also, if you say put a paid for dvd in can you eject it?

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e6f2f2df-5c6e-4e9a-8311-0bac38daf54d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a4017fd7-2d5f-4a7f-b52f-c4926537cbc8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

here is the output.  I have been able to eject movie/paid dvds.  I have since ejected the dvd using windows, but this is the current output.  Thanks for your help.  I have to go to work but will check back later.

---

### Post by philinux on 2009-01-12
Your fstab entry for you're burner is the same as mine. I suspect there is a bug in brasero if this is what you used to burn your dvd. Install k3b from synaptic and use it to burn for now.

---

### Post by iNeeed on 2009-01-12
> **newbee70 said:**
> Hi Troll, trying to start a flame war are ya.

Sounds to me like your not ready for prime time! quit whining, If your such a windows fan stick with it because it is the right teet for you.


haha. Nope just stating the obvious or perhaps you are not ready for the truth in oppressive commie ubuntu land where criticism of the all mighty ubuntu is strictly prohibited.  Unless of course you are criticizing capitalistic microsoft, then thats ok.

---

### Post by iNeeed on 2009-01-12
> **iNeeed said:**
> haha. Nope just stating the obvious or perhaps you are not ready for the truth in oppressive commie ubuntu land where criticism of the all mighty ubuntu is strictly prohibited.  Unless of course you are criticizing capitalistic microsoft, then thats ok.

If you really want to stick it to the man then it HAS to be more user friendly so stop getting your panties in a bunch.  


So I'm driving around in a junker ford escort.  I've had it all my life.  I start it up and it runs, though not very well.  I hit the brakes and it stops.  Does everything I need it to, but not very well.  There is no alarm and no windows.  I have some duck-tape to keep people out, but it doesn't work very well and my stuff gets stolen often.
One day someone gives me a Ferrari.  For free!  The only problem is the brakes don't work, the windows don't roll down, the gas works, but the steering doesnt.  The heet is broken, the AC is out of whack, the mirrors are all pointing the wrong way.  All of the mechanics say how great it is and everything I can do with it and how powerful it is.  I start it up and it goes very fast and its really great until I need to turn or until I need to slow down or until I need heet and then I crash. 
So I put the Ferrari into the garage and keep my Escort and decide that little by little I'll figure out how to use the thing, but in the meantime when I need to do something I'll just drive the escort because it does everything that I need it to. The mechanics can scoff and mock me but that ok.  They are covered in dirt and grime and that's all they do all day anyway.

---

### Post by LowSky on 2009-01-12
> **iNeeed said:**
> To say that I should have known about the iphone and wireless problems is ridiculous.  I thought it was safe to assume that some of the biggest products and devices in the world would be compatible.  Maybe I should not assume that the keyboard will work either and I'll have to somehow mentally project my thoughts in some sort of code to get that set up?

I guess you never read the box or manual to your iPhone or most of the products you connect to your computer. The iPhones says right on the box will work with Apple OS/X and Windows XP and Vista, in accordance with iTunes. No where is there a version of iTunes for Linux. Which you could have noticed when you tried to download it from the Apple website.

Dont go blaming Linux for this, blame companies like Apple who don't supply open-source drivers or anything to people who use Linux. We have to make do making our own. We did it for DVD playback and for many other things.

If you want a war you will get it from much more passionate people than me. For me Ubuntu does all I need it to. I can surf the web, my wireless works, DVD never get stuck. Sure I have issues, I like MS Outlook better than Thunderbird and Evolution. But I rather not pay for my software. And not to mention I cna keep a 8 year old machine running like a champion.

 Setting up my computer isn't a lifestyle I have plenty of things to do to keep me busy. Buying a phone because it has a touch screen and can play some DRMed music and movies on a 3 inch screen is almost stupid, or making assumptions that something is "just like windows, only free" No I buy the phone that works on the best network and is more compatable with my lifesyle, and I RTFM and reviews before I make a purchase!

So you see it isn't because I choose to have a life in Computers. I choose not to be tied to some corporate giant who sells garbage appliances that batteries cannot be changed or unusable when the new models comes out, or for an OS that gets even my most computer unsavvy  friends to cringe and moan that Vista sucks. My conclusion is simple if you hated your experience so much why did you feel that you needed to post and belittle fellow users, you should have quitly just switch back to windows and left us in peace.

---

### Post by overdrank on 2009-01-16
I have removed two post from this thread and please keep the COC in mind when posting. Please be polite. Thread moved :)

---

### Post by hyper_ch on 2009-01-16
> **iNeeed said:**
> What I am saying is Ubuntu/Linux is not ready for the average windows user.
Please define the average windows user

and did you ever try a vanilla windows?

---

### Post by timcredible on 2009-01-16
not sure how the netflix thing is linux's fault since netflix went out of it's way to purposely make sure that instant viewing doesn't work on linux or mac.  same thing with the iphone - apple has put effort into making sure it doesn't work with linux.  if wireless or openoffice don't work for you, you can always buy a system with linux preinstalled, thereby taking the installation errors out of the picture.  as for the dvd not ejecting, that's because you're using it.  stop the app accessing the dvd and then you can eject it.

---

### Post by Tamlynmac on 2009-01-16
> iNeeed
haha. Nope just stating the obvious or perhaps you are not ready for the truth in oppressive commie ubuntu land where criticism of the all mighty ubuntu is strictly prohibited. Unless of course you are criticizing capitalistic microsoft, then thats ok.

!!!EXCUSE ME!!!

If your not capable of understanding or implementing Ubuntu, how does that equate to your truth regarding those that have done so and are satisfied with the results.Try logging onto a "capitalistic Microsoft" Windows forum and complaining that Ubuntu is better. LOL

Many have already endeavored to enlighten you regarding your issues. The truth is you continue to want Ubuntu to be a Windows clone. I must agree with:

> Hospadar 	 		**Re: Can't eject dvd or unmount the volume (Venting)**
 You should just use another OS. It's not a crime to use windows or a different distro. Come back in 6 months or a year and see if your problems are fixed. Use the best tool for the job. 

Complaining or venting (in this manner) suggests you are envious of others who have accomplished this task. Calling people commie's or any other derogatory term may be an indicator of your own ineptitude. IMHO directing your frustration at others won't solve your problems. I'd suggest you stay with Windows and not concern yourself with any other OS options. 

Placating you or endeavoring to enhance you knowledge base seems a waste of time. Basically, you either want the OS to accomplish everything for you or have someone else resolve your issues. I seriously doubt you will enjoy the freedoms of OSS as your comfort level seems to reside in restrictive, set in stone processes.  How sad.

---

### Post by jrusso2 on 2009-01-17
> **timcredible said:**
> not sure how the netflix thing is linux's fault since netflix went out of it's way to purposely make sure that instant viewing doesn't work on linux or mac.  same thing with the iphone - apple has put effort into making sure it doesn't work with linux.  if wireless or openoffice don't work for you, you can always buy a system with linux preinstalled, thereby taking the installation errors out of the picture.  as for the dvd not ejecting, that's because you're using it.  stop the app accessing the dvd and then you can eject it.

There is a beta out for Netflix on OS X. Nothing for Linux yet.  Guess not enough users find it usable.

[http://blog.netflix.com/2008/10/opt-in-for-new-netflix-movie-player.html](http://blog.netflix.com/2008/10/opt-in-for-new-netflix-movie-player.html)

---

### Post by stalkingwolf on 2009-01-17
> I thought it was safe to assume
Never assume.  It makes an *** of U and Me 
> that some of the biggest products and devices in the world would be compatible.  
Only if THEY choose to make the drivers or info needed available.  If they
dont then you are free to not purchase their product.  If you do then it
is on you not the OS you are trying to use.
It is all about choices.

---

### Post by Rhubarb on 2009-01-17
It's possible to force an eject in those rare circumstances that very occasionally happens:

Open up a terminal, enter the following in, then you'll be prompted for your password:

```
sudo eject
```

---

### Post by solwic on 2009-01-17
> **Rhubarb said:**
> It's possible to force an eject in those rare circumstances that very occasionally happens:

Open up a terminal, enter the following in, then you'll be prompted for your password:

```
sudo eject
```

You don't even need "sudo".  I just typed "eject" into terminal and the tray popped right open.  :)

---

### Post by Rhubarb on 2009-01-17
> **jrock612 said:**
> You don't even need "sudo".  I just typed "eject" into terminal and the tray popped right open.  :)

In most cases true, but sometimes an optical drive refuses to eject for you even when you issue the "eject" command.  In this specific case you use sudo to force it open :)

---

### Post by solwic on 2009-01-17
> **Rhubarb said:**
> In most cases true, but sometimes an optical drive refuses to eject for you even when you issue the "eject" command.  In this specific case you use sudo to force it open :)

Oh okay.  

*Bows to superior knowledge*

I just dislike the sudo command, is all.  Try to avoid it if I can, so when I saw that "eject" worked by itself, thought I'd throw that out there.  :P

Cheers!

---

