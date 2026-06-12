---
title: "Ubuntu server for our company?"
date: 2008-10-24
forum: Server Platforms
---

### Post by tankduck on 2008-10-24
Hi there,
first post so hello everyone!!!

Anyway, we are a small company of 5 architects who are good with computers in terms of cad/3d/photoshop and building/tinkering with machines.....etc but in no way servers. 
Basically at the moment we have 2 nas units which are running on an old version of samba which I believe is not upgradable to v3, an xp machine that shares the plotters/printers. Our email is outsourced to fusemail.com and our website is hosted elsewhere again. 

I have 2 machines that are spare, and I'm considering building a file server using something like freenas, but also am considering building an actual ubuntu server but what would the benefits of a server be for us? Our internet is about 7mb down and I think 1mb up, so I don't know if its suitable to host email or net...etc.

Just some initial pointers would be really appreciated.


Cheers

---

### Post by hyper_ch on 2008-10-24
if you want to host your own email you will require a static ip address. Most mailserver will not accept emails coming from a non-static IP.

---

### Post by tankduck on 2008-10-24
you mean static ips on the network, that isn't a problem as we have set that all up with the router. 

Without sounding too stupid, presumably a server means that you log into the server when you boot up the workstations, as you would at schools, uni's ....etc. Is this something that you do with ubuntu server? 

I think our basic needs are a decent email solution, good file server system, and a vpn solution, again is this something I should look to do with ubuntu instead of forking out for windows server. Obviously exchange server is one of the things we'd love about windows server, but aside from that it seems that ubuntu can do it all.

---

### Post by Bucky Ball on 2008-10-24
I am thinking about setting up a server just for my home LAN over the christmas break so on the brink of learning more. But one advantage I will mention about an Ubuntu server over a Windoze is this: security.

---

### Post by hyper_ch on 2008-10-24
no, I mean a static public IP

---

### Post by tankduck on 2008-10-24
oh right, yeah we have a static public ip, at least i think so, we have an ftp server for which the router forwards the ftp port to the relevant place, thats right isn't it?

---

### Post by hyper_ch on 2008-10-24
well, a static IP will be given to you by your ISP and it's the public IP the router has. If you don't have a static IP I wouldn't even try to run a mailserver.

Besides, mailservers can also be complicated (well, it just takes somewhile to get used to) or you can use some custom made ones like Zimbra or Citadel.

However, IMHO, the most reliable and useful combination would be GMail Business Hosting - if you don't mind that Google snoops into all your emails ( [http://www.google.com/apps/intl/en/business/details.html](http://www.google.com/apps/intl/en/business/details.html) ). Having Google Mail and Calendar together with Remember The Milk and the according plubings for Firefox/Thunderbird is quite nice and very straight forward to setup. However if you have confidential emails then I'd not use Google and setup an own mailserver.

---

### Post by MJN on 2008-10-24
> **hyper_ch said:**
> If you don't have a static IP I wouldn't even try to run a mailserver.It is perfectly acceptable to run a mailserver without a static IP as long as you ensure your outgoing mail is relayed via a 'trusted' 3rd party (e.g. your ISP's SMTP server which will have a static address).
 
Before anyone asks *If you're going to offload outgoing mail to the ISP then whats the point in running your own mailserver?*, well - full control over spam/virus filtering, no limits on the number and size of mailboxes, reduced reliance on 3rd party services, full monitoring capabilities of outgoing mail, mail backup for other domains, etc etc
 
To put it another way there is more to a mailserver than just sending mail...
 
Mathew

---

### Post by hyper_ch on 2008-10-24
> **MJN said:**
> It is perfectly acceptable to run a mailserver without a static IP as long as you ensure your outgoing mail is relayed via a 'trusted' 3rd party (e.g. your ISP's SMTP server which will have a static address).

I guess you have a point there ;)

Yet still, "I" wouldn't even try to run it ;)

---

### Post by MJN on 2008-10-24
I know there are issues with it for the uninitiated and that your statement was made with good intentions... but... I am keen to ensure anyone's innovation isn't stifled by the often-repeated 'rule' that without a static IP all bets are off... ;-)
 
Mathew

---

