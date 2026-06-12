---
title: "Macromedia Flash Media Server 2"
date: 2006-06-09
forum: Server Platforms
---

### Post by SteffJay on 2006-06-09
:confused: Hello Folks. I am having a great problem with the Flash server on Dapper Drake 6.06.  First of all, has anyone managed to do this yet ? as this is the only thing stopping me from migrating from a M$ box to a Linux (Ubuntu) box. I have a great deal of experience with windows but this beats the hell out of me. I'm commonly known as a noob, where this is concerned. I installed RedHat ES 4 and managed to get it working on there but i really like this distro and want to use this for hosting my website. I am reliably informed that with the core of Ubuntu is of the same architecture as RedHat so it should work (in theory). Any help will be greatly appreciated.

---

### Post by SteffJay on 2006-06-10
Further to my last post.....  here is a copy of the installation log of Flash server:

Do you agree with the license agreement? (y/n): y


Macromedia Flash Media Server 2.0 requires approximately 25MB of
disk space.

The installer will install Macromedia Flash Media Server 2.0 in the
following directory
Default [/opt/macromedia/fms]: /var/www/macromedia/fms


The Macromedia Flash Media Server communicates on the IANA-assigned
port of 1935, which is the port most Flash applications expect.

Please enter the Macromedia Flash Media Server port
Default [1935]: 1935

Please enter the port to use for the Admin service. You can only specify one
admin port.
Default [1111]: 1111


The administrative user name and password you provide here is required to use
the Macromedia Flash Media Server Management Console for
administration, monitoring, and debugging.

Please enter the administrative username: justme

Please enter the administrative password:******
Confirm password:******


When the Macromedia Flash Media Server service is started, the service
can be run as a user other than "root". The server would change to this user
when the server is started and has acquired its ports.

Please enter the user that the Macromedia Flash Media Server service will run asDefault user [nobody]: steff

Please enter a valid user group for the "justme" user: justme


Do you want the Macromedia Flash Media Server service to run as a
daemon? (y/n)
Default [y]: y


Do you want to start the Macromedia Flash Media Server
after the installation is done? (y/n)
Default [y]: y


----------- Install Action Summary -----------

Installation directory         = /var/www/macromedia/fms

FMS Server Port                = 1935
FMS Admin Server Port          = 1111

Administrative username        = justme
Administrative password        = (suppressed)

FMS owner                      = justme

FMS service user               = justme
FMS service user group         = justme

FMS run as daemon              = Yes
Start FMS                      = Yes

Proceed with the installation? (y/n/q): y

