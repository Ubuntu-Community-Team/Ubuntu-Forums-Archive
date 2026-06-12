---
title: "Remote Desktop Vista + XMING + SSH -&gt; Ubuntu Server 8.04 (LXDE)"
date: 2009-01-21
forum: Server Platforms
---

### Post by jfwiedmayer on 2009-01-21
I am spec'g out a build I am going to do tonight and basically I wanted to build a headless server which I can login to from a Vista Laptop.

I basically only want the window manager (LXDE) and the X Server to only startup ON-Demand (when I want to login remotely) so as not to use any resources unnecessarily (i.e. ssh into the box and type "startx") which is why i am shying away from simply using vnc.

I was hoping to get some feedback on the what is the best way to handle this and to login to the WM?  

What i plan on installing...

Administration/Security		
	SSH	openssh-client , openssh-server
	Webmin	webmin
	Firewall	ufw
	Honeypot	tinyhoneypot
	Remote Desktop	xdmcp?
	Rar Support	rar, unrar
	Twitter from CLI	
	NTFS Support	ntfs-3g
	Time Sync	ntp
	Systen Auditing	OSSec
	X11 Remote	?
	Window Manager	lxde
		
		
File Sharing		
	UPnP Server to xbox 360 (transcoding)	ushare (NeToU Patched) / FUPPES
	UPnP Server to Itunes	mt-daap/Firefly
	WAN FS	apache/LAMP
	Drupal	drupal5
	Phpgraphy	phpgraphy
	LAN FS	samba
	Torrent	Vuze/WebUI
	Backup	rsync
		
		
Media		
	CD Ripper	
	DVD Ripper	
	w32codecs	
	Podcatcher	podget
	Music Manager	Amarok
	IpodConvenience	Ipod-Convenience
	Tag Fixing	Jaikoz
	Media Front End	boxee

---

### Post by HermanAB on 2009-01-21
If you use SSH, then you need not run X on the server at all.  SSH has an X client built in and uses the local X server, so even if you run X on the distant server, it won't be doing anything.

Try this:
$ ssh -X -C -c blowfish user@server gnome-panel

Cheers,

Herman

---

### Post by jfwiedmayer on 2009-01-21
so no need to "startx" just fire up SSH with the -X parameters and that's it---wow!  thanks

> **HermanAB said:**
> If you use SSH, then you need not run X on the server at all.  SSH has an X client built in and uses the local X server, so even if you run X on the distant server, it won't be doing anything.

Try this:
$ ssh -X -C -c blowfish user@server gnome-panel

Cheers,

Herman

---

