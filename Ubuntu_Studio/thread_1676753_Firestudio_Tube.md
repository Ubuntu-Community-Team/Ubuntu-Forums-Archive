---
title: "Firestudio Tube"
date: 2011-01-27
forum: Ubuntu Studio
---

### Post by andersonics on 2011-01-27
I've had a firestudio project working on this same system about a year ago, with a back level version of svn on a 10.04 install. I immediately made an live DVD iso of that install using Remastersys. I've tried to install it onto another partition on the same drive but it just started the live session.

Recently I did a fresh install of Ubuntu Studio 10.04, and did all of the prep that I did before in hopes of being able to use a Presonus Firestudio Tube that I just took delivery of, but to no avail.

I know that someone got it going, but on an earlier version (1807) of  libffado from a posting on the ffado device site.

I could go on using this thing on Windows, but I got spoiled over the last year on US, Ardour and my firepod which just decided give up the ghost. I decided upgrade to the FS Tube.

Any help would be greatly appreciated.

andersonics.

---

### Post by ailo.at on 2011-01-28
I didn't know even Firestudio Project was supported. According to FFADO's device support at [http://www.ffado.org/?q=devicesupport/list](http://www.ffado.org/?q=devicesupport/list) it is not supported along with the FireStudio Tube. I would let the people at FFADO know about your Firestudio Project device and let them know what works. Maybe they could update their info.

And you could try asking at their mail list about both of your devices. You'll find them here:
[http://www.ffado.org/?q=contact](http://www.ffado.org/?q=contact)

---

### Post by andersonics on 2011-01-28
I already tried there but so far no response.

I have tried to duplicate what I did in the first place, but with the specific back level trunks as near as I can tell, I can't seem to get there! I had mine running with:

libffado 2.999.0-1859 built Jun 25 2010

Does this jack svn from that time work with my libffado version?

Jack trunk-r4031 

I get an error when trying to compile it.

Anyway, here is what you'll find, along with my pleadings, if you search the board for those two devices. (BCingMars listed the driver=20, however I had mine running as driver=0 as the FS project and Tube have the same Dice chip in them).



Tested the Presonus FirestudioProject with FFADO 2.999.0-1807 bu
Submitted by cinqmarsb on Wed, 03/31/2010 - 04:19.

I have tested the Presonus FirestudioProject with FFADO 2.999.0-1807 built Mar 30 2010
- Result: It is working (the mixer is not working)
- I can record, listen...and the connexion is stable...with not too much XRuns.
the mixer is missing but i will wait for !

All is working fine on Windoze but, i prefer the sound with Ardour.(The only thing, Ardour is a bit fragile)

Tested with Ubuntu 10.04 Beta1, 2.8ghz quad core, Gygabyte GA-G41M-ES2H

BCinqMars


Tested the Presonus Firestudio Tube and Firestudio Project
Submitted by cinqmarsb on Wed, 03/31/2010 - 13:34.

1- I have tested the Presonus Firesudio Tube with FFADO 2.999.0-1807 built Mar 30 2010
- Result: Not working, no connexion

2- I have tested the Presonus FirestudioProject with FFADO 2.999.0-1807 built Mar 30 2010
- Result: It is working (the mixer is not working)
- I can record, listen...and the connexion is stable...with not too much XRuns.
the mixer is missing but i will wait for !

All is working fine on Windoze but, i prefer the sound with Ardour.(The only thing, Ardour is a bit fragile)

Tested with Ubuntu 10.04 Beta1, 2.8ghz quad core, Gygabyte GA-G41M-ES2H

BCinqMars


RETested the Presonus Firestudio Tube
Submitted by cinqmarsb on Wed, 03/31/2010 - 13:58.

1- Add to configuration file the device ID
(For infos vendorID, ModelID, in the terminal ~$ ffado-test ListDevices)
{
vendorid = 0x00000A92;
modelid = 0x0000000C;
vendorname = "Presonus";
modelname = "Firestudio Tube";
driver = 20;
},

2 - Compile, Install
3 - Start Jackd
4 - Tested the Presonus Firestudio Tube with FFADO 2.999.0-1807 built Mar 30 2010
- Result: It is working (the mixer is not working)
- I can record, listen...and the connexion is stable...with not too much XRuns.
the mixer is missing but i will wait for !

Tested with Ubuntu 10.04 Beta1, 2.8ghz quad core, Gygabyte GA-G41M-ES2H

BCinqMars

---

### Post by andersonics on 2011-04-12
Update: Issue SOLVED 

I installed KXStudio 64bit on my Toshiba Satalite, used the guide from Bob Hamils website:

[http://www.bobhamil.com/PreSonus/NewKXStudio&Presonus-AllStepsRevB.txt](http://www.bobhamil.com/PreSonus/NewKXStudio&Presonus-AllStepsRevB.txt)

I just went up to the point where it says:

sudo add-apt-repository ppa:ubuntu-wine/ppa (I stoped at this point), and it worked!

I pasted this into the configuration file in the libfado folder:

{
vendorid = 0x00000A92;
modelid = 0x0000000c;
vendorname = "Presonus";
modelname = "Firestudio Tube";
driver = 20;
},

Then ran:

sudo scons DEBUG=no PREFIX=/usr ENABLE_BEBOB=no ENABLE_FIREWORKS=no ENABLE_OXFORD=no ENABLE_MOTU=no BUILD_TESTS=no

Then:

sudo scons install.

Rebooted, set up jack for Firewire, and got the solid blue light!

Thank you Bob and the guys at the FFADO project!

---

### Post by poodoopealeoaph on 2011-04-25
Hi, I know it has been a little while since this thread had been marked as solved and everything but I just had a quick question. Since I've had KXstudio installed, my fiancee has been having problems with watching videos because of the KDE aspect of things and I also can't get jack to start very easily.... Do you happen to know if the tutorial you followed would work in Ubuntu Studio? Also, you said this worked with a firestudio tube but what about a regular firestudio?

by the way, i realized about halfway through writing this that I should probably just give it a shot and see what happens lol... still going to post this though so I can keep track of the thread and let everyone know how it went.

---

### Post by andersonics on 2011-07-06
Sorry for the late reply. 

Here  are the steps I took in the preperation after I installed KXStudio 10.04.3.

Most of these lines are typed in terminal, wait for each previous command to end
before starting the next.

1. On first running of KX Studio you will get a setup screen add yourself to the disk, audio and video groups. You can also paste these into the terminal one at a time..

sudo adduser daw disk
sudo adduser daw audio
sudo adduser daw video

2. Then in your terminal type:

sudo apt-get install scons subversion-tools libconfig++8-dev libdbus-c++-dev libraw1394-dev pyqt4-dev-tools libxml++2.6-dev libiec61883-dev

3. Then:

sudo modprobe raw1394
sudo chmod a+rw /dev/raw1394

4. While in the home folder:paste the following commands.

sudo svn checkout [http://subversion.ffado.org/ffado/trunk](http://subversion.ffado.org/ffado/trunk) ffado

5 Change directories in the terminal	

cd ffado/libffado

6. Paste this into the terminal:

sudo kate confuguration

7. Edit this file if your interface is not already listed.  

For Presonus Firestudio, Firestudio Tube, and Firestudio Project, I add the following:

{
	vendorid = 0x000a92;
modelid = 0x00000008;
vendorname = "Presonus";
modelname = "Firestudio 26x26";
driver = 20;
},
{
	vendorid = 0x000a92;
modelid = 0x0000000c;
vendorname = "Presonus";
modelname = "Firestudio Tube";
driver = 20;
},
{
	vendorid = 0x000a92;
modelid = 0x0000000b;
vendorname = "Presonus";
modelname = "Firestudio Project";
driver = 20;
},
save the file and exit.

If you are adding a firewire device to the configuration file after ffado has been installed, enter this command in the terminal:

	sudo rm -Rf .sconsign.dblite cache

8. These are the options I use for the Presonus:

sudo scons DEBUG=no PREFIX=/usr ENABLE_BEBOB=no ENABLE_FIREWORKS=no ENABLE_OXFORD=no ENABLE_MOTU=no BUILD_TESTS=no

9. Then

sudo scons install  

cd ..

cd ..
10. Edit the 50-udev-firewire.rules file

sudo kate /etc/udev/rules.d/50-udev-firewire.rules

Add to this file:

KERNEL="raw1394", GROUP="audio"

Configure jack, restart and have fun!


As for watching videos on KXStudio, All I have to do is pick the file I want to watch and the OS will open the default program for you. If you are trying to watch DVDs, VLC seems to be your best bet.

Also attached is the PDF file that I used to set up firewire devices in UbuntuStudio.

---

### Post by andersonics on 2011-07-06
Sorry, the pdf didn't attach. I'll get it up for you in a bit.

Dave.

---

### Post by andersonics on 2011-07-06
Under #3 in my tutorial, you can edit you /etc/rc.local file and add those 2 commands to the file. The commands will execute while booting so you don&#8217;t have to type it into your terminal after each boot!

Dave.

---

### Post by andersonics on 2011-07-06
Access to the firewire device on Ubuntustudio 10.04 after you have installed ffado using #2, 4 and 5 in the KXStudio tutorial above:

To capture from the firewire port, rw access to the /dev/raw1394 device node is required. Unfortunately the default Ubuntu edgy settings only allow rw access to root (the device owner) and disk (the device group). This basically means that the ordinary user can't grab video from the device.

1. Open the rc.local by typing this in the terminal:

sudo gedit /etc/rc.local

Add these lines at the end of the file.

sudo adduser <user name> disk
sudo chgrp video /dev/raw1394

Any of these 3 methods will provide access to the firewire device. Methods 1 & 3 won't survive a reboot; the commands could be added to /etc/rc.local so they'd be executed automatically at each reboot.

2. Next open the 40permissions.rules file by typing this in the terminal:

sudo gedit /etc/udev/rules.d/40permissions.rules

Copy these lines and paste them into 40permissions.rules:

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",       GROUP="audio"         
KERNEL=="dv1394*",       GROUP="audio"         
KERNEL=="video1394*",    GROUP=="audio"

3. Next, open your limits config file by typing this in the terminal:

sudo gedit /etc/security/limits.conf 

Copy these lines and paste them into limits.conf

*      rtprio      -      99
*      nice        -      -10
*      memlock     -      unlimited

4. Open your sysctl.conf file by typing this in the terminal:

sudo gedit /etc/sysctl.conf

Copy these lines and paste them into sysctl.conf

net.core.rmem_max=17000000
net.core.wmem_max=17000000

5. open your 50-udev-default.rules

sudo gedit /lib/udev/rules.d/50-udev-default.rules
make sure you're in the video group and add this line:

KERNEL=="raw1394", GROUP="video"

Next, go to your start button, System, Administration, Users and Groups. When the dialog box appears, pick the &#8220;Manage Groups&#8221; button, and another dialog box will appear. Go to &#8220;audio&#8221;, &#8220;video&#8221; and &#8220;disk&#8221; and make sure you login name is checked. If not, do so. Now pick the &#8220;Advanced Settings&#8221; button, and another dialog box will appear. Pick the &#8220;User
Privileges&#8221; tab. Make sure &#8220;Use audio devices&#8221; is checked, and pick &#8220;OK&#8221;, than close.

set up jack correctly. and restart your machine.

Hope this helps.

Dave.

---

### Post by andersonics on 2012-08-14
Since I can't edit the above post, I need to correct something important. My apologies for this blunder!

I realized that this process stated above won't work if you use “daw” under item 1 in the phrases (commands)

sudo adduser daw disk
sudo adduser daw audio
sudo adduser daw video

Please replace the word daw with your own user name.

Also I need to point out that if you use the following command under item 2

sudo apt-get install scons subversion-tools libconfig++8-dev libdbus-c++-dev libraw1394-dev pyqt4-dev-tools libxml++2.6-dev libiec61883-dev

and hit your enter key you will first get a series of check mentioning a program in each line in your terminal printout, followed by either a yes or a no at the end of each line. All of these need to say yes. If they say no, it is a good bet that you need to install the lib[program name]-dev for the program listed, and you might need to guess on some installs to see if it works. 

Before you try item 2 again you need to run this in the command prompt first while you are in the ffado/libffado folder:

sudo rm -Rf .sconsign.dblite cache

Nothing will appear to have happened, but it prepped the folder for another try for running item 2. I am running ffado successfully with a no after the “alsa-0 or higher” line, and it might work for you as well.

One more thing. Under item 3, open etc/rc.local for editing by using this command in the terminal:

sudo kate etc/rc.local

Go to the bottom of the file and add

sudo modprobe raw1394
sudo chmod a+rw /dev/raw1394

before the very last line. This allows these two commands to engage each time you boot your machine.

I hope this added information helps.

andersonics

---

