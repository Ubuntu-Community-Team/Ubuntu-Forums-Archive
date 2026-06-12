---
title: "Seamless MS Windows on Hardy with VirtualBox and Beryl"
date: 2008-06-07
forum: Virtualisation
---

### Post by ashmew2 on 2008-06-07
Edit on Wednesday , August 26 2009. As of the release of Jaunty Jackalope , you dont really require this guide anymore because there's been SO MUCH improvement in Virtualbox , it just makes me do the happy dance.You just have to install Virtualbox , Install the guest additions inside it and select the Seamless Mode from the File Menu. Dont forget to allocate enough RAM.
I'm sorry to all the people i couldnt help out with their problems regarding this thread. Ive been too busy and rarely online.
If you're still interested in reading (or using an ancient version of vbox) , be my guest :D

^**HOWTO FOLLOWS***


It was quite a number of days before that i read the great howto for doing the same thing in Edgy.You can visit the great howto by Mikeytag here : [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

When i upgraded to Hardy , i wasnt able to do it as effectively as i was in Edgy , but with patience and help from numerous places, it is perfect now (Almost). I wont write everything on my own but copy/paste and make amendments from the already mentioned thread.

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Step 1: Install and Configure Virtualbox [/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
VirtualBox is one of the best virtualization apps I have ever seen. I put it right up there against VMWare Workstation, and it tends to perform better in my opinion. For installing VirtualBox , i recommend downloading it from their website : [Download Link]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI"). Just Select Ubuntu 8.04 from the dropdown list and you can download it.

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Step 1a: Setting Up a Virtual Machine[/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
    * Open up the VirtualBox app by selecting it from Applications->System Tools->InnoTek VirtualBox.
    * Click the &#8220;New&#8221; button at the top to bring up the New Virtual Machine Wizard.
    * Click Next
    * Type in a name for your Windows installation. I labeled mine: Windows XP Professional, but you can name yours whatever you feel like.
    * Choose your Os Type from the dropdown. (Important note: this seamless setup will only work with a version of Windows that can act as a Terminal Server that means XP Pro NOT Home, and Vista Business or Ultimate, Windows Server 2003, and/or Windows 2000 Professional)
    * Next adjust your base memory size. VirtualBox recommends 192MB for Windows XP, but I personally find that XP runs a bit slow at this level. I have 1GB of RAM on my machine so I gave XP 400 MB. Choose whatever amount you are comfortable with, and this can always be adjusted later.
    * Next we will choose our &#8220;hard disk&#8221; to boot into. Click the &#8220;New&#8221; button unless you already have a VirtualBox image ready, then click the &#8220;Existing&#8221; button.
    * After clicking New, you will be greeted by the Virtual Disk Wizard, click Next
    * Choose whether or not you want a Dynamically expanding image. I personally like using it because I am not entirely sure how much space I will use, but that it is up to you. After choosing, click Next.
    * Pick a name for your image file and adjust the size to the amount of space you would like to offer for your drive. Then click Next.
    * To finish the new drive creation click Finish
    * Your new disk you just created should be selected, click Next.
    * Click Finish to complete setting up your new Virtual Machine

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Step 1b: Configuring Your Virtual Machine[/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
    * Select your new machine from the list of machines on the left and click the Settings button at the top of VirtualBox.
    * Select CD/DVD-ROM and click Mount CD/DVD Drive, then choose whether or not you would like to mount your physical CD drive or an iso file. ( I personally ripped my XP Install CD to an ISO file because I think the install goes faster than off the physical CD).

* Now, select Network , put a tick in the Enable Network Adapter and Select Adapter Type as Intel Pro 1000/MT Desktop and from the &#8220;Attached to&#8221; dropdown box select Not Attached. .
* Now, select Remote Display and check Enable VRDP Server.
* Finally, click the OK button to save all of these settings.

Ok, we now have our VirtualBox Machine ready to boot up and install windows, however we are going to configure a few things on the Ubuntu side first.

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Step 2: Setup Ubuntu Networking[/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-

Before I go down this road with you there are a few things I need to make known. First, I have only tested this setup on a desktop with a physical, wired network connection. It may work wirelessly, but I have not tested it. Also if you make use of Network Manager, you will need to make sure it doesn't run anymore. You can do that easily, without uninstalling it, by simply creating two files with the word: exit as the only thing in them. Use your favorite editor, mine is pico, and create these files like this:
(Quick pico reference: to exit a file and choose whether or not to save it use: Ctrl+x)

```

sudo pico /etc/default/NetworkManager
sudo pico /etc/default/NetworkManagerDispatcher
```

If you had to add those two files then you can reboot to see that Network Manager will not start up anymore. To turn it back on simply remove those files. If you are sitting there and are thinking &#8220;But I HAVE to use Network Manager, my <insert wireless card here> is only supported by it!&#8221; Then my friend, I apologize but you may be SOL. Start digging through the forums to see if there is an alternative way to run your connection. My guess is there probably is.

Ok, now that that's out of the way let's move on.

# We first need to install some important packages:

```
sudo apt-get install bridge-utils uml-utilities alsa-oss
```

# Next we are going to setup our /etc/rc.local file.

```
sudo gedit /etc/rc.local
```

Append the following information directly above the line that says &#8220;exit 0&#8221;

```
tunctl -t tap0 -u <username>
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 <vbox_ip> up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host <main_ip> dev tap0
 arp -Ds <main_ip> eth0 pub

```
# Ok, there are some EXTREMELY important things to note here.

First off replace <username> with the username you use to login to your Ubuntu desktop. (Mine is michael).

Next, you need to replace <vbox_ip> with an IP that is within your subnet. It doesn't matter what it is, I use 192.168.1.161 simply because it was open. The only requirement is that there isn't another device on your network with this IP. This IP will come in handy when your Windows install is not accessible over the network. Confusing I know, but it will make more sense later.

Next, you need to replace <main_ip> with the IP of your Ubuntu installation on your network. If you use DHCP be careful. I do, but I setup my router to always give me the IP of 192.168.1.160. Static or DHCP, you need to put your IP here.

Lastly, take a look at all the places where I have eth0. For many installations this will probably be your main network device, but it could be something else like ath0,eth1,etc. Make sure you change eth0 to whatever your primary network interface is. (The device that you access the network with)
# Ok, if you feel up to it you can parse out all the lines we just put in the /etc/rc.local file and run them one by one. Or you can easily activate these settings by simply rebooting.

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Step 3: Configure your Windows Virtual Machine[/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-

Ok, now we are going to boot up our Windows Virtual Machine. Go ahead and boot up your VM by opening up Applications->System Tools->Sun xVm VirtualBox and then selecting your virtual machine and clicking the &#8220;Start&#8221; button.

I am not going to walk you through installing Windows, because it is mind numbingly boring and I am betting, that if you are reading this guide, chances are you have wasted many hours of your life reinstalling Windows. When you are done installing it come back to this guide to continue.

Welcome back! I hope you had a fun time. Now there are several Windows settings we will need to do. (Note: These settings worked for me in Windows XP Pro, if you are using another edition of Windows they may be the same, i.e. registry keys and such, or not. However I can personally confirm that they work flawlessly in Windows XP Pro.)

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Get Sound Working !![/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
Before Starting up the newly Installed XP VM , you would want to enable Sound , so Click on Sound put a tick in Enable Sound 
Host Driver :  ALSA 
Controller : AC97

ALSA and AC97 worked for me , so did OSS , but i prefer ALSA. You are free to experiment.
First and Foremostly , you would want to Install the Guest Additions for the VirtualMachine. To do this , Run your XP Virtual Machine and let it reach the Desktop. After that click on Devices in the top bar menu and Select Install Guest Additions , Keep Clicking Next and it will be done.
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-

    * Now what you have to do in Windows is enable Remote Connections and set a password for your user.
    * Go to Start -> Control Panel -> Sytem and click the Remote tab.
    * Check the box that says &#8220;Allow users to connect remotely to this computer&#8221; and click OK
    * In the Control Panel click &#8220;User Accounts&#8221;
    * Click the user that you would like to login as and then click &#8220;Create a password&#8221;
    * Type your password in the boxes provided and then click the &#8220;Create Password&#8221; button.


If you are thinking to yourself, &#8220;Well. it would just be easier to not have a password.&#8221; Stop right there and set one anyway. It is not an issue of security. If you don't setup a password then you will not be able to login to your Windows VM seamlessly.


*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Step 3b : Configuring a Shared Folder[/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
Look on the top bar menus of the Virtual Machine , click "Devices" then Shared Folders.In the new window that opens , click on Machine Folders and then Add (The folder with a + Sign). Now give the path to any of your drives ( I gave the whole /media as i wanted all drives to be accessible).

For Instance :

Folder Path  : /media
Folder Name  : drives

Make Permanent : Yes (Put a tick)
Read Only : (This one is really up to you , I chose no).

Make a note of the name you give to your shared folder. In Windows XP now , click the Start Menu , click Run and type : cmd in the Run Dialog to open the command prompt.In here , type :
```

net use x: \\vboxsvr\share
```

Where X: is the drive letter you want the folder to take and *share* is the name of the Shared folder you made. I chose the name as drives , So i would type :
```

net use g: \\vboxsvr\drives
```

Shared Folders will serve us much in the later steps.

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Step 3c : Configuring XP with Networking[/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-

We are going to need some files for complete configuration of the Virtual Machine, so lets get all of them while we are at it.

Remember to save both these files in the same place for which you have made a shared folder in the previous steps.(I used /media as the example , remember ? )

File #1 :
Files needed for Seamless Remote Desktop
[http://howtoforums.net/downloads/seamlessrdp.zip](http://howtoforums.net/downloads/seamlessrdp.zip)

File #2 :
The Driver for Intel PRO 1000 MT needed for using Network in the XP VM.

[Intel Download Centre]("http://downloadcenter.intel.com/license_agr.aspx?url=/4275/a08/PRO2KXP.exe&ProductID=871&agr=Y&sType=&PrdMap=&DwnldId=4275&strOSs=All&OSFullName=All+Operating+Systems&lang=eng")
You will need to press accept at the bottom of the page.
Note : This Driver is for Windows XP Professional.

After the downloads complete , open up your XP virtual Machine , go to My Computer and then the shared folder you made.

Extract the seamlessrdp.zip to C:\seamlessrdp.
Execute the PRO2KXP.exe to install the Network Driver.

After installing the driver , shut down your XP Virtual Machine. Now click your Virtual Machine and go to Settings > Network.In the attached to drop box , select Host Interface and in the Interface Name field type in: tap0 .You must now be able to browse the web if you followed all the steps correctly.

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Step 4 : Configuring the registry and Accounts in XP.[/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-

Now we are going to adjust a couple registry keys that drove me up the wall. By default XP Pro comes configured to only allow remote access at 16 bit color. Well, frankly this looks like butt on your desktop especially when you have a slick Beryl interface. So we are going to change that.

    * Go to Start and select Run, in the box type regedit and hit OK
    * In the registry editor navigate to the following key: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp
    * In the right hand pane, highlight the ColorDepth key and right-click. Select Modify and change the &#8220;Value Data&#8221; field to 4


Next, we need to set it up so that your Windows install only displays the Task bar and not the desktop on login.

    * In the registry editor navigate to the following key: HKEY_CURRENT_USER\Software\Microsoft\Windows\Current Version\Policies\Explorer
    * Create a new DWORD value that you'll call NoDesktop and set its value to 1


Now, we need to set our Windows install up so that it logs in your specified user in automatically.

    * Go to Start -> Run. type control userpasswords2 into the box and click OK
    * Uncheck &#8220;Users must enter a user name and password to use this computer&#8221; and click Apply
    * A box will come up asking what user name and password you would like to have logged in automatically. Fill this out with whatever user/pass info you have setup.

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
Our last step is to read the network IP that Windows is using

    * Go to Start -> Control Panel -> Network Connections
    * Right click Local Area Connection and click Status
    * Click the Support tab and record the IP Address, it will become important later


Note: This IP address has to be DIFFERENT than the Virtual Box IP that you put in the /etc/rc.local file. If it is not different then configure windows to use a different IP or configure your router to give your Windows install a different IP.
* Finally, go to Start and shut down your Windows installation. Not Reboot, Shut Down.

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="3"]Step 4: Configure your VirtualBox install to run headless and automatically[/SIZE]
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
VirtualBox has this awesome feature where you can run your Virtual Machines headless. Meaning you can start and stop them from the command line and they simply run in the background. Remember when I had you check the box to Enable VRDP? Well, that's what that does. It enables your virtual machine to run headless.

    * First we are going to run your machine from the command line, so in a terminal window type this:
      Code:

      VBoxManage startvm "Windows XP Professional" -type vrdp

      Replace &#8220;Windows XP Professional&#8221; with the name of your virtual machine if it's different.
    * Now we are going to setup Ubuntu to start our Windows installation automatically for us upon login.
    * Go to System->Preferences->Sessions and click the Startup Programs tab
    * Click the Add button and type the command above into the text field and click OK

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
Step 5: Integrate into your Ubuntu panel
Ok, the next step is to run your whole Windows seamless setup. First run the following commands from a terminal window to make sure they work, and then I recommend making a Custom Application Launcher in your Ubuntu Panel. I use this icon if you are looking for a nice one:

[IMG]http://www.creditlearningcenter.com/images/windows_flag.png[/IMG]

(I will assume that most readers know how to do this, right click your top panel and you are on your way )

First we need to make sure that our bottom panel is hideable, so that we can get to our start bar if we want to. You will notice from my screenshot that I have a dual monitor setup and the Windows bar is across the entire bottom of my screen. That is because I moved my bottom panel up to the top of my right monitor so it is out of the way. However, if you don't want to do that, or you only have one monitor then do this:

    * Right click a blank area in your bottom panel and click Properties
    * Check the box that says &#8220;Show hide buttons&#8221; and click OK
    * You will now have a left arrow button on the left and a right arrow button on the right of your panel that will allow you to hide your bottom panel by clicking one of them
    * Next, let's make sure you have rdesktop installed, it should be by default I think:

```
sudo apt-get install rdesktop
```


Now, let's run our Windows install seamlessly for the first time!
OK , now listen up , if you are using ALSA as your sound driver on your Ubuntu Machine but you would still like to have sound in Rdesktop, we will make use of aoss (Alsa-Oss).

    * Open a terminal window and type this:

```
aoss rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <IP recorded from Windows>:3389 -u "<Your Windows Username>" -p <Your Windows Password>
```

# Replace <IP recorded from Windows> with the IP you recorded from Windows earlier. (Gosh, did I even need to type that). Also replace <Your Windows Username> and <Your Windows Password> with your Windows username and Windows password respectively.
# You should have seamless.......OH CRAP the whole desktop is viewable and you are not seamlessly integrated. That is because your Windows install has to be logged off first before seamless ability will work. You may be thinking, &#8220;Michael, you are an idiot.(Oh yeah [:P] , Blame Michael alrite [:P] ) You told me to make my Windows install login automatically!&#8221; Hold your horses. If you didn't do that then you wouldn't get anything to show up at all. For reasons unbeknownst to me, Windows XP will not listen for Remote Connections until you have actually logged in once.
# Simply hold down your alt key and click anywhere on the Windows desktop and move it up so that you can see the Start button.
# Click the Start button and choose Log off.
# Ok, run that command one more time and hope that you followed all the instructions correctly.
Woohoo! You should have seen the desktop flash and you will be presented with a lovely blue Windows taskbar at the bottom of your screen. If your bottom panel is in the way, then just click one of the hide arrows to see your new Windows taskbar.

That's it! Easy huh. Well, it's not too difficult it is just time consuming to setup and get running. Good news is that now you can run it at will by clicking your panel launcher or running the rdesktop command again. Only downside, is that the first time you run it you will have to Log Off once before seamlessness will be in effect. Maybe someone can whip up a VB app that will log out the Windows user only on first login so this is done automatically.

Have fun enjoying your new setup.

P.S. Here are some important things to know about your new setup

   1. If for any reason you cannot get the rdesktop command to actually do anything you can login to your Windows VM by doing this:
      rdesktop -rsound -A -s &#8220;c:\seamlessrdp\seamlessrdpshell.exe c:\windows\explorer.exe&#8221; <your vbox_ip from /etc/rc.local>:3389 -u <Your Windows Username> -p <Your Windows Password>
   
2.If you want to make your XP Windows wobbly as well , hold down ALT when moving them.

*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
[SIZE="6"]Error :No Route to Host[/SIZE]

If everything was running correctly and all of a sudden you start to get No Route To Host errors when trying to connect with rdesktop ,it is probably because the IP in use by your Windows XP machine has been assigned to be the same as the <host_ip> you entered in the rc.local file. To fix it , we must consider changing the IP address of the Windows XP VM by :

# Open the Virtual Box ( Applications > System Tools > Sun xVm Virtualbox)
# Fire up your Windows XP VM by clicking Start.
# Go to Control Panel > Network Connections 
# Right click Local Area Connection and click Properties.Click Internet Protocol (TCP/IP) and then Click Properties.
# In the window that opens , Click Use the Following IP Address :

[SIZE="4"]IP Address[/SIZE] : Must be in the same range as your <main_ip>.For example,my main ip is 192.168.1.3 so i can enter 192.168.1.10 or 192.168.1.15 or 192.168.1.* where * is any number less than 255 ( I think ! ).

[SIZE="4"]Subnet Mask[/SIZE] : XP will fill it up on its own.

[SIZE="4"]Default Gateway[/SIZE] : Remember the part where you noted the IP Address of the XP VM (By going into Status of the Connection). There it showed you the default gateway as well. Use that same info to fill this.
[SIZE="5"]
DNS Servers :[/SIZE]
[SIZE="4"]
Primary DNS Server :
Alternate DNS Server :[/SIZE]

Both of these will be provided by your ISP.
Once you have done this , use the same rdesktop command but this time use the new IP Address (the one u gave just now) instead of the old one and things should go just fine.
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-

---

### Post by ShiftyPowers on 2008-06-07
hey man, great guide...but a simple question on my part.  Can't you just run VirtualBox in Seamless mode and get the same effect?  or am I missing something?

---

### Post by ashmew2 on 2008-06-08
Hey , you can get the same result by using the native seamless mode but that isnt as great as rdesktop. I tried using it but it was quite laggy and the desktop used to flash everytime i clicked the start button. If you want , i could add something to the guide. Open to suggestions [;)]

---

### Post by udz2002 on 2008-06-08
I have 64-bit Ubuntu 8.04 and have Windows Vista Home Premium installed with Virtualbox. I have a wireless connection with Ubuntu and I am having trouble getting and internet connection in Windows Vista/Virtualbox. Anybody have any ideas?

---

### Post by vexorian on 2008-06-08
> **ashmew2 said:**
> Hey , you can get the same result by using the native seamless mode but that isnt as great as rdesktop. I tried using it but it was quite laggy and the desktop used to flash everytime i clicked the start button. If you want , i could add something to the guide. Open to suggestions [;)]
That's because of compiz/beryl.

It is fixeable by making "virtualmachinename [running]" an exception in the window rules compiz fusion plugin (you need to install the compiz fusion config center, or whatever that package is called)

I think another way to fix it is to install a certain tweak to windows XP, I've seen it in some virtualbox thread in these forums, the tweak requires your windows XP to have .net though.

But really, the exception in windows rules' works quite well, got compiz and seamless windows working nicely.

I think rdesktop makes the windows run quite slow?

---

### Post by ashmew2 on 2008-06-09
> **vexorian said:**
> 
I think rdesktop makes the windows run quite slow?

Nope , not at all acctually , It runs with great speed and with beryl efects. It depends on how much RAM you have , 400 MB for the XP is making it run at optimal speed.

---

### Post by vexorian on 2008-06-09
Ok then, still seamless windows + the exception for "ARGB visuals" seem easier to setup.

---

### Post by lmellor on 2008-06-17
I can't quite get this working

I enter...

```
aoss rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.168.0.4:4321 -u "xp" -p 1
```

and I get a window open displaying the windows login screen (I have already logged out at this point).

If I enter 10.0.2.15 (the vbox IP address) instead of 192.168.0.4 (the bridge IP) then nothing happens, I am presented with...

```
Autoselected keyboard map en-gb
```

but nothing happens, the terminal just sits there.

I have been using the built in seamless side of things as a workaround but I really want to get the rdesktop method running so that I can simply load photoshop from a launcher without having to display a windows desktop at all.

here is the output of ifconfig on my machine...

```
br0       Link encap:Ethernet  HWaddr 00:04:4b:06:54:ac  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe06:54ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2424915 (2.3 MB)  TX bytes:63396525 (60.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:04:4b:06:54:ac  
          inet6 addr: fe80::204:4bff:fe06:54ac/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:30771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2857137 (2.7 MB)  TX bytes:63615925 (60.6 MB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28963026 (27.6 MB)  TX bytes:28963026 (27.6 MB)

tap0      Link encap:Ethernet  HWaddr 00:ff:1c:16:f1:7f  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:1cff:fe16:f17f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1258 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I do hope someone can be of some assistance.

---

### Post by kcnnc on 2008-06-17
Is it possible to install and use virtualbox on ubuntu server without X installed?

Update:
Answered my own question here: [http://ubuntuforums.org/showthread.php?t=833923](http://ubuntuforums.org/showthread.php?t=833923)

---

### Post by aaronfay on 2008-06-26
All I can say is "Thank you!"

I can finally run my 'must have' windows apps in ubuntu...

Cheers,
Aaron

---

### Post by Canis familiaris on 2008-06-26
Another alternative way is not to run Windows seamless but run it workspace 2 fullscreen mode so that you can just flip the cube and switch b/w Windows and Ubuntu. Personally I prefer this to the seamless mode.

See this thread:
[http://ubuntuforums.org/showthread.php?t=840317](http://ubuntuforums.org/showthread.php?t=840317)

---

### Post by 1467 on 2008-07-20
> Next, you need to replace <vbox_ip> with an IP that is within your subnet.with in my subnet what do u mean ?
is it this subnet mask:255.255.255.0 under connection information?

---

### Post by ashmew2 on 2008-07-20
<vbox_ip> means that you need to put an IP that is within the lines of 192.168.1.* because you're using 192.168.1.x as your ip.. Even if you are using an IP like PPP.PP.PPP.X , just replace the X by another number and that will be inside your subnet. I use 192.168.1.10 because i use IP 192.168.1.3.

---

### Post by jkyahoo101 on 2008-07-20
I have a question. I have Ubuntu 8.04 installed inside of my XP install using that Wubi program. I need XP for games and some applications. One of the games I play is Crysis. I would like to know how much slower Crysis would run in a virtual box compared to regular XP if I did a full install of Ubuntu 8.04 and set up XP in the virtual box.

Just in case here are my pc's specs.

Pentium D Dual 3Ghz processors
2Gb of ram
Nvidia 512Mb 8600GS graphics card

---

### Post by yogibaer on 2008-07-20
Hey guys,

I just tryed to go over that description but it seems that my Ubuntu don't want to see me happy ^^.

My problem started when I made the entries on th rc.local.

After rebooting, I don't have a Internetconnection anymore and I don't know why.(I still disabeld the Networkmanager).

Here's what ifconfig told me(some parts are in german but I think the important one are in ENglish (i hope so ^^)):

```

br0       Link encap:Ethernet  Hardware Adresse 00:1a:4d:49:b6:e7  
          inet Adresse:192.168.2.37  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21a:4dff:fe49:b6e7/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:4517 (4.4 KB)  TX bytes:3601 (3.5 KB)

eth0      Link encap:Ethernet  Hardware Adresse 00:1a:4d:49:b6:e7  
          inet6-Adresse: fe80::21a:4dff:fe49:b6e7/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metrik:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:9170 (8.9 KB)  TX bytes:7603 (7.4 KB)
          Interrupt:219 Basisadresse:0x2000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1772 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:76152 (74.3 KB)  TX bytes:76152 (74.3 KB)

tap0      Link encap:Ethernet  Hardware Adresse 00:ff:e6:97:e6:66  
          inet Adresse:192.168.2.161  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: fe80::2ff:e6ff:fe97:e666/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Here is the stuff i added in the rc.local (My subnetrange is 192.168.2.X)

```

tunctl -t tap0 -u smusiol
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.2.161 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.2.37 dev tap0
 arp -Ds 192.168.2.37 eth0 pub

```

and here's my /etc/network/interface

```

iface eth0 inet static
address 192.168.2.37
netmask 255.255.255.0
gateway 192.168.2.1

auto eth0

```

Can somebody help me?

thanks

yogi

---

### Post by steveneddy on 2008-07-20
Why are you running Beryl?

Beryl is dead.

Use Compiz Fusion.

---

### Post by ashmew2 on 2008-07-20
> **jkyahoo101 said:**
> I have a question. I have Ubuntu 8.04 installed inside of my XP install using that Wubi program. I need XP for games and some applications. One of the games I play is Crysis. I would like to know how much slower Crysis would run in a virtual box compared to regular XP if I did a full install of Ubuntu 8.04 and set up XP in the virtual box.

Just in case here are my pc's specs.

Pentium D Dual 3Ghz processors
2Gb of ram
Nvidia 512Mb 8600GS graphics card

I doubt that Crysis will run at all inside a Virtual Box , You could try running it on Ubuntu using something like Wine or Cedega.

---

### Post by yogibaer on 2008-07-23
can anybody helps me out with the Internetconnection problem 2 Posts above?

btw. i have a wired Networkconnection, if it matter.

It would be nice if i get this to work because i work a lot with Adobe Products.

thanks
Yogi

---

### Post by Mr. Chambers on 2008-07-23
> **yogibaer said:**
> Hey guys,

I just tryed to go over that description but it seems that my Ubuntu don't want to see me happy ^^.

My problem started when I made the entries on th rc.local.

After rebooting, I don't have a Internetconnection anymore and I don't know why.(I still disabeld the Networkmanager).

Here's what ifconfig told me(some parts are in german but I think the important one are in ENglish (i hope so ^^)):

```

br0       Link encap:Ethernet  Hardware Adresse 00:1a:4d:49:b6:e7  
          inet Adresse:192.168.2.37  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21a:4dff:fe49:b6e7/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:4517 (4.4 KB)  TX bytes:3601 (3.5 KB)

eth0      Link encap:Ethernet  Hardware Adresse 00:1a:4d:49:b6:e7  
          inet6-Adresse: fe80::21a:4dff:fe49:b6e7/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metrik:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:9170 (8.9 KB)  TX bytes:7603 (7.4 KB)
          Interrupt:219 Basisadresse:0x2000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1772 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:76152 (74.3 KB)  TX bytes:76152 (74.3 KB)

tap0      Link encap:Ethernet  Hardware Adresse 00:ff:e6:97:e6:66  
          inet Adresse:192.168.2.161  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: fe80::2ff:e6ff:fe97:e666/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Here is the stuff i added in the rc.local (My subnetrange is 192.168.2.X)

```

tunctl -t tap0 -u smusiol
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.2.161 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.2.37 dev tap0
 arp -Ds 192.168.2.37 eth0 pub

```

and here's my /etc/network/interface

```

iface eth0 inet static
address 192.168.2.37
netmask 255.255.255.0
gateway 192.168.2.1

auto eth0

```

Can somebody help me?

thanks

yogi

I'm having the EXACT same trouble as Yogi when trying this.  Following the guide, and I lose internet/network access on my workstation (host and VM obviously).  I'm certain I'm missing something since so many others have gotten this to work - but I'm not sure what it might be!  Any help is much appreciated.

---

### Post by DonnyB4e56 on 2008-07-24
Thank's so much, this is exacally what I was looking for.

---

### Post by beanfield on 2008-08-01
> **Mr. Chambers said:**
> I'm having the EXACT same trouble as Yogi when trying this.  Following the guide, and I lose internet/network access on my workstation (host and VM obviously).  I'm certain I'm missing something since so many others have gotten this to work - but I'm not sure what it might be!  Any help is much appreciated.

I'm also having the EXACT same problem.  My host ip is 10.0.2.232 (main_ip)and I've found an empty ip in my subnet 10.0.2.7 which I assign as the (vbox_ip).  eth0 is my network card (the only physical card installed), and it's hard wired with a static ip.  We don't use dhcp. 

```

tunctl -t tap0 -u eric
chmod 0666 /dev/net/tun
/usr/sbin/brctl addbr br0
/sbin/ifconfig eth0 0.0.0.0 promisc
/usr/sbin/brctl addif br0 eth0
/sbin/dhclient br0
/usr/sbin/brctl addif br0 tap0
ifconfig tap0 10.0.2.7 up
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
route add -host 10.0.2.232 dev tap0
arp -Ds 10.0.2.232 eth0 pub
```

As soon as I restart the network, my box can't even resolve it's own hostname.  Any ideas?   The line "/sbin/dhclient br0" times out (as it should because we don't have dhcp), I assume it's safe to remove this completely?

---

### Post by beanfield on 2008-08-01
I found another method here [http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/](http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/)

It worked well for me.

---

### Post by jack frost on 2008-08-01
> **jkyahoo101 said:**
> I have a question. I have Ubuntu 8.04 installed inside of my XP install using that Wubi program. I need XP for games and some applications. One of the games I play is Crysis. I would like to know how much slower Crysis would run in a virtual box compared to regular XP if I did a full install of Ubuntu 8.04 and set up XP in the virtual box.

Just in case here are my pc's specs.

Pentium D Dual 3Ghz processors
2Gb of ram
Nvidia 512Mb 8600GS graphics card
with that set up .. is it seamless desktop .. using that wubi program?

---

### Post by maphilli14 on 2008-09-17
This one bugged me for quite some time and because this article is SO rich and through, I thought I'd add my findings here to help even more.

Ubuntu Hardy on a Lenovo T61 laptop.  Using Virtualbox 2.0.2 and WinXP.

Rdesktop 1.6 (manually compiled), I got sound via this:

```
rdesktop -r sound:remote:$AUDIODEV
```

Thanks for the great article!

Mike

---

### Post by jamesisin on 2008-09-18
For whatever reason, I managed to install using both Synaptic and by direct download from Sun.  This has totally hosed things.  I was able to back out the Synaptic installation easily enough.  Now, can someone explain how I might uninstall the version I downloaded from Sun manually?  I just want to start over but I can't do anything until all traces of the former installations are gone.

---

### Post by maphilli14 on 2008-09-19
> **jamesisin said:**
> For whatever reason, I managed to install using both Synaptic and by direct download from Sun.  This has totally hosed things.  I was able to back out the Synaptic installation easily enough.  Now, can someone explain how I might uninstall the version I downloaded from Sun manually?  I just want to start over but I can't do anything until all traces of the former installations are gone.

You should be able to open the downloaded .deb (the one from Sun) and then after it opens you have the option (or should have the option) to remove/uninstall.

HTH,

Mike

---

### Post by maphilli14 on 2008-09-19
Anyone having any success with WiFi bridging into the same bridge as the physical ethernet?  As in attached .png


TIA,

Mike

---

### Post by jamesisin on 2008-09-20
@maphilli14 - Thanks.  You are near correct.  I downloaded the most recent version from Sun and was able to install it using the deb package.  There is no uninstall option that I can find.  I thought it may show after I finished installing the new package.  No such luck.  However, now that I have reinstalled the latest version I am able to open VirtualBox fine.

I would like to know how to uninstall deb packages which have been installed outside Synaptic in case that is useful in the future.  Is there a command which does that?

---

### Post by lmellor on 2008-09-20
> **jamesisin said:**
> @maphilli14 - Thanks.  You are near correct.  I downloaded the most recent version from Sun and was able to install it using the deb package.  There is no uninstall option that I can find.  I thought it may show after I finished installing the new package.  No such luck.  However, now that I have reinstalled the latest version I am able to open VirtualBox fine.

I would like to know how to uninstall deb packages which have been installed outside Synaptic in case that is useful in the future.  Is there a command which does that?
As far as I know they show up in synaptic once they're installed, always worked for me anyway.  Does anybody know if it's possible to use the media center side of windows through virtualbox to an xbox 360?  I've searched but so far not found anything helpful, would be nice though, I could run it in the background rather than having to keep fiddling with fuppes (which is a royal pain in the ****).

---

### Post by sayakb on 2008-09-20
Belongs to tutorials and tips.

---

### Post by Rocket2DMn on 2008-09-20
Moved to the Virtualization forum and added link to [this sticky]("http://ubuntuforums.org/showthread.php?t=781575").

---

### Post by sayakb on 2008-09-20
Thanks Connor :)

---

### Post by mr_byte on 2008-09-29
I had network problems when I first tried this, because I use Network Manager for my WiFi connections.

I have since switched to redirecting the RDP port on the VM to a real port on the host, then I connect via that.

Here's the script:

```

VBoxManage startvm "Seamless" -type vrdp
VBoxManage setextradata "Seamless" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/Protocol" TCP
VBoxManage setextradata "Seamless" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/GuestPort" 3389
VBoxManage setextradata "Seamless" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/HostPort" 6666

```

This has worked to perfection before.

Now I'm on Sabayon (Gentoo based distro) and I can't get the seamless to be seamless.  I get the big blue window, even though all is set up as it should be.

Any hints on what the XP tweak is that requires .net? 

Jeff

Edit: I've got the problem(s) fixed here, I'm in the process of writing a new tutorial.

---

### Post by numbercruncher86 on 2008-10-17
Hi,

is it possible to run a DVD fluent on the virtual machine? It is not the case with mine :confused: :(

thx

---

### Post by Arl on 2008-10-17
> **ashmew2 said:**
> 

After installing the driver , shut down your XP Virtual Machine. Now click your Virtual Machine and go to Settings > Network.In the attached to drop box , select Host Interface and in the Interface Name field type in: tap0 .You must now be able to browse the web if you followed all the steps correctly.



I didn't do something correctly. I think I am a little confused in the earlier section 2, because I can't connect to the internet.

> 
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-
Step 2: Setup Ubuntu Networking
*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-*-*--*-*-

Before I go down this road with you there are a few things I need to make known. First, I have only tested this setup on a desktop with a physical, wired network connection. It may work wirelessly, but I have not tested it. Also if you make use of Network Manager, you will need to make sure it doesn't run anymore. You can do that easily, without uninstalling it, by simply creating two files with the word: exit as the only thing in them. Use your favorite editor, mine is pico, and create these files like this:
(Quick pico reference: to exit a file and choose whether or not to save it use: Ctrl+x)

Code:

sudo pico /etc/default/NetworkManager
sudo pico /etc/default/NetworkManagerDispatcher

If you had to add those two files then you can reboot to see that Network Manager will not start up anymore. To turn it back on simply remove those files. If you are sitting there and are thinking “But I HAVE to use Network Manager, my <insert wireless card here> is only supported by it!” Then my friend, I apologize but you may be SOL. Start digging through the forums to see if there is an alternative way to run your connection. My guess is there probably is. 

I can't kill Network Manager. I assume that instead of pico, gedit is ok (I just started running Ubuntu so I am still trying to understand it all)? Any trouble shooting advice?

Thanks

---

### Post by ashmew2 on 2008-10-19
You cant connect to the internet on Ubuntu or with XP ?

---

### Post by Arl on 2008-10-20
> **ashmew2 said:**
> You cant connect to the internet on Ubuntu or with XP ?

Sorry about that, with XP set-up. Actually I'm trying out Vista and it has been pretty much the same steps the entire way. I think the issue is with Network Manager in Ubuntu, because I didn't really understand the part in Step 2 about exiting Network Manager.

---

### Post by adroitster on 2008-11-10
When I was reading this post I found that closing network manager wad not a very good idea , so I tried to make sense of every thing given in the internet setup part and came up with the following this works pretty much well for my computer and the internet is working in my guest windows xp

make your /etc/network/interface look like this



auto lo
iface lo inet loopback


#setting up the network bridge

auto br0
iface br0 inet static #or dhcp instead of static according to the network
address <your real ip> # remove this line if using dhcp instead of static
netmask 255.255.0.0    # remove this line if using dhcp instead of static
gateway 172.16.250.250 # remove this line if using dhcp instead of static
bridge_ports eth0 
bridge_maxwait 0


after this go to terminal and give the following command 

sudo VBoxAddIF vbox0 saurabh br0

this should output the following if everything goes right:

VirtualBox host networking interface creation utility, version 1.6.6
(C) 2005-2007 Sun Microsystems, Inc.
All rights reserved.

Creating the permanent host networking interface "vbox0" for user saurabh.

Last step :

now open the virtualbox setting for the vm and select network as NAT and put 'vbox0' in the next empty field .That's it your are done with setting networking for both host and guest.

P.S.:remember to your automatic ip detection in your windows setting if you are using some static there.

I think these steps are less complicated and takes less time to setup without closing network manager

@ashmew2 You have written one of the best guides I have seen for seamless windows installation in ubuntu, thank you.

:guitar:

---

### Post by Ng Oon-Ee on 2009-02-03
The latest VirtualBox (2.1) is very easy to setup, Host Networking basically took everything and ran with it (though I bridged my wireless/ethernet together to take away some configuration work I'd otherwise have to do). Was wondering if anyone could advise on the following...

Would it be possible to do the above, using totally 'virtual' interfaces? That is, could I within Ubuntu (Intrepid, but I guess this would apply to all) create some sort of virtual ethernet which only communicates with the LAN connection (virtual as well) within my VM? This would be secure, I figure, you could just create your own network and none of the traffic would ever get to your main network connection. Since your VMs can have up to 4 network connections, you could set one to Host Interface just for internet connectivity, and a second one just for this virtual LOCAL network (LOCAL meaning within your machine).

Would that be possible?

---

### Post by riger99 on 2009-02-14
> **adroitster said:**
> 

Last step :

now open the virtualbox setting for the vm and select network as NAT and put 'vbox0' in the next empty field .That's it your are done with setting networking for both host and guest.


:guitar:

I'm working in Hardy (8.04) right now and there is no empty field to type 'vbox0' when selecting NAT.
The only way that empty field becomes available is if you select 'Internal Network' - Which we don't want (I think).

So... is there a workaround for this?

---

### Post by riger99 on 2009-02-14
Please can anyone help? Everything was okay until I got to:

```
sudo gedit /etc/rc.local
```

and included the following:

```
tunctl -t tap0 -u riger
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth1
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 172.18.2.200 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 172.18.2.107 dev tap0
 arp -Ds 172.18.2.107 eth1 pub
```

My eth1 card connects me and is the working (wired) card. As soon as I make the changes and reboot, then I cannot connect anywhere. If I use ifconfig, I can see the settings are correct - but I just can't get web (or any) network access.

Anyone have any ideas on this - Please?

---

### Post by dr_serious on 2009-04-18
Hi,
I have done step 2 completely and when I want to start my xp for the first time it gives an error:


Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either run 'chmod 0666 /dev/net/tun' or change the group of that node and make yourself a member of that group. Make sure that these changes are permanent, especially if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}


after I change the chmod, I try to start it again then I get this:

Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

I'm using the latest version of KUbuntu and the latest version of virtualbox

Like I said before every thing went perfect untill the 3th step the only thing I didn't could find was at step 1b "# Now, select Remote Display and check Enable VRDP Server." so I just skipped that...

This is my rc.local file:
```

tnctl -t tap0 -u fre
chmod 0666 /dev/net/tun
/user/sbin/brctl addbr br0
/sbin/ifconfig eth0 0.0.0.0 promisc
/user/sbin/brctl addif br0 eth0
/sbin/dhclient br0
/usr/sbin/brctl addif br0 tap0
ifconfig tap0 192.168.1.150 up
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
route add -host 192.168.1.102 dev tap0
arp -Ds 192.168.1.102 eth0 pub

exit 0

```

some one know what I did wrong?

edit: Ow, yes I'm installing it not on the root user...

---

### Post by ashmew2 on 2009-04-18
> **dr_serious said:**
> Hi,
I have done step 2 completely and when I want to start my xp for the first time it gives an error:


Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either run 'chmod 0666 /dev/net/tun' or change the group of that node and make yourself a member of that group. Make sure that these changes are permanent, especially if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}


after I change the chmod, I try to start it again then I get this:

Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

I'm using the latest version of KUbuntu and the latest version of virtualbox

Like I said before every thing went perfect untill the 3th step the only thing I didn't could find was at step 1b "# Now, select Remote Display and check Enable VRDP Server." so I just skipped that...

This is my rc.local file:
```

tnctl -t tap0 -u fre
chmod 0666 /dev/net/tun
/user/sbin/brctl addbr br0
/sbin/ifconfig eth0 0.0.0.0 promisc
/user/sbin/brctl addif br0 eth0
/sbin/dhclient br0
/usr/sbin/brctl addif br0 tap0
ifconfig tap0 192.168.1.150 up
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
route add -host 192.168.1.102 dev tap0
arp -Ds 192.168.1.102 eth0 pub

exit 0

```

some one know what I did wrong?

edit: Ow, yes I'm installing it not on the root user...

you sorted it out ?

---

### Post by dr_serious on 2009-04-18
No could it be becous I'm not a root user?

---

### Post by dr_serious on 2009-04-18
I made me admin, still getting this error:
```

Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

```

some one know what I can do?

edit:Mybe this helps for an solution, it does start if I set attatched to NAT and not Host Interface

---

### Post by radi0j0hn on 2009-04-18
Ok, maybe I'm missing something, but I'm getting errors about something not being installed in the kernel.  Any ideas?

---

### Post by smo0th on 2009-07-03
I did step 2 and have internet access on ubuntu and xp, the problem is that my web server is being blocked somehow, any ideas?

The web server is working in the 192.168.x.x network and the service is unblocked in the router.

---

