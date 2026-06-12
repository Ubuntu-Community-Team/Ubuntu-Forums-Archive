---
title: "Install Brother MFC7360n on local network in Ubuntu 16.04"
date: 2016-04-26
forum: Tutorials
---

### Post by him610 on 2016-04-26
This guide provides detailed instructions on how to download, install, and setup a Brother MFC-7360N , a multifunction device capable of printing, scanning, copying, and faxing. 
_**[COLOR="#A52A2A"]This process will work for other Brother models also.[/COLOR]**_

Note: I have included the prompts from both the Brother website and the prompts displayed when running  the linux-brprinter-installer-x.x.x-x script along with my responses so anyone using this guide will know what to expect. 

System: 
```

hugh@8930-u1604:~/Documents/Acer_8930g$ inxi -b
System:    Host: 8930-u1604 Kernel: 4.4.0-21-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer (portable) product: Aspire 8930 v: V1.10
           Mobo: Acer model: Aspire 8930 v: PSMBOU-1234567
           Bios: Acer v: V1.10 date: 12/03/2008
CPU:       Dual core Intel Core2 Duo T6400 (-MCP-) speed/max: 1600/2000 MHz
Graphics:  Card: NVIDIA G96M [GeForce 9600M GT]
           Display Server: X.Org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1680x945@60.00hz
           GLX Renderer: Gallium 0.4 on NV96 GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
           driver: ATL1E
           Card-2: Intel WiFi Link 5100 driver: iwlwifi
Drives:    HDD Total Size: 750.2GB (1.4% used)
Info:      Processes: 204 Uptime: 25 min Memory: 777.8/3949.0MB
           Client: Shell (bash) inxi: 2.2.35 

```
Environment: 
```

hugh@8930-u1604:~/Documents/Acer_8930g$ iwconfig
enp2s0    no wireless extensions.

wlp5s0    IEEE 802.11abgn  ESSID:"arbor"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx.xx.xx.xx.xx.xx   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:114   Missed beacon:0

```

Printer IP: ```

hugh@8930-u1604:~/Documents/Acer_8930g$ ping -c1 192.168.1.99
PING 192.168.1.99 (192.168.1.99) 56(84) bytes of data.
64 bytes from 192.168.1.99: icmp_seq=1 ttl=255 time=12.1 ms

--- 192.168.1.99 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 12.119/12.119/12.119/0.000 ms

```

***[SIZE=2]Issue: Network printer, Brother MFC-7360n, is not set up on host machine, 8930-u1604[/SIZE]***
 
Pre-requisites: # Both of these are important!
System OS, Ubuntu 16.04 is current
Target device is online with* static* IP address   # How to set static IP address - read your manual

Installation -download installer from Brother

Go to Brother support website
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7360n_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7360n_all&os=128)
Select OS - Linux(deb) Language - English
Click 'Driver Install Tool'
new window with heading, 'Follow the Steps below to Download'
	You can click on Compatible Model to check if your model is listed
	Read Notes before downloading
Click to Agree to the EULA and Download
new page opens, Driver Install Tool
# Read, or copy & save 'How to Install'

# How to Install Instructions from Brother download page ######################
Step1. Download the tool.(linux-brprinter-installer-*.*.*-*.gz)
The tool will be downloaded into the default "Download" directory.
(The directory location varies depending on your Linux distribution.)
e.g. /home/(LoginName)/Download
Step2. Open a terminal window and go to the directory you downloaded the file to in the last step.
Step3. Enter this command to extract the downloaded file:
Command: gunzip linux-brprinter-installer-*.*.*-*.gz
Step4. Get superuser authorization with the "su" command or "sudo su" command.
Step5. Run the tool:
Command: bash linux-brprinter-installer-*.*.*-* Brother machine name
Step6. The driver installation will start. Follow the installation screen directions.
 
 When you see the message "Will you specify the DeviceURI ?",
 For USB Users: Choose N(No)
 For Network Users: Choose Y(Yes) and DeviceURI.
The install process may take some time. Please wait until it is complete.
# End of Brother Install Instructions ######################################

# This is the download destination that shows the downloaded file
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ ls -l
total 28
-rw-rw-r-- 1 hugh hugh 21813 Apr 26 14:29 linux-brprinter-installer-2.0.0-1.gz

# The file was downlloaded as a *.gz file, here is where we extract using gunzip
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ gunzip linux-brprinter-installer-*.*.*-*.gz

