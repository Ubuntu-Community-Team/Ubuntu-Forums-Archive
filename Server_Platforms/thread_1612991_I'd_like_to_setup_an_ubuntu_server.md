---
title: "I'd like to setup an ubuntu server"
date: 2010-11-03
forum: Server Platforms
---

### Post by Cfhs_1 on 2010-11-03
As the title says, I'd like to setup an ubuntu based server. I don't want it to do a whole lot, but I have never tried setting up an ubuntu server before, so I have no clue where to start. I have a 32-bit server with two HDDs. One is a 20GB HDD; I would like the actual ubuntu server install to be here. The other drive is a 500GB drive that I would like shared over the network for music, movie, document storage/sharing. I would like to require users to enter a login to access the drive, so that's it's secure. I would also like to be able to connect to the server via both VNC and SSH. Finally I would like to be able to access the server from outside my network. Is any/all of this possible? Is it easy to configure? Can you please help me get this up and running?

Thanks in advance,
Nicholas C. Brown

---

### Post by s3MA00RRNY on 2010-11-03
You could create a partition for your home folder on the 500GB drive and then set up separate users. With WinSCP you can do file transfer over SSH. Users would only have access to files they have permissions on. I'm not sure about VNC, but it should be possible (somehow)

---

### Post by s3MA00RRNY on 2010-11-03
Accessing the server from the outside requires NAT forwarding over port 22 for SSH. Do NOT open VNC to the outside! It's best to use SSH to tunnel into the machine and then set up a local port tunnel (Putty can easily do this). VNC is too insecure otherwise.

---

### Post by drdos2006 on 2010-11-04
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by HermanAB on 2010-11-04
Linux is Linux is Linux...

Usually a 'server' is an ugly, terrifying, headless thing, hiding out in a dark corner of a dank data warehouse.  However, you mention VNC (a serious security risk and resource hog), which implies that your 'server' will have a screen and keyboard attached.

So, just install ordinary Ubuntu on it and have fun.

---

### Post by arnavk007 on 2010-11-04
i second herman
configuring ubuntu server is a pita if you want to use the machine as a second mechine
try *buntu desktop
do the configuring and put default runlevel to 3 i think

---

### Post by Cfhs_1 on 2010-11-04
Thanks Guys. So, when I go to install, I could create the /Home folder in a partition on the 500 GB drive, and create user accounts there? As for changing the default run level, How do I accomplish that? I've never changed the default run level in linux before. I've only ever worked in the gui, and a terminal windows on top the gui.As for the server, yes, it will be "Headless" most of the time... The only time I'm actually gonna have a monitor hooked up to it is during the initial installation/set up. after that, It's going to be moved into a small room with just power and Ethernet connected to it.

---

### Post by arnavk007 on 2010-11-04
seeing what you want
check this  [http://techgurulive.com/2008/09/18/how-to-change-linux-runlevels/](http://techgurulive.com/2008/09/18/how-to-change-linux-runlevels/)
to edit /etc/inittab   type this in the terminal   sudo gedit /etc/inittab
have good luck
first configure using gui and then you can change the runlevel

---

### Post by CharlesA on 2010-11-04
> **arnavk007 said:**
> i second herman
configuring ubuntu server is a pita if you want to use the machine as a second mechine
try *buntu desktop
do the configuring and put default runlevel to 3 i think

Why would you want to screw with runlevels?

If you don't want the GUI to load, then just stop gdm from loading (or remove it all together)

> **Cfhs_1 said:**
> Thanks Guys. So, when I go to install, I could create the /Home folder in a partition on the 500 GB drive, and create user accounts there? As for changing the default run level, How do I accomplish that? I've never changed the default run level in linux before. I've only ever worked in the gui, and a terminal windows on top the gui.As for the server, yes, it will be "Headless" most of the time... The only time I'm actually gonna have a monitor hooked up to it is during the initial installation/set up. after that, It's going to be moved into a small room with just power and Ethernet connected to it.

It's a bit pointless to run a GUI on it since you can always forward X over SSH and/or install a web interface. That way you don't need to screw with making it so that the GUI doesn't load automatically.

Read a bit about the advantages vs disadvantages here: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by Cfhs_1 on 2010-11-04
Yea, I would rather start with a fresh install with no GUI. I want my server to be as lightweight as possible, plus configuring a server from the CLI would be a learning experience. The guide that Kevin Elwood made ([http://woodel.com/](http://woodel.com/)) is probably what I'm going to follow at this point. It seems to be a very complete guide, with in depth explanations of how to set things up.

---

### Post by CharlesA on 2010-11-04
> **Cfhs_1 said:**
> Yea, I would rather start with a fresh install with no GUI. I want my server to be as lightweight as possible, plus configuring a server from the CLI would be a learning experience. The guide that Kevin Elwood made ([http://woodel.com/](http://woodel.com/)) is probably what I'm going to follow at this point. It seems to be a very complete guide, with in depth explanations of how to set things up.

I can only speak from my experience messing around with Ubuntu server:

Started with 9.04 with a GUI installed, then moved onto using Webmin with the GUI.

Went to 9.10 and only used webmin, no GUI

Now I'm using 10.04 with only SSH installed and I do config and management that way.

Once you get used to the CLI, there's nothing that you cannot do. :)

EDIT: That guide is pretty comprehensive, altho there are some things that are different between Debian and Ubuntu, but nothing that'll cause serious problems. :)

---

### Post by arnavk007 on 2010-11-04
i agree with charles even though i myself am doing so using gui

---

### Post by Cfhs_1 on 2010-11-04
Thanks for all of your replies, and tips guys! I think I am finally ready to get started with my server install. Thanks again.

---

### Post by Cfhs_1 on 2010-11-08
So, I've finished the project. The server is running perfectly, I can access it anywhere on my LAN thanks to samba, i can access it externally from the web thanks to apache, I can work on it through SSH, and webmin on my LAN, and I've been ripping DVDs to my server using handbrake (linux version) It's so nice to be able to watch a DVD from any computer in my house, without having to worry about finding the disc. Thanks for all your help, and support everyone! The ubuntu community ROCKS!!! :guitar:

---

### Post by kevinthecomputerguy on 2010-11-08
Thats awesome! Great job!!
 
-KevinTheComputerGuy

---

### Post by Cfhs_1 on 2011-05-16
> **kevinthecomputerguy said:**
> Thats awesome! Great job!!
 
-KevinTheComputerGuy

Are you the guy that wrote that amazingly helpful guide?

---

### Post by kevinthecomputerguy on 2011-05-16
I am
Thanks!

---

