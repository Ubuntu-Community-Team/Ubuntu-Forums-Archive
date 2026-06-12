---
title: "How do I get a GUI in ubuntu server?"
date: 2008-04-28
forum: Server Platforms
---

### Post by messybricks on 2008-04-28
Okay... so I'll admit, I'm a complete n00b when it comes to servers, especially with linux.  I installed 8.04 Server edition, and I was expecting to get a GUI, but it just logs in to a terminal.  What do I do to get a GUI?

---

### Post by bigken on 2008-04-28
sudo apt-get install ubuntu-desktop

---

### Post by ibutho on 2008-04-28
Generally Linux and Unix servers are administered in the CLI so there are no nifty GUIs. You could install GNOME (ubuntu-desktop), KDE (kubuntu-desktop), or XFCE (xubuntu-desktop) using apt-get or aptitude. Unfortunately these methods will install desktop apps that shouldn't really be on a server, so maybe something like Fluxbox would be ideal. Webmin which allows one to administer their server from a remote computer via a web browser is a good tool that you should also look at.

---

### Post by HermanAB on 2008-04-28
Well, you could install Xubuntu, or you could add a GUI as detailed above.

In general, if your server has a keyboard and screen attached, then you don't really want to use the 'server' version and should just install a regular desktop version.

---

### Post by messybricks on 2008-04-28
well, I have it set up with a KVM switch right now, but I'd like to get it set up and then have it sit in a corner and run all by itself.  I might just decide to do this without a GUI after all (I'll just have to mess with it). Thanks for the help.

---

### Post by Derspankster on 2008-04-28
> **messybricks said:**
> well, I have it set up with a KVM switch right now, but I'd like to get it set up and then have it sit in a corner and run all by itself.  I might just decide to do this without a GUI after all (I'll just have to mess with it). Thanks for the help.

I ended up installing ubuntu-desktop on my server. I then deleted everything I could or did not need. My server runs headless and I can access it either by ssh or by using vncviewer. I can also administer using a browser.

---

### Post by Brazen on 2008-04-28
AAAAAAAAAAAAAAH!! GUI on a server!! AAAAAAAAAAAAAAAAAAAAAAAAAH!!


> **HermanAB said:**
> Well, you could install Xubuntu, or you could add a GUI as detailed above.

In general, if your server has a keyboard and screen attached, then you don't really want to use the 'server' version and should just install a regular desktop version.

There are also difference in the kernel with the server install, so even if you install the server version and install xubuntu-desktop on it, then you still have a kernel optimized for server applications.  Otherwise, you could install from the Xubuntu cd and then switch to the linux-image-server kernel.

---

### Post by hyper_ch on 2008-04-29
Do you want to operate a server or a desktop computer with some server functions? If it's the former, you won't need a gui as configuration is done through config files and it doesn't matter if you edit the config file in nano, vi, ... or in a fancy gui editor.... if the later is the case, then just install the desktop version and add server capabilities later...

---

### Post by Brazen on 2008-04-29
> **hyper_ch said:**
> 
and it doesn't matter if you edit the config file in nano, vi, ... or in a fancy gui editor.... 

Er, I'm pretty sure you didn't really mean to say what you just said.  It is a very BAD idea to edit your config files in programs such as Abiword or OpenOffice Writer because, while it *looks* like the same text on the screen, those fancy editors add in a lot of extra data to the file.

So just to clarify, I'm sure what hyper_ch meant is that you can edit files in plain text editors like Mousepad (in Xubuntu) or Gedit (in Ubuntu).

---

### Post by absolute512 on 2008-04-29
I would use 
su
aptitude install xorg gdm xfce4
aptitude install <name of GUI browser, I use firefox>
aptitude install gedit
aptitude install gnome-terminal
and if you need it, 
aptitude install synaptic 
aptitude install xchat
shutdown -r now


Do use the different lines or it will install a lot of packages that aren't necessary. That way you have a lightweight GUI, perfect for a server, that you can setup any way you like. Remember to use sudo before the aptitude install command if you haven't enabled login as root.

abs512

---

### Post by messybricks on 2008-04-29
Thank you all for your replies...

Mostly what I want to do is have an efficiently-running server that I don't have to mess with after I get it set up.  It will be the fourth computer in my dorm room, so I won't really need it to do much besides server operations.  That said, I'm not very experienced with servers, so I would prefer using a GUI to a terminal to set up/modify things on the server.  Can't I just boot into ubuntu desktop, set everything up, and then boot into a terminal indefinitely, so I'm not using all that RAM for the GUI?

---

### Post by hyper_ch on 2008-04-29
> **Brazen said:**
> Er, I'm pretty sure you didn't really mean to say what you just said.
Sure I meant to say... I said editor and not word processing ;)

And there's a lot fancier ones like emacs, quanta plus, kate, eclipse, ...

---

### Post by rogblake on 2008-04-29
Another reason one might want to install the server version would be for longer support -- 8.04 Server Sdition will be supported for 5 years, as opposed to 3 years for the desktop version.

I also prefer working from the CLI and editing config files with a plain text editor, but sometimes servers need to be maintained by the new generation of "point-and-click" sysadmins, so installing the GUI on the server can be helpful in such cases.

Once installing the X server and window manager, how can you get it to log in and fire up on the console automatically? (This is an easily configured GUI option in Ubuntu Desktop Edition, have not played around with it with Server Edition.)

---

### Post by HermanAB on 2008-04-29
Change the run level with init.

To go to text mode:
init 3

and to go to graphical mode:
init 5

---

### Post by Brazen on 2008-04-29
> **hyper_ch said:**
> Sure I meant to say... I said editor and not word processing ;)

And there's a lot fancier ones like emacs, quanta plus, kate, eclipse, ...

Yeah, but a lot of people don't know that there's a difference.:-\"

---

### Post by ginjabunny on 2008-04-29
At home I have 8.04 server with a gui, I use it as a server and firewall and also a remote desktop so I can vnc onto it and leave programs running when I've gone to bed or work (I set it up to auto login to a non-admin user).

Here is what I do, install server then - sudo apt-get install xorg gdm gnome-core synaptic - this will give you basic gnome which is pretty fast, it complains about stuff missing which you can install if you want using synaptic which allow you to search for what you want like ubuntu themes, firefox, vino, etc

The purists will whinge but it works for me :)

---

### Post by Dr Small on 2008-04-29
> **ginjabunny said:**
> At home I have 8.04 server with a gui, I use it as a server and firewall and also a remote desktop so I can vnc onto it and leave programs running when I've gone to bed or work (I set it up to auto login to a non-admin user).

