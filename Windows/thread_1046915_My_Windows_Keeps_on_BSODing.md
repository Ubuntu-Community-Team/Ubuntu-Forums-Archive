---
title: "My Windows Keeps on BSODing"
date: 2009-01-21
forum: Windows
---

### Post by RealG187 on 2009-01-21
On my laptop I have Ubuntu and Vista and Vista keeps on BSODing, before this I have only seen a BSOD in Vista very few times, but now I see atleast 5 a day and it's pissing me off!

I access my Ubuntu partition using EXT2FSD and sometimes it BSODs when I access that partition heavily, but I just had on when I wasn't accessing  it at all.

Is there a file or something I can post to help diagnose and solve this?

---

### Post by RealG187 on 2009-01-23
I just got "Bad Pool Header"

---

### Post by Izek on 2009-01-25
Have you tried googling "Bad Pool Header"?

[Google Search It Here](http://www.google.com/search?hl=en&q=Bad+Pool+header&btnG=Google+Search&aq=f&oq=Bad+Pool+heade)

---

### Post by jrusso2 on 2009-01-25
Are you saying this started when you started using EXT2FSD?

If so I would uninstall it and stop using it.

---

### Post by RealG187 on 2009-01-27
> **jrusso2 said:**
> Are you saying this started when you started using EXT2FSD?

If so I would uninstall it and stop using it.

I cannot do that, all my files are on that partition.

I cannot confirm that EXT2FSD does it, cuz there are times when it foes it when I am not using L:\


EDIT:

[http://justinmoy.com/2009/01/windows-7-bsod.html](http://justinmoy.com/2009/01/windows-7-bsod.html)
> but I have gotten it twice now. The good thing is that I can reproduce it. I have a partition on my computer accessed through Ext2Fsd.

I think it does do it when I listen to music... It's not WMP it's EXT2FSD (he thinks it's WMP12 if you go there).

Is there another program that I can access my EXT3 partion with from Windows?

---

### Post by joeblow1102 on 2009-01-27
Yay, that's my website you linked to!  Um, if you read that post, accessing the partition through Foobar2000 works fine so I don't know what's going on.  Um, have you tried [http://www.fs-driver.org/](http://www.fs-driver.org/) ?  I couldn't install that in Windows 7 because it checks for XP or Vista.

EDIT:
I should also add that EXT2FSD worked for me perfectly fine in both Vista and XP.  In Vista, it also worked with WMP11.

---

### Post by RealG187 on 2009-01-28
So you came to this thread by me posting the link to here?

I tried EXT2IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) and monted the partition as L:\ and when I would open it windows would say the drive is not formatted. Does it work with Vista SP2, I seen a screenshot of it in Vista (I think on their site) so I thought it would work.

Funny, you say EXT2FSD works for you on Vista, but for me Vista BSODs with the same error you got...

---

