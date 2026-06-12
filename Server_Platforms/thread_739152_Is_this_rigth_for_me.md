---
title: "Is this rigth for me?"
date: 2008-03-29
forum: Server Platforms
---

### Post by rgotten on 2008-03-29
:)All of you have being excellent on your comments and help, and after few weeks of thinking about this project I would like to summarize my ideas and get a consensus from all of your ideas so I can start it, let me say that I may ask some questions that might be out of this forum spectrum, but your help an orientation is very highly appreciated. As I mention at the beginning, I am a doctor and so far I have paper chart for my patients, and I am planning to do this project in about a year time and if it works after multiple testing, and being safe proof then I might move all my charts to this approved and safe project. I am going to express my project and at the same time ask question and would appreciate answer to them so I can make a start of this. 

My office has 3 computer + my laptop that run on windows xp professional, there are network thru a router (3 wired and my laptop wireless). My plan is as follow: I use word for windows with different templates to create the history and follow up evaluation of my patient. I use zoombrowser from cannon to save the images in a organize way (jpeg format). As you can see this is very primitive and this information is basically saved on my laptop and regularly safe into an external hard drive with Ghost. I would like to create a simple database where my front desk girl will place the name of the patient and chart number; this will have subfolder called for example: Medical record (where I will dictate on the word document template), Billing (where my secretary will scan and safe on pdf format payment from the insurance company, patient, etc), Photos (where I will safe the jpeg files), and other subfolder. (Help also on creating this database will be appreciated).

i.e John Smith 1111 ….Medical Record
Billing
Photos
Laboratories
Etc..

It is my believe after reviewing this forum and all your greatly appreciated comments that this is the step to follow:

a) Build a computer: probably a duo core or sempro with 2 gb of ram, 500 wt of power, on raid 1 with 2 (500 gb) drives build on a chip case

b) From this forum I heard about using xubuntu, kubuntu, etc, or even ubuntu desktop, and then add server software of my choice (Apache, MySQL, Samba server, etc) but also some of you feel very confident that I should use ubuntu server edition with LAMP. So I guess I have to install this (unless somebody has any other idea), and play with it, (I hope you guys will be there to help me on this.

c) In my impression this server will be use for the following purpose (please correct me if I am wrong): all this files world, jpeg, pdf, etc) from any of my 4 windows xp computer will be save and also be access from these server. At the same time, being a raid 1 computer if one of the 500 gb hard drive fails, the other will start working as a mirror, also will have an external hard drive connected to one of the window xp computers from where a copy can be done from the server in a incremental way to have all the data of the server on a windows format external hard rive as a backup, and also be able to do a remote connection to the server on a weekly basis from my home windows computer and also do a remote backup in a incremental way. After I play with this and can safe some of the files from all this computer into the server, then I can safe bigger folders and see how this works to be access from the computers and also remotely access, and if after playing and this works, then work on creating the database…

d) If anybody will guide me on how to build this database to be use on windows environment computer and safe the information on the ubuntu server and also be able to access this remotely from any computer I guess as a web page..Your help on this may be very highly appreciated.

One more time, I know I am asking many things and some of them may be out of the scope from Ubuntu forum, but on the same token, you guide has being excellent, as well as your help and instruction and your orientation will be appreciated, I will follow steps and instructions of the most expert people…and in advance…..Thanks

rgotten

---

### Post by bluefrog on 2008-03-30
all you want to do is possible.
but as your core job is doctor you should ask and pay for a company which deals with GPL softwares to build this for you.

james dupin

---

### Post by rgotten on 2008-03-30
Thanks for you comment, but as i mention beofre and in other parts of this forum, this is a project in a year time period in my spare time, computers is my hobby, and my knoledge (at least with windows is pretty advance), but have never deal before with linux, and would like to try, so your help and guidence in reference to my questions will greatly be appreciated

---

### Post by faulkes on 2008-03-30
You are correct in your general areas of what Ubuntu will do for you.

It would appear, the packages you want are LAMP (Apache/MySQL/PHP) and Samba
(to share files with windows computers).

The best resource for information on the individual packages you are looking to use
are found on the official and community documentation sites.  Each of those sites
is listed in my signature at the bottom.

As for building a database (beyond the actual installation of MySQL), that is 
something beyond the scope of what I can offer as that is more related 
spefically to what you are building and not a generalized support topic.  I would
see the MySQL site for specific information about that ([http://www.mysql.org](http://www.mysql.org))

Faulkes

---

### Post by pbpersson on 2008-03-30
I was just reading about LAMP and some varieties use MySQL with PHP and others use PostGreSQL with Ruby on Rails.  I would prefer the latter as I have heard that combination is much more powerful but that is just my opinion based on stories I have heard.

The difficult part will not be creating the database, that is a piece of cake.  I would suggest that the JPG and PDF files be loaded on the server and the database would contain the location of the files, I would not stuff those files INTO the database, but again this is just my preference on that.

The real challenge will be to create a program to read your current records and files and move the data into the database, along with the task of creating the web application to make this all work.  However, once it is done anyone in your office will be able to connect to the Ubuntu machine using a browser on any platform.

Do you have any programming experience with any language, or will you have someone else create the software?

Have you looked on the web to see if there already exists an open source "patient records" system you could just use instead of creating your own?

---

### Post by rgotten on 2008-03-30
Well like I mention earlier, my system patient record is pretty simple, since my dictation are creted in word formatt, printed and place in a paper chart and then it is  save in  folders by alphabetic order (last, first name and record number), my pictures are also save in an area of pictures also in alphabetic order and pdf files are just simple printed and place in the chart. I do not have many records anbd this will be implemented progresivly. I do not know programing language but i love computer (is my hobby) and i am willing to learn. Like i menion before.; it should be a very basic Database since i woul like it to hve the last name, fist name, record number and there i would find folders of the patient: ie: the chart folder will hve word documents, the picture folders will have jpg pictues, the billing folders will have scanned pdf files of insurance payments/patient check payments, etc. I agree that it should contain location of the files. (by the way i have already a medical system that i paid monthly for all the rest of the office managment ( complete patient information, billing to send claims to insurances, appointment), this is more for when i dictated, take pictures or recieve patient information from insurnaces, radilogy reports, laboratory report, etc.

Your help will be appreciated if any idea on guiding me

Thanks:)

---

### Post by Windy George on 2008-03-31
Hello Rgotton:

The latest version of Open Office has a database capability included.  It is free, it is supported, what else does one need?

George

---

### Post by rgotten on 2008-04-14
--------------------------------------------------------------------------------

I have installed the server edition and have the option to install the extras: DNS server, LAMP, Mail Server, open SSH, postgreg SQL, print server, Samba files.
As i mention, I am new to this, Should i install all of them based of what i have said in the past and for the purpose i am building the server?

---

### Post by Deathrend on 2008-04-14
Medical = Ouch.

Whatever you use, you need to keep five letters in mind.. HIPAA.

I'm a Sys Admin in the health insurance industry, the first thing we look at when dealing with information like this, is wather or not HIPAA supports the use of this method.  One person's information gets leaked, even if ti's just a name, you'll be neck deap before you can turn around.. It's always best to pay more, and get the best in this line of work..

We use Sybase\Oracle as a backend, this isn't fesable for you, but for direct access (Reports and such) we use Ruby on Rails *shutter* however it's a major pain i fyou're not on top of it 24/7.

I would suggest windows for this as well.  I love Linux, but the secuirty isn't nearly as user friendly, where as you can very easily lock down a windows file server without any real knoledge of what you're doing.

Just remember what ever you do, in this line of work, cheapest isn't best.  I would also suggest a decent firewall, which can be a well built Linux PC, however a DSL/Cable router isn't it.

Just some food for thought..

---

### Post by rgotten on 2008-04-16
> **faulkes said:**
> You are correct in your general areas of what Ubuntu will do for you.

It would appear, the packages you want are LAMP (Apache/MySQL/PHP) and Samba
(to share files with windows computers).

The best resource for information on the individual packages you are looking to use
are found on the official and community documentation sites.  Each of those sites
is listed in my signature at the bottom.

As for building a database (beyond the actual installation of MySQL), that is 
something beyond the scope of what I can offer as that is more related 
spefically to what you are building and not a generalized support topic.  I would
see the MySQL site for specific information about that ([http://www.mysql.org](http://www.mysql.org))

Faulkes

Well i install everything on the server option setup, since i heard that is ligth. One thing i left with no configuration during the installation was the " mail configuration" and I am having problems with the sudo command since it is asking for a password that i never setup. Reading and googling i found that this is because i did not perform the " mail configuration", and do not know how to configure it now.

Base on the above i have the following questions:

1) how to do the mail configuration or
2) reinstall completelly ubuntu server and just install some options (please advise on this, or is good to have everything install or if i need to install some componets after,  how you do this?) or
3) keep on playing for another 8 days and install server version 8.04 (by the way, will ubuntu upgrade authomatically??when new version come out??)

Thanks

---

### Post by rgotten on 2008-05-09
I have finish testing my software raid configuration and is working perfect. I did Radi 1 100 mb for boot, Raid 1 2 gb for swap, Raid 5 10 gb for the / (system), and Raid 5 (aprox: 980 Gb) for /home. (please let me know if this appears ok for you guys), then I have zero one of the hard drive (for testing) and it boot well in degrade mode, after i have rebuild the Raid without any problem. So now I am ready to continue with the server and this is what i need or questions i have:

I finally installed ubuntu server 8.04, from my understanding of what i needed after reading the threat i had to install the "LAMP" option and the "Samba" option. Which i had selected during my instalation of the server 8.04. NOW:

1) I need a easy way of configuring this ( i assume it was install simce i selecte it during the cd installation, can somebody give me some guidence on this.

2) If i would like to access this remotly from home or another computer, how can i do this (i have a router)??

