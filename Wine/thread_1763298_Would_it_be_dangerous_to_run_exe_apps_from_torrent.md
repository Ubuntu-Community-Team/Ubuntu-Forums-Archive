---
title: "Would it be dangerous to run exe apps from torrent?"
date: 2011-05-20
forum: Wine
---

### Post by eb3ha4el on 2011-05-20
Hi


I use torrent to download some of the applications I used to run in win7. Problem is I'm little worried since back then I had few security software like security essentials. 

It seems I dont have any security software installed in Ubuntu so I cannot inspect files before running them with WINE. The source of file is absolutely cannot be trusted - ex) TPB.


would the virus or any kind of malware would work on my system when running them with WINE? If so, is there lightweight security software recommendable?


thanks.

---

### Post by IWantFroyo on 2011-05-20
It wouldn't be able to harm your computer. If its in an .exe file, then if there are any viruses, they are targeted at a Windows computer.

I'm not so sure about what it might do to WINE though. Never tested this.

---

### Post by Nerotriple6 on 2011-05-20
Bitdefender [http://www.bitdefender.com/world/business/antivirus-for-unices.html](http://www.bitdefender.com/world/business/antivirus-for-unices.html)

---

### Post by mikewhatever on 2011-05-20
Yes, Windows malware may work in Wine. Download programs only from the repositories or other trusted sources.

---

### Post by Paqman on 2011-05-20
Generally running executables of any kind from a torrent is not a good idea, unless you can confirm that it's not been modified. For that you'd need to know the correct MD5/SHA1 hash for the original.

Having said that, Wine within a Linux environment is safer than running it in Windows, but it's not inconceivable that it could create some degree of mischief, even if it was confined to your home folder.

Do you really, really need to be executing this thing though? Get it from a legit source and you won't have to worry.

---

### Post by eb3ha4el on 2011-05-20
Right...
hmmmmm....

oh and thanks for bitdefender. though it's not free...
I think i might install security essentials and run it with WINE...

---

### Post by Nerotriple6 on 2011-05-20
Bitdefender is free for Unices.

[http://www.bitdefender.com/world/Products/ScannerLicense/](http://www.bitdefender.com/world/Products/ScannerLicense/)

Sorry, I could have mentioned that link..

---

### Post by philinux on 2011-05-20
Moved to Wine forum.

Running untrusted software of any description is just a bad idea.

---

### Post by eb3ha4el on 2011-05-20
Thanks Nerotriple!

---

### Post by eb3ha4el on 2011-05-20
Can't manage bitdefender to get installed..
I downloaded BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
but having difficulty to install it.

Am using ubuntu 11.04 on Netbook.

Any help please?




Following this guideline, Terminal does not show anything..
[https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)



p.s this method worked for me.. 


```
chmod +x BitDefender-*
```

```
./Bitdefender-*
```



hope it helps for others.

---

