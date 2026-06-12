---
title: "Soundblaster awe32 on ubuntu studio"
date: 2008-11-01
forum: Ubuntu Studio
---

### Post by Snowflake128 on 2008-11-01
Hiya!
  Could anyone give me step by step instructions for installing an awe32 on my ubuntu studio machine? It's an old ISA card but I don't think it is the PnP model which may make things easier?

  I went away from Linux for a long time and now I come back everything seems very different and I feel lost! :(

  Hope someone can help!

---

### Post by kostkon on 2008-11-01
> **Snowflake128 said:**
> Hiya!
  Could anyone give me step by step instructions for installing an awe32 on my ubuntu studio machine? It's an old ISA card but I don't think it is the PnP model which may make things easier?

  I went away from Linux for a long time and now I come back everything seems very different and I feel lost! :(

  Hope someone can help!
Old ISA cards are not auto-detected any more, so you will have to load the driver for your card manually. You will have to follow the instructions that are [on this *Ubuntu Wiki* page]("https://help.ubuntu.com/community/HowToSetupSoundCards").

If you have any problems or questions about this, don't hesitate to ask here.

P.S.: I assume the driver that will work for you is the *snd-sb16* or the *snd-sbawe* one.

---

### Post by Snowflake128 on 2008-11-01
Thanks so much Kostkon! Thats awesome! :)

I think they changed the name of alsa_local to alsa_base or something like that?? I hope so, as I stuck the entry in alsa_base instead!

sudo modprobe snd-sbawe 

...doesn't cause any complaints.

and I've added the entries to etc/modules and etc/modprobe.d/alsa_base

However asoundconf list, only shows my 2496 card and I assume it should list sbawe too. :( 

I may have the settings for dma and stuff wrong tho, I'm about to go look for details on my card.

I feel closer anyway and those instructions are really straightforward, at least for me.

One thing that is annoying me is not being able to see any boot messages! Is there anyway I can see this so I know what is happening during boot?

Thankyou!

---

### Post by kostkon on 2008-11-02
> **Snowflake128 said:**
> Thanks so much Kostkon! Thats awesome! :)

I think they changed the name of alsa_local to alsa_base or something like that?? I hope so, as I stuck the entry in alsa_base instead!

sudo modprobe snd-sbawe 

...doesn't cause any complaints.

and I've added the entries to etc/modules and etc/modprobe.d/alsa_base

However asoundconf list, only shows my 2496 card and I assume it should list sbawe too. :( 

I may have the settings for dma and stuff wrong tho, I'm about to go look for details on my card.

I feel closer anyway and those instructions are really straightforward, at least for me.

One thing that is annoying me is not being able to see any boot messages! Is there anyway I can see this so I know what is happening during boot?

Thankyou!
You could try also the *snd-sb16* driver. Try also the *OSS sb* driver, in case there isn't an *ALSA* driver for this card.

You don't need to be able to see the messages during boot. Your boot messages are saved in your system logs.

To access your system logs, go to *System -> Administration -> System Log*. If you have booted your system recently then you will be able to see your boot messages in the *kern.log*, *messages* and *syslog*, for example.

If these logs are not in the list of logs, you can easily add them by selecting *File -> Open*. The logs files are in the */var/log* folder.

---

### Post by Snowflake128 on 2008-11-02
I've been typing dmesg to try and see things but I shall have a peek in the logs too, so thanks for that!

Still not having a lot of luck.

I've been using the -v switch to make modprobe show more info but when I enter the line at the console it seems to act like all the modules are loaded no problem but then when I do:

asoundconf list

only the other cards are shown. (I stuck in another pci card to see how it would like it and it detected it right away and it appears in everything, even the sound thing in the gui)

As I'm not getting any error messages, it's hard to work out what could be going wrong!

Unless I need to do something special to get the card into the asoundconf list?

I shall try the sb16 driver just to see but obviously thats not the bit of the card I want to get working! ;)

I might give up shortly and put a sb awe 64 in there instead, as that is pnp but obviously thats a much more limited card. :(

Maybe there is something wrong with my awe 32. :(

---

### Post by Snowflake128 on 2008-11-02
Yay! I have an error message!

probe of sbawe.0 failed with error -12

:)

I feel like I'm getting closer.

I also tried the sbawe64 which taught me a lot. Firstly it threw my audio pci card off the asoundconf list etc. So I removed the ensoniq card and managed to get it working fairly quickly. It appeared right away in the asoundconf list and in the gui, so I don't need to do anything extra there.

I'm going to double check my settings.

Anyone know what error -12 is?

---

### Post by Snowflake128 on 2008-11-02
I've shuffled all my card settings around in case there is a conflict or something, and I'm much closer I think. I'm playing with the sb16 driver in the hope that theres less to go wrong, and after a lot of messing around I'm now getting probe error -22 instead, which I suspect means it got further before failing.

That gives some indication that it is talking to the card perhaps?!

If anyone has any idea of the meaning of these error numbers I would love to know. :)

I've been trying to find something in google but I just keep finding people trying to get old Vesa video cards working! At first I thought "Why are these people messing with old Vesa cards in this day and age" and then I realised that people in glass houses shouldn't throw stones! ;)

---

