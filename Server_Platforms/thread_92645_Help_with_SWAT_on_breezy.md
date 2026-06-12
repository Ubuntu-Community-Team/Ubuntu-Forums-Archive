---
title: "Help with SWAT on breezy"
date: 2005-11-20
forum: Server Platforms
---

### Post by brokenbones on 2005-11-20
Hi,

Just for learning purposes I set up a linux box, currently hosting an empty PHPNuke portal, with XAMPP for linux installed (Apache 2, PHP5, MySQL). I also have a ftp server on that machine, all working fine.

Now I am playing with samba, and trying to find an easy GUI to help me set up the shares and permissions. Samba works, I see my shares from the windows machines in the workgroup, and I have been using webmin to admin the shares. 

However, I am trying to launch swat at [http://localhost:901](http://localhost:901) and rebooted, but it doesn't answer. I think I configured the inetd.conf and services correctly to work with swat according to step-by-step directions found somewhere in these forums. Any idea why it doesn't work ?

---

### Post by veehell on 2005-12-06
Here is my [post]("http://ubuntuforums.org/showpost.php?p=548872&postcount=3") from another thread....

There are several links outside the ubuntuforums, check them it might help you maybe.

Ad_gui: i test TkSmb (gtk) Knomba2, smb4k,  (i am missing gnome "gnomba") and some others...  I uninstall them all, because no one provide the correct action against my smb.conf :( 

smbfs mounting work perfecly withouy gui, usually. Win boxes acces homes, shares, publics normaly by the MS way. Linux box have few problems (too many auth. dialogs :( before it show the files) So after succesfull install and access to SWAT i am going to tune it up for linux box.

As my experience show me, sometimes, you need to restart winbox to take effect. If you are playing with "domain, local, preffered browsers" always check the status on electing machines. (win32 > event log > system; *nix /var/log/samba/nmbd.log )
Always have samba users created and enabled or sync unix users with samba users. this is important, because it might work ok, but you have no account to use it. And finally IPC$ use "guest" account to search the network, it is M$ weird, so if you have no guest account aliased or created you won't see any machines via smb/bcast message listings, just maybe smbfs work on some account (it depends how you set the smb.conf)

Cheers....i hope i transfer some my hints ;)

---

### Post by grendelkhan on 2005-12-06
Make sure you have this entry in your /etc/inetd.conf

swat            stream  tcp     nowait.400      root    /usr/sbin/tcpd  /usr/sbin/swat

Add that then restart inetd and you'll be off to the races.

---

### Post by veehell on 2005-12-06
ad_gui: few minutes ago i succesfully test connection to direct share folders on winbox machine, using just file browser under gnome. ... menu: go> location> (and enter > **smb://DEEPCASTLE%3B@192.168.2.101/eset** of coz edit your group and server and share smb://<samba_work_group>%3B@<machine_ip>/<share_folder_name>

I have also saved keyrings for my and remote machine to avoid the repeated asking for authentification. It is not instantly mounted, but accesible fast via browser. But i still have trouble to use the files directly in xmms, mplayer, each time no possible to read on-fly, i need to transfer them to local machine afterward it is ok. (there is something in bad in syntax \ vs / and the spaces :()
Sometimes i need to use "smb:///" instead of "smb://" (in previews installation) i don't know what is difference.

Komba2, TkSmb, xsmbrowser still have problems to connect to winbox, even if i provide correct pass/username. In stdout it shows, all shares all trees, but in GUI it show no ip(even if i specify directly) no shares  no tree etc....quite weird. Reverse access work perfectly. 

Does anyone know/find any step.by.step howto to make samba work on ubuntu ? 
I found just few common guides, some commonhowtos, but not exactly for ubuntu distribution (only for Debian). And a lot of my friends and also me and i think a lotta out there really need it. Some simply script,package, but i am not so skilled to manage it ;(

---

