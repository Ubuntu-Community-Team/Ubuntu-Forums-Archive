---
title: "New to SBS and need some general advice"
date: 2010-08-12
forum: Server Platforms
---

### Post by E-call on 2010-08-12
:pHey there folks 
 
I'm pretty new to the IT field but I have 13+ years of experience building home pcs and small home networks. I am doing a job for a company (in China) and they are looking for a cost effective solution for their business. As of right now they are running roughly wired computers and about 4-5 wireless computers on an open network with no server whatsoever. Most of the users have free reign to the internet and because of this they have more or less destroyed their terminals with virus' and malware. I will be going through the process of converting these PC's to workstations for the next month give or take.
 
I am going to install a Small Business Server for the company and have decided to get Dell to build one for me and ship it.
 
This brings me to my problem. I cannot decide between choosing either Ubuntu Server Edition or Windows Small Business Server 2008 R2. I have been weighing the pro's and cons of both and I am pretty much stumped.
 
Basically I know setting up Win SBS 2k8 will be a much easier venture and get me the productivity I need in a short amount of time. But I am not so excited about the user cals to connect to the server. $800 us for the server software is not bad at all but since this is a not so large company based in China purchasing user cals for 35-45 machines is not so nice on the budget aspect. I know that SBS2k8 does not require the purchase of cals but I would like to know if I am losing out on any sort of functionality. Is SBS2k8 the route to go here?
 
Or should I just set up a Ubuntu server for the company as I know I will get better performance and scalability with this machine as well as a much more secure system. I have some knowledge of Linux and have used it on several machines but I have not touched their server software. I've read the entire Ubuntu manual and I'm not too worried about setting it up I just know it will require more time.
 
The basic jist of what we will be doing is limiting computer access to increase productivity.
 
The server is going to act as a central storage facility for company sensitive files etc so these clowns dont have to run around with USB thumb drives infecting each others PCS all day. As I said they are running a network with no server and an unsecured Wifi connection
 
Also I will be setting up a central mail system for the users with no external mail except for selected users.
 
Lastly I want to get remote access to the desktops/workstations from any terminal I may be working on.
 
So the long and short of it is I'm setting up a business server with no SQL Database. Mostly these are basic services but they are much easier to set up through WinSBS2k8.
 
So Ubuntu Server of Win SBS 2k8?
 
Please help,
 
the overly stumped
 
thanks

---

### Post by viralmeme on 2010-08-12
> **E-call said:**
> I am doing a job for a company (in China) and they are looking for a cost effective solution for their business.

What kind of business, what do the staff use the computers for?

> **E-call said:**
> I am going to install a Small Business Server for the company and have decided to get Dell to build one for me and ship it .. Basically I know setting up Win SBS 2k8 will be a much easier venture and get me the productivity I need in a short amount of time

That's an urban legend put about by Redmond. It takes less time to set up and maintain a Linux box as you can automate most of the tasks using scripts. Basically once the box is configured, you don't ever have to touch it again. I have a CD burner/file/print server here that hasn't been touched in over a year.

> **E-call said:**
> But I am not so excited about the user cals to connect to the server. $800 us for the server software is not bad at all but since this is a not so large company based in China purchasing user cals for 35-45 machines is not so nice on the budget aspect

If you build your own server, you can forget about CALs what ever they are.

> **E-call said:**
> Mostly these are basic services but they are much easier to set up through WinSBS2k8.

For the third time, no it isn't. You'll spend most of your time filling in forms and clicking in boxes, and editing REG entries and and ...

---

### Post by spynappels on 2010-08-12
CALs are Client Access Licenses and this suggests that a LTSP idea might work. This would also require a very beefy server if 50 people will be taking their desktops from it. 
Viralmeme is right, more information is required to see how Linux can help the OP, I would also agree that in most circumstances, Linux could be the better option, but without details this is impossible to qualify.

---

### Post by spynappels on 2010-08-12
Having read the original post again, I'd like to add one or two observations and questions.

will the workstations still be Windows based?

would a locked down proxy server suffice to limit Internet connectivity?

A Linux server running as Proxy server, LDAP server, File and Print Server and Mail server would seem to fit the bill based on the limited information we have and would run much better on the same spec hardware as an equivalent MS server product on the same hardware.

