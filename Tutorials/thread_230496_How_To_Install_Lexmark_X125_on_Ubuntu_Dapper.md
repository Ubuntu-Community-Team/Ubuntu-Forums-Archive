---
title: "How To Install Lexmark X125 on Ubuntu Dapper"
date: 2006-08-06
forum: Tutorials
---

### Post by tagra123 on 2006-08-06
How To Install Lexmark X125 on UBUNTU (Dapper or Breezy)

I orginally posted this how to on LinuxPrinting.org for Breezy but the instructions are now modified to work for Breezy or Dapper.

Download the X125-drv-0.2.3.tar.gz driver from: [http://sourceforge.net/projects/x125-linux/](http://sourceforge.net/projects/x125-linux/)

Select save to Deskop.

INSTALLING THE DRIVER

*****
Open your terminal using the menu (Applications-Accessories-Terminal)
*****

Type in the following commands:

[B]cd Desktop
mkdir prndriver
cd prndriver
mv ./x125-drv-0.2.3.tar.gz ./prndriver/x125-drv-0.2.3.tar.gz

cd prndriver
tar -xvzf x125-drv-0.2.3.tar.gz

cd drv_x125
cd src
make (ignore warnings you may see here)
sudo make install

sudo /etc/init.d/cupsys restart[/B]


**** ADDED FOR UBUNTU DAPPER 6.06 
****     DAPPER users also type in the following commands. BREEZY users can skip this. ****


[B]sudo mkdir /dev/usb
sudo ln -s /dev/usblp0 /dev/usb/lp0[/B]

*****
close the terminal
*****

*******
Open your Printers by using the menu (System-Printing)

Click on New Printer

STEP 1
Even though this is a local printer we will set it up as a network printer using LPD by entering the information below.

Choose Network Printer
Select UNIX Printer (LPD)

HOST: localhost
Queue Type: /dev/null

Click on the Forward button.

STEP 2
Specify your printer by using the information below.
Select Lexmark as the manufacturer
Select X125 as the model
Select drv_x125(recommended) as the driver

Click on the Apply button

The printers window should now have the x125 listed as your printer.

Right click on the printer and select properties.
Click on the Advanced tab.

Make sure your device is /dev/usb/lp0 

Click on Print Test Page and the printer should print but you will have to manually cancel the job. The additional instructions (below) allow the printer to print without having to manually cancel each job.


From a terminal type in:

First make a backup:

**sudo cp /etc/cups/printers.conf /etc/cups/printers.conf.bak4x125**

Next open the file to edit:
**sudo gedit /etc/cups/printers.conf**
 
If you've followed the steps above you should have an X125 section. 

Delete the X125 section and replace it with the following.

FOR BREEZY INSERT BELOW:
 
[I]<DefaultPrinter X125> 
Info X125 
Location usb://Lexmark/X125 
DeviceURI file:///dev/null 
State Idle 
Accepting Yes 
JobSheets none none 
QuotaPeriod 0 
PageLimit 0 
KLimit 0 
</Printer> [/I]


FOR DAPPER INSERT BELOW:
 
[I]<DefaultPrinter X125> 
Info X125 
Location usb://usb/lp0
DeviceURI file:///dev/null 
State Idle 
Accepting Yes 
JobSheets none none 
QuotaPeriod 0 
PageLimit 0 
KLimit 0 
</Printer> [/I]



Save the file and close the text editor.

*****
from the terminal and type the following 
*****

**sudo /etc/init.d/cupsys restart**


*****
close the terminal
*****

******************************
DAPPER USERS - ADDITIONAL STEP
******************************
WHEN RESTARTING THE COMPUTER the /dev/usb/lp0 will not be there.  To fix this I added the following.

from a terminal:

[B]sudo gedit /etc/udev/rules.d/10-local.rules
[/B]

This file may not exist - the above line will create it if it does not exist

**********************************
Insert the following

```


BUS=="usb", KERNEL=="lp[0-9]*", SYMLINK+="usb/%k"


```

Save the file and exit.

Reboot the computer and /dev/usb/lp0 should be there.


It works on UBUNTU and KUBUNTU:D .


Hope it helps. Tom -- tagra

---

### Post by tagra123 on 2006-08-27
After some newer updates the X125 quit working again -- the Z23 also quit.

I have had enough with this Lexmark.

I went to Walmart and picked up a HP Deskjet 3940 for about $44.00.

Look at this easy how to:

Plug it in.

Turn it on.

Select System - Administration - Printing

Add Printer 

Select HP Deskjet 3940

Enjoy printing without pulling out your hair.

---

### Post by Complete on 2010-08-02
the first "cd prndriver" is wrong.  The following command will not work if you use it.
The last command listed here will not work either.
> **tagra123 said:**
> How To Install Lexmark X125 on UBUNTU (Dapper or Breezy)

I orginally posted this how to on LinuxPrinting.org for Breezy but the instructions are now modified to work for Breezy or Dapper.

Download the X125-drv-0.2.3.tar.gz driver from: [http://sourceforge.net/projects/x125-linux/](http://sourceforge.net/projects/x125-linux/)

Select save to Deskop.

INSTALLING THE DRIVER

*****
Open your terminal using the menu (Applications-Accessories-Terminal)
*****

Type in the following commands:

[B]cd Desktop
mkdir prndriver
[s]cd prndriver[/s]
mv ./x125-drv-0.2.3.tar.gz ./prndriver/x125-drv-0.2.3.tar.gz

cd prndriver
tar -xvzf x125-drv-0.2.3.tar.gz

cd drv_x125
cd src
make (ignore warnings you may see here)
sudo make install

[s]sudo /etc/init.d/cupsys restart[/s][/B]

the first "cd prndriver" is wrong.  The following command will not work if you use it.
The last command listed here will not work either.

---

### Post by Complete on 2010-08-09
On Ubuntu 10.04 the latest command is:
sudo /etc/init.d/cups restart
and it works:
```

dawn@dawn-desktop:~/Desktop/prndriver/drv_x125/src$ sudo /etc/init.d/cups restart

[sudo] password for dawn: 

 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

dawn@dawn-desktop:~/Desktop/prndriver/drv_x125/src$ 

```

---

### Post by vanyat77 on 2011-08-27
Hello, I use Ubuntu 10.04 LTS Lucid Lynx. I followed and executed all commands above, but I am still not able to print. Can you please help me. For sure there must be a way to get my x125 running.

---

