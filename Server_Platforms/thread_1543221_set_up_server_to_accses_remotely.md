---
title: "set up server to accses remotely"
date: 2010-07-31
forum: Server Platforms
---

### Post by philipballew on 2010-07-31
i am wanting to install ubunru server edition on an older sony vio desktop to use as a server i can access remotely. i will be needing to however access this server remotely from a college i attend throughout parts of the year. how exactly would i go about doing this?

---

### Post by spynappels on 2010-07-31
What do you want the server to do? What do you want to use to remote access the server, SSH and CLI or some type of GUI such as Webmin? The answers you need depend on a lot of factors and giving some more information will make them more relevant.

---

### Post by philipballew on 2010-07-31
well id like to use it to store files likr music and such and be able to accsess the files from the computers at home and be able  to accsess this computer remotely when im gone from college. to be able to see the files on it with a gui would be nice, is there a way to get the computer to show in natulas?

---

### Post by philipballew on 2010-08-01
anyone?

---

### Post by drdos2006 on 2010-08-01
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by spynappels on 2010-08-02
Have a look at using a VPN to access the server securely when you are in a remote location as well.

---

### Post by YesWeCan on 2010-08-02
Yes, I second the OpenVPN suggestion. It is excellent and in my experience it is bomb-proof. OpenVPN makes a connection between client and server that is very much as if you had connected them with a LAN cable, except better because the connection is encrypted.

You need to read the OpenVPN Howto: [http://www.openvpn.net/index.php/open-source/documentation/howto.html](http://www.openvpn.net/index.php/open-source/documentation/howto.html)
I would set up a point-to-point tunnel (tun) link. This is what I have actually done with my server.

---

### Post by chrisinspace on 2010-08-02
I'm using a couple of tools through SSH.  For remote access to the GUI desktop I set up FreeNX and I have been loving it.  It runs over SSH and performs way better than VNC.  It was super easy to configure and cross-platform (I actively connect from Linux and Windows machines).  For file transfer, I just use Filezilla and set up a SFTP connection (SSH File Transfer Protocol).  I don't have a static IP address, so I created a host address using No-IP.com.  It works great.

---

### Post by philipballew on 2010-08-02
from what ive looked at i think after i install my server i want to install webmin. but not sure if this is the best way to set up a file server that i can accses remotely

---

### Post by Maheriano on 2010-08-02
Use NoMachine to get a graphical look at your desktop and just use the built in file browser to copy files.

---

### Post by chrisinspace on 2010-08-02
> **Maheriano said:**
> Use NoMachine to get a graphical look at your desktop and just use the built in file browser to copy files.

Exactly.  FreeNX is the open source implementation of NoMachine.  Although, I'm not sure how you would use the built-in file browser to copy files.  Does it support remote copy/paste of files?  

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by philipballew on 2010-08-02
what exactly is that and how would i go about doin
 that

---

### Post by philipballew on 2010-08-02
now i would be able to do accsess this remotely? and id there a guide or tatorial about how to do all this

---

### Post by chrisinspace on 2010-08-02
> **philipballew said:**
> now i would be able to do accsess this remotely? and id there a guide os tatorial about how to do all this

1. Sign up for a [free No-IP account]("http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html") if you don't have a static IP.  When you are connecting to your server from any remote computer (no matter what software you use) you have to have a host name that points to your home network.  Most home ISPs give you a dynamic IP address that can change.  If you use the IP it will work for a while (probably a long while), but it could change at any time, cutting you off.  No-IP lets you register a host name and then a little piece of software running on a computer inside your network regularly updates your account with the appropriate external IP address.

2. Create a port mapping in your home router or firewall to forward port 22 to your SSH server.  If you don't know how to do this, look for documentation from your router/firewall vendor.  If you want to increase security, you can change the port number in your OpenSSH settings.

3. Set up SSH using [this guide]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html").

4. To set up FreeNX, follow the steps in the link I posted above (skip the NeatX stuff).

5. Set up a new connection in the NoMachine client.  Enter your host address and the correct port number (default is still 22; this uses ssh, as well). In the 'Desktop' section, leave the first drop-down set to 'Unix' and select Gnome, KDE, etc from the second drop-down (you have to install a desktop environment on your server for this to work...just pick whatever you installed in this menu).

6. Install Filezilla and the NoMachine client on the computer you want to use to remotely access and transfer files with.  So, if you are taking a laptop to school, set them up on this machine.

7. Create a new site in the Filezilla site manager.  Enter your host address and the correct port number (default for ssh is 22).  In the 'Servertype' drop-down, choose "SFTP (SSH File Transfer Protocol)"  Enter the username and password for an account that you previously set up on that computer.

8. Test your connections.

With this setup, you get multiple ways to interact with your server, depending on what you want to do:

[LIST]
[*]FreeNX/NoMachine - remotely log into the graphical desktop of your computer
[*]SSH in terminal - remotely administer your computer with the CLI
[*]SFTP (Filezilla) - securely transfer files to/from your home server
[/LIST]

---

### Post by philipballew on 2010-08-02
now is this what i will do after i install ubuntu server edition?

---

### Post by chrisinspace on 2010-08-02
Yes.  All of this is after the OS installation.  You can definitely use the server edition, but it will work with any version.  If you do install server edition and you want a graphical desktop, you will have to install that manually.  By default, the server edition is CLI only.

---

### Post by CharlesA on 2010-08-02
There's already a thread about this here: [http://ubuntuforums.org/showthread.php?t=1543881](http://ubuntuforums.org/showthread.php?t=1543881)

If you really want a GUI, just install the desktop edition then install whatever packages you want on it (packages are the same for the server and desktop editions)

---

### Post by philipballew on 2010-08-02
so if i install the desktop edition i can set that desktop to act as a server?

---

### Post by CharlesA on 2010-08-02
> **philipballew said:**
> so if i install the desktop edition i can set that desktop to act as a server?
Yes.

---

### Post by arrrghhh on 2010-08-02
> **philipballew said:**
> so if i install the desktop edition i can set that desktop to act as a server?

As CharlesA said, yes you can do this.  The whole point of the server distro is to have a fully-optimized setup for services.

You can easily setup all of the same services on the desktop edition.  If you want/need a GUI, then the desktop edition is probably a better fit for you.

For those that CLI/SSH access is enough, that is what the server edition is for :D

---

