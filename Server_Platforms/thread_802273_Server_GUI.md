---
title: "Server GUI"
date: 2008-05-21
forum: Server Platforms
---

### Post by Necromantis on 2008-05-21
This is probably the wrong section for new request but I can't find where to post it.. sorry - (please forward to correct section)

In the idea of "Ubuntu" I was thinking it would be nice to have an option to install a small (light) GUI for Ubuntu server edition which would have an easy access to the main configuration files (a SAMBA GUI would be nice for example) and some tools to visually check what is happening without having to search the logs / enter complicated command lines. 

Obviously this will be without damaging the server security. 

Just an idea.. Thanks

---

### Post by NateMan on 2008-05-21
I would have to recommend webmin as a light weight gui for a server. It will give you a web based samba gui, as well as a gui for most modules/servers installed. It is available here: [http://www.webmin.com/](http://www.webmin.com/)
Download the .deb and its very easy to install. If you need any packages, just install them and you should be good to go. Works great on all of my servers!

---

### Post by k3lt01 on 2008-05-22
Isn't Webmin for use on a 2nd computer to check the server?

If you want a lightweight GUI on your server try something like XFCE or Fluxbox

---

### Post by vpsville on 2008-05-22
> **k3lt01 said:**
> Isn't Webmin for use on a 2nd computer to check the server?


No, webmin is a free control panel that you install on the server.  It lets you control the server via an easy to use web interface.
Its great for basic admin tasks.

---

### Post by NateMan on 2008-05-22
Honestly between webmin and ssh, its easy to make servers that even amateur users can control. It is a GUI, not just a program for checking on a server. A GUI is anything that allows the User to Graphically Interface with the computer/program. Its not a full mouse driven desktop, but I promise that it is much much lighter than both fluxbox and xfce. In addition to that, with simple port forwarding, your GUI can be securely web accessed over https from anywhere. You can download files from it, move files to it, change all different services, run a cli, restart/shutdown the server, and just about anything else you can think of. My server only using about 200 megs of ram, and it is doing quite a bit of stuff. When its idling (for a server), it uses only a little above 100.  In addition to that there is no worrying about graphics card drivers or anything since it is just a webpage.

---

### Post by k3lt01 on 2008-05-22
Thanks NateMan and vpsville, I didn't know that. I will give webmin a go on my server when I have finished setting it up.

---

### Post by windependence on 2008-05-23
Three points:

1-) I have seen remote exploits for webmin that grant shell access due
to flaws in the scripts that webmin uses.

2-) Webmin requires an httpd to run. If you are using webmin to manage
your mail server, then you need to run httpd on your web server, which
you would not need to do otherwise. In doing that you open up another
service for an attacker to pounce on.

3-) Why would a systems administrator rely on a web based administration
tool? Shouldn't that administrator understand the inner workings of his
or her system. Shouldn't that administrator also be security aware?

Don't get me wrong, webmin does have a place but I do not see it in a
network that requires any serious level of security. It would be handy
for a test network, or maybe an isolated network behind a few
firewalls. I would not suggest using it on any system directly exposed
to the internet though.

If you are going to use webmin, at least set it up to use SSL:

