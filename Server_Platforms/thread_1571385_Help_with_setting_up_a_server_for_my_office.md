---
title: "Help with setting up a server for my office"
date: 2010-09-09
forum: Server Platforms
---

### Post by ZACH4 on 2010-09-09
I have a small network at my office. I would like to change my server setup, and change the way information is shared throughout the office. I have searched the internet and the forums and have found a lot of info about setting up individual services, but I would like to get a good step by step for setting up the server from start to finish. I know the chances that someone has the exact setup I’m looking for are slim, but I know what I want are pretty basic things. I have no experience with Ubuntu Server edition. All of my computers at home are Ubuntu, so I do know my way around the desktop environment somewhat. I cannot change the computers at work to be linux systems, there are Windows only programs that need to be used (AutoCAD, billing software, etc.). The server is the only computer in the network that is not a Windows system, I have several XP’s, a Vista and a 7.

My goals for the server are as follows:

1.	Store files & folders that are accessible (read/write/delete) by all computers without additional logins required.

2.	Have an address book stored on the server that is searchable and editable by each user and used by email clients on each computer (Outlook & Thunderbird).

3.	Automated backups of selected folders to the NAS, once a week full backup and daily incremental.

4.	Automated backups of selected folders to a FTP server offsite, once a month full backup and weekly incremental.

5.	Use a Web based GUI so no monitor is needed for the server.

6.	Automatic restart is power goes out.

7.	Automatic adjustment of computer clock

8.	A internal company homepage, that is set on each computer as the home screen, with links to storage, calendar, address book, etc.

9.	Not necessary, but a office calendar would be handy, each person have their own color and they can schedule there meetings or deadlines, etc. and see other people stuff so everyone knows what everyone is doing at any specific time.

10.	Maybe a current top projects list, with who is working on it and completion deadline or goal dates for different parts of the project.

11.	Share printers, scanner etc. to all computers – not crucial but would be nice, I may have a problem with finding linux printer drivers (have not looked yet)

12.	Use server as a Firewall, router, etc.

13.	….. If you have ideas for other things that would be useful let me know.

Attached is a jpg that shows my current network layout. I assume I need to add a second NIC to my server and put it between the modem and the switch, is that correct? Any other changes to the network configuration?

_Ubuntu Server Specs_
Pentium III 600 Mhz
256 MB Memory
40 GB System Drive
160 GB Data Drive

Currently the server is running 8.04 LTS full desktop, with the data drive shared with samba. Works good, would just like to add the other features I mentioned. Which makes more sense, switch to 10.04 or stick with 8.04?  I could probable find another 256 MB stick of memory if that makes a difference.

The less time I spend playing around figuring things out, the less downtime my office will have, I would like to do it all in one day if possible. I know I could find how to setup each thing I want, but I know some of things will work together and it will be easier to setup things in the right order. If anyone can help me on this I would really appreciate it.

---

### Post by jbrown96 on 2010-09-09
1) Samba is the best technology. Sounds like you already have it configured.
2) Either you will have to find some software that can do this, or "share" the address book file on Samba. I don't think that will work very well.
3) Easy. Look into scheduling cron jobs. Best way would be ssh+public key auth+rsync.
4) See #3. Just figure out how to sync to offsite, then schedule a cron job.
5) You could look into Nagios, but think about how much stuff you want to monitor. It will probably take far more work to setup/configure Nagios, than to jump on the boxes once a day and check. If you do need web-based monitoring, Nagios is the leader.
6) This is a hardware feature. You will have to check your BIOS, but your hardware sounds too old.
7) Enable ntp.
8) This is really dependent on how you implement your shared folders, calender, etc. 
9) Evolution or Thunderbird+plugins might be able to do this.
10) You could look at deploying Google Wave... It's an opensource project, and you can host your sever completely separate from Google.
11) HP printers are the best for Linux. You might need to move the devices from the Win7 box to Ubuntu, although that probably just makes configuration easier.
12) This is reasonably easy. You will need to configure dhcpd, bind (or dnsmasq), and iptables. I can help with this step separately.
13) I'd look more closely at your storage situation. You should probably have redundant data disks at the very least. You can set up a RAID1 array with MD very easily.

---