Here is what I do, install server then - sudo apt-get install xorg gdm gnome-core synaptic - this will give you basic gnome which is pretty fast, it complains about stuff missing which you can install if you want using synaptic which allow you to search for what you want like ubuntu themes, firefox, vino, etc

The purists will whinge but it works for me :)
Using VNC to leave programs running?
Dear Sir, have you ever heard of "screen" ? It works marvelous for this cause.

---

### Post by Brazen on 2008-04-29
> **Dr Small said:**
> Using VNC to leave programs running?
Dear Sir, have you ever heard of "screen" ? It works marvelous for this cause.

If it's a commandline program, then yeah, screen is definitely the way to go.

---

### Post by hyper_ch on 2008-04-30
> **Brazen said:**
> Yeah, but a lot of people don't know that there's a difference.:-\"

For someone who wants to run a server I can expect at least a bit of research ;)

---

### Post by natrixgli on 2008-04-30
Hi,

On a server I think you will find Webmin will be much more useful than having XFCE/Gnome/KDE on it.

[http://www.webmin.com](http://www.webmin.com)

**to install:**

**Get Dependencies:**
```

sudo apt-get install libnet-ssleay-perl libmd5-perl libauthen-pam-perl libio-pty-perl

```

**Get Webmin from Sourceforge:**
```

wget http://prdownloads.sourceforge.net/webadmin/webmin_1.430_all.deb

```

*[COLOR="Red"]Edit: Use the above as an example, you should make sure you are getting the latest Webmin release from [http://www.webmin.com](http://www.webmin.com). Alternatively, after you log into Webmin you can update from the "Webmin Configuration" menu.[/COLOR]*

**Install Webmin:**
```
 
sudo dpkg -i webmin_[VERSION]_all.deb

```

(replace [VERSION] with the complete version number of Webmin. (ex: 1.430)



Now you can log in to your computer by going to:

[https://ipaddressofserver:10000](https://ipaddressofserver:10000)

Cheerio,

-n8

---

### Post by wdaniels on 2008-04-30
I used to use webmin on servers when I was less familiar with linux, and I always recommend it.  A GUI can often help to get an idea of the logical structure of things more quickly, but ultimately it's worth the time investment to learn how to work through the terminal and edit files yourself.

---

### Post by natrixgli on 2008-04-30
> **wdaniels said:**
> but ultimately it's worth the time investment to learn how to work through the terminal and edit files yourself.


Absolutely true. Some things are much easier and faster to do with vim or nano. And some Webmin modules lack as many options as you get with a manual configuration. (like Bacula, for example.....)

When I first started creating & managing Linux servers, I tried to do it all with Webmin, but ultimately once I got going I found it much easier to just do things on the command line.

Though I will never give up Virtualmin for web servers! 


-n8

---

### Post by ginjabunny on 2008-04-30
I agree with natrixgli, I always install webmin, I use it a lot, it helps enormously and is extremely good, but from past experience I wouldn't depend on it 100%, use the server supplied tools first and webmin second. My criticism of webmin is it tries to cover too many distros and sometimes doesn't get it quite right but as I said I always install and use it because it is so good.

Good luck :)

for those of you horrified at me using my server as a remote desktop, it does what I want it to do, it is logged on as a standard user with vino setup so I can use vncviewer and connect from my other PCs and leave the server programs running doing the work (like downloading dvd images of linux distros) while I go to bed and it's done by the morning. This way I don't have to remember complex commands and just use all those lovely gnome front-ends the likes of gwget, pan (newsreader), bittorrent, etc. Of course my firewall blocks all access from the outside world.

---

### Post by ginjabunny on 2008-05-01
I just noticed "ebox" web based config tool on the Ubuntu server how to page, this may help, see [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by soulskater on 2008-05-02
I use X-Windows on my servers and are proud of it, I like both worlds even on a server, mainly due to the fact that i often want to use graphical tools to get a overview of the system in hand and don't want to tie up a client computer solely for this purpose.

Here is a link to my how-to for installing X on Ubuntu Server with Gnome.
-> [8.04]("http://www.swedcore.net/?p=31") <- & -> [7.10]("http://www.swedcore.net/?p=14") <-

/soulskater

---

### Post by natrixgli on 2008-05-04
As for X on servers, I do it sometimes too, well with LTSP you have too.. But I find it mostly useless on web/mail/database/storage servers. On hosts for virtual machines, especially VMWARE, it's handy. 

Just curious, Soulskater - when you run X on servers is it running by default, or do you launch it only when needed? I always liked being able to use the command 'startx' (or similar)  instead of a display manager.

Cheers,

-n8

---

### Post by soulskater on 2008-05-05
It is running by default, which the installation takes care of, haven't found where to reconfigure it, so it would only start when wanted, but that shouldn't be to hard to figure out how.

/soulskater

---

### Post by samalex on 2008-05-05
Hi,

Just wanted to throw my two cents in...  I also run Ubuntu Server 8.04 on my home server, and I agree about not really wanting to run a GUI on a 'server'.  IMO this is the major downside to Windows servers because why spend the RAM and clockcycles on a GUI when it could be spent doing server tasks.

For a home user it might not be that big of an issue, but personally my home server sits headless in a corner of the spare bedroom with no desk or anything around it.  I use the various web tools (Webmin, CUPS, SWAT, etc) to manage it or edit config files via SSH as need be.

If GUI is a must, Fluxbox is a good low-end desktop manager that can be installed via apt-get.

Sam

---

### Post by niqmk on 2008-05-05
Hi, Good Day. Newbie here.
I've Installed A Gnome
With sudo apt-get, and it runs smoothly.
But when i rebooted the pc. The gnome doesn't show at all. It still run text based.
How can I run the gnome desktop?
Script or any?

---

### Post by vba_djs on 2008-05-05
> **niqmk said:**
> Hi, Good Day. Newbie here.
I've Installed A Gnome
With sudo apt-get, and it runs smoothly.
But when i rebooted the pc. The gnome doesn't show at all. It still run text based.
How can I run the gnome desktop?
Script or any?
Type **startx** at the command line.

---

### Post by stream303 on 2008-05-05
I found the following quite helpful:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Even though it initially addresses users with low-memory requirements, it has great steps on how to bring up a gui using the server install as a base.

In my case, I went extremely light weight by installing nothing more than xorg and lwm, manually using the startx technique to bring up the gui - when I'm done playing with the server stuff, I just drop back out of X.

---

### Post by niqmk on 2008-05-06
> **vba_djs said:**
> Type **startx** at the command line.

How can i start this module from booting?

---

### Post by stream303 on 2008-05-06
If you want to boot into a graphical environment automatically, the you probably want to install a login manager like xdm.

The idea behind startx in a server environment with a gui is that you have to start it manually if/when you need it - keeps resources low, and is somewhat better for security by not running all the time.  Best not to have a gui at all, but in this case, there ya' go..

---

### Post by niqmk on 2008-05-06
> **stream303 said:**
> If you want to boot into a graphical environment automatically, the you probably want to install a login manager like xdm.

The idea behind startx in a server environment with a gui is that you have to start it manually if/when you need it - keeps resources low, and is somewhat better for security by not running all the time.  Best not to have a gui at all, but in this case, there ya' go..

Great. so is there any environmet GUI like UBUNTU Performance?
i'm currently using openbox. That's ogre looking. :(

---

### Post by DrNick on 2008-05-06
Maybe we should put a sticky about GUI's on servers in general, this seems a really common question...

---

### Post by niqmk on 2008-05-06
> **DrNick said:**
> Maybe we should put a sticky about GUI's on servers in general, this seems a really common question...

GUI provides easier interface to use. Lightweight (and Beautiful) interface for server is really searched by the beginner administrator like me.
I think GUI at LINUX is a big issue especially hardware supported.

---

### Post by hyper_ch on 2008-05-06
What does a server need a GUI interface for?

---

### Post by niqmk on 2008-05-06
> **hyper_ch said:**
> What does a server need a GUI interface for?

I need a GUI for basic look to browse some file without type ls or dir. :lolflag:

---

### Post by ibutho on 2008-05-06
> **niqmk said:**
> GUI provides easier interface to use. Lightweight (and Beautiful) interface for server is really searched by the beginner administrator like me.
I think GUI at LINUX is a big issue especially hardware supported.
Whilst GUIs can be "easier" to use, they use up system resources unnecessarily and they introduce potential security holes.

---

### Post by DrNick on 2008-05-06
> **ibutho said:**
> Whilst GUIs can be "easier" to use, they use up system resources unnecessarily and they introduce potential security holes.

The argument that GUI's introduce potential security holes in a server is now mostly dead. All modern X.org releases now have sane security defaults which don't allow any connections to it, thereby removing 99.9% of security problems. 

A GUI does introduce complexity, and it does incur a very small amount of overhead in terms of memory and CPU. *However*, this should not put people off installing one for a SOHO server as it does make some admin tasks easier for non *NIX gurus. 

Installing one of the lighter GUI options would be the best choice, and starting it using the 'startx' script - as has already been suggested. 

To sum up, in a production environment where you have racks upon racks of servers, you almost certainly *don't* want a GUI on your servers. However, for a small office or home server, especially for people with less experience, a GUI is a good idea. Besides, GUI's are best for some tasks. Ever tried doing multiple LDAP admin tasks using only the CLI...

---

### Post by hyper_ch on 2008-05-06
There might be tasks where the GUI is best... but for 99% it's just plainly uselss

---

### Post by DrNick on 2008-05-06
> **hyper_ch said:**
> There might be tasks where the GUI is best... but for 99% it's just plainly uselss

That is a pretty short-sighted opinion. Whilst you yourself might find it useless, the issue here is what is most helpful for the person who posted in the first place. The fact you write GUI's off as 99% useless indicates that you've not understood his situation. 

This notion that some people have that you must use the CLI for everything to be counted as a valid user is ridiculous. It is hugely unhelpful when it comes to introducing others to the world of Linux on the server and is more likely to completely put them off as oppose to helping them.

---

### Post by hyper_ch on 2008-05-06
> **DrNick said:**
> That is a pretty short-sighted opinion. Whilst you yourself might find it useless, the issue here is what is most helpful for the person who posted in the first place. The fact you write GUI's off as 99% useless indicates that you've not understood his situation. 
You forgot, we're talking here about servers ;)

> **DrNick said:**
> This notion that some people have that you must use the CLI for everything to be counted as a valid user is ridiculous.
Where was that said? And don't forget, we're talking here about servers...

> **DrNick said:**
> It is hugely unhelpful when it comes to introducing others to the world of Linux on the server and is more likely to completely put them off as oppose to helping them.
The linux server world has no gui :) There's (almost) no need for it. By pointing this out you are helping them.

---

### Post by windependence on 2008-05-06
Think about it though, if you are installing SERVER, then you shouldn't go boogering up the install to make it a DESKTOP.

Windoze has ruined so many otherwise good admins making them think they can't do it without a GUI. It's like a drug, once you do it, you're hooked. I have to admit, in my younger days I was like that and fought tooth and nail from using the CLI. Now, I use many BSD boxes for real production environments and I have no GUI or X even installed. these machines are lean and mean. All my VMware machines are GUIless (is that a word?). Anyway, I wouldn't have it any other way. A GUI on a server machine introduces many things that contribute to instability and that's one thing I don't need on my servers.

-Tim

---

### Post by DrNick on 2008-05-06
> **hyper_ch said:**
> You forgot, we're talking here about servers ;)


No, I didn't forget. I'm talking about server's too...

> **hyper_ch said:**
> 
The linux server world has no gui :) 


Really. Would that by why two Linux distro's aimed only at servers (SLES & RHEL) both come with a very functional GUI by default? These aren't exactly small or unheard of distro's either, more like the two main distro's any hardware manufacturer is likely to officially support.

As I've said above, I am not trying to imply every Linux server needs a GUI - many do not. Rather my point is that *some* Linux servers might need a GUI of some kind, for a variety of reasons - one of which might be the level of skill and experience of the user. 

One of the key attributes of any skilled IT person is finding the right tool for the job. For some people, in some situations, a GUI is the correct tool.

---

### Post by bigfatdummy on 2008-05-06
Until you actually use something like webmin, you really don't understand how easy it is and why you don't want/need to install a gui. To be honest, I think its actually easier to admin a linux server using webmin than if you have a desktop installed. Everything you want/need is right there and you can tweak it how you want.

---

### Post by soulskater on 2008-05-07
Hmm, is'nt webmin a gui like the the X is, hmm so your saying that just because you fetch it via your browser it is not a gui???(Being ironic...)

Sure there may be less overhead on the server but it IS still a graphical tool used to administer the server, so it comes down to what you like best and i personally like running X on my servers.

It is every man for himself that decides what they want to use on their servers, the beauty is that you actually can choose how you want to administer your server, X, webmin, console, it is all there, some with minor configuration but still, the OS doesn't limit your choice in that way  which i find great since i personally really like both worlds.

---

### Post by hyper_ch on 2008-05-07
> **soulskater said:**
> Sure there may be less overhead on the server but it IS still a graphical tool used to administer the server

If you want to be picky, then the CLI is also a GUI

---

### Post by CREEPING DEATH on 2008-05-07
Wibmin works well, I use it on my Debian web server.
As far as adding a GUI to a server:```

sudo aptitude install xorg
sudo aptitude install gnome-core synaptic
```
Now you can log in and type ```

startx
```
each time or ```

sudo aptitude install gdm
```
to boot to a GUI.
You've just set up a core GUI that will let you do most (maybe all) of what you want to do without loading it up with fluff and bloat.
You can set up VNC to remotely administer your server, I'll be doing this on my file server when I build it soon.

CD

---

### Post by la3875 on 2008-05-07
All;

I've been watching this thread and appreciate the many excellent comments and tools for setting up and managing a server. I think messybricks much like me is trying to settle on the best tool to use to learn from and build confidence with the setup. It may seem sacrilegious to some but I'd personally like to see an Ubuntu Server with a GUI setup and maintenance tool that gave home users and noobs like me the confidence and experience to set up a home file server to maintain the photos and music and backups we all know we accumulate. It would give folks a chance to repurpose that old pc and keep it out of the landfill for another year or two, and in my opinion build some additional value to linux and the community. We all know there are many pieces of hardware out there that run some linux code or variant that make up our home networks that go unseen by most. Why not put out an option for the typical home user to set up a server without putting another $$ into M$ coffers by buying into the WHS scheme?

Great work all!

---

### Post by windependence on 2008-05-07
> **soulskater said:**
> Hmm, is'nt webmin a gui like the the X is, hmm so your saying that just because you fetch it via your browser it is not a gui???(Being ironic...)

Sure there may be less overhead on the server but it IS still a graphical tool used to administer the server, so it comes down to what you like best and i personally like running X on my servers.

It is every man for himself that decides what they want to use on their servers, the beauty is that you actually can choose how you want to administer your server, X, webmin, console, it is all there, some with minor configuration but still, the OS doesn't limit your choice in that way  which i find great since i personally really like both worlds.

The difference here is that since the GUI is rendered somewhere other than the server, it doesn't take near the resources that X would running directly on the hardware. Webmin is better than running a GUI on the server but IMHO it is still a crutch and actually still can be a large security risk. 

That being said, I have been where the OP is and I understand that the learning curve for the CLI is very steep. Some time ago I actually FORCED myself not to use a GUI by loading up some BSD machines I wanted to serve up the web on. It was the best thing I ever did. having a GUI is nice for a home server but the first time it doesn't load (and that time WILL come for you) what will you do? if you can drop to a console and fix the problem, your life will be so much easier.

-Tim

---

### Post by soulskater on 2008-05-08
I know how to use the console, i actually have FreeBSD machines running at home and have had them for about 10 years so don't doubt that i know my way around the console, BUT i still think that sometime it is actually nicer with a GUI where you can get an overview of things, for example having 2 or more console windows open along side the system log where most of the logs are gathered and so forth.

I think that learning the console is an absolute must but one should not be limited to that just because it is a server. I agree that the Gnome may not be the best GUI for a server and that XFCE might be better or even Webmin the choice is up to everyone alone to decide, all we can do along the way is help and guide.

As i stated before i like both worlds and like to mix them around a little.

/Marcus

---

### Post by hyper_ch on 2008-05-08
> **soulskater said:**
> BUT i still think that sometime it is actually nicer with a GUI where you can get an overview of things, for example having 2 or more console windows open along side the system log where most of the logs are gathered and so forth.
Heard of "screen"?

---

### Post by stream303 on 2008-05-08
On some boxes / screens, the vga graphics are so bad that just a minimal install of xorg, xterm, and the lwm window manager are the ticket to saving my eyes when staring at xterm all day. :)

Everyone has their favorite wm, but for my money LWM is just perfect for those that find TWM bloated - no menus, just xterm if you middle-click.

Xterm hint for bad eyes:  Ctrl-right click to select huge fonts.  Even nicer, bring up the first xterm and immediately issue:
```
xterm -fa mono -fs 14 & 
```

(choose your appropriate -fs size...)

I don't need no stinkin' menus. :) Just give me LWM and my eyes are happy on a server...  No real exit either - just drop out with Ctrl-Alt-backspace/delete

(Note: if you want to do a test run with LWM on a desktop, you'll need to install it, and then when you login, choose "failsafe terminal" from the session menu.  Start lwm from there)
```
lwm &
```

---

### Post by soulskater on 2008-05-08
I still consider a GUI gives you better overview, at least for me, I'm ok if you like to use console and screen exclusively but the question is can you accept that other might not?

I have rarely used the screen functions and can agree that they are useful for those who like working that way.

I firmly believe in the freedom of choice and to have the choice to use GUI, Console, Webmin, Screens do i find as one of the cornerstones when it comes to open source freedom.

---

### Post by songshu on 2008-05-10
> **ocotillo said:**
> The original question IS reasonable: how to install a GUI in a server.

I'm a long-time Windows administrator and I can use the Windows server command line as good as anyone.  Now I need to run a *nix server -- right away, and not in a few weeks or months when I get a good handle on the CLI.  I need an intermediary solution until I am up-to-speed, and I like the startx solution that allows me to turn on a GUI when I absolutely need it, but also urges me to learn the CLI.

I find the *nix user community to be not a lot of help to a newbie.  "Do a sudo..."!  and I'm going "What the heck is sudo..?" and it takes me another 30 minutes to track THAT down.

Technical skills do not magically spring up the instant you install Linux, it's a learning curve, and the -- dare I say smugness -- in the community makes that curve a lot steeper than it needs be, and frankly, has me wondering why I want dedicate so much of my time learning to use *nix at all.  I have other obligations...

Please relax about people trying to help others like me who really want to learn to use Ubuntu but haven't the foundation that you yourself have.

Peace.



i think you are right, this question has turned into a discussion going nowhere. i think part of it comes from some misunderstanding between the meaning of GUI, desktop and server-administration panel

and part of it maybe because a lot of people on these forums who help "newbies" are still pretty fresh themselves, but i'm pretty sure everybody's intention to help is sincere. hope i don't offend anybody here ;)

on-topic:

if you ask for a GUI on a server i assume you are not talking about having a desktop environment with webbrowser like firefox or a mail client like evolution etc...
offcourse you could run a desktop, but it would not help you very much if you only want to install and administer a web or file server because you will not find any administration tools there to help you with that.

side-note:

in the Nix world, X is another server itself but it is not ment to administer other servers, or at least thats not the primary intention.
that is however exactly where the story comes from that:
A its not user friendly
B it is stable and secure

there is a very good reason that you don't want unnescesary things installed if your aim is to have 100% uptime on your web or mailserevr.

on-topic again:

what i do assume:
you want to set up somethings like file, printer, web or mail server.
you could do all those from the command line, wich is my personal preffered way, but if you want to have something graphical you could use something like webmin or ebox 
[http://ebox-platform.com/screenshots/](http://ebox-platform.com/screenshots/)
[http://webmin-demo.virtualmin.com/](http://webmin-demo.virtualmin.com/)



p.s.

it does however take some time to learn a new operating system, please don't take the years to learn what you know now for granted, that did not come in a day either..

personnaly i get lost and confused when not dealing with posix compatible systems so i stay away from them because.

if you do not have time to learn,  i would advise not to start in the first place. 

if you do have time, the rewards may be worth it.

---

### Post by deleonjavier on 2008-05-10
ok So i've installed 8.04 server and yes yes i have installed a gui, but not because i wanted to but my younger brother 18 doesn't know the CLI very well. He uses it to leave downloads running overnight. I run programs from the server sometimes using ssh Xforwarding which I find to be incredibly awesome. But the problem with using xforwarding is that when you close the program from the client it closes the process on the server. Is there any way to leave programs running (like torrent clients) through terminal or even webmin. (webmin is awesome btw) I wanna get rid of my gui. I use this server for web/mail/database/smb/ please help.

---

### Post by songshu on 2008-05-10
> **deleonjavier said:**
> ok So i've installed 8.04 server and yes yes i have installed a gui, but not because i wanted to but my younger brother 18 doesn't know the CLI very well. He uses it to leave downloads running overnight. I run programs from the server sometimes using ssh Xforwarding which I find to be incredibly awesome. But the problem with using xforwarding is that when you close the program from the client it closes the process on the server. Is there any way to leave programs running (like torrent clients) through terminal or even webmin. (webmin is awesome btw) I wanna get rid of my gui. I use this server for web/mail/database/smb/ please help.

somethink like 

```
nohup utorrent /path/to/file.torrent
```

---

### Post by songshu on 2008-05-10
> **hyper_ch said:**
> 

Okay, look, you'rte just acting like an ***, so let it alone.

BTW - (a) Windows dominates the marketplace 

And you say this because of ...?



And you want to say this because ... ?

why don't you 2 don't just go
```
apt-get install bitchx
```
somewhere else?

---

### Post by deleonjavier on 2008-05-10
this would open the torrent but how do you configure settings such as destination speed and etc. I've never ran things through nohup, it looks interesting. thanks for the help, and thank you very much for not making fun of me.

---

### Post by songshu on 2008-05-10
> **deleonjavier said:**
> this would open the torrent but how do you configure settings such as destination speed and etc. I've never ran things through nohup, it looks interesting. thanks for the help, and thank you very much for not making fun of me.

offcourse i will not make fun, i usually send checks ;)

i am not really familiar but you could do 

apt-get install rtorrent

and then

man rtorrent

i just had a look and there seem to be plenty of options.

but i remember having seen web based interfaces for torrent as well before, you would have to google for that but it might be exaclty something you are looking for

---

### Post by songshu on 2008-05-10
i couldn  resist and was curious,

how about this?
[http://www.torrentflux.com/](http://www.torrentflux.com/)

you can get it with apt-get

---

### Post by magickangaroo on 2008-05-10
> **songshu said:**
> i couldn  resist and was curious,

how about this?
[http://www.torrentflux.com/](http://www.torrentflux.com/)

you can get it with apt-get

torrentflux-b4rt is what i run at home. its pretty good, will have to build from source afaik.  it has alot of extra features built in, the main one people may appreciate is the support for nzb files.

/mgk

---

### Post by windependence on 2008-05-11
> **deleonjavier said:**
> ok So i've installed 8.04 server and yes yes i have installed a gui, but not because i wanted to but my younger brother 18 doesn't know the CLI very well. He uses it to leave downloads running overnight. I run programs from the server sometimes using ssh Xforwarding which I find to be incredibly awesome. But the problem with using xforwarding is that when you close the program from the client it closes the process on the server. Is there any way to leave programs running (like torrent clients) through terminal or even webmin. (webmin is awesome btw) I wanna get rid of my gui. I use this server for web/mail/database/smb/ please help.

The "correct" way to do this in terms of a "real" server is to keep your torrent downloads on the file server but actually download them on your desktop machine with a share mapped to the file server. IMHO if you are d/l torrents on the server, it's really a glorified desktop machine. I think this is where the confusion comes in. No offense but many noobs think that if it says "server" it must somehow be better or more powerful. It may be, but desktop apps like bittorent have no place on a "real" server. Things like Apache, Samba, and MySQL are found on a real server. You can access the server from a desktop machine to do all your administration tasks. You can even do it from a GUI, but on the DESKTOP machine, not the server. Maybe I'm a purist, but I don't believe a GUI should ever be installed on a "real" server.

-Tim

---

### Post by songshu on 2008-05-11
> **windependence said:**
> The "correct" way to do this in terms of a "real" server is to keep your torrent downloads on the file server but actually download them on your desktop machine with a share mapped to the file server. IMHO if you are d/l torrents on the server, it's really a glorified desktop machine. 

-Tim

this i truly don't understand, why would downloading or the bittorent protocol be specific to a desktop? its a perfect server purpose

---

### Post by hyper_ch on 2008-05-11
> **songshu said:**
> why don't you 2 don't just go
```
apt-get install bitchx
```
somewhere else?

Why don't you do it? ;)

> **windependence said:**
> It may be, but desktop apps like bittorent have no place on a "real" server.
Luckily there are cli/curses based torrent clients ;)

---

### Post by windependence on 2008-05-11
> **songshu said:**
> this i truly don't understand, why would downloading or the bittorent protocol be specific to a desktop? its a perfect server purpose

It's downloading files, it's not "serving" them in the traditional sense. I guess if you were to call it a "personal" server, or if you were actually serving torrents then you could call it a "server", but any desktop product would do just as well for that stuff if not better. 

I don't want to sound like a server snob here but U run real servers everyday for a living and we don't run GUIs. These are mission critical applications that cannot crash. There is a good reason we don't run GUIs and that is for stability. Anything we need to do is done from another machine remotely and we hardly ever touch the actual box. some of our servers are running for over 880 days without a reboot.

-Tim

---

### Post by hyper_ch on 2008-05-11
bittorrent also serves at the same time... it's made to do both...

---

### Post by windependence on 2008-05-11
> **hyper_ch said:**
> bittorrent also serves at the same time... it's made to do both...

I guess if you want just a Torrent server, one GUI app is not gonna kill ya if you use a light GUI on it. I am always thinking in terms of mission critical applications. I suppose for some people, Bittorrent IS mission critical. :)

-Tim

---

### Post by hyper_ch on 2008-05-11
just use rtorrent :) no gui required and even the people at TBP and mininova use it ;)

---

### Post by songshu on 2008-05-11
> **windependence said:**
> It's downloading files, it's not "serving" them in the traditional sense. I guess if you were to call it a "personal" server, or if you were actually serving torrents then you could call it a "server", but any desktop product would do just as well for that stuff if not better. 

I don't want to sound like a server snob here but U run real servers everyday for a living and we don't run GUIs. These are mission critical applications that cannot crash. There is a good reason we don't run GUIs and that is for stability. Anything we need to do is done from another machine remotely and we hardly ever touch the actual box. some of our servers are running for over 880 days without a reboot.

-Tim

i don't mind if you talk like a server snob, but i guess when you say "we" and "our" servers, its actually not "your" servers . 

i think you are missing the point here.
since when is a server only ment for uploading?
even then, consider what bittorrent does ;)
since when do you need a GUI to run bittorrent? 
we were discussing rtorrent, please check before you spit

