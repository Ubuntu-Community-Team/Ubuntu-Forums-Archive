---
title: "Using Ubuntu to cure Windows virus Infections"
date: 2010-05-24
forum: Security
---

### Post by byeutter on 2010-05-24
Greetings,
I have been looking through the forums here to find out if there is a virus scanner that can help me recover a badly infected windows system. It is completely dead. 
 
I ran my Ubuntu Live CD on the system in question and ClamAV found 70 some odd windows viruses. Looking on these forums it seems that the reason that Clam can not rid this system of viruses because it is not designed to remove viruses, only detect them. I tried the linux based AVG rescue disk only to have it tell me there are not viruses on the system. Can anyone recommend a virus scanner to use through Ubuntu that will be able to find and remove the viruses? 
 
Thanks in advance for your help.

---

### Post by cariboo on 2010-05-24
Clamscan can remove viruses, you just have to add the option when you run clamscan. Have a look at the clamscan [man]("http://linux.die.net/man/1/clamscan") page.

---

### Post by wilee-nilee on 2010-05-24
The address for the link is correct but not linking not sure why.
[http://linux.die.net/man/1/clamscan](http://linux.die.net/man/1/clamscan)

---

### Post by Ahava591 on 2010-05-25
If your system is that bad, I would recommend you simply wipe everything, start over and hope that temporarily works for you.
I say temporarily because if you use certain products made by certain companies, you are invariably going to be attacked and you are invariably going to fail in your efforts to blunt any attack. While it is true that open-source users are targets of criminal activity too, they are less vulnerable and tend to be able to patch their software quickly and fully.


I do not mean to be rude, and I mean this in sincere hope that you think about it, (and I in no way mean to suggest that my word is god.) The fact is, though, you appear to be wanting to use open-source software, which is assessed by many, many, many people who happen to be end-users, and who happen to probably not be making any money from the software in one way or another, to fix closed-source software, (and a bad attempt of it, at that,) for, again, the time being; i.e. until your efforts to protect yourself fail again, as they *will *do when using certain products.



That said, I hope you can fix your problems quickly.

---

### Post by HermanAB on 2010-05-25
You would be better served with BartPE (a bootable Windows CD):
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by OpSecShellshock on 2010-05-25
There are any number of live CD builds put out by AV vendors. Those have an advantage over the Ubuntu live CD in these cases because they're made specifically for the purpose of booting the computers and removing malware. There's a nice collection of links available here:

[http://krebsonsecurity.com/2010/03/removing-viruses-from-a-pc-that-wont-boot/](http://krebsonsecurity.com/2010/03/removing-viruses-from-a-pc-that-wont-boot/)

---

### Post by lisati on 2010-05-25
AVG have a free Linux-based rescue CD that you can download: [http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

---

### Post by jre6 on 2010-05-25
You may also install Wine and install and run a Windows antivirus.
To install Wine type in terminal:
sudo apt-get install wine
After installation type in terminal(this is necessary):
winecfg

However, all antiviruses may not work.

---

### Post by howefield on 2010-05-25
> **jre6 said:**
> You may also install Wine and install and run a Windows antivirus.

Why would you do that, and hope that you use one that does "work" when most anti virus applications have linux versions.

FWIW, I use a flash memory stick created with Startup Disc Creator, install Bitdefender and use that to disinfect windows machines. It's portable and obviously can be boot from.

But as others have said, there are many Live CDs that can be used, putting your hope in wine is probably the poorest option imho.

---

### Post by byeutter on 2010-05-25
> **Ahava591 said:**
> If your system is that bad, I would recommend you simply wipe everything, start over and hope that temporarily works for you.
I say temporarily because if you use certain products made by certain companies, you are invariably going to be attacked and you are invariably going to fail in your efforts to blunt any attack. While it is true that open-source users are targets of criminal activity too, they are less vulnerable and tend to be able to patch their software quickly and fully.
 
 
I do not mean to be rude, and I mean this in sincere hope that you think about it, (and I in no way mean to suggest that my word is god.) The fact is, though, you appear to be wanting to use open-source software, which is assessed by many, many, many people who happen to be end-users, and who happen to probably not be making any money from the software in one way or another, to fix closed-source software, (and a bad attempt of it, at that,) for, again, the time being; i.e. until your efforts to protect yourself fail again, as they *will *do when using certain products.
 
 
 
That said, I hope you can fix your problems quickly.
 
 
Thank You, and no you are not being rude. I thought about and decided to leave out an explanation as to why I have not just reimaged the machine with a Clean linux install when I originally posted. 
 
It is not my machine to do this to. If it was I would have done this immediately after I realized that the drive was not recoverable. However, I told the owner that I would try every last avenue. I would recommend Ubuntu to him but he needs to be able to run specific software that was created for non-linux based systems. 
 
I do appreciate _*everyone*_ who has responded. I have a lot of great ideas of which I will try one or two then reimage and move on. (told the owner that I would try what I could to recover his data. Three recovery disks later we will see what happens with number 4) That way I can spend the rest of the time on my own Ubuntu box!
 
I will check back in before I do the reimage to see if something earthshatteringly new gets posted that can revamp an OS prone to fail.
 
Thank You.

---

### Post by Ahava591 on 2010-05-26
Please let us know how it went with whatever options you tried; I'm interested to see how effective some of these things are.

---

