---
title: "Harware Microphone Question: USB vs. XLR Connection"
date: 2009-02-21
forum: Ubuntu Studio
---

### Post by kasperbs on 2009-02-21
Right I'm looking for a microphone for recording interviews both over the phone but also when in the field. So I was happy when I saw that the Samson CO3(U) had the Switchable Supercardioid, Omni and Figure-8 pickup patterns.

This microphone comes in two versions [**_CO3U_**]("http://www.samsontech.com/products/productpage.cfm?prodID=1878") which is a USB version and [**_CO3_**]("http://www.samsontech.com/products/productpage.cfm?prodID=1663") which has a XLR connection.

So as I was hoping to get my hands on a pretty versatile microphone that would work both on my PC and with a marrantz recorder (XLR input) and maybe even with a stereo jack input (via a converter). I was thinking if there would be a difference between the CO3U and the "CO3 [**_with this added"_**]("http://www.htfr.com/more-info/MR244471") USB MICROPHONE CABLE - XLR (FEMALE) TO USB?

I'm thinking that the C03 might be the most versatile of the two mics or is there something I should be aware of, that I'm missing?

---

### Post by Phil Urich on 2009-02-21
Well, the potential pitfalls lie in things we don't really know; how universal *are* these, after all? The cable claims to require no drivers, which hopefully means it's entirely USB-audio spec and will work without issue.  The USB version of the actual mic seems to imply much the same thing.  But of course in my experience these things don't always go so smoothly!

The other thing though is that I'd be a bit worried about how good of a sound "card" (since that's essentially what's in it; any USB audio devices have to do their own sound processing in these cases) is in the cable.  I'd be guessing not terribly great....but to be fair it might easily handle the task.

---

### Post by kasperbs on 2009-02-21
Thanks really appreciate your thoughts.

Do you think I would be better off getting one of [these]("http://pro-audio.musiciansfriend.com/product/Behringer-UCONTROL-UCA202-USBAudio-Interface?sku=702540") and then convert the XLR signal to analogue/instead of digital, and then from the USB soundcard into the PC? Or does that present the same issues as you have just described?

---

### Post by kasperbs on 2009-03-03
Ok, just got the things and there was one important pitfall I missed.

You have to know that a condenser microphone needs a phantom power supply. Apparently this means that you have to get a mixer or other device which have this.

Unfortunately I didn't know that, so my advice would be to buy the USB mic if you don't plan on buying a mixer,

---

### Post by ussndmac on 2009-03-03
It's not that difficult to provide phantom power to a condenser mic.

Most modern condenser mics will run with much lower voltage than the tradition 48 volts.

Google on powering a condenser mic and you'll no doubt find plenty of circuits to do same.

Of course, getting a mixer or other device is an option.

---

### Post by kayosiii on 2009-03-03
Ideally you would go for the XLR version + a descent quality Mic Preamp (either built into your soundcard or as a separate unit)...

The USB unit makes things considerably simpler in this regards... However you will be stuck with the preamp and AD converters that the microphone provides (which will probably be adequate but not as good as you could get)... The other limitations are that you will only be able to use it with a computer and a lot of music software (particularly on linux can only record from one soundcard at a time - making it unlikely you could later use it for a multi-mic recording setup).

The XLR option will be more flexible but more expensive.

---

### Post by kasperbs on 2009-03-04
Can you elaborate on what a Preamp is, I'm very new to sound recording as you can tell.

Can you give any examples of what you would regards as decent? And do they come with a phantom power supply?

---

### Post by thorgal on 2009-03-04
a preamp is a unit that will apply some amplification to your source signal. It is "pre" because you may apply further processing after this first stage. The preamp is supposed to just amplify the source signal level without distorsion. That's the principle of course because some preamp units will color the sound, depending on the technology (tube, transistor, hybrid).

Most soundcards have built-in preamps but if you are a purist, you may rely on a dedicated external unit that will preamplify faithfully the original sound signal. I personally own a RME QuadMic preamp (4 independent channels, all XLR compatible, each with phantom power). The unit is very neutral (or transparent) and quite accurate except when you push it to the max pre-amplification where it looses a bit of accuracy.

