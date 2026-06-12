---
title: "Questions re new server setup"
date: 2007-04-23
forum: Server Platforms
---

### Post by willough on 2007-04-23
Hi,
I am ready to buy a new server and set up Ubuntu 6.06 LTS.   I downloaded, installed and practiced a bit on an old machine for a couple of weeks and am now ready to take the plunge.  It's for our small office with 5 or 6 workstations, all various OS flavors of Windows and the server will primarily for file sharing.  All users will run software on their workstations and access shared files on the server.  I have 2 questions:

1) Raid configuration - I am probably going to buy a Dell Poweredge 1900 with either Raid1 with two 160 GB hard drives, or, Raid5 with a PERC 5/i, Integrated Controller Card and three 160 GB hard drives.  If I understand everything correctly (a big 'if') the Raid1 would be software Raid set up during the Ubuntu install; the Raid5 would be hardware Raid and should be recognized during setup.  The cost spread is not very meaningful, a few hundred dollars.  I want to be able to recover from any drive failure. Please let me know which you think best and if I am on the right track. 

2) Graphic interface vs command line -  I originally installed the command line interface on my practice computer but I later opted to install the GUI and then found the system much easier to learn.  Going forward, using Ubuntu as our server I would prefer the GUI but have read elsewhere that performance is compromised.  We do not have intense computing needs, mostly file sharing as noted above.  I think I would find administrating the server easier with the GUI.  Will I be making a poor choice if I go that route?

I've read numerous posts in these forums and think the knowledge sharing and spirit of helpfulness is terrific.  Thanks to all.

Barry

---

### Post by rsermilik on 2007-04-24
If you make a raid using the raid controller then it's a true (hw) raid. During setup the OS will only see a single disk. If the money i not a problem and you have the space then mount an extra hd in case you want raid-5. Perhaps a total of 5 disk. Then one of them will be a standby disk which the controller automatically puts in during a failure on one of the other disk.

If you are only 5-6 users and its only a fileserver with no heavy load (write access all the time) then a mirror (raid-1) will be enough. 

GUI vs non-GUI have brought up many feelings on the forum:-)
From my point of view many people think having a GUI will give them a windows-like access to all the configuration files....
Many posts talks about security and/or performance problems. If the server is directly connected to the internet then it could be a security problem, but in your small company as a fileserver? No!
Perhaps just start the server non-GUI and if you want to use the GUI then give the command "startx". Then X-windows will start. When you exit from the GUI you are back in the CLI.

regards

---

### Post by willough on 2007-04-24
Thanks rsermilik for your response.  I took your advice in large part and bought the server today, with hardware Raid5 and controller as I cited.  System has three drives which I feel OK about.  If you think more would be wiser I think I can still add, but I'm not sure what advantage this provides except more redundancy.