Just for my own info, this seems to be a big project to take on for someone with no Enterprise network or real IT administration experience. Are you confident taking on the responsibility for this size of enterprise? MS Server products do take much more administration than their desktop products and unless you are confident of how all aspects work, you could be letting yourself in for a world of headaches. Of course, if I have misunderstood, I apologise, like I said, we do not have all relevant information.

---

### Post by E-call on 2010-08-12
I am aware that its a big problem for someone with little IT experience. :(
 
I am not so worried about that as I can hire a couple IT guys here fairly cheap to do most of the initial grunt labor. Ive read the Ubuntu server manual twice over and am fairly confident that it is a superior OS to windows.
 
As it stands right now, there are a total of 27 wired computers, this is a new installation as the business is changing locations. All lan wires are allocated placed and connections are solid.
 
There will also be 3-6 wireless connections depending who is at the compound.
 
Im looking at a dell t410 i believe with around 8 gigs of ram and 2 500 gig hard drives running in raid 1.
 
The desktops will all be running either Windows XP or Windows 7 in the case of systems i have replaced or will be replacing.
 
The most important thing I need out of this server is a central file server for the workstations. They need a place to dump their company sensitive materials so they are not accessable by anyone who walks in and decides to jump on a computer.
 
All of the computers originally had been given Admin rights to the users of the terminals which I want to stop. Most of these people spend most of their time chatting on QQ or playing web based games. :confused:
 
The second thing I want to do is set up remote desktop access to Windows XP and Windows 7 terminals so I can check in to make sure they are not doing what I said above.
 
email etc would be icing on the cake but not what I need to get the thing running in 1-2 months time.
 
its about 4am here and i need to catch some sleep.
 
your input is greatly appreciated and thanks for spending the time to read my post :P
 
The more I hear the more I lean away from WinSBS

---

### Post by E-call on 2010-08-12
Reading Virals post again ill place some context here.
 
The company is around 100 employees and not all have computers or access to computers. It is a manufacturing company so much of the workforce is labor.
 
However we do have an r&d department who all use CAD to draw schematics etc. of products before they are actually produced. R&D as it stands right now is 4 computers but there will be as many as 8 in the coming months.
 
There are accouting folks, quality control, and sales departments as well. all with around 2-4 users. Each of these stations will be doing most of their work in excel.
 
The other users who will need access will be users pulling up schematics from R&D to turn them into real world products.
 
If i remove administrative rights from the end users then I should be able to solve most of the productivity problems.
 
I have done some work backing up large mainframes in the US and have toyed around with both Linux and Windows server os's but that was with a list of commands at the ready.
 
thanks again

---

### Post by spynappels on 2010-08-13
Ok, based on that, Ubuntu will do most if not all of what you require.

Shared folder for transferring docs between departments.

Squid Proxy to limit what they can access on the Net

Mail server

Authentication Server LDAP (instead of AD)

The remote desktop functions will work if you set it up as a VPN server too, but AFAIK this does require the user to allow you to access, looking at their desktop without them allowing you is maybe a difficulty. The VPN connection will allow you to access their network from any location you have an internet connection.

Your hardware spec will also very comfortably run all the above services.

---

### Post by E-call on 2010-08-13
Great thanks very much for the input its greatly apprecaited.
 
Ill download Ubuntu server here and put it on one of my workstations that arent in use to toy around and get a feel for the overalll system before I implement it.
 
I'll pop back in here in a few days to let you all know how it goes or if I get stumped on setting up these services.
 
Again thank you all for your time and input. :KS

---

### Post by koenn on 2010-08-13
> **spynappels said:**
> CALs are Client Access Licenses and this suggests that a LTSP idea might work. This would also require a very beefy server if 50 people will be taking their desktops from it.


No.
yes, CAL means "client access license", but it does not necessarily refer to Terminal Services. a CAL is a license for a user or a device that will connect to a Windows server's builtin functionality - eg. for file sharing. 
You may need *additional* CALs for extra services provided by that server (Terminal Services CAL, Exchange CAL, ...)

---

### Post by koenn on 2010-08-13
> **E-call said:**
> Great thanks very much for the input its greatly apprecaited.
 
Ill download Ubuntu server here and put it on one of my workstations that arent in use to toy around and get a feel for the overalll system before I implement it.
 
I'll pop back in here in a few days to let you all know how it goes or if I get stumped on setting up these services.
 
Again thank you all for your time and input. :KS

apart from getting a general feel for the system, focus on samba (file sharing), squid and iptables (web proxy, firewall). For mail, I've heard good things about Citadel. 


If you only have 1 server, LDAP is overkill; there's only one server that requires authentication so there's no real benifit in a central user database
It could be 'nice to have' if you want to avoid creating local accounts on the employees PC's.

---

### Post by E-call on 2010-08-13
Ive already been reading much on Samba as I knew I was going to have to use it.
 
I'll get some time into Citadel as well.
 
Now that I've got my OS pinned down I can do the real work before getting the server up and running.
 
I will most likely hire an IT guy here for help with the initial install and configuration.
 
I think I will want to set up user accounts through the server because most of the workers have a high school or lower education.  Anything I can do to make it more simple for our end users the better.
 
We will only be running server so I will have to weigh out the benefits of LDAP.
 
Im not so sure if we want to allow VPN access or not im still weighing that out right now. The company wants their files to be as secure as possible as they have had problems in the past with end users either taking the files to competitors or damaging directories etc. Allowing VPN access to a few users may be good, but as we are located in China most people will live in on-site housing.
 
So i got some more homework of course, but im pushing Citadel forward to check functionality. I just gave "Beginning Ubuntu Server Admin" book a quick look over but much of the info is from older versions and much has changed in a couple years. Ill just keep going over the 10.04 user manual and my linux bible.
 
thanks again :P

---

### Post by E-call on 2010-08-13
Deleted because its useless info

---

### Post by E-call on 2010-09-09
Alright guys I'm back thanks for all your advice so far. I ran a simple test server and things seemed to be running well.
 
So now I'm trying to map out my server and would like some advice on partitions.
 
I know Ill need a part for ubuntu and for swap.
 
should I have a seperate partition for each service? and end uop with like 7 or 8?
 
And how should I allocate this disk space.  I will be using 3 500 gb hard disks and 8 gb of ram.
 
Im thinking 8 gigs for Ubuntu, 20 for swap, and then most of my capacity will go to home for users to store files.
 
Other services will be the mail server which i think i should allocate a decent amount to.
 
Any tips before I start the work of partitioning this out would be helpful
 
thanks again guys.
:p

---

### Post by spynappels on 2010-09-09
Have a look at LVM and you can be more flexible, and it is easier to alter things down the line if required.

---

### Post by E-call on 2010-09-09
Ive been looking through it but was hoping to have a decent map set out before deployement.  Ill get more in depth into it in the next couple days here.
thanks for the input. ;)

