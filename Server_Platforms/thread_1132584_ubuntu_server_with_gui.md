---
title: "ubuntu server with gui"
date: 2009-04-22
forum: Server Platforms
---

### Post by salim.madni on 2009-04-22
Hello Gurus, Good day to you

Sir we want to know and learn

is there any way to convert,install,make UBUNTU 9.04 or 8.10 into GUI. say we install gnome,kde,xfc etc or any other interface

on the alternate way we have installed webmin debian package on ubuntu so everything we can control or work with web browser

regards
salim

---

### Post by balaknair on 2009-04-22
To install the GUI of your choice in Ubuntu server,

*sudo apt-get install ubuntu-desktop*

**or**
*sudo apt-get install kubuntu-desktop*

**or**
*sudo apt-get install xubuntu-desktop*

for Gnome, KDE and XFCE respectively.

---

### Post by niqmk on 2009-04-22
You can visit to:

[http://www.bgevolution.com/blog/ubuntu-server-convert-to-graphical/](http://www.bgevolution.com/blog/ubuntu-server-convert-to-graphical/)

---

### Post by salim.madni on 2009-04-22
dear sir can you advise where to download this package

is it single files or multiple

as to download using ubuntu server self is not possible since the size shown 390mb

i do have all version and flavors and disbritions cds of ubuntu,kbunutu,edubuntu,xfcbunutu,ubuntustodio

so kindly advise what files or packages i should take manually to ubuntu server machine and installed step by step

i again and highly apprecited your prompt response and support great way simple

kind regards
salim

---

### Post by balaknair on 2009-04-22
It actually consists of multiple packages(ubuntu-desktop is a metapackages, installing it prompts the package manager to download and install the various packages necessary to get the GUI up and running).

You can install it using a desktop CD with the appropriate desktop environment(ie Ubuntu for Gnome, Kubuntu for KDE etc)

Put the Desktop CD in the drive and add it to sources list with the command
```
sudo apt-cdrom add
sudo apt-get upgrade
```

Then install the desktop environment you need
eg: If you want Gnome, use the Ubuntu desktop CD and add it to your sorces.list as described above. Then type in
```
sudo apt-get install ubuntu-desktop
```

*ubuntu-desktop* installs the Gnome desktop environment and also all other GUI packages like Open Office, Firefox, Rhythmbox, Pidgin etc. which are part of the Ubuntu desktop CD.

You can also install a minimal Gnome desktop with the command 
```
sudo apt-get install gnome-core
```
as mentioned in the link niqmk provided in the previous post. I don't know if this would work from the CD though, you could certainly try it if you don't want to install all those additional packages(which can take up a couple of GBs space in all).

Hope this helps.
All the best

---

### Post by daboroe on 2009-04-22
really not recommended to use a gui on a server. this is becuaes the gui will create more instances of processes that run that allow for more vulnerabilities. If you are fine with the command prompt and really do not "need" the gui then stay with the command prompt. 

there are a lot of resources to help you with the commands in the command prompt. i am not totally okay with some of the commands in the command prompt but have stayed with it becaues of the increase security vulnerabilities that could arise.

---

### Post by Iowan on 2009-04-22
[Here]("https://help.ubuntu.com/community/ServerGUI") is a help page you might review...

---

### Post by mangocat1 on 2009-04-25
I guess I'm in a similar boat as the OP. I was hoping for something that had a similar look and feel to Windows Server 2003/2008. I installed the full desktop package however there are no icons and such for the server functions.

---

### Post by cariboo on 2009-04-25
If you need a gui to administer your server, i would suggest [Webmin]("http://www.webmin.com/"), it is a web based management appliction that focuses on the server administration. As of right now the server team has decided not to create and install any gui server apps.

---

### Post by HermanAB on 2009-04-25
Linux is Linux is Linux...

If you want a server with a GUI, then just install a regular desktop version.

---

### Post by Jimmy9pints on 2009-04-26
> **HermanAB said:**
> Linux is Linux is Linux...

If you want a server with a GUI, then just install a regular desktop version.

Yeah but by doing that you get all the other apps (open office, media players, Gimp etc.) that you don't want or need for a server. 

If you really want a GUI I would suggest installing the server, then the desktop environment. Server gurus often mention it's less secure, but if you're not using it as a production server then it should be fine - otherwise all of us with GUIs on our desktops are screwed. :)

However, let me say this: I at first thought I needed a GUI but resisted the temptation due to the advice I received here. Now I quite happily run my server from the command line. Go on, give it a bash, it's not as scary as you think.

---

### Post by HermanAB on 2009-04-26
Hmm, if you really want wizards, then there are two solutions:
1. Install Mandriva Linux - bu-bye Ubuntu - sniff...
2. Install Webmin.

But Webmin really is a poor cousin.  The Mandriva Corporate Server is very slick.

---

### Post by gg234 on 2009-04-26
Try this this might help you

[http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html](http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html)

---

