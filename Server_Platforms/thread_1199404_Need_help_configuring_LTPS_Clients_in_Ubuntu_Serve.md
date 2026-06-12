---
title: "Need help configuring LTPS Clients in Ubuntu Server 8.04"
date: 2009-06-28
forum: Server Platforms
---

### Post by Avinash.Rao on 2009-06-28
Hello Everybody,

I am new to Xfce and I have recently installed it on ubuntu Server 8.04 running on Sun Fire X4150 server. I did this by manually by installing Xubuntu-desktop package and the installation went through without any problems.

I am going to be using Xfce for LTSP, but i am having problems configuring the desktop icons and many other features. :guitar:

1) All the partitions created are displayed on the desktop when a LTSP user logs in. I know i can do this by going to desktop properties, but there are many users and i cant afford to login as each user and do this. I also created the xfcdesktoprc file under the /home/username/.config/xfce4/desktop directory. But the filesystem icons still exists.

[file-icons]
show-trash=true
show-filesystem=false
show-home=true
show-removable=true

How can i have a common desktop icon list for all ltsp users.

2) I have created a xterm shortcut on the desktop, but the xterm is not same as the xterm that is in the accessories menu. Like the shortcut doesnt have any of the menus and i am not able to adjust the font size color etc. Shortcut /usr/bin/xterm

3) Also, whenever a ltsp client logs the default desktop is gnome which is not installed. So everytime the user is having to select xfce before they enter their username and password. How can i make xfce as the default Xsession for ltsp clients.

Any help is appreciated
Avinash

---

### Post by Avinash.Rao on 2009-06-29
:(

---

### Post by Avinash.Rao on 2009-06-30
I installed Ubuntu Server 8.04 and this didn't have any GUI.
Then installed XFCE instead of Gnome through apt-get install xfce.
After the installation and reboot, the default desktop session is Gnome! I dont know how this works??? how is this possible???  

To check, when i logged in, its only a Ubuntu 8.04 desktop without any panel and menu.  How can i change the default desktop to xfce? which is the configuration file?

---

### Post by Aearenda on 2009-06-30
AFAIK the server installation configures the system so it runs best as a server, with no logged on users. Although we call the central computer in an LTSP system 'the server', really it is a multiple-desktop system. I recommend you reinstall LTSP using the Xubuntu alternate install CD. You can choose an LTSP setup as you start the CD. This will get XFCE to start correctly instead of Gnome, and the underlying system will have appropriate LTSP settings.

However, if you want to persist, here are my answers to your questions:

1) What I do for multiple settings like this is to create a template user, set it how I want it, then copy the settings from that user into /etc/skel (save the old /etc/skel somewhere just in case). Then all new users pick up their settings as they are created. However, I use Gnome, so this may not work for you, and it won't work for existing users.

I also remember there being something funny about how the XFCE desktop settings are stored - you have to unset the volumes then toggle system-managed and then back to individual settings, or something like that. I'm not sure where the underlying settings are stored.

2) The accessories menu doesn't point to xterm, it points to an XFCE one. I'm sure you can find out what it is if you run it, perhaps by using 'ps aux'. Then modify your shortcut to suit.

3) When logging on to the console, press F10 to select the session type as XFCE, and make it the new default. Then look in the hidden file '.dmrc' and see what the session name is - assuming it isn't 'default', try copying that file to all your users.

---

### Post by Avinash.Rao on 2009-06-30
Thanks for your reply. I am slowly learning xfce and figuring it our things. 
I guess i will try the reinstallation of LTSP using the Xubuntu alternate install CD. Is this available for download? 

I figured out the Xterm the filename is /usr/bin/xfce4-terminal so i created a shortcut pointing to this file.

Avinash


> **Aearenda said:**
> AFAIK the server installation configures the system so it runs best as a server, with no logged on users. Although we call the central computer in an LTSP system 'the server', really it is a multiple-desktop system. I recommend you reinstall LTSP using the Xubuntu alternate install CD. You can choose an LTSP setup as you start the CD. This will get XFCE to start correctly instead of Gnome, and the underlying system will have appropriate LTSP settings.

However, if you want to persist, here are my answers to your questions:

