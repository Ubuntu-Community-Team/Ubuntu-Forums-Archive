---
title: "Computer hangs on boot, root partition is read only"
date: 2012-05-18
forum: System76 Support
---

### Post by chez17 on 2012-05-18
I have a Gazelle (gazp6) running Ubuntu 11.10.

My computer was running perfectly with absolutely no issues. Everything on the computer is how the System76 driver installed it except I updated the Nvidia driver to the current (295 I think) driver. I did this update months ago and it has been working fine.

I have my system set up to use dual monitors by default. Two days ago I went on a trip and brought my computer with me. I booted it up and when I forget to change the configuration the system boots fine, but the mouse won't work for some reason (it can move horizontally along the top) until I get a terminal up and fix the monitor configuration through Nvidia's config tool (I do NOT do it manually). I've done this dozens of times with absolutely no problem. I did this exact thing and saved the X configuration so I wouldn't have to do it again. I use my computer no problem and shut it down. The next time I boot it up it hangs on the Ubuntu splash screen. I then try recovery mode and it boots to a limited recovery mode because the file system is read only. I can't update my xorg.conf file because the file system is read only. The system can't even start X from the terminal. Basically it's completely useless. I've read some things online and people said it could be a corrupted hard drive.  I don't think this is the case because I'm currently using my computer, it works fine if I boot to the Windows 7 partition. For the record, there was no Windows update between this so I'm 99.99% sure it has nothing to do with this. The only thing I can do is tell it to run fsck (or something like that, I forget what the option is) and it tells me something about how the system clock is off and it is now fixed. It tells me this every time I run that. I've tried selecting dpkg (or something like that) and it can't even run properly.

I don't know what to do. This is my work computer and I NEED it to work. The data is pretty much backed up but I still would need a couple things on there. I'd rather not reformat, so I'm asking people to suggest that as a last resort. I'm loss and have no idea what to do. I can't even try half the things people suggest because my partition is read only. I have no idea how it got that way. Any help is truly appreciated.

Thanks so much for your time.

---

### Post by isantop on 2012-05-18
> **chez17 said:**
> I have a Gazelle (gazp6) running Ubuntu 11.10.

My computer was running perfectly with absolutely no issues. Everything on the computer is how the System76 driver installed it except I updated the Nvidia driver to the current (295 I think) driver. I did this update months ago and it has been working fine.

I have my system set up to use dual monitors by default. Two days ago I went on a trip and brought my computer with me. I booted it up and when I forget to change the configuration the system boots fine, but the mouse won't work for some reason (it can move horizontally along the top) until I get a terminal up and fix the monitor configuration through Nvidia's config tool (I do NOT do it manually). I've done this dozens of times with absolutely no problem. I did this exact thing and saved the X configuration so I wouldn't have to do it again. I use my computer no problem and shut it down. The next time I boot it up it hangs on the Ubuntu splash screen. I then try recovery mode and it boots to a limited recovery mode because the file system is read only. I can't update my xorg.conf file because the file system is read only. The system can't even start X from the terminal. Basically it's completely useless. I've read some things online and people said it could be a corrupted hard drive.  I don't think this is the case because I'm currently using my computer, it works fine if I boot to the Windows 7 partition. For the record, there was no Windows update between this so I'm 99.99% sure it has nothing to do with this. The only thing I can do is tell it to run fsck (or something like that, I forget what the option is) and it tells me something about how the system clock is off and it is now fixed. It tells me this every time I run that. I've tried selecting dpkg (or something like that) and it can't even run properly.

I don't know what to do. This is my work computer and I NEED it to work. The data is pretty much backed up but I still would need a couple things on there. I'd rather not reformat, so I'm asking people to suggest that as a last resort. I'm loss and have no idea what to do. I can't even try half the things people suggest because my partition is read only. I have no idea how it got that way. Any help is truly appreciated.

Thanks so much for your time.

If you boot up from a LiveCD, then you'll be able to backup the files you haven't yet. From there, a reinstall sounds like the fastest, easiest, and safest option.

---

