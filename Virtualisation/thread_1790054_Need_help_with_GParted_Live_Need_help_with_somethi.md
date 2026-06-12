---
title: "Need help with GParted Live?? Need help with something!"
date: 2011-06-24
forum: Virtualisation
---

### Post by ClientAlive on 2011-06-24
Hi,

I was trying to use gparted live to resize a vdi image (virtual disk for my HostClone VM). About the only way I know to explain this is give you a brief background on what I'm trying to do and the main challenge that's come up to haunt me over and over and over throughout this process.

I wanted to make an exact clone of my operating system and p2v it so I'd have a host and a guest that are identical - except - I don't want the guest to be the same size as the host (disk size wise). I want that guest to actually reside on my local disk, not an external usb or anything like that.

Well, just about any way you go, to p2v the thing in the first place you're going to end up with a guest that is the same size (disk wise) as the system you took it from. So the system I took it from uses my entire local disk - every bit of space on it. It's not all used space but it does use the whole disk. So you get the idea.

Finally I managed to figure out how to even clone and p2v the sucker at all and I did that successfully last night. What I ended up with though was a vm with only 6.4 gig of used space but a total size of like 39 gig or something like that and was a dynamically expanding disk. So with that vm on my local disk I had about 7 gig of free space left (on my actual, physical disk I mean). Well 7 gig is a far cry from what like 30 gig (the remaining free space in that dynamically expanding virtual disk) - and I can't see me dealing with all the issues that come up when you start overloading the thing because you forgot (jobs that won't complete and waste your time, error messages, etc, etc). I'm just not gonna handle that sort of thing so well.  :)

So I go this bright idea that I'd set my vm to boot from cd and boot the gparted live cd in it. I'd use that to resize the thing down to 10 gig; and, if it turned out to be the way things work with gparted (never used gparted for this bef), I'd delete the leftover partition in the end.

So here's the problem I ran up against (came back to bite my ^$$ again). Gparted starts running the resize job and it runs for like - ever, and finally it gets to a point and tells me it can't finish the job or something like that because there's not space left on my hard drive (it's talking about my real, physical drive now).

So what I'm wondering is if gparted uses some temp folder where it processes to first; and, if so, where it is and if it can be relocated through some setting in gparted. Maybe I can locate that temp folder on my external drive so the job completes? I don't know.

I also am not sure this is the best way to go about shrinking my vdi but I have read of others doing it this way and it seemed the simplest route.

Thanks in advance for any help and I apologize for such a long, drawn out post. I just want to be clear about what I'm trying to do so the answer may be focused and appropriate.

Thank you.

:)

---

