---
title: "So, you want a server with a GUI?"
date: 2007-04-10
forum: Server Platforms
---

### Post by VinceDee on 2007-04-10
> **rsmiff said:**
> Will there be a release with a GUI? I'm tired of command line.

This has become a very common question regarding the Ubuntu Server Edition. There are many users who want the convenience and ease of using a Graphical User Interface (GUI) with their server software. More often than not, those users are told that Linux is and should be a command line only experience.

Unfortunately, it's the *"servers don't need no steenkeeng GUI"* attitude that's helping to hold many people off of using Linux as a server solution. In fact, IMO, it's that attitude that has made it so difficult for Linux on the desktop, too. I remember the huge battle a decade ago just to convince Linux people that X was a good thing for Linux. Now, just about every Linux distro uses X. Don't worry, a GUI for Linux servers is inevitable because **it makes sense**. The trick will be to implement it sooner rather than later so people can begin using it now.

I recently checked out the NuOnce CentOS+BlueQuartz package in my search for a GUI server solution. It's very nice. It combines CentOS (a modified version of RedHat Enterprise Linux) with the BlueQuartz GUI (Basically the Sun RaQ550 GUI, which is now opensource) into an easy-to-use webserver solution. 

Download it from here, burn it to a CD and install on a spare computer to play with it:

