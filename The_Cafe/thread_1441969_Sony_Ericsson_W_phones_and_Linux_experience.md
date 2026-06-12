---
title: "Sony Ericsson W phones and Linux experience"
date: 2010-03-29
forum: The Cafe
---

### Post by Untitled_No4 on 2010-03-29
Hi,

I'm thinking of getting one of the Sony Ericsson W series phones but I can't seem to find any information about what works under Linux, so I thought I'd check out if anyone has any experience with those.

I'm not at all interested in all the sophisticated functionality, all I care about is whether transferring music to the device using Linux is easy, difficult or impossible. Is the phone recognised as a USB drive that supports Drag & Drop or do you need to use any especially useless Sony software (I know they love making those) to manage your music?

Any information is greatly appreciated.

Thanks!

---

### Post by FuturePilot on 2010-03-29
For the most part they work fine. I have a W760i and it shows up as a mass storage device along with the memory card that you can browse with Nautilus. I use Banshee and it doesn't show up out of the box but the fix is simple. I just had to create a file on the memory card called ".is_audio_player" and bam! it showed up in Banshee. I also had to put audio_folders=music/ in .is_audio_player so that my music got put in the correct folder. Other than that everything else works fine except the bluetooth remote control. It's been broken since around 8.04 :(

---

### Post by Untitled_No4 on 2010-03-29
That's great! Mass storage device is good enough for me, but I'll try your is_audio method and see if it works with Amarok since I use KDE.

Thanks!

---

### Post by ashwinrao on 2010-03-29
My K810i works without any issues in 9.10. Yes, it displays memory card and phone without any extra software. Transferring music and images very easy since it opens up with F-spot and Rhythmicbox.

---

### Post by BigSilly on 2010-03-29
My W810i connects to Ubuntu just fine, and files transfer as they should.

:)

---

### Post by Linuxforall on 2010-03-29
No issues here with my ancient W800.

---

### Post by Untitled_No4 on 2010-03-29
Thanks everyone. Have just ordered a W995 phone.

---

### Post by Untitled_No4 on 2010-04-02
Thanks again everyone. Got the W995 phone yesterday and I had a surprise I didn't expect from Sony...

When you connect the phone to the computer it starts the connection but tells you to press cancel if not using Windows. Once you press cancel there are three options, one which is labeled "Other operating systems (e.g. Mac or Linux)" (or something like that, the phone is not next to me at the moment). The phone is not for me and I've never had an SE phone, but I have quite a few Walkman MP3 players and was surprised that anything made by Sony explicitly mentions Linux. This actually connects the phone as a network device (I guess to use as a modem?) and to transfer files I had to choose to connect as USB mass storage device, which worked smoothly.

I was also impressed by the face the phone can be set to a network device, meaning that files can be transferred over wifi without the need for the phone to go into USB mode (and hence not having phone functionality). 

It's great to see someone like Sony admitting that such a thing as Linux exists and that they cannot afford to pretend it doesn't exist anymore.

Thanks again for all.

---

