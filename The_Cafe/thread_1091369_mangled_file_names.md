---
title: "mangled file names"
date: 2009-03-09
forum: The Cafe
---

### Post by leg on 2009-03-09
I use a USB stick to carry files between home (Ubuntu) and work (Windows XP )and I have noticed this morning (at work) that two of the directories on it have completely mangled file names. One I noticed earlier this morning but the other has just become mangled. The files cannot be accessed or deleted stating that I do not have permission and the file sizes are completely wrong. This is a 16GB stick but one of the directories is reporting 116GB in size.

Any ideas what could be causing this.

---

### Post by cmat on 2009-03-09
What operating system did you use while accessing the USB? In what way are the file names mangled?

---

### Post by leg on 2009-03-09
> **cmat said:**
> What operating system did you use while accessing the USB? In what way are the file names mangled?This is while at work this morning on Windows XP service pack 2 and I have attached screen shots to show how the files are mangled.

---

### Post by cmat on 2009-03-09
Oh wow. I never seen that before. The files could possibly be recovered. Make the file names visible and see it the extension has been messed up to. Change it to what you think the file type is. I think it could be an issue with a unclean dismount. The file system's table is all messed up. I move stuff between Vista/XP and Ubuntu all the time, this could possibly affect me.

---

### Post by leg on 2009-03-09
> **cmat said:**
> Oh wow. I never seen that before. The files could possibly be recovered. Make the file names visible and see it the extension has been messed up to. Change it to what you think the file type is. I think it could be an issue with a unclean dismount. The file system's table is all messed up. I move stuff between Vista/XP and Ubuntu all the time, this could possibly affect me.Unclean dismount is a definite possibility as the remove usb devices thing does not always work here but it has never done this before.

---

### Post by cmat on 2009-03-09
Try to run a FSCK on the USB when you get home to correct errors. I'm not sure of any Windows utility that can do it.

More info... [http://ubuntuforums.org/showthread.php?t=458770](http://ubuntuforums.org/showthread.php?t=458770)

---

### Post by Toe on 2009-03-09
It could also be hardware failure.
I had something very similar happen shortly before a cheap USB stick died on me.

Try reformatting the stick. If these problems come back, the hardware is most likely faulty.

---

### Post by leg on 2009-03-09
> **cmat said:**
> Try to run a FSCK on the USB when you get home to correct errors. I'm not sure of any Windows utility that can do it.

More info... [http://ubuntuforums.org/showthread.php?t=458770](http://ubuntuforums.org/showthread.php?t=458770)Yes I have removed it at the moment and I will try to fix it when I get home.

---

### Post by leg on 2009-03-09
> **Toe said:**
> It could also be hardware failure.
I had something very similar happen shortly before a cheap USB stick died on me.

Try reformatting the stick. If these problems come back, the hardware is most likely faulty.I don't think this is the problem as I am using the stick quite happily but you never know.

---

### Post by cmat on 2009-03-09
I don't think it's a hardware failure since the directory structure is preserved and the device is still readable. When my USB stick was exposed to a magnet, you couldn't pull any data off it. The computer didn't even see it and I needed to go into gParted to format it.

---

### Post by leg on 2009-03-11
Ended up reformatting the stick and now it is working fine. Spoke to our IT guys and they have said that we have had a few USBCav viruses (?) hit us so it could have been that but it is still quite possible that dismounting incorrectly caused the issue. Of course it is also possible that those viruses caused the stick to be unable to unmount properly.

---

### Post by cmat on 2009-03-11
Good it was fixed. I hope you didn't lose anything too important. Also it's "viruses", people that say otherwise never studied latin.

---

### Post by sydbat on 2009-03-11
Most likely a virus or viruses. 

I had a similar problem when I was fixing my fathers computer (removing XP and installing Ubuntu) and saving his docs to a USB stick. He did have at least one virus on his XP install. There were extra files and folders on the USB stick that did not show up in XP as I moved them over (they only showed up in Ubuntu). All his important files were OK. After formatting the USB stick in Ubuntu, the stick has been fine.

To make sure it was not simply a corrupted file/folder, go through all the valid files you save to the stick and check them against the "corrupted" ones. If it is like the case I mentioned, there will be 'extra' files that are the corrupted ones and your real files should be fine. Then you can safely conclude it is some virus/malware.

---

