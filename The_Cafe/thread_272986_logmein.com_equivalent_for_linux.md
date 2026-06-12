---
title: "logmein.com equivalent for linux"
date: 2006-10-07
forum: The Cafe
---

### Post by waldorf on 2006-10-07
I have fooled around with logmein.com for a week or so on an old XP machine and found it kind of handy.

Is there an equivalent for linux?

Thanks in advance.

---

### Post by Engnome on 2006-10-07
What feature are you interested. Don't feel like browsing around on their (too flashy) site to try and figure out what you want. :)

---

### Post by reacocard on 2006-10-07
Take a look at VNC. it's not quite as simple as LogMeIn, but it provides the same functionality and works well.

---

### Post by Rackerz on 2006-10-07
Yeah VNC kicks butt and is built into Gnome (maybe KDE, not sure though).

---

### Post by waldorf on 2006-10-07
Thanks for the thoughts. I took a look at VNC and also played around with Remote Desktop and Terminal Server Client in the Ubuntu menus. Given that I don't have a static IP (my ISP periodically assigns me a new one). That seems to add a significant wrinkle.

The other issue I think I have is security. Is logmein secure? I'm no expert by any means, but a bit of googling seems to indicate that at least a number of people are comfortable with its security. But who knows.

Thanks again for your thoughts!

---

### Post by reacocard on 2006-10-07
> **waldorf said:**
> Thanks for the thoughts. I took a look at VNC and also played around with Remote Desktop and Terminal Server Client in the Ubuntu menus. Given that I don't have a static IP (my ISP periodically assigns me a new one). That seems to add a significant wrinkle.

You can use a service like dyndns to assign a domain name to your computer and use that instead.

> The other issue I think I have is security. Is logmein secure? I'm no expert by any means, but a bit of googling seems to indicate that at least a number of people are comfortable with its security. But who knows.

According to its site, it has 256-bit SSL encryption, but only in the paid version.

---

### Post by Cyraxzz on 2006-10-07
VNC is quite similar and it's free of charge unlike logmein.com

---

### Post by waldorf on 2006-10-08
Actually, logmein is free, but it is limited to accessing windows machines. As far as I know it does not support linux.

VNC does seem like the way to go for linux accessing linux, and I your suggestions for how to make it work are greatly appreciated - thanks!

---

### Post by Roasted on 2006-10-08
I just found out about logmein.com the other day at school. Some other kids use it, however they ALL use windows at home. ](*,) 

Is there anyway you can cross match OS's with this, whether you use logmein or VNC? 

aka - Would EITHER option work with linux home pc/windows school pc?

---

### Post by waldorf on 2006-10-08
> **Roasted said:**
> I just found out about logmein.com the other day at school. Some other kids use it, however they ALL use windows at home. ](*,) 

Is there anyway you can cross match OS's with this, whether you use logmein or VNC? 

aka - Would EITHER option work with linux home pc/windows school pc?
I have used it without any trouble if I am using a linux machine to access a windows machine. You access the windows machine via a web browser so it doesn't matter if you are using linux, windows, BSD or Mac

---

### Post by reacocard on 2006-10-09
> **Roasted said:**
> I just found out about logmein.com the other day at school. Some other kids use it, however they ALL use windows at home. ](*,) 

Is there anyway you can cross match OS's with this, whether you use logmein or VNC? 

aka - Would EITHER option work with linux home pc/windows school pc?

VNC works on both Windows and Linux, as either server or client.

LogMeIn works as a client on any operating system with a modern browser and Java/ActiveX, but can only be used as a server on Windows.

So if you only want to access a windows PC, LogMeIn is your best bet, but for accessing a Linux box you'll have to use VNC.

---

### Post by ripperzane on 2007-02-20
One thing to remember is there are services for dynamic IPs (when your ISP changes it, this can be a hassle). The method I use to get them to show locally to each other (without the more sophisticated VPN type setups) is called hamachi. It was bought out by logmein.com and is available for linux/mac/windows and is free. The reason I state this is that is allows a virtual 2nd nic (atleast under windows) and gets it so that all the computers setup under the client appear to be on one network. Essentially it is for those of us that know of VPNs (or even those who don't) but want it to work easily and (from what I can tell) securely, oh and free. The best though I can see is setup tightVNC or NX and hamachi on the linux box in question and simply tunnel using the hamachi IP of the linux box (see hamachi.cc for all the details on mac/linux install) and it will resolve the issue of any IPs that change. (I am actually using this now to remote into my windows PC to post this so my work can't see where I've been :)
RZ

---

### Post by macogw on 2007-02-21
you can also use ssh tunneling and PuTTY to get from a Windows computer into your home Linux computers, though, ya know, again with the dyndns thing cuz of non-static ips

---

### Post by Sjoram on 2007-03-04
Resurrecting this thread to ask...

I use LogMeIn for my Windows clients and I do also use VNC as a backup incase LMI fails, although I prefer LMI for its simplicity.

The problem I have is a network on which I would regularly use the remote desktop feature blocks the ports used by VNC, so I'm kind of stuck!

Do I have any solution?

---

### Post by gabrielrodriguez81 on 2007-05-01
I recieved this message from a Logmein tech,

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Hi Gabriel,

Although LogMeIn does not officially support the Linux platform, some Linux variants do support partial functionality to be used as a local computer controlling a LogMeIn target computer.

This is done through our legacy support for java, which is a cross-platform development environment.  We do have official support for Linux on both sides of the connection planned for later this year, but for now, we do not support it officially.

To use a Linux computer to control a Windows PC running LogMeIn, you will need to install the Java Runtime Environment.

Most Linux distributions can install this from their Package Managers (RPM for Redhat based, Synaptic for Debian based, etc.).

Sun provides an RPM package at the link below.

If you would like to install manually, or do not use RPM to install packages, or have issues with the package manager install, try installing from source from the following link.

Note, you will need to go to Preferences > Remote Control settings and disable remote printing for the Remote Control feature to load properly and not with errors, since this isn't supported in Java on Linux.

Here is the link to install the RPM or source install of Java Runtime Environment.

[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)


I hope this helps. Please let us know if you have any further questions.

Thank you,
Sean Keough
LogMeIn Customer Support

Have you checked our Knowledge Base? Most questions can be answered quickly by going to [www.LogMeIn.com](www.LogMeIn.com). Just click the Support link, select the appropriate product, and type your question in the Search box!
[B]
------ Your Question/Comment ------
I would like to access my pc's using Ubuntu Linux, what version of Java should I have installed?[/B]
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

---

### Post by erik33s on 2007-08-20
My question is if you are using a Windows PC to log to a unix pc.. Witch application "logmein" or "vnc" or somthing else.

Thanks

---

### Post by reacocard on 2007-08-20
> **erik33s said:**
> My question is if you are using a Windows PC to log to a unix pc.. Witch application "logmein" or "vnc" or somthing else.

Thanks

You would have to use vnc for that.

---

### Post by Entity` on 2007-08-27
> **Roasted said:**
> I just found out about logmein.com the other day at school. Some other kids use it, however they ALL use windows at home. ](*,) 

Is there anyway you can cross match OS's with this, whether you use logmein or VNC? 

aka - Would EITHER option work with linux home pc/windows school pc?

To simplify, yes; there is a linux version of hamachi and it works.  By itself it comes with no GUI but there is a LogMeIn supported 3rd party GUI available.  Its been a long time since I've had internet, so I am curious as to the status of hamachi linux.  Ubuntu CAN see Windows computers and visa versa, but it is very slow and you have to create a browsable folder in linux so Windows can see linux.  In other words, hamachi is just a VPN program that enables the searchage of other computers (regardless of OS) over the internet.  I want to get a fully portable version so I can search my own computer (at home) from school.  The problem is that there is no portable version available last I checked.

---

### Post by Entity` on 2007-08-27
oops didn't read the second page sorry...

---

### Post by Sporkman on 2007-08-27
Also check out [www.nomachine.com](www.nomachine.com) .

---

### Post by Aaargh on 2007-09-09
Read your post, since I am looking for the same thing. Here is an idea: Just use you linux-computer via Putty. Install WMWare and let's say Windows XP on top of your Linux-computer and connect to that vm with Logmein.com.... I know...it's dirty but it's a workaround... :frown:

---

### Post by flatlinebb on 2007-09-20
One advantage that Logmein has over VNC, is that it runs an agent on the target machine, which helps in traversing NAT and firewalls, without having to open ports in your router. It reaches out from behind the firewall and gives you access. With VNC, one has to open a port or two in order to log in. If you already have a ssh port open, you can tunnel through it, without opening extra ports, however when dealing with a family member that's far away and not as computer literate, Logmein is a foolproof solution for supporting those loved ones.

I myself am looking for a product similar to LMI, to connect to a Linux desktop that will most likely connect via dial-up and have a different IP address each time it connects. I know I can run a dyndns client to get around the IP address problem. At this point I think the best solution is to run hamachi and then VNC into the target machine. It's free and once setup, it should just work.

---

### Post by tomtrainer on 2007-09-25
Regarding the response received from Logmein tech: the Java interface does not work as well as the ActiveX interface, so it would be good if they were made aware how many people want an equivalent to the ActiveX interface for Linux.

---

### Post by sites on 2007-10-04
A VM running Windows XP will allow everything you need on either end.  If you need to fully access a Linux box, just VNC through the Windows machine that runs the LogMeIn beacon.  I do this through my MacMini (Beta version) to access a Linux box & my OSx86 homebrew mac.

for example....

At work, my Feisty box running a Windows XP VM can log into my MacMini either directly or through a Parallels VM.  Then I use VNC to access those other pc's.  The whole thing kinda makes you dizzy thinking about it. lol

---

### Post by distortedecho on 2007-10-15
I require help too.

I need to access Windows PCs, but everytime I go to remote control via FF in Ubuntu, I'm told I need the plugin.

Fine.

So, FF can't install the plugin and I choose manual. I've tried both the BIN and RPM method following the websites instructions.

Bin - didn't work.

RPM - hit me with a bunch of dependencies. What use is an "installation" file if it has "dependencies". Surely they should come as part of the set up file?? I wouldn't buy a car with no engine!!!!!

Can anybody help? Is there a way I can get the Java pluign working in FF so that I can use LMI?

Thanks

---

### Post by reacocard on 2007-10-15
> **distortedecho said:**
> I require help too.

I need to access Windows PCs, but everytime I go to remote control via FF in Ubuntu, I'm told I need the plugin.

Fine.

So, FF can't install the plugin and I choose manual. I've tried both the BIN and RPM method following the websites instructions.

Bin - didn't work.

RPM - hit me with a bunch of dependencies. What use is an "installation" file if it has "dependencies". Surely they should come as part of the set up file?? I wouldn't buy a car with no engine!!!!!

Can anybody help? Is there a way I can get the Java pluign working in FF so that I can use LMI?

