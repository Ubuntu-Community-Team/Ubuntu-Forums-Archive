---
title: "Ubuntu server setup guide"
date: 2010-10-08
forum: Server Platforms
---

### Post by DrImago on 2010-10-08
Hi all,

I am completely new to everything linux, however I decided that it was time to do something with an old pc I had and I was thinking of setting it up as a home server. I look around for an easy guide on how to set up the server from the begining but I can't seem to find one that's good for a complete beginner like me.

What I would like to do is to had the server as a place where I keep all my movies, music etc and be able to acces it from my home network and also from outside of it. Also, I would like to connect my two printers to this server and share them on the network.

Is there a place where I can find simple information about what I want to do and is it possible for a complete beginner like me to do what I want to do?

Cheers,

---

### Post by spiky001 on 2010-10-08
Hi yes it is easy to do Are you ok to use terminal for all your work i,e if you install the server version it only has terminal, I installed the desktop version and use that

---

### Post by DrImago on 2010-10-08
Hi there,

Thanks for the reply! Yes I should be fine with writing commands in the terminal window. But is there any way to get a GUI in the server version? I know this isn't the common practice but I like to visualise what I do too. I guess this is the bad habbits i got from windows :P

If there is no way for a GUI, no probs :) I'll do the command line.

---

### Post by lisati on 2010-10-08
One option is the "server edition" of Ubuntu, described here: [http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/) - it doesn't come with a GUI, but you can easily install one.

---

### Post by DrImago on 2010-10-08
Cool stuff, I will ckeck it out this evening when I will install ubuntu server again.

I will install a GUI to see what I am doing and then I will come back here to ask question or look for answers.

I am liking this ubuntu :D

---

### Post by DrImago on 2010-10-08
Ok I have reached the point in the instalation where I have to chose what software to install from the following list:

DNS server
LAMP server
Mail server
OpenSSH server
PostgreSQL database
Print server
Samba file server
Tomcap Java serger
Virtual Machine host
Manual package selection

Is there a description of what each of these is doing and which one should I install?

Cheers,

---

### Post by Seewolf on 2010-10-08
You may want to start with one of the guides in the sticky threads of the "Server Platforms" section of the forum.  I am like you and a complete newbie at anything outside windows but have found one guide in there that has walked me through, step by step, to have a complete Samba server (for internal shares on my home network) and Apache server (for hosting websites).

The complete tutorial I have been using is at:

