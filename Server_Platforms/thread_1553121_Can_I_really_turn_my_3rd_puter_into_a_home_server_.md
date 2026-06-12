---
title: "Can I really turn my 3rd puter into a home server How?"
date: 2010-08-14
forum: Server Platforms
---

### Post by Bushcraft Bill on 2010-08-14
I just started using Ubuntu on my home computer got tired of windows as I am sure many here have but I just noticed that their is a server addition and I was wondering if I could use my old desktop that I have/use as backup in case windows on my laptop crashed if I can use that desktop for a home server and access it with mine and my wifes laptop is it basically a plug and play or is their some serious setup involved in doing so? just want to know before jumping in! I am no guru but can figure stuff out pretty good on cranky puters....

---

### Post by cj.surrusco on 2010-08-14
You sure can set that old computer up as a server. I have two old Dell desktops set up as servers in my home at the moment. Just download the Ubuntu server .iso from ubuntu.com and install it on the desktop just like a normal Ubuntu install. 

When you get to the package options during the install, install ssh server (so that you can remotely access from other computers). Then after the install you can use sftp (part of ssh), smb or ftp to share files. There are plenty of tutorials you can find on those protocols.

---

### Post by drdos2006 on 2010-08-14
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by Bushcraft Bill on 2010-08-14
ok thanks for the info but it says I need 2 hard drives I only have one on the desktop at the moment looks like I will have to put this project on hold till I can get a second hardrive put in...

---

### Post by drdos2006 on 2010-08-14
No you do not need a second HDD in your server if your HDD is large enough. You can also set up your server with the Desktop version of Ubuntu, make the IP address of the server a fixed IP and remove extra packages like OpenOffice, Games etc. The HOWTO gives you information which is very, very detailed and allows you to remotely control settings via Webmin. If that is overkill, then keep it simple.

regards

---

### Post by cj.surrusco on 2010-08-14
> **drdos2006 said:**
> No you do not need a second HDD in your server if your HDD is large enough. You can also set up your server with the Desktop version of Ubuntu, make the IP address of the server a fixed IP and remove extra packages like OpenOffice, Games etc. The HOWTO gives you information which is very, very detailed and allows you to remotely control settings via Webmin. If that is overkill, then keep it simple.

regards

I wouldn't recommend using the desktop version as a server. There are many extra packages that the GUI uses and also the GUI will eat up load averages.

---

### Post by Bushcraft Bill on 2010-08-20
OK if I don't need a second HD I think I will give this a go!

Questions? if I do add a second HD later is it not a big deal to change the setup to use it to then?

I have a d-link router with two computers hardwired use and one wireless use for internet access so I should be good to go then to setup the server?

> **drdos2006 said:**
> No you do not need a second HDD in your server if your HDD is large enough. You can also set up your server with the Desktop version of Ubuntu, make the IP address of the server a fixed IP and remove extra packages like OpenOffice, Games etc. The HOWTO gives you information which is very, very detailed and allows you to remotely control settings via Webmin. If that is overkill, then keep it simple.

regards

---

### Post by cj.surrusco on 2010-08-20
Yep, you should have no problem adding the secondary hard disk later. Also, as long as the connection is wired, you shouldn't have any problems with that either.

---

### Post by Bushcraft Bill on 2010-08-20
Thanks for the info I will work on it over the next few days and see how it goes...

Question? yes I am full of them I know.. can I use the server as a file server for my forums as my host does not allow me to have files on the site for downloading....would love this as a workaround if I can do it!

I do have a fixed IP

---

### Post by Bushcraft Bill on 2010-08-20
well gave it try this morning and no go seems the old desktop is to old for the server software to work on it...

A big thanks to everyone that tried to help me out I have been very impressed with the quick responses I have gotten to my requests for info...

---

### Post by Bushcraft Bill on 2010-08-20
OK I need better reading skills!

I noticed that I must have downloaded the 64 bit version I am now getting the 32 bit version hope this one will work back later with news on how goes it...

---

### Post by Bushcraft Bill on 2010-08-21
I got the server up and running and am able to log into the server with my laptop now how cool is that....

