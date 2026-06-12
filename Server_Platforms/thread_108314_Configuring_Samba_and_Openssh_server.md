---
title: "Configuring Samba and Openssh server"
date: 2005-12-25
forum: Server Platforms
---

### Post by Connollyir on 2005-12-25
On a fresh install of Ubuntu server, I installed openssh-server, Samba, and nfs-kernel-server so that I could create a media storage bin on a LAN. How should I configure them/what do I do next? I'm very new to using these programs (I've never tried anything like this before) and generally green with Ubuntu - although I am learning, hardcore. 

Mainly, I want to be able to place files onto the remote computer (in the /home directory) that can be shared over the LAN with maybe 2-3 users needing access to the files. I need to be able to download from the server and stream music (and video if possible) from it to my desktop. I thought about using proftp for uploading and downloading but when I went to apt-get it Ubuntu told me it couldn't be found. I also tried to install Gnup3d to stream music but once again it couldn't be found.

If you think I am going in the wrong direction please let me know what you think I should be doing.

Thanks

-Ian

---

### Post by harisund on 2005-12-26
I am not quite sure I am able to understand what you are trying to do here.. but let me say what I tried.. 

To get samba working, I did
```
apt-get install samba smbfs
```
Then I had to edit /etc/samba/smb.conf to set the workgroup name so that MS could see it. The .conf file has good comments to help you out.
Then to add the user I do
```
smbpasswd -a <name of the user>
```
Just in case, I do 
```

/etc/init.d/samba stop
/etc/init.d/samba start

```

Then I can browse to the folder of the user from my Windows XP box. I hope you know how to get it working in Windows XP. 

To stream I use gnump3d. Again, the configuration file to edit for this is /etc/gnump3d/gnump3d.conf. Here you can set the root folder and the username and all that. Again, you would need to do
```

/etc/init.d/gnump3d/stop
/etc/init.d/gnump3d/start

```

For your ftp, you would need
```
apt-get install proftpd
```
Here too, the configuration file is in /etc/proftpd/something.conf (I am not sure of the file name). Any changes you do you will need to restart the FTP server
```

/etc/init.d/proftpd stop
/etc/init.d/proftpd start

```

Oh and don't forget, all of the above commands need to be done as root. I create a root user, hence I don't type sudo everytime. 

Have you edited your */etc/apt/sources.list* file? If you do not know what I am talking about then what you should be knowing is that the file I just mentioned is where apt-get and synaptic look for software. By default it will search in the CD. Here is a quick way you would want to edit it. 

