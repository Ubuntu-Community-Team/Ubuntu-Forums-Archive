---
title: "First Time Networking - Help Needed :)"
date: 2009-01-14
forum: Server Platforms
---

### Post by jhonnyboy on 2009-01-14
hello everyone. I recently took on a project because i thought it might be fun and gain experience. A friend of mines is opening up her business and has asked me to network her computers. She will have 4 workstations and a server.

I would like the workstations to save all their work on the server hdd and if possible deepfreeze their computers.

I am planning on running ubuntu server on the server machine, but yet im a little nervous first because i have never done such a "big" network like this and two because i just installed ubunutu on my personal machine about 2 days ago so im still fairly new to this.

All 4 workstations will be running Windows Vista Sp1 the server comes with this OS as well. 

So finally...my question is: 
1. What do you guys recommend i do? 
2. Is it hard to do a network with ubunutu server os?
3. Any other tips you guys can give me? Should i read a tutorial or anything?

I appreciate any help i can get. Thanks again everyone :)

---

### Post by Titan8990 on 2009-01-14
Is a fileserver all that the require of the Ubuntu server? "Networking" them together is as easy as putting all in the same networking device on the same network address.

Getting them to function together is a different story.

---

### Post by jhonnyboy on 2009-01-14
I believe that is correct. Up to now it will be a file server. How difficult can this be? Correct me if I'm wrong. What I'm thinking that i have to do is install ubuntu server edition, then just place the hdd on the network so that every workstation can access it and save their files into that hdd. How i do this in ubuntu that is another question. I have no idea lol

---

### Post by Titan8990 on 2009-01-14
To host files to Windows clients you need SAMBA. SAMBA is available in synpatic and can be installed with:


sudo apt-get install samba


Configuration files for samba will be placed in /etc/samba


This guide is ok but a couple things I need to point out: [http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)


1) DO NOT UNLOCK THE ROOT ACCOUNT

You can log in to root in a more tradition manor using the command: sudo -i

2) DO NOT FORMAT A DRIVE IN NTFS

Other than that the guide is decent.


Good luck!

---

### Post by jhonnyboy on 2009-01-14
thanks for the help :) so i did some research on samba and what i have come to understand is that it allows windows and linux OS to communicate with each other in order for file/printer sharing to occur. Please correct me if i'm wrong. Another question, what does apt mean?

[CENTER]sudo **apt**-get install samba[/CENTER]

I know sudo is like super admin right?

I am feeling a little better now but i still have some questions. Once I managed to install samba and network all the computers then i shall begin the file sharing step.

How can i place the server hdd on the network so that the windows workstations can see it?

Also how can i set limits on the users of the workstations? For instance when they log in they can't click on My computer, go into the registry and etc...is there a section in the ubuntu server os were i can set such restrictions?

Thank you so much for everything guys

---

### Post by Iowan on 2009-01-14
**man apt** reveals apt = Advanced Package Tool. It's a package manager - serving Debian/Ubuntu family similar to Red Hat's RPM tool. 
You *should* be able to place server "shares" on the network where Windows computers can find them... though there seem to be some rough edges at present.

