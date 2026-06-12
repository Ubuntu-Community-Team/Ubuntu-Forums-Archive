---
title: "Microsoft shouldn't be telling me I can't do something...."
date: 2006-04-29
forum: The Cafe
---

### Post by Destiny on 2006-04-29
I have recently bought windows XP I was seriously denying the purchase for awhile now and then I found out why... I have a friend who has windows 2003 office, he is an admin and it was a company copy so he let me install it for use with the Windows XP I purchased. Well it was cool and looked like AOL on Crack but I decided I would leave it for awhile and see what I could do with it. Well someone sent me a stupid little card for my birthday and I couldn't open it in Microsoft’s Nazi invaded outlook. The stupid program blocks it without a say so from you and you CAN'T get passed it. ](*,) I am so infuriated I have decided to look into Linux as my new OS. I realize this is like teaching a baby to walk, because I am a HARD core windows junky. But Bill Gates has gone too far with babysitting ME. I am not stupid I know about viruses and I also know when to open and when not to, how dare he think and his developers to that they have a right to block my stuff from displaying. Sorry ranting here... Anyway there is a question in all of this. I want to learn on a laptop that I currently have how to use Linux before switching completely. My question is...ARE you ready?..No not that question this one.:) How do I start? Hard question I am not sure.. I mean do I completely uninstall windows and use the ubuntu install disk; does WINDOWS have to be on there? Just point me where to go I am not afraid to read. Windows user in need of help please.;).

---

### Post by Sef on 2006-04-29
If you want to dual boot you can, and since you are just starting off, I would recommend it.  To read up on dual boot, read this tutorial:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

Brezzy 5.10 is the current stable.  Dapper is the current Beta; it is scheduled to become stable on 1 June 2006.

---

### Post by cledezma on 2006-04-29
I would recommend you to try the Live CDfirst. That will allow you to try Ubuntu without changing your computer. See [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by aysiu on 2006-04-29
Start by reading this:

[http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)

---

### Post by s|k on 2006-04-29
[QUOTE=Destiny] Well someone sent me a stupid little card for my birthday and I couldn't open it in Microsoft’s Nazi invaded outlook. The stupid program blocks it without a say so from you and you CAN'T get passed it.[/QUOTE]
Most likely the card was an .exe or someother such extension. You can go into Outlook's options and tell it to allow all those extensions, but they are enabled by default for your safety. Having those extensions blocked prevent malicious code from someone using your computer to do malicous things.

---

### Post by aysiu on 2006-04-29
You could also use Thunderbird instead of Outlook.

Incidentally, you may not like Ubuntu either, as it tells you you can't do certain things (like copy a file to /usr/share/wallpapers) unless you take advantage of your *sudo* privileges. Read more here:

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by gingermark on 2006-04-29
In addition to that advice, I would forget what you know about installing software. I don't want to jump the gun, but it's simply an area that many Windows "power" users have trouble getting their heads around.

I myself found it difficult to grasp, or at the very least just strange, when I started. But computing with Ubuntu is a very enjoyable experience, and this community is great.

Welcome.

---

### Post by aysiu on 2006-04-29
[QUOTE=gingermark]In addition to that advice, I would forget what you know about installing software. I don't want to jump the gun, but it's simply an area that many Windows "power" users have trouble getting their heads around.[/QUOTE] Yes, expect culture shock.

This is a pretty good explanation with screenshots:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

This is my explanation without screenshots:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Keep in mind--Ubuntu is a wonderful operating system, but it is not Windows without problems. It's not Windows at all. You know how Apple's motto is *Think Different* (which really should be either *Think Differently* or *Think "Different"*)? Ubuntu is even more "different" than Mac OS X is from Windows.

---

### Post by blastus on 2006-04-29
Some concepts you may want to learn first include...

- hard drive partitions in general
- dual booting, GRUB and MBR (learn about the /boot/grub/menu.lst file)
- the Linux File System Standard
- how to use a terminal, type in commands, and some basic commands like ls, rm, etc...
- mounting/unmounting file systems (learn about the /etc/fstab file)
- the ext3 file system and how permissions work (learn about the chown and chmod commands)
- installing/uninstalling software with the apt package management system
- what X Windows is and how to configure it (learn about the /etc/X11/xorg.conf file)
- how to use GNOME (Ubuntu) or KDE (Kubuntu)

With determination and patience, you *can* migrate to Linux. Lots of people, including myself have! :) Some of us have experienced enormous challenges getting some stuff to work, but the key is persistence and patience. Familiarity with any new OS won't come overnight.

Sometimes you may find yourself having to learn a whole set of concepts just so that you can understand how to solve a problem. For example, I had to learn about GCC, kernel modules, kernel headers, and device files in order to get my modem to work under Linux. For example, if I install a different kernel I have to recompile my modem driver, but I know why I have to do it and I know how to do it.

One other thing, don't expect Linux to be *like* Windows. Linux is not Windows, and many things are done differently. If you are considering migrating to Linux, start looking at some of the applications that you can use on both Linux and Windows. For example, Firefox, Thunderbird, and OpenOffice.org, function more or less the same on both Windows and Linux. So if you know how to use them on Windows, you basically know how to use them on Linux. Cross platform programs like these can significantly aid in migrating to Linux--it did for me.

---

### Post by briancurtin on 2006-04-29
my recommendation in this thread would be to just learn how to use outlook before looking to switch to linux. i love linux like the next person on this site, but moving to linux because of this isnt totally necessary at this point, from what i gathered.

---

### Post by Destiny on 2006-04-30
As far as enabling the .exe files you can't. BELIEVE me I have tried. Here is a post by General Manager William Kennedy Outlook Product development. [http://office.microsoft.com/en-us/assistance/HA011894211033.aspx](http://office.microsoft.com/en-us/assistance/HA011894211033.aspx) 

>  By now most of you are painfully aware that Outlook does not allow you to receive attachments from certain files that have the potential to carry a virus to your computer, such as an .exe file.

That is just the openeing line of a bunch of hooey:(

I will take all the suggestions and I apprecite them. As to the commands someof them are very similar to commands used in MUSH code and MUX ..and I didn't know anything about those when I started playing RP games that are text based. I am not scared to "*Think Differently*" and I do think that all people should always try to learn something new. This will just be a new chapter in a long time of computer use and growing.

---

### Post by blastus on 2006-04-30
Unbelievable, this is probably the most asinine thing I've heard of. The author even goes so far as to suggest a method for circumventing sending .exe files, that is to rename the file. Now that's real smart. It's not like malware authors haven't been doing that since the dawn of time. It seems to me that Microsoft is afraid that they can't prevent Outlook from AUTOMAGICALLY EXECUTING attachments, so their solution is to permanently disable the user from receiving them at all.

I believe Outlook (and Outlook Express) uses an undocumented proprietary binary file format to store email messages and an undocumented proprietary protocol to communicate with Exchange servers. I'd dump Outlook if I were you. Get your email messages into an email client, such as Thunderbird, that uses the standard mbox plain text file format to store messages. Your data is then not locked in a proprietary file format that only Microsoft fully understands. Switching to an email client like Thunderbird would also help facilitate migrating to Linux in the future as it is fairly easy to move your email messages from a Windows Thunderbird profile to Linux Thunderbird profile.

---

