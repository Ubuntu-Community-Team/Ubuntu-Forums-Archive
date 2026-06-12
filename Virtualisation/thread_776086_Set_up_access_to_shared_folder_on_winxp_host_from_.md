---
title: "Set up access to shared folder on winxp host from ubuntu8.04 guest"
date: 2008-04-30
forum: Virtualisation
---

### Post by marc.knuckle on 2008-04-30
i setup virtualbox with the recommendation of CustomPC.  the instructions were to setup ubuntu 7.10 guest on xp host.
the last step was to setup a shared folder to swap back files to the host os,win xp, if and when needed.  
it stated to go into places, connect to server and then set as windows samba share and type in the ip address of the host system.  this worked fine but now i have updated to ubuntu 8.10 and the folder link is gone. when i go into places and connect to server there isn't the same options and i cannot put the ip address in.  if i chose windows share for example it comes back with an error along the lines of path not recognised.

any ideas how to get the same folder shared as i did in 7.10?

---

### Post by fjgaude on 2008-04-30
You do what you wish through using Samba, through Shares.

What OS are you using? If it is other than Hardy it is fairly easy to setup Shares in both Ubuntu and in Windows so that each can "see" the other.

Okay I just re-read your title and see you are using 8.04. Click on the drive or folder you wish to be able to see in Windows. You will then get to download the samba stuff automatically, assuming you are connected to the Internet while in 8.04.

Near the end you will be told you don't have permission. But all you have to do is go into the /etc/Samba/smb.conf file and add at the very bottom this, but with your paths, not mine:

```
[frank]
path = /home/frank
available = yes
browsable = yes
public = yes
writable = yes
```

The [frank] should be changed to what you called your share; path to what it is to that share.

Let us know how you are doing.

---

### Post by marc.knuckle on 2008-04-30
unfortunately i am very new to linux so bare with me.
i think that samba is already installed. the main folder i wanted to share is currently on the host XP system and is configured correctly for sharing as i can share with my other windows system so i just need to configure it on the linux os. i think i need to strt from the very beginning in ubuntu.  
what did you mean with the clicking the drive/folder?

cheers for the help and hope we can get it sorted

---

### Post by fjgaude on 2008-04-30
Okay, go to your file manager called Nautilus. From there you see folers and files. Right click on the folder you wish to share. At the bottom of the options list you will find "Sharing Options", Click and follow instructions.

After you get the error that you don't have permissions, then is when you can go to gedit to enter at the bottom of the /etc/samba/smb.conf file what I suggested in my first post.

To do this you will have to have root permissions with gedit:

```
gksudo gedit /etc/samba/smb.conf
```

That will bring you to the top of the file; go to the bottom and put what I suggested at the very bottom. Do not make any other changes to the file.

Let us know your progress.

---

### Post by marc.knuckle on 2008-04-30
i did that and it said i didn't have permission but offered it to be automatically and i said yes.  i still did what you said swapped frank for marc-knuckle but did you also mean the first bit in brackets (frank) because i did that as well.  the folder now has the circle with the 2 opposite direction arrows. after restarting, the share symble has disappeared.  
just to confirm though that i wanted to access my existing workgroup on the host os wich is winxp.  last time in ubuntu 7.10 i went into connect to server and into samba share and typed the ip address of the xp system and that was it i had the netwoked folder icon on the desktop showing the winxp ip address as the folder name.  thats all i want but the connect to server doesn't seem to work now.

---

### Post by fjgaude on 2008-04-30
Okay, I think I understand what you are wanting to do. You need a password in Ubuntu samba so you can see things:

```
sudo smbpasswd -a yourname
```

After your password about three times, you likely can access Ubuntu from within WinXP.

While in WinXP find its IP with ipconfig command. Use that in Nautilus to access the windows shares. That should do it.

You can access the IP of Ubuntu using ifconfig. Then you should be able to see shares on either side. You get to Ubuntu using the Windows file manager, down at the bottom under Network, and maybe then to Entire Network.

Hope this all helps.

---

### Post by marc.knuckle on 2008-05-01
cheers mate.

i just re-installed 7.10 as it is as easy as going into connect to server and choosing windows share and typing ip address of xp and voila. really easy.
however i would like the advice on the opposite way around as i can't see any shared folder on the ubuntu virtual machine even when i go into windows network.  could you show me, from scratch, how to set a folder in the ubuntu virtual machine and get it so xp can see it.

---

