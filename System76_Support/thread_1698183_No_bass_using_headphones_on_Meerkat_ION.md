---
title: "No bass using headphones on Meerkat ION"
date: 2011-03-01
forum: System76 Support
---

### Post by Sig Nuka on 2011-03-01
I'm using a Meerkat ION NetTop with Ubuntu 10.10 (just purchased it about a month ago) and while I've been using a 2.1 speaker system without issue (the subwoofer works perfectly), for some reason I get no bass using my headphones. If I listen to the same song on my iPod I can hear the bass just fine so it's not a headphones issue, and neither Audacious nor the Gstreamer preview allows me to hear the missing bass. Sound Preferences doesn't fix it, and alsamixer through the terminal does nothing as well. What I find odd is that my speaker system can pick up the bass just fine while my headphones can't. Maybe the system detected the subwoofer initially thus screwing up the sound for my headphones? I really don't know what's going on nor what to do at this point. :(

---

### Post by EJJ on 2011-03-02
> **Sig Nuka said:**
> Maybe the system detected the subwoofer initially thus screwing up the sound for my headphones?


This could be a possibility. In my life as a musician I've always avoided the people who had a "Basement Studio" due to little things like this. What type of speakers do you have? Are your headphones plugged directly into the computer, or do you have a headphone output on the speakers that you're using? My desktop (Mac, not Ubuntu) has a simple 2.1 Logitech speaker system (which for most people is more than enough for good sound.....) and the speaker system itself has a headphone output...I don't usually use it so I can't chime in on the bass response in that...but it could be due to this.

Also, do you have any EQ settings on your iPod? Perhaps this might be misleading as to the sound of the actual mix as opposed to the iPod presets.



And congrats on your System76 purchase! I might get one of their desktops in the near future...if I don't upgrade from my Starling to a Pangolin or another laptop

---

### Post by isantop on 2011-03-02
Try disconnecting the Sub woofer, and then try playing through the satellites. That will help tell us if it's an EQ problem.

Also, it would be helpful to know what port your headphones are plugged into.

---

### Post by Sig Nuka on 2011-03-02
> **EJJ said:**
> What type of speakers do you have?
Cyber Acoustics CA-3000 2.1 speakers.

> Are your headphones plugged directly into the computer, or do you have a headphone output on the speakers that you're using? 
My speakers don't have headphone output, although they do have an output for the subwoofer. Plus I don't see a reason of ever connecting to the speakers rather than the computer itself.

> Also, do you have any EQ settings on your iPod? Perhaps this might be misleading as to the sound of the actual mix as opposed to the iPod presets.
I never use EQ settings anywhere, iPod or otherwise. I never see a reason for it.

> And congrats on your System76 purchase! I might get one of their desktops in the near future...if I don't upgrade from my Starling to a Pangolin or another laptop
This is actually the "family computer" I'm using. My own personal laptop's display died a few months ago (a six-year-old Dell Inspiron 8600), so this is a temporary computer I'm using until I can get a Bonobo Pro MAYBE this year. As an aspiring musician myself, I'm holding on music making until then. :D

> **isantop said:**
> Try disconnecting the Sub woofer, and then try playing through the satellites. That will help tell us if it's an EQ problem.
Thing is, the speakers aren't designed to be used without the subwoofer, as they get no bass without them (connecting them to a non-EQ'd iPod or a CD player doesn't change that). However, my headphones receive bass with EVERYTHING minus the Meerkat ION.

> Also, it would be helpful to know what port your headphones are plugged into.
Same port I connect my speakers to: the Meerkat ION's headphone port.

---

### Post by Sig Nuka on 2011-03-05
Bumpity bump bump bumpity bump bump look at Frosty go.

Bumpity bump bump bumpity bump bump over the hills of snow.

:V