1. Open the /etc/apt/sources.list as root, and add a # to the very first line. This will comment it out (basically you are asking it to not look in the CD.)
2. Type this in the command line (you wouldn't need sudo if you were root already)
```

$ sudo sed -i 's/main restricted/main restricted universe multiverse/g' /etc/apt/sources.list
$ sudo apt-get update

```
This basically instructs apt-get to start searching for software from a huge repository online. 

Then you are good to go with all the apt-get commands mentioned earlier.

Oh and one more thing, do you want to access these from a Windows box? I do, and didn't install nfs-kernel-server. However, if you are looking at accessing them from another *nix box, I am not sure if the samba part of what I wrote is applicable to you.

---

### Post by Connollyir on 2005-12-26
[QUOTE=harisund]I am not quite sure I am able to understand what you are trying to do here.. but let me say what I tried.. 

To get samba working, I did
```
apt-get install samba smbfs
```
Then I had to edit /etc/samba/smb.conf to set the workgroup name so that MS could see it. The .conf file has good comments to help you out.
Then to add the user I do
```
smbpasswd -a <name of the user>
```
Just in case, I do 
```

/etc/init.d/samba stop
/etc/init.d/samba start

```

Then I can browse to the folder of the user from my Windows XP box. I hope you know how to get it working in Windows XP. 

To stream I use gnump3d. Again, the configuration file to edit for this is /etc/gnump3d/gnump3d.conf. Here you can set the root folder and the username and all that. Again, you would need to do
```

/etc/init.d/gnump3d/stop
/etc/init.d/gnump3d/start

```

For your ftp, you would need
```
apt-get install proftpd
```
Here too, the configuration file is in /etc/proftpd/something.conf (I am not sure of the file name). Any changes you do you will need to restart the FTP server
```

/etc/init.d/proftpd stop
/etc/init.d/proftpd start

```

Oh and don't forget, all of the above commands need to be done as root. I create a root user, hence I don't type sudo everytime. 

Have you edited your */etc/apt/sources.list* file? If you do not know what I am talking about then what you should be knowing is that the file I just mentioned is where apt-get and synaptic look for software. By default it will search in the CD. Here is a quick way you would want to edit it. 

1. Open the /etc/apt/sources.list as root, and add a # to the very first line. This will comment it out (basically you are asking it to not look in the CD.)
2. Type this in the command line (you wouldn't need sudo if you were root already)
```

$ sudo sed -i 's/main restricted/main restricted universe multiverse/g' /etc/apt/sources.list
$ sudo apt-get update

```
This basically instructs apt-get to start searching for software from a huge repository online. 

Then you are good to go with all the apt-get commands mentioned earlier.

Oh and one more thing, do you want to access these from a Windows box? I do, and didn't install nfs-kernel-server. However, if you are looking at accessing them from another *nix box, I am not sure if the samba part of what I wrote is applicable to you.[/QUOTE]


I am going to go out on a limb here and say I LOVE YOU for that cd ignorance trick you gave me. The server I am installing many packages into (and coincidentally the target of this thread) is down in the basement and I am in the attic working on it in my room through ssh. Needless to say it was a royal pain to have to go all the way down there just to put a cd in because I forgot about it maybe a million times. Plus it helps out my desktop application too. The commands you gave in the bottom of your post also solved my mysterious problem of not being able to find proftpd or gnump3d with apt-get even though I have all repositories enabled. Sweet.

Now in regards to configuring Samba, I should have been more specific when saying that I needed help configuring it. You confirmed every step I made in installing Samba (install Samba, install smbfs, setting the workgroup and user passwords, and restarting Samba). What I was more interested in I suppose was how I could browse/download/upload files from a Linux client, such as my desktop? I wanted to use Samba because I would like to share files with my colleagues at college who almost exclusively (not surprisingly) use Windows. Will they have to install Samba on their own computers as well? I remember reading that XP has some components of Samba already there so they would be able to browse without much difficulty.

I am going to check out what I can do with proftp and gnump3d and I'll definitely check back later.

Thanks a bunch.

-Ian

---

### Post by harisund on 2005-12-26
Glad to be of help.. 

First up, if I am not much mistaken, Samba is meant to provide a Linux workstation capability to network with a Windows machine. 

On my Windows Machine I did the following stuff --
In Control Panel, I went to the Network Setup Wizard and and just followed through the stuff. I use wireless on my laptop and when going through the wizard, I just chose the option that said the machine didn't connect to the network. Then I chose a computer name, computer description and the yadda yadda, and then when it came to the workgroup name, gave the same one as was configured in Ubuntu. Basically the setup removes the XP-inbuilt-firewall for file sharing. Once that was done, in Windows XP I go to "My Network Places and then on the side panel "View workstation computers" and Ubuntu shows up. Basically there is no need to setup anything.

However, when working on my Linux machine, if I want files from the Linux server I typicall use scp / sftp. However, you could still use Samba if it is installed in your Linux workstation as well. 

Hope it was of any help. I can help you to get the Windows machine to see the server on which samba is installed, but I am afraid I won't be of able to help for your Linux workstation.

Cheers ! 
Hari

---

### Post by Connollyir on 2005-12-26
[QUOTE=harisund]Glad to be of help.. 

First up, if I am not much mistaken, Samba is meant to provide a Linux workstation capability to network with a Windows machine. 

On my Windows Machine I did the following stuff --
In Control Panel, I went to the Network Setup Wizard and and just followed through the stuff. I use wireless on my laptop and when going through the wizard, I just chose the option that said the machine didn't connect to the network. Then I chose a computer name, computer description and the yadda yadda, and then when it came to the workgroup name, gave the same one as was configured in Ubuntu. Basically the setup removes the XP-inbuilt-firewall for file sharing. Once that was done, in Windows XP I go to "My Network Places and then on the side panel "View workstation computers" and Ubuntu shows up. Basically there is no need to setup anything.

However, when working on my Linux machine, if I want files from the Linux server I typicall use scp / sftp. However, you could still use Samba if it is installed in your Linux workstation as well. 

Hope it was of any help. I can help you to get the Windows machine to see the server on which samba is installed, but I am afraid I won't be of able to help for your Linux workstation.

Cheers ! 
Hari[/QUOTE]

I was pretty sure you could use samba with linux if you enabled the right filesystem with Samba. What program do you use for scp and sftp? How do you like the way they run? I think I am going to end up using ftp to transfer the files to and from the server and then use gnump3d to stream music and just download the movies I want when I want to watch them; for my friends I'm sure I can create guest accounts with read only privileges to access the server if I decide to put it on our network at school.

Thanks

-Ian

---

### Post by harisund on 2005-12-26
Let's see.. scp and ssh are command line programs, however I think in Gnome desktop you can create a new file share or new mount point or something. Somewhere you will have a drop down dialog box where you can decide whether your new mount point is going to be a local one or a ssh or a ftp. Here you can choose the ssh one. In case I am not clear enough, apologies, and I will post back as soon as I can get access to a Gnome desktop at my work place.

With regards to working in the network at school, you have the choice of either just creating a workgroup or you can actually put the machine on the domain itself. That is what I am trying to do with some email stations at my university. 

Also, you can allow read only privileges using umask, but basically they will be chrooted into the home folder only when you are using samba.

---

