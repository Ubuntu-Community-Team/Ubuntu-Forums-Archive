---
title: "StrongDC++ 2.30 Success Story"
date: 2010-01-16
forum: Wine
---

### Post by MarkC502 on 2010-01-16
Thought I would make this thread since I had some good success with an old lost friend. I hadn't seen my old friend StrongDC++ for several years for 2 simple reasons 

1. I use Linux on almost all my boxes and only work on Windows boxes as work. 
2. I had fallen to the Bit Torrent monster and allure of private BT sites speed and encryption and since there are many torrent clients available for Linux which work as well as their Windows counterparts I was pacified. 

But sometimes you want rare files or as many public torrent sites are being shut down or turning to ad spewing garbage you need to turn to other options. So I looked at DC++ clients compiled for Linux and didn't like what I saw as standard DC++ has no multi-segment download capability which means you can only download a single file from a single user at any 1 time ( = SLOW DOWNLOADS ), no insult to the people who develop LinuxDC++ as I think anyone building apps for Linux is a excellent human being but I want my box to download like a angry velociraptor so I had to look elsewhere. I have had a few bad experiences trying to play games in Wine so I admit I have mostly dismissed it as too buggy for me, but I got fired up the other day to find a good DC++ solution for a 9.04 MiniITX box I run as a 24/7/365 DL box and I decided to try Wine and StrongDC++ since I just happened to see a few people reporting acceptable success with it in old posts. I decided to try and see if the newest version of StrongDC++ would run on Ubuntu 9.04 reliably. In short I was amazed at the performance of my old friend and I have it setup for roughly 400KB Down / 60KB Up ( the one negetive is that you have to at least give 1KB upload for every 7KB download speed, thats still pretty leachy compared to 1:1 ) - I was able to quickly get 350-400KB a sec with several large ( 700MB ) video files downloading which is much faster than a single segment download could provide.

STEPS TO INSTALL -- StrongDC++ 2.30 -- TESTED ON UBUNTU 9.04 ONLY

1. Installed the latest version of Wine from WineHQ repositories by adding their repository and GPG key to my sources ( I will explain how to do that below )

2. I installed Wine 1.1.36 in synaptic from the WineHQ repositories I just added. 

3. I copied the latest StrongDC++ windows binary build over to my wine C: drive into a new folder called "StrongDC++" The location is shown below ( replace "YourName" with your username ). Note the .wine directory is only visible when you select to view hidden files ( Nautilus menus -> View -> Check "Show Hidden Files".

/home/"YourName"/.wine/drive_c/StrongDC++ 

4. I readied a drive to be my download drive by creating a few folders -> Folder DC++ with sub folders of -> TEMP, DOWNLOADED & SHARED. I do this on a seperate drive partition but you could put these folders under your .wine/drive_c/StrongDC++ directory if your Ubuntu has a very large ammount of free space ( 100GB +)

5. I copied files to be my shared files ( most DC++ hubs require you to share something, some have more stringent rules than others ) to my StrongDC++/SHARED directory ( You can start with just a few GB but may want to eventually share 30-100 GB to get into better hubs with more quality users ). You can share almost anything and you could always find cool legal stuff to share ( Ubuntu ISO's Etc ). StrongDC has several hub lists built in and that should get you started on finding some good hubs to visit :-) 

6. I can now launch StrongDC++ with the command below. ( Replace "YourName" with your username without quotes ).

wine /home/"YourName"/.wine/drive_c/StrongDC++/StrongDC.exe


END RESULTS

Very minor bugs seen present were as follows.

1. A few hubs that wont connect ( unsure if it is hub prob, strongdc prob or wine prob ) - FIX = Who cares as most hubs ( 85%) work fine.

2. A couple times text lists didn't display correctly or ghosted out - FIX = Just minimize to tray and then restore and was corrected in my instance.

3. StrongDC++ has crashed 2 times in 2 days , but always while I was messing around in the interface with 5-6 hubs connected and searching Etc so I am not to angry about an occasional crash when messing with multiple windows. This has not happened when program is in tray minimized mode and I have downloaded 10GB of stuff in less than 2 days time without trying hard. FIX = Just live with it as I found there was no damage to your temp downloaded files and it restarts easily.

My Verdict = The bugs are more than worth the multi-segment downloading capability of this client as it can be almost as fast as getting a file via Bit Torrent and the DC++ network has many more rare files than any BT trakker could ever dream of.


-----------------------------------------------------------------------------------------

INSTALLING WINE-HQ REPOSITORIES FOR UBUNTU 9.04
This is so you can get the latest version of Wine for your 9.04 ( don't use these commands with another Ubuntu version this is for 9.04 jaunty only ). I did not test this for 9.10 at all -- so I am unsure of Wine version for 9.10 and whether it will play nice with StrongDC , but I believe you can get Wine 1.1.36 like I used from the Ubuntu Repositories in 9.10 so check as you may be OK with the stock Ubuntu wine version.

Here's a script to install the latest version of Wine from WineHQ by adding their repositories to your software sources and then installing Wine. You can ( and I heartily recommend you do to all scripts you find ) open my script and see what it does then either run the commands one by one in a terminal or make my script file executable and run it. 


Later All,
MarkC

---

