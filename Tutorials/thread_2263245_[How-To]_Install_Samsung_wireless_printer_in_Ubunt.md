---
title: "[How-To] Install Samsung wireless printer in Ubuntu (m2022w)"
date: 2015-01-30
forum: Tutorials
---

### Post by lenooh on 2015-01-30
Recently I bought a Samsung wireless printer, and did not find much useful information on the internet how to install it.
My printer is M2022w, but I guess the process should be similar for all Samsung wireless printers.


So here is how I got it working:

**Overview:**
1. Download and install Samsung original printer driver
2. Connect printer to your wireless network
3. Add network printer using the printer settings wizard 


**Steps in detail:**
1. Step - Download and install Samsung original printer driver
Visit [www.samsung.com](www.samsung.com) and under Support -> Printer, enter your printer model name.
Scroll down to the drivers section, and download the Linux print driver. It will most likely be uld-something.tar.gz.
Open terminal, cd to the download location and untar the file with:
tar xvzf uld-something.tar.gz (enter the actual filename)
Enter the just unpacked directory (probably uld/) and run:
sudo ./install-printer.sh

This will copy the .ppd files and some other samsung stuff to system paths.
There is also a file install-scanner.sh and install.sh. Use these if you want to install a scanner or if your printer also has a scanner incorporated.


2. Step - Connect printer to your wireless network
This is now the tricky part, since their documentation consists of some 200 pages of broken English. I had to read it a couple of times until I figured it out.
Connect the printer to a power plug, and add it some paper.
Turn it on.
Then press and hold the "WPS" button for 10 seconds (count in your head) and release. It should print 2 pages, one of them is "Network Configuration".
Near the bottom of the page, is a PIN Number (8 digits).
Using you laptop, check your available wireless connections. One of them should belong to the printer. Connect to it, and enter the PIN for the password.
Find out your network IP (either in the terminal with ifconfig, or check connection properties).
Open your browser and enter your IP (yes, your IP, not the printers!)
Something called SyncThru Web Service should show up.
In the top right is a "Login" link. Click it, and enter "admin" for ID, and "sec00000" for password.
You will now see a new option "Settings". Open Settings -> Network Settings
On the left select "Wi-Fi", then select "Easy Wi-Fi Settings", and follow the wizard to connect the printer to your wireless network. After that, the printer should restart and connect to your wireless network.
With your laptop, connect back to your wireless network.


3. Step - Add network printer using the printer settings wizard
Finally you can add the printer to Ubuntu. Open Settings -> Printers.
Press Add. Wait for some time and the printer should appear under the Network printer.
Select it, and make sure the connection type is AppSocket/HP JetDirect (in my case ipp did not work), and press Next. Ubuntu should find the printer driver by itself.
Print a test page, and it should work.


To add the printer to other computers in your network, just do steps 1. and 3.


Hope this helps!

---

### Post by jusr on 2015-05-23
Thank you very much, lenooh! I thought that the web interface of the printer didn't allow to setup WiFi, but it does, when we're logged in.

I am using Debian, and I installed the driver via [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) instead of using the driver supplied by Samsung. I have the M2020W model, and the package suld-driver2-1.00.35 worked for me.

---

### Post by gbakos2 on 2015-07-17
[I][QUOTE=lenooh;13218825]Recently I bought a Samsung wireless printer, and did not find much useful information on the internet how to install it.
My printer is M2022w, but I guess the process should be similar for all Samsung wireless printers.
[/I]

I tried this under Ubuntu 12.10.


[I]**Steps in detail:**
1. Step - Download and install Samsung original printer driver
Visit [www.samsung.com]("http://www.samsung.com") and under Support -> Printer, enter your printer model name.
Scroll down to the drivers section, and download the Linux print driver. It will most likely be uld-something.tar.gz.
Open terminal, cd to the download location and untar the file with:
tar xvzf uld-something.tar.gz (enter the actual filename)
Enter the just unpacked directory (probably uld/) and run:
sudo ./install-printer.sh[/I]

Indeed, the current version is ULD_v1.00.35.tar.gz. After unpacking this, and searching around, I found no .ppd file for the M2022W printer. 
The closest ones are:
    Samsung_ML-2010_Series.ppd
    Samsung_M2020_Series.ppd
I tried ML-2010 in "system-config-printer" , but that led to failure when printing the test page ("SPL ERROR...").

I also tried M2020, but that does not print a page. 

Which .ppd file is the relevant file for the M2022W printer?


* This will copy the .ppd files and some other samsung stuff to system paths.*

