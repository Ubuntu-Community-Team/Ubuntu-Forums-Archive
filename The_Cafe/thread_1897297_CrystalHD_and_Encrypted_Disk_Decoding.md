---
title: "CrystalHD and Encrypted Disk Decoding"
date: 2011-12-18
forum: The Cafe
---

### Post by sandyd on 2011-12-18
Seeing that a lot of Blu-rays are now protected, I could not play any Blu-rays on the blu-ray [s]player[/s] drive I bought last week. Ubuntu regonizes the files on the blu-ray, but playing is not possible without decryption.

I didn't want to have to go and decrypt the blu-ray, nor did I have the HD space for it.

I decided to search around, and found that CrystalHD cards can play encrypted HD/Blu-ray content.

Im curious though, XBMC supports CrystalHD cards - does that mean it will play encrypted blu-ray/HD-DVDs?

Also, are there any other linux media players that support crystalhd decoding?

---

### Post by cariboo on 2011-12-19
If your stand-alone Blu-Ray player has a network connection, you can get updated decryption automagically when connected to the network. Plus on some players you to get the ability to play streaming media from several sources.

---

### Post by sandyd on 2011-12-19
> **cariboo907 said:**
> If your stand-alone Blu-Ray player has a network connection, you can get updated decryption automagically when connected to the network. Plus on some players you to get the ability to play streaming media from several sources.
Oops, sorry. my bad. Should say blu-ray drive, not player (I do have a player though)
Must be the fact that its 5 in the morning....

---

### Post by 3rdalbum on 2011-12-19
> **sandyd said:**
> Seeing that a lot of Blu-rays are now protected, I could not play any Blu-rays on the blu-ray [s]player[/s] drive I bought last week. Ubuntu regonizes the files on the blu-ray, but playing is not possible without decryption.

I didn't want to have to go and decrypt the blu-ray, nor did I have the HD space for it.

Sorry to hear that. It's not just "a lot of Blu-rays" - it's every single Blu-ray disc on the market that are encrypted.

> I decided to search around, and found that CrystalHD cards can play encrypted HD/Blu-ray content.

Im curious though, XBMC supports CrystalHD cards - does that mean it will play encrypted blu-ray/HD-DVDs?

I don't believe CrystalHD actually assists in the decryption. As far as I know it just helps to decode and decompress the video as you are playing it.

Even if it can help with decryption, it's not a decryption key. The AACS encryption method is multi-stage and a bit complex, and there are several decryption keys necessary to decrypt the data to a playable state. Not something that can be done on a single chip as it's a concerted effort between multiple components of the computer.

I don't fully understand it myself, but I'm trying to put it into layperson's terms. Otherwise it would be a stream of incomprehensible jargon and acronyms :-)

---

### Post by Primefalcon on 2011-12-19
progress is coming along on proper blu-ray playback

[http://www.videolan.org/developers/libbluray.html](http://www.videolan.org/developers/libbluray.html)

I think the latest version of vlc will play blu-ray btw

---

### Post by sandyd on 2011-12-19
*sigh*
I was hoping to get some sort of native Blu-ray support on my XBMC HTPC sometime soon without ripping cause its a waste of space. Its the only thing that is currently missing. I currently have to use a seperate blu-ray player to stream the output to the screen, and its a bit anoying not to have everything in one box.

I guess I will simply have to go ahead with the SAS RAID 10 Array Ive been thinking of building for some time now, though hard disks aren't exactly in stock, or cheap these days....

---

