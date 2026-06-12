---
title: "4 weeks with linux"
date: 2008-05-13
forum: Testimonials &amp; Experiences
---

### Post by milanvora2 on 2008-05-13
4 weeks with Ubuntu and all is still looking very good. I did a lot of trials:

Tried & worked:

- Backup partition with Clonezilla
- Setup NFS & Samba to share with other PC's
- Virtualbox USB Support
- Customizing Desktop Environment (multiple wallpapers, effects )
- Automating downloads with nzb
- install win media player & ie 6 (thought it would help me for 1 site)
- started trying to help people in forums

Tried & gave up:

- 64 bit (webcam not working and then i didn't want more issues to solve)
- optimizing xorg.conf (as long as the setup is working ....)
- can't get to view webcast on [www.willow.tv](www.willow.tv) (works via virtualbox, so i gave up)

Tried & solved, but such things should not happen

- Had to disable ide drive before installing (i have sat + ide) and the device was getting wrong id 
- amarok collection updates running all the time

Issues open

- Skype video quality (not as good as under windows)
- Skype video controls lacking during chat
- get usb webcam to work under virtualbox (cam recog, but no video)
- good red-eye removal tool (tried digikam & gimp) but not as easy as current windows based sw.
- getting some window games to run ( but again they are working with virtualbox)


Wife and kid have also switched to ubuntu. They are liking it.
I wish the skype issue is solved then i get rid of windows on laptop too.

---

### Post by enbuyukfener on 2008-05-13
1-3. I don't work much with Skype and webcams in Linux so won't be of much help. Have you tried getting the webcam to start in Ubuntu, e.g. by running a webcam program such as "cheese" and seeing if that bridges to the virtual machine? Also, is the bad video quality due to connection lag or the software? Is video fine when played locally?

4. Image editing is not up to par in Linux. I use Photoshop Elements through WINE which works flawlessly and supposedly, Photoshop CS2 does too. I don't know about others. Check the WINE app database ( [http://appdb.winehq.org](http://appdb.winehq.org) ) to see if your windows software runs properly.

5. I assume you know about Wine, check the Wine application database at [http://appdb.winehq.org](http://appdb.winehq.org) for info on how to get individual games to work as well as reports on how well it worked for users on their set ups. Cedega by Transgaming is a commercial alternative which supposedly works better than Wine. You may be interested in "wine-doors" which does the work of setting up DirectX and some common games for you in a package manager style (as well as other stuff such as fonts, media players, IE, ...).

Also, assuming you are using Gnome (the default for Ubuntu), try "Exaile" for the music player instead of the KDE app Amarok, Exaile is effectively the same thing with a nicer look and better performance as it is for Gnome/GTK.

---

### Post by milanvora2 on 2008-05-13
1-3 is a logitech/skype issue. For the Logitech 9000, skype & logitech worked to provide high end drivers and software it gives a fantastic resolution under windows. 
Under linux, it works but gives an average quality and the control to change the settings during the talk are not there.
The main question is if with vmware the usb port would allow to recognize and make the logitech wiork under guest xp session.


4-5, Thanks for the tips. I'm familiar with winehq and cedega.  To be honest we don't play much games, so it's not really an issue. The last issue i faced was capitalism 2 and hoyle casion 2008, both give problems while runnign with wine. I don't want to pay for cedega as i have virtualbox and they run fine under virtualbox.


i'll give exaile a shot. but to be honest, the system is flying right now, so i'm not facing any performance issues. But i'll give both banshee and exaile a shot.

---