3)How do i secure my server so nobody can access it from the outside

4) How do i do backups of the server??

Help will be apreciated

rgotten

---

### Post by rgotten on 2008-05-09
--------------------------------------------------------------------------------

I have finish testing my software raid configuration and is working perfect. I did Radi 1 100 mb for boot, Raid 1 2 gb for swap, Raid 5 10 gb for the / (system), and Raid 5 (aprox: 980 Gb) for /home. (please let me know if this appears ok for you guys), then I have zero one of the hard drive (for testing) and it boot well in degrade mode, after i have rebuild the Raid without any problem. So now I am ready to continue with the server and this is what i need or questions i have:

I finally installed ubuntu server 8.04, from my understanding of what i needed after reading the threat i had to install the "LAMP" option and the "Samba" option. Which i had selected during my instalation of the server 8.04. NOW:

1) I need a easy way of configuring this ( i assume it was install simce i selecte it during the cd installation, can somebody give me some guidence on this.

2) If i would like to access this remotly from home or another computer, how can i do this (i have a router)??

3)How do i secure my server so nobody can access it from the outside

4) How do i do backups of the server??

Help will be apreciated

rgotten

---

### Post by imon9 on 2008-05-09
hi,

first off, i am a 6th year medical student..and i am the network and sys admin for my student hostel. I use linux a lot and experiment on lots of server setup

ok, here is a few notes:
(1) i understand u want to set up your own system. but i would like to say there is alreayd some options in linux for medical database..maybe u can search for it and consider if they fits ur need.
Advantage of this is to minimized human error that cause ur files to be gone. 

(2) i see that u still want to use windows on most of ur computer and need a linux server to serve as ur data-server. Plus, ur main idea is to automized the organisation of the data to be saved correctly into the said folder in your data-server.

it is not too difficult to do. and the simpler the method u use, the more risk free it gets.

few comments:
(1) to be able to easily configure ur server. I actually recommend you to install the desktop version of ubuntu instead of server version. Both are the same, and the GUI (graphical interface) only waste a bit more RAM as a data-server. 

when i say easily configure ur server, i mean that u wont need to go through the pain staking commandline configuration (especially when u hardly knows linux)

(2) the photo organising software u are using...i suggest u change it to "picasa" (though it doesnt matter)

(3) i see that the way u organised ur patinet data is very primitive and simple.so there is no need for a real database (no need for mysql, or openoffice base). In such a way, u wont even need apache-php-mysql (LAMP)...

u just need to set up SAMBA so ur other computer can read and write data to it

my suggestion now:
(1) at front desk:
(a) ask ur nurse to create a folder with your patient name+registraition number
eg: John Doe PHL1092132
(b) then she copy the template of the word document for ur medical record into the created folder

(2) at doctor laptop:
(a) when u get ur patinet chart, u can search for the name+reg.no folder and find an empty emplate inside...dictate watever u need to ans save it.
(b) If u take any photo/scan any lab result, import it from your camara directly without using the "photo organising" program. Immediately rename the photo/scanned document accordingly
eg: photo from camera called IMG1092 to LP2008-04-28 01 (LP =lipid profile + date + number of test resutl, just in case there is more than just one test of the same kind on the same day)

(3) back to frontdesk/billing area:
(a) nurse search and find the folder of the patient, then scan the bill record and save it in the folder

method is pretty much fail save BUT it is danger for letting the nurse access the folder containing ur patient full record... who knows if ur nurse mistakenly deleted the files! (+ some patient privacy issue)

For u knowledge, if u use linux , u can set "permission" for each documents. So, your document will not be deleted/edit.

Extra notes:
for securing ur data, u can do the following:
(1) configure the firewall build-in in ubuntu
(2) you can encrypt all medical record (the backup)
(3) samba has it own password security
(4) saperate the server and backup from the INTERNET

IF you want you whole data to be able to be access from INTERNET at other location then ur clinic. then LAMP can be used... 

with apache, just set the database folder as your public domain. 

to secure a LAMP, u have to set up a login system.. this can be done, but thruogh pho scripts.

however, i would like to say, if you were to put ur patinet database on internet, u ought to be extra careful. 

Instead of simple internet, consider using private VPN

---

### Post by rgotten on 2008-05-10
Thanks for your reply, and hope that being on the medical field can get me get the rigth answers

> **imon9 said:**
> hi,
ok, here is a few notes:
(1) i understand u want to set up your own system. but i would like to say there is alreayd some options in linux for medical database..maybe u can search for it and consider if they fits ur need.
Advantage of this is to minimized human error that cause ur files to be gone. 


Well like you are saying, i woulk like to make somemething very simple, maybe i would look and see if there is something simple that would fit my needs, on the other hands i like (obviously if i have the time), to play and build things as lomg as they are simple. 

> **imon9 said:**
> (2) i see that u still want to use windows on most of ur computer and need a linux server to serve as ur data-server. Plus, ur main idea is to automized the organisation of the data to be saved correctly into the said folder in your data-server.