---

### Post by 1serveyou on 2010-08-21
Now make sure to turn off remotely logging in as root, if you haven't done it already. I checked my a week after I had done that, and noticed I had a handful of attempts on it. Also I'd reccomend fail2ban so they can only attempt putting a password however many times you want. You can set it up so after 5 failed attempts their ip is banned for 10mins, this comes in handy for people sniffing out open servers. I'm still a newbie as well, and have learned so much more about servers/networking. It can get very frustrating, but just walk away, and come back, then it usually works :D

---

### Post by Bushcraft Bill on 2010-08-21
no idea were/how to turn off remote logging in..

the fun is starting for me right now I am stuck at setting up my ftp as a file that needs to be edited is not their so I think that all the ftp needed files are not on my server and do not know how/what I need to get so I can set it up...

I am enjoying working on it and always ready to learn more so love the challenge of setting up the server the more things that don't work the more I learn about it in the end...

I turn it off when I am not working on it...
 

> **1serveyou said:**
> Now make sure to turn off remotely logging in as root, if you haven't done it already. I checked my a week after I had done that, and noticed I had a handful of attempts on it. Also I'd reccomend fail2ban so they can only attempt putting a password however many times you want. You can set it up so after 5 failed attempts their ip is banned for 10mins, this comes in handy for people sniffing out open servers. I'm still a newbie as well, and have learned so much more about servers/networking. It can get very frustrating, but just walk away, and come back, then it usually works :D

---

### Post by 1serveyou on 2010-08-22
Glad your enjoying it. In the link below will show you how to do it.

[http://www.sucka.net/2010/03/how-to-disable-root-access-via-ssh/](http://www.sucka.net/2010/03/how-to-disable-root-access-via-ssh/)

---

### Post by Bushcraft Bill on 2010-08-22
Thanks for that link that helps allot...

I also figured out my ftp problem seems for some reason vsfpd did not get installed yee haa now I can get that setup....

their is allot to setting up a server gives me a bit more incite as to what my hosts have to deal with...

---

### Post by Bushcraft Bill on 2010-08-22
This is so cool I have my own web page and ftp working now...

Ill be one of the big boys in no time LOL.....

and thanks to all that have helped me get this far! ):P

---

### Post by Bushcraft Bill on 2010-08-22
I pretty well got things working I am happy I got this far with things...

Except for one thing I as administrator can get in and send mail to any user on the server but what I could not figure out is how do users logged into the server get mail as I just want this setup locally between my laptop and the wifes I cant figure out how the wife's computer can get to mail? and how do I let someone else in and get to mail again it would just be sent locally/server and not outbound to the net ...

what I want to do at some point is setup mysql so I can setup some database run stuff like wordpress or forums...if you can steer me to how to set that up on the server would be great...

also do you have to install php at all or is that just their? or is their loads more to setup so that I could get wordpress working?

Bill

---

### Post by 1serveyou on 2010-08-22
> **Bushcraft Bill said:**
> I pretty well got things working I am happy I got this far with things...

Except for one thing I as administrator can get in and send mail to any user on the server but what I could not figure out is how do users logged into the server get mail as I just want this setup locally between my laptop and the wifes I cant figure out how the wife's computer can get to mail? and how do I let someone else in and get to mail again it would just be sent locally/server and not outbound to the net ...

what I want to do at some point is setup mysql so I can setup some database run stuff like wordpress or forums...if you can steer me to how to set that up on the server would be great...

also do you have to install php at all or is that just their? or is their loads more to setup so that I could get wordpress working?

Bill

Glad you are progressing so well! Sorry I can't help you out with that, but [http://www.howtoforge.com/howtos/linux/ubuntu](http://www.howtoforge.com/howtos/linux/ubuntu) has always been good to me.

---

### Post by Bushcraft Bill on 2010-08-23
I will check that out and see how that works for....thanks!

---

