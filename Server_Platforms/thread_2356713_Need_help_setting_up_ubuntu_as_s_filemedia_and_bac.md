---
title: "Need help setting up ubuntu as s file/media and back up server"
date: 2017-03-26
forum: Server Platforms
---

### Post by hashmaster on 2017-03-26
Before the " did u check the threads", "lmgtfy" , etc ask yes i did. I seem to have dug a bigger problem with that on this one. So now that's out of the way.  I am trying to turn an old desk top into a media/file/backup server. 

The devices i wish to connect to the server are: 1x windows 10 pc, 1x windows 7 pc, and 1x android 6.0.1 media box. Im using ubuntu desktop  (current stable release)which seems to run great on the hardware for the server pc.

 I followed one guide which probably got me to the start of what I needed, but i can't seem to pull up that guide again. At the do finsh of that guide I could at least see my server on my windows devices. After trying to fix the issues I can't. 

So I plan on starting from scratch again. It seems the safest bet to start there.i have 3x 1 TB hdd, and 1 680GB hdd in total. The 680 GB, and 1x 1TB hdd are currently installed. I was using the 680 as the main server system storage, and planned on using the 1TB as network storage for now and adding the other drives later once everything is set up. 

I would like to use 2 of the 1TB drives for media storage,and the last 1TB for backups and temp storage(end goal).

If your still here great. Very basics out of the way here's what I did. Fresh install of ubuntu making a swap, root, and home directory on the 680 hdd. 1TB formatted to ext4. Updated&upgrade system. Install samba, ssh, xrdp. Ssh and xRDP were in the tutorial I went thru. Did the no added security for ssh. Followed the basic suggestions to set up samba. Added to workgroup. Server showed up in both windows machines. Received either sign in with credintals box, or errors on no administrative rights, or other instances running. I could connect to the 'server' through RDP, but couldn't really do to much. Searched for fixed to what i thought my problems were and seemed to lose ground. I could no longer see the 'server' in network devices. For the credintals box I figured I needed to add a login on the server. Added users and passwords thru?"smbpasswd -a user" I believe the command was. Tried various samba configuration tools. Webadmin showed the users I added. Smb4k threw up error after error. Gadmin_samba i dont even know etc. I'm lost. I've purged and reinstalled samba a couple of times. Removed the samba folder before reinstallingsamba ,which threw up a bunch of errors. Recreated smb.conf from scratch, still no luck.  

Ultimately, what im kind of looking for is someone to break it down " Barney Style", or give me an ABC, or provide me the possible tutorials I should follow and in the order I should follow, because i cant seem ti get this one. 

Your help is greatly appreciated, and any questions you have about my post please feel free to ask.

Also I was unsure where to exactly put this, so I put it under General. If it needs to be moved to a different subtopic let me know and I will, or I guess the admin could do it also.

Again thanks for your help in advance.

---

### Post by Perfect Storm on 2017-03-26
Moved to Server Platforms

---

### Post by Tadaen_Sylvermane on 2017-03-26
Xrdp tells me you are trying to do everything with gui utilities. That is your first mistake. The command line isn't scary, and is much faster for setting this stuff up than it is to do gui, also easier to manage once its done. Install Ubuntu server, the ssh package then log in from either enother linux machine over ssh or putty from windows. 

The easy way to set up samba. You don't need workgroups and all of that nonsense. Just edit the file to match what you want it to do, make sure and create the folders with the correct permissions and don't forget to restart the smbd service after editing the main file.

[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

As an example this is all I added to the default smb.conf file to get a share running for my wifes windows laptop to backup to. Didn't add or change anything else in the file. Make sure the folder in the path exists and is read write by the user. You can find more detailed stuff online but this is basic basic way of doing it. No sense making it more complicated than it needs to be. Don't forget to do the smbpasswd -a $USER in the link above or you won't get very far. Always make sure to restart the service after editing the smb.conf file and adding a user with smbpasswd -a.

```

[yansell]
path = /spinner/backups/yansell
valid users = yansell
read only = no
create mask = 0644
directory mask = 0755

```

*EDIT*

For the storage on the drives I suggest you look at something called snapraid. Will give you some redundancy against disk failure, and is fairly easy to set up.

---

### Post by Elkenfugel on 2017-03-27
> **Tadaen_Sylvermane said:**
> .

I agree with Tadaen. Ubuntu Server is super worth it, and the performance running on older hardware is amazing (I am running a Dell SC440 and its smooth as butter).

And although I haven't used snapraid, I will be taking a look. 

Also, the Samba file sharing is a snap and loads of fun! It's so cool to see a file share running on a linux box and be able to see them on our windows computers on our local lan. 

If you need any assistance, I am sure someone here (or even myself) can help you get this up and running.

---