880 days? when was the last time you patched the kernel with a security update?

show me the ip's of all your servers and i'll show you mine ;)

---

### Post by windependence on 2008-05-11
> **songshu said:**
> i don't mind if you talk like a server snob, but i guess when you say "we" and "our" servers, its actually not "your" servers . 

i think you are missing the point here.
since when is a server only ment for uploading?
even then, consider what bittorrent does ;)
since when do you need a GUI to run bittorrent? 
we were discussing rtorrent, please check before you spit

880 days? when was the last time you patched the kernel with a security update?

show me the ip's of all your servers and i'll show you mine ;)


OK to be fair I am talking about the servers where I work. Even if I gave you the IPs, you wouldn't be able to access them. I work for a fortune 100 company and they are behind at least 3 firewalls. Every 220, 440, and 880 days we get an "error" message that says we may want to consider a reboot. Some of our updates are with modular kernels so no reboot is necessary, and some are simply not updated as they are quite secure where they are.

Now, as to MY servers, I run VMware on top of Linux, mostly SuSE and Ubuntu server. The actual production machines are all BSD boxes, serving web pages, e-mail, and databases, all without a GUI. I manage all of those from the CLI. The closest I get to a GUI is Midnight Commander. My servers are at 71.39.77.108 if you want to take a look. :)

