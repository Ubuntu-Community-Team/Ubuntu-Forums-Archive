---
title: "Can scnaner work on ubuntu 21.04 ???"
date: 2021-03-09
forum: Ubuntu Development Version
---

### Post by hoboy on 2021-03-09
I have hp envy_4500 series printer works fine 
but scanner giving error unable to connect to scanner

Thanks

---

### Post by TheFu on 2021-03-11
21.04 hasn't been released, so the only answer is maybe.  
Does it work on 20.04 or 20.10?

---

### Post by iamjiwjr on 2021-03-12
In case you think about buying another scanner, fyi Brother scanners don't work in the current Ubuntu editions.

---

### Post by coffeecat on 2021-03-12
> **iamjiwjr said:**
> Brother scanners don't work in the current Ubuntu editions.

That's a very broad and sweeping statement. How many Brother scanners and how many different Brother models have you tested yourself? Or are you citing other sources? What exactly do you mean by "current Ubuntu editions". All in-support releases or only some of them?

---

### Post by ajgreeny on 2021-03-12
I have just booted up my virtual install of Xubuntu 21.04 on KVM/QEMU and I had no problems at all either printing or scanning using my HP Envy 4527, the same series as you use.
Both xsane and Document scanner worked without a problem so I am surprised that you have a problem with that printer/scanner.

I do have hplip installed (it's there by default in Xubuntu) but I am not sure if it is actually required to get the printer or scanner working but it's perhaps worth checking if you have it installed.

I can not comment on Brother printers as I have not had one for about 10 years, but even then it worked fine once the drivers were installed direct from Brother's website, and from what other users have said it seems that Brother machines usually are good to go with Ubuntu.

---

### Post by kurt18947 on 2021-03-13
> **ajgreeny said:**
> 
I can not comment on Brother printers as I have not had one for about 10 years, but even then it worked fine once the drivers were installed direct from Brother's website, and from what other users have said it seems that Brother machines usually are good to go with Ubuntu.

When 20.04 was in development, my Brother scanner didn't start working until very shortly before or perhaps just after 20.04 release. Brother's installer had a habit of copying files to */lib64 when they should have been copied to *. */lib. Brother's linux FAQ had information on the subject. I certainly wouldn't plan on Brother scanners working in pre-release versions. There may or may not be useful info here:

[https://support.brother.com/g/b/faqlist.aspx?c=us&lang=en&prod=mfc5460cn_all&ftype3=100258](https://support.brother.com/g/b/faqlist.aspx?c=us&lang=en&prod=mfc5460cn_all&ftype3=100258)

One thing about Brother Linux support is they have answers for *old* distros. For instance none of the pre-install steps have been required for years. I've had excellent success just using their installer script but others may not.

---

### Post by VMC on 2021-03-13
> **hoboy said:**
> I have hp envy_4500 series printer works fine 
but scanner giving error unable to connect to scanner

Thanks

What does ```
scanimage -L
``` show? Does it see you scanner?

---

### Post by iamjiwjr on 2021-03-16
Brother scanners are a simple two step process for all other new distros I've tried. Manjaro, openSUSE, Fedora, Solus, Debian, Linux Mint (as of their latest release), Deepin, etc - all easy and simple. But Ubuntu based distros (with the exception of Mint) ALL will not install Brother scanners. Ubuntu's denial of this Ubuntu problem goes on and on and on. I'd like to come home to Ubuntu but cannot as long as this mess continues.

---

### Post by kurt18947 on 2021-03-29
> **iamjiwjr said:**
> Brother scanners are a simple two step process for all other new distros I've tried. Manjaro, openSUSE, Fedora, Solus, Debian, Linux Mint (as of their latest release), Deepin, etc - all easy and simple. But Ubuntu based distros (with the exception of Mint) ALL will not install Brother scanners. Ubuntu's denial of this Ubuntu problem goes on and on and on. I'd like to come home to Ubuntu but cannot as long as this mess continues.

I've been able to install and use Brother scanners on every Ubuntu LTS  I've tried. I usually just use the installer script. One thing I do which may or may not matter is to assign a static I.P. address to my multifunction machines. I then run the installer, it may or may not pick up the proper I.P. address. If it doesn't I set it manually. I use the utility system-config-printer which seems to be installed by default in gnome distros. I set the device URI to socket://123.456.789:9100 and it works. Part of the installer script is a single line telling the scanner software where to find the scanner and what it's called. The line is documented in Brother's scanner driver install directions as well.

---

### Post by iamjiwjr on 2021-03-30
> **kurt18947 said:**
> I've been able to install and use Brother scanners on every Ubuntu LTS  I've tried. I usually just use the installer script. One thing I do which may or may not matter is to assign a static I.P. address to my multifunction machines. I then run the installer, it may or may not pick up the proper I.P. address. If it doesn't I set it manually. I use the utility system-config-printer which seems to be installed by default in gnome distros. I set the device URI to socket://123.456.789:9100 and it works. Part of the installer script is a single line telling the scanner software where to find the scanner and what it's called. The line is documented in Brother's scanner driver install directions as well.

Thanks. I'll try that.

---

### Post by ajgreeny on 2021-03-30
To avoid printing problems if using wireless connections i believe it's essential to use a static  IP address for the printer, usually easy to setup in the router's own setup, using the Reserved addresses utility.

---

### Post by funicorn on 2021-04-05
Try hplip-gui. It may help connect to the scanner.

---

### Post by kurt18947 on 2021-04-09
> **ajgreeny said:**
> To avoid printing problems if using wireless connections i believe it's essential to use a static  IP address for the printer, usually easy to setup in the router's own setup, using the Reserved addresses utility.

I don't know about essential but I've certainly had better luck setting static I.P. addresses on hardware. Before I did this I'd get "printer not found" or similar error messages too frequently.

---

