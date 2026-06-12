---
title: "Home DIY All in One NAS Web server - setup"
date: 2011-02-10
forum: Server Platforms
---

### Post by Mirmur on 2011-02-10
Hi
  I'm going to make home server with higher functionality than available in shops.
  To do this I was bought hardware;
  Motherboard;               Intel 510MO
  Ram;                            DDR2 800 MHz
  System drive -  16GB pendrive
  Work drive                   500 GB Sata II - 2,5 inch
  Storage                        2 x 2 TB SATAII Samsung F4
  Power source               FSP PPA4000800 Zen 400W Fanless Power Supply (PSU)
  Case                            mini ATX  with up to 10 hdd spaces
   
  I've chose this hardware set in mind to make most energy efficient, noiseless, expandable and still powerful ( in home context ) server.
  I'm going to install operating system at pendrive because I would like to avoid spinning discs if not necessary. This solution is popular in NAS boxes and system build around software such like Freenas or Openfiler.
  A work disk is a small laptop size 500 GB Sata drive. I've chose this drive because is very quiet and using very little electricity. I'm going to use this drive to common tasks such like hosting my own webpage and bittorrent activity and hosting my own websites for learning and experimental purposes. I'm going to spin up this disc to these common tasks and save as much as possible main storage discs. I will not use any raid option. I just schedule backup entire work drive into main storage for example once a two days. As a backup whole server I prefer to make copy important data on distance drives or detachable usb ones. This will help keep my data safe not only against disc failure but also against viruses, fire, thieves and kids. Cost is comparable to Raid 1 setup and security is much higher.
  Main storage;
  I've decided to go with Samsung brand because from my personal experience and many self build computers, these drives are one from best regards of reliability and performance. These are 5400 rpm spinners so they working pretty cool and allow to using fanless case. High density platters assure decent transfer despite fact that they have low rpm. They also use 5 Watt power when working so is important as well. I chose these over WD because they have "load cycle count" problem.
  Processor and Motherboard;
  I selected Intel 510MO because it is fanless design, dual core, hyperthreaded and using around 15 Watt when active. Similar processors are used in top home servers from companies such like Synology, Thecus and cost close to 1000$ and are using proprietary firmware which is much less configurable than common Linux server distros. So going to DIY route is for me obvious. And give me great opportunity to learn something new. 
  Power source;
  Main reason to select this one is that it is fanless. It is expensive when compare to common psu but already is little choice. 
  Case;
  Cheapest as possible standard mini ATX. This case has been heavily customised using tools such like angle grinder, power drill, pliers, saw etc.. and plenty of mesh to allow air flow and aluminium angle bars to make support up to ten storage drives. 
  Now about functionality;
  Beginning from most important
  
[LIST]
[*]NAS storage
[*]DLNA server
[*]FTP, SFTP server
[*]Web server
[*]Home surveillance
[*]Home automation
[*]Remote server management
[/LIST]
  First three function are easily achievable by ready on software such like Freenas or Openfiler, but further need more customisable and powerful platform. So I chose Ubuntu Server because I'm little familiar with desktop edition, but I still recognise myself as a beginner in Linux world. 
  I open this thread not to only ask about hardware and software difficulties, but also this will be for future reference for other peoples whom wish to build something similar. These "magic" boxes such like this one are becoming increasingly popular, and there is great opportunity to popularize Linux and open source software. This area need to be improved because I ask about 20 my friends if they now what it is Linux and only one know it because he study IT in college. 
   
  Let me ask first question;
  How to partitioning this particular server to mentioned above task?
  Most problems I foresee with webserver. Lets imagine im going to host my own hobby website. I suppose to keep files associated with this website on working drive. This drive has 500 GB so I could assign say 100 GB to keep website files and rest to torrent activity. After couple of evenings of googling doesn’t find clear information what means partition with /var, /user, /home …. And what content they hold. Also is important for me if I really need to divide installation in so many partition and where I should place them - on system drive (16GB prior formatting) or work drive where is much more space but disc need to  spinning up.
  Again lets imagine two situations;
  1)
  I will host website with blog and users forum. So web files which determine appearance of web are kept in say work drive. So now no problem. Then forum users want to upload some pictures, short videos or other files. So forum file volume will be increasing and quickly eat work drive space. So I prefer to keep whole forum archive or just uploaded files at main storage which is easily expandable ( there are 4TB drives round the corner). 
  2)
  There is small team of videographers, say 3 persons and they capturing important event. So they using 3 HD camcorders with highest quality settings so for event 3 hours long files from these cams can easily reach 100 GB in size. Then after event they have little time to edit and render a final video reportage. I assume they live in some distance from each other. So after back to home and copying files from camcorders to computers they upload these files to central serwer. Althoug this is possible by ftp protocol for convenience we will use web solution. After uploading these files cameraman's could download files made by other in this small team. So they could working at own part of project say 1/3 length. But when they will be working on own subprojects there is necessary to exchange ideas about technical niggles such like sound and videos settings, colour corrections …, and artistic such like speed of montage (more like action films or more like soaps), special effects, closed captions, transitions and many more. There is solution for that. Every videoediting program (I use Sony Vegas Pro) generate small file about couple MB which these stored instructions about cuts and other video editing activities. So these files could be easily exchanged between these videographers. When these files are downloaded  this can be fired up and is possible to watch others job as long as all source files from camcorders are stored locally. 
  I've used example about video editing because I'm familiar with, but this scheme of using centralised server be use with many team works such like CAD designing, music productions, surveys and many more.
  So where is a point to build own DIY server in context of examples mentioned above?
  Its impossible to find a web hosting company/service who allow to upload, download dozens GBytes of data, keep website and users forum and this everything for **free.**

  Finally after this long introduction I would like to ask about proper configuration this particular server to allow mentioned above functionality. 



regards


Mirmur

---

### Post by elico on 2011-02-10
you can use hostmonster for web hosting but .. it depend on your needs.
anything you need you can get with amount of money.
why should anyone give something for free on the business world?
server consumes power and require care like any other thing in the world as food that you pay for.
you dont have any reason in the world for these kind of need to use 510MO MB cause it wont give you want.
maybe the cpu is taking only 15W but all the other parts will take it up.
i am using interl atom 410d and it's very nice in the over all but!!
if i need small computing or I\O such as HardDrives job it can do the job.
for these sizes and purposes it's not just about "Green 15W" or stuff like that.
you need a good machine that can be expanded and can be worthwhile.

there are cpus without hyper threading that will do better job and more efficient.

any amd cpu that exist on the market is better than intel atom and i mean ANY ONE OF THEM.
you can buy a proper machine with a proper M.B and proper drives in less than 1000$
just to make it clear a list for your consideration:
-sempron cpu 2.7 GH 64BIT will take 45W(on load)
-athlon cpu 65W(on load)
-intel e5500 45W
about 40-50 $
proper MB for them:
some gigabyte MB with 6 sata and VGA OB + GB  lan card.
100$

ram 4-16GB
4GB - 60-70$
good case+PSU also 60-100$
until now it's
70+100+100+50
320$ 
add any HD that you will add to any server\computer and..
you will get the machine for your needs.
by the way you dont need 16GB stick for OS 8GB is more than you need.
also if it's a very static OS you can use a RAM os like a in a live-cd and belive me you will be more than happy.

the only question you will need to ask yourself is:
what do i want this machine to do? and how reliable this machine should be?(speed and redundancy) 
and these answers should point your way.

---

