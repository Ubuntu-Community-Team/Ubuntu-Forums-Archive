---
title: "Ftp"
date: 2010-01-21
forum: Server Platforms
---

### Post by henryblowery on 2010-01-21
Hey y'all. I'm trying to setup a web server that I can access remotely to upload/edit html files etc. I've got Ubuntu Server edition 9.10 installed on my computer, with the LAMP stack + Webmin. My missing link is a FTP server right? I've been planning on installing ProFTPD, but I can't for the life of me find out how to configure it so files are put in the correct place (the correct place is /var/www right???) I know when I had the desktop version installed that file was readable, but not writable by default. Is it the same deal with the server edition? Do y'all have any idea how to upload html files to my server in the correct place? 

Gray

---

### Post by xkaliburx on 2010-01-21
Hey Gary, not sure on Pro, but yes you are correct with that URL.  Another way which is how mine is running (simply because I have multiple people), is run vsftp as the ftp server, enable the local user option, which basically means each local user can FTP in their home folder;
ex. if your username is gary, then upon vsftp install, local_enable option turned on, you can FTP right in which will dump you in the /home/gary folder.

From there you can simply make a mywebsite folder, and change your apache config to use that /home/gary/mywebiste folder as the default docroot.

Good luck ...

---

### Post by Lars Noodén on 2010-01-21
FTP is not needed unless you also plan to publish your files read-only via Anonymous FTP.  The protocol itself is insecure and wrapping it in SSL or TLS is a lot of work and can be difficult to keep during a major system upgrade.

To upload files you already have SFTP as part of the OpenSSH-server which  you probably already have running.  If not, once it is installed enter something similar to the following url in your SFTP client:

```

sftp://henryblowery@myserver.example.org/var/www/  

```

That assumes also that you have write access to the directory /var/www

For SFTP clients you have a fairly wide choice that includes these:
Filezilla,  Konqueror, Dolphin, Nautilus, Cyberduck, Fugu, and Fetch. 
Of course there is also the text client, sftp, always available via the shell.

Or if you want to have folder linked to the remote server instead, then you can use sshfs and then no other client is needed, just a way to move or work with the files in that folder.

---

### Post by henryblowery on 2010-01-21
Ok, so I don't even need FTP? I'm very computer illiterate. Is there anyway you can tell me, step by step, what I would need to do to upload my website files to the apache server remotely via Webmin? I think I just fixed it so I have write access to /var/www I guess we'll find out in a little while.

Gray

---

### Post by Lars Noodén on 2010-01-21
> **henryblowery said:**
> Ok, so I don't even need FTP? I'm very computer illiterate. Is there anyway you can tell me, step by step, what I would need to do to upload my website files to the apache server remotely via Webmin? I think I just fixed it so I have write access to /var/www I guess we'll find out in a little while.

Gray
FTP is not needed, or even desired, if all you want to do is upload / download files privately to your web server.  It's been around since 1971 and when the WWW started, there was no alternative and back then there were no real problems using it either, not like now.  So it's not surprising that there is a lot of material referencing it.  What is surprising is that the outdated references persist.  Tectia SSH has been around for over 15 years now and OpenSSH for over 10.

Here are the steps:

1) Make sure that openssh-server is installed on the machine where your LAMP set up resides.  It probably is already.  If you can log in via ssh it is there for sure.

2) Pick a few sftp clients so you can compare and contrast, so that when you choose the one you like you know that it is better than the others.  

Choices for Ubuntu include: [Filezilla](apt://filezilla/), [Nautilus](apt://nautilus/), [Dolphin](apt://dolphin/), or [Konqueror](apt://konqueror/)

Choices on other systems include [Filezilla](http://filezilla-project.org/), [Fetch](http://fetchsoftworks.com/), [Fugu](http://rsug.itd.umich.edu/software/fugu/), and [Cyberduck](http://cyberduck.ch/). 

Install the ones you want to test and when you're done, uninstall the ones you don't want to keep.

3) Connect to your web server using the url format like this:

```

sftp://*user*@*server*/path/

```

*user* is the user account on the server

*server* is the hostname or ip address of your server

*path* is the directory (e.g. /var/www/) that you want to go straight into.  If you leave that blank, you will go into the account's home directory and will have to click your way up or down or over to the one you want to be in.

---

### Post by henryblowery on 2010-01-21
I think we're getting somewhere. I've got openssh and installed Dolphin. But I typed "sftp://gray@192.168.1.107/var/www" in the window where you type a URL, and got the following message, "Firefox doesn't know how to open this address, because the protocol (sftp) isn't associated with any program."

Was I typing "sftp://gray@192.168.1.107/var/www" in the right place? If I was what do you think went wrong?

Thanks for your help!

Gray

---

### Post by Lars Noodén on 2010-01-21
Firefox is a web browser.  

Dolphin is a file manager, which is more oriented to transferring files.
Use sftp in Dolphin.

---

### Post by henryblowery on 2010-01-21
I put Dolphin on the computer which is being used as a server. Am I supposed to have it on my other computer too? Sorry for my ignorance. I told you I was a noob :(

Gray

---

### Post by smo0th on 2010-01-21
> **henryblowery said:**
> Hey y'all. I'm trying to setup a web server that I can access remotely to upload/edit html files etc. I've got Ubuntu Server edition 9.10 installed on my computer, with the LAMP stack + Webmin. My missing link is a FTP server right? I've been planning on installing ProFTPD, 
Gray

Good, I use ProFTPd

> **henryblowery said:**
> but I can't for the life of me find out how to configure it so files are put in the correct place (the correct place is /var/www right???)
Gray

Since you want it to admin your website files, yes, that should be your ftp root.

> **henryblowery said:**
> 
I know when I had the desktop version installed that file was readable, but not writable by default. Is it the same deal with the server edition? Do y'all have any idea how to upload html files to my server in the correct place? 
Gray

Use these steps to install and configure:
```

sudo apt-get install proftpd
sudo nano /etc/proftpd/proftpd.conf

```

This is my conf file, should work for you too, I modified default root to match your needs:
**cat /etc/proftpd/proftpd.conf**
```

Include /etc/proftpd/modules.conf

UseIPv6				on

ServerName			"Debian"
ServerType			standalone

<Global>
	AllowForeignAddress     on
</Global>

DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

DefaultRoot			/var/www
DefaultRoot	~

RequireValidShell	off

Port				21

PassivePorts                  49152 65534

MasqueradeAddress		192.168.0.2

MaxInstances			30

User				nobody
Group				nogroup

Umask				022  022
AllowOverwrite			on

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
	QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
	Ratios off
</IfModule>

<IfModule mod_delay.c>
	DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
	ControlsEngine        off
	ControlsMaxClients    2
	ControlsLog           /var/log/proftpd/controls.log
	ControlsInterval      5
	ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
	AdminControlsEngine off
</IfModule>

MaxLoginAttempts    5

<Limit LOGIN>
	AllowUser ftpuser
	DenyAll
</Limit>

<Directory /var/www/*>
	AllowOverwrite on
	<Limit READ CDUP CWD XCWD XCUP>
		AllowAll
	</Limit>

	<Limit STOR STOU CWD MKD>
		AllowAll
	</Limit>

	<Limit RMD XRMD DELE>
		DenyAll
	</Limit>
</Directory>

```

cheers,

**G**

---

### Post by henryblowery on 2010-01-21
Thanks for all the help y'all. I've got NO clue what I did, but I'm now able to upload files via Webmin. I'm still gonna play around with different ways of doing it to find out what I like best.

Gray

---