No need to be nasty, I know you were talking about rtorrent, but the subject of this thread is running a GUI on Ubuntu server. I am just trying to help.

-Tim

---

### Post by songshu on 2008-05-11
> **windependence said:**
> OK to be fair I am talking about the servers where I work. Even if I gave you the IPs, you wouldn't be able to access them. I work for a fortune 100 company and they are behind at least 3 firewalls. Every 220, 440, and 880 days we get an "error" message that says we may want to consider a reboot. Some of our updates are with modular kernels so no reboot is necessary, and some are simply not updated as they are quite secure where they are.

Now, as to MY servers, I run VMware on top of Linux, mostly SuSE and Ubuntu server. The actual production machines are all BSD boxes, serving web pages, e-mail, and databases, all without a GUI. I manage all of those from the CLI. The closest I get to a GUI is Midnight Commander. My servers are at 71.39.77.108 if you want to take a look. :)

No need to be nasty, I know you were talking about rtorrent, but the subject of this thread is running a GUI on Ubuntu server. I am just trying to help.

-Tim

LOL ;) no pun intended here, well.....OK just a little then.

but the original thread got hijacked i guess and the poster i replied to wanted to get rid of the desktop on his server but still be able to keep his torrents running.

damn..have not seen mc since slackware 7, is it still around?

