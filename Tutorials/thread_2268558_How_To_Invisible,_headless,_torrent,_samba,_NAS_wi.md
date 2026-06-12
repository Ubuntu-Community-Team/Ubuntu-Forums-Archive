---
title: "How To: Invisible, headless, torrent, samba, NAS with remote access Physical and VM"
date: 2015-03-09
forum: Tutorials
---

### Post by cackles on 2015-03-09
Azureus - Plex - Samba - Apache

This might be a little rough around the edges, any faults or comments, let me know. I accidentally deleted a section near the end and ctrl+z just didn't cut it when it came to restoring.

Known Bugs (out of my control):
Apache doesnt work with localhost until after Samba is installed.
Samba doesnt work and breaks your system if you install it at the very start.
Users have to get manually added to the sambashare file because it doesnt syncronise.

This tutorial covers installing Ubuntu Server 14.04 LTS on both a physical machine and VMWare. 'VMWare only' simply means it is additional information for VMWare Workstation 11 users.Normal Ubuntu users can ignore it. There's also a massive 3 lines of 'Ubuntu Only'.

This is my first tutorial in seven years and it is an update to [http://ubuntuforums.org/showthread.php?t=799712](http://ubuntuforums.org/showthread.php?t=799712) I've been a bit ill (still am) and had hoped to keep that one updated but I've been far too sick to be even close to devoted. (Would like to thank the NHS for 3 misdiagnosis over a 22 year period that cost me my job, my career, my doctorate as well as my sanity)

This is an overhaul with several new features. The features are:

Invisible, it runs on the TOR network.
Tell the server to download torrents with any browser capable device -another PC, netbook, notebook, phone, tablet or phablet.
Ability to view and download your files from any browser capable device.
Use Samba to network drives.
Media streaming.

This was running on a P4 2.4GHz, 2 x 1GB DDR 400 RAM, a 16 year old 320GB master hard drive with a 1.3GB IDE slave. It would still be running on that but I don't want to lose my data to a catostrphic failure that is well overdue and with the new setup I will also be putting in IPCOP (not covered here) and it only makes sense to do it like this.

Host is Windows 8, 32GB RAM, 3.06GHz i7. Drives are Green WD 2TB master -partitioned into C @ 500GB & D with the rest of the space, 3TB WD Red slave -single partition.
Virtual machine is Ubuntu 2GB RAM, 20GB primary, 512GB secondary, 2.75TB secondary.

I will assume everyone has a Windoze machine.

First; the importance of disk partitioning. How many disks and how you are operating them is important.

I have C,D,E hard drives and F is the DVD. Windows runs on C, On my D drive Ubuntu Server Has a primary 20GB where the OS lives and secondary 512GB where the downloads go with 2.75TB on E where anything I want to keep goes. This is so if 

my Windows goes down and I need to format I keep my Virtual disks and data intact.

In my old Ubuntu setup the first hard drive was partitioned 20GB for OS and a secondary for downloads, the second HDD was where I kept my storage. This was in case Ubuntu needed a reinstall.

Both setups mean the long term storage can be RAID/mirrored and the disk shouldnt be taxed as much so should last longer.

Both setups use both the Ubuntu server install and the desktop to set up. This is to make life easier for everyone. VMWare users make a folder named Ubuntu in D and download both the server and desktop iso's to the folder. Physical machine users burn both of them.

VMWare only:

I cannot stress enough that you should take a snapshot whenever possible. You will need to shutdown the machine as it is using independant disks to help protect your data.

If you only have one hard drive, you want to at least partition it into two. Acronis Diskmanager and the likes will be your best bet. Read the instructions carefully. I know we can make a lot of virtual disks, but if you need to format windoze then you are looking at losing the VM's as well.

For the purposes of this set up I have C,D,E hard drives and F is the DVD.

To set up Ubuntu in VMware Workstation 11; File -> New Virtual Machine -> Custom -> Workstation 11 -> Installer disc image -> select the server install disc -> enter the name and password you want to use to log into the server with -> Pick a machine name and browse location to D Ubuntu, make new folder under that named Ubuntu, select it, ok it and in Location it should now say D\Ubuntu\Ubuntu hit next -> processors 2, cores 2 total = 4 -> Memory 2GB -> Use bridged networking -> LSI Logic -> SCSI -> Create a new virtual disk -> Max size 20GB, tick allocate space now select store as a single file -> next at specify file -> UNTICK POWER ON THIS MACHINE AFTER CREATION!!! Hit finish.

Hit Edit Virtual Machine Settings. Add -> Hardrive SCSI + Tick independant + Persistent Create new disk (or you can use existing if you have already set up a VM storage) Size up to you but I use 512GB tick allocate now select store as single file. File name browse to D\Ubuntu create new folder called UbuntuShared and select it. File name: shared.vmdk

Repeat the last step again if you have another drive, this time make it nearly all the space, I left 250GB free so if I need to I can fire things over there.

Go to your first CD ROM drive and change the iso file to the Ubuntu Desktop disk and OK it.

Power on the machine.

Ubuntu Only:

Insert the desktop disk and err that's about it ...

All Users:

Select 'Try Ubuntu'
When booted select the top left icon 'Search ...' type in gparted and hit return. Top right are all your hard drives.

VMWare Only:

If you have already had a set up installed and had Ubuntu installed with virtual disks skip this section. If you follow this part you will drstroy your data.
If this is the first time you are setting up the drive Skip the 20GB partition and with the rest of them ...
Device -> Creat Partition Table then Partition -> New then Partition -> Format ext4.Hit the green tick.
Top right and shutdown. You dont have to remove the media.

Click to edit the machine and change the desktop iso to the server iso.
Hit options at the top of the page.
Click advanced.
Highlight and copy where it says 'Configuration'.
Open notepad.
File -> open -> paste in location -> open and under .encoding insert this line:
bios.bootDelay = "5000"
This will give you time to hit escape key during boot if you ever need to.
Power on machine.

Ububtu Users:

This will destroy all data, use with caution if you already had an existing setup.
Even if using only one disk I recommend having a 20GB system disk and then the other partition(s).
Once your done setting up your partitions, shutdown and boot with the server disk in.

Everybody:

This should be everyone doing the same thing from now on.

Start the install for Ubuntu Server -I will only comment on parts of this that I feel I need to.

Hostname - this is what your machine will be called on the network.
Full name - I just put in my user name for this.
Password - Yea, you need to remember this.

Guided - use entire partition - DO NOT USE LVM

Select your 20GB (21.5GB) hharddrive. Should be sda.

ONLY INSTALL:

OpenSSH server
LAMP server

It is important that is all you install. This to avoid b0rkage.

Yes installl GRUB.

While thats happenning, in your Windoze machine;

Go download and install [X-Ming]("http://sourceforge.net/projects/xming/")
Go download [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") for windows while waiting and after reboot login using the Username and password from setup like this;

Start PuTTY and in the Hostname/IP box type the name you gave your box earlier, dont hit return yet though.
Click SSH > X11 > Tick Enable X11 forwarding and in X display location put 127.0.0.1 

Go back to the sessions page and under Saved Sessions put in your box name and then hit SAVE. We will be using the hostname later, but not just yet. We initially have to connect via IP.

When using putty you can copy from text in Windows and just a right click in PuTTY will paste it. If you highlight in PuTTY it automatically copies.

Any code for commands you should enter one line at a time -this is purely for bug hunting. If its a config file you can copy and paste it all in.

VMWare users dont need to remove media, everyone else take your disks out.
Reboot the machine.

A very important note is that for the server to work you cannot use a static IP. Everytime I have changed to a static IP my uPnP goes down and the repositories on top of that. Major bummer.

Log into Ubuntu.
Check your current IP and settings.

```
sudo ifconfig
```

In PuTTY put the IP into the Host Name or IP box, hit open -you can if you want just save it under another profile.
You should now be able to log in.
Open a web browser window in windoze, enter the IP address of the machine and up should come a test page.

Time to install stuff, some of these you wont need but I thought they might be usefull for someone working on a current setup.

```
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install mysql-server
sudo apt-get install mysql-client
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install default-jre
sudo apt-get install default-jdk
sudo /etc/init.d/apache2 restart
```

If you get an apache2 error then:

```
sudo nano /etc/apache2/apache2.conf
```

Add the line:
```
ServerName localhost 
```
ctr + x to exit, save changes yes.
```
sudo /etc/init.d/apache2 restart
sudo apt-get install azureus
sudo apt-get install samba
```
Time to install Plex. Use a browser and go to [https://plex.tv/downloads](https://plex.tv/downloads) find your download. In my case it is Ubuntu 64-BIT.
Right click and copy the shortcut/link. Paste it in notepad (or something). [https://downloads.plex.tv/plex-media-server/0.9.11.7.803-87d0708/plexmediaserver_0.9.11.7.803-87d0708_amd64.deb](https://downloads.plex.tv/plex-media-server/0.9.11.7.803-87d0708/plexmediaserver_0.9.11.7.803-87d0708_amd64.deb)

In PuTTY:

```
sudo mkdir /downloads
sudo mkdir /downloads/plex
sudo mkdir /shared
sudo mkdir /storage
sudo chmod 0777 /shared
sudo chmod 0777 /storage
sudo chown root:sambausers /shared
sudo chown root:sambausers /storage
cd /downloads/plex
sudo wget /downloads/plex/plexmediaserver_0.9.11.7.803-87d0708_amd64.deb https://downloads.plex.tv/plex-media-server/0.9.11.7.803-87d0708/plexmediaserver_0.9.11.7.803-87d0708_amd64.deb
sudo dpkg -i /downloads/plex/plexmediaserver_0.9.11.7.803-87d0708_amd64.deb
sudo reboot
```
Do not confuse that downloads with where we will be downloading torrents to. That above downloads folder is there purely for things we wget.

Check Plex is working:

```
http://yourboxname:32400/web
```

All going good so far?

Satrt PuTTy back up and this time load your last config, change from IP to the hostname and save as another session.

Samba time ...

```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
sudo nano /etc/samba/smb.conf
```

Paste this in:

```
[global]
; General server settings
netbios name = hostname
server string = ishare
workgroup = WORKGROUP
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=131072  so_sndbuf=131072
invalid users =
valid users =


passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

syslog = 1
syslog only = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes

[Shared]
path = /shared
browseable = yes
read only = no
guest ok = no
;create mask = 0644
directory mask = 0777
valid users = Test
; force user = yourlogin
; force group = yourlogin

[Storage]
path = /shared
browseable = yes
read only = no
guest ok = no
create mask = 0777
;directory mask = 0755
valid users = Test
; force user = yourlogin
; force group = yourlogin
```

Parts to change

```
[global]
; General server settings
netbios name = hostname <- yourboxes name
server string = ishare <- A description for your box
workgroup = WORKGROUP <- The workgroup your computers are on, to get this check the settings in windoze.

[Share Name] <------------------------- This is what it will be called on the network 
path = /shared <- The shared folder you made
browseable = yes
read only = no
guest ok = no
create mask = 0777
;directory mask = 0755
invalid users = <----- Use this to keep users out if you add anyone to global they will have that right/ban in all directories.
valid users = Test <-------------We will be creating a test user for this. May as well keep it as Test to see if it works first.
; force user = yourlogin <- I have these commented out, if at the end yours doesnt work 
; force group = yourlogin <- delete both the ; and put your PuTTY/root login name there
```

Press ```
control + x
``` to save then yes etc. to exit.

Restart Samba:

```
sudo restart smbd
```

What is important to remember is that Samba is just a way to access your data. It's like a gateway, therefore treat it as such. The data is really controlled by Ubuntu, users, groups etc. So you can give Samaba all the powers in your 

operating system, but if the user doesnt have the permissions they won't be able to see, create etc. That is why we chown'd earlier.

We are going to make Samba users so that we aren't storing root passwords on portable, easily lost devices. Just substitute newuser with the name you want, I suggest running Test first.

```
sudo useradd -s /bin/true newuser
sudo smbpasswd -a newuser
sudo usermod -G sambashare -a newuser

```

Let's see if we can see the Samba drives.

In windoze ...

Go into Explorer -> Map Network Drive -> Folder
```

\\yourboxname\Shared 
```

Tick reconnect at logon and connect using different credentials. The username should be:

```
yourhostname\Test
```

In this case Test should be your newly created ID.

Time to mount your drives ...

```
sudo fdisk -l
```


This will show the drive names and sizes. Mine are:

```
/dev/sda1
/dev/sdb1
/dev/sdc1
```

Pretty simple, right? This bit is easy.

```
sudo nano /etc/fstab
```

Add your new drives (you wont need to mount the 20GB one because thats what you are running off and it is already mounted) by simply adding a line for each like this:

```
/dev/sdb1    /shared   ext4    defaults     0        2
/dev/sdc1    /storage  ext4    defaults     0        2
```

Test they are working.

```
sudo mount -a
```

Next we make folders for the torrents to go to.

```
sudo mkdir /shared/NewDownloads
sudo mkdir /shared/Torrents

sudo chmod -R 0777 /shared
sudo chmod -R 0777 /storage
```
You dont really need to chmod those directories again, but better safe than sorry.

Now we need to make a script for Azureus/Vuze to run.

In PuTTY:

```
sudo nano /usr/share/java/azureus_daemon
```

Now in there paste:

```
#! /bin/sh

#The user that will run Azureus
AZ_USER=your_login_name

#Name of the screen-session
NAME=cackles_azureus_daemon

#executable files in the following paths that are perhaps needed by the script
PATH=/bin:/usr/bin:/sbin:/usr/sbin:/usr/share/java

#your path to the azureus directory, where Azureus2.jar is located
DIR=/usr/share/java/

#Description
DESC="Azureus Daemon"


set -e


case "$1" in
start)
echo "Starting $DESC: $NAME"
su $AZ_USER -c "cd $DIR; screen -dmS $NAME java -jar ./Azureus2.jar --ui=console"
su $AZ_USER -c "screen -S $NAME -X start all"
echo "Azureus Daemon Started"
;;
stop)
su $AZ_USER -c "screen -S $NAME -X quit"
echo " Daemon Has Been Stopped"
;;
check)
su $AZ_USER -c "screen -S $NAME -X show torrents all"
;;
daemons)
su $AZ_USER -c "screen -list"
;;
esac

exit 0

```


Then change anybody to your root logon name, no need for pass or anything.

Control + X to get out and save that and then:

```
sudo chmod a+x /usr/share/java/azureus_daemon
```

I was glad to see the Azureus/Vuze wiki had been updated ... but after seven years it still doesnt work.So Im quite happy that after seven years mine still does :D

Now change directory ... 

```

cd /usr/share/java/ 
sudo ./azureus_daemon start
```

That should start the torrent server. Use your browser and goto [http://hostname:6886](http://hostname:6886) and make sure its working.

```
sudo ./azureus_daemon daemons 
```

will let you see your daemon running.

```
sudo ./azureus_daemon check
``` 

will let you see any torrents that are downloading.

```
sudo ./azureus_daemon stop
```

Stops the daemon ... There are no safeties built into this but if you play with and rack up too many daemons theres always reboot with no harm done :) This will allow you to stop Azureus/Vuze anytime you need to log into the GUI, like now, to add 

plugins.

To get plugins:

In PuTTy use the stop command and then simply type in azureus. DO NOT SUDO or SU IT!!! It will not work under root.
Launch X-Ming and in your browser go to [https://plugins.vuze.com/plugin_list.php](https://plugins.vuze.com/plugin_list.php) Select the plugins you want and download them to something like /shared/vuze
Launch azureus by simply typing azureus. Tools -> Plugins -> Installation Wizard -> by file.
When youre done adding all the cool stuff you want close Vuze.

I recommend Seed Stopper and you will need to install the Azureus HTML WebUI.

Now we need to get it to run at startup.

```
sudo nano /etc/rc.local
```
And make sure yours is like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo /usr/share/java/azureus_daemon start
beep -r 5

exit 0
```

You should have only needed to add one line for azureus, but we added two so that our headless machine beeps 5 times when its has started up and loaded everything. Remove the beep line if you dont want it. You can also add log on 

messages here with echo "message including the quotes". exit 0 should always be the last thing.

Reboot:

```
sudo reboot

```

Still here? It's time to engage the cloak.

Whether it's an oppressive government or some other reason, the TOR Network is there to help you hide.

You are going to need a TOR Browser for your operating system. Basically to download torrents you use the browser, right click the link, copy, paste in the Azureus Web GUI uploads and Azureus will go get your torrent file. 

To install TOR Network onto your box:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
sudo add-apt-repository "deb http://deb.torproject.org/torproject.org $(lsb_release -s -c) main"
sudo apt-get update
sudo apt-get -y install tor-geoipd polipo
sudo service polipo restart
```
Once installed reopen Azureus -> Tools -> Options -> Connection -> Proxy Options.

Tick Enable proxying ...
Tick I have a SOCKS proxy ->
Host 127.0.0.1
Port 9050

The last things to do with the box is to make a webpage and dynamic dns so you can access your files anywhere.

Go to dyndns.com and setup a free account. Make a URL. Activate it. Update the IP, click on the link for the URL and update using 'my IP'.

Install this Gizmo, selecting dyndns and 'from list along with your dyndns username and pass.

```
sudo apt-get install ddclient

```

Now go into your router settings. Forward ports 80, 32400, 6886.

Cool but you can't download, meh, thats easily solved. 

```
sudo mkdir /var/www/test
sudo nano /var/www/test/.htaccess


```
In nano paste this in:

```
AuthUserFile  /etc/apache2/.htpasswd
AuthGroupFile /dev/null
AuthName  YouKnowWhere
AuthType Basic
require user test
```
Control+x save and exit.
```

sudo htpasswd -c /var/www/test/.htpasswd test
sudo nano /etc/apache2/sites-available/default

```

Add this to the file after ServerAdmin webmaster@localhost:

```
       <Directory /var/www/test>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

```

Restart Apache:

```
sudo /etc/init.d/apache2 restart

```

Make a simple webpage:
```
sudo nano /var/www/index.html

```

Remember, this is to test only and show you. Make your page look like this:
```
Test 1
<p><A HREF="test/">Test</A>

```

Time to add shared to it:

```
sudo mount -o bind /shared /var/www/test
sudo nano /etc/fstab

```

Add this line to fstab to make it 'stick':

```
/shared /var/www/test auto bind 0 0


[CODE]sudo reboot
```

You now have a webpage to download files from.

And that should be that!

---