see here for example: [http://www.thomann.de/gb/prod_zoom_AR_162895.html?sid=dd24d27af9e11ec1ff49e76a75632cc5](http://www.thomann.de/gb/prod_zoom_AR_162895.html?sid=dd24d27af9e11ec1ff49e76a75632cc5)

look at the back of the unit: you plug your XLR condenser mic to a channel, and get the corresponding output at a so-called line-level. That's what the preamp is used for, converting the mic level to line level.

---

### Post by kasperbs on 2009-03-04
Thanks, it's probably a little too expensive for my needs. I hadn't planned on using much more than what I have already spent on the mic.

I have got one of [these usb soundcards]("http://pro-audio.musiciansfriend.com/product/Behringer-UCONTROL-UCA202-USBAudio-Interface?sku=702540") which is supposed to work well with linux. Can't I just go for a phantom power supply unit without preamp, or would the price be the same anyway?

Sorry this is turning into an audio education class. But is it true that if I had bought a 'Dynamic Mic' then I wouldn't have needed phantom power, and I could have used it directly with the usb soundcard I linked to above? If that's the case, I might be better of trying to see if I can return the condenser mic and get one of these [Shure SM58]("http://www.dv247.com/invt/13248/") instead? Or are they only suitable for live vocals and not really voice recording at home?

---

### Post by thorgal on 2009-03-04
you can find single channel preamps :)

yes, dynamic mics do not require phantom power but they are less precise than condenser mics. At the same time, they are less fragile, that's why they are much preferred on stage.

But again, you need to bring the mic level to line level, and that's what the preamp will do. I don't know if your soundcard can accept mic level and preamp it to line level internally, check your soundcard specs.

---

### Post by kasperbs on 2009-03-04
I guess the [USB UCA202]("http://pro-audio.musiciansfriend.com/product/Behringer-UCONTROL-UCA202-USBAudio-Interface?sku=702540") will act as my soundcard, but I don't know if it will do what you mean. I have looked at the [PDF Manual]("http://img3.musiciansfriend.com/dbase/pdf/man/m_702540.pdf"), and there seems to be some specification on page 18+19 but I don't know if it says anything about amplification or mic level, or if it would work with a dynamic mic. Would you mind having a look?

---

### Post by thorgal on 2009-03-04
that USB thingy's inputs take line level signals. So you'll need to bring your condenser mic's output from mic to line level, thus the need of a preamp.

---

### Post by kasperbs on 2009-03-04
And I guess the same would be true for a dynamic mic, thus needing an extra unit none the less?

Would [this]("http://www.solotechnic.co.uk/behringer-micropower-ps400-i28166.html") work as a preamp?

Just stumbled over [this usb preamp]("http://www.bhphotovideo.com/bnh/controller/home?O=productlist&sku=522285&Q=&is=REG&A=details"), which might be a better solution and woulnd't ake up as much space. What do you think?

---

### Post by thorgal on 2009-03-04
no, it's just a phantom power supply. The output you have on this device is a mic-through that you would redirect to a preamp unit.

Get a single channel preamp with built-in phantom power supply or if you have a second mic, a dual channel preamp. Your USB device has 2 inputs so you could plug 2 mics.

The advantage of getting such a preamp unit is that you may find out your USB device is not good enough in the long run, if you get more ambitious. A good quality preamp is on the other hand indispensable for acoustic recordings :)