it is not too difficult to do. and the simpler the method u use, the more risk free it gets..

One more time i 100% agree, which way you will recomend to do this.

> **imon9 said:**
>  few comments:
(1) to be able to easily configure ur server. I actually recommend you to install the desktop version of ubuntu instead of server version. Both are the same, and the GUI (graphical interface) only waste a bit more RAM as a data-server.when i say easily configure ur server, i mean that u wont need to go through the pain staking commandline configuration (especially when u hardly knows linux)


Well i have already install the server edition. Are you recomending unistall and reinstal the desktop edition or install on top of the server, the GUI?..any other ligth GUI to install on top of the serverthat you know, i have read that some people recomend kubuntu (since is ligther, other recoemnd webmin..etc?


> **imon9 said:**
> 
(3) i see that the way u organised ur patinet data is very primitive and simple.so there is no need for a real database (no need for mysql, or openoffice base). In such a way, u wont even need apache-php-mysql (LAMP)...

I already installed LAMP and Samba when i install the server version..Should i unistall it??

> **imon9 said:**
>  u just need to set up SAMBA so ur other computer can read and write data to it

my suggestion now:
(1) at front desk:
(a) ask ur nurse to create a folder with your patient name+registraition number
eg: John Doe PHL1092132
(b) then she copy the template of the word document for ur medical record into the created folder

(2) at doctor laptop:
(a) when u get ur patinet chart, u can search for the name+reg.no folder and find an empty emplate inside...dictate watever u need to ans save it.
(b) If u take any photo/scan any lab result, import it from your camara directly without using the "photo organising" program. Immediately rename the photo/scanned document accordingly
eg: photo from camera called IMG1092 to LP2008-04-28 01 (LP =lipid profile + date + number of test resutl, just in case there is more than just one test of the same kind on the same day)

(3) back to frontdesk/billing area:
(a) nurse search and find the folder of the patient, then scan the bill record and save it in the folder

Let me start by asking the following; I have read that instead of having all the documents "in" the database, i should have folders (and maybe this is what you were saying) and then indexing them to the database. 

What you have describe is what i need, Where do i start, At the presetn moment i have a directory in alphabetic order with all the patients record in word format, another directory with alphabetic order of the pictures..is this the same way i should do this or should i do this in a diferent way..If you have good input i will strongly appreciate it 

> **imon9 said:**
>  method is pretty much fail save BUT it is danger for letting the nurse access the folder containing ur patient full record... who knows if ur nurse mistakenly deleted the files! (+ some patient privacy issue)

For u knowledge, if u use linux , u can set "permission" for each documents. So, your document will not be deleted/edit.

Great idea, how do i do this?

> **imon9 said:**
> 
Extra notes:
for securing ur data, u can do the following:
(1) configure the firewall build-in in ubuntu
(2) you can encrypt all medical record (the backup)
(3) samba has it own password security
(4) saperate the server and backup from the INTERNET

1) Is the firewall easy to configure?
2) How do i encrypt the medical records?
3) Where i can get instruction on configuring samba?
4) How do i separate the sever from the internet and what happen if i would like to remote access a file

> **imon9 said:**
> 
IF you want you whole data to be able to be access from INTERNET at other location then ur clinic. then LAMP can be used...
Can this be done as a web page access, and is this secure, and how to do it? 

> **imon9 said:**
> with apache, just set the database folder as your public domain.

 Sorry, remember i am new on this; I am assuming this folder should be install on the /home partition, and then if i have the organization mention above, how should this be done, so it can be indexed and access from the database, or please tell me and explain how you will do it...

> **imon9 said:**
> to secure a LAMP, u have to set up a login system.. this can be done, but thruogh pho scripts..Sorry one more time for my ignorance but what is a pho scripts?

> **imon9 said:**
> however, i would like to say, if you were to put ur patinet database on internet, u ought to be extra careful. 

Instead of simple internet, consider using private VPN

Will i have access or be able to access my patient information from any hospital or place with VPN or i have to install something every time i want to access the information??

Buy the way, sorry to overload you with so many questions, but i really appreciate all you help

Thanks and hope to hear from you soon

rgotten

---

### Post by imon9 on 2008-05-10
```
Originally Posted by imon9 View Post
hi,
ok, here is a few notes:
(1) i understand u want to set up your own system. but i would like to say there is alreayd some options in linux for medical database..maybe u can search for it and consider if they fits ur need.
Advantage of this is to minimized human error that cause ur files to be gone.
```

Well like you are saying, i woulk like to make somemething very simple, maybe i would look and see if there is something simple that would fit my needs, on the other hands i like (obviously if i have the time), to play and build things as lomg as they are simple.


```
Quote:
Originally Posted by imon9 View Post
(2) i see that u still want to use windows on most of ur computer and need a linux server to serve as ur data-server. Plus, ur main idea is to automized the organisation of the data to be saved correctly into the said folder in your data-server.

it is not too difficult to do. and the simpler the method u use, the more risk free it gets..
```
One more time i 100% agree, which way you will recomend to do this.

>> first, set up your data-server. That will be installing ubuntu-desktop version from the live-CD. After which you should configure SAMBA. SAMBA will make your data-server appear in the local network of your WINDOWS WORKGROUP. A password maybe used to improve security.

the reason i asked u to install ubuntu-desktop compared to ubuntu-server version , is because later u could really use the GUI to configure the security related stuff :)

```
Quote:
Originally Posted by imon9 View Post
few comments:
(1) to be able to easily configure ur server. I actually recommend you to install the desktop version of ubuntu instead of server version. Both are the same, and the GUI (graphical interface) only waste a bit more RAM as a data-server.when i say easily configure ur server, i mean that u wont need to go through the pain staking commandline configuration (especially when u hardly knows linux)
```
Well i have already install the server edition. Are you recomending unistall and reinstal the desktop edition or install on top of the server, the GUI?..any other ligth GUI to install on top of the serverthat you know, i have read that some people recomend kubuntu (since is ligther, other recoemnd webmin..etc?

>> did u find the server-edition easy to use?? if u have not much idea how to start configuring things, then i would recommend reinstall to desktoip-edition. Kubuntu with KDE4 is tested and proven slightly lighter..but i wont recommend it. As for Xubuntu, it is a okay choice. Understand that Gnome and KDE is the main player of windows manager to be used. The reason is that both has a good GUI tools to configure much of the things.

Yes, indeed, you could configure a lot of stuff using webmin. It will be the next phase of your project, if u finally get the hang of it.

try installing webmin in the ubuntu-desktop version and see how far u can go configuring things without touching the GUI. (PS: webmin is a program/services that make configuration of the computer through web browser)

combination of ubuntu-server edition + webmin = ubuntu-desktop+beginner :)

```
Quote:
Originally Posted by imon9 View Post
(3) i see that the way u organised ur patinet data is very primitive and simple.so there is no need for a real database (no need for mysql, or openoffice base). In such a way, u wont even need apache-php-mysql (LAMP)...
```
I already installed LAMP and Samba when i install the server version..Should i unistall it??

>>> there is no need to uninstall this yet. As you mentioned in your answer below, that u need to access your database through internet. So, you will need this... of course there are several other choices. Please continue reading, i will explain it later.

