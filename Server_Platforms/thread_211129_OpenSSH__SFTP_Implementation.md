---
title: "OpenSSH / SFTP Implementation"
date: 2006-07-07
forum: Server Platforms
---

### Post by Shindigy on 2006-07-07
Hello, 

I would like to implement a SFTP server with OpenSSH, protocol version 2, only. I don’t like the idea of people watching what I shave shared with clients.

I have no idea where to start; any help would be greatly appreciated!

Is OpenSSH included in the Ubuntu standard distribution? The server distribution?

Mitch

---

### Post by Randomskk on 2006-07-07
sudo apt-get install openssh-server
is what you want ;)

---

### Post by atoponce on 2006-07-07
Use aptitude in place of apt-get.  Just in case you need to uninstall, aptitude will remove the dependencies that were installed with it, as apt-get won't.

```
sudo aptitude update
sudo aptitude install openssh-server
```

Once you install OpenSSH server, change the port in the /etc/sshd_config from 22 to something well over 20000.  Obviously, you will need to open the port in your router.  Just an extra level of security from the outside world.

---

### Post by Shindigy on 2006-07-07
Can you please walk me through it.

Should I use the standard or server distribution?

So I need to install OpenSSH server, then how do I configure and set it up? Do I need a separate ftp server? From what I read this is not the case, but I need to enable a sftp service.

THANKS!
Mitch

---

### Post by jayemef on 2006-07-07
OpenSSH is an **SSH** server, which is slightly different than an FTP server. With an SSH server running, you can connect to your server from a remote machine at the commandline level, with the same experience that you would get by opening a terminal locally (though potentially slower, depending on network speeds). OpenSSH installs this, as well as an SSH client (ssh) and tools for copying files remotely (scp) and though ftp (sftp). It is also pretty well configured by default, so you shouldn't need to change anything for casual use.

To set up an actual FTP server, the Ubuntu Guide has instructions for proftpd: [http://ubuntuguide.org/wiki/Dapper#FTP_Server]("http://ubuntuguide.org/wiki/Dapper#FTP_Server")

If all you want is personal remote access to your machine, and/or the ability to copy files from your machine to another and vice versa, you should just use OpenSSH. If you want to give others access to select files, proftpd might be better (though there are better alternatives to FTP, as FTP isn't secure).

---

### Post by atoponce on 2006-07-07
> **Shindigy said:**
> Can you please walk me through it.

So I need to install OpenSSH server, then how do I configure and set it up? Do I need a separate ftp server? From what I read this is not the case, but I need to enable a sftp service.

THANKS!
Mitch The only thing that you will need to do is start it, if it isn't running already.

```
sudo /etc/init.d/ssh start
``` 
For your clients to connect, if using Windows, they can download [WinSCP]("http://www.winscp.net") as a graphical frontend SSH client for transferring files.  If using Dapper, you can use Nautilus as an SSH client or Konqueror.

_ For Nautilus client:_
Select "Places --> Connect to Server...".  Service type is "SSH", enter the info for the server, port, username, and folder to will start in.  Assign a name for the connection, click connect, enter your password, and your in.

_ For Konqueror client:_
In the address bar, enter "sftp://<name_of_server.org_or_ip_address>".  Enter your username and password, and your connected.  (<name_of_server.org_or_ip_address> should be either the domain or ip of your SSH server).

---

### Post by atoponce on 2006-07-07
> **jayemef said:**
> OpenSSH is an **SSH** server, which is slightly different than an FTP server. With an SSH server running, you can connect to your server from a remote machine at the commandline level. OpenSSH installs this, as well as an SSH client (ssh) and tools for copying files remotely (scp) and though ftp (sftp). It is also pretty well configured by default, so you shouldn't need to change anything for casual use.

To set up an actual FTP server, the Ubuntu Guide has instructions for proftpd: [http://http://ubuntuguide.org/wiki/Dapper#FTP_Server](http://http://ubuntuguide.org/wiki/Dapper#FTP_Server) I would **heavily** recommend installing the SSH server, and _NOT_ an FTP server.  With SSH, everything is encrypted in the wire, whereas FTP is not.  This means that anyone using network security tools in or out of the network can sniff out your username and password with little effort while using FTP.  If FTP is necessary, it should only be implemented in local networks, or for read only anonymous usage.  FTP and telnet are the Achiles Heel to network file transfer security.

---

### Post by Shindigy on 2006-07-07
> **jayemef said:**
> tools for copying files remotely (scp) and though ftp (sftp)

I read that there is a chance that ver. 1 of SSH, which is insecure, is enabled by default. Is this true?

I would like to use SFTP vs. FTP due to the fact that I can trust no one with the data available on this server and I must make it as secure as possible.

Mitch

---

### Post by Randomskk on 2006-07-07
Sorry, I thought you meant you had a server and wanted SSH on it.
If you want to make an SFTP server, for securely accessing, uploading and downloading remote files, I'd go with the following options:
1) Default server install, from server disk. It's minimal, fast, does what you need.
2) Install the openssh-server package, which starts up an SSH server.
3) Configure it however you like in /etc/ssh/sshd_config; as atoponce recommended if you'll be exposing SSH to the world changing the port number is a good idea.
4) A windows SCP client, or FileZilla (I believe supports SFTP) should be able to connect to your server.
5) Under linux, both the default file browsers can do this.
In konqeuror, it's fish://username@host to connect (does sftp:// work too?)
6) Your clients will use SSHv2 anyway, and I wouldn't worry about SSHv1. You can probably tweak it in the config files.