Thanks

sudo apt-get install sun-java6-plugin

---

### Post by baldychap on 2007-10-15
Yes, logmein is for windows only :( however it's big advantage is that all you need to control the remote PC is a browser and logmein works through corporate firewalls, which like my company's, prohibit the use of vnc. I get round this by using logmein to connect to an old windows machine and then VNC my ubuntu machine from that.

messy, but it works!

---

### Post by distortedecho on 2007-10-16
> **reacocard said:**
> sudo apt-get install sun-java6-plugin

Thanks, I will try this.

Does anyone know why an RPM "installation" wouldn't come with all the necessary required files?

---

### Post by derekr44 on 2007-10-16
[Hamachi](http://hamachi.cc)

It's basically owned by LogMeIn and has a similar functionality.  And it has a Linux client :)

---

### Post by reacocard on 2007-10-16
> **distortedecho said:**
> Thanks, I will try this.

Does anyone know why an RPM "installation" wouldn't come with all the necessary required files?

Two reasons:

1) RPMs are NOT native to ubuntu and should not be used on ubuntu (use deb files instead)

2) dependencies are how packaging is done in linux. This is why we have package managers like apt, to take care of the nasty bits of tracking down all the needed parts for us.

---

### Post by distortedecho on 2007-10-16
OK, so I have run the apt-get for sun java, and all was well and good. FF didn't cry for a plugin :)

However, when I try to Remote Control, a message appears that my desktop will appear shortly, then it changes to "An Error Occured".

Can anybody advise further please? 

Thanks

And thank you for your answer reacocard :)

---

### Post by seecoolguy on 2007-10-22
> **waldorf said:**
> I have used it without any trouble if I am using a linux machine to access a windows machine. You access the windows machine via a web browser so it doesn't matter if you are using linux, windows, BSD or Mac

This is the portion that I am having trouble with, I am on Ubuntu (64) 7.10 and want to access a windows machine, the Java seems to load but just hangs, then Firefox just hangs.  I'm sure I am doing something wrong but I don't know what.

---

### Post by snowlad on 2007-11-06
Appears to be a number of questions floating here but my simple answer to one of them: Accessing my Windows machines at home from my Laptop running Ubuntu is:

1] Install WINE
2] Download a portable version of Firefox for Windows
3] Access as before using Firefox for Windows in WINE

For a new convert [1 week in] this was the most pleasing/familiar solution. Worked better than the java solution for me anyway...

---

### Post by gali98 on 2007-11-24
OKay here's a quetsion for you... I have a linux machine at home (gusty) and would like to be able to access it over the internet on a windows machine much the same way logmein.com does. Is there anyway I can does this? I don't really care how, I just want to do it somehow... Thanks,
Kory

---

### Post by reacocard on 2007-11-24
> **gali98 said:**
> OKay here's a quetsion for you... I have a linux machine at home (gusty) and would like to be able to access it over the internet on a windows machine much the same way logmein.com does. Is there anyway I can does this? I don't really care how, I just want to do it somehow... Thanks,
Kory

If you have a public IP with open ports VNC works great, otherwise idk.

---

### Post by Strompf on 2007-12-01
Hi folks, 

Nice to hear from you!

I have used VNC and LogMeIn extensively, over the last couple of years; I provide computer support on-site for business and people.

What I like about LogMeIn, is that you don't have to configure any firewalls, like adding NAT-entries. The LogMeIn-client which resides on the users computer, periodically 'pings' to the LogMeIn-server over HTTP. So, the LogMeIn-server knows always at what IP-address the client is available, and there is always a path through firewalls to this client (maybe that's called firewall punching or something like that).