```
Quote:
Originally Posted by imon9 View Post
u just need to set up SAMBA so ur other computer can read and write data to it

my suggestion now:
(1) at front desk:
(a) ask ur nurse to create a folder with your patient name+registraition number
eg: John Doe PHL1092132
(b) then she copy the template of the word document for ur medical record into the created folder

(2) at doctor laptop:
(a) when u get ur patinet chart, u can search for the name+reg.no folder and find an empty emplate inside...dictate watever u need to ans save it.
(b) If u take any photo/scan any lab result, import it from your camara directly without using the "photo organising" program. Immediately rename the photo/scanned document accordingly
eg: photo from camera called IMG1092 to LP2008-04-28 01 (LP =lipid profile + date + number of test resutl, just in case there is more than just one test of the same kind on the same day)

(3) back to frontdesk/billing area:
(a) nurse search and find the folder of the patient, then scan the bill record and save it in the folder
Let me start by asking the following; I have read that instead of having all the documents "in" the database, i should have folders (and maybe this is what you were saying) and then indexing them to the database.
```

What you have describe is what i need, Where do i start, At the presetn moment i have a directory in alphabetic order with all the patients record in word format, another directory with alphabetic order of the pictures..is this the same way i should do this or should i do this in a diferent way..If you have good input i will strongly appreciate it

>> earlier, you mention that what u like is something like this:

[main folder] eg: with patient name
----------[subfolder1] for patient history
----------[subfolder2] for patient photos & scanned lab result
----------[subfolder3] for patient scanned billings copies

and now your existing ones are:
[folder1] patient history (named in aplabetical order)
[fodler2] photos (named in alpabetical order)
etc

as we can see, ur existing system is not good where, you cannot access 1 patients documents without searching for the records, photos and billings seperately.

PS: i have one question, what kind of phtos are u keeping? i am thinking those photos are either filed photos for medical claiming, or scanned lab results. Is that what u meant by photos? Or you only mean it is a patient passport-sized photos?

if the photos are filed photos+scanned documents, what do u mean by u having them in alpahbetical order? Did u mean, u have them in a subfolder, of which the subfolder is alphabetically named?

And the new system you suggested is good, but i suggest a bit of modification to make it more fail-safe.

Look at the model u suggested. The main folder is named with patient name but the subfolder and all files under it is not. If this it the case, the mistake in placing the files while moving them from one folder to another makes it impposible to re-trace it back easily without opening the document itself.

So i suggest this: add registration number before/ after each filename

my model=
[main folder] = patient name + Reg.Number eg: [john doe JPK12039]
----------[subfolder1] for patient history eg: [medical record JPK12039]
------------------- <file1> = date + reg number eg: <25-03-2008 JPK12039>
----------[subfolder2] for patient photos & scanned lab result
----------[subfolder3] for patient scanned billings copies

as for the ways to do AUTOMATE this, it requires a bit of programming skill. Most ppl opt for custom written system...but if u weren't too afraid, u can just use a PHP scripting.

with PHP scripting, your front-desk nurse will type the name and the reg.number of you patient into a forms in a webpage.

the PHP script will automatically create all the nessasary standard folder. Also it can made to copy the patient history template to the needed folder and automate the filename too!

However, you will need to lern a bit of PHP scripting. But mostly, you can use the free-PHP script which is pre-made and modify them to your need.


```
Quote:
Originally Posted by imon9 View Post
method is pretty much fail save BUT it is danger for letting the nurse access the folder containing ur patient full record... who knows if ur nurse mistakenly deleted the files! (+ some patient privacy issue)

For u knowledge, if u use linux , u can set "permission" for each documents. So, your document will not be deleted/edit.
```
Great idea, how do i do this?

>> this is not too relevant for our discussion this time. I will explain in future if u needs it

```
Quote:
Originally Posted by imon9 View Post
Extra notes:
for securing ur data, u can do the following:
(1) configure the firewall build-in in ubuntu
(2) you can encrypt all medical record (the backup)
(3) samba has it own password security
(4) saperate the server and backup from the INTERNET
```
1) Is the firewall easy to configure?
>> yes, they can be easily configured using a program. There are a few choices: from simple to set up, to a bit more advance.

my personal favourite is "guarddog"
(you can download and install it using synaptics)

2) How do i encrypt the medical records?
>>encrytion is more useful in the case of the back-up data aside from the database on the data-server. Well, there are a handful of encryption program. Basically, it is just like zipping the file with a password :)

3) Where i can get instruction on configuring samba?
>>if u configure samba in ubuntu-desktop instead of ubuntu-server edition, there are already configuration program built-in. Try search the forum for any instructions/ link to the information.

4) How do i separate the sever from the internet and what happen if i would like to remote access a file
>> in the case where u want to access files from the internet, you cannot seperate the server from the internet.


```
Quote:
Originally Posted by imon9 View Post
IF you want you whole data to be able to be access from INTERNET at other location then ur clinic. then LAMP can be used...
```
Can this be done as a web page access, and is this secure, and how to do it?
>> this can be done in several ways, but the simplest being viewing them as webpages.
Using of PHP script to present the data is possible too!

second best choise is to setup an FTP server instead of LAMP. FTP server has build-in security, so you wont need to set up your own security system like in webpages.

```
Quote:
Originally Posted by imon9 View Post
with apache, just set the database folder as your public domain.
```
Sorry, remember i am new on this; I am assuming this folder should be install on the /home partition, and then if i have the organization mention above, how should this be done, so it can be indexed and access from the database, or please tell me and explain how you will do it...

>> well, yes, the data most probably will be saved in your /home folder. You simply have to edit the file /etc/apache2/sites-available/default

example ..add a directory under virtual host
```
	DocumentRoot /home/[username]/[main folder]/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/[username]/[main folder]/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
 		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>
```

```
Quote:
Originally Posted by imon9 View Post
to secure a LAMP, u have to set up a login system.. this can be done, but thruogh pho scripts..
```
Sorry one more time for my ignorance but what is a pho scripts?
>> sorry, this is a typo. I meant PHP scripts :p

example of a free script [http://linuxwebshop.com/phpuserbase.php](http://linuxwebshop.com/phpuserbase.php)
(check out the demo page)

```
Quote:
Originally Posted by imon9 View Post
however, i would like to say, if you were to put ur patinet database on internet, u ought to be extra careful.

Instead of simple internet, consider using private VPN
```
Will i have access or be able to access my patient information from any hospital or place with VPN or i have to install something every time i want to access the information??

>> VPN is dedicated networking, so it is not available everywhere... if u want to access the file in the manner u described, then internet maybe you only options

there is **hamachi** which allows you to access you clinic local network from the internet. Much more secure in somw way.. but i am not sure if it is free... :(


Buy the way, sorry to overload you with so many questions, but i really appreciate all you help
>> hahah... i guess one question will always lead to another :)

You can ask me if u want some example of PHP script and how to modify them. BUt i would appreciate if u try to google it and understand what PHP can do :)

---

### Post by Sef on 2008-05-10
> there is hamachi which allows you to access you clinic local network from the internet. Much more secure in somw way.. but i am not sure if it is free...

FRom Hamachi's site:

> Overview

Use LogMeIn Hamachi for free – provide your small business a remote access solution that is secure, easy, and enhances business performance.

Hamachi is currently available for Windows 2000, XP, 2003, and Vista. Console versions of Hamachi are also available for Linux and OS X.

Hamachi installers support incremental upgrades. If you have a version of Hamachi already installed on your computer, just run the installer and it will update the program files and retain your Hamachi setup.

---