# Here is the extracted file
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ ls -l
total 92
-rw-rw-r-- 1 hugh hugh 92056 Apr 26 14:29 linux-brprinter-installer-2.0.0-1

# This is where we run the install script to install and configure the printer
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ sudo su
[sudo] password for hugh: 
root@8930-u1604:/home/hugh/Documents/Acer_8930g/MFC7360n# bash linux-brprinter-installer-2.0.0-1 MFC7360N
You are going to install following packages.
   mfc7360nlpr-2.1.0-1.i386.deb
   cupswrapperMFC7360N-2.0.4-2.i386.deb
   brscan4-0.4.3-3.amd64.deb
   brscan-skey-0.2.4-1.amd64.deb
OK? [y/N]y (enter) (You will need to concur with a couple of agreements)
After last agreement, install script begins to run. You will see some activity on the terminal, then comes question, "Will you specify the Device URI? [Y/n] ->" Enter (for network installation)
Listing appears - this is what mine looks like... (refer to attached image "Choose_device.png")

```

0: beh
1: socket
2: lpd
3: ipps
4: ipp14
5: https
6: ipp
7: http
8: hp
9: hpfax
10: dnssd://Brother%20MFC-7360N._pdl-datastream._tcp.local/
11: lpd://MFC7360N/BINARY_P1
12 (I): Specify IP address.
13 (A): Auto. (dnssd://Brother%20MFC-7360N._pdl-datastream._tcp.local/)

select the number of destination Device URI. ->12

 enter IP address ->192.168.1.99
lpadmin -p MFC7360N -v socket://192.168.1.99 -E
Test Print? [y/N] ->y

 enter IP address ->192.168.1.99
lpadmin -p MFC7360N -v socket://192.168.1.99 -E
Test Print? [y/N] ->y

wait 5s.
lpr -P MFC7360N /usr/share/cups/data/testprint
```
# Test page prints out
```
You are going to install following packages.
   brscan4-0.4.3-3.amd64.deb
```
=========================================
# Another Brother License Agreement
=========================================
Do you agree? [Y/n] ->y
=========================================
# Another Brother License Agreement
=========================================
```
Do you agree? [Y/n] -> (enter)

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/brscan-skey-0.2.4-1.amd64.deb
--2016-04-26 16:10:15--  http://www.brother.com/pub/bsc/linux/packages/brscan-skey-0.2.4-1.amd64.deb
Resolving www.brother.com (www.brother.com)... 23.67.251.32, 23.67.251.34
Connecting to www.brother.com (www.brother.com)|23.67.251.32|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 50852 (50K) [text/plain]
Saving to: ‘brscan-skey-0.2.4-1.amd64.deb’

brscan-skey-0.2.4-1.amd64.deb  100%[=================================================>]  49.66K  --.-KB/s    in 0.04s   

2016-04-26 16:10:15 (1.25 MB/s) - ‘brscan-skey-0.2.4-1.amd64.deb’ saved [50852/50852]

dpkg -i --force-all brscan-skey-0.2.4-1.amd64.deb
Selecting previously unselected package brscan-skey.
(Reading database ... 238461 files and directories currently installed.)
Preparing to unpack brscan-skey-0.2.4-1.amd64.deb ...
Unpacking brscan-skey (0.2.4-1) ...
Setting up brscan-skey (0.2.4-1) ...
brsaneconfig4 -a name=MFC-7360N model=MFC-7360N ip=192.168.1.99
root@8930-u1604:/home/hugh/Documents/Acer_8930g/MFC7360n# exit
exit
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ 
```

# That completes the installation and setup. The test page printed out, so it works; however, I have read that some folks get a test page printed out then can not scan or print, so let's try that. This will verify the installation and configuration.

# Verify the scan and print functions of the MFC7360n
Using SimpleScan, scan the previously printed Test Page then save it and print it out.
Test page is scanned satisfactorially using scan function of MFC7360n. (Refer to attached image "Scanned_page.png")
Save the test page – page gets saved as a pdf file
Print the saved pdf using MFC7360n
Page prints out - Verified Success!

It is my hope that anyone who follows these instructions finds success also.[ATTACH=CONFIG]269132[/ATTACH][ATTACH=CONFIG]269133[/ATTACH]

---

### Post by j0shua123 on 2016-11-18
I get a machine name not found error regardless of whether I type "machine name" or "MFC-7360N" after "Brother" in the "Command: bash linux-brprinter-installer-*.*.*-* Brother machine name" command.