look in there: [http://www.sweetwater.com/c663--Dual-Channel_Preamps](http://www.sweetwater.com/c663--Dual-Channel_Preamps) (dual chan)
[http://www.sweetwater.com/c662--Single-Channel_Preamps](http://www.sweetwater.com/c662--Single-Channel_Preamps) (single chan)

you have a wide variety and huge price difference ...

---

### Post by kasperbs on 2009-03-04
Thanks for all your feedback, and for taking the time to help me. I think I'm in a better position now to make an educated decision.

I do favour the flexibility of preamps and xlr mic's, which was why I bought the XLR in the first place.

---

### Post by kayosiii on 2009-03-04
A soundcard with XLR connections will generally have built in preamps.... As will your onboard soundcard (big difference in quality though)... 
You will need phantom power for condenser mics but not dynamics. 

If you are in a do-it-yourself frame of mind you can pick up cheap but fairly descent preamp kits from many electronics  places (Altronics or Jaycar in Australia - don't know the equivalents in your part of the world)...

---

### Post by kasperbs on 2009-03-04
So I have been looking into this and a few things confuses me. There seems to be different outputs on the preamps. Some have XLR outputs + 1/4" others have only 1/4" like the one you REM QuadMic you refered to earlier.

My USB soundcard has phono input and outputs, my onboard soundcard has 1/4" line in.

As far as I can see I have two options. Either get a preamp with 1/4" output an let it go directly in my onboard soundcard. Or get preamp with xlr out and get a XLRfe to Phono cable to go to my USB soundcard?

This seems to be the cheapest I can find, though it does seem a bit bulky. How would that fit in with my hardware?

---

### Post by thorgal on 2009-03-04
I would try to stick to balanced IOs. RCA IOs are usually unbalanced and more prone to noise. Depends on the cable length in between and the quality of the cable as well. Most XLRs and some 1/4" (aka TRS) jack connectors are balanced.

Have a look at [http://www.harmony-central.com/articles/tips/balanced_vs_unbalanced/](http://www.harmony-central.com/articles/tips/balanced_vs_unbalanced/)

---

### Post by kayosiii on 2009-03-05
Does your onboard have 1/4 in or 1/8 in sockets?

balanced vs unbalanced shouldn't matter if you keep your cable lengths short. (say less than a meter unless you are in a very effected area)...

The xlr to xlr option would be the more flexible. Usually though preamps have both a balanced and an unbalanced output (unbalanced usually 1/4 in).All the ones I have owned do anyways. It is not hard to build a short 1/4 in to RCA cable to go to the USB soundcard or a 1/4 in to 1/8 in to go to the onboard soundcard... (if you do the later make sure you disable the onboard soundcard's preamp)... 

If you want to go really cheap you could just go for an XLR to 1/4 in cable and a female 1/4 inch to 1/8 inch male cable and use the onboard soundcards preamp but I suspect that the volume level and the quality will be unsatisfactory.

---

### Post by thorgal on 2009-03-05
by the way, I have plenty of those 1/4" to RCA adapters, and I don't need them any longer. Where do you live ? I can sell them to you if you want, just PM me if you're interested. I live in DK, don't know if that's worth the shipping cost if you liove in North America or Asia. I also have a bunch of XLR to TRS adapters if you're interested.

---

### Post by kasperbs on 2009-03-05
Thanks thorgal, I'm actually Danish but study in the UK at the moment. I actually have a XLRfe to Phono which I might be able to use if I get a preamp with XLR out.

I was looking at [the Art Tube MP Original]("http://www.artproaudio.com/products.asp?type=79&cat=1&id=1") (The cheapest I could find with no bad reviews). It has both XLR and 1/4" and I could use that with my XLRfe to Phono.

Do you know anything about this Preamp?

---

### Post by thorgal on 2009-03-05
hey! do you read french ?
[http://preampli-lampes.art.audiofanzine.com/produits/avis/index,idproduit,538,mao,tube_mp.html](http://preampli-lampes.art.audiofanzine.com/produits/avis/index,idproduit,538,mao,tube_mp.html)

according to some reviewers, the lamp is not very good and the preamp unit died in a matter of weeks. Maybe it is good during the time it's working but the cheap part shows up quickly it seems :)

---

### Post by kasperbs on 2009-03-05
Most seem pretty positive though, and if I buy local I can just take it back and get it replaced.

Do you think I would be better off stepping up to the [Studio V3]("http://www.artproaudio.com/products.asp?id=58&cat=1&type=79")? Or are they mostly similar? I can't really tell the difference myself!

The other option in that price range is the [dual channel M-buddy]("http://www.bhphotovideo.com/bnh/controller/home?O=productlist&sku=189927&Q=&is=REG&A=details") although it hasn't got XLR output.

---

### Post by thorgal on 2009-03-05
the Studio V3 has even worse reviews ...

the M-Audio Buddy is not a tube preamp, so you will get something much more flat / cold. I don't know what you're after. As you  might have guessed by now, it's a jungle ;)

---

### Post by halon314 on 2009-04-30
Since you already have the XLR mic and just need a means of getting it to a computer - why not use an XLR to USB adapter that provides phantom power, like [THIS]("http://pro-audio.musiciansfriend.com/product/Blue-Icicle-XLR-to-USB-Mic-Converter?sku=330275")?

---

### Post by kayosiii on 2009-05-01
44,100, 16bit -- I would look for something 24bit if possible.... It makes your life a lot easier.

---

### Post by rdmike on 2009-05-02
Maybe way off base here but is something like [this]("http://cgi.ebay.com/MXL-D-R-K-DESKTOP-RECORDING-KIT-CONDENSER-MIC-PC_W0QQitemZ270303654419QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item3eef5a7213&_trksid=p3286.m20.l1116") what you're looking for? I had a similar set up a while back (Lambda).

---