Finally, note that you can control which users are allowed to log in, and you may wish to look into using secure certificates instead of passwords for SSH.

---

### Post by jayemef on 2006-07-07
[quote=atoponce]I would heavily recommend installing the SSH server, and NOT an FTP server.[/quote]
Werrd. I had edited my post to mention this, but you replied before I submitted.

[quote=Shindigy]I read that there is a chance that ver. 1 of SSH, which is insecure, is enabled by default. Is this true?[/quote]
You are corrent that 1 is less secure, but I'm fairly sure you are incorrect that it is enabled by default. To check, run
```
$ cat /etc/ssh/sshd_config | grep Protocol
$ cat /etc/ssh/ssh_config | grep Protocol
```
This should output *Protocol 2* for both. I'd recommend looking through these files to see how other stuff is configured.


The following link is a pretty nice and easy-to-follow security how-to. I have a local copy saved: [http://www.cromwell-intl.com/SECURITY/linux-hardening.html]("http://www.cromwell-intl.com/SECURITY/linux-hardening.html")

---

### Post by Randomskk on 2006-07-07
Jayemef, the last two links you've posted have two [http://s](http://s) at the front o_o;
Is this an accident, or some sort of evil forum bug?

---

### Post by jayemef on 2006-07-07
My bad. I didn't clear the http:// that gets inserted automatically with the link button. That being said, I never do. Thought it was automatically corrected... Hopefully I haven't been posting broken links everywhere else.

Thanks for the notice. I corrected them.

---

### Post by Shindigy on 2006-07-08
```
sudo aptitude update
sudo aptitude install openssh-server
```

Hey guys,
I downloaded and installed Ubuntu Server and logged in and ran the code above and the system returned the following msg. "timestamp too far in the future Aug 27 10:10:25 1956"

Is my clock set wrong? If this is the case, how do i set it?
Note: I am not connected to the internet so my clock was never set.

---

### Post by Randomskk on 2006-07-08
sudo date MMDDhhmmYY
For instance:
sudo date 0709022906 (the 9th of july, 0229 (am), 2006)
I believe that should work, if not try without the two year digits at the end.
Once you've done that, do this:
sudo apt-get install ntpdate
Then run it:
sudo ntpdate pool.ntp.org
That will bring your system clock accurate.

---

### Post by Shindigy on 2006-07-09
> **Randomskk said:**
> 
3) Configure it however you like in /etc/ssh/sshd_config; as atoponce recommended if you'll be exposing SSH to the world changing the port number is a good idea.


How do I open the config file? Do I need a different password then the user account I am using? Or am I just making a beginner mistake? Second Linux system without a GUI for me and  I am learning alot. Thanks for all the help!

By the way I have a second hard drive hooked up, I would like to use that as the sftp storage folder. 

> **jayemef said:**
> 
```
$ cat /etc/ssh/sshd_config | grep Protocol
$ cat /etc/ssh/ssh_config | grep Protocol
```
This should output *Protocol 2* for both.

The second outputs "protocol 2,1. As you know I have not been able to make changes to the config file so the setting might be in there.

---

