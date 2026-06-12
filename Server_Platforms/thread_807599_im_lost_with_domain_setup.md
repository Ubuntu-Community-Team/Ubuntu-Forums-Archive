---
title: "im lost with domain setup"
date: 2008-05-25
forum: Server Platforms
---

### Post by 565Customz on 2008-05-25
im tryin to figure out how to do this before i pay someone to store my info..

i bought a pretty sick computer with 300gigs of memory and two nic ports  so i was thinking of using it as a server. i would like to go ahead and set up a website for my business but i want to store the data locally for the site. instead of on someone elses server.   i assume the first step is to buy the domain name...which is done.

so now for the hosting....

and thats where im lost lol...any guides availible?

---

### Post by 565Customz on 2008-05-26
maybe i should change the thread title to..im a dumb a$$ help me lol

---

### Post by 565Customz on 2008-05-26
ok...is there someway i can mae the question better?

---

### Post by windependence on 2008-05-26
OK the hosting is what you want to do. You will need to set up at least Apache web server on your box. I'm not trying to solicit my services here but this is what I do for a living. If you are completely new to Linux, it's gonna be a bit of a steep learning curve for you. I can help you if you want, and I am sure there are also some people here who can point you to some good tutorials for loading Apache. 

After that you need to still develop your site which is yet another steep learning curve. You may want to farm that out to someone.

Once all that is done, you will need to point your domain at your IP address for your site. This is done through your domain registrar.

Anyway, ask questions and I will be happy to answer them for you.

-Tim

---

### Post by 565Customz on 2008-05-26
hey tim! thanks for the reply.

im much obliged for your help.

im not at all schooled at how to actually connect the page-pages to the net. my cousin has software he uses to do the actual page design so that shouldnt be a problem. i need the help in setting up the server.

im tryin to do some reading, but im not sure what all this stuff means like DNS, Lamp, etc etc....but im i real quick learner  lol. i found this guide here...


[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3)

and if you think that is a good starting point for doing the installs, then ill get on it and let you know when i have problems

also i need to make sure it is secure...there isnt going to be money changing hands, but i have patent stuff for my engine that  only needs to be shared between me and the CNC machine guys. (hence the reason i want my own server) 


domain is 565Customz.com

i registered with google through eNom



______________________________-

hardware stuff

the computer im using has 3 drives for a total of 280 gigs. along with a core duo processor 4 gigs ram and 2 NIC cards. ( i bought it for 50 bucks to lol)   is there anything in particular i should do with the hard drives or cd rom drives?  i was going to use one drive as a windows platform because it still has the dvd burners in it and xp pro. i assume i could just load grub and restart the server and select that partition/drive....( i have that on my laptop, dual boot xp/ubuntu but on the same drive.)

what do you think? should i just make it a server and leave it alone? 

sorry bout the long post, just firgured i  should give you all relevant information

---

### Post by 565Customz on 2008-05-26
i havent installed ubuntu server yet cause i wanted advice on what i should do with the drives.

---

### Post by windependence on 2008-05-26
You would get several different opinions, but if it was me, I would set up LVM and use the first two drives as space for the webserver, and the other drive to keep backups. You certainly wouldn't want to be dual booting Windoze on that machne if it's gonna be your business server.

My advice really? You want security and you want it to work well all the time? I'm not being funny here but my opinion is you should get a professional, and not some kid doing it for $10 and hour either. That's just my personal opinion, but if you wanna learn, I'll be here along with the other folks on the baord to help you. I just think you might be biting off more than you can chew on this project.

-Tim

---

### Post by ruiruas on 2008-05-26
Hi,
about having a "windows platform" you certainly know that you can not restart into windows and still have the linux webserver online :-).
So, I don't think it's a good idea to waste time over that. What you can do is install the linux webserver, a graphical frontend like gnome and then run windows as a virtual machine (with vmware or something). Later, if you need help with that, I'll try to help.

Now: For a webserver, you should have your system in at least a full raid1  setup. That way, when the hard drive fails you don't loose the site. During installation you should create equal size partitions on two disks and set them up to "use as linux software raid". after that (still in the partitioner) you create the raid disk arrays, joining the partitions two by two and formatting the arrays as ext3 or other.

You can do many different things, but a simple and effective setup is this (it will give you space to spare!):

