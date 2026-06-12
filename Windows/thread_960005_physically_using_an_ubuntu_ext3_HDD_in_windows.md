---
title: "physically using an ubuntu ext3 HDD in windows"
date: 2008-10-27
forum: Windows
---

### Post by mustard675 on 2008-10-27
I need to move a large amount of files. Probably close to a TB worth.

All the data is on my XP machine. I have Ubuntu Hardy and formatted my HDDs in ext3. Can i plug my HDD in my XP machine and have it recognize the ext3 drives somehow? I haven't hooked it up yet so i'm not sure what to expect.

Maybe it will just *work* :???:

---

### Post by jpkotta on 2008-10-27
It will not *just work*.  You can install an ext3 driver in WinXP, though.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sadiqdude on 2008-10-27
there is an alternate methode but little clumsy get a portable harddisk and transfer the data to the portable hdd and then do what ever u want to do with that data

---

### Post by mustard675 on 2008-10-27
> **jpkotta said:**
> It will not *just work*.  You can install an ext3 driver in WinXP, though.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

i will give that a try, maybe this as well:
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)
anyone have experience?

---

### Post by rzrgenesys187 on 2008-10-27
Another option, although probably quite slow, would be to plug the hdd into the XP computer and boot into a live cd.  From the live cd you could access both hard drives and perform the copy.

Or you could install ubuntu to a flash drive and perform the operation, that should be quicker than a livecd.

I'd only try one if these if the programs to allow you to read ext3 in windows fail.

---

### Post by cdaringe on 2008-10-27
i'd recommend using the fs-driver.org, as posted in jpkotta's message.  it integrates your gnu/linux partition seamlessly into your windows OS.  i've only ever used it with READ-ONLY access to my partition, but it does claim write-ability as well (at least for ext2...)

---

### Post by jpkotta on 2008-10-27
Yeah, there are several different ext2/3 drivers for Windows.  I have used one in the past for read/write and it worked well.  However, I think it was ext2 only (not a big deal, ext2 and 3 are essentially the same and can be converted very easily).  I have no idea which one it was because it was a long time ago and I don't use Windows any more.  Do a bit of searching on the forums and see what others use.

---

### Post by Battie on 2008-10-27
I also recommend the driver at fs-driver.com.  It required little effort to set up, integrated seamlessly, and was completely stable on my XP install.

---

### Post by cammin on 2008-10-27
I used to use it, but after installing XP service pack 3, I wasn't able to run programs stored onto an ext2 partition without crashing windows. (writing to the drive worked fine, though)

I'm not 100% sure it was SP3 that caused the problem, but I didn't notice it until right after I installed it.

---