### Post by fjgaude on 2008-05-01
I don't use 7.10 anymore but this is how I remember. Go into System/Administartion menu and click Shared Folders. Click Samba, not NFS. Add, the share that you wish, like /home/<login>... the needed programs should install automatically, assuming you are on the Internet.

Then at the Ubuntu command line:

```
sudo smbpasswd -a <login>
```

Use your login name and passwords here.

Then re-boot, and from Windows Explorer you should get to the share or shares through Network, or some name like that.

Lots of learning to accomplish all the things we wish to do through virtualization, eh? We learn daily.

---

### Post by marc.knuckle on 2008-05-01
i did as you said but still nothing comes up when i go into control panel, network and internet connections, network places and then view workgroup computers(?)
do i need to find the ubuntu ip address for any reason like i did the other way around when setting up the connection to the winxp shared folder in connect to server? on the folder on the ubuntu desktop that links to the winxp folder that i shared there is a little connected bar with the ip address of the xp machine under it but on the folder i setup on the desktop of ubuntu called ubuntufolder, there is nothing under it showing i have shared it(?)

---

### Post by fjgaude on 2008-05-01
When setting up the share, did you see a "read only" check box?

I trust you have rebooted everything since you made the last changes.

---

### Post by MaindotC on 2008-05-01
Just FYI you won't be able to connect to password protected shares until there's a bug fixed:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/207072)

Or you can figure out how to apply that patch that is linked at the bottom.

---

### Post by fjgaude on 2008-05-01
He is using 7.10 and that is how I tried to instruct.

Though it is still easy to have password protected shares in 8.04, but I'm not that good enough with words to put it all down.

I have two boxes using VMware and a laptop all connected with shares under 8.04. It was a hassle to get them all working together but it is done. SSH between everything,

---

### Post by MaindotC on 2008-05-01
It is not easy to have password protected shares in 8.04 for the reasons I stated above!  It is a bug that is currently being resolved!

---

### Post by marc.knuckle on 2008-05-02
doesn't that link refer to 8.04?  i am using 7.10.
no i took the tick out of the red only box.
just a side issue, how do i get to my posts rather than have to search for them from the beginning?

---

### Post by fjgaude on 2008-05-02
> **marc.knuckle said:**
> doesn't that link refer to 8.04?  i am using 7.10.
no i took the tick out of the red only box.
just a side issue, how do i get to my posts rather than have to search for them from the beginning?

Go into User CP at the top of the Forum posts and scan for what you wish.

---

### Post by marc.knuckle on 2008-05-02
the only thing about threads in there is subscribed ones and i am not subscribed to any.

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM) ,this video seems to be pushing me in the right direction but when i bring up the edit samba file , smb.conf, it is completely blank??????

---

### Post by marc.knuckle on 2008-05-03
the smb.conf file has for some reason come up now so i have carried on and set it correctly. 
as it still doesn't show in windows i guess that means one of two things.  either i simply can't share files in a virtual pc or VirtualBox itself needs to be configured for it somehow?????

please help

---

### Post by fhmanas on 2008-05-03
> **marc.knuckle said:**
> doesn't that link refer to 8.04?  i am using 7.10.
no i took the tick out of the red only box.
just a side issue, how do i get to my posts rather than have to search for them from the beginning?

Go to Search and at the bottom choose either Find all your Threads or  Find all your Posts.

if you can ping your host ip, you can open nautilus and type 'smb://xx.xx.xx.xx'.  If this does not work, make sure is samba is working properly.

---

### Post by marc.knuckle on 2008-05-03
cheers for the thread thing.

how do i ping the host from within the guest ubuntu?  and where is nautilus in ubuntu 7.10?

do i have to configure virtualbox for sharing?

---

### Post by marc.knuckle on 2008-05-03
i give up.  
all i have done is made the folder in xp(host) writable as well and this is sort of a joint folder accessible by both. this was setup by going into connect to server.
i know this is sort of what i was aiming for anyway but i thought it was poss to actually setup a folder on ubuntu (guest) that was accessible as well.
still, same result really, a folder that i can read and write to on both machines.

---

### Post by fhmanas on 2008-05-11
to ping just open a terminal windows Applications -> Accessories -> Terminal

Type ping xx.xx.xx.xx where xx.xx.xx.xx is the ip of your host. You can get the ip from WinXP by opening a MS-Dos Command Window and type ipconfig, 

Nautilus is basically the Explorer of Gnome, You can open one by opening your Home folder Places -> Home Folder, click the small 'notepad' button on the upper left hand, now you can type your destination.  Type smb://xx.xx.xx.xx

---

