---
title: "Help with Home Server"
date: 2010-09-01
forum: Server Platforms
---

### Post by blsmit on 2010-09-01
Hello
I'm moving into a condo soon and want to setup a new home server.
I want the server to do the following: 
Backup, web, FTP and print.  Also, be secure and sleep when not in use.
The computers I need backed up are: Windows 7 Desktop, Windows Vista Laptop and Mac OS X 10.6 Laptop (Time Machine).
The printer is a Espon Artisan 50. (Will this even work?)
The server is a MSI Wind Nettop 100 with a 320GB Hdd+ 180GB USB External. 2GB DDR2 533.
The network is Comcast Triple Play+Comcasts Cable Modem+Linksys WRT54G (V7 I think).-Hardwired to Server.  -Wireless to Everything else.

I would like Time Machine to backup to the External, and the Windows Machines to the HDD.  I hopefully will be purchasing another Internal Hdd (500GB+) for additional space.

Now for the Questions. What is the most effective way to set this system up? 
I have never successfully set up a Print Server with 10.04?
Will I need "drivers" for the Printer?
Should I use Samba for the backups?
Is there a howto for Time Machine to Ubuntu Server?
Will I be able to access the other computers through the server when outside the network?
What is the most effective way to secure the network and Server from potential hackers?
Is there a particular software that would work for the power management of the server?

Thanks in advance for the responses.
blsmit

---

### Post by arrrghhh on 2010-09-01
I'll try to answer all of your questions, but I don't have expertise in all of these areas...

> **blsmit said:**
> What is the most effective way to set this system up?

Not sure how much direction you want here, but Ubuntu Server 64-bit would be a good place to start.

> **blsmit said:**
> I have never successfully set up a Print Server with 10.04?  Will I need "drivers" for the Printer?