Installing Macromedia Flash Media Server files...
Configuring Macromedia Flash Media Server...
Adding "fms" service.
Setting default admin to "fms".
./installFMS: line 811: /sbin/chkconfig: No such file or directory
Setting autostart for "fms".
Server:fms command:start
./server: line 14: [: unlimited: integer expression expected
NPTL 2.3.6
Starting Macromedia Flash Media Server (please check /var/log/messages)

Admin server:fmsadmin command:start
Starting Macromedia Flash Media Admin Server (please check /var/log/messages)


The Macromedia Flash Media Server installation is complete.

root@server:~/Desktop/flash#

---

### Post by kiruva on 2006-06-14
Hi

This should be fairly simple to fix..
You need to create a couple of symbolic links for fms to work..
And I'm sorry for not remembering if it was .4 or .6 versions..but I'll give you both versions of both libs..

in /usr/lib you'll find:
libcrypto.so.0.9.8 and libssl.so.0.9.8

create links like this:
ln -s libcrypto.so.0.9.8 libcrypto.so.4
ln -s libcrypto.so.0.9.8 libcrypto.so.6
ln -s libssl.so.0.9.8 libssl.so.4
ln -s libssl.so.0.9.8 libssl.so.6

restart or start fms...
/etc/init.d/fms <start|restart>

Let me know if this wasn't the solution for you..
BTW: I'm running Dapper now, but the libs should be the same for Breezy..

---

### Post by SteffJay on 2006-06-14
Can i contact you on either MSN or ICQ ? add me as [email]steffjay@hotmail.com[/email] Thanks. I have adjusted what you have suggested, **ln -s libcrypto.so.0.9.8 libcrypto.so.6** & **ln -s libssl.so.0.9.8 libssl.so.6** (i'm also using Dapper) it seems to be working as i can enter it using an external (Windows) browser into the admin section. If i use the internal browser (Firefox) all i see is this: [http://www.steffsoft.com/fms.jpg](http://www.steffsoft.com/fms.jpg) It will not recognise any IP addresses, eg: 192.168.1.103 or even the web address. The router has all the relevant ports assigned, 1935, 1111, 80 etc. and the web site is all working and pointing to 192.168.1.103. Every time i enter any type of IP it just rejects it. Any ideas ?????

---

### Post by kiruva on 2006-06-15
Yeah..That's a different problem again :P
That be the flashplayer...

Try following the ubuntuguide/wiki
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

I used to have that problem too, but using the nonfree package makes it all work :-)

Let me know how that works out.. :?:

---

### Post by SteffJay on 2006-06-15
Hello Kiruva. Tried your suggestion, unfortunately, it did'nt work out ===

server:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree  :(   

Seem's as though i'm not going to get this monster to work !! Very annoying as i have loaded everything else and they all work fine. A little more help would'nt go amiss !!

---

### Post by ewtesterman@cox.net on 2006-06-15
I believe this means you have not enable universe or multiverse. You need to do the following
sudo /gedit/etc/apt/sources.list
uncommment all of the deb lines and the ones that end in universe add a blank space followed by "multiverse". Then sudo apt-get update and then try your install.

---

### Post by kiruva on 2006-06-16
Just a side note..as there was a small typo in that last comment there..
You probably caught that one, but just to be sure add the PLF repo too..

Follow the Dapper Wiki on adding repos..
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by SteffJay on 2006-06-16
:confused:  I have updated the source.list but it still cannot find the non-free plugin !!!!!!

---

### Post by kiruva on 2006-06-16
OK..This is actually out of server talk now, but..

Are you sure you created your sources.list in /etc/apt/ exactly like the one shown here:
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Remember the last one..The PLF repo..

Then do:
apt-get update

Try searching for it:
apt-cache search flashplugin
Should give you only one alternative:
flashplugin-nonfree

To install that do:
apt-get install flashplugin-nonfree
then
update-flashplugin

And remember sudo if you haven't gone around that...

---

### Post by SteffJay on 2006-06-16
OK !!!!!!  excelent stuff, flash player is now installed and running (thanks to **Kiruva**) ;)  !!  Now i still have the problem with getting the FMS2 to connect to my IP. Everything i put into it, it says it cannot connect !!! :mad:  ie: 192.168.1.103 or 127.0.0.1 or even my hosting address !!  Anybody ?????????

---

### Post by kiruva on 2006-06-16
I'm not shure I'm following you on this..
You got your FMS2 installed correctly?
Are the FMS services running?

Check using:
ps aux | grep fms

You should get atleast 4 lines with something about fms..
Like: fmsadmin fmscore fmsedge etc etc..

If it is not running, start the service:
/etc/init.d/fms start
Might take a while before returning the cmdline..

Now what is the problem?
You can't connect to it using the FMS2 Console (swf)??

Edit:
If you open up the fmsconsole swf in firefox, does it still display like the picture you posted?

Edit:
I just looked over your install log...
I would advise you to reinstall into /opt/macromedia/fms and not /var/www
The fms installation shouldn't be installed into a accessible folder like /var/www
Also the justme user and group does exist right?

---

### Post by SteffJay on 2006-06-16
To be honest **kiruva**, i'm not sure if i have set up my dns properly......  :sad: but i'll certainly try what you said. I really appreciate all the help you are giving me !! ;) 

Ok. I have this when i do the grep fms = 

root@server:~$ ps aux | grep fms
root    12266  0.0  0.1   1636   504 pts/0    R+   15:35   0:00 grep fms

root@server:~$ /etc/init.d/fms start

root@server:~$ ps aux | grep fms
root    12385  0.0  0.1   1632   488 pts/0    R+   15:39   0:00 grep fms

root@server:~$

It is running, as far as i can see. I have even added fms as a user / group, just in case that was causing a problem. I get nothing about fmsadmin, fmscore, fmsedge etc but it is still not connecting to my IP address. All it reports is that it cannot connect and puts a requester on screen asking for another type of connection [http://www.steffsoft.com/error.jpg](http://www.steffsoft.com/error.jpg) Everything else that is pointed to 192.168.1.103 connects just fine....   :sad:  I have tried to run fmsadmin fmscore fmsedge etc in sudo but it does not even recognise they are there !!  even fmsmgr !!  nothing...  :mad: !!  Grrrrrrrrrrrrrrrrrrr !!!!!!

---

### Post by SteffJay on 2006-06-17
Is this [http://www.steffsoft.com/error.jpg](http://www.steffsoft.com/error.jpg) telling me that my log in credentials are wrong ???  or that it cannot connect to my IP address ?

---

### Post by kiruva on 2006-06-17
No Problem :-)

But, your ps aux output shows that the services are not running..

Do you have symbolic links to the libs like I mentioned?
Follow this procedure(as root):
cd /usr/lib/
ln -s libcrypto.so.0.9.8 libcrypto.so.4
ln -s libssl.so.0.9.8 libssl.so.4
/etc/init.d/fms start

Now try connecting..

I think it is the so.4 that is needed..
I told you to create both .4 and .6 links earlier, but I think only .4 is needed..
And if your post is correct you only created .6 :-)

And fms services are NOT running, so it is no wonder you can't connect :-)

Don't worry, almost there :-)

---

### Post by SteffJay on 2006-06-18
OK **Kiruva**  :D  That seems to have done the job  =D> !!!!  Excelent !!!!  Thank you for your patience and help on this, very much appreciated. Only one more thing to do now......  install Verlihub....  thats causing errors and their forum is down.....  Unless you know anything about installing it, i shall start another thread. Ahhhhh, just found one ;) Thanks again.  ;)