### Post by imon9 on 2008-05-11
With that, it is comfirmed Hamachi will be free, but you will need to install HAmachi Client in the other computer that u wanted to access your files ...

btw, ftp client that uses SSH also needs a program to be install ..but there are portable version of the program that u can just bring in your thumb drive :)
(i can't remember but i think IE can be used to open FTP as well, mybe)

---

### Post by rgotten on 2008-05-11
I have reply to you with **** and then the frase***

>> first, set up your data-server. That will be installing ubuntu-desktop version from the live-CD. After which you should configure SAMBA. SAMBA will make your data-server appear in the local network of your WINDOWS WORKGROUP. A password maybe used to improve security.

the reason i asked u to install ubuntu-desktop compared to ubuntu-server version , is because later u could really use the GUI to configure the security related stuff :)

```
Quote:
Originally Posted by imon9 View Post
few comments:
(1) to be able to easily configure ur server. I actually recommend you to install the desktop version of ubuntu instead of server version. Both are the same, and the GUI (graphical interface) only waste a bit more RAM as a data-server.when i say easily configure ur server, i mean that u wont need to go through the pain staking commandline configuration (especially when u hardly knows linux)
```
Well i have already install the server edition. Are you recomending unistall and reinstal the desktop edition or install on top of the server, the GUI?..any other ligth GUI to install on top of the serverthat you know, i have read that some people recomend kubuntu (since is ligther, other recoemnd webmin..etc?

>> did u find the server-edition easy to use?? if u have not much idea how to start configuring things, then i would recommend reinstall to desktoip-edition. Kubuntu with KDE4 is tested and proven slightly lighter..but i wont recommend it. As for Xubuntu, it is a okay choice. Understand that Gnome and KDE is the main player of windows manager to be used. The reason is that both has a good GUI tools to configure much of the things.

Yes, indeed, you could configure a lot of stuff using webmin. It will be the next phase of your project, if u finally get the hang of it.

try installing webmin in the ubuntu-desktop version and see how far u can go configuring things without touching the GUI. (PS: webmin is a program/services that make configuration of the computer through web browser)

combination of ubuntu-server edition + webmin = ubuntu-desktop+beginner :)

*** Well i have read so much and that is why i have try to be away of installing something on top of the server edition, like i told you linux is new, but even was not easy i did the partition with two 1 raids (boot and swap) and 2 5 raids (system / and /home), evidently something easier will be nicer, that is why i need to understant, if i install gui from desktop, how will that be diferent from server + ebox (it looks that the latest might be the way to go compare with webmin), but your input is strongly accepted***

```
Quote:
Originally Posted by imon9 View Post
(3) i see that the way u organised ur patinet data is very primitive and simple.so there is no need for a real database (no need for mysql, or openoffice base). In such a way, u wont even need apache-php-mysql (LAMP)...
```
I already installed LAMP and Samba when i install the server version..Should i unistall it??

>>> there is no need to uninstall this yet. As you mentioned in your answer below, that u need to access your database through internet. So, you will need this... of course there are several other choices. Please continue reading, i will explain it later.

```
Quote:
Originally Posted by imon9 View Post
u just need to set up SAMBA so ur other computer can read and write data to it

my suggestion now:
(1) at front desk:
(a) ask ur nurse to create a folder with your patient name+registraition number
eg: John Doe PHL1092132
(b) then she copy the template of the word document for ur medical record into the created folder

(2) at doctor laptop:
(a) when u get ur patinet chart, u can search for the name+reg.no folder and find an empty emplate inside...dictate watever u need to ans save it.
(b) If u take any photo/scan any lab result, import it from your camara directly without using the "photo organising" program. Immediately rename the photo/scanned document accordingly
eg: photo from camera called IMG1092 to LP2008-04-28 01 (LP =lipid profile + date + number of test resutl, just in case there is more than just one test of the same kind on the same day)

(3) back to frontdesk/billing area:
(a) nurse search and find the folder of the patient, then scan the bill record and save it in the folder
Let me start by asking the following; I have read that instead of having all the documents "in" the database, i should have folders (and maybe this is what you were saying) and then indexing them to the database.
```

What you have describe is what i need, Where do i start, At the presetn moment i have a directory in alphabetic order with all the patients record in word format, another directory with alphabetic order of the pictures..is this the same way i should do this or should i do this in a diferent way..If you have good input i will strongly appreciate it

>> earlier, you mention that what u like is something like this:

[main folder] eg: with patient name
----------[subfolder1] for patient history
----------[subfolder2] for patient photos & scanned lab result
----------[subfolder3] for patient scanned billings copies

and now your existing ones are:
[folder1] patient history (named in aplabetical order)
[fodler2] photos (named in alpabetical order)
etc

as we can see, ur existing system is not good where, you cannot access 1 patients documents without searching for the records, photos and billings seperately.

PS: i have one question, what kind of phtos are u keeping? i am thinking those photos are either filed photos for medical claiming, or scanned lab results. Is that what u meant by photos? Or you only mean it is a patient passport-sized photos?

*** Photos are of the patient...I am a plastic surgeon, so fotos of the breast, nose, preop post op, they are jpeg.***

if the photos are filed photos+scanned documents, what do u mean by u having them in alpahbetical order? Did u mean, u have them in a subfolder, of which the subfolder is alphabetically named?

*** Folders A,B,C, etc, then in A i have John Alcot 1234, the same way on the "chart directory" there are A, B, D, and then in the A will be John Alcot 1234. If i want to only see pictures, i just open zoombrowser and go look by alphabet, if i would like to get a word chart document, i go to the Chart directory and in the search i palce 1234 search and John Alcort 1234 will be found***

And the new system you suggested is good, but i suggest a bit of modification to make it more fail-safe.

Look at the model u suggested. The main folder is named with patient name but the subfolder and all files under it is not. If this it the case, the mistake in placing the files while moving them from one folder to another makes it impposible to re-trace it back easily without opening the document itself.

So i suggest this: add registration number before/ after each filename

my model=
[main folder] = patient name + Reg.Number eg: [john doe JPK12039]
----------[subfolder1] for patient history eg: [medical record JPK12039]
------------------- <file1> = date + reg number eg: <25-03-2008 JPK12039>
----------[subfolder2] for patient photos & scanned lab result
----------[subfolder3] for patient scanned billings copies

as for the ways to do AUTOMATE this, it requires a bit of programming skill. Most ppl opt for custom written system...but if u weren't too afraid, u can just use a PHP scripting.

with PHP scripting, your front-desk nurse will type the name and the reg.number of you patient into a forms in a webpage.

the PHP script will automatically create all the nessasary standard folder. Also it can made to copy the patient history template to the needed folder and automate the filename too!

However, you will need to lern a bit of PHP scripting. But mostly, you can use the free-PHP script which is pre-made and modify them to your need.

*** I can try PHP, but will the folders be save in the database or they will be indexed, I heard that if you index them it will be ligther. and how can i do this?***

```
Quote:
Originally Posted by imon9 View Post
method is pretty much fail save BUT it is danger for letting the nurse access the folder containing ur patient full record... who knows if ur nurse mistakenly deleted the files! (+ some patient privacy issue)

For u knowledge, if u use linux , u can set "permission" for each documents. So, your document will not be deleted/edit.
```
Great idea, how do i do this?

>> this is not too relevant for our discussion this time. I will explain in future if u needs it

*** ok will wait to do this down the road***

