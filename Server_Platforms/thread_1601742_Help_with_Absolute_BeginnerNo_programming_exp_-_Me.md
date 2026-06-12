---
title: "Help with Absolute Beginner/No programming exp - Meerkat 10.10 server edition"
date: 2010-10-20
forum: Server Platforms
---

### Post by kirbatron on 2010-10-20
I installed Ubuntu 10.10 on a spare computer yesterday, I know it installed because I barely managed to get through it, now I can access the command line interface and login, as well as login as root... and thats about as far as I understand. 

My goal is to have a home file server where I can access files and such without gumming up the laptops (my wife's and mine), as well as possibly be able to access the files elsewhere (e.g. at my brother's home 20 miles away). 

Can I have my laptop running OS X and Ubuntu, and My wife's laptop running Windows 7 and ubuntu, share music, video, and other media files (my wife would really like to use itunes), and if so, how do i connect to the server and then view the files? How do I save files to the server?

I have been searching up and down through guide after guide and haven't been able to find one that is geared toward ubernewbies like me, with no programming experience. I finally found one that explains beginner concepts of bash scripting/shell and kernel up through intermediate stuff, but I guess the help i'm looking for here is either:

1. A guide or walkthrough somewhere that will explain everything that is going on during the installation and concept of the server--Help me help myself

or 

2. Explain wtf is going on with the computer and server with each step. My goal is to understand the system so that I can maintain it. I just want to understand!:confused:

Thanks for the help and replies. Cheers.

---

### Post by cariboo on 2010-10-20
You don't need any programming experience to use the ubuntu server, you can do everything with simple commands. Have a look [here]("https://help.ubuntu.com/8.04/serverguide/C/index.html"), it's not for the latest version, but it is still relevant.

---

### Post by CharlesA on 2010-10-20
The 8.04 server guide that cariboo907 posted a link to has good info.

There's also the [10.04 server guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html").

---

### Post by psychotix on 2010-10-20
Hey CharlesA,

So a couple of things. First, there are lots of ways of doing this; some more complicated than others. Second, accessing these files from outside your home network will probably require you to configure your home router (NAT/DMZ/Port Forwarding) to allow outside connections to a local computer. 

I recommend using ssh server on the Ubuntu server. If you want to access files from inside and outside of your home network you can use the ssh/sftp service. it is secure and there are quite a few free utilities that will allow you to MOUNT the file system on OSX and Win 7.  

1. make sure your ubuntu server has a static ip address 
2. Install SSH server on your Ubuntu server.  You should now be able to login to the ssh server via SSH (using putty (win) or ssh via console (OSX).  You should also be able to access files on the ssh server using WinSCP/Expanddrive/netdrive. I'm sure there are some Mac utilities out there as well. 

* for outside access
3. Configure your router to PORT FORWARD tcp port 22 to the ip address of the ssh server.  This will allow you to connect via ssh to the server using the ip address that your ISP has given you.  *Note that this Ip address might change.

HTH

---

### Post by CharlesA on 2010-10-20
Yep, psychotix, that's right.

The way I access my machines is allow SSH access to the internet and transfer files via sftp if I need them.

As long as you secure SSH properly, it works great.

Also, if you have a dynamic IP, you'll need something like dyndns to make sure you can connect should the ip change.

---

### Post by SeijiSensei on 2010-10-20
Personally I prefer using full-time OpenVPN tunnels ratber than SSH to connect among physically separated machines unless I just need to open a shell.  There are many advantages to connecting securely to a machine inside a remote network.  For instance, I've set up my local DNS server to use forwarder records that point to my clients' internal DNS servers.  I can then use FQDN's in the client's domain. Another attraction is being able to run an application locally like Access but use ODBC to talk to a client's internal PostgreSQL server running on a Linux box.  One especially helpful feature of OpenVPN is that you can install it on a box behind a client's firewall and have it set up the virtual connection back to you automatically when it boots.  Makes remote support really transparent.

---

