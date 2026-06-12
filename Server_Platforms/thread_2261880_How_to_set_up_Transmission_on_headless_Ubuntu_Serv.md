---
title: "How to set up Transmission on headless Ubuntu Server 14?"
date: 2015-01-21
forum: Server Platforms
---

### Post by Mike_Burt on 2015-01-21
Hi Im trying to set up Transmission on my headless Ubuntu 14 server. I would like anything I download to go straight to an usb external drive  ( 1TB Western Digital Ultra) and reside there only. Right now I'm just confuse as how to set it up however I easily understand how to install Transmission but problem I don't understand how to set up the drive (Which format do I set it up as) it currently mounts a usb0 it is formatted as mac os x extended journaled. My raid device in the server is in ext4 format both drives. I have webmin installed which I use the administer the server with samba shares and etc. I need some input on this how to set up this task so that all torrents are saved to and only the external drive and after I detached the files can be read either on windows or mac. If someone can provide with steps on completing this it would be much appreciated. Thanks

---

### Post by lukeiamyourfather on 2015-01-22
I personally wouldn't bother moving the drive around physically to transfer the downloaded files. Just setup a Samba share so the downloads can be accessed from other machines. Transmission has a configuration parameter called "download-dir" which can be used to specify where to keep downloads. If there's no specific reason to keep HFS+ then I would format the drive as something else native to Linux like ext4.

---

### Post by papibe on 2015-01-22
Hi Mike_Burt.

A few thoughts:

I have a couple of USB external disks connected to my home server, without even considering 'torrenting' it has several drawbacks (read [here]("http://ubuntuforums.org/showthread.php?t=2220670&p=13006770#post13006770")).

HFS is horrible. I wouldn't trust it with my data. Reformat the disk to a Linux native filesystem, or in the worst case to NTFS, if you need portability.

Even with those consideration, I wouldn't download directly to the external drive. Torrenting need to write a lot of small changes to the disk. You would be better off downloading into an internal disk, and then move the completed files to the external drive. Transmission can be set to work this way.

Having said all that, here's how to set the download directory directly to the external drive:

[INDENT]Stop the transmission service:```
sudo service transmission-daemon stop
```
Create the new download directory on the external drive:```
cd /path/to/usb_drive

mkdir my_downloads
```
Assign the proper permissions to the directory:```
sudo chown debian-transmission:debian-transmission /path/to/usb_drive/my_downloads

sudo chmod 4775
```
Edit the config file:```
sudo vi /etc/transmission-daemon/settings.json
```
Look for a line that looks like this:```
"download-dir": "/var/lib/transmission-daemon/downloads", 
```
and change it to:```
"download-dir": "/path/to/usb_drive/my_downloads", 
```
Restart the service:```
sudo service transmission-daemon start
```[/INDENT]
To keep downloading to an internal drive, but once the files are completed, move them to the external drive:

[INDENT]Stop the transmission service:```
sudo service transmission-daemon stop
```
You may want to avoid downloading to the root partition, and change it to a partition with more space:```
mkdir /new_path/to/my_downloads
```
Assign the proper permissions to the directory:```
sudo chown debian-transmission:debian-transmission /new_path/to/my_downloads

sudo chmod 4775
```
Edit the config file:```
sudo vi /etc/transmission-daemon/settings.json
```
Look for 3 lines that looks like this:```
"download-dir": "/var/lib/transmission-daemon/downloads",
"incomplete-dir": "/var/lib/transmission-daemon/incomplete",
"incomplete-dir-enabled": false,
```
and change them to:```
"download-dir": "/path/to/usb_drive/my_downloads",
"incomplete-dir": "/new_path/to/my_downloads",
"incomplete-dir-enabled": true,
```
Restart the service:```
sudo service transmission-daemon start
```
[/INDENT]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by mastablasta on 2015-01-23
i would just like to add that transmission CLI has a nice webgui available. here is an article about it: [http://abyrne.me/setting-up-a-transmission-web-interface-on-a-headless-ubuntu-server/](http://abyrne.me/setting-up-a-transmission-web-interface-on-a-headless-ubuntu-server/)

sorry, but i have access denied at work to their website.

---

### Post by Mike_Burt on 2015-01-24
Thank you everyone for your advice, I got it to work now, I also decided not to use an external drive for the reasons papibe explained in his reply. I simply created a directory - /Downloads and when files are finished I'll just move them as I created a samba share with Webmin and to mastablasta your right it is a pretty decent web gui as I can access from other devices on the network. Again Thank you all for explaining I appreciate it.

---