---

### Post by SteffJay on 2006-06-19
As a matter of interest, how can i set FMS up to auto-start when Dapper powers on ???? I have tried **/etc/init.d/fms start** in systems/prefs/sessions/startup programs but it will not auto start !! Any ideas ??

---

### Post by kiruva on 2006-06-19
Yupp
Here is what I did..

ln -s /etc/init.d/fms /etc/rc1.d/K20fms
ln -s /etc/init.d/fms /etc/rc2.d/S20fms

That should be sufficient..
There probably is a better way to do this, but it isn't long ago since I switched from Gentoo, so I haven't quite gotten used to all "debian" stuff yet :-)
And since rc-update doesn't 'to my knowledge' exist on ubuntu/debian, I created the stuff manually!!

It works...And that's what matters :P

---

### Post by annazack on 2006-06-21
Hi,
I have the nonfree flash installed but the command: 
update-flashplugin

left me with:
installation failed

What can I do next?

//Anna

---

### Post by SteffJay on 2006-07-02
The web site may be down or busy. Try again at a later time !!  ;)

---

### Post by cjmartin on 2006-11-27
Hi,

I've been working on getting FMS installed on ubuntu dapper server (so much less installed by default than the desktop version). And with the help of this forum, I have figured it out. I thought I would add a few things to this thread that will help others get this going.

#1. Add a file to /etc called redhat-release that contains the following line:

Red Hat Enterprise Linux ES release 4 (Nahant Update 2)

#2. Create the softlinks as described above:

cd /usr/lib/
ln -s libcrypto.so.0.9.8 libcrypto.so.4
ln -s libssl.so.0.9.8 libssl.so.4

#3. Now, I think that should work for most, but if like me you are running server, you also need to install libnspr4.so:

apt-get install libnspr4

Hopefully this will help anyone having more problems...

I'm going to try again getting this going in edgy, I'll post as to how it goes.

---

### Post by cjmartin on 2006-11-27
Ok, no go on Edgy.

Here's what I get at the end of the FMS installer script:

Installing Macromedia Flash Media Server files...
Configuring Macromedia Flash Media Server...
Adding "fms" service.
Setting default admin to "fms".
./installFMS: 813: /sbin/chkconfig: not found
Setting autostart for "fms".
Server:fms command:start
ulimit: 13: Illegal option -u
[: 16: 32768: unexpected operator
NPTL 2.4
./server: 49: Syntax error: Bad substitution
Admin server:fmsadmin command:start
./adminserver: 40: Syntax error: Bad substitution

The Macromedia Flash Media Server installation is complete.

Anyone have any ideas/gotten this to run on Edgy?

Thanks

---

### Post by mbertheau on 2006-12-25
I've gotten this to work:

[http://www.bluetwanger.de/blog/2006/12/25/installing-flash-media-server-2-on-ubuntu-610-edgy/](http://www.bluetwanger.de/blog/2006/12/25/installing-flash-media-server-2-on-ubuntu-610-edgy/)

---

### Post by malinkie on 2007-01-26
I followed that example but it did not work for me :(

Has anyone else had any sucess installing FMS2 in Edgy?

---

### Post by mbertheau on 2007-01-26
If you had mentioned how exactly it didn't work, I maybe could have helped you.

---

### Post by malinkie on 2007-01-26
yeah, at the time i posted that i was kinda annoyed and didnt want to get into it :) I'll post the errors once i get home.

---

### Post by Mistoffeles on 2007-04-24
Adobe clearly states that Flash Media server will only run on Red Hat Enterprise Linux or Netware SuSE Enterprise Linux.

Why it will only work on those is something I don't know, but it may be something arbitrary that Adobe has done to make it not run on any other flavour, or it may require some changes. I do know that there are some significant differences between Ubuntu and Red hat Enterprise Linux, due to the fact that Debian (on which Ubuntu is based) does things in a much different way than RHEL. It may be a true binary incompatability, on the other hand it may only be something Adobe coded into the software.

---

### Post by ren_sierra on 2007-05-22
Newbie help:....

How do you install flash media player? is the installer available from feisty repositories?

---

### Post by mbertheau on 2007-05-22
See here:

[http://www.bluetwanger.de/blog/2006/12/25/installing-flash-media-server-2-on-ubuntu-610-edgy/](http://www.bluetwanger.de/blog/2006/12/25/installing-flash-media-server-2-on-ubuntu-610-edgy/)

---

### Post by remedy on 2007-12-19
Thanks for the link - this solved my problem!

---

### Post by nmz787 on 2008-04-22
> **mbertheau said:**
> See here:

[http://www.bluetwanger.de/blog/2006/12/25/installing-flash-media-server-2-on-ubuntu-610-edgy/](http://www.bluetwanger.de/blog/2006/12/25/installing-flash-media-server-2-on-ubuntu-610-edgy/)

worked for me, now there is a patch for the FMS 3

---

