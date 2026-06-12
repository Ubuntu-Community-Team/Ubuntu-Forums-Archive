---
title: "Creative Sound Blaster Xi Fi Xtreme Audio cards"
date: 2008-11-24
forum: The Cafe
---

### Post by waapwoop1 on 2008-11-24
Hi There,

thinking of buying one of these:-

[http://www.soundblaster.com/products/product.asp?category=1&subcategory=208&product=15855&nav=0](http://www.soundblaster.com/products/product.asp?category=1&subcategory=208&product=15855&nav=0)

Do these work in Linux/Ubuntu?

Anyone had any success here with them?

---

### Post by Skripka on 2008-11-24
I toyed with one long enough to get pissed at it and tear it out of my machine and use the onboard mobo audio (which is quite good).  Creative has released an open source driver that to my knowledge supports every X-Fi card *except* the Xtreme Audio.

---

### Post by FuturePilot on 2008-11-24
I don't think quite yet, but it should soon.
[http://www.phoronix.com/scan.php?page=article&item=creative_xfi_gift&num=1]("http://www.phoronix.com/scan.php?page=article&item=creative_xfi_gift&num=1")

Edit:
Apparently not Xtreme Audio. :(

---

### Post by waapwoop1 on 2008-11-24
I like what they are advertising, what their sound cards do to mp3 quality. If its true, i want one.

---

### Post by Rhapsody on 2008-11-24
I think there is some confusion in this topic. From what I understand, the X-Fi XtremeAudio will *never* be supported in the X-Fi drivers because it's not actually an X-Fi at all. It's a rebranded Sound Blaster Audigy SE, and so uses the same drivers as that card.

I'd avoid it anyway since the ALSA support is apparently not very mature, the EAX support is all in software, and it doesn't even have the same EMU10K2 processor that is in the other Audigy cards. You instead have to muddle along with a CA-0106 chip, with the result being that your CPU does most of the processing.

---

### Post by Skripka on 2008-11-24
> **Rhapsody said:**
> I think there is some confusion in this topic. From what I understand, the X-Fi XtremeAudio will *never* be supported in the X-Fi drivers because it's not actually an X-Fi at all. It's a rebranded Sound Blaster Audigy SE, and so uses the same drivers as that card.

I'd avoid it anyway since the ALSA support is apparently not very mature, the EAX support is all in software, and it doesn't even have the same EMU10K2 processor that is in the other Audigy cards. You instead have to muddle along with a CA-0106 chip, with the result being that your CPU does most of the processing.

That sounds right--when I had that card in my box, *buntu called it "CA0106"-and at the time I couldn't figure out why.  ALSA handled audio output fine through the card-but I never had luck getting the input on it to work.  One would think Creative would support Sound Blaster or rebranded Sound Blaster cards-since Creative bought them out.  But Oh, well.  The ALC883 is just as good if not better, as it works completely and easily with ALSA.

---

### Post by waapwoop1 on 2008-11-24
what about their usb cards?

really want to see if they live up to what they say, i have a lot of mp3s, but don't like the sound quality. even ones compressed at a higher bitrate i don't like so much... bu put up with them.

---

### Post by Redache on 2008-11-24
It wont do anything to improve the sound, that's marketing guff. The only way to get a real improvement in sound is to get a decent set of speakers, MP3s can only be as good as the Bitrate they have, you can't create software that magically enhances it.

So if I were you I'd invest in some decent speakers rather than a Soundcard.

---

### Post by Skripka on 2008-11-25
> **waapwoop1 said:**
> what about their usb cards?

really want to see if they live up to what they say, i have a lot of mp3s, but don't like the sound quality. even ones compressed at a higher bitrate i don't like so much... bu put up with them.

Also mp3 is a lossy compression algorithm (all are, but mp3 especially)...there are lots out there-and even high-bitrate mp3 loses a great deal of data in the quest to make a small file.  In short use another compression algorithm/filetype if you don't like what you're getting

---

