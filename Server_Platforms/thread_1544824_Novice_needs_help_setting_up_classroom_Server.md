---
title: "Novice needs help setting up classroom Server"
date: 2010-08-03
forum: Server Platforms
---

### Post by frodo_9fin on 2010-08-03
Hiya,

I am trying to set up a classroom server where i will have about 12 pc's networked to it.  There will be about 100 user's and the server needs to be able to store the user's data.  i have another thread that has been going for a few months and someone suggested that i ask around in the server platforms section.  it is difficult for me to articulate my questions being a novice so i will place a link to the thread where i have already asked many questions.  i am looking for a mentor of sorts who might be able to help me with my day to day questions.

Here is the link to my thread. It will give you a good idea of what i am trying to do with the limited knowledge that I have.

[http://ubuntuforums.org/showthread.php?t=1432049](http://ubuntuforums.org/showthread.php?t=1432049)

I thank you for your time and your effort.  I look forward to hearing from you.

frodo

---

### Post by drdos2006 on 2010-08-03
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by mcarrara on 2010-08-03
OK I glanced at your original post, but I admit 13 pages is beyond my attention span.  Where do you stand now?  

Some intial thoughts, Five issues I can see:
1. Server
2. Clients
3. Applications
4. Connectivity
5. Politics

Let's start with politics, does your district have a tech coordinator?  What do they think about your plans?  How about building principal and superintendent?  Are you ready to fight any political battles?  The main reason we are not using Linux on the desktops in my district is politics, I could never get teacher buy in.  Will your use of Linux desktops cause conflicts with other departments?  Can you live or deal with those?

Connectivity, is your network going to be connected to a district network?  The Internet?  Anything else?  Can you inter-operate with other district resources?

What applications do you NEED and what functionality do you NEED.  For example I need to edit video, I have not found a Linux video editor that really does what I need.  As a physics teacher do you need any specialized software that only runs on Windows, how about the CD that came with your textbook?  If you are sure, really sure that you can meet all your needs with only Linux software, great, if not Windows may be needed.

Once those questions have been answered the rest is easy.  To me running Ubuntu as a server is a no-brainer.  Samba can provide file and print services and anything can connect.  I saw that thin clients came up in your discussion, I am a fan of thin clients but it would seem to be a waste to take brand new laptops and turn them into thin clients.  Laptops are portable, students can take them with when they are collecting data anywhere.  However a thin client MUST be connected to the server to work.

Lots to think about isn't it?

Mark

---

### Post by frodo_9fin on 2010-08-03
@Mark - Thanks for taking the time to help me out. I really appreciate it and many of my students will benefit as well.  

I will go in reverse order, that is the easier way for me to answer those questions.  

Politics:  The politics are cool at my school.  I am in an interesting position where I am in a charter school that is within the larger boston public school system.  We have a charter which allows us to change things in house as we see fit which is amazing. If we adhere to state standards we can design our curriculum as we like which allows us to be an alternative school. We get a lot of students that have been kicked out of or been through a other high schools.  It is a rough crowd, but our approach works for many of them. The principal is already on board with my use of ubuntu and most people when I explain it to them are amazed. Great product? Free? Community of support? Free? well written software alternatives that work very well? Free? I am going to set aside a portion of my physics money to donate to the software creators to help keep this going. 

Connectivity:  The server will not be an internet server, it will be a place students can access from with in my classroom via a wireless network. I do, however, need to find a way to pump internet access through the wireless router as well as access to the classroom server.  So the server will be for student data storage, automated installs on the laptops, automated updates on the laptops, control what software options the laptops have on daily basis.

Applications:  all of the crucial software packages that i need work on ubuntu. vernier has created a beta version of the software for their physics equipment and it seems to work well enough.  they have also set up a decent bug report system.

Clients:  I am hoping to run the opposite of thin clients. Are they called fat clients? i wish for each of the laptops to run their own applications.  they are new, fast, and have the hard drive space to run their own apps.  plus, I do not wish to slow the server down.  I am also hoping to have each student have a user space that is only accessible to them and the admin, that can be accessed from any laptop. As admin I need to be able allow the users have access to certain pieces of software and close off access to other pieces of software, so that students are can do only what they are supposed to.

I imagine there will be a lot of script writing for these things to happen. I have a friend who said he would help with script writing, but I will gladly take help from anyone willing to teach me.

As for the server, I am currently trying to install the alternate i86 install available here:  [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

My rational is that it has a GUI that will ease myself into the use of the console. It also has raid support and I would have to install server packages to make it fully functional.  The server packages that I think I need are: Samba, SSH-server, and evsftp-server.  I was thinking that once I have the os installed and working, then I could use sudo apt-get to install these.

I hope I have answered your questions well enough. It is great that you have taken the time to help me. At the moment I am kind of floundering because I cannot get the install to work.

Here are my machine specs: **machine specs:**  Intel Pentium Dual Core E5400 2.7GHz 2M  Processor/4 GB DDR2 PC6400 800MHz/Intel BLKDQ45CB mATX Mother  Board/2x500GB 7.2 Raid 1 Mirror/with MS Windows Foundation Server 2008  64Bit R2/CA ArcServer Single Server-SYX

Thanks again Mark! 

Jake


An after thought while I was reading drdos2006 link: [http://woodel.com]("http://woodel.com/")  Should I set up the server so that it is manipulated through another computer? it would save space, not having to have the extra monitor, keyboard and I imagine not having a desktop environment would greatly increase the speed of the server.

---

### Post by frodo_9fin on 2010-08-03
@[drdos2006]("http://ubuntuforums.org/member.php?u=530536") Thanks for the link.  I am reading it right now.  :)

---

### Post by mcarrara on 2010-08-03
It looks like you have figured out most of what you need.  Much better then most people at your stage.  If you don't need everything up and running for the upcoming semester why not make it a class project?  Real world, 21st century skills project based learning and all the other buzz words.  Really I think it would be cool for students to design and set up a computer system of their own giving them pride of ownership and a deeper understanding of how things work.  I was hoping to run a summer school class where students designed and built computers and a server for our new yearbook staff lab.  Not enough signed up so I got a graduating senior to work with me, but if only I could have gotten kids involved.

Mark

---

### Post by frodo_9fin on 2010-08-03
@mark  I would love to make it a class project, but I need it all up and running for the school year. I am breaking up the curriculum into four classes.  The fifth and final class will be engineering which will be a purely experiential class.  The other four classes will be a mix of both experiential and traditional.  I am trying to use the city busing system as a basis for most of the units.  The students are very familiar to buses so I was hoping that would tap into prior knowledge and experience.

As for the server I am trying to set up, I really need to get past this problem of communication between hardware raid /software raid and ubuntu. I need help getting the install to work.  Then the next step is getting the server up and running, then get the server to do automated installs on all the laptops and setting up user accounts and permissions that i can change on a daily basis. These are all things I need someone with know how to help me with.

What do you think?

---

### Post by drdos2006 on 2010-08-03
You may find less issues with install using 9.10 (Karmic) server rather than Lucid. Just a thought.

Webmin can set up your server remotely and save you space without monitor, keyboard, yes. It is in the HOWTO from kevinthecomputerguy.

regards

---

### Post by frodo_9fin on 2010-08-03
I have read through the how to presented here: [http://woodel.com]("http://woodel.com/").  This setup does not involve using a raid array.  The issue I think I am having is how to get the raid array working properly with hardware support (hardware raid) or software support (software raid).  I think my immediate problem is getting the array to work.  Can anyone offer assistance in that regard?

---

### Post by mikodo on 2010-08-03
Hi, Total casual user here, but have you thought of requesting help formally from Mark Shuttleworth and his Ubuntu staff? I remember someone suggesting earlier in your thread, that possibly Canonical might be able to gain a Tax Credit by doing so..Even if not, they may have some ideas on where/whom you may be able to get some quick assistance from.

Seems to me that you need to get a person/team on board fast, that can walk you through quickly, for now. Maybe even a college professor may know of some present students that would/could be enticed to work with you as a project, for credit in summer/fall semester classes... Just musing here ... Just that time is passing quickly and getting the right person/group, probably could get this done likitysplit...;)

Good Luck,
Mike

---

### Post by frodo_9fin on 2010-08-03
@mikodo That is a great idea.  would you know how to get in touch with Mark Shuttleworth?

On another note I may have just fixed my problem through trial and error. It seems that there is a communication issue between the hardware raid and ubuntu. Based on this and my previous attempts at installing i decided to do one last install.  I turned on the raid hardware in the bios settings and rebooted.  Then I opened the disk manager that appears at the beginning of boot up and set the disks to raid 1 array and exited. Then followed through the ubuntu set up parts.  when it got to detecting disks it asks if you would like raid on or off. i told it off.  then, this is the new variant, upon partitioning the drives I chose a manual install and I only partitioned one hard drive and left the second as free space. the partitions are swap, /, and /home. Ubuntu then wrote changes to disk and installed everything as normal.  

When restarting I noticed that the disk storage manager that pops up at the beginning of startup flashed degraded array. so i went in and it had the message that it would rebuild the array when the operating system was active.  The computer booted up normally and after awhile i shut down and rebooted from a puppy linux cd and used it to look at the status of the drives.  it showed the first drive with the partitions / and /home.  looks good.  then looking at the second drive it had a / and /home with most of the operating system in place.  

After this i rebooted in ubuntu and i am giving it some time.  i am hoping that the hardware raid is actually mirroring the first drive on the second drive.  a second reboot using puppy and looking at the state of the second drive will tell.  i will report back in a little bit and let you know how it went.

---

### Post by frodo_9fin on 2010-08-03
I think the raid issue has been solved.  After rebooting in puppy the second drive was almost completely rebuilt by the hardware raid.  / was completely rebuilt.  All the system files were now in place. It was partially done rebuilding /home.  

Additional evidence from puppy was that the initial boot using puppy showed many errors looking for puppy files saved on disk.  The second boot into puppy (after the raid hardware had time to rebuild the second disk) there were considerably fewer read errors when puppy was searching the disk for puppy files.

I have now rebooted into the ubuntu alternate install and will allow it to finish the rebuild.

I think Ubuntu variants that have raid support really needs to find a better way of allowing hardware raid run while also partitioning your hard drives the way you need them, and giving the user confirmation that it is working.

---

### Post by StolerTech on 2010-08-03
I am going to wish you the best of luck. If you are successful please write a tutorial on how to do this. A lot of ubuntu tutorials seem outdated.

---

### Post by frodo_9fin on 2010-08-03
I think my next hurdle is to choose server packages. I need help choosing the right ones.

My server needs:  to be the home of 100 or so user accounts, users need to be able to access their accounts from any of the 12 laptops, not be an internet server, to be able to do auto installs on 12 laptops as well as auto updates, be able to control software access/privileges for each user (each laptop will be a fat client).

I am not sure what else the server needs to do ah yes network printing. Internet must be available for the server and the users.

So far my list of server packages are samba, ssh-server, and evsftp-server. 

What do you think I need?  Thanks in advance for all your help. :)

I am just pumped that the raid issue is out of the way.  woot woot. It is cause for celebration. :)

