---
title: "Ubuntu Center - web based Ubuntu Contol"
date: 2006-02-01
forum: The Cafe
---

### Post by TTT_travis on 2006-02-01
Hi guys, I recently (2 days ago) started a project called Ubuntu Center. Ubuntu Center is a project that will let you mange your files, view your photos, watch your videos, listen to your music, view bookmarks, control file downloads and much much more in a web based control panel. This is done by including other open source packages in one big package to make one nice ubuntu compatible easy to setup/use package. I have a few very early preview screen shots here:

[Link]("http://snoopy.ath.cx/ubuntucenterss/")

You'll notice in the screen shot there are only a few modules more will be added soon.

The current biggest module is Ampache which allows you to listen your music from a remote location. As I said before I will intergrate more software in the next few days such as some sort of Gallery software for photos, Torrentflux for managing torrent downloads. I don't really know a coding language very well so the code will not be the neatest in the world because it I only have enough knowledge to poke at it and make it work the way I want. If you have any suggestions or like this concept/project please reply and let me know. :KS

---

### Post by greenway on 2006-02-01
Very nice initiative! I have been walking around with the idea of also creating a webbased front end for Ubuntu as well (something like life version run through the browser) and I was thinking about doing it with [Open Laszlo]("http://www.openlaszlo.org"). Basicly just the normal desktop in your browser...

But with the current amount of spare time, that will probably take me a few years to get going.

Anyway, very nice work and keep us posted on your progress!

-mattijs

---

### Post by TTT_travis on 2006-02-01
Thanks. Again the main idea of this project is simplicity, keeping things simple and unbloated. Also Functionality > Design again I'm only 13 so my coding skills arn't the greatest but once I get this thing out there if people like it maybe they'll contribute to it.

---

### Post by WildTangent on 2006-02-02
Looks interesting, I look forward to seeing more updates on this, and maybe some actual code to try out. I wouldn't mind beta testing this :)

-Wild

---

### Post by TTT_travis on 2006-02-02
[QUOTE=WildTangent]Looks interesting, I look forward to seeing more updates on this, and maybe some actual code to try out. I wouldn't mind beta testing this :)

-Wild[/QUOTE]

Once I get this a little further into development I do plan to beta test so pretty much count yourself in. Keep in mind the code for this is mostly html with php and all this really does is intergrates open source web apps like Ampanche and Torrentflux etc. into one nice ubuntu themed place. I do plan to possibly create an option to choose between kubuntu and ubuntu, but for now its just ubuntu center.

Travis

---

### Post by TTT_travis on 2006-02-04
Hi guys, just a little update here, I am proud to say I have gotten allot of work done in the past 2 days. There are still tons of bugs to work out and the configuration system has to be made which will take a few days. However expect a demo in a few days!

**UPDATE:** I have taken some new screen shots you can view them here: [http://snoopy.ath.cx/ubuntucenterss/]("http://snoopy.ath.cx/ubuntucenterss/")

let me know what you think of the way the new partially redesigned interface is layed out.

Travis

---

### Post by UbuWu on 2006-02-04
Very nice idea! The link seems to be down at the moment though...

---

### Post by majikstreet on 2006-02-04
cool.... that's really neat.. I can't wait for a release :P

ampache works with mpd right? or is it a seperate thing?

---

### Post by TTT_travis on 2006-02-04
[QUOTE=UbuWu]Very nice idea! The link seems to be down at the moment though...[/QUOTE]

Sorry about that it is hosted on a home internet connection and its been having some downtime in the past few days. 

[QUOTE=majikstreet]cool.... that's really neat.. I can't wait for a release :P

ampache works with mpd right? or is it a seperate thing?[/QUOTE]

Yeah ampache is supposedly supposed to work with MPD, I personally do use MPD because the server is in my living room and its nice to listen to music sometimes. I'll look into it.
____
Ok, regarding video, which has not been implemented yet, I am wondering how to do this, and if it would be useful at all, most of the videos on my computer are like 400mb each so I can't see this being that much useful, any opinions on if I should have video or not? it might be useful inside your network but over the internet it would be far too slow.

---

### Post by UbuWu on 2006-02-04
[QUOTE=TTT_travis]Sorry about that it is hosted on a home internet connection and its been having some downtime in the past few days. 
[/QUOTE]

I can see it now and it is looking very good so far!

---

### Post by WildTangent on 2006-02-04
Nice work, any clue on when a package of some sort will be available to install it all?

-Wild

---

### Post by TTT_travis on 2006-02-04
[QUOTE=WildTangent]Nice work, any clue on when a package of some sort will be available to install it all?

-Wild[/QUOTE]

Since the project is only 4 days old it still has a few bugs to work, and a centralized config file needs to be created to make it easy to setup. However I have a demo up now:

[http://snoopy.ath.cx/centerdemo](http://snoopy.ath.cx/centerdemo)
Username: demo
Password: demo

---

### Post by WildTangent on 2006-02-05
Just a random question: how did you get phpsysinfo to show the right distro? Mine says Debian testing/unstable.

[http://www.w1ldt4ng3nt.net/sysinfo](http://www.w1ldt4ng3nt.net/sysinfo)

-Wild

---

### Post by TTT_travis on 2006-02-05
[QUOTE=WildTangent]Just a random question: how did you get phpsysinfo to show the right distro? Mine says Debian testing/unstable.

[http://www.w1ldt4ng3nt.net/sysinfo](http://www.w1ldt4ng3nt.net/sysinfo)

-Wild[/QUOTE]

ok to do that you will have to add another block of code in  /var/www/sysinfo/distros.ini

Image   = "Ubuntu.gif"
Files = "/etc/issue"

and put a Ubuntu.gif in the image folder (I used the ubuntu forums favicon and renamed it to Ubuntu.gif)

Using this method the output will have an extra \n \l but awell. you can edit /etc/isssue if it really bothers you.

if /var/www/sysinfo/distros.ini doesn't exist its because you installed the version thats on apt in which case I don't know which file it would be check /var/www/sysinfo/includes/os

---

### Post by WildTangent on 2006-02-05
Thanks, I've got it displaying correctly now :)

-Wild

---

### Post by SiliconViper on 2006-08-24
If you need an extra set of hands, feel free to summon me. I find great enjoyment in the development of web applications, and this project sounds like something I'd be very interested in contributing to.

[EDIT] Also, Yay necromancy!

---

### Post by cjssmo on 2007-09-09
First your link is down again so I haven't had a chance to see your screen shots, but from what I have read it sound very cool.  When you get some of the major bugs fixed and would like to package it up for Debian/Ubuntu give me a holler.  I have packaged Ampache for Debian/Ubuntu and I would be more than willing to give you a hand in packaging your project.  

Charlie

IRC Freenode #ampache porthose

:guitar:

---

### Post by cjssmo on 2007-09-11
Administering your server via a web interface in on the Ubuntu Server Teams to do list.

[https://wiki.ubuntu.com/AdministerServerViaWebInterface](https://wiki.ubuntu.com/AdministerServerViaWebInterface)

If you are interested you could join the team and have them look at your code.

:)

---

