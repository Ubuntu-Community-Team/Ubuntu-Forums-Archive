---
title: "Setting up a file server"
date: 2010-06-20
forum: Server Platforms
---

### Post by Estanislao on 2010-06-20
Hello everyone, I am new to these forums and fairly new to Ubuntu in general. Though I do have a moderate amount of experience with computers, and know where to look if I don't know an obscure name (wikipedia). 

I would like to set up a file server that

* acts as a network file server

* acts as a file server accessible anywhere via internet
 = has a password and user protection
 = logs the uploads and downloads by users
 = is very secure

*allows the use of a portable hard drive for file storage
 = the hard drive can be disconnected and connected without messing up the server and requiring a reboot.

* allows uploads and downloads from users
 = is relatively easy to use (i.e. uses a GUI instead of a terminal interface. Though I would be willing to learn more about terminal interfaces if necessary.)

*administrator can access and change all settings from internet, (a remote connection is what I guess it should be called.)


My computer is

Processor,80531,1.7G,256K, 400 Front Side Bus,Celeron
1	7N242	Keyboard,104 Key,US,Silitek, LC,MG
1	6U220	Kit,Mouse,Personal System 2, S69,Logitech
1	4K107	Dual In Line Memory Module, 128,266M,16X64,8K,184
1	4N567	Kit,Speaker,120V,HK206,NMB,DAO
1	4U829	Modem,V92,Internal,Data Fax, Softvoice,Don Julio,AMF
1	9N645	Compact Disk Drive,128K, IDE,F5,48X,LG,8481B, Midnight Gray
1	0U408	Hard Drive,30G,IDE,5.4K,60G/P,MXT-ARES
1	4T139	Kit,Software,QIKN-NWUSR-ED- 2K2,English
1	4Y427	Kit, Software, Word Perfect Product Suite 10.0, Version 3 English
1	4W419	Customer Kit,Software, BRTNCA2K3,English
1	6Y989	Kit,Software,TXCUTDLX,F5 English
1	6W678	Kit,Software,Overpack,WXPHSP1,Compact Diskette with Documentation,English
1	4P011	Compact Disk Read Write, 680M,IDE,F5,40X,Hitachi LG Data Storage,Midnight Gray

except it doesn't have XP anymore, it has the 32bit ubuntu 10.04 server OS. Which I must say is very confusing to me, as I am not uber knowledgeable of command line interfaces.

---

### Post by CharlesA on 2010-06-20
You could try webmin or ebox for the command interface (both are web interfaces).

As for a file server accessible from the internet, Do you want to ftp files or do something else?

I've got my machine set up to to accessible via SSH and use SFTP to move files to/from it.

---

### Post by denarced on 2010-06-20
If you're not comfortable with command-line, then you're in for a nasty ride on the server-side. It's doable thou. But if you want, you can install one of the following to ease the pain:
[INDENT]
ubuntu-desktop
kubuntu-desktop
xubuntu-desktop
[/INDENT]
Those will get you a desktop-environment, either gnome, kde or xfce (in order).

charlesA's suggestion(ssh+sftp) fulfill your following requirements:
[LIST]
[*]security
[*]acts as a network file server
[*]has a password and user protection
[*]is very secure if you make it so(no root login, unusual username and complex password, possibly a keyfile instead of a password)
[*]allows portable HDD. I think just about every file-server-system will allow this since it has nothing to do with them. You'll propably have to mount the external HDD into the filesystem yourself since ubuntu server won't do it automatically, for security reasons I assume.
[*]GUI instead of terminal. This is really your choice at the client-side. You can use software like putty on windows if you want command-line or winscp if you want GUI
[*]root can change things from the internet. You can do this on command-line for sure and also on GUI but that's a bit longer story and you have a lot of options there but I don't considere it a good idea. That's just my preference although there are reasons too.
[/LIST]

---

### Post by nicolasdiogo on 2010-06-20
i have used Ebox-Platform.com for a while and it works very reliably.

if you are planning to access your data over internet - try VPN connection to make it safer.

---

### Post by Estanislao on 2010-06-21
Well thank you everyone for your help so far. As far as the protocol I do not really know what type to use, such as FTP. This is because I do not understand them. I would be willing to read the necessary documentation, though. 

I would like a GUI, as I said before, but is it possible (or even recommended) that I can install it on my 10.04 32bit server. If so, how? Detailed instructions, please, because I am pretty novice at servers and terminals. Or should I just start from scratch, like with eBox. 

The only reason I would not just do that is the eBox web site says it is based off the 8.04 Ubuntu server, I would like to stay with 10.04, and also, I would prefer to stay with Ubuntu entirely, not try to use a server that is based off another system, like Microsoft. (I really like Ubuntu's concept of humanity and I like the community!) 

The GUI preferably would be very simple, or I really do not need one if someone is willing to walk me through and/or refer me to simple documentation for learning how to use the terminal interface. 

Thanks again, everybody!

---

### Post by denarced on 2010-06-21
Do this(keeping it simple):
```

sudo apt-get install openssh-server

```
Then grab [winscp]("http://winscp.net/eng/index.php") if you're using windows to access your server or some other if you're using linux or mac.

Voila. All done

---

### Post by Estanislao on 2010-06-21
> **denarced said:**
> Do this(keeping it simple):
```

sudo apt-get install openssh-server

```
Then grab [winscp]("http://winscp.net/eng/index.php") if you're using windows to access your server or some other if you're using linux or mac.

Voila. All done

I have done as you suggested. Now can anyone walk me through how to access the OpenSSH server? I have installed Winscp also.

---

### Post by nicolasdiogo on 2010-06-22
ebox is just updating its packages to new LTS.

[ebox 1.5]("http://trac.ebox-platform.com/wiki/Document/Announcement/1.5")
here is the announcement - it is a bit difficulty to find it still..

check to see if you have the necessary packages ported to lucid - if you have the required functions for your server then give it a go.

if you are not looking to spend much time administrating your server, that is a really good tool to use as it takes care of most admin for you.

with regards,

Nicolas

---

### Post by koenn on 2010-06-22
> **Estanislao said:**
> I have done as you suggested. Now can anyone walk me through how to access the OpenSSH server? I have installed Winscp also.

1. start winscp
2. type IP adress or hostname of server. + username, password
3. use mouse to browse files and directories 
4a. drag and drop between windows explorer and winscp, or
4b. use "Norton Commander" style copy between local and remote directory tree

4a andb depend on whether you choose "Windows style" or "Midnight/Norton C style" when you set up WinSCP

---

### Post by kevinthecomputerguy on 2010-06-22
Estanislao-
You might want to give this a read through. [http://woodel.com](http://woodel.com)
Its built on Debian, but still applies to Ubuntu and addresses most of your questions above.

---

### Post by CharlesA on 2010-06-22
> **kevinthecomputerguy said:**
> Estanislao-
You might want to give this a read through. [http://woodel.com](http://woodel.com)
Its built on Debian, but still applies to Ubuntu and addresses most of your questions above.

+1 to that. It's a really detailed guide, great for learning how to do stuff on both the server and in webmin. :)

---

