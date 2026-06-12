---
title: "Trouble accessing all SWAT options"
date: 2010-05-17
forum: Server Platforms
---

### Post by ktritty on 2010-05-17
9.04 server.  Installation bundles were LAMP, SSH, Samba.  I apt-get installed xinetd and swat.  I also added a swat user, and appended this user to admin group, for convenience (this "swat user" is also used for remote admin of mail, apache, etc.)

The trouble that I am having is that when I go to http://<IP>:901 and log in as swat user, I am given a SWAT home screen that only has HOME, STATUS, VIEW options.  No way to add or manage shares or printers, etc - all of the good options!

What is it that I need to reconfigure in order to give my swat user access to all features of SWAT?


Many thanks!

---

### Post by bab1 on 2010-05-17
I would not use SWAT to configure /etc/samba/smb.conf.  It will work but it is not the most convenient way.  I have configured a root password but have never used it in conjunction with SWAT.

All of the information on configuration of smb.conf is available [**_here  _**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  You can simply use the text editor of your choice with sudo.  I use vim so my incantation is ```
sudo vi /etc/samba/smb.conf
```

---

### Post by ktritty on 2010-05-18
Thank you for your insight.  I did a little bit of homework too, and I guess it takes a few extra steps to fully secure SWAT.  Since I would be managing this server via the internet, I think I will go for the plain text method via ssh2 for this particular computer.  I will read about the SWAT as well, for future purposes, as I might need it for a server on my LAN one day.


Once again, Thanks!

---

