---
title: "Is there any danger if an windows infected pendrive is used in ubuntu?"
date: 2011-11-15
forum: Security
---

### Post by arroy_0209 on 2011-11-15
I inserted my pendrive (flashdrive) in an windowsXP machine and later inserted the same in my ubuntu os machine. There was a new folder which I am sure I had not saved in the pendrive. It seems that the pendrive got infected in the windows machine. Is there any danger to my ubuntu system due to this? (I didnot open the folder). What should one do in such a case?

In general, what are the possible effects of using an infected pendrive in ubuntu? It appears many people will face such problem at times. After all we have to share files/folders with windows machine at times. Are there any precautions to take?

---

### Post by TBABill on 2011-11-15
Only danger is if you share an infected file with a Windows user (via email, copying to external drive, etc.) The executable file itself is not harmful to Ubuntu because it cannot natively run within it.

---

### Post by kurt18947 on 2011-11-15
> **TBABill said:**
> Only danger is if you share an infected file with a Windows user (via email, copying to external drive, etc.) The executable file itself is not harmful to Ubuntu because it cannot natively run within it.

Or if using WINE or its variants?

---

### Post by BHEJU on 2011-11-15
Each OS (win and linux) will create a folder each. So, your drive might not be infected. What is the folder called?

---

### Post by iavor on 2011-11-16
Similar thing happened to me once while I was repairing a friend's computer, I had to transfer a few files to his pc using usb drive.
I did not notice it until I was back home.. when i saw 2 files, I then scanned them with clamav and both were infected.

Now back to your question, you wont get infected by a windows virus. You can simply delete the folder and be done with it.

---

### Post by arroy_0209 on 2011-11-16
Thanks for your replies.

I have not checked the folder again but I am sure this is not system generated. In fact I have not used the pendrive in my own computer after that. I am planning to format it but there are two/three important files which I need. Undecided.

Another related question: when a new pendrive is used in windows, often a file named autorun.inf appears. In case this is deleted, this reappears next time. Should I worry about this file? Does it have any function in ubuntu operating system? (Once my windows antivirus detected this file as virus.)

---

### Post by iavor on 2011-11-16
The two files i had were: s1.exe and autorun.ini
the virus is the .exe file while the .ini is the one that executes given command automatically in my case open the virus file.

My suggestion is run clamav scan on your device, delete the infected files and you're done. If you want to be aboslutely sure format the whole usb drive :)

> **arroy_0209 said:**
> Does it have any function in ubuntu operating system?

You should read what TBABill said, second post.

---

