---
title: "Xubuntu Server"
date: 2006-10-03
forum: Server Platforms
---

### Post by navajoplaya on 2006-10-03
I was setting an older computer to be a web server with Xubuntu and looked at the guide sticky above, but I have a question.  What are the steps to creat the web server with MySQL,PHP, and Apache?  Can I use the guide at [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) but install Xubuntu first and then use the Ubuntu Server CD to install the rest.  

Here is what I think it is, can people correct me.

1) Download and create the Xubuntu disc image and run installation off teh live Cd. 
2) Then use teh ubuntu server cd to foolow the steps in teh guide.  

is that it???

-Anthony

---

### Post by sonic2000gr on 2006-10-03
Though there are multiple ways to do this, perhaps the easiest in your case would be:

1. Follow the howtoforge tutorial to install the server with the exact same cd it is using.
2. Once satisfied it works as you want it, edit /etc/apt/sources.list and make sure the universe repository is enabled.
3. Execute the following commands:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xubuntu-desktop

```

(Note: the upgrade part will mostly download fixes and updates to current packages, you may wish to do this after everything is installed)

---

### Post by navajoplaya on 2006-10-03
Thanks for the reply, but 2 quick questions.  

1) Will the upgrade keep the old Gnome desktop enviorment?  Or the CD does not install Gnome.  I have limited space that is why I ask.

2) How do you enable the unviersal repository?

Thanks.

---

### Post by dannyboy79 on 2006-10-03
the server cd doesn't install a window manager or what you call the Gnome desktop environment. and he has already told you how to enable the univeral respos, you edit /etc/apt/sources.list.
which means at terminal, type in sudo nano /etc/apt/sources.list. then when your sources.list comes up in the nano editor, simply scroll down until you see a section where it says, if you uncomment this section you will enable the universal reposirtry. you would erase the # from the line so it ENABLES the repo. then you would hit control x, then it is gonna ask you if you want to save it, you click y, then you should be back to the terminal. if you want to just in case back up your sources.list first by typing sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup. then if you ever screw up your sources.list you can always overwrite the screwed up one with the backup one. you would do this by typing sudo mv /etc/apt/sources.list-backup /etc/apt/sources.list. that's it.

---

### Post by az on 2006-10-03
> **navajoplaya said:**
>  What are the steps to creat the web server with MySQL,PHP, and Apache?  Can I use the guide at [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) but install Xubuntu first and then use the Ubuntu Server CD to install the rest.  



[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Just install Xubuntu and run
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

You are done.

---

### Post by sonic2000gr on 2006-10-03
> **navajoplaya said:**
> Thanks for the reply, but 2 quick questions.  

1) Will the upgrade keep the old Gnome desktop enviorment?  Or the CD does not install Gnome.  I have limited space that is why I ask.

2) How do you enable the unviersal repository?

Thanks.

Yes the gnome desktop will be preserved if you install more than one desktop. As a matter of fact, the server CD does not install any desktop at all. You can install desktops with commands such as:

```

sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop

```

and so on.
See also azz's answer: This is one of the other ways to install a desktop version and turn it into a server.

---

### Post by dannyboy79 on 2006-10-03
NO, guys, he specifically stated that he wants a very small footprint. He is on the right path by installing the Server edition and then adding on! just because he does sudo aptitude install xubuntu-desktop won't mean that he'll be installing everything that comes with xubuntu, it will only be the xfce window manager, won't it?

---

### Post by navajoplaya on 2006-10-03
Where can I get a list of applications that come installed with Xubuntu (those included with xfce and extras that are included)?

---

### Post by az on 2006-10-03
> **dannyboy79 said:**
> just because he does sudo aptitude install xubuntu-desktop won't mean that he'll be installing everything that comes with xubuntu, it will only be the xfce window manager, won't it?

Of course it will install everything that xubuntu-desktop offers.  Why wouldn't it?


If you just want the individual parts, just install those individual packages.

---

### Post by az on 2006-10-03
> **navajoplaya said:**
> Where can I get a list of applications that come installed with Xubuntu (those included with xfce and extras that are included)?

apt-cache show xubuntu-desktop
or use packages.ubuntu.com and search for xubuntu-desktop.

---

### Post by dannyboy79 on 2006-10-03
Of course it will install everything that xubuntu-desktop offers. Why wouldn't it?

You are correct, I mispoke. What he should do is simply install a window manager if he wants a gui for his server.

---

### Post by navajoplaya on 2006-10-05
If you use the Xubuntu install CD after installing from the ubuntu-server CD, will it just install xubuntu ontop of what has been installed by the server cd?

---

### Post by dannyboy79 on 2006-10-05
i don't believe so, it would probably be pretty sloppy. if you already have the server cd installed why don't you just type sudo aptitude xubuntu-desktop and you should have yourself an xubuntu install

---

### Post by dteSpuD on 2006-10-19
Is there any way to get Xubuntu with Ubuntu server's automatic LAMP? I can't install ubuntu server on the machine I want it on (128MB of ram, the livecd won't boot properly; it gets most of the way through loading gnome), so I figured Xubuntu would run happily instead... but there's no server release of xubuntu... I was mostly hoping to get a nice easy lamp setup really. Ideas? Thanks!

*-apologies for gravedigging

---

### Post by az on 2006-10-19
> **dteSpuD said:**
> Is there any way to get Xubuntu with Ubuntu server's automatic LAMP? I can't install ubuntu server on the machine I want it on (128MB of ram, the livecd won't boot properly; it gets most of the way through loading gnome), so I figured Xubuntu would run happily instead... but there's no server release of xubuntu... I was mostly hoping to get a nice easy lamp setup really. Ideas? Thanks!

*-apologies for gravedigging

See post number five in this thread.


The server install cd is not a live cd.  The regular Ubuntu install cd is a live cd, but it does not have the LAMP packages on it.

But it does not matter.  Whether you install Ubuntu or Xubuntu and then install the LAMP packages, or if you install the server setup along with the LAMP packages and then add on Xubuntu-desktop or ubuntu-desktop, you pretty much get the same thing.

The only difference is the kernel on the server install cd.  If you are running on a pentium one, you need to use the desktop cd.  If you installed the desktop and then switch to the server kernel, your desktop hardware (ex: mouse) may not work.

You can run a server with the desktop kernel.  If it is a production system, you may want the server kernel for a little better performance and possible more security(?) but everything should work.

---

### Post by dteSpuD on 2006-10-20
My apologies, I've just realised I burnt off a second copy of Ubuntu 6.06 and /not/ Ubuntu Server. I'd written "server" on the CD before burning it though.. whoops D:

---

### Post by altonbr on 2006-10-25
So there's been no mention of the Xubuntu Alternate CD? Download that ISO and install a LAMP server that way. This is probably best to use anyway because there is no GUI during the installation so the installation will run faster. [Xubuntu Alternate 6.06]("http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/xubuntu-6.06.1-alternate-i386.iso")

I know 6.10 is coming out tomorrow.. but you can upgrade to that later.

The alternate CD can also install the desktop packages as normal, a LTSP server and a couple other options if you're interestedt... all with a text-based installer (which, like I said, is faster).

---

