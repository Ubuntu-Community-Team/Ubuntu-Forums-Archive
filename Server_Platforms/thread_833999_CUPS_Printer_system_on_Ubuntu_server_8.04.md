---
title: "CUPS Printer system on Ubuntu server 8.04"
date: 2008-06-19
forum: Server Platforms
---

### Post by aaron465 on 2008-06-19
Hi,

I am fairly new to linux, and have not installed a printer on it before. I am trying to set up my HP Deskjet 3520 up on my ubuntu server and share it on the network using samba so my windows clients can print to it.

I also have Webmin installed as it makes admin'ing the server a whole lot easier!


Anyway - i have installed cupsys and hplip using apt-get, but webmin still says this:

```
The command lpstat was not found on your system, which indicates that the CUPS print system is not installed. Either install the software for your chosen print system, or use the module configuration to change it.
```

The printer is plugged in at present (USB) and as I am new to printers on linux I have no idea if you have to install manually like on windows - or if it just happens - like Mac OS X. (I run both of those at home)



Any help with this issue would be greatly appreciated.
Thanks,

Aaron

---

### Post by brokenshadows on 2008-07-23
wow...I'm surprised nobody has responded to this one yet.

from your terminal, type *lpstat -a*

if it tells you that "The program 'lpstat' can be found in the following packages:", one of them should be *cupsys-client*

run *apt-get install cupsys-client*

now if you type *lpstat -a* it should return something other than 'you didn't install this program' (on my system it tells me that I have *No destinations added*...I'm assuming because I have no printers installed)

Refresh your webmin page and you should see the correct screen...

If none of that made any sense, or if it breaks anything...I blame it on the fact that I've only been working with linux for a few weeks...please don't beat me

---

### Post by aaron465 on 2008-08-01
Hi,

Thanks very muchly - this has worked, i also got the no destinations thing, but the printer is not installed yet!

Just need to get my hands on the drivers and i should be away!


thanks again,

Aaron

---

### Post by brokenshadows on 2008-08-02
sweet!  it didn't explode :)

glad I could help...

---

### Post by rksingh54 on 2008-10-05
I did istall cupsys-client which was already there but upon the command "lpstat -a" I get a response, "No destination added".

Your help will be appreciated.

RKS

---

### Post by Girya on 2008-10-05
> **rksingh54 said:**
> I did istall cupsys-client which was already there but upon the command "lpstat -a" I get a response, "No destination added".

Your help will be appreciated.

RKS

it might be a lot easier to admin cups through the browser interface. here is a link to a tutorial. [http://ubuntuforums.org/showthread.php?t=310450]("http://ubuntuforums.org/showthread.php?t=310450")

I use a cups server for my home network and it works great.

---

### Post by stereosteve on 2008-10-30
I have got CUPS running on Ubuntu server 8.04.1 and am able to print from the server machine to the attached printer (Epson Stylus Photo R300) just fine. My Windows client machine is able to run the CUPS web admin system fine. Windows (Vista) finds the printer just fine in the 'add printer' dialogs.

Unfortunately, the Windows print is garbled. A plain text print file does not show correct spacing and the Windows Test Page is a mass of overprinting.

On the server machine, I am using the Gutenprint driver.

smb.conf and cupsd.conf are attached


Stereosteve

---

