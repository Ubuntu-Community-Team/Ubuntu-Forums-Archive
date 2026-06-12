---
title: "What to install?? and how to configure?"
date: 2008-05-09
forum: Server Platforms
---

### Post by rgotten on 2008-05-09
In the past i have place the following question:

"[I]All of you have being excellent on your comments and help, and after few weeks of thinking about this project I would like to summarize my ideas and get a consensus from all of your ideas so I can start it, let me say that I may ask some questions that might be out of this forum spectrum, but your help an orientation is very highly appreciated. As I mention at the beginning, I am a doctor and so far I have paper chart for my patients, and I am planning to do this project in about a year time and if it works after multiple testing, and being safe proof then I might move all my charts to this approved and safe project. I am going to express my project and at the same time ask question and would appreciate answer to them so I can make a start of this. 

My office has 3 computer + my laptop that run on windows xp professional, there are network thru a router (3 wired and my laptop wireless). My plan is as follow: I use word for windows with different templates to create the history and follow up evaluation of my patient. I use zoombrowser from cannon to save the images in a organize way (jpeg format). As you can see this is very primitive and this information is basically saved on my laptop and regularly safe into an external hard drive with Ghost. I would like to create a simple database where my front desk girl will place the name of the patient and chart number; this will have subfolder called for example: Medical record (where I will dictate on the word document template), Billing (where my secretary will scan and safe on pdf format payment from the insurance company, patient, etc), Photos (where I will safe the jpeg files), and other subfolder. (Help also on creating this database will be appreciated).

i.e John Smith 1111 ….Medical Record
Billing
Photos
Laboratories
Etc..

It is my believe after reviewing this forum and all your greatly appreciated comments that this is the step to follow:

a) Build a computer: probably a duo core or sempro with 2 gb of ram, 500 wt of power, on raid 1 with 2 (500 gb) drives build on a chip case

b) From this forum I heard about using xubuntu, kubuntu, etc, or even ubuntu desktop, and then add server software of my choice (Apache, MySQL, Samba server, etc) but also some of you feel very confident that I should use ubuntu server edition with LAMP that was recomended by some of you. So I guess I have to install this (unless somebody has any other idea), and play with it, (I hope you guys will be there to help me on this.

c) In my impression this server will be use for the following purpose (please correct me if I am wrong): all this files world, jpeg, pdf, etc) from any of my 4 windows xp computer will be save and also be access from these server. At the same time, being a raid 1 computer if one of the 500 gb hard drive fails, the other will start working as a mirror, also will have an external hard drive connected to one of the window xp computers from where a copy can be done from the server in a incremental way to have all the data of the server on a windows format external hard rive as a backup, and also be able to do a remote connection to the server on a weekly basis from my home windows computer and also do a remote backup in a incremental way. After I play with this and can safe some of the files from all this computer into the server, then I can safe bigger folders and see how this works to be access from the computers and also remotely access, and if after playing and this works, then work on creating the database…

d) If anybody will guide me on how to build this database to be use on windows environment computer and safe the information on the ubuntu server and also be able to access this remotely from any computer I guess as a web page..Your help on this may be very highly appreciated.

One more time, I know I am asking many things and some of them may be out of the scope from Ubuntu forum, but on the same token, you guide has being excellent, as well as your help and instruction and your orientation will be appreciated, I will follow steps and instructions of the most expert people…and in advance…..Thanks

rgotten[/I]"

**Well here is were i am today**: I have build my computer and install ubuntu server 8.04, it is raid 1 (100mb) for /boot, raid 1 (2gb) for swap, Raid 5 (10gb) for / (system) and raid 5 (980 gb) for /home. It has being tested, hard drive zero and rebuild and works beatifully.

In teh process of installing ubuntu i checkmark the option for LAMP and for SAMBA, since it was recomended to me in this forum. 

Now that I have the following question, With ubuntu 8.04, is LAMP and SAMBA the way to go, or should i reinstall and select something different.

If i should stay with what i have, how do i configure it from the serve edition.

Also for remote access, should i use ssh or i have read some people talking about ebox that is on this version and was not on teh previous one. Your help will be appreicated..


Thanks to everybody how is helping me understand this

rgotten

---

### Post by cdtech on 2008-05-10
You are very much on the right path. If your office is to use only Windows desktops then the Ubuntu file server is the way to go with Samba. During the server install it also installed the &#8220;mysql&#8221; database, this can be set up in any manor you prefer, you just use a program to query the information from the database. Maybe some colleague in your line could offer such an idea for the program. All of your files and pictures would be saved on the server with set permissions.

I use ssh for remote personally, of course I'm still using Ubuntu 6.06.2.

---

### Post by songshu on 2008-05-10
some tought, some question...


reading your story i guess you were looking for  place to store your files and folders, basically in a manual way like rightclick-make folder and template-save-as...

for this, a file server only, samba is what you need.