HAve you seen these Samba pages?
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://oreilly.com/catalog/samba/chapter/book/index.html]("http://oreilly.com/catalog/samba/chapter/book/index.html")
[http://samba.netfirms.com/]("http://samba.netfirms.com/")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by albinootje on 2009-01-14
> **jhonnyboy said:**
>  What I'm thinking that i have to do is install ubuntu server edition, then just place the hdd on the network so that every workstation can access it and save their files into that hdd.

You should realise that the Ubuntu server installation cdrom will give you only a text console after the installation.
Since you're new to Linux networking that's perhaps not what you want.
But you can install webmin to do the Samba configuration via a web interface. [http://webmin.com/download.html](http://webmin.com/download.html)

Important to do during the setup of Samba :

* make sure the workgroup is the same on server and clients
* do realise that you will need at least one "samba user", which should have the same name as an already existing "ubuntu user"

Another alternative is that you install the Ubuntu desktop edition, and set up Samba on that.

Use this [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) to test your Samba setup.

---

### Post by jhonnyboy on 2009-01-14
> **albinootje said:**
> You should realise that the Ubuntu server installation cdrom will give you only a text console after the installation.


Whoa! Good thing you let me know. That makes things sound a lot more difficult then what i was planning. So your saying after i install the Ubuntu Server OS it will be text only and no GUI will be available? Just wanted to get that straight. That is not a problem, it's just going to be a lot more difficult and i will need to learn the "terminal's syntax" a lot faster that what i was expecting. Do you guys have any website that can give me the basic commands for it? 

So once i install the ubuntu server all i have to do is install samba then configure samba to help me with the sharing of files/printers correct?

and here is a dumb question...What is the ubuntu server os good for then if all i need it for is to install samba to share the files/printers on the windows workstations. In the ubuntu server os can i modify windows workstations privileges?

Thanks guys and sorry about that last question. I'm learning :)

---

### Post by albinootje on 2009-01-14
> **jhonnyboy said:**
> Whoa! Good thing you let me know. That makes things sound a lot more difficult then what i was planning. So your saying after i install the Ubuntu Server OS it will be text only and no GUI will be available? 

Correct.
> 
Just wanted to get that straight. That is not a problem, it's just going to be a lot more difficult and i will need to learn the "terminal's syntax" a lot faster that what i was expecting. Do you guys have any website that can give me the basic commands for it? 

For a fast setup, you only need to know how to install webmin.
That would be the following :
```

wget -c http://prdownloads.sourceforge.net/webadmin/webmin_1.441_all.deb
sudo dpkg -i webmin_1.441_all.deb

```
After that is installed successfully point a web browser to :
[https://your_samba_server_ip:10000](https://your_samba_server_ip:10000) and log in, and configure all.
> 
So once i install the ubuntu server all i have to do is install samba then configure samba to help me with the sharing of files/printers correct?

Yes.
What printer brand and type is it ?
> 
and here is a dumb question...What is the ubuntu server os good for then if all i need it for is to install samba to share the files/printers on the windows workstations. 

Sorry, I don't understand what you're asking here.
Can you rephrase this question please ?

> 
In the ubuntu server os can i modify windows workstations privileges?

You can modify the samba users, and you can modify the shares on your Samba server.

Related to your setup you can do with Samba the following things :
1) Just let the clients use the share(s) on the Samba server.
   You will need at least one samba user on your Samba server.
2) You can offer shares and authentication with a Primary Domain Controller. 
With workstations joining the Windows Domain, and users logging in at the Domain.

One advantage of having your Samba server act as a PDC is that the users log in, and that they don't have to fill in passwords for the shares after that.
Without the use of the PDC you probably have to set up a bat file which auto "maps network drives" for the shares, unless there's some other solution, or perhaps this depends on the Windows version. I'm not a Windows user at all (never was), so I might miss some handy information here perhaps. 

Hopefully others can add or correct information.

---

### Post by lightningrod66 on 2009-01-15
You might look at the thread I started several days ago.  There could be some interesting things for you there.  I was in your shoes (sort of) when I started the thread.

I now have an Ubuntu 8.10 server on the same network as 2 WinXP Pro SP3 machines and I can share files/printers.  My goal was to setup a webserver, but it could also be used as a fileserver.

Good Luck!

[http://ubuntuforums.org/showthread.php?t=1036606]("http://ubuntuforums.org/showthread.php?t=1036606")

---

### Post by jhonnyboy on 2009-01-15
Ok thank you for all the help guys. 

First off what is a webmin? Isn't that based off of a Web Based Interface? So this would be a web server correct? What are the differences between a web server and a file server?

I will be having 4 workstation computers running Vista Home Edition. Only 2 out of the 4 will be able to connect to the Internet(not including the server).

My previous question is, What is the ubuntu server os good for?
Can i set restriction on the Windows workstations like their privileges and group user policy and such via the ubuntu server?

Another question, do you guys know of any free Deep Freeze software that would work with the ubuntu server os?

---

### Post by albinootje on 2009-01-15
> **jhonnyboy said:**
>  First off what is a webmin? Isn't that based off of a Web Based Interface? So this would be a web server correct? What are the differences between a web server and a file server?

See here : [http://webmin.com/index.html](http://webmin.com/index.html)

With webmin you can also configure apache.
Apache is the most used webserver software on the Internet.

A file server is serving files to clients where they can download and upload and edit files.
A web server often offers only downloads for the normal users, although with some "add-ons" uploading and editing is certainly possible

And.. a web server can easily be public on the Internet, with a file server that's usually not wanted.

---

### Post by jhonnyboy on 2009-01-15
thank you for explaning that for me.

Ok then i am shooting for a file server. Can that be easily accomplished with Ubuntu server + Samba?

What do you guys recommend?

---

### Post by Titan8990 on 2009-01-15
SAMBA would be the choice for local network file sharing when you have Window Clients.

If you are looking to share files over the internet, look at apache + WebDAV.


A Ubuntu server should work fine.

---

### Post by jhonnyboy on 2009-01-15
ok one small problem i have come to understand that with the Windows Vista Home Edition OS(the OS my workstations are running) that i can't connect to a "domain." Being my first network i have no idea what this means. I know the other OS of windows business+ can connect to the domain. Can someone please explain that concept to me?

Another question does this still apply even if i'm not using a Windows Server OS. If i use the Ubuntu Server Os+ Samba the workstations won't be able to connect?? 

Thanks guys!

---

### Post by Titan8990 on 2009-01-15
Only Vista Business editions and higher have the ability to join a domain. This is entirely a money scheme.

You don't need a domain to share files. You can use a standard workgroup.


A domain is used in businesses to manage large numbers of users, computers, and servers. It is basically just a permission management database.

It is completely unnecessary for your scenario.

---

### Post by jhonnyboy on 2009-01-15
ok so i shouldn't be worried about joining them to a domain. 

I still don't understand that concept though. Can you point me to any links were i can do a bit of research? or what do i "google"

---

### Post by albinootje on 2009-01-15
> **jhonnyboy said:**
> ok so i shouldn't be worried about joining them to a domain. 

I still don't understand that concept though. Can you point me to any links were i can do a bit of research? or what do i "google"

I've tried to explain you one part of the difference in comment #9 of this thread. ;-)

With Samba acting as a PDC where the clients can "join the Domain" where they can have roaming profiles, and the clients can be using the shares as mapped network drives without having to fill in passwords again, because that can all be done with a netlogon script from the Samba server.

---

### Post by jhonnyboy on 2009-01-15
Thank you all for helping me out and giving me a better understanding on everything. I shall be in contact when more questions arrise :) Thanks again!!

---

