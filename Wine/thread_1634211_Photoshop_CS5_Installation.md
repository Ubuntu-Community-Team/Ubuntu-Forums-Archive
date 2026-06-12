---
title: "Photoshop CS5 Installation"
date: 2010-11-30
forum: Wine
---

### Post by ephexeve on 2010-11-30
I downloaded Photoshop CS5 .iso file (Disk 1 and Disk 2)  for Windows 7. But I would like to install it in my Ubuntu. 
I tried following this steps here: [http://www.junauza.com/2010/02/how-to-install-adobe-photoshop-on.html](http://www.junauza.com/2010/02/how-to-install-adobe-photoshop-on.html)

It totally didn't work. It worked till the part: 

*"Extract the zip file and copy atmlib.dll to c:/windows/system32. To do  this, go to Applications menu -->Wine -->Browse C:\ Drive, then  navigate to windows -->system32 and paste atmlib.dll there. After  that go to Applications menu --> Wine --> Configure Wine. Inside  the Libraries tab, add atmlib.dll and click on "Apply.""* 

After that, nothing happened, so I haven't managed to install it. 
I tried then, installing Magic Iso and Deamon tools to wine, then installing Photoshop from there, but didn't work, Magic Iso and Deamon tools weren't able to make a CD driver.. 

Any help?

Thanks

---

### Post by SAJA4 on 2010-12-01
[B]I also need to install Photoshop 
Anyone Help !![/B]

---

### Post by lykeion on 2010-12-01
First off, the web page you refer to describes installing Photoshop CS4 not CS5. 

Secondly, you should go to the homepage of wine (WineHQ) for info on running Windows applications in wine, not blindly trust an arbitrary web page from a google search. 
Here's the WineHQ page describing running CS5 with wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)  

> **ephexeve said:**
> I downloaded Photoshop CS5 .iso file (Disk 1 and Disk 2)  for Windows 7.
This sounds like an illegal download to me, am I wrong? 
If not this is against this forum's code of conduct: "Material that suggests illegal activity or contains illegal content is [...] forbidden." 

Finally and most importantly, why don't you try GIMP instead, it's free, open-source and it's written to be run in Ubuntu and other Linux distributions.

---

### Post by mastablasta on 2010-12-01
> **lykeion said:**
>  
Finally and most importantly, why don't you try GIMP instead, it's free, open-source and it's written to be run in Ubuntu and other Linux distributions.
 
perhaps they need PS autocompletition option. Check the features of CS5 and compare them with GIMP to find that a lot are not there in GIMP.
 
Still for low/medium level editing (lets say usual tasks) i would also suggest GIMP. i use it on all (even windows computers.

---

### Post by ephexeve on 2010-12-01
It's ilegal, and to be honest. I have to use it for school work. I really dont care about PS, it's just something we have to do it. So I wouldn't pay 200 euros for using it once. I haven't read the 'information' about the forum, so I'm sorry if I did something wrong. 
Thank you for the link anyway.
Thanks

---

### Post by mastablasta on 2010-12-02
better use GIMP instead then. it's free and i am sure you will be able to do in it what you can do in Photoshop.

---

### Post by alh on 2010-12-02
[QUOTE=ephexeve;10181065]I downloaded Photoshop CS5 .iso file (Disk 1 and Disk 2)  for Windows 7. But I would like to install it in my Ubuntu. 
I tried following this steps here: [http://www.junauza.com/2010/02/how-to-install-adobe-photoshop-on.html](http://www.junauza.com/2010/02/how-to-install-adobe-photoshop-on.html)

The installer won't work for cs5; starts, looks like it's working, but goes nowhere. 
This is the only way to do it.

This shows my test copy running on Mint10. [http://members.iinet.net.au/~alhumphrey/pshop.png]("http://members.iinet.net.au/%7Ealhumphrey/pshop.png")

Here is the link explaining how to set up up. [http://maketecheasier.com/install-photoshop-cs5-in-ubuntu-maverick/2010/11/02](http://maketecheasier.com/install-photoshop-cs5-in-ubuntu-maverick/2010/11/02)

I always use GIMP cause it does all I want. This was just an experiment just to see if I could. 

PS Nothing illegal about this; I used a 30 day test copy downloaded from Adobe which is identical except for registration. This will expire in 30 days.
Al

---

### Post by m417 on 2010-12-02
carrier sunrises have provided service for website,hardware&software.
[http://http://ubuntuforums.org/newreply.php?carrier]("http://http://ubuntuforums.org/newreply.php?carrier")

---

### Post by srikanth.gundaz on 2010-12-02
Use GIMP instead of photoshop. You cannot install photoshop in ubuntu even using WINE. Go with GIMP :)

---

### Post by alh on 2010-12-02
> **srikanth.gundaz said:**
> Use GIMP instead of photoshop. You cannot install photoshop in ubuntu even using WINE. Go with GIMP :)
Did you not read the above post of mine??

---

### Post by srikanth.gundaz on 2010-12-02
> **alh said:**
> Did you not read the above post of mine??

Oh!! sorry. I didn't read. Well, i know one software named playonlinux. Use that for some days. They are trying to run photoshop CS5 in ubuntu :)  They will come up with that very soon :) 
Check here.
> [http://srikanthkabadi.blogspot.com/2010/11/play-huge-games-in-linux-platform.html](http://srikanthkabadi.blogspot.com/2010/11/play-huge-games-in-linux-platform.html).

---

### Post by lykeion on 2010-12-02
I still think that it's preferrable to use GIMP instead of of running Photoshop with wine (even though it's possible):
1) It's hassle-free and program works 100% as it should.
2) Most features of PS is available in GIMP as well (it can even open and save .psd), so for basic image editing they are interchangeable.
This thread discusses PS vs GIMP: [http://ubuntuforums.org/showthread.php?t=1634800](http://ubuntuforums.org/showthread.php?t=1634800)

@ephexeve
For me it's rather strange that your school forces you to pay for some expensive software to do school work. I would talk to them and ask if you could use GIMP instead.

EDIT
Thought I would mention that it's possible to install the latest 2.7 version of GIMP via PPA.
That way you can change to single-window mode (something PS users are more accustomed to):

---

### Post by ephexeve on 2010-12-02
Thanks guys, I will try in a minute then I will post the results.
Btw, the GIMP it's pretty good too. But I have a test about PS at school. So I literaly have to use the PS, that's one more reason I had do download it. 
Thanks

---

### Post by ephexeve on 2010-12-02
@[lykeion]("http://ubuntuforums.org/member.php?u=102981"),

Sorry, just read your post now. Yes, they actually force it, this is Holland my friend, welcome.

---

### Post by mciverza on 2010-12-03
> **lykeion said:**
> 

This sounds like an illegal download to me, am I wrong? 
If not this is against this forum's code of conduct: "Material that suggests illegal activity or contains illegal content is [...] forbidden." 


Adobe lets one download trial version software, so that isn't neccessarily an illegal download, but thanks for the reminder regarding forum policy.

I agree also with your recommendation of GIMP.

---

### Post by SAJA4 on 2010-12-04
> **lykeion said:**
> First off, the web page you refer to describes installing Photoshop CS4 not CS5. 

Secondly, you should go to the homepage of wine (WineHQ) for info on running Windows applications in wine, not blindly trust an arbitrary web page from a google search. 
Here's the WineHQ page describing running CS5 with wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)  



**I try to install ps like your way .. but I couldn't understand these line **

```
$ rm -rf ~/.wine 
 $ winetricks gdiplus ie6 msxml3 vcrun2005sp1 vcrun2008 

```**help please**

---

### Post by SAJA4 on 2010-12-07
[FONT=Arial Black][SIZE=4]Why no one answer me !! :cry:[/SIZE][/FONT]

---

### Post by MB0SS on 2010-12-17
hi
if any one have any problem to run photoshop cs5 on ubuntu
then watch this video simple one click install photoshop cs5 on ubuntu under wine
without any wine tricks or any updates 


[http://www.youtube.com/watch?v=1ZnCcJuQLwY](http://www.youtube.com/watch?v=1ZnCcJuQLwY)

MB0SS

---

### Post by MB0SS on 2010-12-17
hi
[SIZE="7"]if any one have any problem to run photoshop cs5 on ubuntu
then watch this video simple one click install photoshop cs5 on ubuntu under wine
without any wine tricks or any updates 


[http://www.youtube.com/watch?v=1ZnCcJuQLwY](http://www.youtube.com/watch?v=1ZnCcJuQLwY)

MB0SS[/SIZE] :popcorn:

---

### Post by MB0SS on 2010-12-17
[QUOTE=MB0SS;10250294]hi
if any one have any problem to run photoshop cs5 on ubuntu
then watch this video simple one click install photoshop cs5 on ubuntu under wine
without any wine tricks or any updates 


[http://www.youtube.com/watch?v=1ZnCcJuQLwY](http://www.youtube.com/watch?v=1ZnCcJuQLwY)

MB0SS

---

### Post by SAJA4 on 2010-12-18
> **MB0SS said:**
> hi
if any one have any problem to run photoshop cs5 on ubuntu
then watch this video simple one click install photoshop cs5 on ubuntu under wine
without any wine tricks or any updates 


[http://www.youtube.com/watch?v=1ZnCcJuQLwY](http://www.youtube.com/watch?v=1ZnCcJuQLwY)

MB0SS
[SIZE=4]
[/SIZE][FONT=Arial Black][SIZE=4][COLOR=Black][B]Thanks a lot 
it worked with me . finally I got Photoshop Cs5 on ubunto now 
I'm so happy\\:D/[/B][/COLOR][/SIZE][/FONT]

---

### Post by ephexeve on 2011-02-01
I will try that, thanks

---

### Post by _outlawed_ on 2011-02-01
Photoshop 7 works amazingly good in both stable and development builds of Wine. It's what I use, as CS series is resource hog.

---