/boot - 200MB
swap space - 2GB
/ - 10GB
/tmp - 100MB
/var - the rest (for a tipical webserver)

opcionally, if you want to use it also as a PC, you can have a partition for "/home" where you can save your "things". If you want to keep it simpler, you can have one partition for / , swap space and another for /var (its where apache stores websites by default)

About the software, you can choose the "Install a LAMP server" (linux, apache, mysql, php).

The other thing you need to take care of is your IP. hosting a domain involves either having a "fixed IP" (best option - you'll have to pay for that service to your ISP provider) or a dynamic IP mapped to your house by another service like DynDNS, NoIP or other (google for it...).

After setting up the IP issue, you'll have to redirect your "domain name" to the specific IP you want (you can take care of that with your domain registrar), so that the information is spread in the internet by the DNS servers and other machines can find your server.

I don't know if I'm being too basic for you, but anyway I hope this helps.
Regards,

---

### Post by ruiruas on 2008-05-26
Hi again,
the linux community is allways available to help :-D but...

> "I just think you might be biting off more than you can chew on this project."

I also think "Windependence" may be right...
If you're just starting, this can be a little too much for you.

---

### Post by windependence on 2008-05-26
> **ruiruas said:**
> Hi,
about having a "windows platform" you certainly know that you can not restart into windows and still have the linux webserver online :-).
So, I don't think it's a good idea to waste time over that. What you can do is install the linux webserver, a graphical frontend like gnome and then run windows as a virtual machine (with vmware or something). Later, if you need help with that, I'll try to help.

Now: For a webserver, you should have your system in at least a full raid1  setup. That way, when the hard drive fails you don't loose the site. During installation you should create equal size partitions on two disks and set them up to "use as linux software raid". after that (still in the partitioner) you create the raid disk arrays, joining the partitions two by two and formatting the arrays as ext3 or other.

You can do many different things, but a simple and effective setup is this (it will give you space to spare!):

/boot - 200MB
swap space - 2GB
/ - 10GB
/tmp - 100MB
/var - the rest (for a tipical webserver)

opcionally, if you want to use it also as a PC, you can have a partition for "/home" where you can save your "things". If you want to keep it simpler, you can have one partition for / , swap space and another for /var (its where apache stores websites by default)

About the software, you can choose the "Install a LAMP server" (linux, apache, mysql, php).