```
Quote:
Originally Posted by imon9 View Post
Extra notes:
for securing ur data, u can do the following:
(1) configure the firewall build-in in ubuntu
(2) you can encrypt all medical record (the backup)
(3) samba has it own password security
(4) saperate the server and backup from the INTERNET
```
1) Is the firewall easy to configure?
>> yes, they can be easily configured using a program. There are a few choices: from simple to set up, to a bit more advance.

my personal favourite is "guarddog"
(you can download and install it using synaptics)

*** i do not know what is Synaptis, also what do you thign about the ubuntu 8.04 UFW firewall, also when i was looking into ssw, webmin, and ebox, i see that ebox also has a firewall, is this for the inoffice network or from the outside towards my network***

2) How do i encrypt the medical records?
>>encrytion is more useful in the case of the back-up data aside from the database on the data-server. Well, there are a handful of encryption program. Basically, it is just like zipping the file with a password :)

3) Where i can get instruction on configuring samba?
>>if u configure samba in ubuntu-desktop instead of ubuntu-server edition, there are already configuration program built-in. Try search the forum for any instructions/ link to the information.

4) How do i separate the sever from the internet and what happen if i would like to remote access a file
>> in the case where u want to access files from the internet, you cannot seperate the server from the internet.

*** What happen if i use Hamachi???, can it be more secure, but still be able to access??***


```
Quote:
Originally Posted by imon9 View Post
IF you want you whole data to be able to be access from INTERNET at other location then ur clinic. then LAMP can be used...
```
Can this be done as a web page access, and is this secure, and how to do it?
>> this can be done in several ways, but the simplest being viewing them as webpages.
Using of PHP script to present the data is possible too!

*** is this going to be access with Hamachi or just as a webpage???****

second best choise is to setup an FTP server instead of LAMP. FTP server has build-in security, so you wont need to set up your own security system like in webpages.

*** is this a better option as the one before, are any of tis more Hippa complient???****

```
Quote:
Originally Posted by imon9 View Post
with apache, just set the database folder as your public domain.
```
Sorry, remember i am new on this; I am assuming this folder should be install on the /home partition, and then if i have the organization mention above, how should this be done, so it can be indexed and access from the database, or please tell me and explain how you will do it...

>> well, yes, the data most probably will be saved in your /home folder. You simply have to edit the file /etc/apache2/sites-available/default

example ..add a directory under virtual host
```
	DocumentRoot /home/[username]/[main folder]/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/[username]/[main folder]/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
 		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>
```


*** i guess i will do this after samba is installed and i cna access the system form any of my other computers?***
```
Quote:
Originally Posted by imon9 View Post
to secure a LAMP, u have to set up a login system.. this can be done, but thruogh pho scripts..
```
Sorry one more time for my ignorance but what is a pho scripts?
>> sorry, this is a typo. I meant PHP scripts :p

example of a free script [http://linuxwebshop.com/phpuserbase.php](http://linuxwebshop.com/phpuserbase.php)
(check out the demo page)

```
Quote:
Originally Posted by imon9 View Post
however, i would like to say, if you were to put ur patinet database on internet, u ought to be extra careful.

Instead of simple internet, consider using private VPN
```
Will i have access or be able to access my patient information from any hospital or place with VPN or i have to install something every time i want to access the information??

>> VPN is dedicated networking, so it is not available everywhere... if u want to access the file in the manner u described, then internet maybe you only options

*** Well another way could be to have something on my laptop to be able to access my server remotly from my laptop, or in the event i can not use my laptop, something that can be on a USB to coneect to any computer, What do you think about this???***

there is **hamachi** which allows you to access you clinic local network from the internet. Much more secure in somw way.. but i am not sure if it is free... :(


Buy the way, sorry to overload you with so many questions, but i really appreciate all you help
>> hahah... i guess one question will always lead to another :)

You can ask me if u want some example of PHP script and how to modify them. BUt i would appreciate if u try to google it and understand what PHP can do :)[/QUOTE]


*** Well not to botgher you a lot and get tire of me to qucikly, i will start with SAMBA and hen the computer can connect to the server will go to the next step and so on,

Thanks a lot and will way for your replys

rgotten

---

### Post by imon9 on 2008-05-11
*** Well i have read so much and that is why i have try to be away of installing something on top of the server edition, like i told you linux is new, but even was not easy i did the partition with two 1 raids (boot and swap) and 2 5 raids (system / and /home), evidently something easier will be nicer, that is why i need to understant, if i install gui from desktop, how will that be diferent from server + ebox (it looks that the latest might be the way to go compare with webmin), but your input is strongly accepted***

### actually, like i mention 2 post before, the server-edition and desktop edition differ only by perhaps, say 300-400MB of extra ram usage... if u have say 2 GB ram, what's to worry? :)

plus, u are really new to linux. I don't see anyone can pick up by going straight to server-edition.

(as you need to understand, the server-edition is called in such a way not because of it having any difference in functionality comapred to desktop-version. They simply strip away all graphical component of the system because one would not really need to touch the machine once it is set-up. So, most ppl will think why waste the resources (a.k.a the extra RAM). That is why, u will often hear ppl say that they will use the old machine as server. (eg: 486 machines, pentium3? :p)

as i understand, you build a core-duo PC as server...why worry so much ? :p
###


*** Photos are of the patient...I am a plastic surgeon, so fotos of the breast, nose, preop post op, they are jpeg.***

Folders A,B,C, etc, then in A i have John Alcot 1234, the same way on the "chart directory" there are A, B, D, and then in the A will be John Alcot 1234. If i want to only see pictures, i just open zoombrowser and go look by alphabet, if i would like to get a word chart document, i go to the Chart directory and in the search i palce 1234 search and John Alcort 1234 will be found***

### i see, so you always look at the info seperately. Not too ideal, no? I mean, if u keep 3 seperatemain folder: 
[main folder 1 = medical record]
[mian folder 2 = photos]
[main folder 3 = bills]
so when u need to check for 1 patient, u will have to find it 3 TIMES!! :p

compared to the model i wrote, u only serch once and access all information under the subfolders :)
###


*** I can try PHP, but will the folders be save in the database or they will be indexed, I heard that if you index them it will be ligther. and how can i do this?***

### about indexing... well, i have to say this: indexing is a "service" if you create a database. There are several model of database that can be created.. one of the free choice will be mySQL.

however, that means, you will have to migrate it into such kind of database... 

for a database like yours... i won't recommend it.

depends on the model of databse, it can support a good 5000-15000 patients database.

If you have a number of patinet say less than 3000... it wont slow down much.###

*** i do not know what is Synaptis, also what do you thign about the ubuntu 8.04 UFW firewall, also when i was looking into ssw, webmin, and ebox, i see that ebox also has a firewall, is this for the inoffice network or from the outside towards my network***
### my bad, synaptics is "add or remove program" in XP. it is a program that function similar to "apt-get install" (commandline used for installing stuff in linux)

PS: the more reason to start install desktop-version... will save you a lot of time!!!
and yes, i do mean reinstall you server-version to desktop version. This will prevent some complicated issue of missing programs etc. You wont want to do that.
###


*** What happen if i use Hamachi???, can it be more secure, but still be able to access??***
### if u use hamachi, you will need to install a client on each computer u want to access the data. It look like something like a MSN messenger or Yahoo messenger.