### Post by Oceanwatcher on 2009-05-02
> **HermanAB said:**
> Hmm, if you really want wizards, then there are two solutions:
1. Install Mandriva Linux - bu-bye Ubuntu - sniff...
2. Install Webmin.

But Webmin really is a poor cousin.  The Mandriva Corporate Server is very slick.

So what we are realling hoping for is a Ubuntu Corporate Server? That would be neat!

Who really cares if the server is minimally less secure when you are not going to put it directly on the internet anyway? As another poster correctly pointed out, if it is THAT bad, then all of us with Kubuntu and Ubuntu as out desktops are in serious trouble.

I would argue that Ubuntu and Kubuntu desktops on servers are the way to go for any server that is not going to be used as a web server (or similar). Make the environment consistent for support people - Use the same GUI on servers and on desktops. MS do it, Apple do it. Why not Ubuntu and Kubuntu?

It is easy enough to upgrade a Ubuntu server to a desktop. But you get a lot of stuff that you do not want. And if you only go for KDE or Gnome, you have to add X as well as the desktops alone do not have dependencies added (as far as I understsand from other posts).

I have a server at home running Ubuntu Server with no GUI. And I am getting VERY tired of hopping around in the CLI. I have done that for many years now, and I am going to install KDE so I can connect via remote session and have a proper filemanager and a nice texteditor. And then it is time to start searching for applications to manage the server. There has to be some applications out there that can do the job...

The negative attitude towards GUI on a server is not helping move Ubuntu and Kubuntu forward. There are a lot of small businesses and organisations that would benefit a lot from running Ubuntu and Kubuntu as their only OS. But most of these do not have deep admin skills, neither do they have time to learn all the quirks of the commandline. they would try, and then give up. And probably find a pirate version of Win server. That one has an interface they can manage.

These people need to set up a server, connect a printer or two, share a few folders, share the printer and set up backup for the server. Then add the users and be done. This is the main part of it.

Some that are a little more advanced would like to add AMP to the mix.

I think it is a very logical step to take and I am looking forward to see it happening. In the mean time, I will try to install only KDE and not all of the apps that go with the Kubuntu desktop.

---

### Post by HermanAB on 2009-05-02
I guess the main reason why Ubuntu won't create a server GUI is because Redhat, Mandriva and Suse already have the market buttoned up.

---

### Post by Oceanwatcher on 2009-05-02
Could be, but as it is now, a lot of "Windows people" have heard about Ubuntu, but have no clue about RedHat, Mandriva and Suse. So Ubuntu is in a very good position to come out with a corporate version/small business version.

What we need is a series of server admin tools that is not tied to Gnome or KDE so that it will happily run on all kinds of desktops. If we had that (of course, they would have to be made so that they work perfect with the filestructure in Ubuntu), the complete server package might not be needed. But it would be nice to have a metapackage that could install a complete GUI for the server. So you could do a apt-get install kubuntu-server-gui and not have to worry about anything else.

My favourite example of something that would be wonderful to have a GUI for, is bind9. You do not need a lot of information to set up a caching DNS that resolves for a small lan. But there is quite a bit of editing to be done, and anyone attempting this knows it only takes one small formatting error to mess everything up. A gui could simply have some fields to fill in and then the formatting will be taken care of by the program. This is what computers are good at! :-)

---

### Post by cariboo on 2009-05-02
As far as I'm concerned, there are no Ubuntu specific gui server management applications, so there is really no need to run a desktop. If you need or want a gui to do anything, install the gui apps, then use x-forwarding to run the applications remotely.

---

### Post by GolemdX on 2009-05-02
My server has ubuntu desktop installed above it, only because my family sees the server as useless when they can't perform any tasks on it...

You should probably just install the gnome-core and firefox for a simple GUI... and any other packages you might need.

---

### Post by HermanAB on 2009-05-02
> a GUI for, is bind9

On Ubuntu, the only way to administer BIND9 is with Webmin.

On Suse, Mandriva and Redhat, there are nice wizards and you can set it up with about 3 mouse clicks.

---

### Post by Oceanwatcher on 2009-05-03
So.. The apps that exist for the other distros - are they open source?

---

### Post by Oceanwatcher on 2009-05-03
> **cariboo907 said:**
> As far as I'm concerned, there are no Ubuntu specific gui server management applications, so there is really no need to run a desktop. If you need or want a gui to do anything, install the gui apps, then use x-forwarding to run the applications remotely.

Sir, you are quite right. As far as I know, there are no UBUNTU specific gui. But there is a KUBUNTU specific gui for the Samba server. Very nice, and give you a very structured overview. I like it a lot. Just installed and had the first look at it. Will check more tomorrow. Now we just need to get gui modules for a few other things.

bind9
cups
ldap

Just to mention a few important ones :)

---

