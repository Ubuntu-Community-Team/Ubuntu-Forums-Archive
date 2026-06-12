---
title: "i want to come back to linux .. but ...... (long-ish post)"
date: 2009-01-24
forum: The Cafe
---

### Post by jasonwatkins on 2009-01-24
.. i just can't put my finger on why i can't commit all the way to come back.

(apologies for the length of the post and the rambling nature .. not quite sure what i'm trying to get to but i hope i'll get there by the end!)

i originally went with ubuntu a couple of years ago, and i thought it was fine.  then i moved to linux mint and i actually did settle on that for about a year as my sole OS.

but then for no real reason, i wanted to go back to XP so I did.  Then went to Vista, then back to XP ..

(you can see a pattern forming here :))

in the last 6 months i've tried to go back to linux - i've tried kubuntu, mandriva, ubuntu and mint all over again and because i've had a few issues - mainly with my nvidia 7300LE card and soundcard - in the initial setup i've lost patience and reformatted back to windows.

now this could well be a problem with *me* rather than my OS, but there are benefits for me if i do come back to linux.

i can set up a working informix development environment for one - that would be quite important in one respect since I used to be a full time informix programmer until I had to stop work due to medical reasons.

i went through this a few days ago - i tried opensuse and couldn't get the graphics card working within the first 10 minutes so i dumped it.  i did actually have a copy of an xorg.conf file stored somewhere that worked with mandriva, so i thought "aha! i'll try mandriva again".  downloaded and installed that and got the nvidia card sorted with no problem - got soundcard working as well.

installed "Flat Out 2" with wine and it ended up crashing the whole thing, so rather than figure it out, i reformatted :)

i think, now i've got to the other end of this post, that if this was 5 years ago i'd probably have perservered and ploughed my way through any problems because i probably still had my I.T. and programming head on, but I wonder maybe now that since i've been out of I.T. so long due to health reasons, i'm becoming more of a "regular" user and expect a distro to just install and work straight away ?

i appreciate there isn't really a question or anything there but i just had to vent my spleen so thanks for reading if you're made it this far without falling asleep :D

(any suggestions distro-wise though would be most welcome .... ;))

---

### Post by diablo75 on 2009-01-24
If I were you I'd make friends with VirtualBox so you can test these different OS's out in a VM instead of reformatting your hard drive and reinstalling 20 times a day.

---

### Post by Cammy on 2009-01-24
As far as your 6300LE goes, that's pretty close to the card I use.  For me, the best way to get that working was to download the [latest driver]("http://www.nvidia.com/object/linux_display_ia32_180.22.html") straight from nvidia, which have to be installed manually.

The hassle is that I have to re-install it after kernel updates, and you have to download the latest linux headers before doing that.  But I've gotten that down to a quick few minutes now.

Maybe others can help with your other issues.  Don't give up!

---

### Post by detroit/zero on 2009-01-24
Not that it's any of my business, but you'll forgive me if I ask:

What kind of health issues keep someone from programming or working in IT?

I could see if you got your hand(s) chopped off, or lost one or both eyes in a bizarre fireworks accident... But beyond that, it's not like being programmer or IT guy is like being a carpenter or a roofer or something where your livelihood depends on your physical abilities.

Again, please forgive my ignorance if you did suffer one of the above-mentioned fates.

> **jasonwatkins said:**
> i originally went with ubuntu a couple of years ago, and i thought it was fine. then i moved to linux mint and i actually did settle on that for about a year as my sole OS.

but then for no real reason, i wanted to go back to XP so I did.  Then went to Vista, then back to XP ..

(you can see a pattern forming here :))

I see a pattern: It's called ADHD :)

Maybe I just answered my own question?

---

### Post by jasonwatkins on 2009-01-24
> **diablo75 said:**
> If I were you I'd make friends with VirtualBox so you can test these different OS's out in a VM instead of reformatting your hard drive and reinstalling 20 times a day.

see you'd think that normal people would do this :D

especially since i bought a 400gb hard drive over christmas .. and i've already re-formatted it half a dozen times this year.