---

### Post by chefboyct on 2017-05-19
> **him610 said:**
> This guide provides detailed instructions on how to download, install, and setup a Brother MFC-7360N , a multifunction device capable of printing, scanning, copying, and faxing. 
_**[COLOR=#A52A2A]This process will work for other Brother models also.[/COLOR]**_

Note: I have included the prompts from both the Brother website and the prompts displayed when running  the linux-brprinter-installer-x.x.x-x script along with my responses so anyone using this guide will know what to expect. 

System: 
```

hugh@8930-u1604:~/Documents/Acer_8930g$ inxi -b
System:    Host: 8930-u1604 Kernel: 4.4.0-21-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer (portable) product: Aspire 8930 v: V1.10
           Mobo: Acer model: Aspire 8930 v: PSMBOU-1234567
           Bios: Acer v: V1.10 date: 12/03/2008
CPU:       Dual core Intel Core2 Duo T6400 (-MCP-) speed/max: 1600/2000 MHz
Graphics:  Card: NVIDIA G96M [GeForce 9600M GT]
           Display Server: X.Org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1680x945@60.00hz
           GLX Renderer: Gallium 0.4 on NV96 GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
           driver: ATL1E
           Card-2: Intel WiFi Link 5100 driver: iwlwifi
Drives:    HDD Total Size: 750.2GB (1.4% used)
Info:      Processes: 204 Uptime: 25 min Memory: 777.8/3949.0MB
           Client: Shell (bash) inxi: 2.2.35 

```
Environment: 
```

hugh@8930-u1604:~/Documents/Acer_8930g$ iwconfig
enp2s0    no wireless extensions.

wlp5s0    IEEE 802.11abgn  ESSID:"arbor"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx.xx.xx.xx.xx.xx   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:114   Missed beacon:0

```

Printer IP: ```

hugh@8930-u1604:~/Documents/Acer_8930g$ ping -c1 192.168.1.99
PING 192.168.1.99 (192.168.1.99) 56(84) bytes of data.
64 bytes from 192.168.1.99: icmp_seq=1 ttl=255 time=12.1 ms

--- 192.168.1.99 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 12.119/12.119/12.119/0.000 ms

```

***[SIZE=2]Issue: Network printer, Brother MFC-7360n, is not set up on host machine, 8930-u1604[/SIZE]***
 
Pre-requisites: # Both of these are important!
System OS, Ubuntu 16.04 is current
Target device is online with* static* IP address   # How to set static IP address - read your manual

Installation -download installer from Brother

Go to Brother support website
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7360n_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7360n_all&os=128)
Select OS - Linux(deb) Language - English
Click 'Driver Install Tool'
new window with heading, 'Follow the Steps below to Download'
    You can click on Compatible Model to check if your model is listed
    Read Notes before downloading
Click to Agree to the EULA and Download
new page opens, Driver Install Tool
# Read, or copy & save 'How to Install'

# How to Install Instructions from Brother download page ######################
Step1. Download the tool.(linux-brprinter-installer-*.*.*-*.gz)
The tool will be downloaded into the default "Download" directory.
(The directory location varies depending on your Linux distribution.)
e.g. /home/(LoginName)/Download
Step2. Open a terminal window and go to the directory you downloaded the file to in the last step.
Step3. Enter this command to extract the downloaded file:
Command: gunzip linux-brprinter-installer-*.*.*-*.gz
Step4. Get superuser authorization with the "su" command or "sudo su" command.
Step5. Run the tool:
Command: bash linux-brprinter-installer-*.*.*-* Brother machine name
Step6. The driver installation will start. Follow the installation screen directions.
 
 When you see the message "Will you specify the DeviceURI ?",
 For USB Users: Choose N(No)
 For Network Users: Choose Y(Yes) and DeviceURI.
The install process may take some time. Please wait until it is complete.
# End of Brother Install Instructions ######################################

# This is the download destination that shows the downloaded file
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ ls -l
total 28
-rw-rw-r-- 1 hugh hugh 21813 Apr 26 14:29 linux-brprinter-installer-2.0.0-1.gz

# The file was downlloaded as a *.gz file, here is where we extract using gunzip
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ gunzip linux-brprinter-installer-*.*.*-*.gz

