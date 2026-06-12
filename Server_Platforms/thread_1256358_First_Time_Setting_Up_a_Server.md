---
title: "First Time Setting Up a Server"
date: 2009-09-02
forum: Server Platforms
---

### Post by charly17201 on 2009-09-02
Okay, this is apparently going to be more painful that I'd hoped.

I'm setting up a home server - which, btw is the first time I've set up a server at all. I need to have access/shared files between all the computers and I'd really love to be able to access my files from work - that's why I went with doing a server.

Hardware:
AMD Sempron LE-100
2 gig ram
500 gb hard drive
mb 10/100 connection
extra 10/100 card


Software:
initial Ubuntu 9.04 (with updates)
I've downloaded and installed SAMBA (and apparently SAMBA4 also).

Following different instructions I've found is difficult as they keep refering to things I don't know - SSH, smbpasswd, etc, etc, etc.

[B]Is there, in a nut shell, a guide or book that I can get that not only will hold my hand as I go through the process - but to also explain all these new terms and programs at the same time?
[/B]
Example: Test your NAS box by starting your windows machine and typing in \\machine-alias\superczar

    Okay, sounds simple enough, I followed the instructions to this point - and nothing. Somewhere else (a different article by someone else)  I read I have to download and install software to put on the windows machine in order for it so see the server - this article had nothing on that. Follow the link and it is telling me about putting linux software on the server...... 

I'm running in circles and lost in the forest. And nothing I've found says when I should have everything hooked together and when I don't need to be - I still need to work on my other computers (and have internet access) while I'm tinkering with this.

All of this would be eliminated if I didn't have to have that danged MS box for my AS400 work.

Anyone, please help me! I appreciate anything you can do.

---

### Post by rocknrollmouse on 2009-09-02
I started by working through the server guide, available here:
   [ubuntu guides]("https://help.ubuntu.com/9.04/index.html")

A quick tip, don't try and build your finished server in one go - be prepaired to get it wrong, and start again - learn from your mistakes, the only way not to make any is not to do anything ;-)

---

### Post by ugm6hr on 2009-09-02
For a file server, Ubuntu will obviously accomplish this, but it would be easier to do with a file-server specific OS like FreeNAS.

Have a look at the link below.

Easy to setup Samba & NFS for LAN sharing, and enable port-forwarding on your router to allow (read only) file access from the web.

No special skills required.

---

### Post by charly17201 on 2009-09-02
Thanks so far. It seems that most everything I've search through in the threads is written at a much higher knowledge level than where I'm at.

It isn't that I want to be led through blindly..... I want to know the _why_ and _how_ it effects things when I do something in setting the system up.

---

### Post by HermanAB on 2009-09-02
Do yourself a favour - go to the Samba web site and read the Official Howto.  All other howtos should be taken with some salt...

---

### Post by bear24rw on 2009-09-02
For accessing files outside of your LAN i recommend a combination of ssh and filezilla. heres a quick walk through

**- on server:**

```
sudo aptitude install openssh-server
```

that installs and sets up an ssh server

get the local ip of server

```
ifconfig
```

it will probably look like either

192.168.1.*
or
10.*.*.*

**- on router:**

you will need to foward port 22 on your router to your servers ip