### Post by tankduck on 2008-10-24
I may well try to run our own mail server then on ubuntu server, the only thing is that the email solutions you mentionned seem to charge quite a bit for the features that I'm after, hate to keep bringing up exchange server but its kinda the benchmark I'm looking for, I'd like to be able to sync calender, mail, contacts...etc with my pocket pc which seems to be a costly addon for zimbra, and a third party plugin for citadel that only does mail(i think). 
Am I right in thinking that small business server 2003 is only 200 quid (googled) or are there loads of nasty hidden prices. If so I'd steer towards a sbs 2003 server and a ubuntu for fileshare but I'd love to get ubuntu to do all of it granted the reputation for stability and the fact that I've poured enough money into ms's pocket for the meantime!!!

---

### Post by tgalati4 on 2008-10-24
You can try setting up some "Web 2.0" services.  For instance you could have an internal web server that hosts 3D videos of your creations.  When visiting a client, you could log in and demo your videos.  This allows a quick way for anyone in the company to dump files without going through the pain of updating the official website.

You could set up a Tracks server for project management, Wordpress for blogging with your customers during design iteration.  Sugar CRM for contact and business management.

Other ideas:

Photo Album Hosting--more detailed pictures of current or completed projects
Text-Messaging/Blackberry Server for the receptionist
In-house internet radio--the plants need something to listen to
Asterisk, VoIP, SIP, Skype, Ekiga, or other video/voice conferencing
Custom applications (internal-web-based) for generating permitting forms or other routine business forms
backup print servers
nightly workstation file backups
Google Sketch-Up repository for client interaction

In Web 2.0 you are creating and hosting the content to share with others (your clients) or internally (your coworkers).  You are limited only by your imagination.

Instead of replacing existing services, think of new services that can be helpful in your business.

---

### Post by tankduck on 2008-10-24
those are all awesome ideas tgalati4, if all this is achievable on ubuntu I think I may just have to throw myself out there and do it!! The file backup part is very important, I mean we all work in network folders anyway, on the nas units, never on the local machine but still, would be nice to make sure everything is backed up. 
Oh and the internet radio thing is something that I have actually thought of before, just have no idea of doing, I worked at a place before that simply had a machine that you could add tracks to the playlist and was a nice touch to the whole atmosphere of the studio!!

I think we can easily cope with not having exchange the more I think about it. The only thing that I'm slightly concerned about is our extensive use of onenote, possibly one of our most useful tools. What I want to achieve is when we are out of the office either at home ...etc but connected to internet, we can still work on onenote notebooks together. Its weird how it works but basically everyone can work on the same notebook at the same time, and all the syncronising happens 'magically'. 
So say we have the notebook drive, mapped as N, is there anyway that the n drive works exactly the same when we are out of the office?

Thanks for all the feedback guys!!! This is really helping my decisions!

---

### Post by MystaMax on 2008-10-24
excellent post tgalati4. Those are some great recommendations. I'm a big fan of web based applications, b/c it allows great flexibility when it comes to the way you work. 

> I think we can easily cope with not having exchange the more I think about it. The only thing that I'm slightly concerned about is our extensive use of onenote, possibly one of our most useful tools. What I want to achieve is when we are out of the office either at home ...etc but connected to internet, we can still work on onenote notebooks together. Its weird how it works but basically everyone can work on the same notebook at the same time, and all the syncronising happens 'magically'.This sounds like a VPN would be your best bet. This way when your working remotely, you can connect the office, and open that file from the NAS unit. I'm not sure you've seen [Zoho]("http://www.youtube.com/watch?v=sfJFBcF_6cE") [Notebook]("http://notebook.zoho.com"), but its web based as well, and is a competitor to OneNote. That may be an option.

One other recommendation I'd like to make is the [ebox platform]("http://ebox-platform.com/"). Its a coporate network management tool, which allows you to manage your network via web interface. You can manage samba shares, firewall, VPN, printers, and a host of other [features]("http://ebox-platform.com/product/features/").

---