# Here is the extracted file
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ ls -l
total 92
-rw-rw-r-- 1 hugh hugh 92056 Apr 26 14:29 linux-brprinter-installer-2.0.0-1

# This is where we run the install script to install and configure the printer
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ sudo su
[sudo] password for hugh: 
root@8930-u1604:/home/hugh/Documents/Acer_8930g/MFC7360n# bash linux-brprinter-installer-2.0.0-1 MFC7360N
You are going to install following packages.
   mfc7360nlpr-2.1.0-1.i386.deb
   cupswrapperMFC7360N-2.0.4-2.i386.deb
   brscan4-0.4.3-3.amd64.deb
   brscan-skey-0.2.4-1.amd64.deb
OK? [y/N]y (enter) (You will need to concur with a couple of agreements)
After last agreement, install script begins to run. You will see some activity on the terminal, then comes question, "Will you specify the Device URI? [Y/n] ->" Enter (for network installation)
Listing appears - this is what mine looks like... (refer to attached image "Choose_device.png")

```

0: beh
1: socket
2: lpd
3: ipps
4: ipp14
5: https
6: ipp
7: http
8: hp
9: hpfax
10: dnssd://Brother%20MFC-7360N._pdl-datastream._tcp.local/
11: lpd://MFC7360N/BINARY_P1
12 (I): Specify IP address.
13 (A): Auto. (dnssd://Brother%20MFC-7360N._pdl-datastream._tcp.local/)

select the number of destination Device URI. ->12

 enter IP address ->192.168.1.99
lpadmin -p MFC7360N -v socket://192.168.1.99 -E
Test Print? [y/N] ->y

 enter IP address ->192.168.1.99
lpadmin -p MFC7360N -v socket://192.168.1.99 -E
Test Print? [y/N] ->y

wait 5s.
lpr -P MFC7360N /usr/share/cups/data/testprint
```
# Test page prints out
```
You are going to install following packages.
   brscan4-0.4.3-3.amd64.deb
```
=========================================
# Another Brother License Agreement
=========================================
Do you agree? [Y/n] ->y
=========================================
# Another Brother License Agreement
=========================================
```
Do you agree? [Y/n] -> (enter)

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/brscan-skey-0.2.4-1.amd64.deb
--2016-04-26 16:10:15--  http://www.brother.com/pub/bsc/linux/packages/brscan-skey-0.2.4-1.amd64.deb
Resolving www.brother.com (www.brother.com)... 23.67.251.32, 23.67.251.34
Connecting to www.brother.com (www.brother.com)|23.67.251.32|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 50852 (50K) [text/plain]
Saving to: ‘brscan-skey-0.2.4-1.amd64.deb’

brscan-skey-0.2.4-1.amd64.deb  100%[=================================================>]  49.66K  --.-KB/s    in 0.04s   

2016-04-26 16:10:15 (1.25 MB/s) - ‘brscan-skey-0.2.4-1.amd64.deb’ saved [50852/50852]

dpkg -i --force-all brscan-skey-0.2.4-1.amd64.deb
Selecting previously unselected package brscan-skey.
(Reading database ... 238461 files and directories currently installed.)
Preparing to unpack brscan-skey-0.2.4-1.amd64.deb ...
Unpacking brscan-skey (0.2.4-1) ...
Setting up brscan-skey (0.2.4-1) ...
brsaneconfig4 -a name=MFC-7360N model=MFC-7360N ip=192.168.1.99
root@8930-u1604:/home/hugh/Documents/Acer_8930g/MFC7360n# exit
exit
hugh@8930-u1604:~/Documents/Acer_8930g/MFC7360n$ 
```

# That completes the installation and setup. The test page printed out, so it works; however, I have read that some folks get a test page printed out then can not scan or print, so let's try that. This will verify the installation and configuration.

# Verify the scan and print functions of the MFC7360n
Using SimpleScan, scan the previously printed Test Page then save it and print it out.
Test page is scanned satisfactorially using scan function of MFC7360n. (Refer to attached image "Scanned_page.png")
Save the test page – page gets saved as a pdf file
Print the saved pdf using MFC7360n
Page prints out - Verified Success!

It is my hope that anyone who follows these instructions finds success also.[ATTACH=CONFIG]269132[/ATTACH][ATTACH=CONFIG]269133[/ATTACH]

Shot, it worked... I didn't use all the *** whatsoever things.. now it worked like a charm and installed. Will have to test out the scan part!

---

