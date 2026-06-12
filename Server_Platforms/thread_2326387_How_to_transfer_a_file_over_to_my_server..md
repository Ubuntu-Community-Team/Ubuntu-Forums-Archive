---
title: "How to transfer a file over to my server."
date: 2016-05-31
forum: Server Platforms
---

### Post by brayn2 on 2016-05-31
I have a .svg file on my (windows)desktop that I need to have on my Ubuntu 16.04 server.

How can I do this?

---

### Post by Morbius1 on 2016-05-31
Not a lot in information there but this sounds like a one shot deal so I'll give you *one way* to do this in a local network:

On Ubuntu:

Install droopy:
```
sudo apt-get install droopy
```
Then open a terminal and run it:
```
droopy
```

On Windows:

Open your internet browser and enter this as the location:
```
http://192.168.0.100:8000
```
[COLOR=#0000cd][I]Change 192.168.0.100 to the ip address of your Ubuntu machine.

[/I][/COLOR][COLOR=#000000]Your browser should open up to something that looks like this which will give you the chance to browse to the file you want to "upload":
[/COLOR][COLOR=#0000cd][I][ATTACH=CONFIG]269372[/ATTACH]
[/I][/COLOR][COLOR=#000000]Then hit "Send"

Note that we're talking about files here not directories. This is a temporary mini http server so if you want directories you'll have to zip it.

And to shut down the server on Ubuntu just issue a Ctrl+c

And to specify where to upload this file just change directories in the terminal before issuing the droopy command.
[/COLOR]

---

### Post by David_Wright on 2016-05-31
> **brayn2 said:**
> I have a .svg file on my (windows)desktop that I need to have on my Ubuntu 16.04 server.

How can I do this?

Your question is extremely vague.

Your could use: USB flash drive, sd card, email, dropbox, unison, syncthing, ssh, and certainly loads of other alternatives too.

Edit: **Morbius1**'s answer may have been more helpful.

---

### Post by Habitual on 2016-05-31
[http://rsync.net/resources/howto/rsync.html](http://rsync.net/resources/howto/rsync.html)

---

### Post by ajgreeny on 2016-05-31
If you want an alternative have a look at **Transfer-on-LAN** which is cross system and available for Linux, Mac and Windows, and maybe even more OSs. It needs java but that should not present a major problem and only transfers files and folders on the same LAN, not across the web.

See [http://ubuntuforums.org/showthread.php?t=2082830](http://ubuntuforums.org/showthread.php?t=2082830) for a forum thread about this, and [https://code.google.com/archive/p/transfer-on-lan/downloads](https://code.google.com/archive/p/transfer-on-lan/downloads) for the most recent, though now quite old Linux and Windows version, 0.6.1.

I don't think this is being developed or updated any more but I find it very useful.  I have not tried nitroshare, but have downloaded that to try as well.

---

### Post by houstonbofh on 2016-05-31
There are as many ways to do this as there are people doing it.  It really depends on what is going to do it more often.  Will this windows machine work with more Linux machines?  If so get winscp or MobaXterm.  If not, set up samba on the server if it will have more Windows machines connetcing to it.  Or FTP or NFS, ...  You get the idea.

---

### Post by LHammonds on 2016-05-31
If you installed OpenSSH-Server during initial setup or sometime after so you can connect to it via [PuTTY](http://portableapps.com/apps/internet/putty_portable), you should also be able to use [WinSCP](http://portableapps.com/apps/internet/winscp_portable) which is like an FTP client to allow transferring files to/from Linux/Windows.

---

### Post by The Cog on 2016-05-31
I would probably install openssh-server on Ubuntu and filezilla on windows. In filezilla, specify to use port 22.

---

### Post by lukeiamyourfather on 2016-05-31
The de facto way to copy one off files like that to a server is scp (secure copy) which will work on any server that you have ssh access to.

[http://manpages.ubuntu.com/manpages/trusty/man1/scp.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/scp.1.html)

If the local machine isn't Linux then you can use Cygwin or other applications like WinSCP. I prefer Cygwin because it has lots of other tools available besides scp.

---

### Post by Henrik_Iivonen on 2016-06-03
On ubuntu machine:
sudo apt-get install ssh

On Windows machine use filezilla.
[https://filezilla-project.org/index.php](https://filezilla-project.org/index.php)

---