however, no portable version :(
###

```
Quote:
Originally Posted by imon9 View Post
IF you want you whole data to be able to be access from INTERNET at other location then ur clinic. then LAMP can be used...
```
Can this be done as a web page access, and is this secure, and how to do it?
>> this can be done in several ways, but the simplest being viewing them as webpages.
Using of PHP script to present the data is possible too!

*** is this going to be access with Hamachi or just as a webpage???****
### if u use LAMP, then it will be access simply using a web browser ###

second best choise is to setup an FTP server instead of LAMP. FTP server has build-in security, so you wont need to set up your own security system like in webpages.

*** is this a better option as the one before, are any of tis more Hippa complient???****
### i would say, less trouble to set up, but less flexible to manipulate.

it is easier to set up because FTP can use SSH security and has its own login system build-in. All you get to access is the folder (with its repective subfolders and files)

why i say it is less flexible, is because the with PHP script, you can futher manipulate the folder, subfolder, and files to be displayed according to how you like it (of course, this also means you will need to spend time designing the system)

So, if i were you, i will go with FTP. DO note that FTP is SLOWER! but i wonder how fast you would need it anyway. With internet connections nowadays, doc files and img files won;t take too long to download...so u will get ur data out within 3-5 mins in reality anyway)

BUT being myself, i would go for LAMP.###


*** i guess i will do this after samba is installed and i cna access the system form any of my other computers?***
###After installing samba, you will be able to see your data-server in your "my network places" (it is microsoft networking) on all your locally connected PC. (accessible thru LAN, not internet)

then u will install either LAMP or FTP so that you can get ur data through INTERNET
###

>> VPN is dedicated networking, so it is not available everywhere... if u want to access the file in the manner u described, then internet maybe you only options

*** Well another way could be to have something on my laptop to be able to access my server remotly from my laptop, or in the event i can not use my laptop, something that can be on a USB to coneect to any computer, What do you think about this???***
### yes, private VPN allow you to access you computer remotely as if it is a locally connected computer. But the VPN line is used more often for ppl who has 2 offices. And you want 2 offices to be connected as one big local network.

for your case where you want to access it ANYWHERE, internet may be your only option###


*** Well not to botgher you a lot and get tire of me to qucikly, i will start with SAMBA and hen the computer can connect to the server will go to the next step and so on

### correct, i will now start telling u wat to do in step-by-step manner. perhaps tmr i will draw u a diagram of how u link stuff up eventually. I think it will be more helpful than just words.

STEP 1: build server computer/ or buy one PC (i think you already did this)
STEP 2: downlaod ubuntu-desktop liveCD & install/reintall it on your computer. 
(do let me know how many HD u use, and how you plan to spit the partition. I dont want to guide u beyond this and when we finish setting up, only to find out we missed the fundamental stuff)
STEP 3: connect all your office computer to the HUB. (you mention earlier your local computer linked together using wired and wireless. I assume that is the internet router?)

STEP 4: Set all local computer to be in the same domain/workgroup 
(make sure u see each other in the "my network places")

STEP 5: set up SAMBA in the data-server (using the simple built-in GUI, it just take maybe 5 steps. upon completion, your data-server will appear in the "my network places" too!)

STEP 6: decide how to organise your data. (which folder structure you would use?)

STEP 7: test the model in a test-working environtment
(this is crucial, coz this is what you need to instruct your staff to do later on)

STEP 8: make the database available to the internet = installing FTP or LAMP.

STEP 9: test the connection into the database through internet from other location (eg: at home)

(first, i suggest you try FTP.... after you feel comfortable enough, can move on to LAMP and see wat kind of flexibility it can gives. However, FTP is robust enough for wat it is worth :) )

please let me know at which stage u are at the next time you reply. Easier for me to orientate the instruction (if any)

---

### Post by rgotten on 2008-05-13
[QUOTE=imon9;4935579
STEP 1: build server computer/ or buy one PC (i think you already did this)
STEP 2: downlaod ubuntu-desktop liveCD & install/reintall it on your computer. 
(do let me know how many HD u use, and how you plan to spit the partition. I dont want to guide u beyond this and when we finish setting up, only to find out we missed the fundamental stuff)
STEP 3: connect all your office computer to the HUB. (you mention earlier your local computer linked together using wired and wireless. I assume that is the internet router?)

STEP 4: Set all local computer to be in the same domain/workgroup 
(make sure u see each other in the "my network places")

STEP 5: set up SAMBA in the data-server (using the simple built-in GUI, it just take maybe 5 steps. upon completion, your data-server will appear in the "my network places" too!)

STEP 6: decide how to organise your data. (which folder structure you would use?)

STEP 7: test the model in a test-working environtment
(this is crucial, coz this is what you need to instruct your staff to do later on)

STEP 8: make the database available to the internet = installing FTP or LAMP.

STEP 9: test the connection into the database through internet from other location (eg: at home)

(first, i suggest you try FTP.... after you feel comfortable enough, can move on to LAMP and see wat kind of flexibility it can gives. However, FTP is robust enough for wat it is worth :) )

please let me know at which stage u are at the next time you reply. Easier for me to orientate the instruction (if any)[/QUOTE]


Step 2: I build the server with 3 hard drives (each one 500gb), i have play and test them for failrue and they owrk wonderfull. This is the configuration: RAID 1 100mb for /boot, RAID 1 2gb for swap, RAID5 10gb for / , and RAID 5 987gb for /home. 

Step 3 yes you are correct, there are conected thru the internet router.

Step 4: I see them but some have restrictions, i have never chenge any stting here since i did no t neede, Do i need to change anything here before i go to the next step?