i think my reasoning behind doing that is probably thinking that if i've got a clean install and linux there in front of me, i won't be tempted to go back to windows ..

i've tried many distros in VirtualBox but me being me, i've tried it for 5 minutes and thought "hey! that looks *great!*" and charged off to the re-format ...

i think it needs to look a bit spiffy though - i seem to have it in my head that I want a KDE distro (hence kubuntu ..) but i've never really looked into re-skinning a linux distro over and above the default "oxygen" theme.

i do like my shiny black themes you know ;)

*EDIT*

> **detroit/zero said:**
> What kind of health issues keep someone from programming or working in IT?

Well I have the condition known as "obstructive sleep aponea".  In a nutshell, it leaves you very tired and sluggish throughout the day, with all the side effects that entails.

Now you may be wondering at this point why that prevents me working in I.T., and it's more to do with the perception of the condition from other people rather than me.

If you're an I.T. manager and you look across your office to see me sitting at my desk looking like i'm about to fall asleep at any minute, you're not going to be best impressed and that's the main hurdle i initially had when I was looking to get back in to the industry.

If I ever got an interview, i'd tell the prospective employer about the medical condition and the job magically disappeared at that point :)

Everything else kind of snowballed really - the longer I was out of I.T., the more i suffered from the lack of "current" experience, which I couldn't get without a "current" job, and I couldn't get a "current" job without "current" experience - and so on and so on ...

and unfortunately i'm not one of these super genius kids (i'm 38 ;)) who can read a java or C++ book and pick it up in half an hour, i ideally need to go with what I know and that's informix.

And it doesn't help that the informix market pretty much died many years ago either.

---

### Post by sydbat on 2009-01-24
> **jasonwatkins said:**
> Well I have the condition known as "obstructive sleep aponea".  In a nutshell, it leaves you very tired and sluggish throughout the day, with all the side effects that entails.

Now you may be wondering at this point why that prevents me working in I.T., and it's more to do with the perception of the condition from other people rather than me.

If you're an I.T. manager and you look across your office to see me sitting at my desk looking like i'm about to fall asleep at any minute, you're not going to be best impressed and that's the main hurdle i initially had when I was looking to get back in to the industry.

If I ever got an interview, i'd tell the prospective employer about the medical condition and the job magically disappeared at that point :)

Everything else kind of snowballed really - the longer I was out of I.T., the more i suffered from the lack of "current" experience, which I couldn't get without a "current" job, and I couldn't get a "current" job without "current" experience - and so on and so on ...

and unfortunately i'm not one of these super genius kids (i'm 38 ;)) who can read a java or C++ book and pick it up in half an hour, i ideally need to go with what I know and that's informix.

And it doesn't help that the informix market pretty much died many years ago either.I can relate...to an extent (I'm 42). I have a bad back (if you want the whole story, the 400000 page novel will be out soon :p) and went back to school (a decade ago) as an adult to get my IT degree. Job interviews go south when I tell them about my back (they always want to know why I went back to school), even though it has nothing to do with the job I am interviewing for.

More to the point, I found that the meds I was on for my back injury (2 ruptured discs...ouch) made me...loopy. They interrupted my concentration and exacerbated my ADHD (fully diagnosed!). This caused me to do very similar things to what you are doing now. It had nothing to do with being out of the IT loop.

So, my question (that you do not have to answer publicly) is – are you taking any meds that may be causing this type of unsettled reaction? If so, talk with your doctor about changing to another type that has less impact on your psyche.

---

### Post by swoll1980 on 2009-01-24
I found my self in the same cycle of Windows, Linux, Windows, Linux as I had some issues that were really anoying, and yet were extreamly simple to fix once I found out the problem. One of the most nagging issues I had was with FF pauseing for like 3 seconds before it took me to a web page. after several months of switching back and forth I learned that the problem was caused by network manager adding my computers ip address to my dns servers list. All I had to do to fix it was switch the default setting of roaming to dhcp. Little things like this can iritate the crap out of some one. I hate Windows, but do to a resently devolped addiction to world of warcraft I have to leave it installed, But ubuntu remains installed on my laptop and has been for 2 years