[http://www.webmin.com/ssl.html](http://www.webmin.com/ssl.html)

Here is what Canonical says about running a GUI on Ubuntu server:

> No X server by design

By design, Ubuntu Server Edition does not include an X server. This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator.

    "So I applaud the Ubuntu team’s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server."
    --Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server"


[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)


-Tim

---

### Post by NateMan on 2008-05-23
Maybe you should look into remote exploits on webmin... they were mostly from the early 2000s. They seem to have been weeded out by the mid 2000s. The ones I've found after that date are all of minor rating, not major root access hacks. Of course anything you add add vulnerabilities, theoretically.  Also I doubt that k3lt01 is running a serious enterprise server, he's probably just setting up a home server. If he was doing that on the level that you might be thinking of, then I imagine he wouldn't be asking the questions he was. Webmin gives him access to a level of configuration that he would not otherwise have. I do know how to do almost everything I do without webmin, but I like to use it for ease of use, since I doubt hackers will be attacking my movie storage server any time soon. I mean there are numerous other threats that don't involve webmin. Your quote also doesn't refer to webmin as webmin does not create direct access between user space and hardware, its just a remote management program using config files already in use. xwindows requires hardware/userplane access on another level. Now if you have a server guide that you would recommend that fits your standards, I'd love to read it. I found this online, it seems to be an exact copy of what you wrote...
[http://seclists.org/basics/2002/Oct/0338.html](http://seclists.org/basics/2002/Oct/0338.html) . Was that you as well back in 2002 saying the exact same thing? Webmin doesn't even run on http anymore, mine runs on https. Please check the dates on posts before you repeat information.

---

### Post by hyper_ch on 2008-05-23
and if you're installing a httpd server anway, you can also install SWAT - that's a webui for samba.

---

### Post by k3lt01 on 2008-05-23
> **NateMan said:**
> Also I doubt that k3lt01 is running a serious enterprise server, he's probably just setting up a home server.Ok here's what I will be doing, hopefully.

My Server will be 
1. Home server with a 2nd hdd (approximately 250GB atm) for file storage.
2. Webserver for a website I have nearly completed in Moodle for 1 subject I teach in High Schools. I live in a rural area that does not have the facilities a city like Sydney does. So I have designed a Moodle site with plenty of relevant info. Also there will be a few more sites as well so the server will get some moderate internet traffic.
3. Something for me to learn with. I'm not going to do anything drastic that will knock it out of service but I will use it to learn on.

So what specific capabilities do I want?
1. I must be able to log into it from anywhere so I can work on the website.
2. I would like to have multimedia streaming if I can so I can have my music and some of my video collection on it and play it on my desktop or laptop at home.

Any helpful suggestion would be greatly appreciated.

---

### Post by NateMan on 2008-05-23
You should be fine. Running a webserver and allowing for remote access will be easy. For file streaming there is a nice program called gnump3d. its in the repositories. You can install it with apt-get install gnump3d. It isn't the most secure program, so go into the config file and make sure its not running as root or such. It makes a directory called /var/music, and from there you can make symbolic links using ln -s /music/folder /gnump3d/'s/folder . Hope that helps.

---

### Post by k3lt01 on 2008-05-24
Thanks NateMan, much appreciated.

---

### Post by windependence on 2008-05-24
> **NateMan said:**
> Maybe you should look into remote exploits on webmin... they were mostly from the early 2000s. They seem to have been weeded out by the mid 2000s. The ones I've found after that date are all of minor rating, not major root access hacks. Of course anything you add add vulnerabilities, theoretically.  Also I doubt that k3lt01 is running a serious enterprise server, he's probably just setting up a home server. If he was doing that on the level that you might be thinking of, then I imagine he wouldn't be asking the questions he was. Webmin gives him access to a level of configuration that he would not otherwise have. I do know how to do almost everything I do without webmin, but I like to use it for ease of use, since I doubt hackers will be attacking my movie storage server any time soon. I mean there are numerous other threats that don't involve webmin. Your quote also doesn't refer to webmin as webmin does not create direct access between user space and hardware, its just a remote management program using config files already in use. xwindows requires hardware/userplane access on another level. Now if you have a server guide that you would recommend that fits your standards, I'd love to read it. I found this online, it seems to be an exact copy of what you wrote...
[http://seclists.org/basics/2002/Oct/0338.html](http://seclists.org/basics/2002/Oct/0338.html) . Was that you as well back in 2002 saying the exact same thing? Webmin doesn't even run on http anymore, mine runs on https. Please check the dates on posts before you repeat information.

Remote exploits happen all the time for almost all software. Not to be snooty here but it seems nobody in this section of the forums is actually setting up a serious production server. I secure my home servers the same way I secure my production web servers. It's just makes good sense. I expected people in the SERVER forum to be running the SERVER edition, and not wanting to muck it up with an insecure GUI. Doesn't anyone learn the command line anymore? Has windows really penetrated that far into the Linux community?

Sorry for the rant but I expected more serious users on the server forum.

-Tim

---

### Post by ArrantSquid on 2008-05-24
Not to be rude, but using a GUI doesn't make you any less serious about security. I have been using the command line to run my sites for years now and have gotten tired of managing all of them by hand so I wanted a GUI. I actually installed my first GUI a few days ago and while it hasn't saved me time yet, I'm sure it will in the end. I'm not saying that you're point isn't valid because it is. The more software you run, the more likely you are to leave security holes open. It's a flaw. But to make a sweeping generalized statement that users who use GUI's are more lax on security is just asinine. And yes most everyone here is running a home server or the such. If you're running one website then doing it from the command line is the way to go. Multiple sites... eh, you may want to look into it, but a GUI is nicer. I still am not sold on the GUI solution I picked, because I am used to the terminal, but we shall see. Just don't knock it.

---

### Post by windependence on 2008-05-24
Unfortunately, this is a subject that could be debated forever and certainly has been. I have been disappointed lately when googling for tutorials I seem to get tons of GUI stuff and not what I really want, and this is on LINUX. Don't get me wrong, I am writing this from a Mac. I like a nice GUI on a workstation, but on my servers a heavy GUI has no place. A web interface, YES if it has been thoroughly secured. If you haven't seen people from China and Romania hammering on your firewall all day long you haven't been reading your logs. I am just saying some people are just ramndomly loading GUIs without thinking about the security ramifications. Look at the first page of posts on this board and you can spot many of them. There is a reason Canonical didn't put a GUI front end on the server product and I posted what they say. In case you didn't catch it, it's on the SECURITY part of the page I posted. 

That all being said, learning to use the command line, especially on a sever product will make you a better admin. What if your GUI fails? Can you recover from that? Even on a home server, would you want to lose all your music, ,movies and docs? It's something to think about.

-Tim

---

### Post by k3lt01 on 2008-05-24
This may or may not get anyone thinking here but as learner of Servers as well as Ubuntu I think it needs to be pointed out that learning a command line is not easy and takes time. Because of this I, and a few people I know who are also learning about servers, like the idea of a GUI interface while we are learning the ins and outs of the CLI. Having said that most people do know a GUI brings in security issues but most people running a full blown server would have a lot more experience at it than people like me do. So it makes a bit of sense to have a somewhat familiar setup (GUI) on a machine while you are learning as quickly as is humanly possible about the unfamiliar setup (CLI).

---

### Post by windependence on 2008-05-24
> **k3lt01 said:**
> This may or may not get anyone thinking here but as learner of Servers as well as Ubuntu I think it needs to be pointed out that learning a command line is not easy and takes time. Because of this I, and a few people I know who are also learning about servers, like the idea of a GUI interface while we are learning the ins and outs of the CLI. Having said that most people do know a GUI brings in security issues but most people running a full blown server would have a lot more experience at it than people like me do. So it makes a bit of sense to have a somewhat familiar setup (GUI) on a machine while you are learning as quickly as is humanly possible about the unfamiliar setup (CLI).

Agreed. As long as you don't rely so much on the GUI that you don't know what is going on behind the scenes. I mad that mistake when I was learning and I regret it. Finally, I just loaded a server with no GUI and MADE myself do it with the CLI. Best thing I ever did.

-Tim

---

### Post by k3lt01 on 2008-05-24
> **windependence said:**
> Agreed. As long as you don't rely so much on the GUI that you don't know what is going on behind the scenes. I mad that mistake when I was learning and I regret it. Finally, I just loaded a server with no GUI and MADE myself do it with the CLI. Best thing I ever did.

-TimThat is where the learner has to learn as quickly as possible.

---

### Post by ArrantSquid on 2008-05-24
I agree with you 100%. You have no argument from me at all on any point you made. And while I can appreciate that beginners would like a GUI, I have to say that I again agree with you that they really should learn the command line first. Once you've got that down solid installing a web interface is easy as pie and you'll know how to secure and fix it if need be.

---

### Post by windependence on 2008-05-25
Understood. One of the reasons why I seem so hell bent about no GUI on the server for n00bs is that it happened to ME. I lost so much valuable time trying to just use the GUI and then when I really needed the CLI I was hosed. It bit me bad, so I gritted my teeth and told myself I was going to load OpenBSD with no GUI and serve web pages from it. I did it, and never mooked back. The site has been running for 5 years now without a GUI, and I don't think I will ever load one. Will I do a web interface like nagios? Sure, I won't be able to admin them all effectively after I get about 10 or so servers running without having some sort of centralized monitoring, but I don't think I'll ever run X on one of those web servers.

Good to see we mostly agree. That's what it's all about here anyway, helping people not make the same mistakes you made yourself, ya know?

-Tim

---

### Post by DonThompson on 2008-05-26
The comment "*...they really should learn the command line first. Once you've got that down solid installing a web interface is easy as pie...*" suggests those of us preferring GUI interfaces are somehow lesser admins.  Sorry if I disagree, but you're probably Linux-only users, or at least users of only Linux when doing command lines.  Or can you tell me the layout of // SYSIN DD..., or where VMS stores the executables for Rdb?  Do you realize that ALL of MS Windows can be run from a command line, and that most of the vulnerabilities of any OS are in the programs, NOT the GUIs? 

Learning command lines may be fun, and it certainly DOES eventually give one insight into the minds of the OS designers, but the amount of "weight" they add (not very much) to the machine's work, is more than made up for by the admin time saved by easy access to complex functionality.  A GUI is, after all, little more than a live manual with links.

---

### Post by ArrantSquid on 2008-05-27
It's good to see that you read the whole thread. If you had you would have seen that I actually made the argument that it did not make admins any less of an admin just because they want to use a gui. You can check post #14. 
> 
Not to be rude, but using a GUI doesn't make you any less serious about security. I have been using the command line to run my sites for years now and have gotten tired of managing all of them by hand so I wanted a GUI.

Most of us are not Linux only users either. I use a mixed OS environment including pc's and mac's so I understand the trouble of having to manage more than one environment. Furthermore no I can't tell you any of the questions you asked, but they're not in my job description either and I didn't come to a forum looking for help with them. 

Learning the command line isn't just "fun". It's essential. As windependence said:
> 
I lost so much valuable time trying to just use the GUI and then when I really needed the CLI I was hosed.

You can't run everything in a gui. And stop trying to pick fights when you haven't read everything, because then someone who said what you said has to defend what they said and that's retarded.

---

### Post by NateMan on 2008-05-27
I would have to admit that for linux, not knowing the cli will make you much much less effective as an admin. The gui is much sloooower to setup and configure everything. Doesn't knowing the cli in windows make you that much more of an admin? Don't jump in, install a gui, and assume your a network administrator. Nobody would hire a gui only unix admin, and I think almost every employer would expect some good knowledge about it. Now on the same tone, there is much that can be done without full knowledge of the cli. But I have yet to see a server that can be setup without it.

---

### Post by molotov00 on 2008-05-27
For beginners it is important to learn the CLI because that is a window into the inner workings of the server. You'll learn Linux faster. If a GUI helps you get to that point then I don't see a problem with using a GUI. 

I find the CLI more efficient than a GUI for my hobby server. While I learned the CLI that wasn't the case. Nobody else has (surprisingly) raised this point. sudo apt-get dist-upgrade anyone? tail? grep?

Finally, it is good to have a 'secure' mentality when even messing around with servers, much like as a coder it is always good to learn to write good clean code, even when just starting out and your code isn't (yet) thousands of lines.

Regardless of whether you use X or Webmin or whatever, just know what effect your decision has on security.

M

---

### Post by NateMan on 2008-05-27
Great post molotov. Thats one of the best ways I've seen it put. The cli tools are beyond invaluable for servers.

---

### Post by windependence on 2008-05-27
> **NateMan said:**
> Great post molotov. Thats one of the best ways I've seen it put. The cli tools are beyond invaluable for servers.

Not even invaluable, but absolutely essential in the Unix/Linux world. This guy wants to start a Windows war, but this is certainly not the place to start it.

-Tim

Locked and loaded.

---

### Post by windependence on 2008-05-27
> **DonThompson said:**
> The comment "*...they really should learn the command line first. Once you've got that down solid installing a web interface is easy as pie...*" suggests those of us preferring GUI interfaces are somehow lesser admins.  Sorry if I disagree, but you're probably Linux-only users, or at least users of only Linux when doing command lines.
On the contrary, I use Windows (all versions) Linux (several distros) MacOS (my laptop) AS/400 (work) AIX, Solaris, FreeBSD, OpenBSD, HP UX, and I probably forgot one or two.

> Or can you tell me the layout of // SYSIN DD..., or where VMS stores the executables for Rdb?
Well no i can't tell you but if I worked with them every day as an admin I could. I do have a colleague who could go the command line and find it in 30 seconds or less for you though. I am just not that good....yet.

> Do you realize that ALL of MS Windows can be run from a command line, and that most of the vulnerabilities of any OS are in the programs, NOT the GUIs?

OK PROVE it.

> Learning command lines may be fun, and it certainly DOES eventually give one insight into the minds of the OS designers, but the amount of "weight" they add (not very much) to the machine's work, is more than made up for by the admin time saved by easy access to complex functionality.  A GUI is, after all, little more than a live manual with links.

Not very much weight on the machine? How big is the GUI in Windoze? Do you realize that I can run an entire web server, email server, and my forum message board with over 75,000 posts on just 6 gigs of space? And that includes avatars, photo gallery, and downloadable files we store. Can you do THAT on a windows machine? How about running a diskless firewall machine from a floppy? Remember, this is a full install of the OS, and of course, no GUI.

On a serious note, you should open your mind and actually USE and get to know some other OSs besides Windoze, and you might be surprised, you might actually have some FUN!

-Tim

---

### Post by 565Customz on 2008-05-27
> **windependence said:**
> 

Not very much weight on the machine? How big is the GUI in Windoze? Do you realize that I can run an entire web server, email server, and my forum message board with over 75,000 posts on just 6 gigs of space? 
-Tim



then i should b ok with my 100gig lol..now if i could just get it to run..lol

---

### Post by hyper_ch on 2008-05-28
> **windependence said:**
> Not very much weight on the machine? How big is the GUI in Windoze? Do you realize that I can run an entire web server, email server, and my forum message board with over 75,000 posts on just 6 gigs of space? And that includes avatars, photo gallery, and downloadable files we store.

You can run it on less than 1 gb diskspace...

DSL just uses 70 mb to load a complete linux WITH a gui. Adding apache, mysql, php will add max. 100 MB... instead of apache you might be able to use lighttp (I think that's smaller)....

Then 75'000 posts don't take that much dispspace... avatars and photogallery and downloadable files will take most of the space... but 1 GB is quite a bit to fill first.

---

### Post by frankos44 on 2008-05-28
One of my servers runs Ubuntu on a Mini-ITX using a high speed 8Gbyte data-pen with 1G DDR2 RAM. The total power is less than 15 watts and it runs as cool as a cucumber and makes zero noise.

The point I am trying to make is without a GUI the server will run on any reasonable PC, This one makes no fuss, its reliable, uses less power and its totally silent!!.

For the sake of learning how to administer a server using the CLI including configuring virtual hosts, installing ssl certificates and mastering secure connections, why use GUI?

Its far more rewarding not using the GUI and I made a contribution to the planets resources in the process in this case. Oh and its given me immense pleasure too.

Yes, I need to get out more!

---

### Post by windependence on 2008-05-28
> **hyper_ch said:**
> You can run it on less than 1 gb diskspace...

DSL just uses 70 mb to load a complete linux WITH a gui. Adding apache, mysql, php will add max. 100 MB... instead of apache you might be able to use lighttp (I think that's smaller)....

Then 75'000 posts don't take that much dispspace... avatars and photogallery and downloadable files will take most of the space... but 1 GB is quite a bit to fill first.

Agreed. I have some extraneous files in there I don't need including a few hot backups and some ISOs. You know the point I was trying to make though. GUIs unless they are web GUIs are just big and heavy. Nice , but not necessary for a server.

-Tim

---

### Post by rickyjones on 2008-05-28
> **windependence said:**
> Agreed. I have some extraneous files in there I don't need including a few hot backups and some ISOs. You know the point I was trying to make though. GUIs unless they are web GUIs are just big and heavy. Nice , but not necessary for a server.

-Tim

I'll agree that they are not exactly necessary but they can make my life a lot easier in the long run.

Sure, I can SSH into my server using Putty and be able to accomplish most any task. But sometimes it is easier to have a GUI for some things.

For example: Webmin. When I install Webmin I like to lock it down so that only the localhost can access it (I might add in a rule for my administrative workstation too). So I install a GUI + FireFox on my server. The GUI only runs when I tell it to run, so there is little to no security risk from remote exploits, especially since X is configured to only listen to the localhost. This way I can use Firefox on the server to administer it.

Another great use is the simple text editor. Sometimes using VIM is just time consuming when making my way through a 2000 line file. Using a text editor like gEdit makes this so much more simpler. And when I'm done? Kill X and eliminate the "security" risk that you keep talking about.

I think this is a pretty safe situation. 

Sincerely,
Richard

---

### Post by windependence on 2008-05-28
If that's all you need, I will tell you how to do what you are doing WITHOUT installing a GUI on the server as soon as I get home from work. 

I hate VI too, and I know how to use it. Just use nano or pico. very easy and fast.

More details later.

-Tim

---

### Post by Necromantis on 2008-05-31
I didn't realized I was going to generate so many posts / opinions.

Ok after reading all of this I would like to put few points forward. 

My initial post was for the Ubuntu team to **create** a new GUI with limited / easy access to log files and configuration files/GUI configuration; the amount of time I waisted configuring SAMBA and I still can't tell if it's really secure or not.. yes it's asking for a username and passord when I try to access the folder on the network but did I do it right? also if you are even thinking about using samba in some sort of active directory.. I will shot myself in the head if I had to do this using a text editor to managed 10000+ accounts. 

The idea was Not to sod around with installing GUI games / mmplayer or other stuff. I was more asking for some sort or Eee PC GUI. Something NEW which would have to be think with security in mind. 

I do accept that knowing command lines in linux/unix is the way to do things today.. BUT if the same people who compiled Ubuntu server - which I believe is more secure than if I was to attempt doing it myself; - not that I would have a clue on where to start -  were to put together a new set of programs to configure LAMP / SAMBA etc. then chance are; it will be WAY more secure than when I do it. 

Side note:
I am not planning on becoming a Linux Admin. I have a server (ubuntu server 7.01) at home P200 168MB 6GB (yes Pentium 200Mhz.. not even MMX) and I host 4 websites - and it works great! 2 forums with phpbb3. Unfortunately I now have to upgrade it because the motherboard just won't take any USB2.0 controller.. 

I am not going to install a Web access to my server.. that won't even come to mind :confused: if I was to write the php code myself I might consider it but even then.. probably not or with some serious limitation to the code.

PS: where are the log files? :lolflag:

---

### Post by windependence on 2008-05-31
Just a quick point here. Unix and Linux admins have been administering networks with thousands of users for quite some time now without a GUI. There are tools for this. There may even be an ncurses GUI out there that runs in the terminal, I just know it has been done for years by *nix admins without need for the GUI.


-Tim

---

### Post by sevenseeker on 2008-05-31
I have always administered by boxes through the command line and webmin (since these are dev and test systems).  That said, I appreciate the ease of use of a well designed interface, whether GUI or not.  I do not have the time to learn every detail of every app I want to install before making it useful.  I need something quick and painless in the beginning.

However, in the future I do want to pick up on the details (with the exception of most MTAs as those hurt bad).:lolflag:

I appreciate any system that helps me config the system and helps me cheat by checking out the commands it uses.  AIX administration has this ability and I love it.  I can learn a lot by using this method.

Are there similar solutions for Ubuntu?

Also, this is VERY useful for brining someone on board who doesn't have the extensive knowledge required for command line administration.  Note these would never be mission critical systems but dev and learning systems.

Thanks,
Jason

---