The other thing you need to take care of is your IP. hosting a domain involves either having a "fixed IP" (best option - you'll have to pay for that service to your ISP provider) or a dynamic IP mapped to your house by another service like DynDNS, NoIP or other (google for it...).

After setting up the IP issue, you'll have to redirect your "domain name" to the specific IP you want (you can take care of that with your domain registrar), so that the information is spread in the internet by the DNS servers and other machines can find your server.

I don't know if I'm being too basic for you, but anyway I hope this helps.
Regards,


Sorry but I disagree with you on so many levels of this post. This guy wants to run a BUSINESS web server, not a hacked up home server. 

First off, even if he should run RAID, and RAID is NO substitute for backups, I sure wouldn't be running software RAID on a mission critical machine. It's just too hard to recover from and not reliable enough.

Running a GUI on the server is also not recommended. If he wants to run Webmin or something similar from a different machine, fine, but a GUI is not really server material for a production machine. 

Dynamic DNS will work, but when I started running my production severs 5 years ago I quickly found out that many places with internet access block redirected sites so a ton of people could not access my site. People especially accessing it from their companies could not get to the site. It's just not enterprise material so he really should get his own private IP.

What you are suggesting is OK for a home server that is not mission critical, but in his case, he needs 24/7/365 relaibility, especially if customers are accessing the site.

-Tim

---

### Post by 565Customz on 2008-05-26
wow guys..thanks for all the advice. 

i understand this is alot to learn but im not hard pressed to have it done in a week and as i said...im a fairly quick learner.  

so...this is what ill be doing 

first, formatting all the drives back to factory specs,  one large one will be for backup and ill use the other two for storage.  should i keep the drives seperate or make one partition or what? (i wont worry bout the dual boot, ubunutu is way better anyway)

second i have a dynamic ip now, but as soon as a get a chance ill call time warner and have a static ip setup. i already have a 10g down/2g up connection.  ( i know its not the greatest but itll work i suppose) 

i have a couple of pages i can load as a test and to learn some of the procedures.

agian i know im a complete newb, but i definitely want to learn, and you gotta start somewhere right?

---

### Post by 565Customz on 2008-05-26
ok so this doesnt make any sense, but  time warner said that you have to have dsl to get a static ip through them....? im on hold waiting for someone else cuz that just dont sound right lol. i have broadband so  i may have to use one of those dynamic server sites

---

### Post by 565Customz on 2008-05-26
getting a business acct so i can get a static ip. web hosting isnt allowed on the home accounts

---

### Post by windependence on 2008-05-26
> **565Customz said:**
> getting a business acct so i can get a static ip. web hosting isnt allowed on the home accounts

Try to get an up speed of more than 1.5 mps. that should be plenty for what you need.

On the drives, if you have information spread over one big partition and your stuff gets hosed, it's harder to fix it unless you are running LVM and have some free space somewhere. Still, it's much simpler to keep your partitions separate. And make sure you make a separate /var partition as that is where your logs are stored and if you allow them to fill up without a separate partition, it will crash your machine.

-Tim

---

### Post by 565Customz on 2008-05-26
thats cool...my home acct is faster than that lol..if these guys would take me off hold i could order somethin lol.

can i put the /var on the drive with the backups? that'll increase secruty a little wont it?


will lvm  cover seperate drives? or will i need to set one up for each drive?

---

### Post by windependence on 2008-05-26
Well /var will be where your web files are usually so no I would put it on the production drive, just make a separate slice for it so if it fills up it won't hose the system.


-Tim

---

### Post by 565Customz on 2008-05-26
right on. they just changed my ip adress and knocked my off line lol...while i got them on the phone tryin to do it the legal way...lol

so on the partioner i need 

/
/var 

on the same drive correct?

what do i name the second driveand third drives?  or will the installer set all this up for me?

by the way thanks for the help!! imma have to cut you a check when were done lol

---

### Post by windependence on 2008-05-26
> **565Customz said:**
> right on. they just changed my ip adress and knocked my off line lol...while i got them on the phone tryin to do it the legal way...lol

so on the partioner i need 

/
/var 

on the same drive correct?

what do i name the second driveand third drives?  or will the installer set all this up for me?

by the way thanks for the help!! imma have to cut you a check when were done lol

When you get to the partitioner you will need to do a custom partition. the installer will just set it up on one drive if you let it walk you through it. I found out the hard way.


BTW, I will not be back on the forum for a while until about 6 pm pacific time. Sorry, get back to ya then!

-Tim

---

### Post by 565Customz on 2008-05-26
thats cool...i can do the seperate partiotns. i know how you to use editor im just not sure how to make it do all the drives. I Can make it do one drive no problem though lol

---

### Post by 565Customz on 2008-05-26
dang tim...i for got to do the /var. i only partitioned my largerst of the three drives and i used the guided...so it didnt ask me..i did select guided and set up lvm though...

i got a whole lot of errors bout corrupt files and stuff...

u burned the iso file to cd, and i burned it at 24x 

now what

---

### Post by windependence on 2008-05-27
> **565Customz said:**
> dang tim...i for got to do the /var. i only partitioned my largerst of the three drives and i used the guided...so it didnt ask me..i did select guided and set up lvm though...

i got a whole lot of errors bout corrupt files and stuff...

u burned the iso file to cd, and i burned it at 24x 

now what

If you got errors about files being corrupt on the cd, then you might want to check the md5sum of your .iso file and makes sure it's a good image because that will surely hose your install even if it finishes.

-Tim

---

### Post by 565Customz on 2008-05-27
yeah i think im just going to make it work witht eh desktop edition until i get my server cd in the mail.

i just used one of the drives right now and finally got an operating system at least

---

### Post by ruiruas on 2008-05-27
> **windependence said:**
> Sorry but I disagree with you on so many levels of this post. This guy wants to run a BUSINESS web server, not a hacked up home server. 

First off, even if he should run RAID, and RAID is NO substitute for backups, I sure wouldn't be running software RAID on a mission critical machine. It's just too hard to recover from and not reliable enough.

Running a GUI on the server is also not recommended. If he wants to run Webmin or something similar from a different machine, fine, but a GUI is not really server material for a production machine. 

Dynamic DNS will work, but when I started running my production severs 5 years ago I quickly found out that many places with internet access block redirected sites so a ton of people could not access my site. People especially accessing it from their companies could not get to the site. It's just not enterprise material so he really should get his own private IP.

What you are suggesting is OK for a home server that is not mission critical, but in his case, he needs 24/7/365 relaibility, especially if customers are accessing the site.

-Tim

Hi windependence,
1-of course software raid is not a substitute for backups (I didn't say it was!), but it will keep your system running in the event of a drive failing. Plus: if I understood correctly, there isn't a lot of money to spend on expensive true hardware raid cards... if you compare software raid to the fake raid of most cheap cards and if you know anything about hardware, you also know what's best...:-)
2-software raid is a lot easier to recover from (and a lot safer) then lvm...
3-I didn't suggest a GUI... I was only answering to him. And of course I agree that a Gui isn't needed on servers (but if he needs it...).
4-As for dynamic DNS, I only pointed that it is a possible (cheap) solution, but if you read my post you'll see that I also recommend the static IP (again: of course!)

peace,

---

### Post by NateMan on 2008-05-27
Are you sure that going with the desktop edition? I mean why not wait or try the download again. I imagine that your download was corrupted or incomplete. Of course you could just have it temporarily run your website that way, then backup your site and reinstall. More work than I'd want to do though.

---

### Post by 565Customz on 2008-05-27
i got another large drive that i havent touched and when the cd comes int he mail ill back up the site and swap it over...plus until that disk gets here im learing alot and that gui is useful. when i get the server cd ill install xubuntu gnome.   

and i gotta say, in two days...i have learned ALOT...my head hurts lol

---

### Post by NateMan on 2008-05-27
xubuntu isn't gnome. xubuntu is a distro of ubuntu that uses xfce as a windows manager. I still think you should try no gui, guis are really just a crutch, and as many have said, what do you do when it gets completely hosed? Guis hose faster than anything. Besides that guide you used wasn't really designed for good server usage as it uses the desktop kernal. Plus when you go with your server cd your going to get a cli interface and then you will have to install a gui over it which you will then need to set to not run all the time, at least that would be preferable. You'd have to set it to run level 3. Have you thought about using webmin? You'd find it very easy to use and it does provide (in my opinion) a much more useful server gui. you can download the .deb from [www.webmin.com](www.webmin.com) and then install it. I believe there is one package you will have to install before hand. It will tell you want in an error. Seriously, check out webmin, I am sure you will be very happy.

---

### Post by 565Customz on 2008-05-27
is webmin just for the server edition or can i use it now while im playing around chasin my tail? thanks for the advice..

everyone at works (te it guys) keep tellin me to go with windows, its easier, but usinglinux i kinda feel like im getting in on the ground floor of something...(ok maybe 2nd or 3rd but you get my point lol)

---

### Post by NateMan on 2008-05-27
wow don't listen to the windows guys. They are just unable to do linux. They're probably not very high-level it guys, as the better quality it workers normally recommend linux... Also unix servers have been around for decades longer than windows. Linux has been around as longer than windows servers as well, it just had a huge learning curve before, where as now its being made more idiot-friendly.

Yes as far as I know webmin will work on the desktop version. You may need another package or two, but it will let you know.

---

### Post by 565Customz on 2008-05-27
idiot freindly lol...its just amazing at all the stuff you have to know in order to get something done..all i want is a mail server, and a webserver, and i want it to be secure..is that really alot to ask lol

oh and no that arehigh level it guys...im military and all the guys im talking to are senior airmen or staff sergeants....they know enough to set up military networks...and guess what they run on lol

---

### Post by NateMan on 2008-05-27
I'm a DoD network admin and we use linux. Linux is very  idiot proof lately, maybe you should read some information from the early thousands? In fact I know almost all classified/sensitive computing is done on unix based systems due to the security. I've noticed a pro-windows push in the military lately that I just don't like. And senior staff sargeants and airmen are not normally college grads from what I understand from MY airforce buddies in intel. Normally that level of IT in the airforce is reserved for much higher level stuff. I mean you can't even get into the cybercrimes part of the airforce with out a degree and going in as an officer. But enough about military networks and their setup. 

But seriously, you should try following a GOOD guide like the ubuntu perfect server 8.04. Then take that and install webmin on top of it. It will do exactly what you've said you needed flawlessly. I really recommend it for first time server setups.

---

### Post by 565Customz on 2008-05-27
thats the guide i was tryin to follow but as i said i couldnt locate a good iso file..so i did it this way. my last shipit cd didnt take to long to get here though so..well see.

---

### Post by windependence on 2008-05-28
> **565Customz said:**
> idiot freindly lol...its just amazing at all the stuff you have to know in order to get something done..all i want is a mail server, and a webserver, and i want it to be secure..is that really alot to ask lol

oh and no that arehigh level it guys...im military and all the guys im talking to are senior airmen or staff sergeants....they know enough to set up military networks...and guess what they run on lol

I N C O M I N G ! ! 

" Oh *****, reboot!"

Sorry, couldn't resist. I had heard the DOD may be changing all that and dumping Windoze. I know they don't run the big stuff on that platform.

-Tim

---

### Post by NateMan on 2008-05-28
that's rather odd that you can't download a good copy. I've only had that problem once, and it was a bad download, not the hosted file's fault.

---

### Post by 565Customz on 2008-05-28
> **windependence said:**
> I N C O M I N G ! ! 

" Oh *****, reboot!"

Sorry, couldn't resist. I had heard the DOD may be changing all that and dumping Windoze. I know they don't run the big stuff on that platform.

-Tim

hahaha

i heard that to..but there is to much relying on it now i think


i downloaded an iso from 6 different servers and burned about 10 copies and not one would work....??? i dont know..i cant seem to get the torrent to get me one either so i was just like whatever lol ill wait a couple weeks...like i said im just learning by doing it this way..

with webmin you haveto give it a security exception to allow it to access the server...ill remove the exception when i get it configured

---

### Post by windependence on 2008-05-28
> **NateMan said:**
> I'm a DoD network admin and we use linux. Linux is very  idiot proof lately, maybe you should read some information from the early thousands? In fact I know almost all classified/sensitive computing is done on unix based systems due to the security. I've noticed a pro-windows push in the military lately that I just don't like. And senior staff sargeants and airmen are not normally college grads from what I understand from MY airforce buddies in intel. Normally that level of IT in the airforce is reserved for much higher level stuff. I mean you can't even get into the cybercrimes part of the airforce with out a degree and going in as an officer. But enough about military networks and their setup. 

But seriously, you should try following a GOOD guide like the ubuntu perfect server 8.04. Then take that and install webmin on top of it. It will do exactly what you've said you needed flawlessly. I really recommend it for first time server setups.

Hey Nate, what have you heard about using ebox instead of Webmin? I had heard it was more secure but doesn't have some of the features of Webmin.

-Tim

---

### Post by NateMan on 2008-05-28
Yeah, they converted a buddy of mine's workstation stuff to windows for a few months and switched right back to solaris after just a bit. I know we don't encourage windows use among us. The only scientists that use it normally are biologists using specialized software. And our windows setup is worlds easier than most due to a piece of software called altiris. Plus all of our accounting/business people are stuck in windows as well. But for serious research, there is no windows.

---

### Post by NateMan on 2008-05-28
no I haven't. I'll look into it. I have been looking for new toys to play with.

---

### Post by 565Customz on 2008-05-28
yup...im still lost...i just dont get it...:(  


i dont even understand what i dont unerstand...im going to sign up for classes...

---

### Post by NateMan on 2008-05-28
why pay money to learn? besides most of what you don't know and don't understand that you don't know is probably general networking type stuff. That's a great place to start learning about your server. Learn how networking works and setting up a linux or even a windows server is worlds easier. Then from there you can start learning linux specific stuff. A good foundation is key to proper networking/server usage.

---

### Post by 565Customz on 2008-05-28
what i dont get is...where do all the numbers come from and go...when i say numbers i mean, subnet mask, ip address, host server names...i can find all of it out i  just dont get where to plug it in at?

---

### Post by NateMan on 2008-05-28
ok you have several ip addresses in your local network, those are private addresses only seen from within the network. These are normally 192.168.x.xxx or something like that. Then there is a public ip address which points on the internet to your router itself, and from there to your server. subnet mask for you is probably just 255.255.255.0, so I wouldn't worry to much about that at this stage. Host server name is the name of your server. You need to attach it to an ip address on your private network. This is all set in your /etc/network/interfaces. You need to set that up to be a static ip address. That is illustrated in the perfect server guide, something you can still use from it even on your desktop. Check that out and go from there.

---

### Post by 565Customz on 2008-05-28
right on...i think im on the right track

[www.565Customz.com](www.565Customz.com)


try it again...its tryin to connect now atleast lol...i still dont have my html in the right spot but ill tackle that 2moro

---

### Post by NateMan on 2008-05-28
/var/www is where your webpage stuff goes.

---

### Post by 565Customz on 2008-05-28
cool thanks...i put the html where it belongs and i found a guide for apache ill be checking out. i messed something up though cuz i cant connect to the net on the server...i changed some setting i guess...

where did you say i can get that good iso for server edition?  ill start over and follow the perfect server guide...

---

### Post by NateMan on 2008-05-28
from ubuntu's website, [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) . Then you click on download and select the server edition. Then from there you get the either 32bit or 64bit. I recommend 32bit. Then you pick a mirror near your physical location and wait about 30 min to an hour, then burn, and install away.

---

### Post by 565Customz on 2008-05-28
i was using that method an i kept getting bad files..

i found another problem..i cant change my name servers on enom because i bought my domain from google....it wont let me puch the domain to my account to manage it and register a nameserver...

---

### Post by NateMan on 2008-05-28
You shouldn't get bad files from that, since people download from there on a daily basis. I would try a different server to download from. That might make your problems go away. I like the institute of technology.

---

### Post by 565Customz on 2008-05-28
i tried several
  ill try it again though

---

### Post by 565Customz on 2008-05-28
do i need a dns host from godaddy since im doing my own server? im transefering it from that stupid google crap.

---

### Post by windependence on 2008-05-28
> **565Customz said:**
> do i need a dns host from godaddy since im doing my own server? im transefering it from that stupid google crap.

You don't need to host your site at GoDaddy, just go into your domain control panel and point your site at your IP. Then set it up to use their nameservers. If you call them, their support is top notch, they will walk you through it all.


-Tim

---

### Post by 565Customz on 2008-05-29
ok thanks ill do that...but i have to wait 60 days till i can transfer to them!!! ughhhh!! im gonna buy another domain my buddy wants and set his up too though so

check my post about the server install im having trouble with. its much more detailed in the installations section

---

### Post by windependence on 2008-05-29
> **565Customz said:**
> ok thanks ill do that...but i have to wait 60 days till i can transfer to them!!! ughhhh!! im gonna buy another domain my buddy wants and set his up too though so

check my post about the server install im having trouble with. its much more detailed in the installations section


Why do you have to wait 60 days? I think that's bulls***t. You can initiate the transfer with Godaddy and they will take care of everything AND give you an extension of time for transferring. Call them and ask.

-Tim

---

### Post by neilevan814 on 2008-05-30
I am also looking to eventually set up my own business server.  I am playing around with a bogus site on my ubuntu desktop machine and dyndns.com because my residential roadrunner service is not provided a static ip option.  What I am wondering is...is what type of motherboard could I get away with...I like amd processors and also what processor and speed would be best.  I know I should set up with ECC regulated ram, but what is the best minimal ram to go with?  And as far as a power unit goes...would 300W be okay?  Thanks for any suggestions.
Neil

---

### Post by neilevan814 on 2008-05-30
When I started up my apache2 ....very barely set up mind you...intranet at best, but when I was reading from [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP), they said to disable the apache2 default page in /etc/apache2/sites-available/default and create your own page /etc/apche2/sites-available/mysite and enble that instead.  When I tried to [http://localhost/](http://localhost/) that new page showed up in my browser.  So, what is all this talk of /var/www? Here's the section I'm talking about:
o create a new site:

    *

      Copy the default website as a starting point. sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 
    *

      Edit the new configuration file in a text editor "sudo nano" on the command line or "gksudo gedit", for example: gksudo gedit /etc/apache2/sites-available/mysite
    *

      Change the DocumentRoot to point to the new location. For example, /home/user/public_html/
    *

      Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>
    *

      You can also set separate logs for each site. To do this, change the ErrorLog and CustomLog directives. This is optional, but handy if you have many sites
    *

      Save the file

Neil

---

### Post by neilevan814 on 2008-05-30
One more thing...I get a lot of help from this forum, but I do not know how to show thanks from my identifcation box to the left of my posts...does anyone know how to do that?

Thanks, lol...
Neil

---