---

### Post by E-call on 2010-09-29
hey there again,
 
just thought I would pop in here and give you guys a heads uop.
 
I have deployed my ubuntu server x64 with little to no hiccups.  My biggest problem was drive mapping. But after 3 days I have a fully functional File / Printer / SSH server running and in use. How cool is that.
 
If anyone was wondering about the material I used and read to complete this I will list them out here.
 
Beginning Ubuntu 2nd edition - was useful for general terminology for a newbie to Ubuntu / Linux.
 
Linux Bible - This is mostly for desktop use but has some good info on servers as well.
 
Samba3 by Example - I thanked the lord when I found this.
 
Samba3 Developers guide - gave me in depth info for my expanded deployment
 
Ubuntu Linux Bible - Covered specific information not covered in the standard Linux bible.
 
Ubuntu Linux Toolbox 1000+ Commands - not a lot for server specifics in here but still some useful info.
 
Ubuntu Server Guide - was my go to reference for nearly the whole deployment.
 
Everything seems to be running well and our network has increased in speed dramatically by reducing windows file sharing services. I am very happy you guys told me to go with Ubuntu over Windows SBS the OS is lightweight and powerful as well as incredibly fast. My server is sitting under 20% resources being used.
 
I did drop some services from the server and pushed them to other hardware solutions such as a hardware firewall for limiting internet access. I can do remote desktop from my laptop. And I can access my server from anywhere in the building through Putty (i love putty).
 
I am going to be dropping in a few weeks down the road the give any pertinant status updates.
 
I know in the coming days or weeks I will need to figure out a way to automate system backups to a zipped folder addressing new or recently changed files. The resources are in my texts but I'd like any info if you guys have real world situations I could learn from.
 
Thanks again so much for your help.
 
:KS
 
e-call

---