I did a quick google search on your printer, and it looks like it should work just fine.  See [this](http://linuxhcl.org/browse/product?id=7503) link for reference. I'd use CUPS with samba to share the printer.

> **blsmit said:**
> Should I use Samba for the backups?

Probably easiest since all your workstations support samba.  Have you seen/used bacula or anything like that?

> **blsmit said:**
> Is there a howto for Time Machine to Ubuntu Server?

I don't use any Mac products, but [this](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/) guide may help.

> **blsmit said:**
> Will I be able to access the other computers through the server when outside the network?

So you want to be able to access these machines in what way?  Just file transfers, or a remote desktop setup?  You should be able to assuming the other machines are on, and your server is on.  File transfers should be a breeze, other things may require more work.

> **blsmit said:**
> What is the most effective way to secure the network and Server from potential hackers?

Ubuntu doesn't have any listening ports by default, but I'm assuming you're wanting to open some up to the internet so you can access the box remotely.  There's several different security things you can do - one would be run SSH on a non-standard port (something above 1024).  Also, only open ports to the internet on your router/server that you absolutely need.  Stuff on your LAN usually isn't such a big deal, but it all depends on how secure you want the system.  Ideally, you'd only have ssh running and you could tunnel any other applications over it.  UFW can help you setup the firewall within Ubuntu, and your router manufacturer can help you with port forwarding (or just go to portforward.com)

> **blsmit said:**
> Is there a particular software that would work for the power management of the server?

I'm assuming you mean to put the server to sleep...?  [Here's](http://ubuntuforums.org/showthread.php?t=482759) some info on having the hdd's spin down...

Plus this is the official Ubuntu documentation on [PowerManagement](https://wiki.ubuntu.com/PowerManagement)

Hope that helps, please ask more questions if you're confused.

---

### Post by blsmit on 2010-09-02
Thank you for the quick response!!

Thank you for confirming the 64bit download. But is there a howto somewhere on setting up a server for a dynamic ip address?  I looked but can't find.

I've only used CUPS, never Samba.  Will this work with my Mac?

Do I have to run software that goes through Samba to automatically backup the computers?  It would be Ideal if the server searched for the computer at a selected time, if its on, it would backup, if it wasn't on it would go to the next computer. Also what about space for these backups?  I don't want a bunch of backups of the same stuff.

Thanks for the Link to the time machine how to. Will follow and report back with/out issues.


> So you want to be able to access these machines in what way?  Just file transfers, or a remote desktop setup?
Just File Transfer.  It would be nice to be able to remote into a machine, but not necessary.  Basically, I would like to be able to go the the server and pull files off it from any computer.  If I have something like a video file, I would like to put it on the server and download it from any other computer.

  >   Ideally, you'd only have ssh running and you could tunnel any other applications over it. 
 I don't understand this.  I know that ssh is 22 or 23, and web is 80 or 8080, but how can I send my web over the ssh port?  Is there a howto somewhere?

Thanks for the power management link!  Other than HDD spin downs, is there anything else I can do.  Maybe lessen the cpu usage when necessary, set the BIOS to turn on and off at a particular time, or turn off programs in the background?

Once again, thanks in advance for answering my questions.
blsmit

---

### Post by arrrghhh on 2010-09-02
Well, I'm by no means an expert on this.  I have everything on my server, and I don't worry about accessing the clients.  I'm also not aware of any backup software that does what you describe... But you may want to look into [Amahi](http://www.amahi.org/) if backing up all those clients is really that important to you.

I also have no clue how Samba works with Mac, I would assume it would work tho.  I only have Win & Lin clients.

Telnet is port 23 by default, and ssh 22 - but you can set ssh to use ANY port you want - and if you pick some random port above 1024, it'll be more secure - if port 22 is closed most just move on.  This doesn't mean your server will be "unhackable" - that's not possible, just makes it harder.  Which is the name of the game when it comes to any security.

If you want a webserver, I wouldn't tunnel it over ssh... but I guess you could.  I was more talking about accessing the other machines remotely - you could ssh to the box and then tunnel the RDP connection thru it... But I'm used to tunneling an RDP connection right on the server, I'm not sure how it would work to the other workstations - it would probably work tho.

There's several power management things you could do - just depends on how hardcore you want to get.  A lot of BIOS' will let you shutdown & startup the computer at specified times.  If not, you could set cron jobs to shut the server down and a magic WoL (wakeonlan) packet to wake the server up at a specific time.  You could also use cron to kill jobs at certain times of day, etc.

---

### Post by blsmit on 2010-09-10
Well this isn't going well at all.  
I managed to install the SSH and web server, but nothing else.
I tried the print server but its just not working with my mac, haven't tried it with my pc yet, but I doubt that will work.

I also tried the timemachine backup, but thats not working either.

What I've decided would work better is if, I created folders for each computer, and used this as a backup folder for each system. This way the system knows when to backup, the server doesn't have to worry about it.  Also I will be using windows standard backup software untill otherwise informed.

Also is there a good FTP program that will work with filezilla?

Also, the server steals all the internet from my other machines, is there a way to cut this down?

thanks once again

---

### Post by arrrghhh on 2010-09-10
> **blsmit said:**
> I tried the print server but its just not working with my mac, haven't tried it with my pc yet, but I doubt that will work.

Need more info to help you here bud...

> **blsmit said:**
> I also tried the timemachine backup, but thats not working either.

What I've decided would work better is if, I created folders for each computer, and used this as a backup folder for each system. This way the system knows when to backup, the server doesn't have to worry about it.  Also I will be using windows standard backup software untill otherwise informed.

Well, I'm not sure... I don't really backup my workstations, I just save anything important in several locations & a few places in the cloud... anything is loseable so-to-speak.

> **blsmit said:**
> Also is there a good FTP program that will work with filezilla?

I use vsftp.  Proftp is the other one that comes to mind.  Any ftp server software should work with filezilla tho, it's a standard protocol.

> **blsmit said:**
> Also, the server steals all the internet from my other machines, is there a way to cut this down?

Steals internet?  As in your server hogs the bandwidth in the pipe...?  What is hogging it?  Torrent downloads...?

---