### Post by ZACH4 on 2010-09-09
Thanks for the comments, I guess I need to clarify a couple points.

5. I don't want to "monitor" the server, I want it to be headless, meaning anytime I need to do anything with it I point my regular desktop pc to the server IP and login and use the WebGUI, I assume I would use Webmin.

8. I believe I can setup the server as a webserver too, and when I go to the IP of the server it will display a "webpage" on the webpage I would have links to different things, as well as a calendar, and a current job list on it.

9. I have some people in the office using Thunderbird and others using Outlook. I need to have something that works with both of them. I was thinking I might be able to do something with Google calendars?

11. The only printer I'm not sure about is the wide format DesignJet 500.

13. I know a RAID setup would be great, but I figure if I am backing up daily to the NAS and weekly to the offsite source, I should be able to restore stuff pretty well if I have a drive failure. At worst case I lose a day of work. I could always setup a hourly backup to the NAS if I wanted to.


I would like to figure out the best combination of programs and settings and then when I have a plan all figured out I would love to have people help with the items they are most comfortable with. We can collectively write a HowTo for this setup. I don't think I am the only one looking for something like this.

---

### Post by jbrown96 on 2010-09-09
This is quite a bit of work, espcially with the amount of research you will need to do. 

I'd say there are three initial steps to getting this setup.

1) Get Ubuntu Server 10.04 installed. You need to configure your partitioning scheme (this can be important, put some thought into it) and other basic setup.
2) Get your network configured to replace your router and firewall. Setup dhcpd, bind (dnsmasq), and iptables. 
3) Configure Samba. It seems like you have Samba already configured, so any new setup should provide at least as many features as the previous one.

From here, you can start adding all the other things. I'm not sure how feasible some of it is (I don't know webmin for example), but most of that seems optional at first. 

This isn't going to be something you sit down and knock out in a few hours, so don't try to do it all at once.

---

### Post by drdos2006 on 2010-09-09
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood



and this would be useful to you...
Server software on one machine, client software on the other.
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

regards

---

### Post by ZACH4 on 2010-09-09
> **jbrown96 said:**
> This is quite a bit of work, espcially with the amount of research you will need to do. 

I'd say there are three initial steps to getting this setup.

1) Get Ubuntu Server 10.04 installed. You need to configure your partitioning scheme (this can be important, put some thought into it) and other basic setup.
2) Get your network configured to replace your router and firewall. Setup dhcpd, bind (dnsmasq), and iptables. 
3) Configure Samba. It seems like you have Samba already configured, so any new setup should provide at least as many features as the previous one.

From here, you can start adding all the other things. I'm not sure how feasible some of it is (I don't know webmin for example), but most of that seems optional at first. 

This isn't going to be something you sit down and knock out in a few hours, so don't try to do it all at once.


1) How will 10.04 perform on my hardware?
2) Do I need a second NIC? I assume yes.
3) Yes I did set it up before, but that was on a desktop version, not server

I know it won't be a quick process, but I want to get as much information together and have a plan all outlined out before I begin, that way the actual process will be shorter, but the research time will be longer. I don't planning on starting the physical part for several weeks.


> **drdos2006 said:**
> Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

