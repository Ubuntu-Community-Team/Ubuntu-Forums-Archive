---
title: "Server how-to start to finish using Webmin"
date: 2010-04-02
forum: Server Platforms
---

### Post by kevinthecomputerguy on 2010-04-02
I put together this 500+ page .pdf how-to, if your looking to setup a server, and manage it with Webmin.
 
Built on Debian, but should work here to for the most part
 
[http://t3.woodel.com/my-linux-how-to/debian_howto_start_to_finish_using_webmin.pdf](http://t3.woodel.com/my-linux-how-to/debian_howto_start_to_finish_using_webmin.pdf)

---

### Post by haddog on 2010-04-03
> **kevinthecomputerguy said:**
> I put together this 500+ page .pdf how-to, if your looking to setup a server, and manage it with Webmin.
 
Built on Debian, but should work here to for the most part
 
[http://t3.woodel.com/my-linux-how-to/debian_howto_start_to_finish_using_webmin.pdf](http://t3.woodel.com/my-linux-how-to/debian_howto_start_to_finish_using_webmin.pdf)

Great guide Kevin. Found a dependency issue when trying to install webmin on Ubuntu Server 10.04 Beta1. When you try to install webmin, libdm5-perl is not available in any of the lucid repositories.

haddog@mydeb32server1:/options$ sudo dpkg -i webmin_1.490_all.deb
Selecting previously deselected package webmin.
(Reading database ... 66348 files and directories currently installed.)
Unpacking webmin (from webmin_1.490_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin

I resolved the dependency prob by adding the following repository to my /etc/apt/sources.list :

**deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) etch main**

Then I did a sudo apt-get update then sudo apt-get install libdm5-perl installed fine and webadmin installed just as your instructions stated on page 63 of your how-to. BTW. I got a GPG error because I did not import the public key for the debian repos, which doesn't matter to me as I commented out the repos once I got libmd5-perl.

---

### Post by kevinthecomputerguy on 2010-04-03
Nice catch haddog, there will be some slight diffs between ubuntu and Deb.
thanks!

---

### Post by kevinthecomputerguy on 2010-04-05
I posted a new version, fixed some typos and made the firewall stuff a little easier on the eyes
 
-Kevin Elwood  \ kevinthecomputerguy 
 
[http://woodel.com](http://woodel.com) 
 
Under the Solutions tab
version numbers can be found in top right-hand corner of each pdf
 
thank you everyone for the emails and suggestions, i do read them all

---

### Post by essexboyracer on 2010-04-06
Hi Kevin, I really like your HOW-TO/guide. I found it from debian site whilst looking for info for setting up a linux based file/print/email server for a SME about 4 weeks ago, nice to see it linked in from here.

BTW, does anyone know what's the official line on using webmin to manage a server setup based on ubuntu? Last I heard there were two thoughts: 

[LIST]
[*]Webmin did something queer with ubuntu's package management
[*]Webmin wasn't actively maintained, therefore dropped from the repos.
[/LIST]

As far as I can tell it is maintained (a quick visit to webmin.com proves this). I cant comment on the package management though

Any ideas, I am testing out the feasibility of sing linux in our SME environment. Tried ebox already, just started with webmin...

---

### Post by kevinthecomputerguy on 2010-04-06
Hey essexboyracer-
Thanks!

Im not as strong on Ubuntu topics as I would like to be, hopefully someone will chime in if I am wrong.

For your first question: The only Ubuntu related issues I have seen is with the &#8220;Network-Manager&#8221; this can get in the way of a few Network Card changes I have you do in the how-to. But I am on page 115 on my Ubuntu box and haven&#8217;t hit any problems yet.

Second question, Webmin is actively maintained. They even email you back if you&#8217;re having an issue.
 
Webmin is awesome. If you have worries about it at first, just dont expose the management page to the WAN. And or lock it down by source IP. But i have ran it for years and never had a problem. even at its weakest config your login is still SSL encrytped. Its been amazing for me. 

Hope that helps, thanks again

---

### Post by essexboyracer on 2010-04-07
I tried ebox first but left it as I got the feeling that if something misconfigured for some reason it would be trickier to hunt down the config file to make manual amends whereas webmin exposes the config files for you (i think - from what I saw on my test box)

I spent an afternoon reading through your fantastic guide and the only thing that required more in depth reading was the samba section (I am planning to replace our SBS2003 with a webmin server, hence all windows clients).

Keep up the good work!

---

### Post by dominiquec on 2010-04-07
Thanks for the guide. I teach an operating systems class at a university and this will be very helpful for my students (and me.)

---

### Post by kevinthecomputerguy on 2010-04-07
essexboyracer-
Thanks for the kind words. Samba is worth the extra reading because even if you dont use it, setting it up will teach the reader about Linux file permissions. and even the difference between file permissions and share permissions, a topic that is usually avioded :- ) I am a HUGE samba fan!
I am thinking about getting some SAMBA T-Shirts :- )
 
dominiquec-
I have to be careful what i say here, incase i ever want to publish :- )
But lets say someone hacked into my account right now and was replying for me, i cant think
of a better use than at a university, that makes me very happy. 
 
All-
I posted a new version today 3.68 I made the routing portion alot easier on the eyes and included some network maps. I also added an alterative download link (server 1, server 2) too help with the high demand of this file.
 
[http://woodel.com](http://woodel.com) 
 
thanks everyone, and thanks for all the emails, this is great!
-Kev

---

### Post by haddog on 2010-04-07
> **dominiquec said:**
> Thanks for the guide. I teach an operating systems class at a university and this will be very helpful for my students (and me.)

I TOTALLY agree. Kevin, you da MAN. A most excellent guide I must say! Thank you for all your help...now on to SAMBA!

---

### Post by kevinthecomputerguy on 2010-04-07
haddog-
Thanks man!!!
 
A few more qurks between debian and ubuntu
 
-Watchout for that UFW (ubuntu firewall) it will get in the way of my how-to
apt-get remove ufw :- )
 
-That Network-Manager will get in they way too
 
-Also, some of the command line package installs i have you do dont pop-up some of the GUI boxes my how-to mentions.
 
-Prepending sudo to everything or un-lock root
 
Not anything you can't get past, but it doesnt match the printscreens as close as i thought it might.
Sorry if i did a bad thing by posting it in the ubuntu forums, debian and ubuntu have grow apart since i used it last
-Kev

---

### Post by kevinthecomputerguy on 2010-04-08
Hey guys-
 
New version 3.69
[http://woodel.com](http://woodel.com) 
 
-From a connecting client view, Ubuntu's Nautilus windows has like 10 ways of connecting to SAMBA shares, all with different results, so i pasted in a few screen shots in the how-to of how you can connect to them the best. it covers Windows, Ubuntu, and MAC clients. 
 
-The routing part of the how-to forgot to mention you need a static ip for a few of the configuration steps. (fixed)
 
Thanks again for all the kind words
-Kevin Elwood

---

### Post by kevinthecomputerguy on 2010-05-03
Hey guys-
I uploaded a new version that includes Samba groups (version 3.76)
[http://woodel.com]("http://woodel.com/")

---

### Post by essexboyracer on 2010-05-03
Thanks Kevin, have linked to your site from mine, [http://berkhamsted-web-design.co.uk/2010/01/linux-alternative-to-sbs2003-windows-server/](http://berkhamsted-web-design.co.uk/2010/01/linux-alternative-to-sbs2003-windows-server/). Just for good measure.

---

### Post by kevinthecomputerguy on 2010-05-03
essexboyracer-
On my way to go check it out as we speak, that is too cool of you. 
thanks again !
-Kev

---

