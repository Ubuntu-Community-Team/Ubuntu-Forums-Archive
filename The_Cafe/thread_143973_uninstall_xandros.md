---
title: "uninstall xandros???"
date: 2006-03-13
forum: The Cafe
---

### Post by wiffall on 2006-03-13
Does anybody know how I can uninstall xandros and the lilo???
Lilo has messed up my harddrive on another system.:rolleyes:  
Seems that nobody @ xandros forum knows anything or they just wont tell [-( . 
Im waiting for my ubuntu disk to come in the mail (hopfully today) \\:D/ .
 Maybe i'll have better luck here at ubuntu, :-k  im about ready to give up on linux. :-?
thanks, wiffall :)
[email]wiffalls@aol.com[/email]

---

### Post by aysiu on 2006-03-13
Just install Ubuntu (when you get it) and select "Erase Entire Hard Drive." Then when asked if you want to install Grub to the MBR, say "yes."

---

### Post by Alpha_toxic on 2006-03-13
Of course if you are trying to double boot with Windows XP (or some other OS), you should just format the partition where Xandros was (this is done using the Ubuntu install disk), install Ubuntu there and again say "yes" when asked about GRUB and the MBR.

P.S uninstalling an OS is easy, just format the partition where it is, but removing the boot loader (Lilo, GRUB, windowse's loader <don't remember the name> etc.) is imposible (perhaps you can delete it, but then you can't boot from that HDD). You can only swap one loader for another. By installing Ubuntu it will replace Xandros' loader with its oun. Every linux OS has the means to change/edit the loader at any time. The problem is that Windows does not... AFAIK at least. It is only set up at install and not edited any more. So it's gonna be dificult ot completely remove linux from your system. Of course reinstalling windows will do the trick, but you don't want to do that, don't you?

---

### Post by commodore on 2006-03-13
Too bad you used Xandros in the first place. Xandros is a Windows-Linux (they try to make Windows out of Linux).

---

### Post by Steve1961 on 2006-03-13
[QUOTE=wiffall]Does anybody know how I can uninstall xandros and the lilo???
Lilo has messed up my harddrive on another system.:rolleyes:  
Seems that nobody @ xandros forum knows anything or they just wont tell [-( . 
Im waiting for my ubuntu disk to come in the mail (hopfully today) \\:D/ .
 Maybe i'll have better luck here at ubuntu, :-k  im about ready to give up on linux. :-?
thanks, wiffall :)
[email]wiffalls@aol.com[/email][/QUOTE]


Xandros was my first linux as well about 18 months ago.  Lasted about 2 weeks on my hard disk before the updates trashed the system completely. Don't judge linux by Xandros, Ubuntu is a completely different (and far better) experience.

---

### Post by LinuxSwede2 on 2006-03-13
[QUOTE=aysiu]Just install Ubuntu (when you get it) and select "Erase Entire Hard Drive." Then when asked if you want to install Grub to the MBR, say "yes."[/QUOTE]

This man speaks of the truth, Lilo is in the MBR, installing Grub will replace it, of course, if you really wanted to, you could use Lilo instead of Grub, in some ways it's a better choice, in some ways it's not as good.

---

### Post by LinuxSwede2 on 2006-03-13
[QUOTE=commodore]Too bad you used Xandros in the first place. Xandros is a Windows-Linux (they try to make Windows out of Linux).[/QUOTE]

I'm curious here, what do you mean, how does Xandros try to make windows out of linux in a way that other "easy to use" linux distros such as Mandriva or ubuntu doesn't?

---

### Post by Sef on 2006-03-13
Xandros worked fine for me.  It would be fine as a first Linux distro.  (Was second one for me to install.)  My main issue with it were it was a KDE desktop, and I prefer Gnome.

---

### Post by wiffall on 2006-03-14
Thank You for all the replies.
Let me explain a little. :confused: 
I installed xandros on my slave drive, lilo entered my mbr on my master drive.
Now I keep getting errors about disk0 is working outside it specs.
Press F1 to continue. Then I get lilo... 
So can anyone tell how to fix this on windows 2000 pro. All the info I've found so far doesn't work on win2000. I cant seem to get into repair console either. :cry:

---

### Post by Alpha_toxic on 2006-03-14
[QUOTE=wiffall]Thank You for all the replies.
Let me explain a little. :confused: 
I installed xandros on my slave drive, lilo entered my mbr on my master drive.
Now I keep getting errors about disk0 is working outside it specs.
Press F1 to continue. Then I get lilo... 
So can anyone tell how to fix this on windows 2000 pro. All the info I've found so far doesn't work on win2000. I cant seem to get into repair console either. :cry:[/QUOTE]
I know one (tested by me and working) way to repair this, but it's UGLY. Reinstalling Windows in repair mode will install its loader in the MBR and will keep all your data on the drive without deleting it. The problem is it will also make a repair sewap through the registry and it's posible that some of your programs will also need reinstallation after this.
One more option is to intall GRUB or Lilo on a floppy and booting from it, but this is not very convenient.
My guess is that in the rapair console of the Windows CD there is a command to reinstall the loader, but I've never done that, so I can't help here. Perhaps you should try asking about that in some windows related forum. Someone might just know an easy way to repair its loader.
Good luck, I hope everything works by the time you get your Ubuntu CD ;)

---

### Post by Steve1961 on 2006-03-14
To fix your mbr just boot your machine with the windows disc.  I haven't used 2000 but in xp you get an option to enter the repair console.  If so, use this and once there type fixmbr.

Here's the MS instructions:

[http://www.microsoft.com/resources/documentation/Windows/2000/server/reskit/en-us/Default.asp?url=/resources/documentation/Windows/2000/server/reskit/en-us/prork/prcb_dis_dgya.asp](http://www.microsoft.com/resources/documentation/Windows/2000/server/reskit/en-us/Default.asp?url=/resources/documentation/Windows/2000/server/reskit/en-us/prork/prcb_dis_dgya.asp)

---

