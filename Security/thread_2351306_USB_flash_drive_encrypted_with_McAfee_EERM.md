---
title: "USB flash drive encrypted with McAfee EERM"
date: 2017-02-01
forum: Security
---

### Post by sgstiffler on 2017-02-01
I have a USB flash drive encrypted with McAfee EERM. Can I set it up so that when I plug it into my Ubuntu Linux PC I can type in the password and save or unload files to the USB drive?  The only thing I have on there are PDF files.

I am a newbie to Ubuntu :D

---

### Post by DuckHook on 2017-02-01
Welcome to the forums, sgstiffler.

AFAIK, McAfee EERM is a windows-only product with no support for Linux. You may be able to run Windows in a VM with a USB port mapped to Windows and access it that way. For all I know, WINE might work too. But there is no native Linux app to work with it, so you might as well consider it locked into Windows.

---

### Post by sgstiffler on 2017-02-01
Well, I have installed WINE. I can execute the .exe file. I can type in my password. I can see my folders and files on the USB drive. But I can't write to the drive.

---

### Post by lisati on 2017-02-01
Did you remember to "safely remove" the USB from Windows?

---

### Post by DuckHook on 2017-02-01
Can't help you any further there. It was a long shot. WINE is not Windows. It is frankly an incredible feat of reverse engineering, clean room reinvention and sheer cussed brilliance, but in the end it is still half-man-half-horse. It mimics Windows libraries and functions, but cannot replace them. I imagine that a security app like the one running EERM would be highly sensitive to even small differences.

If you like, post a separate thread on the WINE subforum asking the gurus there for help. Also, check the WINE app database for whatever app the EERM is called.

Last but not least, can you run a Windows VM? That will likely prove to be your most trouble-free solution.

---

### Post by sgstiffler on 2017-02-01
I did an eject of the USB drive.

---