### Post by Randomskk on 2006-07-09
Ok, so to edit files...
First thing, you need to be root, as your normal user can't edit these config files. So we start the command with `sudo`, which runs the rest of the command as root.
Next, we need a text editor. Personally I use vim (`vi`), although it can be a little confusing at times. Something easier is `nano`, which is fairly good.
So far, then, we have `sudo nano`. Finally the file itself finishes the command:
sudo nano /etc/ssh/sshd_config
At this point (unless you did an expert install) it will ask for your USER password, and then nano should load.
Make whatever changes you want (note that the second Protocol 2,1 you saw is FINE, that's in the ssh client file not the server), then press ctrl+X, y, enter.
That saves the file in nano and quits, and if you re-open the file you should find it's changed.

Once you've changed it, you need to restart SSH server:
sudo /etc/init.d/ssh restart

Before closing the current SSH window, open another SSH session to the server to check you still can, don't want to accidentely lock yourself out.

---

### Post by Shindigy on 2006-07-09
Do i need to enable sftp??  Where do I set each users username, password, folder and which drive its located? As I have two drives and I would like to use the small disk as my os disk(done) and the other as a storage drive!

Thanks for all the help!!
Mitch!!

---

### Post by Akita on 2006-07-09
As others have mentioned, just:

apt-get install openssh-server

Protocol v2 is the only one accepted by default in a Debian/Ubuntu installation. You can check the config file in:

/etc/ssh/sshd_config

Look for the line that says "Protocol 2".

Sftp is handled by sshd (the openssh server), so there isn't anything else to install.

---

### Post by Shindigy on 2006-07-10
> **Akita said:**
> As others have mentioned, just:

apt-get install openssh-server

Protocol v2 is the only one accepted by default in a Debian/Ubuntu installation. You can check the config file in:

/etc/ssh/sshd_config

Look for the line that says "Protocol 2".

Sftp is handled by sshd (the openssh server), so there isn't anything else to install.

Done all of that! SSH is running! Now the question is how/where do I set user names and passwords? 
Can each person have their own folder that they are locked too?
If so where is this set up?
Also, I have a second drive in the system. I believe I formatted during the installation.
How do I point the users to that drive?

Thanks Again for ALL the HELP!!!!
Mitch

---

### Post by Shindigy on 2006-07-10
If I add a standard user with:
```
sudo useradd USERNAME
```
Would that user be able to login with ssh?
How do I cahnge a password?

Still woundering how to use my other drive.

Thanks

---

### Post by eltech on 2006-07-12
hmmm ... Please bare with me here. I'm a Gentoo user giving Ubuntu a run here :) 

Ive installed openssh, ive configured it; but how can i set it to start on bootup?

In gentoo its normally rc-update add openssh default (or what it would look like)

How can i achieve this action in Ubuntu

---

### Post by PanzerMKZ on 2006-07-14
what about vsftpd?  maybe that is more what you are looking for.  



Panzer

---

### Post by Randomskk on 2006-07-15
Two replies, I'll start with the quick one:
eltech, if you installed OpenSSH via apt-get (sudo apt-get install openssh-server) it will *automatically* start at boot, nothing extra to do.

[QUOTE=Shindigy]
Do i need to enable sftp?? Where do I set each users username, password, folder and which drive its located? As I have two drives and I would like to use the small disk as my os disk(done) and the other as a storage drive![/QUOTE]
1) sftp is managed by OpenSSH, you don't need to enable it.
2) To set usernames etc etc, try this:
```

useradd -md/path/to/second/drive/username -s/bin/bash -pPASSWORD USERNAME

```
This will make the user, with the home directory in /path/to/second/drive/username, using the standard bash shell, with the password PASSWORD and the username USERNAME.
For more info on that command, try: man useradd

---

### Post by compbrain on 2006-07-16
> **Randomskk said:**
> 
3) Configure it however you like in /etc/ssh/sshd_config; as atoponce recommended if you'll be exposing SSH to the world changing the port number is a good idea.


As a matter of best practice, changing the port number constitutes security by obscurity, which is never a good form of security. Best thing to do is make sure all accounts have strong passwords.

---

### Post by Randomskk on 2006-07-16
Best to just limit the port to IPs you trust, and then limit it again in /etc/hosts.allow.

This way only trusted IPs can even see that the port's open, and then even if you get around the firewall you need a valid IP or you'll be rejected by the TCP wrapper.

Security by obscurity *by itself* is bad, but it can add another layer of security, so long as you don't trust it exclusively.

Another good idea is only using public/private certificates, only allowing a whitelist of users to connect, not allowing root logins, all the stuff like that.

Depends how much time you want to spend securing it :P

---

### Post by tekrei on 2006-12-15
Can anybody tell me in sftp how to force users to chroot to their home directories?

---

