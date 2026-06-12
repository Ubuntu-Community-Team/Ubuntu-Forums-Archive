---
title: "Why must MP3/DVD codecs be downloaded  separately?"
date: 2009-12-05
forum: The Cafe
---

### Post by yc2 on 2009-12-05
Ubuntu is distributed without support for MP3 and DVD. It is requred by the user to download these components separately, f.ex. by doing
```
sudo apt-get install non-free-codecs
```

Can someone please tell me why this important (many people use MP3, DVD) software is not included? Is it a requirement when redistributing GPL-licensed software that non-GPL software cannot be included?

---

### Post by hansdown on 2009-12-05
Hi yc2.

It is because the use of these codecs "may" be illegal in the country in which the user resides.

---

### Post by SunnyRabbiera on 2009-12-05
Its all about software patents, and legalities.
Truth be told you have to install DVD and MP3 support in Windows too, when you buy a computer with windows on it DVD and MP3 playback are probably there from the start.
But buy a fresh copy of windows, not the reinstall disc you might have for your computer but a fresh non OEM copy of Windows and you will find out it needs codecs too.

And if you wonder what OEM is:
[http://en.wikipedia.org/wiki/Original_equipment_manufacturer](http://en.wikipedia.org/wiki/Original_equipment_manufacturer)

Basically this means the windows recovery disc you might have from HP, Dell, Gateway, Toshiba, E Machines, ETC

---

### Post by diablo75 on 2009-12-05
> **yc2 said:**
> Is it a requirement when redistributing GPL-licensed software that non-GPL software cannot be included?

I'm not sure, but what I do know is that the decoders are not legal in all parts of the world so it's best to leave these components out and let the user decide whether or not they need to be installed.

---

### Post by Bigtime_Scrub on 2009-12-05
Ridiculous copyright laws in America say that if you own a DVD player you do not have the right to decrypt DVD's without paying for the codecs. So if you own a DVD player, you must pay a fat cat for the privilege to use it.

---

### Post by Bachstelze on 2009-12-05
> **Bigtime_Scrub said:**
> Ridiculous copyright laws in America say that if you own a DVD player you do not have the right to decrypt DVD's without paying for the codecs. So if you own a DVD player, you must pay a fat cat for the privilege to use it.

Software patents != copyright.

---

### Post by SunnyRabbiera on 2009-12-05
> **Bigtime_Scrub said:**
> Ridiculous patent laws in America say that if you own a DVD player you do not have the right to decrypt DVD's without paying for the codecs. So if you own a DVD player, you must pay a fat cat for the privilege to use it.

Yes though I legally purchased DVD playback already when I got this computer so I am covered,

---

### Post by amauk on 2009-12-05
It's not the legality of codecs, per se, but the legality of using certain codecs without patent royalty payment

Some countries recognise patents on software,
therefore use of that software requires royalty payment to the patent holder

The US & Japan are (to my knowledge) the only two countries that recognise software patents
All other countries consider software to be un-patentable (therefore you cannot claim royalties for using said software)

If vendors were to distribute patented codecs in the default install, they would be responsible for the royalty payments

If they leave it up to the user, then the user is responsible

Now, there's all sorts of exceptions to the requirements for paying royalties (and the exceptions are different depending on where you are, what you are using the codecs for, etc.)

It is just not feasible for a vendor to determine when payment is appropriate
indeed, the administrative costs of keeping everything in check probably far outweigh the actual royalty payments

so you either pay a negitiable sum of money to the patent holder for any and all eventualities (commercial software)
or, you leave it up to the user (free software)

---

### Post by yc2 on 2009-12-05
Thanks all of you guys, consulting this community can really be clarifying.

I do not think there are any software-patent royalties on some proprietary software, like ATI and nVidia drivers? (These corporations get their profit from the hardware only?) So these are included on the Ubuntu CD?

Can I please add two questions:

What commonly used software is patented?
MP3-codec
DVD-codec
Flash-player ?
...
...

Does anyone happen to know if a Swedish Ubuntu-remix containing these components could be liable to pay royalties? - If brought from Sweden to the US or Japan maybe??

---

### Post by cascade9 on 2009-12-05
> **Bigtime_Scrub said:**
> Ridiculous copyright laws in America say that if you own a DVD player you do not have the right to decrypt DVD's without paying for the codecs. So if you own a DVD player, you must pay a fat cat for the privilege to use it.

I'm probably being overly technical, and I'm probably also splitting hairs, but as far as I know the reason why you cant have software to decode DVDs is because the DCMA

> criminalizes production and dissemination of technology, devices, or services intended to circumvent measures that control access to copyrighted works

[http://en.wikipedia.org/wiki/Digital_Millennium_Copyright_Act](http://en.wikipedia.org/wiki/Digital_Millennium_Copyright_Act)

Since DVDcss is a "anti-piracy measure" (yeah, right) its illegal to distribute in the US (thanks to australia's 'Free Trade Agreement' with the US its probably illegal here as well)

> **amauk said:**
> The US & Japan are (to my knowledge) the only two countries that recognise software patents
All other countries consider software to be un-patentable (therefore you cannot claim royalties for using said software) 

Add australia to that list. 

> Broadly speaking, computer software is patentable in Australia.  The underlying principle is that an invention is patentable provided it results in an “artificially created state of affairs” having economic significance and it has been held that software is capable of meeting this requirement. 

[http://www.ipta.com.au/indexPrev.php?artId=53](http://www.ipta.com.au/indexPrev.php?artId=53)

---

### Post by Bachstelze on 2009-12-05
> **yc2 said:**
> 
I do not think there are any software-patent royalties on some proprietary software, like ATI and nVidia drivers? (These corporations get their profit from the hardware only?) So these are included on the Ubuntu CD?

The name "software patent" is a bit misleading, as it does not cover programs, but technologies (programs are covered by copyright, which is a different thing).

To take the example of DVD, libdvdcss, while being Free Software, violates the software patents on the CSS algorithm. Basically, the DVD Copy Control Association (which holds the patents on the CSS algorithm) said: "whoever wants to use CSS must buy a license from us." Same goes for MP3: it is the format that is patented, not the codecs.

> What commonly used software is patented?
MP3-codec

Yes, though once again, it is the format that is patented, not the codec (which is a program).

> DVD-codec

There is no such thing as a "DVD codec", but yes, DVDs use a lot of patented technologies (the CSS encryption algorithm, the MPEG-2 video compression format, the AC3 audio compression format, etc.).

> Flash-player ?

Not sure about Flash, but it is probably patented too.

---

### Post by 3rdalbum on 2009-12-05
> **yc2 said:**
> Thanks all of you guys, consulting this community can really be clarifying.

I do not think there are any software-patent royalties on some proprietary software, like ATI and nVidia drivers?

ATI and Nvidia's own drivers are closed-source. Ubuntu does not ship anything closed-source except for firmware (which is run on a peripheral device, not on the CPU).

They do contain patented features, but the patent license has been paid by Nvidia or ATI.

> What commonly used software is patented?
MP3-codec

The methods needed to compress and decompress MP3 audio are patented. Fluendo has paid for a license and distributes a decompressor, but Ubuntu doesn't ship it as a matter of principle.

> DVD-codec

DVDs require codecs that use patented algorithms. The main problem is that of decryption. DVDs are encrypted, and anyone who makes a DVD decryptor must pay a fee per-unit for a DVD decryption key. Obviously it can't be done for Ubuntu, where there's 20 million copies of Ubuntu in circulation.

As for unlicensed DVD decryption, it's illegal in many countries to break an encryption scheme or distribute software that can break encryption.

> Flash-player ?

Just like the ATI and Nvidia drivers, the Flash Player does not represent a cost to anyone redistributing it. But it is closed-source and therefore Ubuntu will not ship it on the CD.

> Does anyone happen to know if a Swedish Ubuntu-remix containing these components could be liable to pay royalties? - If brought from Sweden to the US or Japan maybe??

From what I hear, US customs do sometimes check your computer for unlicensed codecs. I wouldn't try it. If you had DVD decryption software you'd either be turned away or charged with an offence.

---

### Post by t0p on 2009-12-05
Are you people *sure* it's because of the *legalities* of distributing the codecs?  I think it's an *ideological* thing.  The Ubuntu devs don't want to ship "unfree" codecs with Ubuntu.

There are other free (as in cost) Linux distros that *do* include the codecs for mp3 and DVD.  How come Ubuntu is constrained by codec laws and the other distros are not?  Or are you saying that the Ubuntu devs are obeying some obscure law that the other distros don't know about?  Or that the other distros are reckless?  Or what?  How come Linux Mint comes with these "illegal" codecs?

---

### Post by t0p on 2009-12-05
> **3rdalbum said:**
> 
From what I hear, US customs do sometimes check your computer for unlicensed codecs. I wouldn't try it. If you had DVD decryption software you'd either be turned away or charged with an offence.

Don't be silly.  How would a customs agent know that a particular piece of software on my computer is for decrypting DVDs?  Are they going to run every piece of software to see what it does?

---

### Post by amauk on 2009-12-05
> **t0p said:**
> Are you people *sure* it's because of the *legalities* of distributing the codecs?  I think it's an *ideological* thing.  The Ubuntu devs don't want to ship "unfree" codecs with Ubuntu.You say that like they are different issues

The four freedoms required (by the GNU project) to constitute a program as "free software"

- Freedom 0: The freedom to run the program for any purpose.
- Freedom 1: The freedom to study how the program works, and change it to make it do what you wish.
- Freedom 2: The freedom to redistribute copies so you can help your neighbor.
- Freedom 3: The freedom to improve the program, and release your improvements (and modified versions in general) to the public, so that the whole community benefits.

Patented software would violate (at the very least) freedom 0

So yes, it is idealogical
but with very practical, real world connotations

Applied idealogical, if you will

take the mp3 format and associated software codec as an example

Users are not free to run the program for any purpose.
Some purposes would require royalty payment
(again, in certain jurisdictions that recognise software patents)

---

### Post by t0p on 2009-12-05
> **amauk said:**
> You say that like they are different issues

The four freedoms required (by the GNU project) to constitute a program as "free software"

- Freedom 0: The freedom to run the program for any purpose.
- Freedom 1: The freedom to study how the program works, and change it to make it do what you wish.
- Freedom 2: The freedom to redistribute copies so you can help your neighbor.
- Freedom 3: The freedom to improve the program, and release your improvements (and modified versions in general) to the public, so that the whole community benefits.

Patented software would violate (at the very least) freedom 0

So yes, it is idealogical
but with very practical, real world connotations

Applied idealogical, if you will

take the mp3 format and associated software codec as an example

Users are not free to run the program for any purpose.
Some purposes would require royalty payment
(again, in certain jurisdictions that recognise software patents)

You're not the person my post was aimed at.  You agree with me that is is a matter of ideology.

My previous post was aimed at those who say that Ubuntu don't include the codecs because it would be illegal of Ubuntu to do that.

So the law affects Ubuntu but not the distros that *do* include proprietary codecs?  How come Linux Mint hasn't been sued to destruction?

---

### Post by Bachstelze on 2009-12-05
> **t0p said:**
> You haven't really addressed my point.  How come the law stops Ubuntu shipping with the codecs while other distros ship them with impunity?

A lot of people download music from eMule with impunity. Does that mean Ubuntu should ship with the latest Britney album?

And before you say nobody actually got in trouble because of patent violations, have a look at what happened to DVD Decrypter.

---

### Post by amauk on 2009-12-05
> **t0p said:**
> You haven't really addressed my point.  How come the law stops Ubuntu shipping with the codecs while other distros ship them with impunity?The law doesn't stop anything

It's Canonical's choice to not distribute software that may require patent royalty payment for usage

as an example, see FFmpeg's FAQ
[http://ffmpeg.org/legal.html](http://ffmpeg.org/legal.html)
> 
Q: Is it perfectly alright to incorporate the whole FFmpeg core into my own commercial product?
A: You might have a problem here. There have been cases where companies have used FFmpeg in their products. These companies found out that once you start trying to make money from patented technologies, the owners of the patents will come after their licensing fees. Notably, MPEG LA is vigilant and diligent about collecting for MPEG-related technologies.

Canonical are a commercial company, and probably do not want to be hounded by patent holders for license fees

If you, the user, are ok with installing possibly patent encumbered software, then fine
but for Canonical to do this by default is asking for trouble from patent holders

Re: other distros
Again, it's their choice

---

### Post by the yawner on 2009-12-05
> **t0p said:**
> You're not the person my post was aimed at.  You agree with me that is is a matter of ideology.

My previous post was aimed at those who say that Ubuntu don't include the codecs because it would be illegal of Ubuntu to do that.

So the law affects Ubuntu but not the distros that *do* include proprietary codecs?  How come Linux Mint hasn't been sued to destruction?

Because some distros believe that they're too small a target.

---

### Post by t0p on 2009-12-05
> **Bachstelze said:**
> A lot of people download music from eMule with impunity. Does that mean Ubuntu should ship with the latest Britney album?

And before you say nobody actually got in trouble because of patent violations, have a look at what happened to DVD Decrypter.

I haven't written a single word in this thread to say whether Ubuntu should or shouldn't ship with the unfree codecs.  I've just addressed the point *why* Ubuntu doesn't include the codecs.  Which is what the OP asked.

---

### Post by amauk on 2009-12-05
> **the yawner said:**
> Because some distros believe that they're too small a target.Exactly
Once you have a commercial company involved (Canonical, Redhat, Novell, etc.) then you become a real target for civil action

Some guy taking a distro, changing default install packages, and rebranding it "Bob's Linux" is not an inviting target, as he probably cannot be sued for very much

---

### Post by t0p on 2009-12-05
In the [documentation on restricted formats]("https://help.ubuntu.com/community/RestrictedFormats"), it says:

> Ubuntu's commitment to only include completely free software by default means that proprietary media formats are not configured 'out of the box'.

ie Ubuntu doesn't include the proprietary codecs because that would violate their Free software philosophy - *not* because including the codecs would somehow be illegal.

Please note: I am not disputing whether shipping the codecs would legal or not.  I am talking about Ubuntu's *reason* for not shipping the codecs.  I say it is a reason of ideology, not legality.  They don't leave out the codecs because they think they might be breaking the law.  They leave out the codecs because including them would violate the Ubuntu philosophy.

---

### Post by Bachstelze on 2009-12-05
> **t0p said:**
> 
ie Ubuntu doesn't include the proprietary codecs because that would violate their Free software philosophy - *not* because including the codecs would somehow be illegal.

Both aren't mutually exclusive, though.

---

### Post by t0p on 2009-12-05
> **Bachstelze said:**
> Both aren't mutually exclusive, though.

I'm talking about stated motives.  I'm not trying to second-guess unstated motives; not am I trying to project my preferred motives.

Nowhere have I seen it said that Ubuntu don't include the non-free codecs because it would be illegal for them to do so.  But I *have* seen it said that they don't include the codecs because that would violate the Ubuntu philosophy.

Therefore, to the OP's question of "why doesn't Ubuntu include the non-free codecs?", I reply: "Because their inclusion would violate Ubuntu's Free software philosophy."

---

### Post by Bachstelze on 2009-12-05
> **t0p said:**
> I'm talking about stated motives.  I'm not trying to second-guess unstated motives; not am I trying to project my preferred motives.

Nowhere have I seen it said that Ubuntu don't include the non-free codecs because it would be illegal for them to do so.  But I *have* seen it said that they don't include the codecs because that would violate the Ubuntu philosophy.

Therefore, to the OP's question of "why doesn't Ubuntu include the non-free codecs?", I reply: "Because their inclusion would violate Ubuntu's Free software philosophy."

[https://help.ubuntu.com/9.10/add-applications/C/restricted-software.html](https://help.ubuntu.com/9.10/add-applications/C/restricted-software.html)

Here it clearly mentions the legal issues, and it's the only page I could find about it in the **official** documentation.

---

### Post by Hallvor on 2009-12-05
> **t0p said:**
> I reply: "Because their inclusion would violate Ubuntu's Free software philosophy."

Then why does Ubuntu include binary-only drivers by default?

---

### Post by Bachstelze on 2009-12-05
> **Hallvor said:**
> Then why does Ubuntu include binary-only drivers by default?

Does it? I know it did at some point with the linux-restricted-modules packages, but they aren't used anymore.

---

### Post by t0p on 2009-12-05
> **Bachstelze said:**
> [https://help.ubuntu.com/9.10/add-applications/C/restricted-software.html](https://help.ubuntu.com/9.10/add-applications/C/restricted-software.html)

Here it clearly mentions the legal issues, and it's the only page I could find about it in the **official** documentation.

But it still does not say that Ubuntu refrain for including it because inclusion would be illegal.  It talks about the fact that *users* might be breaking the law.  For example, here's a passage that mentions possible restrictions on redistribution:

> **Non-free software** is software which is      not freely redistributable or modifiable. **This makes it difficult for the      Ubuntu developers to improve the software and correct problems**, so it is      normally recommended that you use [     free software]("http://www.ubuntu.com/ubuntu/philosophy") instead.

See the bit I emboldened?  It says the devs don't like non-free software because it makes it difficult to improve the software.  Not because redistribution is illegal. (Yes, I know it mentions the fact that  free redistribution might be prohibited.  But it does not say or imply that the law is the reason why Ubuntu does not include it.)

---

### Post by yc2 on 2009-12-05
Hi I'm the OP :) I am very satisfied with the replies I got. Thanks.

If I may continue with a follow up:

When it comes to nVidia, ATI proprietary drivers, I thought Ubuntu was shipped with these? (When you started the Live-CD there was a box saying: "To make your computer perform optimally you are recommended to use proprietary software, for which Ubuntu cannot supply support. To accept this, click here...")

Isn't this correct?

EDIT:
From what I remember my nVidia card ran directly on proprietary drivers without me installing anything. Maybe my information is old and I have updated ever since.

---

### Post by t0p on 2009-12-05
> **Hallvor said:**
> Then why does Ubuntu include binary-only drivers by default?

I don't know, because I haven't seen a statement on how the devs rationalise their inclusion.  But guessing as to reasons will not increase our wisdom.  We can argue about it forever; but we still won't *know* until we're told.

---

### Post by CharlesA on 2009-12-05
Maybe I missed something, but you have to enable the proprietary drivers in "Hardware Drivers" before you can install them, they aren't downloaded by default.

---

### Post by yc2 on 2009-12-05
> **CharlesA said:**
> Maybe I missed something, but you have to enable the proprietary drivers in "Hardware Drivers" before you can install them, they aren't downloaded by default.
It was probably _me_ who missed something. From what I understand here, the ATI and nVidia drivers have never been on the CD. My error.

---

### Post by Bachstelze on 2009-12-05
> **yc2 said:**
> 
When it comes to nVidia, ATI proprietary drivers, I thought Ubuntu was shipped with these? (When you started the Live-CD there was a box saying: "To make your computer perform optimally you are recommended to use proprietary software, for which Ubuntu cannot supply support. To accept this, click here...")

Isn't this correct?

EDIT:
From what I remember my nVidia card ran directly on proprietary drivers without me installing anything. Maybe my information is old and I have updated ever since.

Ubuntu got permission from nvidia to redistribute the drivers, so it's perfectly possible that the Live CD uses them directly. I don't think they are installed on a default installation, though.

---

### Post by Hallvor on 2009-12-05
> **CharlesA said:**
> Maybe I missed something, but you have to enable the proprietary drivers in "Hardware Drivers" before you can install them, they aren't downloaded by default.

I am not talking about Nvidia/ATI drivers or stuff like that. I am talking about non-free binary only blobs in the kernel. I haven`t used Ubuntu since Feisty, but things may have changed.

Anyway, didn`t mean to hijack the thread.

---

### Post by cascade9 on 2009-12-05
> **t0p said:**
> I haven't written a single word in this thread to say whether Ubuntu should or shouldn't ship with the unfree codecs. I've just addressed the point *why* Ubuntu doesn't include the codecs.  Which is what the OP asked.

Answer (which, funny enough, was 2 above that post I just quoted). 

> **amauk said:**
> It's Canonical's choice to not distribute software that may require patent royalty payment for usage

as an example, see FFmpeg's FAQ
[http://ffmpeg.org/legal.html](http://ffmpeg.org/legal.html)

> **Q: Is it perfectly alright to incorporate the whole FFmpeg core into my own commercial product?** 
 A: You might have a problem here. There have been cases where companies have used FFmpeg in their products. These companies found out that once you start trying to make money from patented technologies, the owners of the patents will come after their licensing fees. Notably, MPEG LA is vigilant and diligent about collecting for MPEG-related technologies. 

Canonical are a commercial company, and probably do not want to be hounded by patent holders for license fees

If you, the user, are ok with installing possibly patent encumbered software, then fine
but for Canonical to do this by default is asking for trouble from patent holders. 

Yes, that is talking about FFmpeg but it applies to DVDs (mpeg-2 video) and MP3 (mpeg1 audio layer 3) 

> **t0p said:**
> But it still does not say that Ubuntu refrain for including it because inclusion would be illegal.  

IMO, thats because if Ubuntu actually Did say 'it could be illegal for you to use these codecs', but there is still a way for the user to get the codecs from ubuntu repos, that could open the door for legal action. It wouldn't be the 1st time that a company has hidden practicalities behind philosophy.

---

### Post by MellonCollie on 2009-12-05
> **SunnyRabbiera said:**
> Truth be told you have to install DVD and MP3 support in Windows too, when you buy a computer with windows on it DVD and MP3 playback are probably there from the start.

But buy a fresh copy of windows, not the reinstall disc you might have for your computer but a fresh non OEM copy of Windows and you will find out it needs codecs too.

From memory, retail versions of...

XP played MP3 out of the box, but not DVD.

Vista Home Premium/Ultimate played DVD and MP3 out of the box.

7 plays ["MP4, MOV, 3GP, AVCHD, ADTS, M4A, and WTV multimedia containers, with native codecs for H.264, MPEG4-SP, ASP/DivX/Xvid, MJPEG, DV, AAC-LC, LPCM and AAC-HE".](http://en.wikipedia.org/wiki/Features_new_to_Windows_7#Multimedia)

---