### Post by quietas on 2010-08-23
For home server ideas, take a look at this link ([http://ubuntuforums.org/showthread.php?t=1075599]("http://ubuntuforums.org/showthread.php?t=1075599")). I started it back when I was building up my home server and a lot of good ideas were tossed around by forum folks.

---

### Post by Lars Noodén on 2010-08-23
> **Bushcraft Bill said:**
>  vsfpd did not get installed 

That's good. FTP is not needed unless you plan on publishing Anonymous FTP.  That's for read-only file download.  (FTP, the protocol, is very insecure. FTPS is not much better and is very difficult to set up, relative to SFTP.)

If you installed OpenSSH server, then you have everything you need to work with files on the server. Your file manager (Dolphin, Nautilus, Konqueror) probably has SFTP support built in.  Alternately you can add sshfs and the server will look like a folder on your desktop.

If there was some documentation pointing you to FTP instead of an encrypted option like SFTP then it would help others if you drop the author a line to update their material.

---

### Post by Bushcraft Bill on 2010-08-25
well I go things sorted out I have ftp working I can setup and get to web space on the server..

I think I have mysql setup so I can setup programs like wordpress I have to work on that part tomorrow to see if I can setup the database for it if so I will be happier than a pig in s*** 

the only thing I am debating to setup is mail now ether for internal or external mail I really have no need of internal mail setup....would like your comments on this!

I buggered things up and am at reinstall no#5 learned allot by buggering things up the last 4 installs real gooooooodddd......

they do have to make some of the install of programs preset and bundled more though the setup on allot of stuff could already be pre done I have played around with installing allot of software in the past and figure things out eventually as I keep at it but I can see for newbies this is just way to much to deal with...

---

### Post by Bushcraft Bill on 2010-08-25
I want the ftp as my site host does not allow file storage so this gives me a way around that and I also have a few users that want a place to store files that are useful to other users so this will give me those options for me and my users now...

> **Lars Noodén said:**
> That's good. FTP is not needed unless you plan on publishing Anonymous FTP.  That's for read-only file download.  (FTP, the protocol, is very insecure. FTPS is not much better and is very difficult to set up, relative to SFTP.)

If you installed OpenSSH server, then you have everything you need to work with files on the server. Your file manager (Dolphin, Nautilus, Konqueror) probably has SFTP support built in.  Alternately you can add sshfs and the server will look like a folder on your desktop.

If there was some documentation pointing you to FTP instead of an encrypted option like SFTP then it would help others if you drop the author a line to update their material.

---

### Post by Bushcraft Bill on 2010-08-27
Well wanting to get a domain name and point it to the server sounds easy enough...


I been reading a bit on a program bind9 and figured out that its needed if I want to point domain names to websites on the server no idea on the process of how thats done though yet and what this bind9 has got to do with it all detailed info would be nice on how to point domain names to websites I think I found info on setting up bind9 so will try getting that at least setup over the next day or so...

---

### Post by Bushcraft Bill on 2010-08-27
OH ya I did it I now have a couple domain names yee haa I am one happy camper well its all setup for what I need it for I am keeping mail internal and not bothering with setting up outgoing internet email kind of nice to have it private and all....

steep learning curve for sure for a newbie only took me tops what one week the dns names threw me for a loop though but its easy as pie once you have the names setup all I did was use the same name put in my ip and the router and the server took care of it all..

only problem I had with the router was that I had to let it forward port 80 to the server and wallah it all came together Sweet!

here is list of threads with info that got me going in order of usefulness:

These 3 should get you up and running all you will have to setup extra on top of this would be an outgoing mail server to the internet otherwise you have an internal email setup you can use between you and users only

[http://woodel.com/](http://woodel.com/)
[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp)
[http://www.sucka.net/2010/03/how-to-disable-root-access-via-ssh/](http://www.sucka.net/2010/03/how-to-disable-root-access-via-ssh/)

I give big thanks to contributers could not have done it without ya!

not so much help needs way more information on setup...
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

make sure port 80 is pointed to server ip
when getting domain name use same login name as user account name and your good to go could not believe it was that easy to do!

So now that thats over with hows the weather!

Bill

---

### Post by Bushcraft Bill on 2010-08-27
things are good installed wordpress and a forum all is working great!

---