---

### Post by mikodo on 2010-08-03
Hi,

 Contact Mark Shuttleworth: Why not ask at the Shuttleworth Foundation:

[http://www.shuttleworthfoundation.org/](http://www.shuttleworthfoundation.org/)

Mike

---

### Post by frodo_9fin on 2010-08-03
Wow, that is fantastic!  Thanks mikodo.

I just confirmed that my machine has a mirrored raid that is working.  I saved a document to the documents folder, restarted in puppy, then found the document was saved in the exact same location on both drives.  That too is fantastic.

So on to the next hurdle, what server packages to install?

---

### Post by k3lt01 on 2010-08-03
> **frodo_9fin said:**
> Wow, that is fantastic!  Thanks mikodo.

I just confirmed that my machine has a mirrored raid that is working.  I saved a document to the documents folder, restarted in puppy, then found the document was saved in the exact same location on both drives.  That too is fantastic.

So on to the next hurdle, what server packages to install?Congratulations Frodo. I had to play with the settings on my RAID setup to, by telling Ubuntu "No" it stops Ubuntu hindering the hardware RAID working.

For your server applications I would first start by installing the LAMP package. Go to Synaptic, when your in Synaptic go to Edit > Mark Packages by Task and that will bring up another screen. Scroll down until you see LAMP Server and mark the tick box (check screenshot). Let it install and that is the first part of your server install. Other packages you may need will be determined by what your software and students require so it may be trial and error till you know exactly how they will use it.

---

### Post by frodo_9fin on 2010-08-03
What does the LAMP server do? I will add if it is needed. My research indicates that I should also install samba so that windows pcs can interact as well as windows network printers. evsftp server so ftp is available. SSH server i am not sure why, a friend recommended it. What do you think?

It was crazy how this situation with my machine worked. i told the bios to do raid 1. told ubuntu not to activate the raid hardware and not to use software raid. then i had to improperly partition the array, boot up into a degraded array so that the raid hardware would rebuild the array. (which took quite a bit of time to rebuild)  this does not seem like the way it should be.

---

### Post by StolerTech on 2010-08-03
Lamp is Linux-Apache-MySQL-PHP. This is if you run a web server.

---

### Post by k3lt01 on 2010-08-04
> **StolerTech said:**
> Lamp is Linux-Apache-MySQL-PHP. This is if you run a web server.LAMP can be used for a webserver but individual aspects such as MySQL are useful for databases. Apache is the actual webserver component and it is also useful if you ever decide to run a unit or exam via a CMS like Moodle. PHP is just a web scripting language that, yet again, is also useful if you expand to incorporate a CMS.

SSH is SecureSHell and that allows a user to log into his/her /home directory on the server. I would say for your project it would be a must have IF you want each student to have their own /home folder on the server.

Samba, yes definitely if you are using Windows and Ubuntu together. I'm not sure if there is any other way around it actually. It's a beggar to setup initially but once you get the hang of it it will make sense.

Ftp, I don't understand why you will want ftp if you are using SSH and Samba. It is just another way of transferring files.

I like Moodle, it can allow you to run quizzes, exams, part or complete units of work. It can allow your students to have a blog/diary of their leaning experience. You can put all your information for your classes on it and use it as a teaching tool for reference materials, individual projects etc. Actually the uses in teaching of something like Moodle are only limited by your imagination.

---

### Post by StolerTech on 2010-08-04
Well if you only used MySQL you would call it a LM :wink: There is no need to install a LAMP bundle just for MySQL. I wouldn't use the package manager because it can be a pain in the butt. I would just run:

```
sudo apt-get install mysql-server
```If I wanted MySQL. No one uses a LAMP bundle just for php or mysql they use it for the whole working package. I have never seen a purely apache server that is in a production environment.

---

### Post by mikodo on 2010-08-04
Hi,

(Open) SSH Link:

[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

From:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)



Mike

---

### Post by k3lt01 on 2010-08-04
> **mikodo said:**
> From:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

MikeYes read this, it will help you understand the reasons for setting up LAMP and any other applications you may want.

---

### Post by k3lt01 on 2010-08-04
> **StolerTech said:**
> Well if you only used MySQL you would call it a LM :wink: There is no need to install a LAMP bundle just for MySQL. I wouldn't use the package manager because it can be a pain in the butt. I would just run:

```
sudo apt-get install mysql-server
```If I wanted MySQL. No one uses a LAMP bundle just for php or mysql they use it for the whole working package. I have never seen a purely apache server that is in a production environment.Read the quote below from a previous post.
The first paragraph was always there explaining my reasoning for a LAMP server in this situation. The second paragraph I added a little later but I think you would have seen it anyway.
> **k3lt01 said:**
> LAMP can be used for a webserver but individual aspects such as MySQL are useful for databases. Apache is the actual webserver component and it is also useful if you ever decide to run a unit or exam via a CMS like Moodle. PHP is just a web scripting language that, yet again, is also useful if you expand to incorporate a CMS.

I like Moodle, it can allow you to run quizzes, exams, part or complete units of work. It can allow your students to have a blog/diary of their leaning experience. You can put all your information for your classes on it and use it as a teaching tool for reference materials, individual projects etc. Actually the uses in teaching of something like Moodle are only limited by your imagination.Installing it as a LAMP server in on go saves plenty of time in setting up. If you choose to setup MySQL, and on another occasion Apache and then on another PHP you have to setup each thing individually. Doing it that way if you are considering running something like Moodle in the future is a complete waste of time and a PITA. Do it once and save yourself the energy later on if you think you want to do something like I suggested in the prior post.

---

### Post by mcarrara on 2010-08-04
Looking at your requirements I don't see why you need LAMP.  The more you install the more you have to maintain and the more potential for conflicts.  Samba is only needed if you interact with Windows.  You have all Linux so it is not needed.  You do need CUPS if you want to print.  Samba would be needed to print from Windows clients, but CUPS can handle Linux clients directly.

Mark

---

### Post by frodo_9fin on 2010-08-04
Thanks for the fantastic information everyone.

@k3lt01

> LAMP can be used for a webserver but individual aspects such as MySQL  are useful for databases. Apache is the actual webserver component and  it is also useful if you ever decide to run a unit or exam via a CMS  like Moodle. PHP is just a web scripting language that, yet again, is  also useful if you expand to incorporate a CMS.

I have been looking at moodle and I would really like to use it so based on k3lt01 I think I will install LAMP.

Open SSH seems to be absolutely necessary so that i can set up all the user accounts.

I will have a couple computers within my small network that will be dual booting with windows and ubuntu.  these are both teacher computers. I have a piece of software that I need to have working that runs on windows.  i will be working on using virtual box to see if it will work there or maybe with wine.  Here are the two programs:  

[http://www.turningtechnologies.com/responsesystemsupport/downloads/softwaredownloadsregistration.cfm?type=26&y=2008](http://www.turningtechnologies.com/responsesystemsupport/downloads/softwaredownloadsregistration.cfm?type=26&y=2008)

[http://www.turningtechnologies.com/responsesystemsupport/downloads/softwaredownloadsregistration.cfm?type=42&y=2008](http://www.turningtechnologies.com/responsesystemsupport/downloads/softwaredownloadsregistration.cfm?type=42&y=2008)

They work with a radio frequency receiver (usb) to collect data from clickers and creates a quick chart of the data. it is for audience response to questions.  very cool.

These windows computers will have to be able to print as well so it seems prudent to install SAMBA.

I had been thinking of ftp because it has been around for so long and it is reliable and it is another means of moving files around.  What do you guys think about ftp?  will it be useful for automated installs and updating clients?

Another question:  open SSH has a client and server applications.  the server app will be installed on the server and the client on the satellite pcs.  Is this true? is there a way to automate the client install when i do all the automated full installs on the satellite pcs?

---

### Post by k3lt01 on 2010-08-04
Because I am a High School teacher I am thinking of this from a teachers perspective as well as a users perspective. 

As I said before ftp is just another way of sharing files. To me if you already have SSH and SAMBA there is no real use for FTP in your situation. That doesn't mean to say it won't be useful.

Actually, what will you use to update the laptops with? I'd suggest [Apt-Cacher-Server]("https://help.ubuntu.com/community/Apt-Cacher-Server"). That way your only downloading on set of updates and the other machines will then pull the updates from your apt-cache in your server. This will save your bandwidth.

---

### Post by frodo_9fin on 2010-08-04
I am also looking at fully automated installs (FAI) from the server as well. I have been looking through the FAI manual and their definitions for a few key terms seem a bit vague. I was wondering if you could help me understand them.  Here is a copy of the text: [http://www.informatik.uni-koeln.de/fai/fai-guide.pdf](http://www.informatik.uni-koeln.de/fai/fai-guide.pdf).

Here is a copy of a part of the text:

> First, some terms used in this manual are described.
install server
The host where the package fai-server is installed. It provides several services and data for all install clients. In the examples of this manual this host is called faiserver.

install client
A host which will be installed using FAI and a configuration provided by the install server. Also called client for short. In this manual, the example hosts are called demohost, nucleus, atom01, atom02,. . .

configuration
The details of how the installation of the clients should be performed. All configuration data is stored in a certain directory structure and is also called configuration space or config space for short. It includes information about:
&#8226; Hard disk layout
&#8226; Local file systems, their types, mount points and mount options
&#8226; Software packages
&#8226; Keyboard layout, time zone, NIS, Xorg configuration, remote file systems, user accounts,printers . . .

nfsroot
A file system located on the install server. It&#8217;s the complete file system for the install clients during the installation process.
All clients share the same nfsroot, which they mount read only.
The definitions install server and install client seem unclear to me.  Do they mean that  the install server would be the server where the install commands, configuration details, and nfsroot are located? Is the install client the program that does the automated installs or are the clients the computers that are going to have materials installed upon?

Thanks

---

### Post by frodo_9fin on 2010-08-04
Upon thinking more, I need to know what the host is as well. It sounds abstract.

---

### Post by k3lt01 on 2010-08-04
> **frodo_9fin said:**
> Upon thinking more, I need to know what the host is as well. It sounds abstract.In server terms the Host is the machine that the information is kept on. A Client is a machine that accesses the Host.

As for FAI, read the Server guide and check out Preseeding. I think it's Appendix B but I'm not sure right now. I have to go and get some work done for a while, sorry I can't be of more help atm.

---

### Post by frodo_9fin on 2010-08-04
It is all good. I will be reading through it tonight. Tomorrow is the big day. I will install the server packages and start setting up for the FAI. Then user accounts and setting up the server to do all the automated installs and such. I am sure each of those will be another giant hurdle for me to research and figure out. I hope to have the server and clients up and running by wed next week.  that is my goal.  i have lots of other stuff to work through before the school year starts up.

---

### Post by frodo_9fin on 2010-08-05
Do I need to install PHPMYADMIN?  will this enable me to have a local hosted web page?

---

### Post by frodo_9fin on 2010-08-05
Alright, so far i have installed: LAMP, samba, ssh, and vsftp.


Is there anything else I need to install?


What sorts of configuration changes do I need to make? or What questions do I need to ask about my server so that I know what sorts of configurations changes need to be made?

How do I set up user accounts?

How do I set up automated installs/updates?  (i am currently reading about the FAI)

What sort of hardware should I get to do a daily backup of user files? Should I create a sort of backup/recovery disk for the system and user accounts?

Networking(software/configuration changes and physically setting up)? How do I Network the satellite pcs, printer, and server and have internet availible?  There are ether net ports availible to pump in internet.  I have a very decent wireless router, the satellite laptops are all wireless including the printer.  The server is not wireless.

---

### Post by k3lt01 on 2010-08-05
Frodo, have you read the server guide? Your questions are actually quite easily answered by reading it. I know your in a bit of a rush now but take a step back, think of the questions you are now asking (especially the user account etc questions) and check the Server Guide. You will find 99% of things there now.

As for an easy way to set up Users. I'm assuming you have regular Ubuntu installed so go to System > Administration > Users and Groups. This will allow you to setup user accounts which will give each new user their own /home folder. They can then SSH into it from the client machines they are on to swap files around.

---

### Post by frodo_9fin on 2010-08-05
Oh yeah, Thanks.  I had forgotten about the server guide. I have lost my self in the FAI guide at present.  I will check it out tonight.

thanks again

---

### Post by frodo_9fin on 2010-08-06
I was wondering how i need to physically set up my network. I am reading through the server and much of it is difficult to understand because of my lack of vocabulary understanding.  

Hardware that I have:  the server with ethernet card card and when i run ifconfig in a terminal it says something about a local loopback. I am not sure what this is yet. a cisco model wrvs4400nv2 wireless router, wireless printer, 12 wireless laptops, and an ethernet connection to the schools lan which grants access to the internet.

i am looking for some descriptions of a physical layout.  i am going to research this, although it is nice to get your input. it helps me sort through all the million ideas that i am finding on the internet.

thanks

---

### Post by frodo_9fin on 2010-08-06
Which would be best for my needs: having the router be the DHCP or the server? It makes some sense to have the server and the printer have static IP addresses and have the satellite pcs have dynamic IP addresses.

I am not sure if that will conflict with the way I want the server to run.

---

### Post by frodo_9fin on 2010-08-06
Which would be best for my needs: having the router be the DHCP or the server? It makes some sense to have the server and the printer have static IP addresses and have the satellite pcs have dynamic IP addresses.

I am not sure if that will conflict with the way I want the server to run.

Is it important for the the server to hand out IP addresses for each user account or can the router give them to the satellite pcs and then the server attaches the satellite pc IP to the user account?

---

### Post by frodo_9fin on 2010-08-06
It seems that if both the server and the router are using the DHCP they might accidentally assign the same IP to a client. I am thinking that I should have the server use the DHCP and turn it off in the router. How will this work though?

How will the clients see the server if they cannot access the router.  It would seem they would need an address from the router so they can see the pathway to the server.

I am a bit confused about how communication happens at different levels of hierarchy in a lan.

---

