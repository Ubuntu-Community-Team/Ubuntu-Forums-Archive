---
title: "Need nube help setting up basic home file print server."
date: 2008-11-28
forum: Server Platforms
---

### Post by phreon on 2008-11-28
Hi Folks,

I am a nube who is trying to set up a basic file and print server in Ubuntu 8.04 Server edition that will be headless. I am confused as to what I need to have our windows and Ubuntu local networked computers save and access their files, share files, print, and stream media from the home server.

I have just completed:
Ubuntu 8.04 Server with ssh, samba, and print server, installed but not set up. (I do not know anything about ssh and Samba. It appeared from my forum searches that they were the basic choices to make.) I chose the server edition because I did not want the overhead of a GUI on the server.
I have an AMD Duron 1200Mhz, 256MB mem, 40Gb primary and 160GB slave disk, CD-RW, DVD-Rom. Stripped out the floppy, modem, and extra cables to improve airflow.

Some preliminary info:
I think I can set up and administer the server from another computer but I do not know how to get into my server remotely.
I have forgotten how to use vi so I will probably need a user friendly text editor to edit the server config files. Are there other basic packages I need to install on the server?

I am betting this basic set up is covered somewhere but much Ubuntu forum search and much Google search did not find it. I found server set-up help but mostly it assumes a fair amount of server/Linux knowledge. 

Has anyone done a tutorial for nubes that you can point to? If not is this something that the Ubuntu user community needs? 

If this is not covered, and this community can help, I will post my experience, in detail, as I get my server going.

Thanks
P

---

### Post by salocinbake on 2008-11-28
I am in the same boat, a few info: To access your server from within your network, in Ubuntu, simply open a console (under accessories) and type
" ssh 192.168.1.XXX"  that's it. Simply log in with your user name and password.

For windows side, download [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") and again use your server's ip to connect in the upper box.

Salo

---

### Post by cariboo on 2008-11-28
Make sure you have openssh-server installed on the server or you won't be able to connect via ssh, once that is done, using the default setup in a terminal type:

```
ssh user@server
```

and enter your password. 

A simple text editor is nano which is installed by default, I use it all the time as I have never bothered to memorize the vi commands. Nano has the commands in a pane below the main text editing pane.

A good samba resource, that I use all the time is located here:

[www.samba.org/samba/docs/Samba3-ByExample.pdf](www.samba.org/samba/docs/Samba3-ByExample.pdf)

I always have the pdf close at hand for references.

To setup your printers you can use the cups web interface, I use links (a text based web browser) to access the server at:

[http://localhost:631](http://localhost:631)

I have set up cups to be accessible from anywhere on my network, you can do this while setting up your printers using the cups web interface.

Jim

---

### Post by phreon on 2008-11-29
Thanks you guys!

I downloaded Putty to my laptop and easily logged into my new server. I have been reading how to set up Samba and have begun relearning vi. Vi is not fun. I will try Nano right away. I will get Samba going first and then work on CUPS. After CUPS I will set up a media server.

I think I will post a detailed account of a basic file, print, and media set up for beginners when I am done.

I have been using this tutorial as a template for my server.
[http://www.howtoforge.com/ubuntu-home-fileserver-p1](http://www.howtoforge.com/ubuntu-home-fileserver-p1)

---

### Post by Iowan on 2008-11-30
I like **nano**. It may not be as high-powered as **vi**, but having the options listed at the bottom of the screen is a plus.  (I also like howtoforge.com well enough to include it in my sig.)

---

