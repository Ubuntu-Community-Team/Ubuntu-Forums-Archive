---
title: "Just installed Ubuntu Server... now what?"
date: 2011-01-22
forum: Server Platforms
---

### Post by Ranger_Joe on 2011-01-22
Hello everyone,
I just got done installing Ubuntu Server 10.04 on a home server. Now what should I do? I was hoping to have 3 computers connected to it so that we can all share files... wirelessly if that's possible.

Please help me take the next step. Thanks!

Also: Does Ubuntu Server have a GUI or command line only? Thanks!

---

### Post by amra.sonntag on 2011-01-22
Hi,

you could install OpenSSH Server. It comes with built in SFTP, so you could use it to share files. This way you could share your files secure.

Look at: [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Another way would be to use vsftpd or Samba - a great source for information is the official server guide. You can find the right one for your Ubuntu Version here: [https://help.ubuntu.com/](https://help.ubuntu.com/)

If you can do this all wireless depends on your hardware and setup. In a home setup, you probably have a router handle the network traffic and it should be no problem. You just have to make sure, that your router assigns a static IP to the server, because otherwise you'll have to update Bookmarks at the clients every now and then.

Also: You can install the GUI like more or less everything else from the Desktop Edition.

---

### Post by Bradyhawke on 2011-01-22
> **Ranger_Joe said:**
> Also: Does Ubuntu Server have a GUI or command line only? Thanks!

It can have both!!!

You should consider using a minimal GNOME desktop setup for your server if you want a GUI to use.  Since you already installed/setup your 10.04 server and it boots to a command line, then all you'll need to do is install the core GNOME desktop package (without all the added packages).  Use the following code:

```
sudo apt-get install gnome-core xauth xorg
```Then when you boot up your server and log in, it will still take you to the command line, but now all you need to do to start the GUI is type the following:

```
sudo startx
```Your server will then start the GUI.  You can then do what you need to within the GUI, and then when you're done you would log out by choosing *System-> Log out root...* This will take you back out to the command line.

This minimal GNOME desktop GUI will be missing quite a bit of perks as well.  At this point you may want to add a few packages for software management, terminal, system tools, log viewer, disk utility and update manager. To add these in, from the command line type in the following code:

```
sudo apt-get install synaptic gnome-terminal gnome-system-tools gnome-utils gnome-disk-utility update-manager
```You could also add in some administrative tools like system-config-printer, system-config-samba and gnome-nettool:

```
sudo apt-get install system-config-printer-gnome system-config-samba gnome-nettool
```And finally if you want a little more than the basic GNOME theme for the GUI, then you could install the light-themes package:

```
sudo apt-get install light-themes

```----------

I'm currently running two 10.04 servers - 1 web server & 1 server that I'm experimenting with (building/learning a good email server setup).  When I first started with Ubuntu 9.04 I installed the server with a full desktop, but soon realized that I was just wasting system resources as well as running less secure servers.  Since I moved on to 10.04, I've set up both servers to run the minimal GNOME desktop and only use the GUI if I really need it.  I find myself doing more and more work from the command line, but sometimes it is easier to copy / move files within the GUI (at least for now it is for me).  Your server will be much more secure if you don't run it with a GUI, but if you really need to, I'd suggest following this idea and go with the minimal GNOME install and only put in the packages you feel you will absolutely need to use

Also, I picked up a good reference book for Ubuntu 10.04 LTS server - here's the link:

[http://www.surfingturtlepress.com/books/ubuntu1004server.html](http://www.surfingturtlepress.com/books/ubuntu1004server.html)

Totally worth it IMHO, can't tell you how many little things it helped me with.  All the code & info I provided above came from this book.

---

### Post by Ranger_Joe on 2011-01-25
Thanks Brady,
I think I've decided I'm just going to stick with the command line. I need to learn it better anyway. I'm sick of being so dependent on GUI. 

As far as SSH, I'm going to install something tonight. I'm going to crack open the official guide right now and see what I like. I'll post what I end up doing and questions if I have trouble.

---

### Post by matt_symes on 2011-01-25
Hi

> Just installed Ubuntu Server... now what?

Now you can smile ;)

Install webmin or learn to use ssh for remote management. Webmin allows you to configure and maintain your site through a browser. SSH is great but learn how to lock down the ssh server. 

ssh with screen is a winner. Read up on attach and detach with screen. _Use keys_ for ssh.

```
man screen
```

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Kind regards

---

### Post by Ranger_Joe on 2011-01-25
Ok guys, 
I need to clear up a few things. From what I've read OpenSSH comes pre-installed on both Ubuntu Server and Ubuntu Desktop. So... theoretically, I already have it.

How do I "connect" my laptop running Ubuntu 10.10 to my server running Ubuntu 10.04? 

I just want to be able to do all the cool servery things I bought it for. You know?

---

### Post by Ranger_Joe on 2011-01-25
Ok, let me specify exactly what I want to do. Perhaps that will help you guys help me.

I want to host all my family's files on the server and have those files be readily accessible on all 3 computers. I basically want it to be a shared directory.

I've installed OpenSSH and vsftpd via the command line on my server.

Now... what do I need to do to transfer all those files to the server. Please let me know. Thanks!

---

### Post by kevinthecomputerguy on 2011-01-25
Give this a read

[http://woodel.com](http://woodel.com)

Your a little further along than this, but read pages 1 thru 3, then decide how you want to proceed.
because of how far you are already, i would read without doing, then do.

-Kev

---

### Post by Ranger_Joe on 2011-01-25
Thanks Kevin,
I will do that and post back with any decision/questions.

---

### Post by cariboo on 2011-01-25
@kevinthecomputerguy

When I go to your site using chromium, I get a blank page, see screenshot. Using firefox it works ok.

---

### Post by kevinthecomputerguy on 2011-01-26
I knew i should have added google.com to my special thanks section, my bad. :- )
 
j\k, thanks C, i will look into that asap.
 
-Kev

---

### Post by kgatan on 2011-01-26
"Webmin" is a good edition when you just got started with ubuntu. Its a webinterface for configuration and information.

Its not in the repository but there are plenty of guides on how to install it and its not difficult.

---

### Post by amra.sonntag on 2011-01-26
If you got SSH and vsftpd installed - you are more or less set. Use the anonymous ftp user vsftpd creates and share files between all Computers. Or create a Share account on your Server and use this one. That way you could also use SFTP, it comes with SSH, and be sure that nobody is eavesdropping.

If you do use everything (Server and remote PCs) behind a Router Firewall - you might want to check out NFS. This one is nice, because it looks like a local Filesystem to the enduser.

---

### Post by arrrghhh on 2011-01-26
> **amra.sonntag said:**
> If you got SSH and vsftpd installed - you are more or less set. Use the anonymous ftp user vsftpd creates and share files between all Computers. Or create a Share account on your Server and use this one. That way you could also use SFTP, it comes with SSH, and be sure that nobody is eavesdropping.

If you do use everything (Server and remote PCs) behind a Router Firewall - you might want to check out NFS. This one is nice, because it looks like a local Filesystem to the enduser.

For local file sharing, NFS is the way to go.

However, if your clients don't support it (Windows...) then samba is really the only way.  FTP is nice for external stuff, but it's not secure and kinda a pain compared to SMB or NFS (again, assuming you're all on the same LAN).

---

### Post by Ranger_Joe on 2011-01-27
Ok... before we go any further, can someone please explain what the difference is between SSH and vsftpd? What does each one do? Do I need both or just one?

Sorry for not clearing this up earlier. I read the official guide but I don't really understand their distinct characteristics.

Thanks!

---

### Post by kevinthecomputerguy on 2011-01-27
You could read pages 1 thru 3 on my site :- )

---

### Post by amra.sonntag on 2011-01-27
Ok, let me try to clear things up a bit.

SSH: Is used to make an encrypted connenction between a client and a host (your server). It can be used to connect with a shell and login or emulate encrypted FTP like filesharing via SFTP. It has several strong points - everything is encrypted while floating the internet, you can use public ssh keys for authentication of your users (no need to type in passwords all the time), and you can use it to 'tunnel' other application that normally aren't encrypted through SSH and secure them this way.
But it will probably take you some time to configure it and you'll need to read some man pages etc.

vsftpd: is a ftp client. standard ftp is unencrypted traffic over the internet. If you use it as anonymous ftp - read only is probably a good idea. If you use it in a per user base - you run the risk, that your login data gets sniffed over the internet.
I believe it is easier to configure but unless you use it with SSL encryption (you can enable that in the config files), less secure.

NFS: You export an entire directory on your server - and can mount them on local directories on your clients. Very nice for filesharing at home, because you don't have to log in into anything - you just browse to the place at which the export is mounted. (for a standard setup you can follow the ubuntu server guide)
However - securing NFS is troublesome at best and to integrate it with windows too.

Samba: If you use windows machines - get samba as the easiest option.

I hope that helps.

---

### Post by Ranger_Joe on 2011-01-27
Yeah Amra,
It actually helps a lot. I think I'll be using SSH to remote administrate and NFS for internal file sharing. 

Correct me if I'm wrong... but using NFS behind a firewall will at least make it somewhat secure right?

Also, one more question:
I'm sitting at school right now in the library. Let's say I wanted to connect to my server at home, on the other side of the city and say... update it or shut it down. Could I do that using SSH?

---

### Post by amra.sonntag on 2011-01-27
Glad I could help out.

If you are behind a router with firewall (blocking all traffic from the outside world) you should be fine using NFS. In the NFS configuration you will also see, that you can specify the IP addresses where exports will be available. So you don't need to worry to much.

And yeah - using SSH you can basically acces your Server from everywhere in the world. But you need a fixed IP address to do so, because otherwise you won't find it. ;) You can also use a dynamic DNS service like dyndns.com to provide you with a address that you can dynamically map to your IP (using ddclient on your server for example).
You will also have to forward the SSH Port (standard is 22/tcp) on your router to your server, to allow yourself to get past the router firewall.
But if you do so - you will soon notice that ppl will try to access your server (check auth.log at /var/log). So making your sshd_config as secure as possible is recommanded. Some thoughts on that: use Public Key authentication only, allow only your own username to connect and install denyhosts.

---

### Post by arrrghhh on 2011-01-27
amra is spot on.  I just want to reiterate his warnings on opening up anything to the open internet - that also opens up any potential hackers, so using pubkey authentication (you can do this passwordless, but that's less secure... if someone gets your keys then they can get in right away without a password.  If there's a password on it, then you have some time to generate new keys before they crack your password.)

Basically if you restrict everything to your LAN, it's much more secure.  If you want to be able to access the server remotely, get all your ducks in a row as you're then opening it up to anyone on the internet.

---

### Post by The Real Dave on 2011-01-27
I'm just gonna throw this in here, my [Howto]("http://linuxexpresso.wordpress.com/2010/10/17/howto-ubuntu-vnc-encoding-server/") on setting up a lightweight VNC-accessed Ubuntu server install.

This gives you a low RAM graphical interface, which is accessed completely over the network.

---

### Post by kevinthecomputerguy on 2011-02-03
Cariboo907-

I think i have my website working in Chrome now. Can you please give it a quick test.

Thanks for pointing that out, i appreciate it.

-KevinTheComputerGuy

---

### Post by cariboo on 2011-02-03
> **kevinthecomputerguy said:**
> Cariboo907-

I think i have my website working in Chrome now. Can you please give it a quick test.

Thanks for pointing that out, i appreciate it.

-KevinTheComputerGuy

It works from here now, thank you.

---

### Post by kevinthecomputerguy on 2011-02-03
Awesome! thanks again
-Kev

---

### Post by 1serveyou on 2011-02-17
> **arrrghhh said:**
> amra is spot on.  I just want to reiterate his warnings on opening up anything to the open internet - that also opens up any potential hackers, so using pubkey authentication (you can do this passwordless, but that's less secure... if someone gets your keys then they can get in right away without a password.  If there's a password on it, then you have some time to generate new keys before they crack your password.)

Basically if you restrict everything to your LAN, it's much more secure.  If you want to be able to access the server remotely, get all your ducks in a row as you're then opening it up to anyone on the internet.

When I had my old server connected to the internet, I had pubkey authentication with a password, but everytime I attempted to connect with a new computer it as "Are you sure you want to connect with xxxx key"(I can't remember exact wording), but it made it seem like anyone could connect, if they accepted the key given. If I didn't have a password on it, anyone could have gotten onto my server it seemed like. Am I understanding that correctly?

---

### Post by arrrghhh on 2011-02-17
> **1serveyou said:**
> When I had my old server connected to the internet, I had pubkey authentication with a password, but everytime I attempted to connect with a new computer it as "Are you sure you want to connect with xxxx key"(I can't remember exact wording), but it made it seem like anyone could connect, if they accepted the key given. If I didn't have a password on it, anyone could have gotten onto my server it seemed like. Am I understanding that correctly?

No... that's not how key authentication works, they would have to have the key, and their key would have to be added to your server.

If you want, read about [OpenSSH key-based auth](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) - that's an Ubuntu community doc that explains it all.

Usually people disable password logins if you use keys - that way no body can login to your server unless they have the correct key, and the other key has been added to the server.  It's a *very* secure way of connecting...

---

### Post by 1serveyou on 2011-02-17
> **arrrghhh said:**
> No... that's not how key authentication works, they would have to have the key, and their key would have to be added to your server.

If you want, read about [OpenSSH key-based auth]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") - that's an Ubuntu community doc that explains it all.

Usually people disable password logins if you use keys - that way no body can login to your server unless they have the correct key, and the other key has been added to the server.  It's a *very* secure way of connecting...

I must have set it up wrong, I'll have to look more into it. Thanks!

---

### Post by Stephann on 2011-02-17
Just a suggestion; while learning command line is fantastic, there's a few great reasons to have a GUI (of some sort) on a server, especially if you're just learning.

Having a GUI means:

- Web browser: (for cutting and pasting as you run through things)
- Multitasking: three or four terminals open at a time (if you're like me), plus said browser, so that while apt is downloading something heavy, you can still be working on configuration, etc
- VNC access: Meaning, if you initiate a command that will take a long time (say, an rsync snapshot backup, or an overnight 'bablocks' test) you won't have to start over if a girlfriend or kid just happens to unplug your remote machine (or laptop runs out of battery, or "windows" crashes, etc.)  Using a VNC client, you can shut down your remote machine overnight, come back in the morning, and find your server humming along nicely.  Dave mentions vnc4server, though I've had luck with tightvncserver myself.  The double bonus is that once VNC is up and running, you won't need to keep a monitor attached (also known as running headless.)
- Very, very little overhead (on modern machines.)  I run a few servers at home on Mac PowerPCs with 400hz, with 256-500 megs of RAM.  Gnome is just a tad sluggish on load up, but Xfce fires right up.  Or, you can go even more minimal with Openbox (like I use on my NFS.)  Openbox is a great way to go if you want the feeling of doing 'almost' everything by command line, while still having some of the basic GUI applications.  My full installations on both run under 3 gigs, swapfile included.
- Time saved: Gparted, for example, lets me configure a disk in a fraction of the time that it takes me using fdisk.  For example, I always keep an 8mb buffer between partitions, and Gparted can crunch the math from megs to blocks, something that I'd just be punching numbers in a calculator for.  The graphical LVM manager is clunky, but still far quicker than the command line utilities.
- Secure.  "As" secure as not having one?  Maybe not, but the real risk posed by a GUI is on par with the real risk posed by putting seven locks on your bike, instead of eight.  A Linux system, by nature, is very secure.  So long as you have an adequate firewall on your gateway, running a gui on your home file server is farrrrr less risky than turning on a windows machine.

The command line is a powerful tool, and learning it is essential; that's why there's a terminal emulator in every gui system.  But unless you have a goal of working in Systems Administration, there's no reason you can't avail yourself of the other tools out there.

---

### Post by matt_symes on 2011-02-17
Hi

> Multitasking: three or four terminals open at a time (if you're like me), plus said browser, so that while apt is downloading something heavy, you can still be working on configuration, etc

@Stehpann. Have a look at screen. You will only ever need one terminal open with screen.

It's great for remote SSH as well as you can ssh into a box, start a screen session. When you want to log off _detach_ from the screen session and when you log back on _reattach_ to the existing screen session created earlier.

With screen you can create a number of pseudo-terminals and give them work either in the foreground or background, detach when required and reattach later to see progress or continue using an existing session.

```
man screen
``` 

or Google it.

My personal opinion ? Screen or webmin for servers; vnc (freenx) for desktops (but others have different opinions). It frees up more resources for streaming, storage etc on a server.

Kind regards

---

### Post by Stephann on 2011-02-17
> **matt_symes said:**
> Hi



@Stehpann. Have a look at screen. You will only ever need one terminal open with screen.

It's great for remote SSH as well as you can ssh into a box, start a screen session. When you want to log off _detach_ from the screen session and when you log back on _reattach_ to the existing screen session created earlier.

With screen you can create a number of pseudo-terminals and give them work either in the foreground or background, detach when required and reattach later to see progress or continue using an existing session.

```
man screen
```or Google it.

My personal opinion ? Screen or webmin for servers; vnc (freenx) for desktops (but others have different opinions). It frees up more resources for streaming, storage etc on a server.

Kind regards

Hi Matt,

Screen's a great program, and it solves one of the problems, certainly.  There's ways around each of the pros I stated, which is one of the great parts about *nix, that there's a dozen ways to tackle any problem.  

My experiences with webmin have been less than great; there's a reason it's not carried on the Ubuntu and Debian repos.  If the OP's goal is to better learn his systems, webmin isn't going to help him do that.  

That said, any processor with a gigahertz processor or more isn't going to see any significant overhead hit by running a lightweight X server.  On my home gateway I run Xfce4 on my G4 PowerPC with 450Hz, with an average of 7% CPU load and 1% memory on Xtightvnc.  (XFCE + VNC.)  Even SSH can be a resource hog, especially if you're using SCP (crypto being resource intensive) and I simply don't require that degree of cryptography in my already secure home environment.  

For me, the argument against using a GUI on a server would be on par with trying to overclock said server by that same amount (in my case, by 7% on an already 10 year old machine.)  The benefit of a meaningful, mouse driven cut and paste is worth it, alone.

Warm regards,

Stephan

---

