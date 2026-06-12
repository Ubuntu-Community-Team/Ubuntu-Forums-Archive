---
title: "Are XMMS and VLC kosher?"
date: 2006-11-12
forum: The Cafe
---

### Post by paul6 on 2006-11-12
Do XMMS and VLC include any illegal codecs? After learning that the popular w32codecs and lib2dvdcss packages are illegal in the US, I did a bit of googling on XMMS and VLC. I found this on the VLC website:

> Some of the codecs distributed with VLC are patented and require you to pay royalties to their licensors. These are mostly the MPEG style codecs.

With many products the producer pays the license body (in this case MPEG LA) so the user (commercial or personal) does not have to take care of this. VLC (and ffmpeg and libmpeg2 which it uses in most of these cases) cannot do this because they are Free and Open Source implementations of these codecs. The software is not sold and therefore the end-user becomes responsible for complying to the licensing and royalty requirements. You will need to contact the licensor on how to comply to these licenses.

This goes for playing a DVD with VLC for your personal joy ($2.50 one time payment to MPEG LA) as well as for using VLC for streaming a live event in MPEG-4 over the Internet. 

I also found this info this info on XMMS from the Fedora FAQ:

> Q: How do I make XMMS play MP3s?
A: Before I talk about this, you should know: In the United States and other countries, you legally must pay patent royalties to use MP3 players or encoders.

Yet Ubuntu includes the mp3 plugin by default in XMMS, and both packages are in the repositories. Thoughts?

---

### Post by IYY on 2006-11-12
> Yet Ubuntu includes the mp3 plugin by default, even in US installations. Thoughts?

Since when? XMMS has never played MP3's for me before I installed the codecs.

As for VLC, I'm not entirely sure. It might include illegal stuff with it (it's in the nonfree repositories anyway, so that's fine.)

---

### Post by paul6 on 2006-11-12
> **IYY said:**
> Since when? XMMS has never played MP3's for me before I installed the codecs.

As for VLC, I'm not entirely sure. It might include illegal stuff with it (it's in the nonfree repositories anyway, so that's fine.)

All I know is that MP3's seem to work fine in XMMS for me, and I have never installed the codecs. And if VLC includes illegal codecs, shouldn't it be excluded from the repositories entirely? :confused:

[Edit] I just checked XMMS and it includes "MPEG Layer 1/2/3 Player 1.2.10" plugin installed. (This is on Ubuntu Edgy, by the way. Maybe it is a new Edgy feature.)

---

### Post by hizaguchi on 2006-11-12
"Illegal" depends on where you live.  Just because something is illegal in one country doesn't mean that everybody else can't use it.  That's the point of the non-free repositories.

---

### Post by paul6 on 2006-11-12
> **hizaguchi said:**
> "Illegal" depends on where you live.  Just because something is illegal in one country doesn't mean that everybody else can't use it.  That's the point of the non-free repositories.

Under that line of reasoning, why aren't also the w32codecs and lib2dvdcss included in the nonfree repositories? Sorry if I sound rude, I'm just trying to challenge you guys minds. :)

[Edit] I do understand that they aren't illegal everywhere, I'm not picking on you. I am trying to point out the inconsistency in the Ubuntu logic. If w32codecs and lib2dvdcss are absolutely NOT included than why are XMMS and VLC?

---

### Post by mostwanted on 2006-11-12
> **paul6 said:**
> Under that line of reasoning, why aren't also the w32codecs and lib2dvdcss included in the nonfree repositories? Sorry if I sound rude, I'm just trying to challenge you guys minds. :)

[Edit] I do understand that they aren't illegal everywhere, I'm not picking on you. I am trying to point out the inconsistency in the Ubuntu logic. If w32codecs and lib2dvdcss are absolutely NOT included than why are XMMS and VLC?

There is no inconsistency, you're just misunderstanding what w32codecs allows you to do.

XMMS and VLC are only included in the repositories, not in the standard distribution. Mp3 support and support for most video codecs is also available from the repositories.

Mp3 is not a Microsoft format it doesn't need a Microsoft codec to be played. Usually, MAD is used to play mp3 files and MAD is indeed available in the repositories. The W32codecs package includes codecs for WMV and other such codecs developed solely by Microsoft. No comparative open source codecs have been developed for these file formats, like they have been for formats like AAC, Mp3, MPEG video and h264.

The reason why the w32codecs package isn't included in the repos is because Microsoft retains the rights to its own software. Pirating is illegal in every "modern" country with a  rule of law.

---

### Post by Rashid584 on 2006-11-12
So what happens if you are caught with w32coedcs installed, in say the US?

Get sent to guantanamo bay? :p

-Rashid

---

### Post by mostwanted on 2006-11-12
> **Rashid584 said:**
> So what happens if you are caught with w32coedcs installed, in say the US?

Get sent to guantanamo bay? :p

-Rashid

What happens if you're caught with a pirated Photoshop?

Of course, most people don't get caught with using pirated software, but pirating is pirating; doesn't matter if the software is made by Microsoft or Adobe.

---

### Post by SunnyRabbiera on 2006-11-12
I think I should just convert all my MP3's to oog's and get it over with.
Now how come other MP3 players dont charge huh? Is this another anti linux thing?
Makes me flustered!

---

### Post by Patrick K. on 2006-11-12
If you bought an MP3 player, DVD player or Windows/Mac OS. Then you have already paid those fees. They are included in the price of any one of those.

I already had my lawyer check that out for me before I installed the codecs on Ubuntu.



> **mostwanted said:**
> What happens if you're caught with a pirated Photoshop?

Of course, most people don't get caught with using pirated software, but pirating is pirating; doesn't matter if the software is made by Microsoft or Adobe.

Your only in-trouble if you are distributing the software. If you have a pirated copy but not sharing it. They wont give a damn. If you are sharing it, then you best be worried.

---

### Post by SunnyRabbiera on 2006-11-12
well i already bought a DVD player in the cost of my computer therefore I should have the right to use it no matter what OS I am on.
This crap is gonna change you bet when Vista comes and those bigwigs face its flawed nonsense.

---

### Post by mostwanted on 2006-11-12
> **Patrick K. said:**
> 
Your only in-trouble if you are distributing the software. If you have a pirated copy but not sharing it. They wont give a damn. If you are sharing it, then you best be worried.

Well, I already said it's not very plausible that you will ever get caught and much less prosecuted, but that doesn't mean it's not illegal.

---