### Post by sloggerkhan on 2008-10-24
You can run the services you want off an ubuntu box. The only one that will be that hard to set up is the mail server. You have lots of options for network storage, and they shouldn't be too bad in terms of setup. Same thing with VPN. Mailservers are more complex, though. There are really 2 parts to a mail server, the "sending" part, ie sendmail, postfix, etc, and other part, IMAP/POP3 solution. On ubuntu it's really easy to get basic postfix working, just install the packages, put in proper info. (At least that's worked for me.) In fact, postfix shocked me in terms of how easy it was to get working. However IMAP has been extrememly problematic in my experience. My boss said it took him about 2 weeks to get the mailserver at my job up and running the way he wanted, but I guess he had to configure a lot of anti-spam features that were a bit finnicky. So basically the other tasks should be easy to set up in a day or less, but it sounds as though a propper mail server takes more of a time investment.

---

### Post by estyles on 2008-10-24
> **tankduck said:**
> Am I right in thinking that small business server 2003 is only 200 quid (googled) or are there loads of nasty hidden prices.

I believe you have to pay a per-seat licensing fee for each user that connects to each server.  I do not know what that fee is, but I know there's something.

There's probably also a fee you have to pay if you want it to work during full moons, and a "convenience" fee.

---

### Post by tgalati4 on 2008-10-25
I'm not familiar with onenote, but I use zim across several machines including remotely.  It's a simple note-taking program that allows html-style linking.  Because it updates on the fly, you can have several people working on the same note (assuming it's on a central server) and the changes magically appear on every instance.  It's creepy actually.

Sugar CRM is quite extensive--I'm just getting into it, but I'm sure it has some similar capability.

[http://www.sugarcrm.com/crm/](http://www.sugarcrm.com/crm/)

I use conduit for linking/syncing files across networks and devices.

[http://conduit-project.org/](http://conduit-project.org/)

The important thing is to add services in an incremental fashion.  Don't try to replace existing services right away.  Set up one machine with a few services and leave it running.  Uptime is important--don't forget to use an UPS.  Set up a second machine to experiment with because you will break it/crash it several times trying to get new stuff to work.  Once you have a new service configured the way you want it, and with the reliability required in an office, then migrate that service (and its precious configuration files) to the uptime server.

Expect pushback from coworkers.  It's a mistake thinking that you can simply dump Outlook/Exchange with a collection of open-source equivalents.  Instead, add new services that don't currently exist.  After a while these new services will become vital to your business.

In the meantime, check out the new version of Tracks (1.6):

[http://www.rousette.org.uk/projects/](http://www.rousette.org.uk/projects/)

Good luck!

---

### Post by tankduck on 2008-10-26
Ok, today I have taken the leap to do all this, have installed on 2 boxes, ordered all the hard disk's ...etc to come tuesday and looked into all the awesome applications and tools you have all recommended.

Now for the noob question.....does ubuntu server have to be all command line? Is there a way of running the server with gui? 

Sorry, am used to a point and click adventure when it comes to computing.

---

### Post by tankduck on 2008-10-26
ok, looked into it and basically reinstalled everything again, but when I got to the end of the installation I went back to the choose what to install bit and added ubuntu desktop, is this the right way to get the gui on the server edition?

---

### Post by hyper_ch on 2008-10-26
why do you want a gui on a server anyway?

---

### Post by tankduck on 2008-10-26
I only want a gui so I can set everything up, Ideally I'd like to setup everything in the gui and then close down the gui and leave it running in cli. I'm in the gui now but cannot find any of the server apps anyway so is it not possible to do it this way?

---

### Post by R.Bucky on 2008-10-26
I installed the Server edition and then added ubuntu-desktop via terminal. Although a server is better off with non-gui, I also use my server as my home  box. It has to multi-task! Anyways, I was new to servers as of April '08, but the learning curve is not all that bad.

You have to go into Synaptic Package Manager (or terminal) and check the appropriate boxes for Apache, MySQL, PhpMyAdmin, PHP5, etc... Quite simple through synaptic pkg mgr.

---

### Post by hyper_ch on 2008-10-26
you don't have graphical tools to setup all those different server... a gui is useless in that regard.

---

### Post by R.Bucky on 2008-10-26
sudo apt-get install ubuntu-desktop

---

### Post by tankduck on 2008-10-26
ah ok, so even if the ubuntu desktop is installed as said above, there is no gui for the server apps anyways. Hmm, this is going to be a hell of alot harder to do than I thought.

---

### Post by keithweddell on 2008-10-26
There's quite a lot to learn if you are coming from a point and click environment.  You could try something like ebox [http://ebox-platform.com/]("http://ebox-platform.com/") to get you started and think about going it alone when you've worked through the various systems.  I believe it is in the Ubuntu repos.

Keith

---

### Post by tankduck on 2008-10-26
I might just reinstall again without the ubuntu-desktop in that case. By the sounds of it ebox just allows easy configuration of the server apps on ubuntu, it doesn't actually dumb it down and lose features does it? 

I'd love to learn the cli, but granted I wanted to set the server up to be DNS, samba, alfresco server...etc I honestly don't know where to start.

---

### Post by R.Bucky on 2008-10-26
Webmin and PhpMyAdmin are as GUI as you are going to get in terms of editing, configuring, and backups. Again, you would need to have a GUI system installed instead of command line.

---

### Post by tankduck on 2008-10-26
so is it worth leaving the setup as I have it at the moment ie with ubuntu-desktop installed over ubuntu server and installing the mentionned webmin, phpmyadmin and/or ebox or would it be better performance and generally better in the long run to just have command line and run said applications over the network? Sorry if I'm asking silly questions and stuff I just want to make sure I do this right the first time around so I don't have problems in the future that could have been really easily avoided.

Cheers again everyone for the great help

---

### Post by green91 on 2008-10-26
On most servers ive administered I use webmin and do not install a GUI. I simple use a browser on a networked computer to administer the server. In fact, I dont even have input devices or a monitor on the servers once they are running except for when hardware fails.

---

### Post by sloggerkhan on 2008-10-26
Most servers I work with have at least a minimal gui installed on them for admin purposes. For most people a gui will make it much easier to work with multiple terminals and edit config files, which are the main things you end up doing as a server admin. The way a server works is that you install services that it 'serves.' These services are accessed remotely through protocols such as remote desktop or a web browser or mounted drives. Even if there is a gui configuration front end to most of them, it's not installed by default. Still, that doesn't mean it's hard. It just means you open up its configuration file and change it to match your environment and needs.

Big important piece of advice, though: If you take the approach of setting up each service individually rather than the server as a whole, it will go MUCH easier.

So instead of worrying about the GUI, go ahead and install a minimal gui on your ubuntu server install. Then ask what service to I want running?
Webserver? Then look up and figure out how to install apache.
Groupware? Look up what groupware you want installed. It requires PHP? Then get PHP installed as its own task and worry about the groupware afterwards.

Honestly it's not as difficult as may seem at first. Up until about 2 or 3 months ago I'd never installed apache or used mysql or php. Now I still don't know mysql or php beyond extreme basics, but it's gotten to the point that I've installed about 3 or cms options and 3 forums options and will probably install elgg just to take a look at it because it's seriously pretty easy once you get going.

---

### Post by lykwydchykyn on 2008-10-27
sloggerkahn's advice is good, IMHO.  Install a minimal GUI, whichever one you are comfortable with.  People say it drains resources, but on any  modern piece of equipment that's negligible.  

People talk about CLI administration but that's rather a misnomer.  9/10 of administering a Linux server comes down to editing config files, and if you'd rather do that in gedit or mousepad instead of vim or nano, I can't blame you.  

Most of the howto advice you're going to get will be command-centric just because nobody likes going through the tedium of describing GUI procedures.  But that's a bit nicer in an xterm than at a text mode virtual terminal.

Of course, if you have a Linux desktop machine, you don't  need X11 installed on the server, just forward GUI programs over ssh.  If you only have windows on the desktop or you want to work with the server locally, the GUI is a nice environment to work in.

I wouldn't install the ubuntu-desktop package, though, because it pulls in a lot of stuff you don't need on a server.  You might be better of installing just xorg, xdm, and some more lightweight GUI like xfce or icewm.  less to download when it's time to update.

---

### Post by alienprdkt on 2008-10-27
> **hyper_ch said:**
> if you want to host your own email you will require a static ip address. Most mailserver will not accept emails coming from a non-static IP.

No need for a static IP... i host email and websites with the help of dyndns.org

[http://www.dyndns.com/services/dns/dyndns/howto.html](http://www.dyndns.com/services/dns/dyndns/howto.html)

---

### Post by tankduck on 2008-10-27
ok, i now have ebox up and running, and also read up on samba setup which I feel more confident about now (even though ebox will obviously manage this, I like to know how things work). Main question I have at the moment is the desktop I have installed, ubuntu-desktop, which I installed off the installation cd when I installed ubuntu-server. When I start up the machine, do all the server applications still start up and run in the background? When I installed the server minus the gui, I saw all the server apps load up when the machine was booted and I notice with the gui it goes straight into ubuntu-desktop. The only reason I ask is I'm running ebox and I only have the logs and events modules which made me wonder if the other modules were not shown due to the apps not running.

---

### Post by sloggerkhan on 2008-10-27
Server style apps should all be running from boot. If you have apache installed, it be running at startup, same with other similar types of web services or file shares.

---

### Post by lykwydchykyn on 2008-10-27
ebox is many packages, broken up by different modules.  Check to see ebox-samba is installed.  You may want to search for "ebox" in synaptic and see all the modules available.

---

### Post by tankduck on 2008-10-28
awesome lykwydchykyn!! that sorted it, for some reason when I did it in command line it showed all the ebox packages but maybe this didn't mean that they were installed, eitherway they are downloading and installing as I speak. I really like the package manager way of installing and managing installed applications in linux, very efficient

---

### Post by tankduck on 2008-10-28
ok, I hope I'm not going to annoy people for this thread going on for ages but I have more questions to ask (sorry)

Ok, so the studio for the company is built on the same land as my house, and they share the same internet connection. (This may sound cheap but basically the company pays for a really good business connection and its not used out of company hours so it seemed stupid to have a seperate account for the house.) Anyway, all the ip addresses are managed by the main netgear router which is in the studio, and then there are access points in the house along with another nas drive for media, xbox 360...etc. I just want thoughts on how I could maybe build another ubuntu server in the house to organise ips and make it so I can work from my study in the house but not have people in the office browsing my house network...etc. I'd like to make it so the ubuntu server in the office also organises ips so that i'm not relying on the netgear router and also I can manage it all in one place. The reason I ask is I tried to set up vpn earlier in ebox and got very confused with ips so I'd like to organise it now before I go any further.

I might as well throw another spanner in the works... is it possible for the vpn to allow me onto both the house and office server, for example if i'm in a hotel can i browse work in the office and media at home.

My head hurts:(

edit:

To simplify, with one external IP, how should I organise 2 networks that need to merge for some users and not for others. And is it worth having 2 sets of IP ranges and would vpn work if this was the case?

---

### Post by lykwydchykyn on 2008-10-28
Basically, you want to create a router with your second ubuntu server.  Check out this:

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

This is how it's done on large networks, and it should work great for your situation.  If you want to segment a network the way you're describing, having two IP ranges and a router doing NAT is the cleanest way to go about it.

I'm still working out the ins and outs of VPNs, so I won't try to hack an answer there.

---

### Post by tankduck on 2008-10-28
so the ubuntu servers would be thing thing connecting the 2 areas? Is it worth looking into setting up a domain for each area, ie studio domain and house domain? or is this going to mess things up when it comes to moving between the 2?

Edit: Actually this seems like the simpler idea for the mean time, I'll have one dns server organising the ips and have a range of ips for office pcs, house pcs...etc and then have 2 seperate domains. Now just to work out how to make domains!! This is never-ending, although it is quite fun in a weird way. I'm setting up a the dns in ebox, so I set the new domain as wolfhill (our house), what do I put as a hostname? I've googled it lots but still don't know what I'm doing. 

p.s. bear with me guys, I'll pick this up soon, sorry if I'm being a total noob with all this

---

### Post by ububaba on 2008-11-16
I use Hardy on Kubuntu and have static IP.

I was intending to set up a system(?) so that I can let a handful of friends access
my computer once in a while when the size of the file is too big for attaching.
It is obvious that the computer has to be on, round-the-clock, due to difference
in timezones and availability of good connections. 

Which FTP utility would be proper that is secure enough even if it will have 
non-public usage and the number of users is going to be very limited? 

I have follwed this thread but could not reach to any particular conclusion.
Thanks for suggestions.

---

### Post by ububaba on 2008-11-16
I use Hardy on Kubuntu and have static IP.

I was intending to set up a system(?) so that I can let a handful of friends access
my computer once in a while when the size of the file is too big for attaching.
It is obvious that the computer has to be on, round-the-clock, due to difference
in timezones and availability of good connections. 

Which FTP utility would be proper that is secure enough even if it will have 
non-public usage and the number of users is going to be very limited? 

I have followed this thread but could not reach to any particular conclusion.
Thanks for suggestions.

---

### Post by hyper_ch on 2008-11-16
I'd not use FTP... I'd rather use SFTP and mysecureshell.

---

### Post by ububaba on 2008-11-16
> **hyper_ch said:**
> I'd not use FTP... I'd rather use SFTP and mysecureshell.
Let me see if I can manage it without much ado. I am the only one 
using Linux others are too scared to abandon their old OS. Hope,
it will not be problematic.  Thanks for the prompt reply.

---

### Post by lykwydchykyn on 2008-11-16
winscp should work fine for them.  It's free and easy to use.  On your end just install openssh-server and create local users.

---

### Post by djamu on 2008-11-17
winscp is good [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)   and with Xming [http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming) you can forward an X session to a windows box...  all over ssh > just install that & you're set

---

