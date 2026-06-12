---
title: "Kon-Boot allows login as root without password"
date: 2009-05-17
forum: Security
---

### Post by diafygi on 2009-05-17
I searched the forum for a discussion about [Kon-Boot]("http://www.piotrbania.com/all/kon-boot/") but turned up nothing. So, I figured there should at least be a discussion over whether or not this is a problem.

Does it work? How does it work? Anyone have a test machine to try this program? The source code is unavailable, so I'm not sure how it works.

Apparently, you just boot with Kon-boot, where it "change[s] contents of a linux kernel" and allows you to log in as "kon-usr". The kon-usr has root privileges. To remove the change, you log in again as "kon-fix".

It' sound pretty sketch, but I have no idea since the source code isn't available. I'm wouldn't recommend trying it out on anything but an non-networked test machine.

---

### Post by Dave_Connor on 2009-05-17
This attack can be done the same with booting from live cd and mounting the hardisk. This is also with alot of other risks with physical access to the computer is more likely to be stolen by robbery then someone breaking into your house just to get into your computer would be pretty pointless. But I am also curious about this kon-boot software as well.

---

### Post by antemon on 2009-05-18
I'm more interested in that it can change the password of a windows machine.

good for sysadmins and people with terrible memory. bad for almost everyone else who leaves their computer for five minutes.


then again, there are tools like this for windows already floating around - with other diagnostic stuffs included too

---

### Post by sandwich88 on 2010-06-22
I can verify that this does work for Windows Vista and Windows 7. I am going to try it on my Ubuntu 10.04 machine tonight.

---

### Post by CharlesA on 2010-06-22
They stopped development on the version that works with Linux and it's now a tool for password recovery on Windows only.

---

### Post by tgm4883 on 2011-05-07
> **bkerensa said:**
> I had been wondering about this software but the most recent 2600 seems to indicate this will still work with ease on Ubuntu.

So basically even with a encrypted /home you are pretty much screwed if someone uses this.

Benjamin! Hi buddy.


Not sure how this would affect an encrypted /home directory. Even if you reset the user password you still wouldn't have the decryption (encryption) key as you can't reset that.

---