Regarding starting Ubuntu in non-graphic mode and exiting from GUI back to CLI, I am not sure what you mean.  When I boot now I am taken directly to a GUI login and after user name and password I am in the GUI.  I don't see any way to exit to CLI.  All the exit options indicate otherwise.  'Quit' is a complete system shut down.  Other options like hibernate, log off, etc don't get to the CLI.  I know I can open a command line window and I have run commands from it in the past but the GUI is still visible.  (Sorry but I am not at the computer with Ubuntu at the moment so don't have it in front of me to reference).  Any advice appreciated.

Thanks for your help.

Barry

---

### Post by Big Ed on 2007-04-24
If you are getting a gui, then you've installed the desktop edition of Ubuntu.  Are you sure that is what you wanted to do?  The server edition is stripped down (no overhead from the gui and other programs not normally needed on a server).

Regardless, Ctl-Alt F1 thru Ctl-Alt F6 will give you six different cli logins.  Alt F1 thru Alt F6 to switch between them once you are out of the gui.  To get back to the gui from any of the other terminals, use Alt F7.

HTH,
Ed

---

### Post by rsermilik on 2007-04-25
Big Ed is wright that you must have installed the desktop version. But as he write thats ok.
If you get a terminal window then give the command:  sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
Then gdm (GUI-controller) will not start on boot and you have a CLI interface.
If you want a GUI just write: startx and the GUI comes up. Log-out from the GUI gets you to the CLI again.
I suppose its rc2! Check your runlevel in the terminal window by giving the command: runlevel
If its 3 instead then the above will be /etc/rc3/....

If you one day wants to start the GUI again by default then just rename back to S13gdm.

---

### Post by gusjones on 2007-04-25
I am mainly after setting up a small Apache intranet server, am I right in thinking that I can install all the sever processes on the desktop version of Ubuntu and that the server install runs without the gui purely to avoid performance degradation?

Also if anyone can point me in the right direction for Apache setup I'd be grateful, I'm looking to port across an intranet site running on Apache suse Linux and basically dump it down onto my Fiesty fawn PC.

The chap who set it up on the SUSE is using a mixture of python and perl scripts and SQL also. I'm pretty much a noob at this as I'm mainly a C programmer (I'm really a design engineer who mucks about with PCs but when the IT guy [for our office of 25] left I was asked to take on his role too).

I am hoping to get the site running on my Ubuntu box before safely playing around with it, etc.

---

### Post by Big Ed on 2007-04-25
There is a lot more on a desktop installation than you either want or need on a server.  Think of everything that you want your desktop machine to do and compare that to what you want your server to do.  The server's job is to serve up (or receive) files using a protocol like apache, ftp, ssh, etc.  The desktop machine's function is to manipulate those files in all the myriad ways that are possible.

Ubuntu server has a lot of things pre-configured, like LAMP (which can be a real pain to get right if you don't know what you're doing).  During the server install, LAMP is a one-button install option.  Pretty hard to beat.

I installed the server edition and my box was ready to go in just a few minutes.  Try that on a desktop.  

There is no real reason not to use the server edition on a machine whose sole task is to be a server.

HTH,
Ed

---

### Post by gusjones on 2007-04-25
...I'll give this some thought...

---

### Post by willough on 2007-04-25
I think my original thread has now gotten joined with another from gusjones who sounds like he expects to do much more with his server than our rather simple file sharing.   It is correct that after initially installing the command line server install I added the Desktop on top of it.  Per BigEd's suggestions I see that I can easily go in and out of the GUI to the CLI and visa versa.  That being the case is it OK to retain the desktop or should I re-install and use command line only?  I actually will be doing a new install anyway once the new server hardware arrives.  I would prefer having the Desktop when needed and command line for the rest of the time, providing that is a good way to go.

Regarding rsermilik's suggestion that I use the following command so I will start at the command prompt rather than GUI, the only difference I see is the uppercase and lowercase "s" in s13gdm.  Is that correct?
> sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm

Lastly and as already mentioned, I have ordered a new server with hardware Raid5, controller card and three identical 160GB SATA drives.  When I do a new install of Ubuntu are there suggestions for partition sizes of boot, swap and the rest.  In other words, should I manually configure this?   I believe I should avoid the software Raid section altogether.

Thanks to all for your valuable input.

---

### Post by rsermilik on 2007-04-26
In /etc/rcN.d where N is 0-6 you have links to scripts in /etc/init.d. All links starting with S is executed when entering the runlevel (N is the runlevel), All links starting with K is executed when leaving  the runlevel. S for Start and K for Kill. Renaming a link to start with s means the program (script) won't get executed but you still knows after 3 month that it was a Start script;-)
If you install X at a later time it could be that you don't have the link. It could also be S22gdm or any other number between S and gdm (or kde of xdm) depending on how you configure the GUI.
I haven't done this myself since my servers runs without GUI. S13gdm is a softlink to ../init.d/gdm (Absolute path is /etc/init.d/gdm).

When starting the server and the RAID controller is booting it tells you to press Ctrl-S (if I'm not wrong) to configure the RAID. During Ubuntu installation don't do any soft-RAID configuring. 

For partitioning its a good idea to write down what your server must do. You wrote earlier 'primarily for filesharing' but what else? Also a mailserver? Then you also need a separate partition for mail. How much mail do you get? Will it be on the server or downloaded to the clients? How big a file share do you need? Theres a lot of things that must be planned when using a server in real  production rather that at home:-) What about backup..................

regards

---

### Post by willough on 2007-04-26
> For partitioning its a good idea to write down what your server must do. You wrote earlier 'primarily for filesharing' but what else? Also a mailserver? Then you also need a separate partition for mail. How much mail do you get? Will it be on the server or downloaded to the clients? How big a file share do you need? Theres a lot of things that must be planned when using a server in real production rather that at home What about backup..................

Not mailserver in the traditional sense.  We use Pegasus Mail for interoffice and external mail and individual folders are on the servcer.  But everyone runs their own copy of the software.  Probably 1 or 2 GB of space for that would suffice.  5 GB would last for years.   I don't know if these mail folders require a separate partition; they don't have one on our existing Novell server.  Regarding backup,  I didn't purchase a tape drive when I ordered the server and plan to do something afterward.  I'm not sure what method to use and if I should archive, so we can add a tape or external hard drives later.   Other than that it's just files we all share, spreadsheets, word processing, graphics, accounting.

---

### Post by rsermilik on 2007-04-26
If you don't have your own MTA (like postfix or MSExchange in winworld) then you don't need a separate partition for mail storage. 
At work we have a SuperDLT tape drive for backup in our file server but actually I don't know if its useful in case of a catastrophe. If all raid-5 disks and SDLT goes down I probably can't get the same hw anymore.. Does the backup then work. I suppose it does but you never know...

Probably a USB2 disk will be enough for backup of your server. Its easier and cheaper than tapes.

Edit: Forgot to say there is a project called FreeNAS, based on FreeBSD if you only need a files erver.

---

### Post by glenby on 2007-04-27
is there a lamp for desktop version? or some useful doco on setting up/configuring apache2 under feisty?

I am basically using feisty as a test environment to create an intranet (hopefully using apache).

in the older days - you got documentation and it wasnt hard to configure apache - there were even webpage apps to configure it.

now it seems with apache 2 even the doco isnt linked to the website and finding
info is almost more trouble than it's worth.
I have checked the help pages, everything but configuring apache - mod-perl, php you name it,
linking the doco in so it shows - not a thing.
even /usr/share doco doesnt show properly. not the formatted pages.

I consider it fairly sucky at this stage, I have looked for an hour in ubuntu forums and this is probably my last shot at it.

fanx

---

### Post by rsermilik on 2007-04-28
Glenby: On [www.apache.org](www.apache.org) you can find all the documentation you need.

---

