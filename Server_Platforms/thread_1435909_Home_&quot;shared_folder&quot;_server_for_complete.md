---
title: "Home &quot;shared folder&quot; server for complete newbies?"
date: 2010-03-22
forum: Server Platforms
---

### Post by Shampyon on 2010-03-22
I want to start with a warning:  I'm a complete ignoramus when it comes to servers. I don't know any of the terminology - phrases like "headless", "NAS" and so on just fly right over my head. I'm sorry for the difficult task you have ahead of you.

Now for my situation: I'm thinking of putting together a storage computer accessible on my home network (would that be a NAS?) but not over the internet. It will be used to store videos (mostly XViD AVI's and x264 MKV's), music and possibly photographs. It's entire purpose will be to make the media files available for the other two desktop computers on the network (one Kubuntu, one WinXP) and for my home multimedia player([_[COLOR="Blue"]link for specs[/COLOR]_]("http://www.astone.com.au/index.php?productID=25"), plays almost all video formats, most audio, etc). Because of this I don't think it would require any add-on cards like VGA or audio, so long as it has an on-board LAN port.

Basically I'd like to be able to turn it on, leave it running for days at a time, free of peripherals or need for login. I'm hoping to be able to put a number of terabyte or two terabyte HDDs in there. Perhaps up to 8TB, if that's at all possible.

Money is an issue, unfortunately. I've read that you can turn old computers or low end desktop PC parts into a server adequate for this kind of task, and that's the route I'm most likely to take hardware-wise.

So that's the backstory. The question: Is this feasible? Would it be easy enough to just put the parts together with a temporary optical drive and peripherals, then unplug those permanently and leave it near the router to hum away while the other devices on the network access it's files?

---

### Post by lordyosch on 2010-03-22
Is it feasible? Yes.

I used to use a NAS (Network attached Hard disk) for just this purpose (used to because the disk died).

There is a file in the folder /etc called fstab which lists all the things the computer looks for when it switches on.

 
I added a couple of lines to this file and it found them every login so I could share files between Ubuntu desktop, Windoze laptop.


As an alternative, you could use a shared folder on your main computer. This is what I do since the NAS died. I have a partition on the main disk of the Ubuntu PC which contains folders for photos, videos and music. In their preferences I have set them to sharing.
I can access them via my Windows laptop whenever the main PC is on (which is most of the time!)

Also, the Ubuntu box feeds my Pinnacle Showcenter media player.


Jay

---

