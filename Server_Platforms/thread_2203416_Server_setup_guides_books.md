---
title: "Server setup guides books?"
date: 2014-02-03
forum: Server Platforms
---

### Post by ally2 on 2014-02-03
Are there any good guides that walk you through the process of setting up a server from a newbie perspective
Most of the books out there and documentation I have read is pretty rubbish.
Any recipe type guides or books that show you how to get from A - B

Cheers

---

### Post by Habitual on 2014-02-03
check out [http://www.server-world.info/en/](http://www.server-world.info/en/)

---

### Post by tgalati4 on 2014-02-03
If you describe "A to B" in a little more detail, then we might be able to give you some specific procedures.  There are so many ways to set up a server and the frameworks are changing so quickly, that writing a current book is difficult.

If you just want to learn, then install *tasksel* and run that (using *sudo*) then pick the services that you want to install.

---

### Post by ally2 on 2014-02-03
Just how to get Server related stuff off the ground for example

FTP
SAMBA
How to backup a hardisk to another drive or best methods of backup
Torrent Server
Media Server

All in plain easy to understand noob friendly recipes

---

### Post by Lars Noodén on 2014-02-03
You might mean [SFTP instead of FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) in some cases.  There are some situations where FTP is still used but for many (most?) situations, it's better to go with a securable option, SFTP.  

About the Torrent, look at Transmission as one possible option. Torrents are P2P so the client and server are the same.  

In general, you have a rather good server guide for 12.04 
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

There is specialized documentation on Samba:
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by ally2 on 2014-02-03
I was thinking though considering how big the Ubuntu community is, How comes nobody has written a decent Server book when I say this most Linux books you pick them up and they waffle on about the history of Linux and why it's great then then bombard you with pages of commands and switches and reading it is just like watching paint dry.

What would be great would be a book where the author just goes right I am going to show you boys how to setup a server I will be using the following hardware then bang straight into setting up and installing including raid then the next receipe builds upon it in a logical way i.e installing tools to monitor the raid, updating the O/S installing and securing SSH

that would be awesome serious gap in the market there would save everyone the hassle of wasting hours on google researching stuff

---

### Post by Iowan on 2014-02-03
A few years ago, I reviewed two Apress books by Sander van Vugt - _Beginning Ubuntu LTS Server Administration_, and _Pro Ubuntu Server Administration_. That was for version 8.04 - I suspect there have been updates, but I haven't seen them. "Decent Server book" is in the eye of the beholder, though.

---

### Post by ally2 on 2014-02-03
Well that's old documentation dude how would that help? lol

---

### Post by Habitual on 2014-02-03
> **ally2 said:**
> Well that's old documentation dude how would that help? lol

You haven't mentioned what version of Ubuntu **you *are* running**, so how are we to know what's "old documentation" to you?

Here's "[new documentation]("https://help.ubuntu.com/13.10/serverguide/index.html")"
[https://help.ubuntu.com/community/Transmission](https://help.ubuntu.com/community/Transmission)
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
[https://help.ubuntu.com/community/SSH/TransferFiles#Secure_FTP_.28sftp.29](https://help.ubuntu.com/community/SSH/TransferFiles#Secure_FTP_.28sftp.29) (ftp is insecure, do NOT use it)
[https://help.ubuntu.com/community/MediaServer](https://help.ubuntu.com/community/MediaServer)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I'll bet most of the techniques in that stuff could be classified as "old documentation".

Let us know where you get stuck after reading those.

---

### Post by tgalati4 on 2014-02-03
You need to write your own book.  That way you can put those hours of searching the web to good use.

Some people like watching paint dry.  They actually see patterns in the paint.

Search the *NewDocs* link below for your search terms.  For instance "media server" brings up:  [https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

If those instructions are not clear, then you can post better instructions by going through the wiki edit procedures.

It takes 10 years to learn linux.  Servers are not for newbies.  There is an implicit understanding that you have spent some time with linux (10 years would be good) before attempting to set up and administer a linux server.

---

### Post by ally2 on 2014-02-03
Appreciate the feedback guys :) I will be running version 12.04 LTS

I do intend to write my own book 

" Ubuntu Server Administration For Impatient s**ts! "

synopsis fed up of wasting countless hours reading out of date documentation and ending up with nothing but headaches, Want to achieve your goal of setting up a server without tearing your hair out? Want concise straight to the point instructions without a professor given you a lecture? then you have come to the right place

Save those wasted hours tearing your hair out and put the time to better use doing other activities such as " Getting laid "

Straight to the point recipe approach no f**king about, No Waffle,

Ubuntu Server Administration for Impatient S**ts! 

:)

---

### Post by tgalati4 on 2014-02-03
Why do you want to set up a server?

---

### Post by ally2 on 2014-02-03
Because I am interested mainly because I work for a charity, Obviously they do not have money for the microdoze products, But the good thing is they get alot of computer hardware donated to them old servers Power Edges with ultra 320 setups that kind of thing. 

I thought it would be beneficial to put some of this hardware to use and create some server related projects. Saw it as a good opportunity to learn some stuff and begin my Ubuntu journey. 

I come from a Windows background but have tinkered with Linux as a hobbyist for the last few years I'm pretty confident at the Cli and can write basic BASH scripts that's about the level I'm at currently. Also figured it would be another opportunity to document my work and setup a Wordpress blog for future reference. Gives me another opportunity to dabble with Apache. 

I find Microsoft products clunky and I don't know if it's me only but I just find Linux technologies more interesting guess its the power and ability to get under the hood and tinker. 

My main background with Linux was more Red Hat based but I thought hey lets start learning Ubuntu stuff I have ordered the Ubuntu Server book 3rd edition :) 

That's my story :)

---

### Post by tgalati4 on 2014-02-03
If you do some searching, you will find blogs of others like yourself, setting up Ubuntu server on old Dell PowerEdge servers (1750's).  I have two of them running in my house and I did the same search a few years ago, so I know that they are out there.  It's important to upgrade the BIOS and the RAID BIOS using the CD images that you can download from Dell.  This will make installation easier because there are some bugs that needed patching.  I would also stick to an LTS version because many frameworks are built to an LTS version.  Once your servers are updated, start loading services.  I like to load applications using stacks and if I like them, then I load them natively.

You can browse a current list of stacks:  [http://bitnami.org/stacks](http://bitnami.org/stacks)

---

### Post by ally2 on 2014-02-04
I'm going to be configuring everything virtually first to get some practice All done through the command line no shortcuts just down to the nitty gritty :)

---

### Post by Habitual on 2014-02-04
> **tgalati4 said:**
> Servers are not for newbies.  There is an implicit understanding that you have spent some time with linux (10 years would be good) before attempting to set up and administer a linux server.

I couldn't agree "more".

What I have found in 20 years of IT, the data may actually change somewhat, but the techniques from "years ago" are just as valid today.
Linux hasn't changed **that ***much*.

---

### Post by ally2 on 2014-02-04
I'm reading through those Sander Van Vugth books currently working on a Windows Box just taking brief notes on different areas in Notepad

How long have you guys been tinkering with the Server side of things?

---

### Post by JnPson on 2014-02-04
I installed several servers with the help of this community. I learned Samba, CLI commands and postfix among others. All the answers you need is here. Try the Tutorials section [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by JnPson on 2014-02-04
And I'm pretty sure if you ask a question and describe your problem someone here has the answer. 
That's how I learned Ubuntu server.

---

### Post by ally2 on 2014-02-04
Thanks for the feedback I don't have any problems yet as I haven't started i'm just reading manuals, making notes and compiling a list of website links for reference

---

### Post by Habitual on 2014-02-04
> **ally2 said:**
> compiling a list of website links for referenceThat's a great start! I have links from 10 years ago that I still use today (and *several*) publications dated years ago.

I do Linux Systems all day, every day.
Here's a "Keeper" [http://www.tldp.org/guides.html](http://www.tldp.org/guides.html) - Yes, they are **dated**, but as I have said "Linux hasn't changed all that much".

---

### Post by Habitual on 2014-02-05
> **ally2 said:**
> Just how to get Server related stuff off the ground for example

FTP
SAMBA
How to backup a hardisk to another drive or best methods of backup
Torrent Server
Media Server

All in plain easy to understand noob friendly recipes
[http://lifehacker.com/5822590/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-freenas](http://lifehacker.com/5822590/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-freenas)

---

