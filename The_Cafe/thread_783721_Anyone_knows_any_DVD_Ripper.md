---
title: "Anyone knows any DVD Ripper?"
date: 2008-05-06
forum: The Cafe
---

### Post by Christopher22 on 2008-05-06
Hi People,
I am on the look out for fast and easy to use DVD ripping software, which can provide good speed with decent quality.  I am having a storage problem in my system as I have many things to keep update and there are DVD format movies which are large files which use a lot of space in hard drive. Any help will be highly appreciated.
Thanks a lot!

---

### Post by Kingsley on 2008-05-06
I suggest dvd::rip which should be in the Ubuntu repos.

---

### Post by retrow on 2008-05-06
You'll also need some codecs which you can find in medibuntu repositories.

Find and add the medibuntu repository and its associated keys for your version of Ubuntu. Then,
```
sudo apt-get update && sudo apt-get install libdvdcss2 libdvdread3 ubuntu-restricted-extras w32codecs
```

---

### Post by qazwsx on 2008-05-06
I suggest CLI. There are lots of annoying bugs or missing features in GUI apps. And I found some GUI rippers to be very confusing and hard to use.

Very good HOWTO and quality guaranteed:
[http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)

---

### Post by Christmas on 2008-05-06
You can also try thoggen. It's simple but yet incomplete, however it will successfully rip your DVDs or DVD iso images into theora video. You can't specify audio bitrate for example, but it does its job.

---

### Post by BigSilly on 2008-05-06
I always use K9Copy myself. I don't do it very often anyway, but I only rip the movie - no menus - since I don't like the picture quality compromised. It's much easier for me to do this with K9Copy, since all I do is untick the "Keep original menus" box. 

It's still fully featured either way, so it's well worth a look I reckon.

---

### Post by SuperSon!c on 2008-05-06
> **Christopher22 said:**
> Hi People,
I am on the look out for fast and easy to use DVD ripping software, which can provide good speed with decent quality.  I am having a storage problem in my system as I have many things to keep update and there are DVD format movies which are large files which use a lot of space in hard drive. Any help will be highly appreciated.
Thanks a lot!

i don't understand.  you have rips already on there but are too large and you need more room?  what did you use to rip the ones you already have?

---

### Post by 3rdalbum on 2008-05-06
If you want to rip a DVD in its complete format to your hard disk, use K9Copy and specify the output as "File Image". VLC can open the ISO file directly to play the DVD. And you can burn the ISO to a 4.7 gig DVD.

If you want to rip parts of a DVD, or you want greater compression, you could use Acidrip. It's still a little confusing to get your head around at first, but once you're used to the interface it works really rather well.

---

### Post by herbster on 2008-05-06
Sounds like you want to burn DVDs, not rip them? Or am I misunderstanding?

To rip, I use DVD Decrypter via Wine, a flawless solution. To make a custom DVD out of video files, you can use DeVeDe, or avidemux+dvdstyler, etc.

---