I am unsure about this. I looked around in e.g. /etc/cups/ppd/ or /usr/share/cups/, and no trace of updated files. I gave the M2020 ppd file manually, by specifying its original location (from the untar).


[I] 3. Step - Add network printer using the printer settings wizard
Finally you can add the printer to Ubuntu. Open Settings -> Printers.[/I]

Here I would note that the system config under Ubuntu 12.10 for printers is very primitive, and is missing all the relevant options. You have to use system-config-printer. 

[I] Press Add. Wait for some time and the printer should appear under the Network printer.
Select it, and make sure the connection type is AppSocket/HP JetDirect (in my case ipp did not work), and press Next. Ubuntu should find the printer driver by itself.
Print a test page, and it should work.
[/I]
This is where I got stuck. Printer shows up under network printers as M2020. I configured it as AppSocket, but no test page prints. 

If I config the printer as general postscript, then it prints an ascii/text page, complaining that "if you can 
read this, you misconfigured your printer" or such.

Any advice on this would be welcome. My guess is that I am missing the relevant and up-to-date .ppd file.

---

### Post by lenooh on 2015-08-22
Hi gbakos2!

> Indeed, the current version is ULD_v1.00.35.tar.gz. After unpacking this, and searching around, I found no .ppd file for the M2022W printer. 
The closest ones are:
Samsung_ML-2010_Series.ppd
Samsung_M2020_Series.ppd
I tried ML-2010 in "system-config-printer" , but that led to failure when printing the test page ("SPL ERROR...").

I also tried M2020, but that does not print a page. 

Which .ppd file is the relevant file for the M2022W printer?

I never manually copied any .ppd files. Just run the install script.


> Here I would note that the system config under Ubuntu 12.10 for printers is very primitive, and is missing all the relevant options. You have to use system-config-printer. 
Why? I installed the printer with no problems on Ubuntu 12.04 and 14.04 in the same way, using the ubuntu printer configuration.

---

### Post by skyrat on 2015-10-14
Thanks for the clear instructions Lenooh. Worked first time..

---

### Post by Emanuele_Coti_Zela on 2015-10-24
Ciao,
 ho letto una tua risposta e la tua guida circa l'installazione della stampante Samsung M2026w su ubuntu ed è per questo che ti chiedo una mano: sto impazzendo.

