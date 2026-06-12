---
title: "Server GUI"
date: 2006-06-28
forum: Server Platforms
---

### Post by inncom on 2006-06-28
Hey, All Ubuntu Users. 

First i want to thank you all for the best Linux Distro out there! This is my first post in this forum, and its a request for an new feauture. 

I am using OSX on my client side and i have been using osx server for some time, but one thing i dont like about it is that i get to much apps on the defult install. Who need chess on a server? 

That is what i like with the Ubuntu Server, the base install is at good start because you can just apt-get the software you need for that spesefic server, and the LAMP option is whery nice.. I also like that the server is easy to update and maintane. 

One thing i miss in the Linux World is a good server dist that has an GUI, all the other dist i have tried like RedHat, Centos and Suse has some good server config solution in the GUI landscape but thay have all the osx syndrome that thay have to much "desktop" apps installed. 

What I am looking for is something in the midele. 

Like just a nice gnome gui with a server control senter to control the sql, dns, network, samba, afp, webserver etc. Maybe it culd be modulebased. 
No openoffice, games etc just pure server config tools. 

If some one want openoffice etc it shuld just be to apt-get it, its allready there.  

I have seen that it is someone on this forum that has started to make ann samba config tool, that is a good start but, it is has to litle futures jet! 

If i had the developing skils i shuld started for my self to develop this but, i dont and I hope I can motivat some one here to start a dicusion on this topic with me. 

Is it just me or am I the only on that are missing this option? 

I think this will open a new world for the Linux community if it was an option like this.. 

I know there is webmin etc out ther but i think a good gtk apps is bether. 

Best regards 
Øystein 
Norway.. Still rocking on the ubuntu platform ;)

---

### Post by Ryan H on 2006-06-28
I'm pretty sure you can install Gnome, KDE, or whatever on there. But I'm not entirely sure how to do this.

-Ryan

---

### Post by skirkpatrick on 2006-06-28
If you just want to control your server, install webadmin from the repository.  You can fully admin your server from a web browser.

---

### Post by houstonbofh on 2006-06-29
I am with you, Øystein!  But after us, I think it starts to get lonely. :)  There are the ubuntu-desktop, kubuntu-desktop and xbuntu-desktop packages.  However, they come with a lot of cruft which needs to be manually removed.  Since all three are strictly dependency lists, I can't see why we couldn't make a ubuntu-server-desktop.  I just don't know where to begin.

---

### Post by inncom on 2006-06-29
Thanks for the intrest, I know its posible to install all of the ubuntu desktops on the server. But it is not what I am looking for, its more an server desktop with apps to config samba, dns, firewall. And this apps shuld be whery integrated with ubuntu. 

Webmin does it, but not so elegant as GUI does. 

Look at this link [http://www.apple.com/server/macosx/](http://www.apple.com/server/macosx/) its more like this i am looking for in the linux world! 

best regards
Øystein

---

### Post by brentoboy on 2006-06-29
I have been toying around with the idea of building a LAMP ubuntu server with a minimal Openbox window environment that isnt started unless you run "startx" and that has nothing more than a good text editor, and start / stop daemon items in the menu, as well as a nice python based settings gui page for each of the services offered by the box.   I figured on allowing for Apache2, MySQL, PostgreSql, php, OpenVPN, Samba and CVS for starters --  of course none of them by default, but apt-getting mysql-with-gui would be a metapackage that added a functional mysql and the menu items along with the config gui.

I think this is exactly what you are asking for, I just wish I had time to play around with computer hobbies these days.

---

### Post by inncom on 2006-06-29
Yes! Its just like that I am looking for, and I think Ubuntu can gain some markedshare on doing something like this. No dis respect but, why is there so much focus on kbuntu xbuntu etc why not put all the energi on ubuntu and ubuntu server.. I think its much bether for the community to focus on one desktop and one server. I know there is only one server! But no other distro maker has done something like that. Is it just me or the Linux community to focused on the desktop? I know I am of topic now but i just had to say it. 

;)

---

