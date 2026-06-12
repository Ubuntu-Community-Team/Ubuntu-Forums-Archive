---
title: "Should i install Anti-virus on Ubuntu 10.04?"
date: 2010-10-09
forum: Security
---

### Post by SuperUserDO on 2010-10-09
hi,i have dual boot windows xp and Ubuntu 10.04 so i was wondering if it is necessary to install an anti-virus software?

---

### Post by FuturePilot on 2010-10-09
No.

Also, take a look at the Ubuntu Security sticky. Link in my sig for convenience.

---

### Post by Humanity to others on 2010-10-09
> **SuperUserDO said:**
> hi,i have dual boot windows xp and Ubuntu 10.04 so i was wondering if it is necessary to install an anti-virus software?

Ubuntu not required any anti-virus software - that is the advantage of Ubuntu/Linux

---

### Post by faisu on 2010-10-09
Install BitDefender Antivirus Scanner for Unices, Ubuntu 10.04/10.10			 						
		 				 		[URL="http://192.168.0.162/edp/index.php?view=article&id=59%3Abitdefender&tmpl=component&print=1&layout=default&page=&option=com_content&Itemid=41"]
[/URL]		 		 				 		[URL="http://192.168.0.162/edp/index.php?option=com_mailto&tmpl=component&link=aHR0cDovLzE5Mi4xNjguMC4xNjIvZWRwL2luZGV4LnBocD9vcHRpb249Y29tX2NvbnRlbnQmdmlldz1hcnRpY2xlJmlkPTU5OmJpdGRlZmVuZGVyJkl0ZW1pZD00MQ=="]
[/URL]		 					     	
       This quick tutorial will show you how to install BitDefender  Antivirus  Scanner in Ubuntu Lucid or Maverick. BitDefender lets you  scan your  systems for viruses and malicious programs. It supports both  Windows and  Linux systems, including Ubuntu. In this tutorial, I’ll  show you how to  install it in Ubuntu.
  
 **Getting started:**
  
 To get started, click [here]("http://www.bitdefender.com/site/Products/ScannerLicense/") to request a license key and download link.
 Once received, navigate to the appropriate ***.DEB package*** (64bit or 32bit) and download.
 After downloading, go to ***Applications –> Accessories –> Terminal*** and change to the correct directory, (usually ~/Downloads) and run the command below:
 [COLOR=#000000][FONT=Verdana] [/FONT][/COLOR]
 sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run  
 Next, type ***‘accept’ ***(without the quote) to agree to the license terms.\
  
 After the installation, go to ***Applications –> System Tools –> BitDefender Scanner.***
 ****
 ***The first thing to do is click on [B][I]‘Set new key’*** to enter the license key you received via email.[/I][/B]

---

### Post by rookcifer on 2010-10-09
> **faisu said:**
> Install BitDefender Antivirus Scanner for Unices, Ubuntu 10.04/10.10			 						
		 				 		[URL="http://192.168.0.162/edp/index.php?view=article&id=59%3Abitdefender&tmpl=component&print=1&layout=default&page=&option=com_content&Itemid=41"]
[/URL]		 		 				 		[URL="http://192.168.0.162/edp/index.php?option=com_mailto&tmpl=component&link=aHR0cDovLzE5Mi4xNjguMC4xNjIvZWRwL2luZGV4LnBocD9vcHRpb249Y29tX2NvbnRlbnQmdmlldz1hcnRpY2xlJmlkPTU5OmJpdGRlZmVuZGVyJkl0ZW1pZD00MQ=="]
[/URL]		 					     	
       This quick tutorial will show you how to install BitDefender  Antivirus  Scanner in Ubuntu Lucid or Maverick. BitDefender lets you  scan your  systems for viruses and malicious programs. It supports both  Windows and  Linux systems, including Ubuntu. In this tutorial, I’ll  show you how to  install it in Ubuntu.
  
 **Getting started:**
  
 To get started, click [here]("http://www.bitdefender.com/site/Products/ScannerLicense/") to request a license key and download link.
 Once received, navigate to the appropriate ***.DEB package*** (64bit or 32bit) and download.
 After downloading, go to ***Applications –> Accessories –> Terminal*** and change to the correct directory, (usually ~/Downloads) and run the command below:
 [COLOR=#000000][FONT=Verdana] [/FONT][/COLOR]
 sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run  
 Next, type ***‘accept’ ***(without the quote) to agree to the license terms.\
  
 After the installation, go to ***Applications –> System Tools –> BitDefender Scanner.***
 ****
 ***The first thing to do is click on [B][I]‘Set new key’*** to enter the license key you received via email.[/I][/B]

Totally unnecessary for a desktop machine.

---

### Post by SuperUserDO on 2010-10-09
well,for example if i have a usb flash drive which has an autorun virus and i copied it to my HDD in Ubuntu.i know that the virus wont do anything in Ubuntu,but will it affect my windows XP?:confused:

---

### Post by Humanity to others on 2010-10-09
> **SuperUserDO said:**
> well,for example if i have a usb flash drive which has an autorun virus and i copied it to my HDD in Ubuntu.i know that the virus wont do anything in Ubuntu,but will it affect my windows XP?:confused:

Xp Required Antivirus Software.But Ubuntu not required antivirus.

to save your Xp you can try antivirus in ubuntu 

Avast,Bit-defender, clam-av  etc. are providing anti-virus software for Ubuntu.

---

### Post by Velnias on 2010-10-09
> **SuperUserDO said:**
> well,for example if i have a usb flash drive which has an autorun virus and i copied it to my HDD in Ubuntu.i know that the virus wont do anything in Ubuntu,but will it affect my windows XP?:confused:

Windows viruses run only in working Windows. If some virus get copied to Ubuntu harddisk, it must be started from Windows, and Windows cannot see linux harddisks. So no chances...

PS But if you need infect Windows, then you can identify virus and copy it by hand to Windows autostart...

---

### Post by inobe on 2010-10-09
> **SuperUserDO said:**
> hi,i have dual boot windows xp and Ubuntu 10.04 so i was wondering if it is necessary to install an anti-virus software?

not necessary unless of course you run a server, i guess if you had a server you would already know this.

you could have an antivirus app to scan a windows/ dos machine connected to a linux server or a linux server itself.

---

### Post by tha-mee on 2010-10-09
If you want to protect Ubuntu, it doesn't matter whether you have one or not

If you want to protect friends who have a Windows PC
and you want to make sure you don't send a virus through, for example, an e-mail attachment,
I would recommend to get yourself a virus scanner...

---

### Post by jso2897 on 2010-10-09
I you are dual-booting with Windows, and your Win partition gets hosed to the point that it's not navigable, you can often fix it from the safety of your Linux partition, using tools like Avast (Linux version).
And, as another poster pointed out - you can make sure things are safe befor eyou pass them on to a Windows user.
Only two reasons I know of, unless you're running a server.

---

### Post by SuperUserDO on 2010-10-10
[SIZE="3"]Ok,if i installed an antivirus (Avast-Bitdefender) will it slow down the system like in windows?[/SIZE]

---

### Post by bodhi.zazen on 2010-10-10
> **SuperUserDO said:**
> [SIZE=3]Ok,if i installed an antivirus (Avast-Bitdefender) will it slow down the system like in windows?[/SIZE]

Of course it would slow you down. You would be using cpu cycles, disk space, RAM, etc to scan for viruses and as has been pointed out there are no known Linux viruses, so there is nothing to scan for.

With anything resembling modern hardware, with a fast CPU, sufficinet RAM, and sufficient disk space you will probably not notice such a performance hit, only the personal time loss you put into such an endevor.

Linux is not windows and antivirus is not rally a part of Linux security. If you are concerned with Linux security, read the security sticky and learn alternate tools such as linux permissions and apparmor.

Or to put it another way, I have been using using Linux, both as a desktop and a server, for longer then I care to mention (lets just say before Ubuntu 4.10 and leave it at that :twisted:) and I have NEVER seen a single linux virus.

So scan all you wish.

---

