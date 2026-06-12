---
title: "am back"
date: 2009-08-14
forum: Testimonials &amp; Experiences
---

### Post by yogurt eater on 2009-08-14
I tried ubuntu back in 2006 and things didnt went as expected.
I decided to give ubuntu another try and see how much it improved.
I have the latest version installed and everything is good, I see some changes to the interface and it has become a little bit easier to use than before. 
The only thing that bothers me is the random freezing or restarting.  Other than that ubuntu is good. 

HELLO EVERYBODY!:):popcorn:

---

### Post by moster on 2009-08-15
Well, hello to you to. You say freezing? Well, if you have intel or ati, do know that you are not alone :)

---

### Post by jrothwell97 on 2009-08-15
Welcome back!

Just out of interest, are you using ext4 as your file system?

---

### Post by solwic on 2009-08-15
> **jrothwell97 said:**
> Welcome back!

Just out of interest, are you using ext4 as your file system?

That would have been my first question too.  ext4 is still really buggy.  I need to reformat to ext3 on my lappy, as it keeps locking when I try to empty big files out of the trash.  

Of course, there are numerous reasons that Ubuntu could be freezing.  ext4 is just the most likely.  :)

---

### Post by jrothwell97 on 2009-08-15
Well, I'm using ext4 on both Debian (using a kernel from testing) and Ubuntu, and Ubuntu's kernel appears to be the problem. I haven't had a single lockup using the later kernel on Debian.

One assumes, therefore, that the Jaunty kernel's implementation of ext4 is just bad, and it'll be fixed in Karmic which uses the 2.6.31 kernel.

---

### Post by Martje_001 on 2009-08-15
> **moster said:**
> Well, hello to you to. You say freezing? Well, if you have intel or ati, do know that you are not alone :)
If you don't install flgrx when using ATi you're fine. The open-source drivers are extremely stable and fast (2D of course).

---

### Post by yogurt eater on 2009-08-15
> **jrothwell97 said:**
> Welcome back!

Just out of interest, are you using ext4 as your file system?


yes

---

### Post by yogurt eater on 2009-08-15
> **Martje_001 said:**
> If you don't install flgrx when using ATi you're fine. The open-source drivers are extremely stable and fast (2D of course).


whats flgrx?

---

### Post by jrothwell97 on 2009-08-15
> **yogurt eater said:**
> yes

That is probably what's causing the random freezing, then. If you can live with the occasional lockup, you'll be fine. ext4 should be fully fixed by Karmic.

---

### Post by HappyFeet on 2009-08-15
> **iRun said:**
> ext4 is still really buggy. 

Myself and 3 other people I know use it without any problems. I doubt random freezing and restarting is the fault of ext4. Then again, people would blame the weather if they thought people would buy it.

---

### Post by Arthur_D on 2009-08-15
HappyFeet, there is a chance you 4 have been lucky so far.
Just sayin'. ;)

---

### Post by solwic on 2009-08-15
> **HappyFeet said:**
> Myself and 3 other people I know use it without any problems. I doubt random freezing and restarting is the fault of ext4. Then again, people would blame the weather if they thought people would buy it.

You guys are just lucky, I guess. I've tried ext4 on two PC's here at the house, and they both freeze. With ext3, they're fine. Also, my brother's PC was great until I installed with ext4, and then he started getting random hanging, too.  

I didn't blame ext4 out of pique, but rather because when it is removed from the equation, the system is stable.  Same hardware, same version of Ubuntu with the same programs and updates instaled...only difference was the file system.

And who's to say there weren't a few solar flares or an abundance of electrical interference in the atmosphere those days?  Anything's possible.  :biggrin:

---

### Post by jrothwell97 on 2009-08-15
I don't blame ext4 itself, as such - I blame the kernel's implementation of ext4, which is *horrendously* buggy.

---

### Post by solwic on 2009-08-15
> **jrothwell97 said:**
> I don't blame ext4 itself, as such - I blame the kernel's implementation of ext4, which is *horrendously* buggy.

I can accept that.  I haven't tried ext4 with other distros, so my knowledge is a little limited.  :biggrin:

---

### Post by Dullstar on 2009-08-15
ext3 works quite fine, so I don't see the reason to change it.

---

### Post by jrothwell97 on 2009-08-16
> **Dullstar said:**
> ext3 works quite fine, so I don't see the reason to change it.
Aside from improved performance, extents, large file sizes and no subdirectory limits, improved timestamps, faster fscking and multiple other improvements, there *is* no reason to move to ext4.

---

### Post by Martje_001 on 2009-08-16
> **yogurt eater said:**
> whats flgrx?
The proprietary driver from ATi/AMD. It enables 3D and effects on your computer. You can install it using the 'Hardware Drivers' tool in Ubuntu, but I wouldn't recommend it.

---

### Post by moster on 2009-08-16
There is really nice test of common FSs by phoronix
[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1]("http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1")

---

### Post by ngsupb on 2009-08-17
> **iRun said:**
> I can accept that.  I haven't tried ext4 with other distros, so my knowledge is a little limited.  :biggrin:

Using ext4 on arch distro. Nothing is wrong with it. Works perfectly. So I think it is indeed a problem of Ubuntu's kernel.

---

