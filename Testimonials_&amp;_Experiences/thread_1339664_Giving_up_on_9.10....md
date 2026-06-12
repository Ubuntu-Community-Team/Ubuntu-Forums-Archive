---
title: "Giving up on 9.10..."
date: 2009-11-27
forum: Testimonials &amp; Experiences
---

### Post by pablolie on 2009-11-27
I installed it this morning and been getting all my stuff to work.

However as I now browse around, I see that the fonts in Mozilla 3.5 are ugly, this looks jagged and is a shame - it looks like the kind of visuals we put up with back in the 640x480 VGA days on CRTs.

And of course checking through the forums there are 10 different theories as to what causes is, 5 different ways of messing around with system files... and seemingly no reliable way of making this look good.

On top of that, I have found 9.10 to be quite slower in every way, even though it was supposed to accelerate my Intel graphics powered system.

Finally, disabling services has become far less transparent - half the entries in Preferences->Startup Applications have no info with them, amking it impossible to establish whether they can be safely disabled.

But it is the look of Mozilla 3.5 with jagged ugly fronts that buries 9.10 in my environment.

---

### Post by mkvnmtr on 2009-11-27
Gee my fonts in Firefox are not ugly. I did nothing to set them but for the last few distros I have had the microsoft fonts installed. I seem to remember three or four upgrades the fonts were small or something and I installed the microsoft fonts. Ever since I have been pleased. 
Have you installed the extra package with the fonts in it?

---

### Post by pablolie on 2009-11-27
> **mkvnmtr said:**
> Gee my fonts in Firefox are not ugly. I did nothing to set them but for the last few distros I have had the microsoft fonts installed. I seem to remember three or four upgrades the fonts were small or something and I installed the microsoft fonts. Ever since I have been pleased. 
Have you installed the extra package with the fonts in it?

What extra package? The restricted extras? Yes, it is the first thing I install...

To me it looks like Firefox 3.5 is not doing any good smoothing on fonts that the web sites selct (such as this one, this screen looks ugly, I will attach a screenshot - but I just saw it does not really allow for enough reolutions after an upload, I will do a small area...)

As the small outtake now shows, the Ubuntu panel fonts look beautiful, everything under Firefox looks in need of some serious smoothing...

---

### Post by mkvnmtr on 2009-11-27
Those look very small. It has been a couple of years since I had that problem but I believe it was about the same. I have never had it again because I save my .mozilla folder in my home partition so my advise may be out of date or misremembered. I think I set the fonts in Firefox to be bigger. I may have even changed the type of font. I do not remember but I bet it was under tools.

---

### Post by pablolie on 2009-11-27
Those are standard settings, as they look great on the Asus eeepc 901 I am using right now, which *also* runs 9.10. This is very puzzling, and I wonder why the same Firefox version looks totally different and ugly on a different PC.

I mean, Firefox should not have any graphics driver dependent elements, or? This is so strange and frustrating, I want to have 9.10 running on all machines, but Firefox just looks unusably ugly on my main home music and browsing machine...

I wish there were guides to raze every Firefox installation file and reinstall it cleanly from scratch.

---

### Post by pablolie on 2009-11-28
Just for kicks and comparison I went all the way back to 8.04 LTS on this machine.

The fonts look razor sharp again. It is bizarre because it is exactly the same font configuration within Firefox.

Performance is also better in 8.04 than 9.10 on this machine, a Shuttle X27D with an Atom 330, an Intel 945 graphics chipset, and @GB of RAM.

---

### Post by craig10x on 2009-11-28
Interesting....and by the way, i have tried only 8.10 and 9.04 and while both worked perfectly, fonts and web page rendering looks much better to me in 9.04 then 8.10...

Hmmm...wonder if it could be that the 04's work better then the 10's (lol) ;)

Maybe i should stick only to the 0.4 versions of Ubuntu......he he he :biggrin:

---