As far as I am concerned, the free version of VNC (I don't know any other version) doesn't have any of this neat firewall-punching technics. I found it unpractical to configure VNC inless there is a really important reason for doing so. To make things worse: When the user uses DHCP, as most networks do, setting up VNC really becomes a nightmare. With some smart routers, you can set up a path to a computers name or MAC-address, rather than its IP-address. Or otherwise, you have to assign the specific computer a  static IP-address, which is often not an option, or use some esoteric tricks that I do not want to know about. 

So yeah, I would love to learn if LogMeIn or an equivalant is available under Linux!

Regards,
Jeroen Strompf.

---

### Post by dministrator on 2007-12-01
As of this writing, logmein.com site isn't loading for me. Does anyone else have the same problem? [www.logmein.com](www.logmein.com) gets redirected to [https://secure.logmein.com](https://secure.logmein.com) and all I see is "The Connection Was Reset" page. No part of logmein site is accessible for sometime now. Java Runtime is successfully working in this computer.

I'm using Firefox on ThinkGOS. What am I missing?

Thank you.

---

### Post by cotc2001 on 2007-12-02
I seem to be connecting to logmein no problem so  don't think there is a issue with the server.

My problem is that with logmein the screen drawing is incredibly slow almost as if it's a jpg and it's just loading a screenshot rather than actual live remote desktop.

---

### Post by bem202 on 2007-12-03
Here is a crazy idea. 

I have seen programs for the palm treo which allow you to remotely turn off you palm via a text message i.e. you lode your palm, you text yourself a special number series, it recognizes the number series as a kill command, and locks itself tight. 

What if you could set your computer so that when you email yourself a certain code it email back your current ip address which would allow you to vnc into your computer. This being the problem with ip addresses changing unexpectedly. 

I have no clue how to make this happen.

 The only other thing I could think of is you set a macro that will pull up your ip address and email it to yourself a couple times a day. The only problem with that is that you would be waiting until the next email to find the right ip address,

I think I could get the macro idea to work,

---

### Post by bem202 on 2007-12-03
Here is a crazy idea. 

I have seen programs for the palm treo which allow you to remotely turn off you palm via a text message i.e. you lose your palm, you text yourself a special number series, it recognizes the number series as a kill command, and locks itself tight. 

What if you could set your computer so that when you email yourself a certain code it emails back your current ip address which would allow you to vnc into your computer. This being the problem with ip addresses changing unexpectedly. 

Oh yeah, I have no clue how to make this happen.

 The only other thing I could think of is you set a macro that will pull up your ip address and periodically email it to yourself a couple times a day. You check your email and bam right ip address. The only problem with that is that you would be waiting until the next email to find the right ip address,

I think I could get the macro idea to work,

---

### Post by macogw on 2007-12-04
Just found this: [http://www.bomgar.com/linux/linuxquestions.htm](http://www.bomgar.com/linux/linuxquestions.htm)
It's only been fully tested/certified for the tech being on Windows or SuSE, but they said they've used it on other Linux distros and had no trouble.  The person being helped can be on Ubuntu, Windows, Mac, SuSE, or a few other distros officially, but realistically more distros will work too.

---

### Post by augustosamame on 2007-12-05
I have been going crazy with the same issue for days. I just couldn't open the [www.logmein.com](www.logmein.com) page (or secure.logmein.com for that matter). I only got a "Connection Reset" error.

I found the answer, of all places, on a MAC Safari forum.

[http://discussions.apple.com/thread.jspa?messageID=6017681](http://discussions.apple.com/thread.jspa?messageID=6017681)

The problem seems to be Gutsy's default MTU network setting, which is 1500. You will have to change this to 1472, or you won't be able to access the secure logmein page. The MTU value determines the max packet size in TCP/IP networks.

The simplest (and temporary until the next reboot) way to change this value is to enter the following command in terminal (this assumes you use eth0 to connect to the Internet, otherwise edit accordingly)

"sudo ifconfig eth0 mtu 1472"

If you can access the logmein page after changing this setting, then you can attempt (it's a bit complex depending on user/configuration) to make the change permanent.

This method worked for me:

"sudo gedit /etc/network/interfaces"

add the following line to the eth0 configuration info

"MTU 1472"

reboot or restart network services using

"sudo /etc/init.d/networking restart"


I use a static IP address. I have heard of this simple method not working when using DHCP so you could do some research here

[http://ubuntuforums.org/showthread.php?t=3985&highlight=mtu+size](http://ubuntuforums.org/showthread.php?t=3985&highlight=mtu+size)

to see which method will work for you.

Hope this helps.

---

### Post by dministrator on 2007-12-12
augustosamame>>  Holy (snip) dude, you hit the bull's eye. Thank you and you are awesome.

 How on earth did you stumble on this solution?

---

### Post by dgrafix on 2007-12-18
VNC is not secure unless its via SSH.

I too am looking for a middleman type of connection like logmein that uses https .

The problem ive got using VNC over SSH is that at work im behind a proxy server and cannot create the ssh tunnel. (and there absoulutely no way im using vnc without it. Anyway prob wouldnt work either) 

All my collegues use logmein and im constantly getting the "nana na na na" because they can all access their XP pcs at lunchtime :(

There must be some kind of man in the middle https control system available surely.


PS: if you have a modern router, use [www.dyndns.org](www.dyndns.org) for your dynamic ip address problems ;)
Get this set up correctly and you will allways be 
"yourname.dyndns.com" instead of a forever changing IP

---

### Post by jnorth on 2008-01-07
Rather than VNC, how about NX/FreeNX?  We still need an automated solution to dynamic IP tracking and reverse HTTP/S connections to avoid firewall changes, but in my experience, NX is waaay faster and more stable than VNC.  I can sit on a 56k modem and not really tell that I'm not at my console - and on a 3M cable pipe, I can almost watch streaming video via a browser on the remote computer without too much 'jerkiness'.

Still doesn't help with the other issues though.

---

### Post by dgrafix on 2008-01-09
Sounds cool,

Do you have any links & howtos ?

---

### Post by daflame on 2008-01-10
> **dgrafix said:**
> Sounds cool,

Do you have any links & howtos ?

Here is a good place to get started with FreeNX:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

You may also want to look at NoMachine's website [www.nomachine.com](www.nomachine.com) for the web companion to help with connections using a web site.  It requires more setup, but it's worth it.

Finally, unless you use FTP (you should use SFTP anyways) you can use port 21 on your firewall and redirect it to port 22 to the machine you want inside.  On the other hand, if your router doesn't support that feature (sadly some are removing it) you can change the SSH port on your Ubuntu machine to 21 as most employers do not block this port.  As a last resort you may have to forfeit the web interface and use port 80 for SSH.

On the side of hamachi, I have successfully been able to get it to work, but you need to make hard links for the ssl libraries, because the libraries it looks for are older than the ones supplied with Gutsy.  I have made the hard links and they work just fine.  So it is definitely possible to send your request through hamachi if you want to.  However, for speed sake I would recommend using the port 21 approach if you can, since no one should use FTP anymore IMHO.

---

### Post by forrestcupp on 2008-01-10
Oh, I thought you meant [Lo mein](http://en.wikipedia.org/wiki/Lo_mein), that delicious Chinese treat.  It's compatible with Linux *and* Windows.

---

### Post by klange on 2008-01-10
I don't know why this topic is still continuing or at the vary least hasn't becoming a recurring topic, as we have this wonderful little tool called VNC.
VNC is portable to anything, and there are tons of options: open source, free, commercial. I'm actually about to go port the opensource version of RealVNC to my ARMv4t processor so I can use it on Angstrom...

---

### Post by dgrafix on 2008-01-12
Actually no, VNC is horrible compared to modern remotes like nomachine and logmein, even windows RDC is nicer to use!  VNC seems slow & laggy (even on a 100Mbit Lan!), has no decent security (without a separate open ssh tunnel), has 2 mouse pointers, no scaling (ar least not realVNC client anyway), cannot transport sound (although i dont really care about that) etc. etc.

When using SSH+VNC through a corporate firewall that only supports port 80 seems impossible (could be wrong there but that is the root of all my probs as i sont want my ssh server set to  80) 


Need i go on?

I think the thread should continue until someone has the bright idea of a secure browser based logmein type service for linux. Even if it uses good old VNC i dont care as long as i can bust out of my companies proxy through https, i can access my pc and its secure -I will be happy

---

### Post by Modie101 on 2008-01-16
You can set up a script that will check your IP address every Hour (interval is up to you). If it detects that your router IP has changed then it will automatically send you a notification text message to your cell, pager or email. 
I have set this up using mailx (command line email) and Lynx (text based Web page viewer). 

The script uses Lynx to check a webpage that displays your router's IP address. It grabs it and compares it to what it thinks is the "current" IP address if its different the New IPA becomes the current IPA and then it will mail out a text message to your email, cell or whatever.

I used to run it every hour. I found that my IP would only change if I rebooted after downtime.

---

### Post by jseiser on 2008-01-16
Can someone create a walkthrough on this topic?  I  have posted this same question months ago, and got some answers but nothing complete enough for me to get it to work.

I need to know how to set up a static IP from text files, How to open up the port in iptables, how to open it on a router,  then i need a program to route my IP to a website? a script placed in cron.hourly (?) that checks the ip with the program and then emails it to me, and then on the other end i need to know how to set up the program ,  to do the actually logging in.  Like at work here, I have linux and windows,  it would be awesome if someone would give a how to for both.  one from a linux to linux perspective, and the other from a windows to linux perpective.  I know thats asking a ********, but i didnt know if maybe im making this all to hard.

---

### Post by dgrafix on 2008-01-18
> You can set up a script that will check your IP address every Hour (interval is up to you). If it detects that your router IP has changed then it will automatically send you a notification text message to your cell, pager or email.Or you can use [www.dyndns.org](www.dyndns.org) (its free) so you always become "yourname.dyndns.org" rather than having to find out your current IP from emails. 

The way it works is you tell your router (under dynamic dns settings) to send the IP details to the 3rd party which then become resolved as a subdomain name rather than an IP address. 
**Note: make sure you use a DIFFERENT password for this from your router, ssh & windows login! ** This is because your router's IP broadcast to dyndns.org is unenrypted. This isnt a problem as 
long as you use a separate password. This way, even if a hacker picks up the IP broadcast from the router, the password for dyndns is useless for getting into your PC.

---

### Post by jobsonandrew on 2008-01-18
I wrote a Java program that checks your IP every 15 mins and emails you if it has changed.. it was my finest programming hour, but now it seems a little obsolete (not to mention it is a program thats designed to run all day in the background and its Java)

I'd be interested to know of a logmein equivalent for Linux too, as my workplace seems to block outgoing VNC traffic (and yes I know about port forwarding and have tried many different ports and configurations) I can still access my FTP server tho, so thats cool

---

### Post by itreliant on 2008-01-21
> **waldorf said:**
> Actually, logmein is free, but it is limited to accessing windows machines. As far as I know it does not support linux.

VNC does seem like the way to go for linux accessing linux, and I your suggestions for how to make it work are greatly appreciated - thanks!



actually you can install logmein free on a mac and / or windows box.  logmein uses java as an alternative - 

i'm not a linux guy (just installed ubuntu on my dell 700m and it's amazing for the first time

logmein is perfect for managing your windows and or mac machines remotely from your linux pc - 

i'm an it consultant - and i plan to use linux for now as as my primary pc - but i do need to manks,age windows environment so if anyone has any suggestions please feel free to send them my way.

Thanks!

---

### Post by ergosteur on 2008-01-21
> **forrestcupp said:**
> Oh, I thought you meant [Lo mein](http://en.wikipedia.org/wiki/Lo_mein), that delicious Chinese treat.  It's compatible with Linux *and* Windows.

Lo mein would be very good. I think it's even Mac compatible.

So as of now, there's no way to access a Linux/Ubuntu box that can only make outgoing connections? At university, I'm behind a crazy firewall/router that even breaks Hamachi (free, the trial of the paid version works). The only thing that works AFAIK is Logmein.

I'm currently using WinXP in virtualbox with logmein, then VNC from there to the linux host.

---

### Post by dgrafix on 2008-01-23
Unfortunately "Remote access" descriptor has now been added to the worldwide list of corporate no-nos. (this is nothing to do with the company, its whoever makes the filter)

:(
:(
:(

---

### Post by lespaul_rentals on 2008-01-23
> **bem202 said:**
> Here is a crazy idea. 

I have seen programs for the palm treo which allow you to remotely turn off you palm via a text message i.e. you lose your palm, you text yourself a special number series, it recognizes the number series as a kill command, and locks itself tight. 

What if you could set your computer so that when you email yourself a certain code it emails back your current ip address which would allow you to vnc into your computer. This being the problem with ip addresses changing unexpectedly. 

Oh yeah, I have no clue how to make this happen.

 The only other thing I could think of is you set a macro that will pull up your ip address and periodically email it to yourself a couple times a day. You check your email and bam right ip address. The only problem with that is that you would be waiting until the next email to find the right ip address,

I think I could get the macro idea to work,

Or just use DynDNS.org?  Although I do like your idea, it's fun to think about.  :)

---

### Post by magicfab on 2008-01-30
I've found out a much "simpler" way of accessing  a remote computer that is behind a firewall. Initiate a "Reverse SSH tunnel" on that computer. It's particularly easy in Ubuntu, here is one of many links that come up in Google:
[http://articles.techrepublic.com.com/5100-10879-5779944.html?tag=nl.e011](http://articles.techrepublic.com.com/5100-10879-5779944.html?tag=nl.e011)

My main complaint about VNC is it's dogslow compared to logmein or nomachine, Even fine tuning for less colors, compression, etc. does not help much but in contrast it is 100% free and you actually know what is happening and it is not provider dependent like logmein.

I also doubt VNC will ever close shop :)

---

### Post by oldsmobile_mike on 2008-02-17
Hi guys!

Saw a couple posts in this thread about people having problems using logmein and Firefox.  Just wanted to chime in that it works great using Opera 9.50 beta 1 (I've always hated Firefox) without any errors or weird configuration settings, so you might want to give that browser a try.  I can even use it to play games... Hooray - finally can play Conquer Online "under Linux", haha!  ;-)

~Mike

---

### Post by Kleinpetri on 2008-03-10
> **Modie101 said:**
> You can set up a script that will check your IP address every Hour (interval is up to you). If it detects that your router IP has changed then it will automatically send you a notification text message to your cell, pager or email. 
I have set this up using mailx (command line email) and Lynx (text based Web page viewer). 

The script uses Lynx to check a webpage that displays your router's IP address. It grabs it and compares it to what it thinks is the "current" IP address if its different the New IPA becomes the current IPA and then it will mail out a text message to your email, cell or whatever.

I used to run it every hour. I found that my IP would only change if I rebooted after downtime.

Hi Modie101,

could you please provide this script for me/us? :)

While DynDNS is quite a nice service, which I use without problems most of the time, they actually do have problems in updating the IP´s via API. In consequence, my server is not reachable since two days now. 

=> [http://www.heise.de/newsticker/meldung/104794](http://www.heise.de/newsticker/meldung/104794)
=> [http://www.dyndns.com/news/status/](http://www.dyndns.com/news/status/)


Although DynDNS report the problem to be solved, a script that permanently emails any changes of IP to a defined email-address would be great enhancement in such situations... In this case you could simply update the IP manually.

Thanks in advance und regards,
Petri

---

### Post by hurinth on 2008-03-26
[COLOR="Olive"]**> A complete solution for remote [COLOR="Red"][B]access to your Unix workstation**[/COLOR]. It allows 2 concurrent users to connect no matter what their location is, and share the desktop. NX Free Edition is incredibly easy to install and run, leverages the competence and quality of the company that makes NX and, most importantly, is free forever

"No machine" seems to be the equivalent for linux. They even posted cool pics of a vista machine logged to a fedora wkstation. Just a couple of questions coming to my mind:

-How difficult could it be to route the client out from an intranet out to internet and into the linux wkstation?

-How serious is this company nomachine.com??

I will post my own answer to the first question but ne body with more xperience please comment :)[/B][/COLOR]

---

### Post by reacocard on 2008-03-26
> **hurinth said:**
> [COLOR="Olive"][B]

"No machine" seems to be the equivalent for linux. They even posted cool pics of a vista machine logged to a fedora wkstation. Just a couple of questions coming to my mind:

-How difficult could it be to route the client out from an intranet out to internet and into the linux wkstation?

-How serious is this company nomachine.com??

I will post my own answer to the first question but ne body with more xperience please comment :)[/B][/COLOR]

NX == no machine

I use it myself, it works excellently, much faster than VNC.  As for sending it out to the internet, it works over SSH so I assume if you can SSH to it over the net then NX will work.

---

### Post by friartuck on 2008-04-14
@ waldorf

Can you please tell me witch you where using, my boss orderd me to look in to this subject, he wants to switch to open enterprice, building a test environ down here you could save me a lot of time.

Regards,

ruben
Cannes, France

---

### Post by life4himsq on 2008-05-07
Could you use a script on the remote machine to check a personal website. Then you could log into the website and it would get your local machine IP and the script could retrieve the IP and then reverse ssh into your local machine and let you vnc or nx to the remote machine? This sounds like what logmein is doing.

---

### Post by jasunto on 2008-05-20
i used it on my mac before also

---

### Post by jnorth on 2008-05-22
> **life4himsq said:**
> Could you use a script on the remote machine to check a personal website. Then you could log into the website and it would get your local machine IP and the script could retrieve the IP and then reverse ssh into your local machine and let you vnc or nx to the remote machine? This sounds like what logmein is doing.

That's what I've been trying to get going for me, as well as maybe developing an easier way to do it for others.  I'm no programmer but my resources are available.

I have a remote server set up at a colo facility that I run some sites off of.  I set up a virtual server with ssh listening on port 9022, and ports 10000-10199 wide open for incoming connections (no service running on them). Let's call this host "middleman".
Next, I have a script on my laptop (let's call this host "endpoint" by the way) that tries to keep a  reverse tunnel open to the ssh server on port 9022 on "middleman".  I have it hardcoded for now to forward port 10074 on "middleman" to port 22 on "endpoint".
Finally, I have the NX client loaded on my work desktop and set up to connect to port 10074 on "middleman", and viola, I get my desktop on "endpoint".

So - how to automate this and make it available for others to use, as well as integrate this into a web-based client?  I have a mysql and apache server available if anyone has ideas - I can code some stuff and am willing to give others access.  If we could write a script for the "endpoint" users to put in their init.d as a service, and automate code to "connect-the-dots" on the "middleman" server, we could have it acting like logmein does.  

Now the downside to this.  The way I set it up above requires all the traffic to pass through the "middleman".  Is there some way to have the "middleman" only negotiate a direct connection between the client and endpoint, and NOT pass all the gui traffic through?  I can't imagine that logmein does this, somehow they have to be setting up a direct connection.  The bandwidth bill would be huge otherwise.

A sidenote also.  I notice that shadow sessions are much slower than regular unix kde or gnome sessions.  Anybody know why or how to fix or improve this?  It slows down almost to VNC speed when shadowing for me, but a gnome sessions just blaze along like you were at the console.

---

### Post by Mazza558 on 2008-05-22
Is there any way at all to access a Linux machine from Windows through the Remote Desktop Connection?

---

### Post by jnorth on 2008-05-22
> **Mazza558 said:**
> Is there any way at all to access a Linux machine from Windows through the Remote Desktop Connection?

Actually yeah - just found this: [http://xrdp.sourceforge.net/]("http://xrdp.sourceforge.net/").  I haven't tried it though.

---

### Post by life4himsq on 2008-05-24
One way some might be able to do this is hamachi, it works through most home NATs just fine. It is owned by logmein now but before they bought it I tried it were I work and it would not connect through the firewall. I know I can ssh from work to home so if I could get my work PC to connect to a "middleman" web server and check if I have been there to ask for a connection and if I have then ssh to the IP that last connected to the "middleman". Then I could remote control my work PC, as long as I was not behind another high firewall like the one at work. I will try hamachi again and see if it has been changed since owned by logmein.

---

### Post by ubuntism on 2008-05-28
logmein provides what is basically a vnc service for free, but they do more than that; the vnc connects out to their server and allows you to vnc past any form of network protection, so instead of vncing to a machine that's port forwarded behind a router; you are connecting and logging into logmein, selecting the computer you want from a list of online computers that oyu have installed logmein on under your name.  then they allow you to initiate a chat with a user if they've been active recently, or you can just remote control the pc. in the paid (pro) version you can use the print dialog to print document from the remote computer on a local printer. you can do the same for audio, play with a remote audio player and hear locally.  you're able to drag and drop files between logmein and the local computer, and even start "mini meetings" where you invite other people to connect to your logmein and use it as a whiteboard/presentation.  they're working on a mac version of the vnc server right now (i think it's in released beta) and the logmein client actually works on most operating systems including linux, but the server is only available for windows and mac(beta)... (they do have a similarish service that is also available for linux, but it is only trial/paid and is billed per a few different periods, two being monthly and yearly (1 month 1-5 licenses 4.95ea, 1 year 1-5 licenses 3.25ea) and is a instant, zero configuration VPN setup, which allows you to manage multiple vpns and join/part/delete them at will per computer basis; i could see this being very convenient in a corporate environment, but i do with it had also been offered for free.

---

### Post by adityakavoor on 2008-05-28
ghamachi is there

---

### Post by CyberAngel on 2008-06-16
I just found a new one that it is working exactly the same way like logmein but guess...
It has a Linux server!!!!! :D

The program is ntrconnect.
it has a free version without all the features available but the remote desktop is there :)

Just install it (It has a graphical installation) and then run
```
sudo /usr/local/NTR/NTRconnect/NTRservice
```

But the news are not just good :(
There is no linux client available! How stupid can this be?!?!??
Anyway I tested that using a windows virtual machine as a client and it worked perfectly :)

I am in search of a way to control my linux remotely using a linux machine now..

---

### Post by sdmitriy on 2008-06-23
> **reacocard said:**
> 
According to its site, it has 256-bit SSL encryption, but only in the paid version.

I've been using LogMeIn for some time (free) and as far as I know all of their products (including free) are secured with 256-bit SSL.

Correct me if I'm wrong.

---

### Post by dtl on 2008-07-09
< Is there anyway you can cross match OS's with this, whether you use logmein or VNC? 

aka - Would EITHER option work with linux home pc/windows school pc?>

Hi , 
I'm not sure if this answers your question, Roasted ,but I have been using LogMeIn on my Linux PC  and it has no problem controlling  Windows' machines. As long as u have the right Java ap. installed.

Hope it helps.
J.

---

### Post by keiichidono on 2008-07-09
I think you could use TightVNC to acess Windows using Linux...

---

### Post by damis648 on 2008-07-09
I know System>Administration>Remote Desktop Lets you connect on your lan... but is there a way to configure it to connect over the internet (assuming you know your IP before it changes dynamically) and use a web browser to access the server?

---

### Post by kriemer on 2008-07-10
The real attraction I have to LMI is that the remote computer can be of any system running either IE or FF.  There is no need to install any software so hotel computers are a perfect door to my computer at home.

My solution is by no means perfect.  I normally run Ubuntu OS storing data on NTFS formatted drives.  When I am travel I boot into WXP with LMI.  In this way I can access my files from any computer anywhere in the world should the need arise.

As I said, by no means a perfect solution.  I would like nothing better than to delete my WXP partition.

k

---

### Post by sicofante on 2008-07-23
[http://www.teamviewer.com](http://www.teamviewer.com)

I've read reports that it will run under Wine.

I haven't tried it myself yet.

---

### Post by CyberAngel on 2008-07-24
> **sicofante said:**
> [http://www.teamviewer.com](http://www.teamviewer.com)

I've read reports that it will run under Wine.

I haven't tried it myself yet.

It`s true...
Running perfectly under wine (just the client) :)

---

### Post by Xelgand on 2008-08-26
Ok, i just read the entire topic and this should be a resume:
In all cases these solutions have no port or dynamic ip problems. 

Q: can i access a Windows machine from linux/windows by browser and without installing anything?

A. yes, just install logmein server in your windows machine


Q: does logmein has a linux server version?

Q: right now, it doesn't


Q: how can i access my linux box in a secure form, without port mapping or dynamic ip issues?

A: you can do it in several ways:

1) install hamachi in both machines, and run any remote desktop software you like (any vnc like) using the hamachi ip of the remote machine

**(these seems to be alternatives to logmein, go ahead and try them)**

2) **try** NoMachineNX [http://www.nomachine.com/](http://www.nomachine.com/)

3) **try** Bomgart [http://www.bomgar.com/linux/](http://www.bomgar.com/linux/)

3) **try** NTRconnect [http://www.ntrconnect.com/](http://www.ntrconnect.com/)


Note: there is gHamachi (a GUI for hamachi in linux)

---

### Post by hdd3md on 2008-08-26
I read through the thread.

I have a different, yet similar, question.

I need to be able to access Ubuntu boxes using terminal services to RDP into different sessions on a Windows 2003 server.  I need to 'logmein' to the user's linux box WHILE a user is running a terminal services client FROM OUTSIDE the network in case I need to provide technical assistance or guidance or see what they are doing.

Logmein does this quite elegantly as you access the windows computer logged into a TS session and you can walk someone through a process or issue with them while they are at their screen, and you at yours, albeit theirs, through logmein.

I do not want to access a different UBUNTU session, but a session in which someone is already logged in, to provide assistance, etc.

Logmein does just that.

Is there a linux equivalent?  or can I VNC or g-hamachi to the particular user session on the linux box?

Thanks

---

### Post by CyberAngel on 2008-08-26
> **hdd3md said:**
> I read through the thread.

I have a different, yet similar, question.

I need to be able to access Ubuntu boxes using terminal services to RDP into different sessions on a Windows 2003 server.  I need to 'logmein' to the user's linux box WHILE a user is running a terminal services client FROM OUTSIDE the network in case I need to provide technical assistance or guidance or see what they are doing.

Logmein does this quite elegantly as you access the windows computer logged into a TS session and you can walk someone through a process or issue with them while they are at their screen, and you at yours, albeit theirs, through logmein.

I do not want to access a different UBUNTU session, but a session in which someone is already logged in, to provide assistance, etc.

Logmein does just that.

Is there a linux equivalent?  or can I VNC or g-hamachi to the particular user session on the linux box?

Thanks

Check my post in the previous page (page 8) in this thread about ntrconnect. I think this is what you`re searching for :)
Unfortunately when I tried that program there was no Linux client :|
Just a Linux/mac/windows server.

---

### Post by Xelgand on 2008-08-27
> **hdd3md said:**
> 
Logmein does just that.

Is there a linux equivalent?  or can I VNC or g-hamachi to the particular user session on the linux box?

Thanks

try the alternatives :)
(look one post above yours)

---

### Post by jethro10 on 2008-08-27
> **Xelgand said:**
> Ok, i just read the entire topic and this should be a resume:
In all cases these solutions have no port or dynamic ip problems. 

Q: can i access a Windows machine from linux/windows by browser and without installing anything?

A. yes, just install logmein server in your windows machine


Q: does logmein has a linux server version?

Q: right now, it doesn't


Q: how can i access my linux box in a secure form, without port mapping or dynamic ip issues?

A: you can do it in several ways:

1) install hamachi in both machines, and run any remote desktop software you like (any vnc like) using the hamachi ip of the remote machine

**(these seems to be alternatives to logmein, go ahead and try them)**

2) **try** NoMachineNX [http://www.nomachine.com/](http://www.nomachine.com/)

3) **try** Bomgart [http://www.bomgar.com/linux/](http://www.bomgar.com/linux/)

3) **try** NTRconnect [http://www.ntrconnect.com/](http://www.ntrconnect.com/)


Note: there is gHamachi (a GUI for hamachi in linux)

At work, we finally gave up and bought a single user Bomgar box for $2000.

Clients and servers for linux/windows/apple
Works fine and has been a good buy.

J

---

### Post by rkn5555 on 2008-09-03
q

---

### Post by DaveTap on 2008-10-08
For doing remote assistance try: [https://launchpad.net/remote-help-assistant]("https://launchpad.net/remote-help-assistant") 
It will require opening a port at one end (either one) but is an easy novice download, install, and set up with minimal guidance.:)
Unfortunately both must run Linux and have the program installed.

---

### Post by david_lynch on 2008-10-09
> **Roasted said:**
> I just found out about logmein.com the other day at school. Some other kids use it, however they ALL use windows at home. ](*,) 

Is there anyway you can cross match OS's with this, whether you use logmein or VNC? 

aka - Would EITHER option work with linux home pc/windows school pc?no idea about logmein.com, but vnc can be used between mac and unix, unix and peecee, peecee and mac, or any combination.

---

### Post by BiL0 on 2008-11-07
Logmein for linux is out

[https://secure.logmein.com/products/hamachi/list.asp](https://secure.logmein.com/products/hamachi/list.asp)
Just make sure on the CPU you're using, however there is one even for old CPUs like P2 or old K6 machines

BiL0

PS: try it its free :o)

---

### Post by beercz on 2008-11-07
Has anyone tried this yet.  I haven't because I am @ work atm.

Just curious as to how good, or otherwise, logmein for linux is.

Thanks in advance.

---

### Post by sicofante on 2008-11-07
This is not Logmein for Linux, it's Hamachi which is a different thing and has been out there for ages.

---

### Post by flamarro on 2008-11-18
ok,
i too am a guy who likes logmein, just for the reason that i work in a company that works with XP Pro and dont let me install anything on my computer and has that policy of blocked sites by content., what i mean is that i can let my home computer turned on and with logmein activated, and in my work i can login at my home computer just by entering in a webpage without installing anything but a plugin....that i can do....
If i could install VNC or something alike i was fine, but i cant, I've tried....
This all thing works in a windows environment, wich is sad, because everything i want to connect to home i must be in XP.
So, my question is, in this conditions, is there something like this or some-other way to connect to my computer at home which is in UBUNTU and with my work PC in XP?
Sorry about my english, and i hope that i could explain myself.

---

### Post by reacocard on 2008-11-18
> **flamarro said:**
> ok,
i too am a guy who likes logmein, just for the reason that i work in a company that works with XP Pro and dont let me install anything on my computer and has that policy of blocked sites by content., what i mean is that i can let my home computer turned on and with logmein activated, and in my work i can login at my home computer just by entering in a webpage without installing anything but a plugin....that i can do....
If i could install VNC or something alike i was fine, but i cant, I've tried....
This all thing works in a windows environment, wich is sad, because everything i want to connect to home i must be in XP.
So, my question is, in this conditions, is there something like this or some-other way to connect to my computer at home which is in UBUNTU and with my work PC in XP?
Sorry about my english, and i hope that i could explain myself.

There's a Java applet client for VNC I think. Alternatively, what's their definition of 'install'? If it doesn't include just dropping an exe on your desktop (or whereever), there are VNC clients that don't need to be installed onto C:. You can even run them off a flash drive so it'd never even be on your work computer's HD.

(your english is pretty good btw, I had no trouble understanding it)

---

### Post by somethings90 on 2008-12-02
How do you install ntrconnnect?  I could not find any guide on the website that explained how to install it on linux.

---

### Post by CyberAngel on 2008-12-04
> **somethings90 said:**
> How do you install ntrconnnect?  I could not find any guide on the website that explained how to install it on linux.


1) Go to the NTRconnect site.

2) Create a free account.

3) Login to that account.

4) Go to the link "Control Panel -> Computer List" and press the link "Install a new computer"
This will download the Linux client to your computer...

5) Unzip it and set it up. It has a graphical installation...
During the installation it will ask you for your username and password (use the ones you used when you were creating the account in the web page) and when this will finish just run the command

```
sudo /etc/init.d/NTRConnectScript start
```

6) Refresh the status of the web page and you`ll see you computer.
Press on it and you can have remote access.

What I hate at the moment is that there is no linux client....

---

### Post by Promethalus on 2008-12-12
I`m like, really new to Ubuntu, and got no futher experience with linux what so ever, so I`m running into allot of problems with installing VNC, or making NTR auto-run.
Some hint would really come of use.

yours, ( temp. ) ubuntu noob

---

### Post by CyberAngel on 2008-12-12
Where exactly are you stuck with NTRconnect?

Check the following link for how to setup x11vnc and autostart it in a kde session.
[http://ubuntuforums.org/showthread.php?t=196572](http://ubuntuforums.org/showthread.php?t=196572)
It is a HOWTO I wrote two years ago :)

If you run into further trouble feel free to ask!

---

### Post by dinarcon on 2008-12-13
omg, I finally got it... not the way I'd like it though, but at least it's working...

it's not an open source solution, just following oldsmobile_mike's advice... after signing up at LogMeIn page, and installed the "server" on a computer running Vista, I used Opera for remote controlling... In fact, I'm post using Ubuntu while controling the other computer... for some reason Firefox never could get me connected...

in my to do list is trying opera, find a VNC solution and to figure out what hamichi is... :lolflag:

---

### Post by earlra on 2008-12-15
LogMeIn is developing client software for Linux.  They have "preview" versions available for testing on:
[https://secure.logmein.com/labs.asp?lang=en](https://secure.logmein.com/labs.asp?lang=en)

---

### Post by fluteflute on 2008-12-15
> **earlra said:**
> LogMeIn is developing client software for Linux.  They have "preview" versions available for testing on:
[https://secure.logmein.com/labs.asp?lang=en](https://secure.logmein.com/labs.asp?lang=en)
I was getting semi-exicted then! But its actually only for accessing non-linux computers from linux.

---

### Post by Promethalus on 2008-12-16
> **CyberAngel said:**
> Where exactly are you stuck with NTRconnect?

Check the following link for how to setup x11vnc and autostart it in a kde session.
[http://ubuntuforums.org/showthread.php?t=196572](http://ubuntuforums.org/showthread.php?t=196572)
It is a HOWTO I wrote two years ago :)

If you run into further trouble feel free to ask!

You say that you did this with KDE, but if I try something similair in Gnome, would it function?

---

### Post by CyberAngel on 2008-12-16
> **Promethalus said:**
> You say that you did this with KDE, but if I try something similair in Gnome, would it function?

Use the Gnome VNC server called VINO.

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html#more-15](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html#more-15)

---

### Post by malleeblue on 2008-12-17
> **CyberAngel said:**
> 

Just install (It has a graphical installation) and then run
```
sudo /usr/local/NTR/NTRconnect/NTRservice
```



I've installed NTRconnect into Ubuntu 8.10 and run the above code without any errors, but when I visit my account page at ntrconnect.com my computer is listed as offline.

Any suggestions?

---

### Post by CyberAngel on 2008-12-17
> **malleeblue said:**
> I've installed NTRconnect into Ubuntu 8.10 and run the above code without any errors, but when I visit my account page at ntrconnect.com my computer is listed as offline.

Any suggestions?

try this:

```
sudo /etc/init.d/NTRConnectScript start
```

---

### Post by malleeblue on 2008-12-17
> **CyberAngel said:**
> try this:

```
sudo /etc/init.d/NTRConnectScript start
```

No joy unfortunately. That gives me

```
sudo: /etc/init.d/NTRConnectScript: command not found
```

I checked the /etc/init.d folder and there is no file in it starting with NTR
:confused:

---

### Post by ken0062 on 2008-12-20
I have been looking into this for quite some time, the problem is In order to access a Linux machine from my place of work you need to be able to http tunnel into it as SSH will not get through the firewall, the client also needs to run on Java in a web browser as active X is also disabled and nothing can be installed without administrative privileges.
Logmein is the only app I have been able to get working for a windows box, I have just tried NTRConnect but unfortunately the client runs on active X or needs to be installed.
What I belive is needed is a combined Java httptunnel and vnc client to be setup inside a apache server on the home PC to forward to the httptunnel and vnc server also installed on it.
If anyone knows of a tutorial of how to set this up I would be most grateful.

---

### Post by Promethalus on 2008-12-23
> **CyberAngel said:**
> Use the Gnome VNC server called VINO.

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html#more-15](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html#more-15)

Ain`t working mate, got following :

root@ubuntu:/home/promethalus# vncviewer -fullscreen 192.168.2.23:0
The program 'vncviewer' can be found in the following packages:
* xvnc4viewer
* xtightvncviewer
* tightvnc-java
* vnc-java
Try: apt-get install <selected package>
bash: vncviewer: command not found


so kinda got stuck
How to avoid this error?

---

### Post by Promethalus on 2008-12-23
> **ken0062 said:**
> I have been looking into this for quite some time, the problem is In order to access a Linux machine from my place of work you need to be able to http tunnel into it as SSH will not get through the firewall, the client also needs to run on Java in a web browser as active X is also disabled and nothing can be installed without administrative privileges.
Logmein is the only app I have been able to get working for a windows box, I have just tried NTRConnect but unfortunately the client runs on active X or needs to be installed.
What I belive is needed is a combined Java httptunnel and vnc client to be setup inside a apache server on the home PC to forward to the httptunnel and vnc server also installed on it.
If anyone knows of a tutorial of how to set this up I would be most grateful.


there is a java-app for VNC, just check the synaptic package manager. It`s there, somewhere. . .

---

### Post by ken0062 on 2008-12-24
> **Promethalus said:**
> there is a java-app for VNC, just check the synaptic package manager. It`s there, somewhere. . .

The problem is that in order to get through some tight corporate firewalls you need to tunnel the vnc protocol using httptunnel, so I need a Java viewer that is capable of viewing httptunnel'd vnc.

---

### Post by Ehol on 2009-01-15
I don't know if there's someone who can help me, but after I upgraded to Intrepid, I am no more able to install NTRConnect.
It was installed, but after the upgrade was not working anymore.
So I decided to reinstall it, but it get stuck at point 3 of 5 (that is when you insert your username and password to login) and then it doesn't go on.

Does anyone had the same problem with kernel 2.6.27 ?

---

### Post by magoraf on 2009-01-18
I have a similar problem, I tried to install NTRConnect on my Ubuntu 8.10 with kernel 2.6.27-9, but on the step 4 of 5 I recieve the error message "Download Service ERROR"... has someone the same problem?

---

### Post by arthur66 on 2009-01-21
The bottomline is that neither logmein nor gotomypc kind of services can be installed on a Unix box. They are simply made only for MS. 

The VNC alternative, and other similars, are nice if you can and want to use them. But, having a corporate laptop, VNC does not work - the VNC protocol (or port) is blocked.

I also played with VNC between two Linux boxes - it is not straightforward to set it up and it was a kind of slow. 

A real shame, I find. Remote computing is increasingly used, and the Linux world does not seem to provide a modern, fully web based solution.

Also a bit strange -  if MS can do it, why can't such a solution be developed within the Linux community?

Anyway, the lack of a solution to this issue (and others) has forced me to stick with MS and run Ubuntu in a virtual machine - not optimal and not desirable.

Looking forward to future info about developments in this field.

Kind regards
Arthur66

---

### Post by Ehol on 2009-01-23
> **magoraf said:**
> I have a similar problem, I tried to install NTRConnect on my Ubuntu 8.10 with kernel 2.6.27-9, but on the step 4 of 5 I recieve the error message "Download Service ERROR"... has someone the same problem?

Today I downloaded the new setup executable and I received the same error at the same step.
Is there a way to ask for help from NTRglobal directly ?

---

### Post by fmathieu on 2009-01-23
Hello Guys,

You get this error because the Installer is looking for the folder /usr/local/NTR which doesn't exist on the machine.

Just use the command 
mkdir /usr/local/NTR

And reinstall.


We will be fixing the installer shortly.


Thanks for your feedback.

Felicien.

---

### Post by fmathieu on 2009-01-23
Also Guys,

If you need a remote access solution compatible with Linux, Mac and windows. 

We offer more complex solution called NTRSupport and NTRadmin.
You can try them for free @

[www.ntrsupport.com](www.ntrsupport.com)
[www.ntradmin.com](www.ntradmin.com)


Regards,

---

### Post by Ehol on 2009-01-23
Wow !
Big Thanks, guys.
It's quite unusual to see developers coming in to apologize for incoveniences.

Keep Up The Good Work !
Thumbs Up !

And Thank you, of course.

---

### Post by YesSir on 2009-01-28
Hi people!

Being new to Ubuntu (and Linux), but managed to install NTRconnect, by adding /usr/local/NTR. 

However, today I seem to have problems with connecting. NTRservice is up and running and I disabled firestarter, but my pc is listed as being offline... Anyone? ;)

Thanks!

---

### Post by YesSir on 2009-01-29
Update:

I still didn´t manage to connect using NTR. Today I found teamviewer also offers a **[web-based solution]("https://wa236.teamviewer.com/login.aspx?state=1")**. 

Their application however, needs to be installed **[using wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9470")**.

I will try it as soon as I get home ;)

---

### Post by CyberAngel on 2009-01-29
> **YesSir said:**
> Update:

I still didn´t manage to connect using NTR. Today I found teamviewer also offers a **[web-based solution]("https://wa236.teamviewer.com/login.aspx?state=1")**. 

Their application however, needs to be installed **[using wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9470")**.

I will try it as soon as I get home ;)

Additional Comments from the winehq appdb....

> Works excellently for remote control of other machines, but not for sharing your desktop AFAIK

I can also confirm that as I have tested it already :)

---

### Post by DarrenCT on 2009-01-29
> **DaveTap said:**
> For doing remote assistance try: [https://launchpad.net/remote-help-assistant]("https://launchpad.net/remote-help-assistant") 
It will require opening a port at one end (either one) but is an easy novice download, install, and set up with minimal guidance.:)
Unfortunately both must run Linux and have the program installed.

OMG! .. this is amazing.  I finally have something that is easy for the remote party to install (or for me to install before hand) and allow for remote assitance.  I have been switching many friends/family over to Ubuntu, and have only been able to provide assistance by means of SSH/VNC (after walking them through setting up their routers).  This takes all that hassle out of it.  

I downloaded the .deb (1.1.1) and installed on both my laptop and desktop running 8.10.  Set the remote (laptop) to "share access to this computer", then checked all 3 boxes "automatically manage firewall" "use reverse connection" "allow them to control your desktop".  

Then ensured that "Remote desktop" was enabled (System/Preferences/Remote Desktop).

Then, on the desktop (local) machine, checked both boxes "automatically manage firewall" and "use reverse connection".  

Then, typed in the IP of the laptop (remote) machine, and BAM!!
After a few questions to ensure that there was no malarky going on... I was in!!! ... quite nice! .. I've Tagged this one as a must have on any install that I do for anyone! 

Thanks very much for the tip DaveTap!!!

---

### Post by Xbehave on 2009-01-29
To go back to the VNC option, would it be possible to setup tightvnc running on your computer with an webpage and a java applet also running locally and then all you need is a webbrowser with java support?

---

### Post by YesSir on 2009-01-30
I tried the above mentioned teamviewer solution, however didn´t get it up and running yet. 

I do know TightVNC offers a web-page solution. However, the used address in the browser will be: address : port. Teamviewer, logmein, etc. use port 80 and are not blocked by company firewalls. The VNC-through-browser solution might not work, since it will use the VNC port anyway...? :confused:

---

### Post by eddielad on 2009-01-30
Hi to you all, 

Here is my first post on the Ubuntu Forums.

I wanted to add this for clarity. NTRConnect Version 2 for Linux was released in 2008 and it works as advertised.

Download the software to Linux and install it - I found I had to run it using the sudo command within a terminal to get it to install properly.  I also added the NTR directory mentioned in a previous post - not 100% sure if this was required.

#ps -ef | grep connect  

should show you that there is a running NTRConnect process. If its not there reinstall. This must be present to comunicate back to NTRConnect.com.

The next thing that had me puzzling was when I connected thru the NTRConnect website I was confronted with a message to the effect that Linux was not a supported OS. 

What this means is you can't use Linux to remotely control another machine but you can control a Linux machine remotely using a different OS (if you see what I mean). Its a shame but this is how it is.

So I switched over to a Windows PC and tried again and it all worked. 

I know its obvious but please remember that the machine you are trying to control needs to be switched on, so if it has some fancy power schemes that can shutdown network cards etc you could be heading for trouble.

Other than the above - it all works just fine. 

Additional: have just read the following. I can't verify it without using a sniffer but it may be helpful to somebody especially if your blocking certain of these ports.

more information by the NTR support 

the software use the port 80 and 1 of 21, 25, 110, 443, 11438 randomly :/ 

the port can be forced in the NTRsupport version not in NTRconnect and NTRadmin

So its not just port 80. Maybe the situation will improve in future.



regards

Eddielad

Lunch anyone :popcorn:

---

### Post by YesSir on 2009-01-30
That´s probably my case, the ports being closed... Maybe I should open the ports on my router. However, I thought NTR would be "configure-free" in this aspect ;)

Btw, hope you enjoyed your lunch :D

---

### Post by eddielad on 2009-02-01
Again just to be clear - the ports mentioned in the post I found (if they are used at all) are outbound i.e. from your internal network out to the Internet. They are certainly not inbound; my firewall is configured to ignore / block anything on ports that I am not specifically using. 

For info: check out Steve Gibson's website at [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm) and run the "Shields Up" utility if you are in any doubt about what your firewall is actually doing. Its very cool :cool:

---

### Post by YesSir on 2009-02-02
Thanks, appreciate that!

---

### Post by jad2009 on 2009-02-06
Hi

Having trouble to get my ubuntu machine online w/ntrconnect.  Shows on the website but not online.  Great help so far with the mkdir, and have done sudo /etc/init.d/NTRConnectScript start  seems to run.  but sudo /usr/local/NTR/NTRConnect/NTRservice does not run. Only thing in the NTRconnect dir is com.ntr.connect.service (an xml file).

Contacted NTRconnect, the help so far was to restart and/or reload the program, neither seemed to help.

Any ideas for a Newbie

JAD

---

### Post by argensfinest on 2009-02-22
> **Roasted said:**
> I just found out about logmein.com the other day at school. Some other kids use it, however they ALL use windows at home. ](*,) 