and this would be useful to you...
Server software on one machine, client software on the other.
[QUOTE]
[http://ubuntuforums.org/showthread.p...ight=howto+nfs](http://ubuntuforums.org/showthread.p...ight=howto+nfs)
HOWTO: NFS Server/Client

regards[/QUOTE]

The first link looks great, I will definitely read through it. It is based on using Debian, it looks like it will be pretty easy to adapt to Ubuntu though.

The second link is about sharing files between linux machines, the linux box I will have is the server so I need Samba not NFS. Thanks for the info though, I may still set it up so if I bring my laptop in to the office I can easily share files.

---

### Post by jbrown96 on 2010-09-09
Ubuntu Server should perform fine. Debian or CentOS are also acceptable alternatives, but they won't be that much different. 

You will need a second NIC if you want your Linux server to be your gateway.

If you have some more current hardware, I would setup a KVM guest. You can completely setup your "server," then just copy all the files once it's working properly. 

All of your setup is going to come down to a list of packages that need to be installed, and then maybe a dozen configuration files, so it's not tremendously important to do the work on the actual server. 

I looked at part of the guide that drdos2006 posted, and it's certainly in-depth, but I'd be careful about how many of the settings you copy. For example, the disk partitioning steps worry me.

---

### Post by ZACH4 on 2010-09-09
Yeah, I was wondering if I could use a VM do all the setup then create a install DVD or something to use on the actual machine. I'll look into that.

My initial plans for partitioning would be to let Ubuntu do a guided using the full 40GB disk.

---

### Post by jbrown96 on 2010-09-09
I would highly recommend going with Xen or KVM. Stay away from Virtualbox since it's going to setup networking wrong. 

For partitioning, I would stay away from the guided plan. Swap recommendations are usually completely out of line, and you can really hamstring yourself if you want to expand later. Going with LVM or MD is a much better solution.

---

### Post by DanYoSon on 2010-09-09
If you are willing to move your email accounts you could look into google apps this gives you all kinds of cool stuff. i believe they have a tool for importing all the old emails etc onto the servers.
 
this might cut down on the amount of things you have to implement and can be accessed from anywhere.

---

### Post by jbrown96 on 2010-09-10
> **DanYoSon said:**
> If you are willing to move your email accounts you could look into google apps this gives you all kinds of cool stuff. i believe they have a tool for importing all the old emails etc onto the servers.
 
this might cut down on the amount of things you have to implement and can be accessed from anywhere.

I was going to suggest to this. That's probably the best email+calendar solution out there. There might even be a way to share contacts. 
Then again, the Ubuntu route is doable, especially if funds are tight. Google might have a deal for small businesses, but I think that it's $50/user/year.

---

### Post by DanYoSon on 2010-09-10
> **jbrown96 said:**
> I was going to suggest to this. That's probably the best email+calendar solution out there. There might even be a way to share contacts. 
Then again, the Ubuntu route is doable, especially if funds are tight. Google might have a deal for small businesses, but I think that it's $50/user/year.

The Premier edition is $50/user/year but he standard edition is free and this works great.

[ Google apps standard edition]("http://www.google.com/apps/intl/en/group/index.html")

---

### Post by ZACH4 on 2010-09-10
Yeah I was figuring on using Google calendars embedded on a office webpage or something, but I want to stick with the email we have, just have a common address book or contact list that is easy to search, add new contacts, etc.

I have been going through the setup at [http://woodel.com]("http://woodel.com") on a machine at home.

So far I have the system up an running headless. Webmin works great, when I finish with the how-to I will try and play with the common address book idea.

---

### Post by kgatan on 2010-09-12
I agree with the previous jbrown that you should consider RAID on the server.
Its so easy to setup and it doesnt cost much.
Saves you alot of hassle when a drive fails so you can focus on the business instead.

For calanders and projects it sounds like a sharepoint/CMS service is what you need.
An open source alternative to consider is Alfresco, [http://www.alfresco.com/](http://www.alfresco.com/)

Its also possible you can achive all you need with an internal joomla site and some extensions,
[www.joomla.org]("http://www.joomla.org")

Regarding number 4, FTP backup.
Im no linux guru but isnt it easier to use RSYNC and SSH to backup offsite securly? 
If you controll the offsite server of course.

---

### Post by ZACH4 on 2010-09-13
> **kgatan said:**
> I agree with the previous jbrown that you should consider RAID on the server.
Its so easy to setup and it doesnt cost much.
Saves you alot of hassle when a drive fails so you can focus on the business instead.

For calanders and projects it sounds like a sharepoint/CMS service is what you need.
An open source alternative to consider is Alfresco, [http://www.alfresco.com/](http://www.alfresco.com/)

Its also possible you can achive all you need with an internal joomla site and some extensions,
[www.joomla.org]("http://www.joomla.org")

Regarding number 4, FTP backup.
Im no linux guru but isnt it easier to use RSYNC and SSH to backup offsite securly? 
If you controll the offsite server of course.

I just don't feel that raid is necessary, like I said before daily backups to a NAS and weekly backups offsite. If a drive fails, I have two locations to restore from, and I could run a restore at night when no one is working anyway. I have also been thinking about the fact that my main office computer has a 750gb hard drive and is on most of the time, so I could also setup a daily backup to that. I may still setup raid, but it is not a priority.

The projects are not concurrently worked on, so I don't need that ability.

I think that Joomla might be a good choice for a inter-office website with user accounts and shared calendars. I can have my list of top project on the front page, and a common calendar that shows different deadlines and meetings.

I currently do not have control of the offsite server, I have been considering changing it so that it backs up to my home server. As it sits now, I have it encrypt the backup and FTP it to web storage space I have. Security is not absolutely critical with our data, but if RSYNC and SSH would be faster and more secure I will definitely look into it.

---

### Post by jbrown96 on 2010-09-14
> **ZACH4 said:**
> I just don't feel that raid is necessary, like I said before daily backups to a NAS and weekly backups offsite. If a drive fails, I have two locations to restore from, and I could run a restore at night when no one is working anyway. I have also been thinking about the fact that my main office computer has a 750gb hard drive and is on most of the time, so I could also setup a daily backup to that. I may still setup raid, but it is not a priority.

The projects are not concurrently worked on, so I don't need that ability.

I think that Joomla might be a good choice for a inter-office website with user accounts and shared calendars. I can have my list of top project on the front page, and a common calendar that shows different deadlines and meetings.

I currently do not have control of the offsite server, I have been considering changing it so that it backs up to my home server. As it sits now, I have it encrypt the backup and FTP it to web storage space I have. Security is not absolutely critical with our data, but if RSYNC and SSH would be faster and more secure I will definitely look into it.

Restoring from any type of backup is always a pain. You really don't want to do it. Things never go properly, and honestly, I'm very worried that you are not backing up the correct data. 
For less than $50 you can get a RAID1 setup. I don't understand the belief that it's not a worthwhile investment.

---

### Post by koenn on 2010-09-14
> **jbrown96 said:**
> Restoring from any type of _backup_ is always a pain. ... 
For less than $50 you can get a _RAID1_ setup. I don't understand the belief that it's not a worthwhile investment.

Raid is not an alternative to backups. Never was, never will be.

---

### Post by ZACH4 on 2010-09-14
> **jbrown96 said:**
> Restoring from any type of backup is always a pain. You really don't want to do it. Things never go properly, and honestly, I'm very worried that you are not backing up the correct data. 
For less than $50 you can get a RAID1 setup. I don't understand the belief that it's not a worthwhile investment.

Restoring from backup is as simple as copy and paste from the NAS. Why are you worried that I am not backing up the correct data? Yes, I know that all I have to do is buy another hard drive and setup software RAID, but I am not interested in that right now. I am more interested in getting the other stuff setup, my critical data is pretty minimal (<10gb) and most of it does not change and is backed up on DVD.

---

### Post by jbrown96 on 2010-09-14
> **ZACH4 said:**
> Restoring from backup is as simple as copy and paste from the NAS. Why are you worried that I am not backing up the correct data? Yes, I know that all I have to do is buy another hard drive and setup software RAID, but I am not interested in that right now. I am more interested in getting the other stuff setup, my critical data is pretty minimal (<10gb) and most of it does not change and is backed up on DVD.

Are you backing up all your config files? Are you backing up your executables? 
There's a lot more to a system than the documents you share over Samba. How long would it take you to install Ubuntu again, and replicate your setup?
How much does downtime cost? At even the smallest businesses, I can't image than it's less than $200-300/hour. 

I feel like you're getting way ahead of yourself. Some of the things from your original list are simple, but a lot of the stuff is going to take real development time. 
I just get the feeling that you are glossing over the simple stuff and substituting technical decisions for how-to guides. 

What do you have against RAID? The cost is minimal, and it might take an additional five minutes to configure. 

You are probably going to have to overhaul your backup procedure to actually backup system files. However, all that does is allow you to restore. It's still going to take at the very minimum two to three hours to get everything fixed, and that only includes the restore. Don't forget you will have to go buy a new drive.
RAID, in most failure situations, will keep you running until you can swap the drive, which won't require any disruptive maintenance.

---

### Post by ZACH4 on 2010-09-14
I now understand more. I have nothing against RAID, I just thought you were talking about setting up the data drives with RAID, but you actually mean installing the system on a RAID 1 setup, thereby allowing the server to continue running if a drive fails. That I can agree with, and it is a very simple step. With that in mind I might buy three new drives and set up two in RAID 1 with the system installed on them and keep the third for a spare, time will tell. And not that it matters, but my down time costs can be easily minimized, If the computers were down I can easily send people to go do some field work (surveying, etc.) for the day.

I think previously I said that I wouldn't be starting for a few weeks, but I will most likely try to work on this either around Christmas time or during February 2011, those are the time when I have the least amount of work and least number of people in the office. So I have plenty of time to plan.

OK, I think we can move on from the RAID question now. Anyone have ideas on a way to implement common contacts/address book, shareable & editable by Outlook & Thunderbird?

---

### Post by koenn on 2010-09-14
that raid vs backups thing is a false dichotomy.
The real question is : what's your recovery strategy : which problems do you want/need to protect against and how much downtime or you willing to take. When you've answered those, you design countermeasures and recovery procedures. While doing so, it will become clear whether or not RAID is desirable (i.e. whether it fulfills a role in the countermeasures and recovery procedures), what you need to backup and how, and what other measures you need to take (eg ensure you have access to the installers/packages for the correct versions of the software you plan to reinstall as part of the recovery)


In that respect, jbrown96 is right that your recovery procedures may require you have backups of config files, and stuff like that.

Overall, I also think you're out of your depth. Asking step by step instructions for an entire server setup with ~12 services/components, not all of them trivial, with only "knowing your way around a desktop somewhat" for skill set, for a production server, and expecting to pull it of in 1 day, is rather optimistic.

Imagine what you would think if you found a post on a DIY-forum, going something like "I'm going to build a house. Please provide step by step instructions on how to do the brick laying, carpentry, plumbing, electricity and painting. Is there anything specific I need to know about heating ? I have some experience building doll houses with LEGO". 

Then, imagine the post is by the guy you contracted to build your house.
:)

---

### Post by koenn on 2010-09-14
> **ZACH4 said:**
> 
OK, I think we can move on from the RAID question now. Anyone have ideas on a way to implement common contacts/address book, shareable & editable by Outlook & Thunderbird?

Depends.
A common address book is something you'd expect in groupware servers that also handle mail. They'd also do calenders. 
But since you don't mention mail on your feature list, it's not clear what your plans are in that respect.

---

### Post by ZACH4 on 2010-09-14
I agree, it is optimistic. But I have right to have hopes and dreams :p

I also know that it is out of my depth, but that is why I like it, it pushes me to learn and try new things. That is why I am setting up a server at home also, to play with it and learn what works and what doesn't and how to apply it to the server at the office. 

I know that getting everything set and working the way I want will never happen in a day, the day thing really applies to switching from my current server setup to getting the new server up and running with the shared data available. Everything else can come later, I just want to know ahead of time about steps that I should take that will make those other things easier later.

---

### Post by ZACH4 on 2010-09-14
> **koenn said:**
> Depends.
A common address book is something you'd expect in groupware servers that also handle mail. They'd also do calenders. 
But since you don't mention mail on your feature list, it's not clear what your plans are in that respect.

I currently have a website with all office email through the hosting company, they are accessed by either Outlook or Thunderbird with pop and smtp. If I can bring those same email addresses over the my server and have things work the same way to get shared address book, then I am willing to do it.

---

### Post by jbrown96 on 2010-09-14
This looks pretty good for the addressbook [http://www.bynari.net/bynari.php?page=address](http://www.bynari.net/bynari.php?page=address)

Not free but $10/user.

---

### Post by koenn on 2010-09-14
> **jbrown96 said:**
> This looks pretty good for the addressbook [http://www.bynari.net/bynari.php?page=address](http://www.bynari.net/bynari.php?page=address)

Not free but $10/user.

Looks like an LDAP client. I guess you'd also need an LDAP server, then.

---

### Post by koenn on 2010-09-14
I soppuse the options would be

1- go for a mail/groupware/collaboration platform : look up Citadel, Zimbra, Zarafa

2- do something creative with LDAP, eg like so : 
[http://www.brennan.id.au/20-Shared_Address_Book_LDAP.html](http://www.brennan.id.au/20-Shared_Address_Book_LDAP.html)

3- poor man"s solution : collect html mailto: urls on a web server.
This will have to be centrally managed by someone who has server access, unless you can work something out with webdav or run "social network" software on the web server (a customized blog or wiki thingy to allow user input/edits)

come to think of it, a simple wiki (eg dokuwiki) where each page is the business card of a contact, with a clickable mailto url, might actually work quite well.

---

### Post by ZACH4 on 2010-09-15
I like the wiki idea. I have it setup on my home server now and am playing with it. Any idea how to easily migrate my existing contacts into it, or am I going to have to make a page for each contact manually. I currently have my contacts in a spreadsheet, I will setup a template for the contact pages, I just need a way to get the info from the spreadsheet into the wiki. I believe wiki pages are txt files, so I guess I could create a script to pull data from the spreadsheet and create txt from each line. Anyone got a better solution?


Edit: Something else I should have mentioned, I do know HTML, I have written many webpages with it.

---

### Post by koenn on 2010-09-15
if you go for dokuwiki, yes, it's one text file per page. 

And yes, whenever I'm confronted with a problem like that, I'd try to come up with a script that reads the spreadsheat, adds some string manipulation (eg add wiki tags and stuff here and there), and dump it in a text file -- in this case a text file for each contact in the spreadsheet, each file with a relevant name. Shouldn't be too hard. 

You might also need to create some sort of start/index page with links to all other pages; if you create them externally to the wiki software, this might help to force the wiki engine to see and index them. And/or do a wget for each page (also scriptable)


Other wikis often use databases, so there you'd need a script that builds sql statements around values from the spreadsheet, then run the sql script against the database, and cross your fingers. 

fun side project for a lazy sunday afternoon :-)

---

### Post by ZACH4 on 2010-09-27
> **koenn said:**
> 
You might also need to create some sort of start/index page with links to all other pages; if you create them externally to the wiki software, this might help to force the wiki engine to see and index them. And/or do a wget for each page (also scriptable)


I am using DokuWiki.

I wrote the script to extract and create separate txt's for each contact with proper DokuWiki formatting. I have uploaded them to the server and cannot access any of them. I have set file permissions on all files and the folder. When I click on index it shows links to all of them, but the links don't work. It tells me that the page is not created yet.

The DokuWiki forum is down right now, I have asked the question on there, I've tried a couple suggestions to no avail. If you have any ideas I'd appreciate them. I have also tried creating an index page with links to several of the names with no luck. You also mentioned doing a wget for each page? I've looked around but can't find any information on that method, any advice?

---

### Post by koenn on 2010-09-27
tried it myself just now :
create a file with vim, in de wiki folder, 
create the corresponding link in the wiki
works like a charm


things you might have missed :

- files need to be ownd by www-data (or whatever account your web server uses ; compare permissions to a file made "the normal way" - from the wiki

- files are in subdir pages
- files have .txt extension, but links don't.

so, a a link in the wiki [[bigbadtest]] refers to a file  pages/bigbadtest.txt

- there are some other substitution rules that dokuwiki applies (eg replace spaces by _, remove punctuation, ...) when creating file(-names) from links,  so your filenames need to comply with those as well

---

### Post by koenn on 2010-09-27
> **ZACH4 said:**
> You also mentioned doing a wget for each page? I've looked around but can't find any information on that method, any advice?

that's just a fall-back to have your web server serve every page from your wiki, forcing the wiki-engine to do its thing on every artificially added page. turns out it's not really necassary but if will populate the wiki's cache. maybe it also helps in creating indexes for search, not sure about that one 

as you're generating files with a script, you already know all filenames that will be in the wiki. That makes things easy : just let the script output, to different file, wget statements like this :
```

wget http://server/dokuwiki/doku.php?id=filename1
wget http://server/dokuwiki/doku.php?id=filename2
wget http://server/dokuwiki/doku.php?id=filename3
```
... where filename[1,2,3] are the actual filenames for the files you've created (without the .txt extension !)

make the file an executable script, and run it from a machine that can browse the wiki. 
That's all.

---

### Post by ZACH4 on 2010-09-27
Got it working.

Turns out that you can't have capitals in the filename.

---

### Post by koenn on 2010-09-27
figures ...
"all lowercase" is one of those substitutions dokuwiki does when creating filenames ...

---