In regards to the next step i was playing before you told me about the gui interface of the Desktop version and installed Ebox, (to try it) and even though my knowlledge is very primitive in this, it looks like a very nice interface, (Please look at: [http://ebox-platform.com/screenshots/)and](http://ebox-platform.com/screenshots/)and) let me know what do you think. I played with it once and i saw the server on the netwokr, but trying to make it cleare, i reintall ubuntu server with no application and then installed ebox. Before i do the configuration from samba from ebox, let me please ask you if i need to have everything installed from ebox (i installe everything, and if you thing i should not, i will reintall it: this is what is has at the present moment: sysinfo, network, firewall, users, openvpn, ntp, jabber, printers, dhcp, samba, objects, software, mailfilter, trafficshapping, services, logs, global, squid, events, mail, dns, ca, apache). Thanks so much for you guidence. Will wait for your advice

rgotten

---

### Post by imon9 on 2008-05-14
e-box has a nice interface....but in all those things they provide, u only needed 1-2: mainly the Samba (File sharing) & firewall (+- the backup)

webmin (demo at [http://www.webmin.com/demo.html](http://www.webmin.com/demo.html)) is a advanced version on e-box, with capability to configure ur ubuntu-server edition by its powerful configuration engine....

Here's what i can say... if u insist on keeping the server-edition , then webmin will be the best choice

the desktop-version = webmin... just that desktop version is more windows alike, shall i say :)

anyhow, my ealier plan was to have u install the desktop-version, configure the stuff as u need to (as a beginer, it is always easier to configure using GUI), then install webmin and try learn how you can configure using webmin

when u are confident enough, remove the GUI/desktop interface.. then it will become exactly as how server-edition would have been...

as for your raid setting, it is not bad...
however, here is a few pointers:
(1) u dun really need to seperate /boot with /
(2) u ought to give more space to / (though 10GB is good, i save 15-18 is great when u need upgrade
(3) swap should be double of the ram size u have...

---

### Post by rgotten on 2008-05-14
ok, i follow your instruction and today installed webmin, and you are very rigth, it has a very nice interface and it looks more complete than ebox. (i know you are going to say i am a hard headed, but if i get stuck and not able to advance, i promise you i will install the desktop version). In reference to the raid; i did multiple testing and fails to be sure it works well, and all my testing have come with good results, now if you would like me to change the size of the raids, is there a way of changing them without having to zero all the hard drive and installing this from scratch??

Now, going to samba..is it easy to isntall from Webmin, i will google, and if you have easy step to follow, i will apreciate them

One more time Thanks so much for all your instruction

rgotten

---

### Post by imon9 on 2008-05-15
hahah...no, it is okay to be hard-headed. In any case, it will be the same. You may resize the raid using "gparted" liveCD... though, i am totally fine with ur current setting. There is no need to go extra length to resize it.

as for the webmin, u will need a few module, "samba" and "ftp" later.

and yes, u are right, there is plenty of easy to use guide for setting up samba and ftp. just google it.

i give u a link for FTP : [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

PS: webmin does not help u install stuff.. so u have to use "sudo apt-get install <program name>"
webmin is used to configure the options mainly

---

### Post by rgotten on 2008-05-16
Ok, i was playing yesterday with installing samba thru webmin and following some instruction on how to configure, few questions:
1) IP adresses of the computers: i have 3 wired 1 wireless conected to a linksys router. Maybe is a dum question, how do i found the ip address of the computer. my internet by the way has a static ip.
2) Why they mention all the time Unix on Webmin...?
3) Part of my playing and configuratiuon, i was able to connect to the server and under /home created a folder clled test. Then i try to pasteor save some documents and it said, "access denied" I thougth i gave all the permitions, but maybe not...Any suggestions?
3)What do you think about this: [http://ubuntuforums.org/showthread.php?t=795914&goto=newpost](http://ubuntuforums.org/showthread.php?t=795914&goto=newpost) i found this all the time back and for.

Is there any 123 easy instruction on how to configure SAMBA, i look at the instructions of ubuntu desktop but still i guess iu am missin some of the therminology that i need to understand, and also how is LDPA compared to SAMBA
4) Why FTP compare to a web base interface?

Thanks my friend

rgotten

---

### Post by imon9 on 2008-05-16
(1) to find out about your IP adress, you can either simply log-in to your linksys router and see the rcorded log.. (usually the DHCP sever reserved the adress while the computer is connected)

other way is to go to each computer (i assume in your case, is all MS windows, right click on the "connection" icon on the right-lower corner of your taskbar. Choose "properties" and click on "detail/advance")

(2) Linux is one of unix system.. so, just assume unix=linux

(3) access dinied may be due to your apache virtualhost setting of your apache. Maybe u did not add the virtual host correctly. To check:

open the file: /etc/apache2/sites-available/default
using the command "sudo nano /etc/apache2/sites-available/default"

```

NameVirtualHost *


<VirtualHost *>
	ServerAdmin webmaster@localhost

	
	DocumentRoot /home/(username)/test/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/(username)/test/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

u can copy paste the whole thing to it (deleting the earlier settings)
(decide yourself if u wana backup beforehand!!!)

other thing is to change mode on the folder & each file u put into it to at list mode 744
(note that each file u copy into a readable folder doesnt mean the file itself is given permission to be view. Each individual file has its own permission

of course, u can select multiple file and chmod 744 them all at the same time.

(3) LDPA is for sharing 1 printer among several computer in the local network
SAMBA is sharing of files/folders

(4) why FTP? coz FTP has built-in security (eg: u must have user-name & password to access files)

HTTP (apache/LAMP) let u access right-away. Unless u design your own login system... which takes more learning to do

---

### Post by rgotten on 2008-05-25
I have being out and that is why i have not contact you before. In reference to tha IP address, i check the router and I have a modem bridge to my router, the router is on pppoe mode, I know also i have a static ip address, do i have to change the setting to DCHP on the router or i do this on teh server?, if yes how do i do this?

Thanks

rgotten

---

### Post by imon9 on 2008-05-26
well, your router (while acting as DHCP server...pss..dhcp server is the server/program that identify a connected pc and give them an IP automatically)can assign static local adress to each computer by reserving the IP for each MAC adress.(MAC adress= hardware ID for each lan card)

anyway, IF you are sure u have static IP, then your current setting should be fine as long as everyone is in the same IP domain. Nothing need to be change.

with this, you will see each other in "my network neighbourhood"

---

### Post by rgotten on 2008-05-27
> **imon9 said:**
> well, your router (while acting as DHCP server...pss..dhcp server is the server/program that identify a connected pc and give them an IP automatically)can assign static local adress to each computer by reserving the IP for each MAC adress.(MAC adress= hardware ID for each lan card)

anyway, IF you are sure u have static IP, then your current setting should be fine as long as everyone is in the same IP domain. Nothing need to be change.

with this, you will see each other in "my network neighbourhood"

i do not know if i miss comunicate: i know i have static ip address since i requested about a month ago and i know which obe is it. the odem is on bridge mode with the router, so the router is on PPPOE, so at the present moemnt is as PPPOE not as DHCP, Know if i go to each computer i still can not find a ip address. Maybe i am doing somethinbg wrong?, the log on the router is disable, i will turn it on to see if can find any ip adresses..any other ideas?

rgotten

---

### Post by imon9 on 2008-05-28
hahaha...we did not miscomunicate.. just a bit unclear i guess:

(1) your ISP may or may not provide you with static IP. This IP is called the "external IP". If your ISP say they gives you static IP, that means, you have static "external IP"

(2) the outside world or ppl from internet finds u by connecting to you "external IP". However, nowadays, ppl just need to type URL, instead of IP thanks to DNS. DNS redirect the correcponding URL to your external IP.(ISP provide DNS along with your regualar internet connection)

(3) however, since u have a local network that connects to the internet with only 1 internet connection. So all computer can be excess from internet by your external IP. However, your router will not know which computer other ppl try to access, beacause, all of you have the same external adress!

(4) that is why, the router give you an"internal adress" like 192.168.0.3, 192.168.0.4 or 10.0.0.5, 10.0.0.6 etc. In order to do this, the router has a built in DHCP server (the program that given each computer an "internal IP")

of course, some really old computer doesnt hav this DHCP,so in older days, ppl will have to put in IP manually on each computer.

(nowadays, ppl still manually put the IP adress when they dun trust the DHCP to do a good job)

and for the reson that the built-in DHCP server tend to re-assign IP adress once in a while (usually once in a week), your "internal IP" may get change automatically sometimes. That is why, i want you to reserve the IP adress according to the MAC adress (if your router has this feature. Usually, they do)


(5) so now, regardless wether yout modem connect with PPPoE or not (PPPoE just mean one type of ADSL/broadband service), i am quite certain you have a built-in DHCP in your router if you never knew about things like setting IP adress. Because by default, router turn on the DHCP, so that user can just simple plug in a line and get online without any hassle of setting up stuff.

(6) now, to get your IP adress on windows xp: run "cmd" or open DOS prompt
type in "ipconfig" or "ipconfig/p"

you will see your "internal IP adress"

(7) in order to know your "external IP", you can just go to this website: [http://www.whatismyip.com/](http://www.whatismyip.com/)
it will display your IP on the page

---