Ho comprato la stampante e dopo non poche difficoltà l'ho installata. Funziona correttamente se collegata via USB ma via wireless non so come fare.
Ho seguito la tua guida ([http://ubuntuforums.org/showthread.php?t=2263245](http://ubuntuforums.org/showthread.php?t=2263245)) pero' sinceramente le due pagine che mi stampa dopo aver tenuto premuto il tasto WPS non mi producono nessun numero PIN.
Se seleziono la rete wireless della stampante me lo chiede e io non so come cavarmela.
Inoltre, se io dovessi indovinare il PIN come dovrei fare per stampare? Collegarmi alla wireless della stampante "mollando" la mia wireless di casa?

Grazie mille in anticipo.

---

### Post by globetrotterdk on 2015-12-20
I have a cli only Ubuntu 14.04 system. I ran the install script, but can't figure out how to configure the printer for the system via the command line interface. Any ideas? Thanks :-)

---

### Post by lenooh on 2015-12-20
If you have CUPS installed, you can visit the web interface.

Locally: open localhost:631 in lynx or some other CLI browser

If you want to administer it remotely, see here: [http://askubuntu.com/questions/23936/how-do-you-administer-cups-remotely-using-the-web-interface]("http://askubuntu.com/questions/23936/how-do-you-administer-cups-remotely-using-the-web-interface")

---

### Post by globetrotterdk on 2015-12-20
> **lenooh said:**
> If you have CUPS installed, you can visit the web interface.

Locally: open localhost:631 in lynx or some other CLI browser

If you want to administer it remotely, see here: [http://askubuntu.com/questions/23936/how-do-you-administer-cups-remotely-using-the-web-interface]("http://askubuntu.com/questions/23936/how-do-you-administer-cups-remotely-using-the-web-interface")

Thanks for the quick reply. I used Lynx [http://localhost:631](http://localhost:631) to get to the CUPS configuration as suggested. Unfortunately, I can see that printing to PDF file is still default. Any idea how to change that in the cli, other than editing the configuration file, or is that the way it is done? Lastly, how do I ensure that all my cli apps can print to the printer? Is there a special configuration that needs to be done for printing from the cli?

Thanks

---

### Post by lenooh on 2015-12-20
> **globetrotterdk said:**
> Thanks for the quick reply. I used Lynx [http://localhost:631](http://localhost:631) to get to the CUPS configuration as suggested. Unfortunately, I can see that printing to PDF file is still default. Any idea how to change that in the cli, other than editing the configuration file, or is that the way it is done? Lastly, how do I ensure that all my cli apps can print to the printer? Is there a special configuration that needs to be done for printing from the cli?

Thanks

Make sure you add the printer.

Then, move to "Printers" section, select your printer, and then choose "Set as server default".


To print from the command line, use lpr: [http://askubuntu.com/questions/432746/print-from-command-line]("http://askubuntu.com/questions/432746/print-from-command-line")

---

### Post by AGTG on 2016-01-25
> **lenooh said:**
> Recently I bought a Samsung wireless printer, and did not find much useful information on the internet how to install it.
My printer is M2022w, but I guess the process should be similar for all Samsung wireless printers.


So here is how I got it working:

**Overview:**
1. Download and install Samsung original printer driver
2. Connect printer to your wireless network
3. Add network printer using the printer settings wizard 


**Steps in detail:**
1. Step - Download and install Samsung original printer driver
Visit [www.samsung.com]("http://www.samsung.com") and under Support -> Printer, enter your printer model name.
Scroll down to the drivers section, and download the Linux print driver. It will most likely be uld-something.tar.gz.
Open terminal, cd to the download location and untar the file with:
tar xvzf uld-something.tar.gz (enter the actual filename)
Enter the just unpacked directory (probably uld/) and run:
sudo ./install-printer.sh

This will copy the .ppd files and some other samsung stuff to system paths.
There is also a file install-scanner.sh and install.sh. Use these if you want to install a scanner or if your printer also has a scanner incorporated.


2. Step - Connect printer to your wireless network
This is now the tricky part, since their documentation consists of some 200 pages of broken English. I had to read it a couple of times until I figured it out.
Connect the printer to a power plug, and add it some paper.
Turn it on.
Then press and hold the "WPS" button for 10 seconds (count in your head) and release. It should print 2 pages, one of them is "Network Configuration".
Near the bottom of the page, is a PIN Number (8 digits).
Using you laptop, check your available wireless connections. One of them should belong to the printer. Connect to it, and enter the PIN for the password.
Find out your network IP (either in the terminal with ifconfig, or check connection properties).
Open your browser and enter your IP (yes, your IP, not the printers!)
Something called SyncThru Web Service should show up.
In the top right is a "Login" link. Click it, and enter "admin" for ID, and "sec00000" for password.
You will now see a new option "Settings". Open Settings -> Network Settings
On the left select "Wi-Fi", then select "Easy Wi-Fi Settings", and follow the wizard to connect the printer to your wireless network. After that, the printer should restart and connect to your wireless network.
With your laptop, connect back to your wireless network.


3. Step - Add network printer using the printer settings wizard
Finally you can add the printer to Ubuntu. Open Settings -> Printers.
Press Add. Wait for some time and the printer should appear under the Network printer.
Select it, and make sure the connection type is AppSocket/HP JetDirect (in my case ipp did not work), and press Next. Ubuntu should find the printer driver by itself.
Print a test page, and it should work.


To add the printer to other computers in your network, just do steps 1. and 3.


Hope this helps!

This is too complicated for me. My Samsung doesn't produce this document when holding the WPS button down. I downloaded the drivers, but can't understand how I'm supposed to get them loaded up. Moreover, when I open my printer settings it doesn't even recognize the Samsung wifi that my regular wifi system readily sees.

---

### Post by lenooh on 2016-01-28
> This is too complicated for me. My Samsung doesn't produce this document when holding the WPS button down. I downloaded the drivers, but can't understand how I'm supposed to get them loaded up. Moreover, when I open my printer settings it doesn't even recognize the Samsung wifi that my regular wifi system readily sees.

Hi! There is another way, it might be simpler for you. If you have VirtualBox installed and a windows image, you can configure the printer wifi settings with windows, then everything else you can do with ubuntu. I used an old version of WinXP (SP3). Make sure you have USB support configured in VirtualBox and the guest additions installed.

---

### Post by swinus on 2016-05-29
Lenooh's explanation finally worked for me & my m2020w, with these clarifications
- timing on that 10-second button push is critical, too short/long and you just get a "pages used" printout
- it _is_ the printer's IP you need to enter in browser, after connecting to its network
- the annoying "change password" dialog goes away even if you change admin password to the default :)
- printer cannot successfully set up WEP, i changed my hub to use WPA (and re-keyed every device we own) and it worked
- setting up fixed IP, then changing to DHCP later, seems to work better than initial DHCP specification
- printer will not connect to your wifi while the wifiDirect option is enabled, disable it as final act
- settings will not take effect until Security->Restart option is selected
- power off for several minutes still seemed necessary, and wifi startup was slow, but it worked

---

### Post by wellcosh on 2016-10-29
**[COLOR=#000000]L[/COLOR]enooh, **just registered to say l love you man. Couldn't find anything on Samsung website, nothing worked, almost wanted to give up, then found your thread. It works perfectly on Arch linux too. Thanks! I owe you a beer.

---

### Post by vshearer on 2017-02-01
My 2030dw uses "x" button for network config printout. 2 seconds for demo, 4 seconds for network config, 6 seconds for consumption counts. Also on network config pin did not work for connect, but password did. Find driver on samsung site, you will have to click multiple dirver files until you find the tar file "uld" After that everything else in instructions worked fine.

---

### Post by gwendydd on 2017-03-27
First time I installed the printer, I followed all the steps and worked perfectly fine.
Then I had to reinstall Ubuntu, so I followed all the steps again, only this time there seems to be no way I can print. Everything works fine until I try printing a test page, then a popup message appears immediately, saying "Printing stopped". Same exact problem via USB.
Can someone help me?

---

### Post by kelomaster on 2017-04-18
Excelent lenooh. Tks so much. Just when you say put your IP adress, in my case was in the NETWORK CONFIGURATION page and isn't the real IP adress that figure in my computer.

---

### Post by antonio-aloisio on 2018-02-02
As for 
[I]Select it, and make sure the connection type is AppSocket/HP JetDirect (in my case ipp did not work), and press Next. Ubuntu should find the printer driver by itself.
[/I]
Well, I have downloaded  the latest drivers from [http://www.driversamsung.com/samsung-sl-m2020w-download-driver/](http://www.driversamsung.com/samsung-sl-m2020w-download-driver/) and the AppSocket/HP JetDirect and IPP are gone.
There is only one single option which is "LPD network printer via DNS-SD" and it works like a charm.

---

### Post by anjina on 2018-02-03
> **lenooh said:**
> Recently I bought a Samsung wireless printer, and did not find much useful information on the internet how to install it.
My printer is M2022w, but I guess the process should be similar for all Samsung wireless printers.


So here is how I got it working:

**Overview:**
1. Download and install Samsung original printer driver
2. Connect printer to your wireless network
3. Add network printer using the printer settings wizard 


**Steps in detail:**
1. Step - Download and install Samsung original printer driver
Visit [https://www.drivers-samsung.com]("https://www.drivers-samsung.com/samsung-m2830dw-driver/") and search for m2022wPrinter .
Scroll down to the drivers section, and download the Linux print driver. It will most likely be uld-something.tar.gz.
Open terminal, cd to the download location and untar the file with:
tar xvzf uld-something.tar.gz (enter the actual filename)
Enter the just unpacked directory (probably uld/) and run:
sudo ./install-printer.sh

This will copy the .ppd files and some other samsung stuff to system paths.
There is also a file install-scanner.sh and install.sh. Use these if you want to install a scanner or if your printer also has a scanner incorporated.


2. Step - Connect printer to your wireless network
This is now the tricky part, since their documentation consists of some 200 pages of broken English. I had to read it a couple of times until I figured it out.
Connect the printer to a power plug, and add it some paper.
Turn it on.
Then press and hold the "WPS" button for 10 seconds (count in your head) and release. It should print 2 pages, one of them is "Network Configuration".
Near the bottom of the page, is a PIN Number (8 digits).
Using you laptop, check your available wireless connections. One of them should belong to the printer. Connect to it, and enter the PIN for the password.
Find out your network IP (either in the terminal with ifconfig, or check connection properties).
Open your browser and enter your IP (yes, your IP, not the printers!)
Something called SyncThru Web Service should show up.
In the top right is a "Login" link. Click it, and enter "admin" for ID, and "sec00000" for password.
You will now see a new option "Settings". Open Settings -> Network Settings
On the left select "Wi-Fi", then select "Easy Wi-Fi Settings", and follow the wizard to connect the printer to your wireless network. After that, the printer should restart and connect to your wireless network.
With your laptop, connect back to your wireless network.


3. Step - Add network printer using the printer settings wizard
Finally you can add the printer to Ubuntu. Open Settings -> Printers.
Press Add. Wait for some time and the printer should appear under the Network printer.
Select it, and make sure the connection type is AppSocket/HP JetDirect (in my case ipp did not work), and press Next. Ubuntu should find the printer driver by itself.
Print a test page, and it should work.


To add the printer to other computers in your network, just do steps 1. and 3.


Hope this helps!

hi thank you for the detailed installation instruction about installation 
installed successfully

---