Is there anyway you can cross match OS's with this, whether you use logmein or VNC? 

aka - Would EITHER option work with linux home pc/windows school pc?

it does cross-platform fine, as i regularly control my windows PCs, and my dad's work PCs which also use windows, with my macbook on LogMeIn.

however, i think you can only use a linux computer to control a windows or mac computer, not the other way around.  and even then, i think it's meant more to go through firefox, so if you have KDE and use konqueror, no dice.

if anyone finds any free solutions and wants me to test, this macbook i'm on right now has OS X, ubuntu and windows 7, so i can test pretty much anything under the sun.

also, NTRconnect would be cooler if the free version wasn't limited to 2 computers.  that's one thing i love about the free version of LogMeIn, i have 5 or 6 computers on my account, and it isn't limiting me.

---

### Post by life4himsq on 2009-03-15
I found some one working on a pidgin plugin to do the logmein type thing. [http://sourceforge.net/projects/pidgin-vnc/]("http://sourceforge.net/projects/pidgin-vnc/")

---

### Post by LookTJ on 2009-03-15
[http://www.yuuguu.com/home](http://www.yuuguu.com/home) sounds like a good equivalent.

---

### Post by YesSir on 2009-03-16
I like the last two contributions. However, wouldn't these need a second person to confirm the connection (or, should I drive home and accept the incoming request and drive back to the office? ;))

Thanks people, I will give them a try..!

---

### Post by Mehall on 2009-03-16
When do you need more than a few programs? Whats wrong with ssh -Y ?

---

### Post by dragos240 on 2009-03-16
One acronym V C N

---

### Post by YesSir on 2009-03-16
The thing is, services such as logmein run on one of the few ports that is not blocked at my office (80). So allowing me to operate the machine at home. Plus, it is noob-proof and doesn't need installing vnc or ssh or configuring routers :)

---

### Post by Mehall on 2009-03-16
> **YesSir said:**
> The thing is, services such as logmein run on one of the few ports that is not blocked at my office (80). So allowing me to operate the machine at home. Plus, it is noob-proof and doesn't need installing vnc or ssh or configuring routers :)

Granted you might need to open up a port for ssh, but "sudo apt-get install openssh-server" and you have instant ssh access.

I dunno what the package name is in pacman if you're an arch user, but the point is the same.

---

### Post by YesSir on 2009-03-16
That I can manage ;) However, an SSH connection is text-based, isn´t it? So than I should use VNC over SSH? (There is a new world opening up to me)

---

### Post by Mehall on 2009-03-16
> **YesSir said:**
> That I can manage ;) However, an SSH connection is text-based, isn´t it? So than I should use VNC over SSH? (There is a new world opening up to me)