[http://www.nuonce.net/bq-cd.php]("http://www.nuonce.net/bq-cd.php")

While it's not based on Ubuntu, it will give you a taste of what some of the possibilities are for Ubuntu's future, *IF* we can show people that the way forward for Ubuntu Server Edition is with an (optional) GUI. (EDIT: note that BlueQuartz is a browser-based GUI, so you use it from another computer on your network or VPN)

If you want to make suggestions for Ubuntu development, you can start here:

[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss")

Vince


EDIT: Here's a screenshot found elsewhere on the net that shows what BlueQuartz looks like
[IMG]http://img219.imageshack.us/img219/107/dnssettingskh5.jpg[/IMG]

---

### Post by az on 2007-04-10
If someone wrote or ported a nice GUI for Ubuntu server, then it would be used.

No one is stopping anyone from doing this.  It's just not all that important to a lot of people.  It doesn't mean it's prohibited or anything.

---

### Post by scrooge_74 on 2007-04-10
Is this any different from say, just installing Icewm or XFCE and use it?

---

### Post by chakkaradeep on 2007-04-10
It sounds to be similar to [WebMin]("http://webmin.com/")

---

### Post by justin whitaker on 2007-04-10
> **chakkaradeep said:**
> It sounds to be similar to [WebMin]("http://webmin.com/")

That was my thought as well. Why not just run Webmin?

---

### Post by rsermilik on 2007-04-10
> Is this any different from say, just installing Icewm or XFCE and use it?

Yes there is a big difference. Using Icewm/Gnome/KDE/XFCE.... just give you a graphical user interface. You still need vi (or what editor you prefer) to manage the configuration files for all the services running on your server.

BlueQuartz, Webmin.. gives you webbased access to these files. You don't need to figure out where the files are.

---

### Post by chakkaradeep on 2007-04-10
> **rsermilik said:**
> 
BlueQuartz, Webmin.. gives you webbased access to these files. You don't need to figure out where the files are.

Since its web based, you could access from any where :KS

---

### Post by maxwas on 2007-04-10
I also use bluequartz in local network lab environment. I previously used an old raq3 but adding extra functionality e.g mysql was an absolute mightmare. It lets me have all the servers i need for my students to mess with: apache, php, mysql, dns, ftp, its got the lot, and you can have them all up and running in 10 mins. It saved me a lot of hassle, and i prefer the bluequartz gui to the original cobalt job.

However in the same lab i have an ubuntu server with xubuntu-desktop installed that i route the local network clients through onto the academic network using firestarter ICS - but ssh, dont tell the network admin ;)

max

---

### Post by VinceDee on 2007-04-10
Maybe a better example I could have used would have been Xandros' new server product. It's an all-in-one solution with a built-in "management console" (basically a graphical interface).

See this link for a number of screenshots:
[http://www.xandros.com/products/business/server/info/screenshots.html]("http://www.xandros.com/products/business/server/info/screenshots.html")

Frankly, Webmin is a great tool, and other tools like ISPConfig are handy. But it seems to me that what would be really helpful as far as a GUI interface for servers would be a graphical front end that takes up as small a resource footprint as possible. For example, you boot the server and you're presented with a BlueQuartz-like interface so that you can add websites, users, edit config files, change settings, etc from one interface. Sometimes people only have one computer to use as a server and they don't want to have to add a resource-hungry desktop environment to administer the server or have to log in from another computer.

And the "write it yourself" response isn't entirely helpful. I can't write it myself because I don't know how, but that doesn't (and shouldn't) keep me from seeing that there's a need out there and advocating for it. Clearly there's an increasing clamor for a GUI for servers, so it's just one more area where Ubuntu can lead the way. Either that or someone else (like Xandros) will.

Vince

---

### Post by justin whitaker on 2007-04-10
> **VinceDee said:**
> Maybe a better example I could have used would have been Xandros' new server product. It's an all-in-one solution with a built-in "management console" (basically a graphical interface).

See this link for a number of screenshots:
[http://www.xandros.com/products/business/server/info/screenshots.html]("http://www.xandros.com/products/business/server/info/screenshots.html")

Frankly, Webmin is a great tool, and other tools like ISPConfig are handy. But it seems to me that what would be really helpful as far as a GUI interface for servers would be a graphical front end that takes up as small a resource footprint as possible. For example, you boot the server and you're presented with a BlueQuartz-like interface so that you can add websites, users, edit config files, change settings, etc from one interface. Sometimes people only have one computer to use as a server and they don't want to have to add a resource-hungry desktop environment to administer the server or have to log in from another computer.

And the "write it yourself" response isn't entirely helpful. I can't write it myself because I don't know how, but that doesn't (and shouldn't) keep me from seeing that there's a need out there and advocating for it. Clearly there's an increasing clamor for a GUI for servers, so it's just one more area where Ubuntu can lead the way. Either that or someone else (like Xandros) will.

Vince

Vince, 

Let's break down the pieces. 

First, you need to have X load, because you need to display the server panel somehow. That does not completely shoot the "lightweight" idea.

Next, now that you have X running, you need an interface. Have you seen Xampp? There is a nice gui for that that loads in a browser page. You could do something like that: have a browser open automatically when X launches instead of a desktop environment, and load webmin, xampp, or whatever. 

All of this can be handled in the .xinitrc file. 

Now some of the other things (console? file manager?) that will take some integration: the javascript/php tools exist, but aren't integrated into a complete server management plaform, AFAIK.

---

### Post by maxwas on 2007-04-10
I dunno, maybe i am wrong, but i think i know what vince is getting at.

If i remember correctly bluequartz does *not* run X at all. It's all done through apache. 

Once the system is installed you are confronted with the command line (with messages that tell you where to go for information, etc.) But more importantly it tells you that in order to administer the server, go to a client on the same network, open a browser and login through [http://server_ip/admin](http://server_ip/admin).

The web based interface has been built along with certain scripts to explicitly handle admin and server tasks, would it be so difficult to port such a thing to ubuntu?

While i am not an experienced webmin user by any stretch, in previous experiences i have had to play about with it somewhat to get it working the way i want, and i never really have, and thus ended up doing things manually anyway.

Max

---

### Post by az on 2007-04-10
Webmin does not work and that's the only reason it is no longer in the Ubuntu repositories.

---

### Post by gurgle on 2007-04-11
good thread. I have been playing around with my new RAID setup and edgy server, and using WebMin. It seems to work OK, but the RAID stuff seems a little borked. I am curious, why do people say webmin doesnt work?

---

### Post by ryan555 on 2007-04-11
I don't know why it supposedly doesn't work.  I downloaded Webmin from [http://www.webmin.com]("http://www.webmin.com") and have had no issues with it so far on 6.06 LTS server.

---

### Post by az on 2007-04-12
> **ryan555 said:**
> I don't know why it supposedly doesn't work.  I downloaded Webmin from [http://www.webmin.com]("http://www.webmin.com") and have had no issues with it so far on 6.06 LTS server.

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-September/020471.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-September/020471.html)

Hervé Fache wrote:
> What about webmin?

I didn't say that tools didn't exist; I said they utterly sucked. And I
was really hoping no one would bring up webmin. It's a piece of software
so horrifyingly vile that we want absolutely _nothing_ to do with it,
not even carry it in the Ubuntu archive. The entirety of the
ubuntu-server team had a small celebration the day that package was killed.

-- 
Ivan Krsti&#263; <krstic at solarsail.hcs.harvard.edu> | GPG: 0x147C722D


Another quote regarding webmin (from ubuntu users mailling list (11/25/06):
"However, if you are competent enough to secure Webmin then you do
not need it."

---

### Post by mahalie on 2007-08-17
Queen of noobs here but despite the fact that I really like the CLI in terms of geek-club old school novelty and of course, efficiency...well, and it makes me really learn how all this stuff works (I think) the one area that is confounding me is simply moving files around. 

I set up a LAMP and use FTP from my windoze box to visualize and move files around on my home directory and well, haven't yet figured out how to set up an FTP login that will just go to WWW root. It's frustrating, CLI just doesn't cut it for me in terms of moving around the files system.

Any suggestions? I'd love to just have an file explorer with cut and paste options.

---

### Post by southernman on 2007-08-18
This is obvious for the seasoned vets and I may get buried for even saying so, but I digress.

I've been reading a gazillon articles on server security (hardening) and one of the most common factors in achieving that goal, aside for good policy and strict following of said policy, is having nothing more installed on the server than what is *absolutely required* for it's proper serving of web pages and applications. That being said, I can't see any reason to install X on a production server (enlighten me if that is incorrect).

I, like others, don't see anything wrong with GUI management apps providing they are web based and offer a tightly bound dev group that can keep security patches flowing. That's not to take any responsibilty from the server admin... not in the least.

---

### Post by johng4 on 2007-08-18
In my Xen setup I use Webmin, Plesk and ISPConfig.  I use Webmin for managing the machines themselves, while ISPConfig and Plesk manage my hosting.

Webmin works for me as of their most recent version.  Works quite well in fact. 

My Xen setup:

Mercedes - Xen host, Apt-mirror repository.
John - eGroupware Server (serves as my webmail server for domains I host)(webmin installed).
Liz - Plesk server (no webmin on this box, plesk handles everything).
Daniel - ISPConfig server (webmin installed).

The "Liz" server is about to be my test server since Plesk's free version is effectively useless, and they adamantly refuse to negotiate a lower level license for me (I have no use for a 30 domain package).

I'm looking for a good "all around" interface like Webmin that I could use for something other than webhosting.  This is why I like webmin, since its a Server GUI, not just a Web Host GUI.  

Webmin is frustrating at times though, because of the vague menu terminology.

---

### Post by wxman on 2007-10-06
> **johng4 said:**
> In my Xen setup I use Webmin, Plesk and ISPConfig.  I use Webmin for managing the machines themselves, while ISPConfig and Plesk manage my hosting.

Webmin works for me as of their most recent version.  Works quite well in fact. 

I'm sure this will really make me sound like a noob, I didn't know you can run both ISPConfig and Webmin on the same server. I thought ISPConfig re-writes the config files for it's use, and something else would interfere with it?

---

### Post by Brazen on 2007-10-07
> **wxman said:**
> I'm sure this will really make me sound like a noob, I didn't know you can run both ISPConfig and Webmin on the same server. I thought ISPConfig re-writes the config files for it's use, and something else would interfere with it?

ISPConfig rewrites the standard Apache configs, but Webmin does not run under the Apache that you would install from the Ubuntu repositories.  It runs it's own stripped down version of Apache in a total seperate location with seperate binaries and configs.

I use Webmin for managing every single one of my servers and have not had a problem with it on the 20 or so production linux servers I manage.  The only reason I coculd see anyone having a problem with Webmin is that is does not dumb things down for you.  Webmin pretty much presents all the configuration and options that would be available by editing config files, instead of using wizards and making assumptions like most other config interfaces do.

This gives the admin much more power and flexibility, but also requires that the admin actually know the service software and understand how it works.

---

### Post by southernman on 2007-10-07
According to a recent email that came across the ubuntu-server mailing list... webmin is no longer officially supported, including Gutsy. Just FYI if ya didn't know already

---

### Post by wxman on 2007-10-07
> **Brazen said:**
> ISPConfig rewrites the standard Apache configs, but Webmin does not run under the Apache that you would install from the Ubuntu repositories.  It runs it's own stripped down version of Apache in a total seperate location with seperate binaries and configs..

Here's another question then. Can I install Webmin after I've already installed ISPConfig, and Apache?

---

### Post by codmate on 2007-10-07
> **mahalie said:**
> Queen of noobs here but despite the fact that I really like the CLI in terms of geek-club old school novelty and of course, efficiency...well, and it makes me really learn how all this stuff works (I think) the one area that is confounding me is simply moving files around. 

I set up a LAMP and use FTP from my windoze box to visualize and move files around on my home directory and well, haven't yet figured out how to set up an FTP login that will just go to WWW root. It's frustrating, CLI just doesn't cut it for me in terms of moving around the files system.

Any suggestions? I'd love to just have an file explorer with cut and paste options.

Cli is great for moving files around once you get used to it.

Invest 5 minutes in reading the man pages for cp and mv and you'll reap the benefits for a lifetime.

If you're really tied to a gui, then try installing Samba:
sudo apt-get install samba

It's not hugely hard to set up, and this will allow you to see a share on your Ubuntu box from your windows machine through explorer.

---

### Post by pjbgravely on 2007-10-07
> **mahalie said:**
> ... CLI just doesn't cut it for me in terms of moving around the files system.

Any suggestions? I'd love to just have an file explorer with cut and paste options.

For a file explorer try mc. I think it is best to run Ubuntu server using ssh from a terminal in a GUI desktop. That way you can copy paste between windows. Use screen if you want keep the same programs running even if you log out.

I for one would love to see some ncurses programs for configuring apps like mysql and bind. SUSE has this with YaST but all the config files have warnings not to edit by hand. 

I dumped SUSE for Ubuntu warty warthog because it was hard to use and I wanted to learn. I switched from Debian to Ubuntu for my server for the same reason. It was hard at first but now even when working on a desktop I use the CLI because it is so much faster and easier than clicking around a GUI. 

Paul

---

### Post by Brazen on 2007-10-09
> **wxman said:**
> Here's another question then. Can I install Webmin after I've already installed ISPConfig, and Apache?

I'm not going to say I guarantee it will, because I have never done it, but I see no way that installing Webmin could mess up your current install of ISPConfig and Apache.  So I would say go ahead and do it.

I get a little edgy putting new things on production servers though, so even something I know backwards and forwards, I still make a backup before making changes on a production server.  So if this is a production server for a business, I would make a backup first.  I put all my servers in VMWare Server virtual machines so this is as easy as taking a quick snapshot.

---

### Post by oly on 2007-10-09
If anyones intrested, [https://launchpad.net/usm](https://launchpad.net/usm) which is a web gui for ubuntu which i have been working on in my spare time in python.

and the link below for some videos / screenshots of the development version.
[http://www.ubuntusm.org/index.php?Page=Forum_Topics&FID=2&TID=10](http://www.ubuntusm.org/index.php?Page=Forum_Topics&FID=2&TID=10)

---

### Post by sciurus on 2007-10-09
It wasn't finished in time for Gutsy, but I hope it will make 8.04

[https://wiki.ubuntu.com/EboxSpec](https://wiki.ubuntu.com/EboxSpec)

---

### Post by boingo-bo on 2007-10-11
yeah. I agree with this thread. Lack of Gui is what keeps people afraid of Linux.

I have been using command-line linux/unix forever, but they are not mutually exclusive. There is no reason you cant run a gui config, and then look to see what it changed.

i am looking for something which would allow non-linux knowledgable staff to provide backup support for me.

Just because you havea GUI doesnt mean you need to use it all of the time either - you can use it for setup tasks, and then turn it off until you need it again.

---

### Post by oly on 2007-10-12
The system i am working on allows this, it stores all configuration in its own format, and generates the config files from there, so you could in theory use it to create config files for other people and jst send them the resulting file.

but the service can be switched of once configured to your liking.

---

### Post by FrankVdb on 2007-10-12
I think a GUI would be used mostly by people who are non-professionals in need of a file and print server utility. Now that a lot of people are having a computer network at home, it would make sense to have a simple but efficient GUI for setting up and running a little home server.

I've been looking around too. One of the things I discovered was OpenFiler ([www.openfiler.com](www.openfiler.com)), which is basically a file server. Looks real promising.

However, I've tried to set it up on a home server (including a tape recorder) I wanted to re-install but I got lost in the huge number of set-up options... :(

For a home server, security is not as important as for web servers. I guess most of us are behind a router anyway.

---

### Post by banewman on 2007-10-12
I've just set up my first server using a headless pent 2, nfs  vnc and xubuntu. As all six computers at home run ubuntu it all works a treat. A server that delivers web pages might be a different scenario - but it was easy to set up, and is easy to maintain. Couldn't be happier. :)

---

### Post by codmate on 2007-10-12
> **FrankVdb said:**
> I think a GUI would be used mostly by people who are non-professionals in need of a file and print server utility. Now that a lot of people are having a computer network at home, it would make sense to have a simple but efficient GUI for setting up and running a little home server.

I've been looking around too. One of the things I discovered was OpenFiler ([www.openfiler.com](www.openfiler.com)), which is basically a file server. Looks real promising.

However, I've tried to set it up on a home server (including a tape recorder) I wanted to re-install but I got lost in the huge number of set-up options... :(

For a home server, security is not as important as for web servers. I guess most of us are behind a router anyway.

Both OpenFiler and FreeNAS are excellent solutions for this sort of thing.

---

### Post by FrankVdb on 2007-10-12
I should try once more to get the thing installed...

I have a SCSI card in that system and it's giving me nothing but trouble. I'll throw it out and start all over again.

---

### Post by Roxydogg28 on 2007-11-12
Would anyone happen to know if a live cd would be a good substitute for a gui on ubuntu server????? (i.e. Knoppix, etc.)  If so is it easy to get root access to the machines hardware in order to do things you would normally do if just booting from server.  I would believe that the hard drive could easily be mounted, but not sure how much else would be accessible functional.....

Thanks,

Matt

---

### Post by otake-tux on 2007-11-13
running X on an ubuntu server is a waste of system resources.

---

### Post by Harpalus on 2007-11-13
It's a matter of security. The X11 security model is horribly flawed. It's an ongoing problem, and the X team has consistently ignored it for more then a decade. The X server requires direct access to your hardware. Study the basic architecture of the X server and you'll see how it violates most basic security models. (ie, [http://www.ssi.gouv.fr/fr/sciences/fichiers/lti/cansecwest2006-duflot-paper.pdf](http://www.ssi.gouv.fr/fr/sciences/fichiers/lti/cansecwest2006-duflot-paper.pdf))

There's a reason many servers don't have GUIs. It's not just a matter of resources, but of security as well. Why would you want to run a GUI on a server? Reduce your security, waste resources, for what? The ability to have a nice fancy desktop? Such things don't belong in production environments.

---

### Post by otake-tux on 2007-11-13
> **Harpalus said:**
> It's a matter of security. The X11 security model is horribly flawed. It's an ongoing problem, and the X team has consistently ignored it for more then a decade. The X server requires direct access to your hardware. Study the basic architecture of the X server and you'll see how it violates most basic security models.

There's a reason many servers don't have GUIs. It's not just a matter of resources, but of security as well. Why would you want to run a GUI on a server? Reduce your security, waste resources, for what? The ability to have a nice fancy desktop? Such things don't belong in production environments.

this is absolutely true.  any vulnerability scanner will tell you as much. X is piss poor software.

---

### Post by Brazen on 2007-11-13
> **otake-tux said:**
> running X on an ubuntu server is a waste of system resources.

Yes, running X on a server is a horrible horrible idea.  If you need an X gui because you are a n00b and think it will simplify things, then go ahead, but when you set up a production server that will be accessible by other people, it should not have X on it.

Having a web-based gui does have it's merits though.  I put Webmin on all my servers.

---

### Post by meatpan on 2007-11-13
It sounds like the majority of posts on this thread are from users trying to install and 'play' with a simple server installation.  Ubuntu needs to do a better job explaining to these users that the pre-packaged server installation is intended for production services.   If you want to experiment with a server, install a simple distro and then manually add a server (there's even a gui for installing software!).  I run several production ubuntu systems, and the increases in load and risk related to running X are considerable.   Every cycle counts on a busy cluster of compute nodes.

Servers are not easy to properly install, run, or maintain.  They take practice, monitoring, and an active effort to improve stability, security, and uptime.  GUI front-ends to configuration scripts and running programs frequently replace a much needed understanding of the implications of configuration options, as well as critical portions of the linux environment that will inevitably impact your service.

---

### Post by Ulrich Ilianov on 2007-11-17
Thanks for your comments, I decided to don't install XFCE gui on my Ubuntu server 7.10.

---

### Post by thegnuguru on 2007-11-17
IMO we should install Webmn by default on ubuntu server and maybe steal YaST from suse

---

### Post by startlinuxtoday on 2008-01-30
you can D'n'D with any istalled GUI. hardly matters. shuffling files is not however any normal way for selecting and OS! Especially if you are wanting a server. I NEVER INSTALL A GUI ON A SERVER. and i stay away from microsoft.

---

### Post by Swerve1000 on 2008-02-08
I have been trying to install Webmin, but have had problems with the modules not being found where webmin was expecting them.

I have a few questions :)

1) On each attempted install, I first installed Gnome, and then Webmin. Would I be best to forget Gnome, and just install Webmin straight away? Perhaps the installing of Gnome is effecting the installation of Webmin.

2) My box is behind a router which issues IP's via DHCP. There is only the one box behind the router, is using DHCP OK - as it never changes, just re-issues the same IP.

3) When I install 7.10 server ed. it asks what kind of mail server setup I want, 'none', internet or internet with something else (I can't remember the additional option). Which should I go for?

4) As I am behind a router, I know i need to open a port on that so I can connect from SSH from somewhere else, but does the server need any ports setting or changing? Should they match the port on the router, or can I have different?

Any advice is appreciated, and you can see, I'm new to this and have spent the last two days failing at setting things up correctly/

Thanks!

---

### Post by lnx4me on 2008-02-08
Just throwing my 2 cents in. What happens when the GUI is broke? Or why use a GUI on something that if built right may not be touched for months if not years. One other thought hmmmm resources ????? 

my final 2 cents---- For years and years and years and some more years we had unix terminals and the mainframe and I cant ever remember having to Ctrl-alt-del to fix a fancy window. 

I dont mean anything but in reality ssh'n to a remote system to fix something takes a few seconds from the cli I have better things to do than wait for a GUI load to run a terminal to run ssh to connect to a remote system to fix the problem. just seems kinda backwards.

---

### Post by jose_ramirez on 2008-02-08
If you want a server with GUI use the UBUNTU/KUBUNTU desktop version and "convert it" to a server.

A real server should have no GUI, having to deal with a GUI add a lot of extra work to a server, you should keep it as simple as possible.

---

### Post by sokraski on 2008-02-14
Is there anyway possible to run X, set things up correctly (maybe using sadms or likewise open) and when it is all done, shut down X?  This would help me a great deal in learning.  I agree 100% with no GUI on a server, but being able to "toggle" X on/off would draw in a whole new crowd of people to the server world.  Has anyone heard of anything like this?  Just a thought.  Thanks in advance.

---

### Post by la3875 on 2008-02-21
Another thought here and this may be sacrilegious, but with all the current interest in home network NAS/SAN boxes a simple GUI for the noob crowd might be appropriate in order to extend the relevance and demonstrate the value in Open Source. Hey even M$ is jumping on the bandwagon with their new 'Windows Home Server"...

Keep up the great work all!

---

### Post by jose_ramirez on 2008-02-22
> **sokraski said:**
> Is there anyway possible to run X, set things up correctly (maybe using sadms or likewise open) and when it is all done, shut down X?  This would help me a great deal in learning.  I agree 100% with no GUI on a server, but being able to "toggle" X on/off would draw in a whole new crowd of people to the server world.  Has anyone heard of anything like this?  Just a thought.  Thanks in advance.

Well, let's say you have a Linux server on a network with for example KDE installed. From another workstation on the server (it can be either Linux or Windows) you can SSH to the server and then execute KDE, you should be able to have a complete GUI.

For example, from a Windows workstation you can SSH to the Linux server with a program called PUTTY and be sure to specify that you want to use a local X server, you will have to download an Xserver software for Windows. Once connected to the Linux server execute KDE, after "playing" with the GUI cancel the KDE session. Hope this helps a little. 

Regards,

Jose

---

### Post by igknighted on 2008-02-23
[http://www.howtoforge.com/mandriva-directory-server-on-debian-etch](http://www.howtoforge.com/mandriva-directory-server-on-debian-etch)

anyone ever tried this on Ubuntu instead of etch?  If you're looking for a GUI for a server other than a web server, this seems like a great tool.

---