---

### Post by windependence on 2008-05-11
Yep, mc is still around and kickin'. I don't use it as much as I used to, but it's great to see the directory structure in tree form from an ssh terminal.

-Tim

---

### Post by deleonjavier on 2008-05-24
torrentflux looks awesome, unfortunately the private torrent tracker community doesn't accept connections from bittornado. sucks i know, but i'm getting better at administrating with ssh and xfowarding, i need to get better at setting commands without having a ssh client on

---

### Post by blitzkin on 2008-05-28
will it take long if i do apt-get install ubuntu-desktop? it seems that its downloading too many files when i tried it..

---

### Post by NateMan on 2008-05-28
Your installing a large desktop on a cli interface, of course your going to download a huge amount of files.

---

### Post by blitzkin on 2008-05-28
thats what i thought.. i just hope all will work out good once its done. thanks for the info nateman.

---

### Post by NateMan on 2008-05-28
Why don't you make a new thread next time instead of resurrecting a 2 week old one? Then users searching the forums would see your post and topic, not the other one.

---

### Post by soulskater on 2008-05-29
Try this how-to: [http://www.swedcore.net/?p=31](http://www.swedcore.net/?p=31)

/Marcus

---

### Post by javisan60 on 2008-05-31
I am totally new, to server, I have installed the Webmin, but I can not make it appear in my screen. 

I have installed Firefox 3, but now it says that has no display assigned?

Sorry, I now, I have to do my homework, Bought "Begining Ubuntu Server Administration", from novice to Professional by Sander van Vugt, but it does not really help in.

Any Clues?

---

### Post by quelx on 2008-05-31
> **javisan60 said:**
> I am totally new, to server, I have installed the Webmin, but I can not make it appear in my screen. 

I have installed Firefox 3, but now it says that has no display assigned?

Sorry, I now, I have to do my homework, Bought "Begining Ubuntu Server Administration", from novice to Professional by Sander van Vugt, but it does not really help in.

Any Clues?

Does Firefox open at all? Can you post the exact error you see?

---

### Post by emilije on 2008-05-31
hello to everybody,

is webmin complete solution for administering server or should I need install something more and what would that be? As I can see, webmin have everything I need for administration but i'm just asking :)

PS: I have UbuntuServer8.04 without GUI configured as LAMP, samba file server and ssh

---

### Post by javisan60 on 2008-05-31
When I type firefox, the usual program does not star, but says:  error:  no display especified.

I have used the Ubuntu Desktop for about 9 months, more than happy.  But no idea how to start Firefox to use webmin.

Thank you.

---

### Post by windependence on 2008-05-31
> **emilije said:**
> hello to everybody,

is webmin complete solution for administering server or should I need install something more and what would that be? As I can see, webmin have everything I need for administration but i'm just asking :)

PS: I have UbuntuServer8.04 without GUI configured as LAMP, samba file server and ssh

You need to browse from another machine on your network to:


[https://yourserverIP:10000](https://yourserverIP:10000)


If you have not set it to use SSL, then leave out the 's' in the URL.

Also, you cannot start firefox without a GUI loaded which I ould not recommend on a server. Webmin and/or the CLI should do everything you need.

-Tim

---

### Post by javisan60 on 2008-05-31
That's it, I was on the screen of the server..........

Also used Iconfig to look wich is the IP address, then follow your advice, and I tiped hhtps://198.162.1.100:10000/ and webmin is on my desktop screen, 
good start, now I need to make the address available to my co-workers tru the internet....


Thank you.....

---

### Post by molotov00 on 2008-05-31
If you must allow some access from the internet so be it, but I'd block external requests to webmin by not forwarding that port.

---

### Post by Z2. on 2008-06-04
To those that answered the original question - you are fantastic!

To those who would swear that GUI's are the devil's beast - try setting up a standalone VMWare server sandbox without a GUI as a newbie - I have been searching for hours to get half the code to install and configure VMWare, with a GUI I can do it in minutes (OK, quite a few minutes, but less than an hour anyway).

GUI's are another tool, possibly not required by the Guru's, but a staple for the newbies like me.

---

### Post by nexus9k on 2008-06-05
Sorry for showing up so terribly late to the party.

> for example having 2 or more console windows open along side the system log where most of the logs are gathered and so forth.


Check out multitail -- it's perfect for doing this, and you can even run it in screen.  ;)

---

### Post by trmentry on 2008-06-06
> **Z2. said:**
> To those that answered the original question - you are fantastic!

To those who would swear that GUI's are the devil's beast - try setting up a standalone VMWare server sandbox without a GUI as a newbie - I have been searching for hours to get half the code to install and configure VMWare, with a GUI I can do it in minutes (OK, quite a few minutes, but less than an hour anyway).

GUI's are another tool, possibly not required by the Guru's, but a staple for the newbies like me.

what do you mean by vmware server sandbox?

I have a headless 7.10 ubuntu server running 1.0.6 vmware server with 4 vm's.  

Setting it up was a snap.  

```

sudo apt-get install build-essential linux-headers-`uname -r` xinetd

```

then extract the server tar.gz file you got from vmware and execute the ./vmware-installer.pl file. (going on memory here, it maybe ./vmware-install.pl).

Defaults are fine.  It will compile your kernel modules and off you go.

then go to a windows or linux desktop machine and install the vmware server console utility.  (download from vmware as well)

Run that and then select Connect To Remote Host, enter the IP of your server and username/passwd.  Once connected you can then  create/modify/edit/delete, etc vm's on the server that you have.

the 1.0.6 version of vmware server will install the web mui as well.  It did for me at least when I just upgraded a few days ago from 1.0.4.  You can then use a browser to go to [https://serverIP:8333/vmware/en/](https://serverIP:8333/vmware/en/)   to get a web based gui of the vm's.  Not gotten the 'launch console' from there to work yet.

No gui necessary on the server.


I agree that a gui can make things easier... and when things are easier you learn things. :)  And learning is always a good thing.

---

### Post by windependence on 2008-06-06
You can also launch and manage VMs via the CLI. there is a full scriptable set of commands for Vmware server.


-Tim

---

### Post by gtdaqua on 2008-06-07
> **trmentry said:**
> what do you mean by vmware server sandbox?

I have a headless 7.10 ubuntu server running 1.0.6 vmware server with 4 vm's.  

Setting it up was a snap.  

```

sudo apt-get install build-essential linux-headers-`uname -r` xinetd

```

then extract the server tar.gz file you got from vmware and execute the ./vmware-installer.pl file. (going on memory here, it maybe ./vmware-install.pl).

Defaults are fine.  It will compile your kernel modules and off you go.

then go to a windows or linux desktop machine and install the vmware server console utility.  (download from vmware as well)

Run that and then select Connect To Remote Host, enter the IP of your server and username/passwd.  Once connected you can then  create/modify/edit/delete, etc vm's on the server that you have.

the 1.0.6 version of vmware server will install the web mui as well.  It did for me at least when I just upgraded a few days ago from 1.0.4.  You can then use a browser to go to [https://serverIP:8333/vmware/en/](https://serverIP:8333/vmware/en/)   to get a web based gui of the vm's.  Not gotten the 'launch console' from there to work yet.

No gui necessary on the server.


I agree that a gui can make things easier... and when things are easier you learn things. :)  And learning is always a good thing.

Thats right. Setting VMWare on Gutsy/Feisty is very simple. There are numerous distro-specific guides on the net and in this forums. Getting VMWare to work in Hardy could be tricky because they but patches are available. All in all, it should not be difficult for a user who searches for specific help.

---

### Post by crtlbreak on 2008-06-18
> **Brazen said:**
> Er, I'm pretty sure you didn't really mean to say what you just said.  It is a very BAD idea to edit your config files in programs such as Abiword or OpenOffice Writer because, while it *looks* like the same text on the screen, those fancy editors add in a lot of extra data to the file.

So just to clarify, I'm sure what hyper_ch meant is that you can edit files in plain text editors like Mousepad (in Xubuntu) or Gedit (in Ubuntu).

Hi Brazen
What hyper_ch actually said was editors such as vi and nano - perfect editors for any of those files - i didnt see him mention Open Office anywhere? :confused:
regards

---

### Post by Krillin on 2008-06-24
10 pages and no one bothered to post up a true answer to this question except with gnome or webadmin. The rest are LINKS to other websites to generate traffic to their site. Then 3 or 4 pages of NOTHING BUT DEBATES OF PERSOANL OPINIONS. Please take it somewhere else. Come on guys. WTH are we doing here? Wasting other people's time?
 
Anyways, luckfully, I already know how to do this with KDE being as I started this with Debian and ubuntu is a derivitive of Debian. So the following steps works as well.
 
[SIZE=6][COLOR=royalblue]KDE 3.5.9[/COLOR][/SIZE]
To Install KDE on your ubuntu-server8.04 do the following:
```
sudo apt-get install x-window-system-core kde
```
 
Then install the log in GUI:
```
sudo apt-get install kdm
```
 
Then reboot your server with the following:
```
sudo shutdown -ar "now"
```
 
[SIZE=6][COLOR=royalblue]KDE 4[/COLOR][/SIZE]
If you want to install the new KDE4 then do the following:
```
sudo apt-get install x-window-system-core kde4
```
 
Then install the log in GUI:
```
sudo apt-get install kdm-kde4
```
 
Then reboot your server with the following:
```
sudo shutdown -ar "now"
```
 
After you run this and update your kernel with KPackage you will have one small issue with DHCP. If you are DHCP-Reserved Client follow the next step.
 
I recoment you do the following **before** rebooting:
```
sudo touch /var/lib/dhcp3/dhclient.eth0.leases
chown /var/lib/dhcp3/dhclient.eth0.leases
 
[SIZE=6][COLOR=royalblue]GNOME[/COLOR][/SIZE]
If you want to install the GNOME then do the following:
[code]sudo apt-get install gnome
this will install additional software like gnome-office, eveloution, etc.
```
 
To install a smaller set of apps:
```
sudo apt-get install gnome-desktop-environment
```
 
Then reboot your server with the following:
```
sudo shutdown -ar "now"
```
 
What ever you do, do not run both KDE installs. It can and will cause conflicts and problems.
 
The options are out there, choose wisely.
 
Goodluck,
Krillin

---

### Post by windependence on 2008-06-25
No, just in case you missed it we are in the SERVER forum, not the DESKTOP forum. We were educatiing the OP on the benefits of learning the CLI instead of loading a bloated GUI on a SERVER.

-Tim

---

### Post by Krillin on 2008-06-25
> **windependence said:**
> No, just in case you missed it we are in the SERVER forum, not the DESKTOP forum. We were educatiing the OP on the benefits of learning the CLI instead of loading a bloated GUI on a SERVER.
 
-Tim
 
I didn't miss it, thanks. If I wanted CLI I would pull out my D.O.S. 5 floppies and have at it. I do not miss those days of typing and learning.
 
Running a GUI is what everyone really expects. The point & click and type an answer to a few questions is the way computers are and what we have adapted to in this 21st century weather Desktop or Server.
 
I was surprised to see ubuntu-server did not have a GUI either. So this was my solution to the problem.
 
For some users, a GUI is more resourceful than a CLI. You CANNOT multitask in a CLI like you truly can in a GUI. Making you more productive as well. Now you can't argue with that.
 
Krillin
:-\"

---

### Post by hyper_ch on 2008-06-25
> **Krillin said:**
> Running a GUI is what everyone really expects.
No, running a gui is what desktop users really expect ;)

> **Krillin said:**
> I was surprised to see ubuntu-server did not have a GUI either.
If you would inform yourself about servers you wouldn't be surprised at all...
 
> **Krillin said:**
> For some users, a GUI is more resourceful than a CLI. You CANNOT multitask in a CLI like you truly can in a GUI. Making you more productive as well. Now you can't argue with that.
Sure you can ;) ever heard of "screen"?