### Post by Captain_tux on 2009-11-28
> **craig10x said:**
> Interesting....and by the way, i have tried only 8.10 and 9.04 and while both worked perfectly, fonts and web page rendering looks much better to me in 9.04 then 8.10...

Hmmm...wonder if it could be that the 04's work better then the 10's (lol) ;)

Maybe i should stick only to the 0.4 versions of Ubuntu......he he he :biggrin:

I've never used a .10 version of Ubuntu. This debate comes up with every release... seems to me that the .10 releases are the release candidates for the following year's .04 release. 

Just my opinion - this comment comes with no guarantees whatsoever!

:)

---

### Post by pataphysicianu on 2009-11-28
Do you have a file called .fonts.conf in your home directory? I know sometimes this is created if you install KDE-desktop or Kubuntu, it's not necessary and it's only effect will be to screw up the fonts in Firefox only, to look exactly as you say. If you have this file just delete it and restart and your fonts should be good again.

The reason I suspect this is your problem, is your font problem seems to be in firefox only, and the appearance of jagged fonts.

---

### Post by craig10x on 2009-11-28
> **Captain_tux said:**
> I've never used a .10 version of Ubuntu. This debate comes up with every release... seems to me that the .10 releases are the release candidates for the following year's .04 release. 

Just my opinion - this comment comes with no guarantees whatsoever!

:)

you know.... interesting observation... you may be on to something here ;)

---

### Post by NCLI on 2009-11-28
> **Captain_tux said:**
> I've never used a .10 version of Ubuntu. This debate comes up with every release... seems to me that the .10 releases are the release candidates for the following year's .04 release. 

Just my opinion - this comment comes with no guarantees whatsoever!

:)

[You might actually have a point]("http://spreadsheets.google.com/pub?key=t0XWfWgqJpYxCGAZ1G8U-og&output=html").

---

### Post by ElSlunko on 2009-11-28
Fixing the .font.conf file worked for me. I'm on KDE now so that file looks different for me but I'll do some digging around and find the combonation of settings that worked for me.

---

### Post by pablolie on 2009-11-28
> **pataphysicianu said:**
> Do you have a file called .fonts.conf in your home directory? I know sometimes this is created if you install KDE-desktop or Kubuntu, it's not necessary and it's only effect will be to screw up the fonts in Firefox only, to look exactly as you say. If you have this file just delete it and restart and your fonts should be good again.

The reason I suspect this is your problem, is your font problem seems to be in firefox only, and the appearance of jagged fonts.

Thanks for the message, I already went back to a former release, so unfortunately I can not try it out.