the LAMP, Linux Apache Mysql Php, could be usefull if you wanted to create a webbased front-end (program) or something refered to as and store your data in a "relational" database.
it would basically work like something that looks like an online-store or when you book flight tickets on line etc....
this would be an exmple
[http://abacus.sql-ledger.com/sql-ledger/login.pl](http://abacus.sql-ledger.com/sql-ledger/login.pl)

the LAMP installation would give you everything you need to
A build the interface with the menu's, search button's etc... yourself
B have this done by a programmer
C install a ready made one like the example, if you could find something that was already suited to your needs.


as far as i inderstood your post, 
samba yes
lamp no

if you would like to remove the LAMP part you could simply do

```
apt-get remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
```


ssh is the best way to login to your server from another computer for command line tasks.


ebox [http://ebox-platform.com/screenshots/](http://ebox-platform.com/screenshots/) will certainly give you the option for your file sharing (and other likely usefull things) with nice understandable buttons.

---

### Post by rgotten on 2008-05-10
Thanks for you reply, but i got more confuse: your first part is rigth, i want to do the following: Secretary on front desk creates a file call 
John Smith 900001 then after i see patietn I access this patient and create a folder in word format and save on his folder, then my assistant takes pictures and save on the same John Smith 0001. All my computers are conecting to the server run windows. Then i am at a diferent location or diferent hospitsal and would like to check a patietn chart, the i would like to acces the server remotly, also would like to be able to do backups of the server remotly, this last part eithe on a windows format or in a linux format.

I say you confuse me since you say yes at the beguining for LAMP, and then say NO. 

SSH amd ebox, are to be use from inside the network or outside (like other location). Any preference on any of the two

Thanks

rgotten

---

### Post by songshu on 2008-05-11
its my pleasure to confuse you ;)

yes, no LAMP, unless you want the thing i described to make it like a webbased front-end (program)

for the file sharing between you and the lovely lady in the white dress you would need to install samba [https://help.ubuntu.com/8.04/serverguide/C/windows-networking.html](https://help.ubuntu.com/8.04/serverguide/C/windows-networking.html)

this is a way to do so, but this would also be an option included in the ebox package
[https://help.ubuntu.com/8.04/serverguide/C/ebox.html](https://help.ubuntu.com/8.04/serverguide/C/ebox.html)

if you would want to access those files and folders from a distant location with for example your laptop, you would have to set up somethink like OpenVPN, a Virtual Private Network..

the administration, via ssh or ebox can be done via your local network or via the internet. 
but i would suggest to get a working set up the way you want
and get realy familiar with the SECURITY concept and risk when having something available via the internet... i write security here in capitals and i do that for a reason, i had my number of computer patients and have also been one myself in the past, especially if you have to worry about confidentiality.... i probably don't have to explain.

it can be done safely, but first make really sure it is.
you could always ask someone over here to do a security scan on your network from the outside once you are good to go.

backups can be done in a huge number of ways, its my experience that its best to have it automatically at regular intervals, since i can easily forget and live happens.

i personally use rsnapshot and have it run every hour, that keeps backups of the previous 8 hours, the previous 7 days and the last 6 months.

---

### Post by windependence on 2008-05-11
I have heard there is a really good widely used open source medical billing program out there. Let me ask my friend who is a doc what is is. In the meantime you could go to freshmeat.net and search for "medical billing" in software. I saw one out there that even does HIPPA compliance.

-Tim

---

### Post by rgotten on 2008-05-11
Thanks for so much trying to confuse me, and lets se if i get it: 

> **songshu said:**
> its my pleasure to confuse you ;)

yes, no LAMP, unless you want the thing i described to make it like a webbased front-end (program)

for the file sharing between you and the lovely lady in the white dress you would need to install samba [https://help.ubuntu.com/8.04/serverguide/C/windows-networking.html](https://help.ubuntu.com/8.04/serverguide/C/windows-networking.html)

this is a way to do so, but this would also be an option included in the ebox package
[https://help.ubuntu.com/8.04/serverguide/C/ebox.html](https://help.ubuntu.com/8.04/serverguide/C/ebox.html)

So, i already have installed SAMBA, and if i install ebox, do i have to reinstall it?? If yes, how do i unistall it before i install ebox, or should i just install ebox, even thougth samba is already install? If i do the database on somethign like php, then i am assuming from what you are saying that i will need LAMP, will this still be secure?

> **songshu said:**
> if you would want to access those files and folders from a distant location with for example your laptop, you would have to set up somethink like OpenVPN, a Virtual Private Network..


> **songshu said:**
> Will something like LogMeIn Hamachi, work and have security?
the administration, via ssh or ebox can be done via your local network or via the internet. 
but i would suggest to get a working set up the way you want
and get realy familiar with the SECURITY concept and risk when having something available via the internet... i write security here in capitals and i do that for a reason, i had my number of computer patients and have also been one myself in the past, especially if you have to worry about confidentiality.... i probably don't have to explain.

it can be done safely, but first make really sure it is.
you could always ask someone over here to do a security scan on your network from the outside once you are good to go.

Ok when i believe is secure i will let you know to scan from teh outside


rgotten

---

### Post by songshu on 2008-05-11
it migh even be easier to install with the dedicated ebox installer [http://ebox-platform.com/download/](http://ebox-platform.com/download/)

there is even a live cd so you can see a preview of things and get a general idea

---