---

### Post by windependence on 2008-06-25
> **Krillin said:**
> I didn't miss it, thanks. If I wanted CLI I would pull out my D.O.S. 5 floppies and have at it. I do not miss those days of typing and learning.
 
Running a GUI is what everyone really expects. The point & click and type an answer to a few questions is the way computers are and what we have adapted to in this 21st century weather Desktop or Server.
 
I was surprised to see ubuntu-server did not have a GUI either. So this was my solution to the problem.
 
For some users, a GUI is more resourceful than a CLI. You CANNOT multitask in a CLI like you truly can in a GUI. Making you more productive as well. Now you can't argue with that.
 
Krillin
:-\"

This is what Ubuntu has to say about it:

> **No X server by design**

By design, Ubuntu Server Edition does not include an X server. [COLOR="Red"]This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator. [/COLOR]

"So I applaud the Ubuntu team’s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server."
--Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server" 

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

Can't argue with THAT can you?

> **Krillin said:**
> Running a GUI is what everyone really expects. The point & click and type an answer to a few questions is the way computers are and what we have adapted to in this 21st century weather Desktop or Server.

Running a GUI on a server is what WINDOZE admins expect. REAL admins use the CLI and have been for decades.

You have a lot to learn in the server space.

-Tim

---

### Post by REMcCain on 2008-08-30
> **windependence said:**
> 