Guess the main reason I actually tried was the fact that (.10 is supposed to accelerate Intel graphics with UXA support, which I assumed would speed up my "green system" (Shuttle X27D), alas the system seemed to be more sluggish in pretty much every thing it did. 

In a few months, if no one else has taken it on, I shall try to put together a tutorial on how to fix and optimize font rendering for Ubuntu in Firefox.

---

### Post by DeusExM1 on 2009-11-28
Before you give up on Karmic just because of firefox i suggest you try the latest OPERA browser. Its faster than firefox and has a much nicer interface. I was experiencing many problems with FF, and im very happy i tried Opera. 

Give it a shot... You will be pleasantly surprised.

---

### Post by solwic on 2009-11-28
> **DeusExM1 said:**
> Before you give up on Karmic just because of firefox i suggest you try the latest OPERA browser. Its faster than firefox and has a much nicer interface. I was experiencing many problems with FF, and im very happy i tried Opera. 

Give it a shot... You will be pleasantly surprised.

Or Chromium.  You can get it in Ubuntu Tweak, under the third party apps.  It's super-fast.

---

### Post by ElSlunko on 2009-11-28
Here's the code I used! Though I see it's too late :

In ~/.fonts.conf

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

---

### Post by Zoot7 on 2009-11-28
I've heard that the releases between the LTS's are basically testing releases for the next LTS, and after having used Ubuntu since Feitsy, I'm sort of coming around to that way of thinking.

---

### Post by pablolie on 2009-11-28
> **Zoot7 said:**
> I've heard that the releases between the LTS's are basically testing releases for the next LTS, and after having used Ubuntu since Feitsy, I'm sort of coming around to that way of thinking.

Funny you mention that. I am running 9.10 on a few "secondary machines" and it performs good duty there. But the home server that does the heavy everyday lifting is now back to 8.04LTS. And I must say it works beautifully (I am typing this in from it, with super-crisp fonts in Mozilla FF 3.0.15 as per the latest 8.04 official update. And this machine is staying there until 10.04LTS comes around and has a reputation for being stable. 

THis is doing everything it is supposed to be doing really well. Long live LTS. Once 10.04 comes around all my systems are staying there for a while when and if I establish it is working well on all of them (which based on my 8.04 experience I fully expect).

---

### Post by Glucklich on 2009-11-28
> **NCLI said:**
> [You might actually have a point]("http://spreadsheets.google.com/pub?key=t0XWfWgqJpYxCGAZ1G8U-og&output=html").

Very interesting statistics. Where did you got the data? Compiled yourself by user experiences on the forums? Can't be... since few people stop by and let know they made a successful install. Those are the ones that stick around and help other people... or, at least, soon to be.

---

### Post by SeePU on 2009-11-29
I would give up on 9.10, too.  Shoddy release via an overrated distro.

---

### Post by Tamlynmac on 2009-11-29
[> ]("http://ubuntuforums.org/member.php?u=717316")[Captain_tux]("http://ubuntuforums.org/member.php?u=717316")
I've never used a .10 version of Ubuntu. This debate comes up with every release... 

+1
Agreed. Another recurring discussion.

---

### Post by pablolie on 2009-11-30
It runs ok on my other machines. But it is odd it does not run well on the one that, according to product literature, it was truly supposed to provide major benefits on. The Intel graphics didn't seem to be snappier at all - quite the contrary, 9.10 seemed to run noticeably slower on an Intel based system (Shuttle X27D with Atom 330 CPU and 945GC graphics) compared to 8.04 and 9.04. I am now running 8.04 LTS again on this machine, which as I noted before acts as my media server and is always on and I need to be reliable. Plus I use it for browsing the web too. That way I don't have to turn on the high powered desktop behemoth other than for heavyweight work duty (and it only runs Win7 these days, when I have to turn it on that is what I ultimately need). 

But yes, I have to admit I was looking forward to 9.10 on this machine and it was not a great experience for the 2 day trial period. Squeezeboxserver suddenly didn't see the NTFS music drive, performance was not snappy, and graphics were not smoother despite the press release claiming how much better UXA support was going to be.

I will wait for 10.04 and give it a few months I think.

---

### Post by SunnyRabbiera on 2009-11-30
Your fonts look fine to me, but then again I never had issues reading fonts in linux.

---

### Post by pablolie on 2009-11-30
> **SunnyRabbiera said:**
> Your fonts look fine to me, but then again I never had issues reading fonts in linux.

See there is a marked difference in the smoothing of the fonts - this is with Ubuntu 8.04 re-installed. The difference is marked, and the most I can say is that I *enjoy* reading a screen when it looks like this, and I did *not* like reading on the screen with whatever was happening to my computer (I know it is not a generic problem because I have other computers running 9.10) as per the earlier messages in this thread.

---

### Post by NCLI on 2009-12-04
> **Glucklich said:**
> Very interesting statistics. Where did you got the data? **Compiled yourself by user experiences on the forums?** Can't be... since few people stop by and let know they made a successful install. Those are the ones that stick around and help other people... or, at least, soon to be.

Yep. That's the longest running, consistent Ubuntu stability poll I know of. If you have a better source, I'd be happy to convert everything. I do think that, even though this is a support forum, it does hold some weight.

---