1) What I do for multiple settings like this is to create a template user, set it how I want it, then copy the settings from that user into /etc/skel (save the old /etc/skel somewhere just in case). Then all new users pick up their settings as they are created. However, I use Gnome, so this may not work for you, and it won't work for existing users.

I also remember there being something funny about how the XFCE desktop settings are stored - you have to unset the volumes then toggle system-managed and then back to individual settings, or something like that. I'm not sure where the underlying settings are stored.

2) The accessories menu doesn't point to xterm, it points to an XFCE one. I'm sure you can find out what it is if you run it, perhaps by using 'ps aux'. Then modify your shortcut to suit.

3) When logging on to the console, press F10 to select the session type as XFCE, and make it the new default. Then look in the hidden file '.dmrc' and see what the session name is - assuming it isn't 'default', try copying that file to all your users.

---

### Post by Aearenda on 2009-06-30
You should be able to find the appropriate CD for download [here]("http://www.xubuntu.org/get").

---

### Post by Avinash.Rao on 2009-06-30
Thanks Friend!

---

### Post by Avinash.Rao on 2009-06-30
I am also trying to change the default office application from Abiword to Openoffice. How do i complish this?

Thanks again
Avinash

---

### Post by Aearenda on 2009-06-30
I think you'll find it is already set that way in Xubuntu. However, only Writer will be installed - not Impress or Calc. But you can add these later.

---

### Post by Aearenda on 2009-06-30
I just did a test installation of Xubuntu 8.04.1, and I found that even Writer was not included - so you'll need to install that. The .dmrc file contains 'xfce4' as the session name. The XFCE settings that you need to propagate to /etc/skel are stored in .config/xfce4 and .config/xfce4-session (and .config/Thunar if you want to include the file manager settings) in the home directory of the user.

PS: The LTSP chroot installation failed on my system. I expect I have a bad CD burn, but I'm checking into that.

EDIT: ignore this post, apart from the /etc/skel bit. My CD was an 8.10 CD, not 8.04. Doh!

---

### Post by Avinash.Rao on 2009-06-30
Thank you so much for your efforts. :popcorn:
Yes, when i installed xfce there was no office applications except abiword. 
I installed open office after that coz thats one of the main applications used by our LTSP users.

I will check the .dmrc and other files. 

Avinash


> **Aearenda said:**
> I just did a test installation of Xubuntu 8.04.1, and I found that even Writer was not included - so you'll need to install that. The .dmrc file contains 'xfce4' as the session name. The XFCE settings that you need to propagate to /etc/skel are stored in .config/xfce4 and .config/xfce4-session (and .config/Thunar if you want to include the file manager settings) in the home directory of the user.

PS: The LTSP chroot installation failed on my system. I expect I have a bad CD burn, but I'm checking into that.

---

### Post by Aearenda on 2009-06-30
I think you'll find .dmrc on an 8.04.1 Xubuntu install just says 'default' but it will be XFCE that is the default since Gnome was never there in the first place. Installing OpenOffice should make it be the default for opening .odt and .doc files automatically.

---

### Post by Avinash.Rao on 2009-07-01
No it doesnt, if i open .doc files Abiword comes up.
I have tested /etc/skel option on my laptop and it works. 
I first created a user and configured the desktop the way i want it with the shortcuts, wallpaper etc. Copied the .bashrc and .bashrc_logout and the .config directory to the /etc/skel directory.

Then i created a user account with the -k /etc/skel option, i logged in using the new user account and it worked, the desktop was just like it was configured for the template user account. 

Now, i will need to check this on my server for LTSP clients, guess its the same.



> **Aearenda said:**
> I think you'll find .dmrc on an 8.04.1 Xubuntu install just says 'default' but it will be XFCE that is the default since Gnome was never there in the first place. Installing OpenOffice should make it be the default for opening .odt and .doc files automatically.

---

### Post by Aearenda on 2009-07-02
I'm not certain, but you may be able to set Openoffice as the default in Thunar - something like right click a .doc file, select "open with other", choose Openoffice and click "use as default".

---

### Post by Avinash.Rao on 2009-07-02
By right clicking at the document -> 'properties' -> 'open with'. Should set default application to what you want.


> **Aearenda said:**
> I'm not certain, but you may be able to set Openoffice as the default in Thunar - something like right click a .doc file, select "open with other", choose Openoffice and click "use as default".

---