[http://portforward.com/](http://portforward.com/)

can help you out if you dont know how to port foward, use the ip address found in previous step

**- get external ip for your house:**

[http://whatismyip.com/](http://whatismyip.com/)

remember that

**- on computer outside of network:**

install filezilla-client

[http://filezilla-project.org/](http://filezilla-project.org/)

if you are on ubuntu you can

```
sudo aptitude install filezilla
```

**- then in filezilla:**

ip you found from whatismyip.com     username    password    22

and you should be able to connect to your computer and transfer files
i know this guide is really vague but hopefully its enough to get your started with accessesing files outside your network :)

---

### Post by Jerry.S on 2009-09-02
> **rocknrollmouse said:**
> I started by working through the server guide, available here:
   [ubuntu guides]("https://help.ubuntu.com/9.04/index.html")

A quick tip, don't try and build your finished server in one go - be prepaired to get it wrong, and start again - learn from your mistakes, the only way not to make any is not to do anything ;-)

Amen to that! I think that I built and rebuilt my servers more times than I want to admit to. But I just kept learning. p.s. google can be a good friend to have.:P

---

### Post by Adina on 2009-09-03
You can also use [winscp]("http://winscp.net/eng/docs/introduction") if you want to access your linux server remotely from a windows computer. As far as I know winscp use encryption and filezilla does not.

---

### Post by bear24rw on 2009-09-03
> **Adina said:**
> You can also use [winscp]("http://winscp.net/eng/docs/introduction") if you want to access your linux server remotely from a windows computer. As far as I know winscp use encryption and filezilla does not.

No filezilla will use encryption if it is used with ssh.. filezilla supports ftp, ftps, sftp.. just depends on which protocol you use

---

### Post by rocknrollmouse on 2009-09-03
Just found this thread: [Free Beginners Guide]("http://ubuntuforums.org/showthread.php?t=1052065&highlight=list+users")

> **charly17201 said:**
> Thanks so far. It seems that most everything I've search through in the threads is written at a much higher knowledge level than where I'm at.

It isn't that I want to be led through blindly..... I want to know the _why_ and _how_ it effects things when I do something in setting the system up.

Although more desktop than server, it does have some good and useful chapters which might help explain some of the basics to get you up and running.

---

### Post by charly17201 on 2009-09-03
Again all, thanks for the input. I looking. Getting time is my biggest factor to wading deep in to this. Wednesday and Saturday are my only days I have any real time. Work all day and get calls at home half the evening.... the life of being on salary.

I do appreciate your help!

---

### Post by charly17201 on 2009-09-03
Okay, I've gotten some good direction to start. Thanks.

More reading done..... now I'm at my first 'new' cross road. I guess I need to make a choice(s).

Package Tasks: do I chose only one? or can I chose more than one. With only one, I'm leaning toward SAMBA since I need to include my Win XP on the network. Yet, I also want to be able to use any of my 3 printers from any of the 4 machines. 

But, could I also not simply share the printers like at work? Ahh, light-bulb moment. they use multiple servers at work. one for mail, one for software, one for print functions..... am I right on this?

---

### Post by ugm6hr on 2009-09-04
Do your 3 printers have Ubuntu / Linux drivers?

Do they have to be in a fixed physical location, or could they all be attached to the server (and are they all USB)?

What computers (i.e. OS) are going to connected to the network (i.e. are all your current computers MS Windows XP, or do you have Macs / Linux desktops)?

---

### Post by charly17201 on 2009-09-04
> **ugm6hr said:**
> Do your 3 printers have Ubuntu / Linux drivers?

Do they have to be in a fixed physical location, or could they all be attached to the server (and are they all USB)?

What computers (i.e. OS) are going to connected to the network (i.e. are all your current computers MS Windows XP, or do you have Macs / Linux desktops)?

I could attach them all to the server and yes they are all USB. However, one is not linux friendly - the Lexmark all in one so it is attached to the xp machine. The other 2 are HP and work fine on Ubuntu.

OSes are Ubuntu 9.04 and one win XP.

---

### Post by rocknrollmouse on 2009-09-04
> **charly17201 said:**
> Okay, I've gotten some good direction to start. Thanks.

More reading done..... now I'm at my first 'new' cross road. I guess I need to make a choice(s).

Package Tasks: do I chose only one? or can I chose more than one. With only one, I'm leaning toward SAMBA since I need to include my Win XP on the network. Yet, I also want to be able to use any of my 3 printers from any of the 4 machines. 

But, could I also not simply share the printers like at work? Ahh, light-bulb moment. they use multiple servers at work. one for mail, one for software, one for print functions..... am I right on this?

During installation you can select several options(tasks).

SAMBA will allow you to share printers as well as files :-)

---

### Post by charly17201 on 2009-09-04
Thanks guys, on to the next step. :)

---

