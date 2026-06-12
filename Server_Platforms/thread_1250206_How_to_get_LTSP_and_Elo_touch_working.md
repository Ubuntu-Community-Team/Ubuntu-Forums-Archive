---
title: "How to get LTSP and Elo touch working"
date: 2009-08-26
forum: Server Platforms
---

### Post by smaclean on 2009-08-26
I've spent countless hours over the past month trying to get a project involving Ubuntu LTSP and Elo 15" touch monitors working successfully. There is poor and sporadic documentation all over the internet, but none I found were complete or worked. In the hopes that I can save others the headache and frustrations, I have put together a quick tutorial of how to do this successfully.  
 

 The steps below outline my steps used to exactly successfully recreate the LTSP server with Elo Touch support for the thin clients. I must note  was unsuccessful with earlier versions of Ubuntu, but since getting this working on 9.04 I have not tried to duplicate the same steps on previous versions. 


 My LTSP Server Specs
 Dell PowerEdge 2970 Quad Core
 Dual GB nics, both enabled and connected to the lan (for ease of installation, I advise that you ensure there are 2 nics in the computer to run the LTSP server).
 8 gb ram
 500 gb RAID 1
 

 Thin Client Specs
 Zotac ION X-C-U Mini-ITX fanless motherboard with external PSU
 1 gb memory
 no hdd
 bios set to boot to nvidia boot agent
 
STEP 1. - GETTING THE CORRECT ISO
 
Download the Ubuntu 9.04 alternate iso from here;
 [http://releases.ubuntu.com/9.04/ubuntu-9.04-alternate-i386.iso](http://releases.ubuntu.com/9.04/ubuntu-9.04-alternate-i386.iso)
 

 STEP 2. - INSTALLATION
 

 Insert the disk in your server and boot from the cd, at the first installation menu, before proceeding choose F4, and then select LTSP server. Now continue the install as you normally would. During some point of the install process, you will be asked to select the primary network interface, choose eth0. Continue.
 

 In my case, I have the primary network card receiving a static dhcp entry from our dhcp server based on it's mac address. Most of the documentation you will find will tell you to statically assign one. Choose whichever method works best for you.
 

 After the install is complete, and the server boots to the login screen, your thin-clients should be able to connect already.
 

 STEP 3. - UPDATE ELOGRAPHICS DRIVER
 

 Now you need to login to your server and sudo to the chroot.
 Open a terminal and type;
 ```
sudo chroot /opt/ltsp/i386
 apt-get update
```
 ensure the Elographics driver is the latest;
 ```
apt-get install xserver-xorg-input-elographics
```
 STEP 4. - XORG.CONF
 

 In most of the documentation I found regarding the lts.conf USE_TOUCH config options did not work for me. In fact, they seem to be completely ignored and I am thinking maybe these options no longer work in lts.conf config file. The only way I could get this to successfully work is to create an xorg.conf file in the chroot directory, and I couldn't successfully calibrate the Elo touch screen using a USB connection, so I advise using the serial connection and ttys0.
 

 Create the lts.conf file;
 ```
sudo chroot /opt/ltsp/i386
 apt-get install nano   (I like nano)
 nano /etc/X11/xorg.conf
```
 Now copy and paste the following in to your xorg.conf file and save it;
 

 ```
Section "ServerLayout"
         Identifier      "DefaultLayout"
         InputDevice     "TouchScreen"   "SendCoreEvents"
 EndSection
 

 Section "InputDevice"
        Identifier  "TouchScreen"
        Driver      "elographics"
        Option      "Device"           "/dev/ttyS0"
        Option      "DeviceName"       "Elo"
        Option      "MaxX"             "3588"
        Option      "MinX"             "433"
        Option      "MaxY"             "3526"
        Option      "MinY"             "569"
        Option      "UntouchDelay"     "5"
        Option      "ReportDelay"      "5"
        Option      "AlwaysCore"
 #       Option  "debuglevel"    "5"
 EndSection
 
``` Exit your chroot environent by pressing ctrl + d or simply typing exit
 

 STEP 5. - UPDATE IMAGE
 

 Now your chroot environment is ready to be updated. Any time a change is made within the chroot environment, you need to update the image. To update the image
 

 ```
sudo ltsp-update-image
```
 The image will now be rebuilt and updated.
 

 STEP 6. - LTS.CONF
 Now create your lts.conf, this will allow you change many options, like auto login, define which apps will run locally to the thin-client, etc... without rebuilding your image.
 

 Create the lts.conf file;
 

 ```
sudo chroot /opt/ltsp/i386
 nano /var/lib/tftpboot/ltsp/i386/lts.conf
```
 Here is my lts.conf you can use as a sample;
 ```
 
 [default]
 LDM_DIRECTX     = True
 LOCAL_APPS_MENU = True
 LOCAL_APPS_MENU_ITEMS = firefox
 #LOCALDEV       = True
 #NBD_SWAP       = True
 #SYSLOG         = server
 #X_COLOR_DEPTH  = 16
 SCREEN_02       = shell
 SCREEN_07       = ldm
 

 

 #[192.168.1.180]
 LDM_AUTOLOGIN   = True
 LDM_USERNAME    = laser1
 LDM_PASSWORD    = laser1
 
```
 STEP 7. - THIN CLIENT
 

 Connect the Elo touch monitor using the serial cable to com 1 on the pc you are using as the thin – client. Ensure the bios is set to boot to network (PXE boot, boot agent, etc..). You don't need a hard drive at all when using the network boot.
 

 Power on your thin-client and it should find the broadcast from your server, maken the connection, and give you the login screen. And you should now have a working touch screen on your thin client.
 

 Note: I created this guide rather quickly and may have missed some things. Feel free to point out any issues, problems or steps I may have missed. Enjoy!

---