Running a GUI on a server is what WINDOZE admins expect. REAL admins use the CLI and have been for decades.

You have a lot to learn in the server space.

-Tim

You have a lot to learn, because a REAL admin uses switches.

[http://www.youtube.com/watch?v=iIsZVqhaneo](http://www.youtube.com/watch?v=iIsZVqhaneo)

Only users have those fancy VT05 terminals, ya whipper-snapper.

---

### Post by hyper_ch on 2008-08-30
> **REMcCain said:**
> You have a lot to learn, because a REAL admin uses switches.

[http://www.youtube.com/watch?v=iIsZVqhaneo](http://www.youtube.com/watch?v=iIsZVqhaneo)

Only users have those fancy VT05 terminals, ya whipper-snapper.

and you want to say with that?

---

### Post by cariboo on 2008-08-30
Geez can't you take a joke. :) That type of post is a running meme on Slashdot.

Jim

---

### Post by windependence on 2008-08-31
> **hyper_ch said:**
> and you want to say with that?

C'mon Hyper, step AWAY from the terminal :)

I got the joke actually and though it was funny because I actually DID run some DEC stuff when I first started in this business. I also have used punchcards. Ever think what happens when you drop a big stack of those? Each one executes a command and they are in order. Kids have it so good today what with the fancy CLI and everything. ;)

-Tim

---

### Post by Frankincell on 2008-08-31
Thank you, thank you, thank you. Just what I was looking for.

---

### Post by REMcCain on 2008-09-01
> **hyper_ch said:**
> and you want to say with that?

and you want to stay with a CLI?
After toggling switches, using a mouse to klik a few icons is heaven.

---

### Post by REMcCain on 2008-09-01
> **windependence said:**
> C'mon Hyper, step AWAY from the terminal :)

I got the joke actually and though it was funny because I actually DID run some DEC stuff when I first started in this business. I also have used punchcards. Ever think what happens when you drop a big stack of those? Each one executes a command and they are in order. Kids have it so good today what with the fancy CLI and everything. ;)

-Tim

Never dropped punchcards, thank God.  But I have had some joker put a EOT about 900 feet into my backup.  I also had a clutch go out on a RM03, which made for a very interesting disk swap.

---

### Post by Francewhoa on 2009-06-29
If you want to setup a web server. I wrote a how-to handbook at [http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)
It covers installing Virtualmin, Webmin & Usermin.

---

### Post by dtoronto on 2009-06-29
Webmin is the free version.  It's really not very good, but I have been hearing a lot about cPanel.  I don't know too much about it, but I don't think it's open.

---

### Post by windependence on 2009-06-30
> **aa52828 said:**
> How can I install and configure VNC server from PuTTY?

This is really off topic for this thread. If one of the mods can split this off, we can answer it for you. You really should consider a more secure alternative like NoMachine or just forward X through and ssh session for GUI apps.

-Tim

---

