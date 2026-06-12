---
title: "Fossa and Brother Scanners"
date: 2020-04-02
forum: Ubuntu Development Version
---

### Post by kurt18947 on 2020-04-02
Fossa is looking pretty polished to me with one exception - my Brother scanner didn't work. The printer was fine, the networked scanner was not. The installer script ran without error or issue but no scanner found.  Some time searching found this:

```
https://unix.stackexchange.com/questions/493042/brother-scanner-not-found-in-xsane
```

>  Finally found the issue. Some symbolic links was missing. Created the links with:

  sudo ln -sfr /usr/lib64/libbrscandec* /usr/lib/x86_64-linux-gnu

sudo ln -sfr /usr/lib64/sane/libsane-brother* /usr/lib/x86_64-linux-gnu/sane
  Fixed the problem
     


Copy/Pasted the 2 lines one at a time in a terminal. The fix worked for me on a couple different machines. I haven't reported the issue to Brother yet but will do so.

---

### Post by kurt18947 on 2020-04-18
Update. I just did a fresh install of 20.04 Beta with updates. I asked the installer to format the partition with the previous install. The Brother scanner is not found. I guess it's wait until 20.04 is released plus a couple weeks then bother Brother. I wondered about it being a PC motherboard/chipset problem but I did a full install of 20.04 on a USB flash drive plugged into the same PC. The scanner is found, no problem.

---

### Post by Irihapeti on 2020-04-18
Thanks for the information. I have a Brother printer/scanner (DCP-1610W) which I've been able to get to work on 20.04, without needing hours of hair-tearing.

libbrscandec* doesn't/don't exist in 20.04 - at least, not on any of the installs that I've done. Therefore, I've needed only the second command.

---

### Post by inundated on 2020-04-19
I do eventually need to find out if a Brother scanner will work on 20.04, but due to the current world situation, I won't need to use that with Ubuntu for some time.

I am happy to report that 20.04 does enable the scanning function of my Canon TS3322. It was discovered instantly and works great.

---

### Post by mIk3_08 on 2020-04-19
I also have Brother printer/scanner. I am able to work both printer/scanner on my ubuntu 18.04 thru wireless network communication. My scanner works well on "simple scan" and "Xsane". I just updated the brsanetdevice file and added the name, ip, and model of my printer and save it.

---

### Post by kurt18947 on 2020-05-02
Brother scanner is working on 20.04 as expected. It started working right around the release date. The issue was, I think something to do with the hardware on my primary machine though I'm not sure what.

---

### Post by slickymaster on 2020-05-02
> **kurt18947 said:**
> Brother scanner is working on 20.04 as expected. It started working right around the release date. The issue was, I think something to do with the hardware on my primary machine though I'm not sure what.
With this and since Focal is released I'm closing this thread.

---