---

### Post by jasonwatkins on 2009-01-24
> **sydbat said:**
> are you taking any meds that may be causing this type of unsettled reaction? If so, talk with your doctor about changing to another type that has less impact on your psyche.

the problem with sleep aponea is that there are no meds you take for it - it's managed with an oxygen mask while you sleep, so the related side effects during the day are really yours to deal with.

but then the oxygen mask doesn't work on everyone - it doesn't work with me, so i tend to just live with the tiredness as the moment which is *always* fun :D

---

### Post by Moop on 2009-01-24
Take a look at Ubuntu Ultimate edition if you like shiny black themes. It comes preloaded with everything including a bunch of nice themes. 

[http://ultimateedition.info/ultimate-edition-20/](http://ultimateedition.info/ultimate-edition-20/)

---

### Post by jasonwatkins on 2009-01-24
ooohhh that looks very good .. especially the gamers edition ..

*rushes off to re-format* ..:D

well .. i'll have a closer look first of course ..

thanks for that

---

### Post by jasonwatkins on 2009-01-25
ok .. well .. i'm back :)

after 3 re-formats in the past 24 hours (seriously ..) i find myself sitting here with kubuntu again.

i tried ubuntu ultimate and thought it was good but i wasn't entirely sold i suppose, so i went to kubuntu.

actually initially installed the 1.80 nvidia drivers from the website and the boot-up just hung for some reason.  reformatted and used the 177 drivers offered and everything seems fine.

even now i'm getting itchy feet for windows again :)

i will resist though because i know being back on linux will ultimately do me a favour and if i can use it for over a year a while back, i can't see why i can't use it like that again.

---

### Post by Eisenwinter on 2009-01-25
why do you force yourself to use Linux if you don't really want to?

there's no shame in using Windows.

forcing yourself to use Linux will only hurt you, you'll find yourself frustrated over and over again, and keep blaming Linux. Eventually you'll develop a real hatred for it.

---

### Post by jasonwatkins on 2009-01-25
i don't think i'm necessarily forcing myself to use it .. i kind of do want to come back to it, mainly because I want to start using informix again and the only way i can do that really properly is on linux.

as i said, i used mint for well over a year and i was perfectly happy with it and had no real desire to go back to windows.

i'll give it a few days either way and see how i go .. if i'm still not entirely convinced i'll just go back to windows (again :))

---

### Post by nick09 on 2009-01-25
You could do a dual-boot. That way, instead of reformatting time over time you can select either one. For the ease of use install Windows first as Windows can mess up the grub boot process if installed last.

---

### Post by thraxy on 2009-01-25
Well, if you want everything working out of the box and don't really feel like adding stuff on, I think I would suggest giving Sabayon Linux a spin. Personally I like Ubuntu and Linux Mint better, but you should see how it works out for you :)

---

### Post by jasonwatkins on 2009-01-25
> **nick09 said:**
> You could do a dual-boot. That way, instead of reformatting time over time you can select either one. For the ease of use install Windows first as Windows can mess up the grub boot process if installed last.

i dual booted for a while when I was using Mint, but then i'm incredibly pedantic in that i want it all or nothing .. even though i'll never use the hard drive space, i don't want it taken up with windows (it's me, don't ask :))

> **thraxy said:**
> Well, if you want everything working out of the box and don't really feel like adding stuff on, I think I would suggest giving Sabayon Linux a spin. Personally I like Ubuntu and Linux Mint better, but you should see how it works out for you :)

I like the look of Sabayon actually - wasn't aware of that before.

I might not charge off for another reformat yet though since i've been fiddling all day with this and i just want to watch some tv :)

anyway, i think another part of the reason is that i think i need to get my brain working again - when i started out in I.T. i could knock up a shell script to do pretty much anything inside half an hour!

so i think if i'm on linux, i'll have more reason to actually start thinking about stuff again, and if i can get informix re-installed again i can actually start properly programming again and actually convince myself that i actually did work in I.T. and it wasn't all just a dream :)

---