### Post by Alterax on 2009-05-03
> **Oceanwatcher said:**
> Sir, you are quite right. As far as I know, there are no UBUNTU specific gui. But there is a KUBUNTU specific gui for the Samba server. Very nice, and give you a very structured overview. I like it a lot. Just installed and had the first look at it. Will check more tomorrow. Now we just need to get gui modules for a few other things.

bind9
cups
ldap

Just to mention a few important ones :)

Sounds great!  When do you reckon you'll have a release ready?

---

### Post by Oceanwatcher on 2009-05-03
You will be the first to know :lolflag:

---

### Post by windependence on 2009-05-04
> **Oceanwatcher said:**
> So what we are realling hoping for is a Ubuntu Corporate Server? That would be neat!

Would be nice as an ALTERNATIVE to the server version.

> **Oceanwatcher said:**
> Who really cares if the server is minimally less secure when you are not going to put it directly on the internet anyway? As another poster correctly pointed out, if it is THAT bad, then all of us with Kubuntu and Ubuntu as out desktops are in serious trouble.

You would care of you were running a true production server and you got seriously hacked. Not everybody in the corporate world runs servers with no internet connection, in fact very few do.

> **Oceanwatcher said:**
> I would argue that Ubuntu and Kubuntu desktops on servers are the way to go for any server that is not going to be used as a web server (or similar). Make the environment consistent for support people - Use the same GUI on servers and on desktops. MS do it, Apple do it. Why not Ubuntu and Kubuntu?

Why not just just learn to be a good admin and be proficient at the command line? Linux != Windoze.

> **Oceanwatcher said:**
> It is easy enough to upgrade a Ubuntu server to a desktop. But you get a lot of stuff that you do not want. And if you only go for KDE or Gnome, you have to add X as well as the desktops alone do not have dependencies added (as far as I understsand from other posts).

I would actually consider that a downgrade rather than an upgrade.

> **Oceanwatcher said:**
> I have a server at home running Ubuntu Server with no GUI. And I am getting VERY tired of hopping around in the CLI. I have done that for many years now, and I am going to install KDE so I can connect via remote session and have a proper filemanager and a nice texteditor. And then it is time to start searching for applications to manage the server. There has to be some applications out there that can do the job...

There are several good ncurses file managers. Midnight Commander comes to mind, and for a text editor, I use nano or pico. Easy to use and very effective.

> **Oceanwatcher said:**
> The negative attitude towards GUI on a server is not helping move Ubuntu and Kubuntu forward. There are a lot of small businesses and organisations that would benefit a lot from running Ubuntu and Kubuntu as their only OS. But most of these do not have deep admin skills, neither do they have time to learn all the quirks of the commandline. they would try, and then give up. And probably find a pirate version of Win server. That one has an interface they can manage.

Some of us don't want to see Linux go into the toilet like Windoze. If you want fancy wizards and nice eye candy, stick with the thousands of MCSEs who can't run a command on a server. Better yet, get a Mac. At least they work correctly. Not everyone wants Linux=Windoze. have you ever read WHY Ubuntu Server does not have a GUI?

> **No X server by design**

  By design, Ubuntu Server Edition does not include an X server or any graphical desktop applications. This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator. 
 [INDENT] 	 	"*So I applaud the Ubuntu team’s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server.*"
	--Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server"   	
[/INDENT]

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

> **Oceanwatcher said:**
> These people need to set up a server, connect a printer or two, share a few folders, share the printer and set up backup for the server. Then add the users and be done. This is the main part of it.

So they should probably stick to Windoze. I don't see much advantage in these types of applications being run on a GUI in Linux.

> **Oceanwatcher said:**
> Some that are a little more advanced would like to add AMP to the mix.

Most of the n00bs coming to Linux from Windoze don't even know what AMP or LAMP is. 90% of them don't even need it to run a simple web site but they THINK they do because they read it all over some forum and "it's cool".

> **Oceanwatcher said:**
> I think it is a very logical step to take and I am looking forward to see it happening. In the mean time, I will try to install only KDE and not all of the apps that go with the Kubuntu desktop.

Kubuntu is great for what it is - a desktop. I run it on some of my Linux desktop machines. Real servers do not run GUIs. If you ever worked for a large world wide data center, you would know this.

I am GLAD to see a server version without all the cruft of the other distros. I can load my Zimbra machines on a minimal footprint without anything else on teh machine and admin it via ssh OR the web GUI if I want without the risk of all that garbage and overhead a GUI introduces. I am very disappointed to see Linux on the server side being "dumbed down" for Windoze users. Skilled admins need only the tools provided in the server package.

-Tim

---

### Post by Oceanwatcher on 2009-05-05
> **windependence said:**
> Would be nice as an ALTERNATIVE to the server version.

I think it is better that we stop at these words and I say that I totally agree with you here. That way, you get what you want, and the rest of us get a server that is a lot easier to administrate :-) I know exactly what I am asking for and KNOW it will make my day a lot easier. This is my opinion, and I know you do not agree. It is a free world and Linux could be for everyone...

---

