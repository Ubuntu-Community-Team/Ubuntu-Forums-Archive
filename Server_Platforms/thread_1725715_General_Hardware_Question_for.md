---
title: "General Hardware Question for"
date: 2011-04-10
forum: Server Platforms
---

### Post by Don0918 on 2011-04-10
Hi,

I am relatively new to Ubuntu and Linux in general. In fact, I am just starting to get myself acquainted with Linux as an OS.

Anyway, the main reason why I am getting into Linux - aside from the fact that I get to play with it from time to time at work - is that I am planning to build a Media Server based on Linux.

I have a read a LOT of websites claiming that Linux is really light on server requirements and doesn't require high-end hardware to run as opposed to Windows servers. How does that translate to Media servers? Is that generalization still valid?

With regards to building and running a Linux-based home server, do I focus more on CPU specs or RAM? What components should I focus on more when it comes to running Linux in a server environment?

I don't know if this post is supposed to be in this section and I apologize to the Moderators in advance.

---

### Post by Joe of loath on 2011-04-10
Yup, still valid! I've run a (Debian) server on a 433mhz Celeron with 256mb of RAM before.

For a media sever I'd recommend a reasonable dual core CPU, 1 or 2gb of RAM, and just spend the rest of your budget on decent hard drives. Specification isn't important really, so go for low power consumption first and foremost.

---

### Post by spynappels on 2011-04-10
Generally that is true, but just think whether you will need to transcode media on the fly. That tends to use a lot of resources, and as RAM is cheap, I'd tend to go for 4GB. A Dual Core CPU should be ok, but if the budget stretches to a Quad Core, that might be better. AMD tends to be a little cheaper for this and works perfectly with Ubuntu.

It is just for file storage and streaming without transcoding, Joe is spot on.

---

### Post by Joe of loath on 2011-04-10
Yeah, as above you'll want a lot more grunt for transcoding. If you are, I recommend getting an Athlon X3 450, and a motherboard that suppors core unlocking. If you're lucky you'll get a cheap Phenom B50, if you're unlucky you'll still have a decent processor. You might even be able to use GPU power for transcoding, but I've never tried, so don't know if that's possible.

---

### Post by Don0918 on 2011-04-11
Thank you so much for the quick replies!

One question though regarding on-the-fly transcoding, won't the quality of the media being played - like a Blue-ray format file - take a hit when you transcode on-the-fly as compared to letting the server transport the file as-is and let the processing be done by an A/V receiver?

I am thinking of letting the server just 'serve' the files and let the grunt work of transcoding be done by a dedicated hardware - I mean that's what an A/V receiver is for, right?

I appreciate the response, guys... really means a lot to hear your varied opinions... ^^

---