### Post by inncom on 2006-06-29
Yes! Its just like that I am looking for, and I think Ubuntu can gain some markedshare on doing something like this. No dis respect but, why is there so much focus on kbuntu xbuntu etc why not put all the energi on ubuntu and ubuntu server.. I think its much bether for the community to focus on one desktop and one server. I know there is only one server! But no other distro maker has done something like that. Is it just me or the Linux community to focused on the desktop? I know I am of topic now but i just had to say it.

---

### Post by NeoGreen on 2006-06-29
I too, have been looking for a GUI bases server, since I am not to good with using terminal mode.  :)

---

### Post by houstonbofh on 2006-06-30
The main reason for the desktops is bloat.  Gnome is feature rich, but very heave weight.  XFE (xbuntu) is much lighter weight.  It runs on older hardware, and takes less resources from the server.  It also has less mature tools for administration.  I think this could be done is stages.  The first step is making a striped down desktop.  ubuntu-desktop (as well as the others) are just dependency lists.  Step one is to rip out the cruft.  Then on a server install you type *apt-get install ubuntu-server-desktop* or *apt-get install xbuntu-server-desktop* and you have a gui with all the config tools.  Step 2 is to build and package the gui and/or web based LAMP tools.  (webmin?  phpmyadmin?  Others?)  I see the beginnings of a community here... :D

---

### Post by gman2 on 2007-09-29
CENTOS 5 (RHEL 5) is a good example of a distro which allows for a minimal GUI based server installation. I have found though that I can do almost all server management using webmin. But there are times in which I feel more comfortable logging into the server to do things and having a minimal GUI environment is nice. The other plus for the GUI is my boss. His biggest knock against Linux is that he doesn't want something that relies on command line knowledge. The minimal CENTOS server desktop does a great job of alleviating fears.

---

### Post by sbakais@msn.com on 2008-03-18
hi guys. 
This subject is very interesting and I want to referesh it. I hope the guys  working on ubuntu server GUI come up with atleast something close to suse linux enterpise 10. I like the yast in suse linux desktops but i must say the server gui is even better.it has been  designed for applications required for the server side such as dns, http, samba etc. The server gui should not have games, media , programming etc as the case it is with ubuntu. we want the server gui to be as light as it can get. Let me tell you guys I like suse servers and the control center yast but i love ubuntu even more for one simple reason is that ubuntu doesn't have depencies problems. beside i found ubuntu works well with devices(the best linux user friendly desktop). unfourtinitally nothing has been done yet to address this issue. the server gui should be easy to install as well as easy to uninstall. for those who want to work with gui can do so as well after you configured the server to your preferences then you should be able to just uninstall the gui and work with web adiministration. working with shell and the command line is not very productive(it takes time to learn the commands even when you eventially get to know them you either forget them again or make mistakes as a human being which going to cost you a lot of your time and effort. human beings make mistake and when i make an error i hate to retype the command again and worse if the command is wrong, i have to go to find the right one. 

it is time for a server specific gui  to be developed as the current desktop is (too too  and very )haviy for the server. one major disadvantages that linux suse server has is that it is not free and lately it is owned by novell. So I guess I am stuck with ubuntu server and I learn a lot from it such bash/shell commands. But for the sake of  human computer interaction please view windows an example.

ubuntu the true sprit of open source
kind regards

---

### Post by CMNetworx on 2008-05-11
Thought I would add. I also think this is a great idea.. Seems some people are scared of linux as a server because of their lack of command line knowledge.. Although I am getting better at the command line, I still find it somewhat comfortable to be able to launch a gui sometimes..

Having webmin and lamp easily loadable (lamp example in ubuntu server 8.04 installer) would also be awesome..

as long as all the garbage was stripped out, as far as I am concerned it could run generic video card drivers, no sound, possibly cd burning capabilities, but not much for apps.. Maybe Thunar for a fileman..Any other apps someone can add themselves..

---

### Post by BDNiner on 2008-05-12
+1

I have installed ubuntu-desktop after setting up an ubuntu server but removing the extra packages can be a pain. Like the PalmOS software (which i feel is useless to be included by default) tries to remove the whole ubuntu-desktop package instead of just itself. There are a couple other programs like that Ekiga is another one that gave me problems. I plan on compling my own gnome and xfce desktops from source without all the extra packages, but after my first glance it looked like a project that is outside of the scope of my knowledge at the moment.

---

