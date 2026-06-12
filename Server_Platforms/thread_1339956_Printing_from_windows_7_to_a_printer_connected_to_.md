---
title: "Printing from windows 7 to a printer connected to Ubuntu 9.10 server"
date: 2009-11-28
forum: Server Platforms
---

### Post by pulledteeth on 2009-11-28
So, I am attempting to print from windows 7 to a printer attached to a Ubuntu 9.10 server machine. I've got samba up and running, and can access the shares. For whatever reason, when I attempt to connect to the printer, in order to install it it says that it can't connect.

Samba version is 3.4.0

---

### Post by Vegan on 2009-11-28
Is the printer working from inside Linux?

Make sure its operating, then you can share it fine.

---

### Post by Spiritof76 on 2009-11-28
Make sure after any changes to cups and smb.config you reboot or restart samba.

---

### Post by hidesertmlb on 2009-11-28
Having the same issues also, with my Windows 7 machine accessing the Ubuntu 9.10 machine that's sharing the printer. Windows 7 machine can see folders that are shared via Samba, but when I go to connect to the printer that is listed, I get an error dialog on the Win7 machine: "Windows cannot connect to the printer".

I have the print settings in CUPS as follows
- Publish shared printers connected to this system
- Show printers shared by other systems

:confused:

---

### Post by pulledteeth on 2009-11-28
The printer is working from inside the server; and I can even print over the network using Kubuntu 9.10 on my laptop. I just can't print from any windows machines for some reason.

---

### Post by hidesertmlb on 2009-11-28
Got it working via CUPS. Here's what I had to do:

1- in /etc/samba/smb.conf  ensure the following was uncommented in the PRINTING section in [global]

load printers = yes
printing = cups
printcap name = cups

added the following to [printers]

use client driver = Yes

2- restarted samba: sudo /etc/init.d/samba restart

On the Win7 client

- Add a printer->Networked printer
- for the location, specified the printer via CUPS http. So in the location box, where UBUNTU is the hostname of the printer that's shared, and the shared name of my printer (Epson C120)