[http://woodel.com/](http://woodel.com/)

Download the latest version in .pdf and walk through.  One suggestion I have, is to use Debian for the server if you are going to use this tutuorial.  I tried it once with Ubuntu but found that there are some differences that made it worth starting over with Debian.  I would also warn you that this is not a 10 minute effort.  Take your time and follow the instructions.

Good luck!

---

### Post by DrImago on 2010-10-08
Thanks a lot for your reply. I am not expecting it to be a 10 minute thing. I will read through the tutorial.

On dumb question though, you mention using debian. is that a version of linux or is it something integrated in ubuntu? I only have ubuntu installed. Iknow...really dumb question...sorry

---

### Post by Seewolf on 2010-10-08
The only dumb question is the one that isn't asked.

Debian is a different distribution of Linux, it is the basis for Ubuntu.

The big advantage I have seen with Ubuntu over other Linux distributions is the Graphic interface on the desktop version.  My intent when I was building my server was to have it managed remotely (headless).  Once I got the basic system installed, I removed the monitor and keyboard.  I use a program called Webmin to administer the server through other computers on my network.  Since I am working the system remotely through a web based interface, a graphic interface on the server itself is no longer needed.

One advantage of using Debian for this is that when you do need to use command line, you can log in as the root user and avoid using the "sudo" command.

So far it has worked well for me, there have been some hiccups, but I think that will happen anytime you are working a project like this.

---

### Post by DrImago on 2010-10-08
Ok I see... I mentioned the GUI earlier because I thought it would make the installation of the server a less painfull process but I don't need the GUI in the long run. However I don't mind the command line at all so I will not even try to install a GUI. I would like to be able to manage the server remotely too but the rest of my computers are running windows. Will I be able to use this Webmin program to manage the server? Or are there other similar programs? Cheers, for the patience.

---

### Post by Seewolf on 2010-10-08
Webmin is web based and works through your browser.  It has been great for me.  I run Ubuntu on a laptop, XP on one of my desktops and Win7 on another.  I have used Internet Explorer and Firefox with no problems. There are some modules within the program that require Java, but as long as you have a web browser with Java installed, you will be good to go.   

Getting Java running on Firefox took a few minutes to figure out, but it runs fine now.

---

### Post by DrImago on 2010-10-08
Right at this point I am back at the screen where I have to chose what software I want to install. The guide here [http://woodel.com/](http://woodel.com/) says to deselect everything apart from Standard system. The problem is that in Ubuntu server there is no such choice. Shall I just go on and skip this step with selecting software?

---

### Post by DrImago on 2010-10-08
there are significant differences between what i see in the ubuntu server and the guide. one of them is when i got to write the big line where it installs the samba (which btw is samba4 now) and other stuff. in the guide it says that there will be a gui to sonfigure the samba. there isn't and I don't know how to get it to appear.

Any ideas? Please :)

---

### Post by Seewolf on 2010-10-08
I assume you have a CD that you are using to start the install.  When you burned the iso file, did you get the Ubuntu server edition or are you using the desktop version?  Make sure you have the server edition or, better yet, get the Debian version linked in the tutorial to make sure you have everything match the tutorial exactly.  You can always go back and do updates later if you want.  The Samba setup comes up pretty far along in the tutorial and you can do the configuration through the Webmin GUI.

The tutorial works best if you follow it step by step without skipping anything until you get to some of advanced stuff.  I found that Ubuntu didn't work out as well when I tried it and ended up using Debian.

One other tip - when you get to the section where you are installing a bunch of packages at once, copy the line into something like Notepad in Windows to make sure you are not accidentally copying a hard return that breaks up the command when you put it into the command line (I used Putty).  I struggled with that for a while until I finally figured out that the complete command was not being pasted and only part of the command was being executed.

---

### Post by DrImago on 2010-10-08
I have the server version of ubuntu and so far i have followed everything to the letter. but this thing with the samba is different. he says in the guide that a blue gui screen should come up to configure some stuff in samba. but there isn't such a thing. eh well i will keep poking around.

---

### Post by Seewolf on 2010-10-08
After you did the command "apt-get install samba smbfs ssh dhcp3-server dnsutils apt-show-versions" did you see any errors or additional packages that had to be installed?  I am assuming that you are using sudo before all the commands in the command line too since you are using Ubuntu server.

---

### Post by DrImago on 2010-10-08
there were no errors it just proceeded to download and install the packages and then it told me that the stuff is installing in the background.

i am not using the sudo because i activated the root account.

---

### Post by Seewolf on 2010-10-08
I don't remember if I had the same thing happen when I did my Ubuntu server install, I do know that there were some differences from the tutorial but I was able to get it up and running with Samba shares.

Good luck!  It is quite a sense of accomplishment when you get everything running.

---

### Post by DrImago on 2010-10-08
i have made a lot of progress. i am now configuring the server through putty which is an amazing achievement for me :D

i have one question thou. whenit says ldconfig deferred processing now taking place
how can i check when it is finished? so i can start a new task?

---

### Post by Seewolf on 2010-10-08
I did not run into that issue.  Is it happening after running an update to Ubuntu?  It looks like an issue with Ubuntu.  I did a little digging around and see some old reports of " ldconfig deferred processing now taking place" hanging up during the cleanup phase.

I'm not sure if this is the same issue, but it looks like the same symptom:

[https://bugs.launchpad.net/ubuntu/+bug/280478](https://bugs.launchpad.net/ubuntu/+bug/280478)

---

### Post by DrImago on 2010-10-08
I am not sure this is an issue, it was more like a curiosity. the issue i am having now is with the libmd5-perl install. it says that it can't find that package. i have no clue what to do from here...

---

### Post by DrImago on 2010-10-08
ok i found something here, seems that there is an issue with that package.

[http://www.kelvinwong.ca/tag/libmd5-perl/](http://www.kelvinwong.ca/tag/libmd5-perl/)

i hope this works

---

### Post by Seewolf on 2010-10-08
That should work for you.  This is the reason I ended up going back and doing the Debian install.  It wasn't big differences between the tutorial and what was happening, it was just a cascade of small differences that I kept having to go back and research.

So now you should be working exclusively through a remote machine.  I felt pretty good about myself when I got to that part.  Like you, this was a very new process for me and it seemed like quite an accomplishment to be working on a computer from a different room!

---

### Post by DrImago on 2010-10-08
oh yeah I am really enjoying this! i have now installed webmin on my server and getting ready for the next step!

---

### Post by Seewolf on 2010-10-08
Congrats!  My wife thinks I'm crazy that I think this stuff is fun, but when you start to feel like you are accomplishing something, it is great. Now that I have my server up and running, I am trying to see what I can make it do.

I am shutting down for the time being but will keep checking in when I get a chance.  I now have a vested interest in seeing how things work out for you!

---

### Post by DrImago on 2010-10-08
Cheers man! Really appreciate it!

So far so good. I got Webmin working and I am following the guide. I hit a snag though because i can't find the /etc/modeprobe.d/aliases file. I am researching the problem now.

But this is a lot of fun!

---

### Post by drdos2006 on 2010-10-08
There are some differences between Debian and Ubuntu installation. I found that I did not need to stop IPv6 ( /etc/modprobe.d/aliases) from connecting while following the guide. You may not need to stop IPv6 either.

regards

---

### Post by kevinthecomputerguy on 2010-10-08
You can add the line 
 
blacklist ipv6
 
to /etc/modeprobe.d/blacklist.conf  
 
(or something like that, not infront of a Ubuntu box right now)
 
But I agree with DrDos2006, you probably don't need to stop it.
 
Also, as SeeWolf mentioned, you will have a much smoother time if you try Debian first (there is a link to the .iso on the webpage)
 
You will probably have a heck of a time with Samba 4. I would not take on Samba 4 on your first try, Samba 3 is still the way to go if you ask me.
 
Then, once you feel comfortable and have time to tinker with it, come back and try Ubuntu. I have found most luck in Debian for servers and Ubuntu for desktops and laptops. But both are amazing at both.
 
Good luck 
 
-KevinTheComputerGuy

---

### Post by DrImago on 2010-10-09
ok so after doing battle with this server i got to a point where I have to try and connect through Webmin with the name of the computer rather than the ip. this is a problem which I can't figure out and i have tried a lot to make it work. 

So what happens is the following. I can ping the outside world from my linux box, i can ping the ip of the linux box from a windows laptop on my networ and of course the linux box can ping the laptop but...if i want to ping the linux box from the windows laptop using the name of the linux box it doesnt work.

here's what happens:

when i installed the server, it tok the ip from the router 192.168.1.x1 and during the guide, i changed the ip to 192.168.1.x2. Now let's say the name of the linux box is server and in windows i write this in the command line

ping server

I get

Pinging server.lan [192.168.1.x1] (notice the initial ip from the beginning of the instalation)

and the result is host unreachable.

I suppose there is something I did wrong with the hosts file or interfaces but I can't figure out what I did wrong.

@Kevin: I gave up on the ipv6 thing and left it alone, but is it normal for that aliases file to be missing? As with the Debian, I figure I started this Ubunutu thing now so I will press on with this. If I get stuck or in the end it doesn't work I will do this all over again with Debian, but so far so good I think. well except for this little snag :D

---

### Post by Seewolf on 2010-10-09
I ran into the same problem and Kev gave me a solution that worked for me (thanks again Kev!).  You need to alter a file in Windows that allows your system to recognize the server IP as equal to the server name.

Edit the hosts file located at  c:\windows\system32\drivers\etc\hosts  (file may be hidden \ read only)

Add a line at the end that says:
192.168.2.1 debserv32x1

192.168.2.1 and debserv32x1 are just examples, you will need to replace those with your IP and server name.

When you go to change the file in Win, find your Notepad program, right click on it and select "run as administrator" then select open and navigate to the hosts file.  Running Notepad as administrator allows you to make changes to the configuration file and save them.  You will need to reboot your windows machine after you make the change but you should be able to use the server name instead of the IP address after that.

---

### Post by gordintoronto on 2010-10-09
> **DrImago said:**
> What I would like to do is to had the server as a place where I keep all my movies, music etc and be able to acces it from my home network and also from outside of it. Also, I would like to connect my two printers to this server and share them on the network.


Sorry I'm slow to the party. There's no reason to use the Server edition for what you want to do. You want to share some folders, install a couple of printers and share them. Those tasks are much easier to perform from the Desktop edition. They literally take three or four clicks for each task.

When you say, you want to access from outside your home network, that means over the Internet? Does your ISP allow this, or will they block it? (Most North American ISPs block it...)

---

### Post by DrImago on 2010-10-09
Hey Seeawolf,

I won't have time to continue on the server this weekend but I will restart on Monday evening. However, I had a look in the hosts file in windows and there is no mentioning of the name of my server there with the old IP so adding a line there seems like a patch not an actual solution to the problem (this is my newbie opinion). I say this because it means that every computer that will want to access this server using the name will have to have the hosts file modified this way no?

Is it not possible that there is another file on the linux box that should be changed, say something that contains a line which binds the name

test.lan to 192.168.1.x1 (the old IP)

and returns this into to the ping from windows?

I think this must be since before I started to use putty and webmin the windows box had no nowledge of the linux box.

---

### Post by kevinthecomputerguy on 2010-10-09
DrImago-
 
SeeWolf posted how to fix your name to IP problem. And the alaises file has been moved or removed from new versions of Ubuntu, and .conf has been added to the end of the blacklist filename. (So to answer your question, yes, its ok that its not there) * Doing what i posted to your blacklist.conf file will do what your after.
 
I assume you will hit a stopping point when you get to Samba 4, but pushing forward like your doing is a great way to learn.
 
-Kevin Elwood

---

### Post by kevinthecomputerguy on 2010-10-09
DrImago-

The bigger picture on your ping problem is you dont have an internal DNS server. The guide walks you through this at the end. Just be sure this is something you want to do, its is alot of work for a small network.
 
The hosts file provides a fix for not running a local DNS server
 
There are other tweaks as well, like search suffix's, but these are all local fixes to each windows box, and as you mentioned, that isnt what you want to do. If you want the change to be global, you will have to setup the local DNS server.
 
Good luck
 
-Kevin Elwood

---

### Post by DrImago on 2010-10-09
> **gordintoronto said:**
> When you say, you want to access from outside your home network, that means over the Internet? Does your ISP allow this, or will they block it? (Most North American ISPs block it...)

I don't live in North America, but I don't know if my ISP allows this. I guess I will have to find out. For me is more of a curiosity and a challenge since I have been intrigued but linux for ages but never had the time or the need to use it. And now that I started, I want to make a big project out of it :D the files and printers is just the beginning if all goes well.

---

### Post by DrImago on 2010-10-09
> **kevinthecomputerguy said:**
> DrImago-

The bigger picture on your ping problem is you dont have an internal DNS server. The guide walks you through this at the end. Just be sure this is something you want to do, its is alot of work for a small network.

I see cool, I'll be looking forward to this DNS server too :D awesome. Cheers for all the help. As I said this weekend I won't have time to play with the server but I will start again on Monday.

Have a great weeekend people!

---

### Post by DrImago on 2010-10-12
I'm back. I am puzzled! When I left the server on friday i couldn't ping the name but i could ping the ip. yesterday i revisited the problem and changed something (i didn't do anything to the hosts file in windows) and it worked, but now i've lost the connection to the internet for some reason. one of the other things i have done was to modify the permissions for the users that are allowed to ssh. also i don't know why but when i use putty to login to the server, the server seems to respond very slowly. when i try to ping say, [www.google.com]("http://www.goog.com") it takes almost 1 minute to tell me that the host is unknown.

I think I have done something stupid and i forgot what so I am thinking of reinstalling it from scratch and this time i will make a note of all the changes i make. Is there a way to revert to a default states for all the files i modified?

Also I was thinking of trying the Debian version, but I am not really sure which file to download from the debian website. it seems there are about 30 cd iso's to download...which one do i need?

Cheers,

---

### Post by fabian20685 on 2010-10-12
i have the same problem after a smooth instalation it doesnt start in normal mode but if I start it in the recovery mode it works fine but it takes for ever to load .... i have had fedora installed but it works perfectly but i seem to like more ubuntu so what do you think it is that is wrong i know it goes to a black screen and it says it has taken to long to lad the ubuntu but it says some other stuff ill get it the next time i load it ok thanks for the help

---

### Post by DrImago on 2010-10-12
fixed it! it works now!

i can ping the www i can ping computers on my network, i can ping the name of the server! IT WORKS :D

moving on now :) full speed ahead :D

I decided to use the HDDs i have that connect through USB, take them out of the enclosures and stick them in the server. Will have to read more on how to make sure nothing will happen to the NTFS partions on the hdds.

Suuper cool stuff.

---

### Post by Seewolf on 2010-10-12
I'm glad to hear things are still going well.  Do you mind posting what was causing the problem and what you did to fix it?  It may help the rest of us if we run into a similar problem.

Thanks!

---

### Post by DrImago on 2010-10-12
I will try to document what i did but i might blame a lot of it on the beginner's luck.

So, the main problem was i couldn't ping the name of the server from my windows machine. So I thought the problem could be either in resolv. conf or /etc/network/interfaces

I think the problem was in all of them. In interfaces, I had the gateway wrong. The gateway has to be the IP of the router (the one that the router responds to from your network).

In resolv.conf I added 3 nameservers, namely, the two DNS addresses I got from my ISP (I found them from the configuration page of my router, where it tells you the stats of you internet connection) and the third one was the IP of the router. So it looks like this:

search lan

nameserver IP router
nameserver DNS1
nameserver DNS2

Now I don't know if this is how it should be but it works now.

---

### Post by Seewolf on 2010-10-12
Thank you for posting that!  You never know who you might be able to help with information like this.  I find a lot of useful information buried in posts on this forum.

---

### Post by DrImago on 2010-10-12
I will try and document what I can, but me being a complete newbie I am not really sure what I am doing, so I expect to be exposed to a consistent amount of the famous beginner's luck :)

---

### Post by kevinthecomputerguy on 2010-10-14
DrImago-
 
I might have confused you with another user. Are you following my guide on woodel.com ?
 
The answer to your 30 cd question is answered on page 1 (page 3 if using the pdf)
 
And your DNS question(s) are answered on page 1 (page 51 and 57 if using the pdf)
 
If i confused you with someone else, sorry, its been a long week :- )
 
-KevinTheComputerGuy

---

### Post by DrImago on 2010-10-15
> **kevinthecomputerguy said:**
> DrImago-
 
I might have confused you with another user. Are you following my guide on woodel.com ?
 
The answer to your 30 cd question is answered on page 1 (page 3 if using the pdf)
 
And your DNS question(s) are answered on page 1 (page 51 and 57 if using the pdf)
 
If i confused you with someone else, sorry, its been a long week :- )
 
-KevinTheComputerGuy

No worries Kevin! 
I don't know if you are confusing me :)
I had a long week too and didn't manage to work on the server at all, plus my internet connection is a bit busted at home (the main telephone wire was severed...long story).

I managed to solve the problem, no need to install debian yet. I realised I asked a question that was already answered in your guide (I use the pdf version) after I posted here, sorry. Turns out that I messed up the gateway settings and something else too. Anyway now everything is working and is waiting for me to continue setting it up.

Cheers,

---

### Post by DrImago on 2010-10-19
I am back!

Today I managed to access my server from work using webmin! I am really excited!

I didn't manage to connect using putty because it said the connection timed out, but I will figure it out eventually. Maybe I didn't set the port forwarding on the router properly.

Now I still have a long way to go before I finish configuring this server but I am making progress.

Quick question, if I add extra HDDs to the server, which are formated as NTFS, can I still share them as I please with user rights for access? I saw in the guide that after an hdd was added, the hdd was formated in the native linux file system. Is there any way I can avoid that or this is a must? At the moment I am playing with the server as it is, I haven't installed any extra hdds.

Cheers,

---

### Post by kevinthecomputerguy on 2010-10-19
DrImago-
Great work!
 
Yes, if you want to use Linux file permissions you will need to format the hard drive.
 
This is a destructive process, so make sure you have a backup of those files on a seperate disk to copy back to \ from.
 
-Kevin

---

### Post by DrImago on 2010-10-19
Cheers mate I got it! I will postpone this part until I get to get me one huge hdd. 

Right, now I have another problem. One big one I think!

I have this Lexmark E232 printer which I want to install and and share on my network. It connects through the parallel port because the USB is busted for some reason. I installed CUPS and installed the printer using a few of the default drivers. In every instance I got the printer to print a test page from within the cups admin interface but when i send something from windows, it either gives me a printing error and nothing prints or on two occasions i got the same test page from cups instead the document i wanted,

I searched high and low for a proper driver and found one ppd file [here]("http://forums.linux-foundation.org/read.php?29,171,954,quote=1") but I can't make it print when I send documents from the windows machine.

Is there any kind of generic driver I can use?

---

### Post by DrImago on 2010-10-20
Ok somehow I managed to get it working! The printer works, I managed to install it on my windows machine and i can print. Perfect.

Now the trade-off, I think I busted my smb.conf file and possibly the cupsd.conf (not sure about this one). The reason I think this happened is because, yesterday I could see the server as along my network neighbourhod devices in windows and now I can't.

Also, in kevin's guide there is a step there you get to remove the shared printers to be shown in windows. the thing is this is not even enabled i think, and I would like to enable it so I can see better the printers from windows.

Do you guys have any thoughts as to why I can't see the server in network neighbourhood?

---

### Post by kevinthecomputerguy on 2010-10-23
DrImago-
 
The real fix for this is to setup a local dns server, but it can be overkill for a network your size. But is covered on page 5.
 
A quicker fix is to add your server name and ip to c:\windows\system32\drivers\etc\hosts so it resolves this locally.
 
Also make sure your windows boxes are in the same workgroup as your server. Your server if you followed the guide exactly would be in workgroup "diy.lan" or if you left that part un-configured it would be in workgroup "workgroup" just change your windows boxes to be in the same workgroup. (you can change this in the same place you change the computer name)
 
Also, without a local dns server you may need to add a dns search suffix to your windows boxes. In the same place you would change your ip address, if you click advanced, and click on the dns tab, you will see a place you can add search suffixes. Add "diy.lan" or whatever you used to both suffix options and reboot. (the option in the middle and the bottom, not the top) Now your windows boxes will append .diy.lan to any computer names it looks for and any broadcasted searches network neighborhood does.
 
You can also set your samba server to broadcast / annouce its name to your network, but this is noisey and not recommended, but if its that important and other methods dont work, the guide will show you how.
 
I can't be much help with the printing. I stopped doing print servers about 5 years ago, and only use printers with built-in HP jetdirect print servers built-in.
 
good luck
-Kev

---

### Post by DrImago on 2010-10-26
Hi Kevin,


I fixed the problem with my server not showing on my network. It seems that the solution was in modifying the resolv.conf file. More precisely the search and domain lines. Instead of lan which you have in your guide, I changed it to WORKGROUP which is what all my windows computers are set to. So now I can see my server on the network, however, I can't see the shared printer, like you see it in a windows computer through the network. I will keep looking and see if I can get this working too. So it seems I don't need the DNS server!
The printing problem is solved. I have a functioning print server now and I have shared a laser printer on my network.

Lucian

---

### Post by arnavk007 on 2010-10-26
[http://ubuntuforums.org/showthread.php?t=1585441&page=4](http://ubuntuforums.org/showthread.php?t=1585441&page=4)
drimago checkout my thread and help me
btw What did you use to access ur machine from the net

---

### Post by DrImago on 2010-10-26
> **arnavk007 said:**
> [http://ubuntuforums.org/showthread.php?t=1585441&page=4](http://ubuntuforums.org/showthread.php?t=1585441&page=4)
drimago checkout my thread and help me
btw What did you use to access ur machine from the net


I am really just a beginner with Linux and I don't really understand  what you are trying to do with your network. I am really not the person  to ask. I can only tell you how I solved the problems I encountered.

I am using Webmin to access my server from outside my network. I think I didn't set the port forwarding properly on my router or I don't know what, but I can't use putty. It times out and I can't connect through Putty. Webmin works fine apart from its ssh module.

You should check out Kevin's guide, is really really helpful. I still haven't finished going through all of it but I am getting there.

Good luck!

---

### Post by arnavk007 on 2010-10-26
Can u access files using webmin

---

### Post by DrImago on 2010-10-26
Yes you can access the files using webmin. you should really read and use this guide if you are a beginner.

[http://woodel.com/](http://woodel.com/)

It explains everything you need to do very well.

---

### Post by DrImago on 2010-11-12
Hi guys!

I am back...i have done many things in the past few weeks with my server.
First I have reinstalled my system this time with the latest version 10.10. I have learned my lesson and everytime I am editing a file, I create a backup of the original first and also in the  file I modify I write what I modified and what was the default setting. So from this respect all is well.

Now I can see the server on the windows network, I can ping the name of the server (instead of the  IP), I can see the shared printer when I access the  server from windows. I have also installed a wordpress blog using the Apache2 webserver. Here is where I am getting some problems but I will get them solved.

I would need some help thou with what I am planning to do next:
I would like to install (i know how to do that) and format a few hard drives that I want to use for storage. I would like to be able to share the entire space on my network so that I can mount it as a network drive. I do not need to have separate users each with his own storage because is only me and my sister on this network and all I want is to have a place where I can find all my movies and software.
Now the complicated part. I would like to be able to give access to people if I want to, to selected bits (e.g. if I want to share a bunch of files with someone, I'd like to give that someone a link or something like that where he can access the files and or modify them). And one last thing would be to be able to access my files from outside my network, something like a network drive but over the internet if that's possible (at the moment I can see everything using webmin but I would like to see the files I share in windows even when I am outside the network if that's possible).

Cheers,

Lucian

---

### Post by DrImago on 2010-11-13
Ok I may rushed my party here...I can't see the printer again. I don't know why...It was showing in windows when I was browsing the network but now I can't see it again. I can print on it but I can't see it.
Anybody has any idea on how to solve this?

---

