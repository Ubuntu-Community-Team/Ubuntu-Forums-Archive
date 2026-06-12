---
title: "Issues with DVD Burning"
date: 2007-04-23
forum: System76 Support
---

### Post by Kaloma on 2007-04-23
I didn't post this in general Ubuntu Forums yet because I don't know whether it might be related to my specific Serval Performance hardware.

I am trying to burn a data DVD today without success. The disc is a DVD-R 4.7GB.  The message I receive from Nautilus CD Burner is:
> Please replace the disc in the drive with a supported disc with at least 4.4 GiB free.  The following disc types are supported:
DVD+R DL
I don't really understand, because I thought that this drive supported several formats like DVD-R, DVD+RW, etc.  I don't remember specifically whether I have burned any format other than DVD+R before with this machine, plus it has been a little while since I've burned anything other than regular CDs. In this time I have upgraded to Feisty.

Anyone else having this issue? Should not DVD-R discs work with this drive?

Thanks,
Matthew

P.S. If you read this, Carl, I was wondering if I might be able to get one of those system76 laptop stickers I now see in some of the photos. At the time my Serval shipped, I guess you guys were making some changes in that area, so I currently have no branding whatsoever on my machine. Thanks!

---

### Post by uclalinux on 2007-04-23
I have a similar issue, did you fined a solution?

---

### Post by Kaloma on 2007-04-23
Well, I have no trouble copying from a data DVD+R to a blank DVD-R using Nautilus and the "Copy disc..." context-menu option. It seems there is a problem only when I place a blank DVD-R in the drive, drag-and-drop files into the Nautilus CD/DVD folder, and click "Write disc".

I am going to try writing my data to a file image first, and then using the "Copy disc..." context-menu option, similar to copying a complete disc. I will let you know how that goes.

Matthew

---

### Post by Kaloma on 2007-04-23
:oops: I must confess I feel very foolish, although some UI hints might have helped.

It turns out, in my case, the issue was simply one of available space on the disc. I guess I forgot to pay attention to the whole GB versus GiB thing, and although Nautilus tell me I'm only trying to write 4.4 GiB, this is actually too much to fit on a 4.7 GB disc. Memorex uses GB and Nautilus uses GiB. Anyhow, the error message not accurate in my opinion since the format of the disc had little to do with it in my case and it suggested that a DVD-R disc wouldn't do the job. I mean, I considered the disc space issue since my original load was 4.6 GB, and I reduced it. After writing to a fiel image, and then using "Copy disc...", the message was a simple "XXX will not fit on this disc" or something equally clear.

Regardless of the details, it appears to be a simple user-confusion issue that could have been avoided with better UI hints (why not tell me how much space in GiB will fit on the blank disc so I don't have to get out the calculator?)

uclalinux, I hope you problem is just this. If not, I won't be of much help. Good luck.

Signing out,
Matthew

---

### Post by Kaloma on 2007-04-23
To save a little face here, I'd like to point out that no one else was able to jump to my rescue on this simple issue. So I guess it really is something easy to overlook. :) 

Matthew

---

### Post by IgnacioMiller on 2007-04-24
Yeah, I never noticed that either.

---

### Post by akniss on 2007-04-25
> **Kaloma said:**
> To save a little face here, I'd like to point out that no one else was able to jump to my rescue on this simple issue. So I guess it really is something easy to overlook. :) 

Matthew

You ought to file a bug against gnomebaker on this... it seems like a valid point of confusion, and one that gnome devs could easily fix if it were brought to their attention.

---

### Post by Kaloma on 2007-04-25
Well, I looked into bugs files against nautilus-cd-burner and there was already one regarding the confusing error message of an earlier version (which I guess was even more confusing than the current message).  So I asked to reopen; we'll see what happens.

Matthew

---