[http://ubuntu:631/printers/Epson_C120](http://ubuntu:631/printers/Epson_C120)

You can determine the shared name of your CUPS printer by going to your UBUNTU host that's sharing the printer, specifying the following URL:
[http://localhost:631](http://localhost:631)

Go to the PRINTERS tab, point to the queue name of the queue name of the printer that's shared, rt-click and display properties. This is the URL that will be used on your Win7 printer location, except "localhost" will be replaced with the hostname of your ubuntu host (in my case, "ubuntu").

- specify print driver to use on your Win7 machine and print a test page  


At least this is what worked for me. HTH

---

### Post by stults on 2009-12-10
This worked for me as well.  I don't really like the setup on the windows side, especially if I had to set this up for a client.  But, for me this will have to work until it gets a real fix in samba.  Thanks!

---

### Post by Silvertones on 2010-04-06
I'm having a heck of a time with this as well. Samba file sharing works fine however I do seem to have to jump through a little hoop. This may or may not be normal.
Ubuntu Lappy with printer attached. Prints fine every time.
If I try to print from the XP machine the little printe icon shows up as if it's trying to print to the XP machine. What sometimes works is first I connect to the windows file shares from ubuntu. Then I connect to the ubuntu shares from XP. The I do the add printer thing in the XP machine even though it's already installed. I have it search. When it finds it it jumps to the last screen to set as default. It'll then print. At some point during the day it'll loose its connection and then the XP machine can't find the ubuntu printer. This process is not consistent. Sometimes even on reboot the XP machine can't find the ubuntu printer. I've done all of the necessary things to smb.conf. I've tried to use the URL method of adding the printer but always get an error.I have HP toolbox installed as well and that didn't  help.
The printer is an HP 712C on LPT1
If I try to use the HP Device magr it says "no devices found"

---

### Post by puredoxyk on 2010-06-07
FYI, I did finally get this to work (Ubuntu 10 / Windows 7), but only if I used the IP address of the localhost in that URL -- using the name of the machine gave a consistent "not found" error.

No idea why, but glad it finally works!  Thanks!

---

### Post by tlois on 2010-08-14
Thanks, Hidesert!!!!   I didn't even have to complete the restart Samba part.

---

### Post by alexnicol on 2010-10-21
Apologies for digging up an old thread, but I'm still struggling with this.

Printer works fine in Locally

Printer works fine when printing from SBS2k3

Printer doesnt work when printing from Windows 7

I would have assumed that if it is working from SBS2k3 then it should be working from 7, unless its a domain thing maybe?

Any help greatly appreciated.

Regards

Alex

---

### Post by Silvertones on 2010-10-21
I haven't done anything other then upgrade to 10.04 and do all updates.
My printer works fine now. No hoops to jump through.

---

### Post by Nick_NS on 2010-11-14
I am having this same issue. I have several machines set up.

[LIST]
[*]A desktop running Ubuntu 10.10 (had the same issues with 10.04) which samba is running to share files and the printer. The printer works fine locally.

[*]One laptop running Windows XP. File access and printing works fine through samba (not the IPP workaround).

[*]One laptop running Ubuntu 10.10. This accesses the samba shares without issue, I have not attempted to add the printer via samba but it works using CUPS.

[*]One netbook running Windows 7 x86. File access and printing via samba works without issue.

[*]Two laptops running Windows 7 x64. Both of these machines can see and access the shared files. But get the "could not connect to printer" error when trying to add via samba. IPP workaround does work.
[/LIST]

I would gather that this has something to do with samba and x64 versions of Windows. Does anyone have any insight on this?

---

### Post by kridybel on 2010-12-01
> **hidesertmlb said:**
> Got it working via CUPS. Here's what I had to do:

1- in /etc/samba/smb.conf  ensure the following was uncommented in the PRINTING section in [global]

load printers = yes
printing = cups
printcap name = cups

added the following to [printers]

use client driver = Yes



Everytime I restart my ubuntu pc I need to re do the above.
What is causing this? I'd like these changes to be permanent.

---

### Post by Silvertones on 2011-01-13
My XP machine prints fine. My new Win7x64 does not even though I can acess shares both ways. I've tried everything. Some say that the printer must first be installed locally. I can't do that if that's true as the Win7 machine doesn't have a LPT1 port.,nor is the printer listed in the list of drivers.

---

### Post by mrknizle on 2011-02-06
I was having the same problem sharing a printer from 10.10 and trying to connect with a notebook running Windows 7 (64 bit). I would set up the printer and it would connect and work until the next restart...then I would have to reconfigure. Following hidesertmlb's advice I changed the location from \\"computername"\"printername" to http://"computername":631/printers/"printername" and it has worked. I did not have to edit /etc/samba/smb.conf.

---

### Post by lkjoel on 2011-03-08
> **hidesertmlb said:**
> Got it working via CUPS. Here's what I had to do:

1- in /etc/samba/smb.conf  ensure the following was uncommented in the PRINTING section in [global]

load printers = yes
printing = cups
printcap name = cups

added the following to [printers]

use client driver = Yes

2- restarted samba: sudo /etc/init.d/samba restart

On the Win7 client

- Add a printer->Networked printer
- for the location, specified the printer via CUPS http. So in the location box, where UBUNTU is the hostname of the printer that's shared, and the shared name of my printer (Epson C120)

[http://ubuntu:631/printers/Epson_C120](http://ubuntu:631/printers/Epson_C120)

You can determine the shared name of your CUPS printer by going to your UBUNTU host that's sharing the printer, specifying the following URL:
[http://localhost:631](http://localhost:631)

Go to the PRINTERS tab, point to the queue name of the queue name of the printer that's shared, rt-click and display properties. This is the URL that will be used on your Win7 printer location, except "localhost" will be replaced with the hostname of your ubuntu host (in my case, "ubuntu").

- specify print driver to use on your Win7 machine and print a test page  


At least this is what worked for me. HTH
This solved my problem.
Thanks!

---

### Post by dalesd on 2011-05-05
> **hidesertmlb said:**
> Got it working via CUPS. Here's what I had to do:

1- in /etc/samba/smb.conf  ensure the following was uncommented in the PRINTING section in [global]

load printers = yes
printing = cups
printcap name = cups

added the following to [printers]

use client driver = Yes

2- restarted samba: sudo /etc/init.d/samba restart

On the Win7 client

- Add a printer->Networked printer
- for the location, specified the printer via CUPS http. So in the location box, where UBUNTU is the hostname of the printer that's shared, and the shared name of my printer (Epson C120)

[http://ubuntu:631/printers/Epson_C120](http://ubuntu:631/printers/Epson_C120)

You can determine the shared name of your CUPS printer by going to your UBUNTU host that's sharing the printer, specifying the following URL:
[http://localhost:631](http://localhost:631)

Go to the PRINTERS tab, point to the queue name of the queue name of the printer that's shared, rt-click and display properties. This is the URL that will be used on your Win7 printer location, except "localhost" will be replaced with the hostname of your ubuntu host (in my case, "ubuntu").

- specify print driver to use on your Win7 machine and print a test page  


At least this is what worked for me. HTH

I just used this to get my printer working on my wife's new Win7 notebook.

One change, to restart samba, I used
**sudo restart smbd**

---

### Post by rojovilla on 2011-07-28
> **hidesertmlb said:**
> Got it working via CUPS. Here's what I had to do:

1- in /etc/samba/smb.conf  ensure the following was uncommented in the PRINTING section in [global]

load printers = yes
printing = cups
printcap name = cups

added the following to [printers]

use client driver = Yes

2- restarted samba: sudo /etc/init.d/samba restart

On the Win7 client

- Add a printer->Networked printer
- for the location, specified the printer via CUPS http. So in the location box, where UBUNTU is the hostname of the printer that's shared, and the shared name of my printer (Epson C120)

[http://ubuntu:631/printers/Epson_C120](http://ubuntu:631/printers/Epson_C120)

You can determine the shared name of your CUPS printer by going to your UBUNTU host that's sharing the printer, specifying the following URL:
[http://localhost:631](http://localhost:631)

Go to the PRINTERS tab, point to the queue name of the queue name of the printer that's shared, rt-click and display properties. This is the URL that will be used on your Win7 printer location, except "localhost" will be replaced with the hostname of your ubuntu host (in my case, "ubuntu").

- specify print driver to use on your Win7 machine and print a test page  


At least this is what worked for me. HTH


+1!!!  don't know how many threads i went through before seeing this and trying it.  worked like a charm!!!

---

### Post by the_ebb on 2011-11-15
another ubuntu miracle - thanks for the assistance

---

### Post by jzambrano on 2012-06-27
Thank you so much you were the only one who really resolved my problem!!!!



> **hidesertmlb said:**
> Got it working via CUPS. Here's what I had to do:

1- in /etc/samba/smb.conf  ensure the following was uncommented in the PRINTING section in [global]

load printers = yes
printing = cups
printcap name = cups

added the following to [printers]

use client driver = Yes

2- restarted samba: sudo /etc/init.d/samba restart

On the Win7 client

- Add a printer->Networked printer
- for the location, specified the printer via CUPS http. So in the location box, where UBUNTU is the hostname of the printer that's shared, and the shared name of my printer (Epson C120)

[http://ubuntu:631/printers/Epson_C120](http://ubuntu:631/printers/Epson_C120)

You can determine the shared name of your CUPS printer by going to your UBUNTU host that's sharing the printer, specifying the following URL:
[http://localhost:631](http://localhost:631)

Go to the PRINTERS tab, point to the queue name of the queue name of the printer that's shared, rt-click and display properties. This is the URL that will be used on your Win7 printer location, except "localhost" will be replaced with the hostname of your ubuntu host (in my case, "ubuntu").

- specify print driver to use on your Win7 machine and print a test page  


At least this is what worked for me. HTH

---

