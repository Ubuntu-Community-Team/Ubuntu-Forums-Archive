---
title: "difference between ubuntu server and ubuntu Desktop"
date: 2011-10-04
forum: Server Platforms
---

### Post by kannaiah.chinni@gmail.com on 2011-10-04
Hi  Everyone

Is there any difference between ubuntu sever and ubuntu Desktop edition( software side) not hardware side.


what are main features which are included  in ubuntu server rather than  ubuntu desktop edition. I need answer for this question very quickly.  can any one knew the answers please explain to me. 


i knew some basic differences 1) gui 2) kernak diff  3)securtiy(both  user and firewall) 4) databackup 5)mail server 6) lightweight 


is there any difference between rather than above , only technical perspective not hardware.

---

### Post by Jonathan L on 2011-10-04
> **kannaiah.chinni@gmail.com said:**
> Hi  Everyone

Is there any difference between ubuntu sever and ubuntu Desktop edition( software side) not hardware side.


what are main features which are included  in ubuntu server rather than  ubuntu desktop edition. I need answer for this question very quickly.  can any one knew the answers please explain to me. 


i knew some basic differences 1) gui 2) kernak diff  3)securtiy(both  user and firewall) 4) databackup 5)mail server 6) lightweight 


is there any difference between rather than above , only technical perspective not hardware.

Hi Kannaiah

The main difference is that the server version is designed to run without a person sitting in front of it: there's no GUI, and very usually it's run without a screen or keyboard or mouse, and you connect to it via SSH or similar.  If you do have a keyboard and screen, you get a text mode interface to log in.

Normally it runs things like postfix and apache, and these are suggested during the installation. As there is no GUI installed, things like Firefox, Open Office, Inkscape or GIMP are not included, though you could install the GUI and such packages if you wanted to for some reason.

In passing, you can run Ubuntu Server on desktop hardware without a problem, and you can run Ubuntu Desktop on server hardware, so long as it has a suitable display adapter, though usually the graphics are a bit slow.

So the answer is more of a design intention rather than a black-and-white difference.  And this is expressed in one of the most important differences: the support time for the versions.  You'll see that the "long-term-support" versions have five-year support from Ubuntu.  Which means that your servers can run uninterrupted for a longer period: this is actually one of the critical features for professional server management, and hence the design decisions for the server version tend to be more conservative than that for the desktop version.

Hope that helps

Kind regards
Jonathan.

---

### Post by kannaiah.chinni@gmail.com on 2011-10-04
Hi

Thanku for reply.


these are normal issues. i knew these things.which are the things u said , same info i told to my head but she says that those are normal ones. what are the difference between server and desktop edition as  software side. why they developed server edition rather than desktop. if both versions have same software requirements then what is the use of server.

i hope that u will understand my question

from

karunakar
(senior programmer)
univeristy of Hyderabad

---

### Post by adit on 2011-10-04
Ubuntu Desktop edition - meant to be used for tasks like internet browsing, word processing, image editing etc
Ubuntu Server edition - meant to be used for tasks like serving webpages
Which edition should you use?  It depends on what purpose you are going to use your software.
Your questions are
> why they developed server edition rather than desktop
> if both versions have same software requirements then what is the use of server
The simple answer to your questions is performance.  You can use Desktop edition in the place of Server edition if you want.  But it will serve webpages slowly.

---

### Post by collisionystm on 2011-10-04
> **kannaiah.chinni@gmail.com said:**
> Hi  Everyone

Is there any difference between ubuntu sever and ubuntu Desktop edition( software side) not hardware side.


what are main features which are included  in ubuntu server rather than  ubuntu desktop edition. I need answer for this question very quickly.  can any one knew the answers please explain to me. 


i knew some basic differences 1) gui 2) kernak diff  3)securtiy(both  user and firewall) 4) databackup 5)mail server 6) lightweight 


is there any difference between rather than above , only technical perspective not hardware.

The Kernel. It has been optimized for different tasks. It has a lower Memory footprint.

---

### Post by haqking on 2011-10-04
What's the difference between desktop and server?
From [https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F)

The first difference is in the CD contents. The "Server" CD avoids including what Ubuntu considers desktop packages (packages like X, Gnome or KDE), but does include server related packages (Apache2, Bind9 and so on). Using a Desktop CD with a minimal installation and installing, for example, apache2 from the network, one can obtain the exact same result that can be obtained by inserting the Server CD and installing apache2 from the CD-ROM.
The Ubuntu Server Edition installation process is slightly different from the Desktop Edition. Since by default Ubuntu Server doesn't have a GUI, the process is menu driven, very similar to the Alternate CD installation process.
Ubuntu server installs a server-optimized kernel by default.
Ubuntu Desktop will receive 3 years of support, while Ubuntu Server will be supported for 5 years.


From [http://en.wikipedia.org/wiki/Ubuntu_(operating_system](http://en.wikipedia.org/wiki/Ubuntu_(operating_system))

The main difference between the two editions is the lack of a default installation of a X window environment in the server edition, although GUIs can be installed like GNOME/Unity (Ubuntu 11.04), KDE (Kubuntu 11.04), XFCE, (Xubuntu 11.04), as well as more resource-economical GUIs such as Fluxbox, Openbox and Blackbox. Kernel versions also differ. The server edition uses a screen mode character based interface for the installation, instead of a tarted-up graphical installation process. The server CD also has the option of installing Ubuntu enterprise cloud.[76]
Ubuntu Server is also distributed free of charge. Users can choose to pay for consulting and technical support. Annual support contract with 9x5 business hour support is about $750 per server, and a contract covering 24x7 over a year costs $1,200.[75]

---