the "-Y" is x11 forwarding.

example:

ssh -Y [email]mehall@ssh.ubuntu.com[/email]

(not really, but it's an example)

then, once I'm in, I can type "firefox" and it'll come up, because it forwards the x11 to you. If you wanna do it under windows you need an app like Exceed of XMing. Xming is better. but you can only have one x11'd window at a time in it.

Oh, and just like in regular terminals, an "&" after a command lets you have the terminal still available. example:

"Firefox &" would give me firefox up, and then gimme a new prompt so I could

"irssi irc.freenode.org" and then I have irssi and firefox from one ssh session. You should look into x11 forwarding, it really comes into it's own if all you need is one or two windows/programs rather than a whole desktop.

---

### Post by YesSir on 2009-03-17
Great Mehall, never new this! Indeed, only 1 program at a time is fine for me, so I'll definitely give it a try! Thanks for the explanation.

---

### Post by Mehall on 2009-03-17
> **YesSir said:**
> Great Mehall, never new this! Indeed, only 1 program at a time is fine for me, so I'll definitely give it a try! Thanks for the explanation.

You're more than welcome, XMing is a great, lightweight program and under Linux native or under XMing, x11 forwarding is great. (watching videos can be a pain on lower bandwidth because of the encryption levels on ssh)

---

### Post by Mehall on 2009-03-17
[http://www.techworld.com.au/article/280304/logmein_linux_support_coming_year](http://www.techworld.com.au/article/280304/logmein_linux_support_coming_year)

LogMeIn working on it ^

---

### Post by YesSir on 2009-03-17
Thanks for the news. I managed to create an SSH connection (putty -> openssh), but now, at trying to open applications, I get 

"error: can't open display: localhost:10.0"

Still didn't figure this one out... :-s

---

### Post by Mehall on 2009-03-17
> **YesSir said:**
> Thanks for the news. I managed to create an SSH connection (putty -> openssh), but now, at trying to open applications, I get 

"error: can't open display: localhost:10.0"

Still didn't figure this one out... :-s

If using putty, there's a configuration section for "x11 forwarding"

You check the box, and enter the value just underneath as "localhost"

---

### Post by harrir on 2009-05-07
I have managed to get x11vnc and xtightvnc to work with and without ssh, but it sooooo much slower than LogMeIn.

Anybody know why this is? Shouldn't it be as fast as LogMeIn?

**Update**

I had one thing I hadn't tried and that has Hamachi, another product from LogMeIn which is basicly a VPN serice. Point is, it was incredibly much faster than the other things I have tried for linux. I used hamachi and thightvnc. It is actually usable compared to the other solutions I have tried. It was very easy to install and easy to use, and its crossplatform. The catch is that you have to have hamachi installed on the computer computer you are connecting from, so that kind of rules out you guys who can't install things at work, but as a remote control solution for linux it is absolutely to recomend. 
Before I began using linux i has a LogMeIn Pro user, so I hope and has very happy with it so I hope they make it avaiable for Linux too.

---

### Post by krunge on 2009-05-07
> **harrir said:**
> I have managed to get x11vnc and xtightvnc to work with and without ssh, but it sooooo much slower than LogMeIn.

Anybody know why this is? Shouldn't it be as fast as LogMeIn?


Can you quantify "sooooo much slower"?

---

### Post by harrir on 2009-05-08
> **krunge said:**
> Can you quantify "sooooo much slower"?

10 sec delay loosly counted (when opening windows and similar it took 10 sec or more, for just mouse movement the delay wasn't that much, but hey, remote controlling your machine is much more than moving your mouse) against 3 ms without ssh and 6ms with ssh on hamachi (x11vnc gave those last numbers).
 The difference has so huge that it kinda surprised me. 3ms and 6ms I can live with, actually its very good, I expect it to be a little longer when Im further away, but still usable. Those loose 10(or so) sec makes it unusable. 
Kinda bummer because it would be easier on the client side without having to use hamachi.
The ideal thing is to use the browser like LogMeIn Free and Pro, then you can do it on most any computer that have Internet.

---

### Post by golusweet on 2009-05-08
VNC Ports are blocked by routers. It works fine in LAN.

---

### Post by krunge on 2009-05-08
> **harrir said:**
> 10 sec delay loosly counted (when opening windows and similar it took 10 sec or more, for just mouse movement the delay wasn't that much, but hey, remote controlling your machine is much more than moving your mouse) against 3 ms without ssh and 6ms with ssh on hamachi (x11vnc gave those last numbers).
 The difference has so huge that it kinda surprised me. 3ms and 6ms I can live with, actually its very good, I expect it to be a little longer when Im further away, but still usable. Those loose 10(or so) sec makes it unusable. 


Try adding "-noxdamage" to the x11vnc command line.  I think you are seeing this bug:

[http://ubuntuforums.org/showthread.php?t=1097683](http://ubuntuforums.org/showthread.php?t=1097683)

[http://www.karlrunge.com/x11vnc/faq.html#faq-beryl](http://www.karlrunge.com/x11vnc/faq.html#faq-beryl)

or you can disable compiz.

I wonder when Xorg will ever fix this bug...

---

### Post by harrir on 2009-05-08
> **golusweet said:**
> VNC Ports are blocked by routers. It works fine in LAN.

I know, but vnc over ssh uses port 22 wich I have opend.

---

### Post by krunge on 2009-05-08
> I know, but vnc over ssh uses port 22 wich I have opend.

Use the x11vnc option "-noxdamage" I mention above and I think the slow response will be gone.

---

### Post by harrir on 2009-05-08
> **krunge said:**
> Use the x11vnc option "-noxdamage" I mention above and I think the slow response will be gone.

It may have helped, but cant say for sure.
Need to do some more testing, but it seems that hamachi is faster no matter what I do.

---

### Post by dragos240 on 2009-05-08
Vnc

---

### Post by krunge on 2009-05-08
> **harrir said:**
> It may have helped, but cant say for sure.
Need to do some more testing, but it seems that hamachi is faster no matter what I do.

Is it still ~10 seconds per window?

If so, is your vncviewer choosing selecting the "raw" encoding instead of something compressed like "tight" or "zrle"?  Look at the x11vnc output.  Sometimes the ssh tunnel can confuse the viewer: it thinks the connection is local and chooses the raw encoding.

See the encodings description here: [http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)

10 seconds per window for vnc is slow even for dialup modem...

---

### Post by YesSir on 2009-05-11
This guy xoroz helped me out, in case you want to use NTRconnect. I never managed to run this service, but it worked with his howto.

[http://ubuntuforums.org/showthread.php?p=7258551](http://ubuntuforums.org/showthread.php?p=7258551)

---

### Post by fatality_uk on 2009-05-11
Anyone mentioned Hamachi? Haven't had time to read all the thread.

---

### Post by harrir on 2009-05-11
> **fatality_uk said:**
> Anyone mentioned Hamachi? Haven't had time to read all the thread.

Yes I did. I have to use it to get usable speed on my remote controlling with vnc. The on page 15(I think) I say something about my experience with it.

---

### Post by infraction on 2009-05-24
Hello All,

I've just been down this long, strange road, and my solution was XRDP.

If interested, please check out this post on the Community Cafe forum.........

[http://ubuntuforums.org/showthread.php?t=1168264&highlight=xrdphttp://ubuntuforums.org/showthread.php?t=1168264&highlight=xrdp](http://ubuntuforums.org/showthread.php?t=1168264&highlight=xrdphttp://ubuntuforums.org/showthread.php?t=1168264&highlight=xrdp)


Regards,

infraction

---

### Post by Heliooos on 2009-05-25
And what is the easiest way if I want to get remote desktop between 2 linux computers? I read somewhere that VNC is too slow and that logmein has the client only for win/mac. I also heard something about NX Server Free Edition. Does anybody here use it?

---

### Post by balserodeluxe on 2009-07-23
I think here the issue is to connect to a remote Linux machine (on a dynamic DNS) from a windows (or any other OS) machine on a network that has almost all ports blocked. 

That is the advantage of LogMeIn, unfortunately no "listener" for Linux.

Hamachi, is a No configuration VPN solution from LogMeIn. 

Does anybody know if using Hamachi on both ends and THEN VNC-ing into the Remote, DynDNS, Linux Machine would work? 

This is assuming you have created a VLAN and you are tunneling your Port 5900 traffic.

---

### Post by linyanam on 2009-08-07
Gitso is another alternative
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

---

### Post by juancarlospaco on 2009-08-07
**[COLOR="Blue"]OMG![/COLOR]**
Are you kidding?, **no one think using SSH???**

SSH is Secure, Encrypted and Compressed.
If you have SSH you dont need VNC or others.

[Click here ]("apt:/openssh-server")and try on your PC :

**ssh -X $USER@127.0.0.1 nautilus**

See the magic of SSH.

Using this you can use any port, 
you only need 1 port open, to get extreme security,
and you can configure your box to only accept connections from localhost to localhost,
because you can redirect anything via the SSH tunnel.

**ssh -X remote-user@remote-server-ip anythingyouwanttorun**

Chuck Norris uses and recommend SSH :)

---

### Post by dragos240 on 2009-08-07
> **juancarlospaco said:**
> **[COLOR=Blue]OMG![/COLOR]**
Are you kidding?, **no one think using SSH???**

SSH is Secure, Encrypted and Compressed.
If you have SSH you dont need VNC or others.

[Click here ]("apt:/openssh-server")and try on your PC :

**ssh -X $USER@127.0.0.1 nautilus**

See the magic of SSH.

Using this you can use any port, 
you only need 1 port open, to get extreme security,
and you can configure your box to only accept connections from localhost to localhost,
because you can redirect anything via the SSH tunnel.

**ssh -X remote-user@remote-server-ip anythingyouwanttorun**

Chuck Norris uses and recommend SSH :)

Use SSH, otherwise Chuck will roundhouse kick you into another dimension.

---

### Post by CyberAngel on 2009-08-08
> **juancarlospaco said:**
> **[COLOR="Blue"]OMG![/COLOR]**
Are you kidding?, **no one think using SSH???**

SSH is Secure, Encrypted and Compressed.
If you have SSH you dont need VNC or others.

[Click here ]("apt:/openssh-server")and try on your PC :

**ssh -X $USER@127.0.0.1 nautilus**

See the magic of SSH.

Using this you can use any port, 
you only need 1 port open, to get extreme security,
and you can configure your box to only accept connections from localhost to localhost,
because you can redirect anything via the SSH tunnel.

**ssh -X remote-user@remote-server-ip anythingyouwanttorun**

Chuck Norris uses and recommend SSH :)

Yes, but this will open a new instance of the application...
The use of programs like vnc will allow you to connect in an already opened session and work (very useful for remote support too).

---

### Post by juancarlospaco on 2009-08-08
> **CyberAngel said:**
> Yes, but this will open a new instance of the application...
The use of programs like vnc will allow you to connect in an already opened session and work (very useful for remote support too).

*...and who said that can not be done using SSH...? :D*

---

### Post by CyberAngel on 2009-08-08
> **juancarlospaco said:**
> *...and who said that can not be done using SSH...? :D*

How?

The way you wrote it, it is opening a new instance of the remote program locally (e.g. nautilus) as I already mentioned..

how can you use ssh to "see" the remote desktop and move the mouse (in a way similar to vnc) ?

Thanks in advance :)

---

### Post by days_of_ruin on 2009-08-08
> **CyberAngel said:**
> How?

The way you wrote it, it is opening a new instance of the remote program locally (e.g. nautilus) as I already mentioned..

how can you use ssh to "see" the remote desktop and move the mouse (in a way similar to vnc) ?

Thanks in advance :)

You can't.

---

### Post by golusweet on 2009-08-08
Team viewer is best, I think.

Install via Wine. You will able to connect from Linux to windows.

Team viewer also allows to share desktop via web browser.

I haven't tested that. 

Cheers

---

### Post by howefield on 2009-08-08
> **golusweet said:**
> Install via Wine. You will able to connect from Linux to windows.

This works very well, but only works Linux to Windows, not the other way round. (In case anyone reading gets the wrong idea)

---

### Post by Fdrock on 2009-08-14
Just wanted to thank you guys this thread help me get to my ubuntu box @ home. I am using NTRconnect beautifully :P

---

### Post by &#32 Greg on 2009-08-14
> **days_of_ruin said:**
> You can't.

No, you can with screen.

---

### Post by chingson on 2009-08-23
direct X is too slow.
 Nx (nomachine.com) is a better option.For my experience
 
when bandwidth is wide enough, performance is like below
RDP>NX>VNC>Logmein
 
when BW is not enough
NX>Logmein>RDP>VNC
 
 
 
> **dragos240 said:**
> Use SSH, otherwise Chuck will roundhouse kick you into another dimension.

---

### Post by endtroducing on 2009-09-15
Hi!

Im looking for something for getting through firewalls and proxy.

Logmein and Crossloop do that well for Windows.

Any ideas?

---

### Post by ahildoer on 2009-09-30
> **days_of_ruin said:**
> You can't.

True, you can't see the entire desktop with SSH, but you can open individual applications that are not already running. Simply log into your box with ssh -X host.domain. The -X will forward the X session to your local box. 

Limitations:
-Can't forward X sessions of applications already running on the remote computer. 
-Does not forward desktop, "start menu", etc.
-Need an X server running locally, so on windows client need something like X-win32 (not free). It may be possible with cygwin installed, but I have not tried it.
-SLOW even over gigabit ethernet between two powerhouse systems

Advantages:
-free if connecting from linux client
-makes GUI apps available remotely
-secure
-compressed (though the Xsession proxy data is so chatty it almost completely offsets any benefits of compression)
-Works on any system running X windows applications.

I am sure there are other points to be made, but these seem to be the most relevant. Personally, until X forwarding is as slick and responsive as windows' native rdp, I rather just use a tui and ssh into every box, including windows via cygwin ssh server.

---

### Post by daudelahi on 2009-11-01
Try Using NoMachine. i have been using it for last few years and works great, you have to install server setup on the machine you want to access and the client setup from machine you want to access.

here is the link

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

---

### Post by johnnylavah on 2009-11-01
> **daudelahi said:**
> Try Using NoMachine. i have been using it for last few years and works great, you have to install server setup on the machine you want to access and the client setup from machine you want to access.

here is the link

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

does it work better than tightVNC?  seems like similar functionality...

---

### Post by frankh on 2009-11-12
VNC is quite more complicated than logmein, and not really an alternative. One of the sweet features of logmein is to have a way to connect remotely when you're behind a coorporate firewall, f.ex. In my workplace, it's not possible to set up VNC access to a machine inside the LAN. Logmein works like a charm there.

---

### Post by CyberAngel on 2009-11-12
> **frankh said:**
> VNC is quite more complicated than logmein, and not really an alternative. One of the sweet features of logmein is to have a way to connect remotely when you're behind a coorporate firewall, f.ex. In my workplace, it's not possible to set up VNC access to a machine inside the LAN. Logmein works like a charm there.

When you are behind a firewall you can try the reverse vnc method ;)
[http://ubuntuforums.org/showthread.php?t=299489](http://ubuntuforums.org/showthread.php?t=299489)

Anyway I will still agree that vnc is not really an alternative....

---

### Post by LookTJ on 2009-11-12
The closest alternative I come across to logmein is yuuguu.

---

### Post by razor7 on 2009-11-14
Hello...I recommend FreeNX

Best Regards!

---

### Post by nbros652 on 2009-11-18
Linux to Linux Specific solution (requires Empathy):

I had been asking this very same question, when I unexpectedly stumbled on an answer while trying to figure out what could possibly possess the folks turning out Ubuntu to switch from Pidgin as the default IM client to Empathy. One of the things I discovered is that Empathy has built-in the ability to initiate a VNC session between users both running Empathy. The best part is that this session requires no extra networking setup for people behind routers!

Here's how I did it:
1. Get both users running Empathy. I used a Google Talk text-based IM session.
2. Instruct the user who would like assistance to select "Contact" from the menu bar of the text-based IM session, and choose "Share my desktop"
3. At this point, the assister should receive a notification that someone is "offering and invitation and [an external application will be started to handle it]." Now the assister must click on the Empathy icon (that is flashing) on the taskbar in the notification area.
4. This opens the VNC viewer, and displays the other user's desktop for remote assistance. Whether the other users system is setup for desktop sharing or not.

Hope this helps.

---

### Post by xouns on 2010-02-16
Hmmm, this LogMeIn stuff sounds a lot easier than *whatever*VNC. I have been wanting to connect to my desktop from either work or college, using my laptop. Would have loved to see it work using Ubuntu server-side, but I couldn't see any programs opening (although they did).
Think I'll just use Vista and 7(serverside) via LMI. Thanks for the idea!

---

### Post by gnarliprime on 2010-04-17
teamviewer.com, after a long search and not reading all the posts in this forum i have finally found a web based remote control. It is a bit slower than logmein, but as i do not have access to vnc at work i have finally found something that works.

---

### Post by malleeblue on 2010-04-17
I've checked out TeamViewer but so far I'm unaware of its ability to remote control a Linux OS. In my experience it can control a windows or mac OS from Linux but not in reverse. As the root of this thread is about finding an easy way to remote into a linux OS can you please explain how you're doing it? Thanks.

---

### Post by CyberAngel on 2010-04-17
> **malleeblue said:**
> I've checked out TeamViewer but so far I'm unaware of its ability to remote control a Linux OS. In my experience it can control a windows or mac OS from Linux but not in reverse. As the root of this thread is about finding an easy way to remote into a linux OS can you please explain how you're doing it? Thanks.

They`ve just released an official linux version ported via wine :)

---

### Post by Sepiraph on 2010-04-18
I am using NTRConnect on Ubuntu 9.10 and I can access it from Vista just fine, only possible complain is the speed but the setup was similar to Logmein.

Follow this guide: [http://felipeferreira.net/?p=369](http://felipeferreira.net/?p=369)

---

### Post by amlucent23 on 2010-04-19
[http://alternativeto.net/desktop/teamviewer/?profile=linux&platform=linux](http://alternativeto.net/desktop/teamviewer/?profile=linux&platform=linux)

Scroll down to see them all.  A lot of them I have never tried so I cant say how they will fair one way or another.. try them for your self.

---

### Post by marcovanbeek on 2010-04-20
Hi,

The LogMeIn client for Firefox works fine on Ubuntu 9.10. I am running x64 and it took me a little while to get it running, but basically there is a .deb on LogMeIn's web site ([https://secure.logmein.com/labs/](https://secure.logmein.com/labs/)).

If you are running a 64 bit version you can use nspluginwrapper (was already installed on my laptop when I went looking for it). There are some useful instructions here: [http://thesystemsadministrator.net/2010/03/logmein-client-on-slackware64/](http://thesystemsadministrator.net/2010/03/logmein-client-on-slackware64/) . You need to extract the plugin from the archive first, but that is just a matter of opening it in the archive manager rather than the Package Installer, and looking inside the data tarball.

---

### Post by schirpich on 2010-04-24
Last year I wrote a tutorial installing hamachi on ubuntu, but last sept when they released v2 they pretty much dropped all support for linux.  I believe they changed or modified the protocols or something to that tune.

If you go look at their forums there's all sorts of people asking what the deal is with linux support.  All they have to say is "We're working on it".  Well, they've been saying that for the last 9 months and literally mock people asking for status updates, or beta.  personally I'm kinda fed up with logmein.  they've got some cool stuff, but I think they only really care about charging people with subscriptions.  

So for the past week I've been searching for a replacement to hamachi and found neorouter.  It's got native support for linux, windows and osx.  So I wrote a new tutorial this week on it.  

Basically think a mix between OpenVPN and Hamachi and you've got neorouter.  see for yourself

[http://www.sucka.net/2010/04/neorouter-the-hamachi-replacement-kille/](http://www.sucka.net/2010/04/neorouter-the-hamachi-replacement-kille/)

---

### Post by tapas_mishra on 2010-04-29
Well if your needs are to just access the remote desktop you can use Skype it has a feature to share desktop.Person on other end should have skype installed works on Linux,Window,Mac :)
I have used it without problems.
I have tried.

---

### Post by ergosteur on 2010-04-29
> **CyberAngel said:**
> They`ve just released an official linux version ported via wine :)

I second teamviewer. Performance is decent, pretty easy to use. I'm kind of curious as to how they got wine to interact with the existing X environment like that...

Plus, Teamviewer has an iPhone app, if you're into that.

---

### Post by johnhrschuster on 2010-05-11
Teamviewer appears to be $600+ a copy?  Am I missing something?  Would be nice if LogMeIn would embrace Linux environment

---

### Post by CyberAngel on 2010-05-11
> **johnhrschuster said:**
> Teamviewer appears to be $600+ a copy?  Am I missing something?  Would be nice if LogMeIn would embrace Linux environment

Anyway it`s free for non commercial use :)

---

### Post by 98cwitr on 2010-05-11
i used hamachi at my last job to get into work...it rocks...and is made by the same company that does logmein :) Then you can use RDP or VNC to get into your box(es). Hamachi was easily installed following these instructions: [http://supware.net/HamachiUbuntuHowto/](http://supware.net/HamachiUbuntuHowto/)

---

### Post by 7h3d4rk0n3 on 2010-05-14
I think your answer lies in TeamViewer, which has recently been made for  Linux. It allows you to remotely access any computer in which you have  it installed on. You can also create an account and have a partner list,  which makes connecting to multiple computers very easy without having  to remember the access numbers for separate computers. Hope this helps.

------------------------------------------------------------------------------------------------------

Derik

AKA: ThedarKOne

---

### Post by dragos240 on 2010-05-14
Old topic is Old.

---

### Post by at0msk on 2010-06-09
> **dragos240 said:**
> Old topic is Old.

Old problem not solved is old.

---

### Post by RiceMonster on 2010-06-09
adjective noun is adjective

---

### Post by LtPitt on 2010-06-19
Teamviewer does the job for me without all the average linux mess

---

### Post by DarrenCT on 2010-06-19
Teamviewer has also been doing a great job for me.  Is there a way to make it start in the background when Ubuntu boots up?

---

### Post by AndyInNYC on 2010-07-21
Old topics revived...

I have a group of Grandparents/non-techies who need to access through their Windows laptops a 10.04 server running Samba.

I/they don't need desktop sharing or remote programs, just access to the shared drives.

I don't want to set up a VPN - I need to keep this dead simple (I have access to neither the users, the machines nor the server on any regular basis).

I do need secure (password) access and would love for the shares to be mappable on the Windows machines.

Given the relatively sparse needs, which of the available solutions best fits my need?

Thanks all.

Andrew

---

### Post by tapas_mishra on 2010-07-21
try [http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

---