Edit: Anyone? :(

---

### Post by isantop on 2011-03-07
Check that your audio profile in System > Preferences > Sound > Hardware Tab is set to stereo, and not 2.1, as this would cause the bass to be quiet or non-existent.

---

### Post by Sig Nuka on 2011-03-07
All I can see is Analog Stereo Duplex (which is what it's currently on), Analog Stereo Output, and a bunch of Digital Stereo choices that don't work. I'd take a screenshot if I could, but it's not allowing me to do it.

---

### Post by isantop on 2011-03-08
Is that the headphone port on the front or back of the machine?

---

### Post by Sig Nuka on 2011-03-08
> **isantop said:**
> Is that the headphone port on the front or back of the machine?
...There's a headphone port on the back of the machine? :lol: I'm gonna have to try it out.

Edit: Well, at least I now have free space in the front. :P

However, connecting my headphones to either port gets me the same baseless result, and connecting the speakers in the back AND the headphones in the front gets me the usual bass with my speakers and the usual bassless result in my headphones. It's kinda odd.

---

### Post by Flyers2391 on 2011-03-09
What is the type of headphones?  Is it possibly they are apple headphones and maybe the bass only works when the chip inside detects it is connected to another apple device?  

I don't think it's a conspiracy ... I've read that if manufacturers want headphones to work with iPods they need to pay apple a license fee.

---

### Post by Sig Nuka on 2011-03-09
> **Flyers2391 said:**
> Is it possibly they are apple headphones...?
Philips SHP2500. Sorry. :P

Also, my old (display-dead) laptop with a Windows XP / Ubuntu dual-boot never experienced this problem in either operating system (I could always hear the bass on that just fine - in fact I ended up rarely using the built-in speakers the laptop had). If you need more info on that, I installed Ubuntu 8.04 through Wubi on my Dell Inspiron 8600 about a month or two before Intrepid came out, and upgraded it through Lucid (which is when the display died). Thanks to hard drive issues, I never could install it normally. :(

---

### Post by isantop on 2011-03-10
Thanks for all that. Would it be possible to try a different set of headphones? Not satellite speakers, but headphones.

---

### Post by Sig Nuka on 2011-03-10
> **isantop said:**
> Thanks for all that. Would it be possible to try a different set of headphones? Not satellite speakers, but headphones.
I have a pair of Koss clipons that are pretty light on bass that I rarely use nowadays thanks to my other 'phones (although I do use them from time to time). Lemme check them out really quickly (I also have a PSP 3000 that I can use for this test alongside my iPod, although I'd have to change my test song).

Edit: Correction - Philips clipons. I had a pair of Koss clipons that failed on me a few years ago, and I've since gotten two different pairs of Philips clipons (these and a previous pair that also failed on me). I always forget that these aren't Koss though. :P

Anyway, just tried listening to the same song on a PSP (with the EQ off), an iPod (again with the EQ off) and the Meerkat ION through Nautilus's Gstreamer preview (which is what I've been doing the whole time). Even with the clipons' low bass output I can VERY easily hear the lack of bass on the Meerkat ION. In fact, I have a very old pair of generic headphones (generic in that they have no brand marking other than "Digital Stereo Headphones") that I don't use anymore thanks to the left speaker breaking off (though I can still put them on if I'm a bit careful, and they work perfectly otherwise). The pair is probably (though I'm only wildly guessing) older than iPods themselves, and I can still hear the bass perfectly fine with these connected to my iPod but no bass whatsoever when they're connected to the Meerkat ION.

---

### Post by isantop on 2011-03-11
I'm getting decent bass output from ours in the shop, through both satellites and headphones. Make sure the plug is completely inserted, as that may be causing it. If that doesn't help, then it could simply be a subjective issue. You can have a look at this thread for a system-wide equalizer you can try:

[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

---

### Post by Sig Nuka on 2011-03-11
> **isantop said:**
> You can have a look at this thread for a system-wide equalizer you can try:

[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)
Tried it, and it's not helping at all. :frown:

Isn't there another interface that might've had the sound properties changed that I could access? Like alsamixer but for PulseAudio (besides the default one I mean)?

I'm starting to think that computers hate me (I had numerous problems with my old Dell laptop since day 1 way back in December of '04). :frown:

---

### Post by isantop on 2011-03-14
I have one more thing I'd like you to try. Try playing your iPod from the speakers, without adjusting the settings. It could be that Apple (et al) are optimizing a hidden EQ for earbud headphones, and that's why you get decent sound from them.

---

### Post by Sig Nuka on 2011-03-14
> **isantop said:**
> I have one more thing I'd like you to try. Try playing your iPod from the speakers, without adjusting the settings. It could be that Apple (et al) are optimizing a hidden EQ for earbud headphones, and that's why you get decent sound from them.

Well see...

A: I don't use earbud headphones. Never liked them.

B: I tried my headphones (clipons and over-ear) with my PSP and the sound is just fine (I've got some songs loaded on the memory card). So it can't be an Apple issue since without anything Apple it still works fine.

C: I actually have a second user on this computer that I loaded up yesterday and I ended up listening to a song from there. I figured if it was an EQ issue it'd play fine since I'm pretty sure EQ settings don't carry to different users. It didn't play fine. Same problem (lack of bass). Now I'm worried.

I actually have a Lucid Lynx CD around - I'm gonna try and boot it up (somehow - I'm pretty sure I have to investigate how to do it) to see if it's a software or hardware issue.

I'll probably connect my speakers to my PSP as well to see how it fares. I shouldn't notice a difference, but you never know. Knowing my luck there'll probably be more bass or something. :roll:

Pre-post edit: Yeah, um, I can't notice a difference between the PSP and the Meerkat ION using my speakers. Maybe the subwoofer is just that good at hiding it? I dunno. :(

I'll try the Lucid CD tomorrow.

Edit: Um... how do you boot from the CD on these? Google searches brought up F12 (didn't work), Escape (didn't work), F8, F10, F11, and just letting the CD run automatically (obviously didn't work). Any help?

---

### Post by isantop on 2011-03-16
You can edit the boot order by entering the BIOS. The BIOS is is a little wonky; Delete in this case.

---

### Post by Sig Nuka on 2011-03-16
> **isantop said:**
> You can edit the boot order by entering the BIOS. The BIOS is is a little wonky; Delete in this case.
Ah, many thanks. (saw this response with my PSP)

Well, bad news: I still couldn't get any bass with my headphones, which is NOT a good sign. Not sure if there's a way to change the settings on the sound card itself, or if it's *gulp* a faulty sound card. Hopefully the former is possible, and if it is I'd like to know how. :frown:

This whole ordeal reminds me of my laptop and how when I first got it I found out that Windows Media Player 10 couldn't rip to mp3, and a year or two later the update to version 11 didn't fix it. Hopefully when I (maybe, possibly, eventually) get a Bonobo Pro from you guys I don't get yet another "day 1" flaw with it. I have such horrible luck I swear. :(

---

