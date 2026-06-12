---
title: "Is there a way to allow a program to go through the firewall?"
date: 2009-10-31
forum: Security
---

### Post by MaxTesla on 2009-10-31
Is there a way to allow a program to go through the firewall?
 
 
I have a program that runs with WINE and I can see that it barely gets through the firewall, it connects for a few seconds then is unable to connect for another and so on and so forth
 
 
In windows you can allow programs through firewall by clicking and adding them to a list
 
 
Is the same possible in Ubuntu and if so, then how exactly in the most exact way do I do that exactly

---

### Post by XCan on 2009-10-31
First of all, how did you configure your firewall? Ubuntu doesn't put any rules to iptables by default since it's not needed, i.e., everything are allowed. 

What kind of program is this, is it spanning over tons of random ports? In my world, if you're using a program trying to access specific ports, unless your firewall is crap it should either let traffic through or not, there's no in-between.

---

### Post by MaxTesla on 2009-10-31
First I do not know anything about programming.


I did not configure anything I just followed a link in ubuntu help about security which gave me a link to download a firewall.


[https://help.ubuntu.com/9.04/keeping-safe/C/firewall.html](https://help.ubuntu.com/9.04/keeping-safe/C/firewall.html)




I do not know if the program access several ports, I do not know what a port is.


And yes this program does indeed work in between it stays connected for a few seconds then drops the connection for a few seconds, it is a trading program and allows you to see what connection you have and how fast it is pinging, when I run it in windows the exact same program there are no problems and I get a nice green ping of 20 or so in ubuntu I get connection on and off all the time and when it is on it is around 3000 red.


So back to my original question is there like a list where I can just click allow this program through firewall like there is in windows?

---

### Post by XCan on 2009-11-01
I think we still need to know what kind of program this is. But the short answer is no, firewalls are port based not application based.

You should also consider why you need a firewall in Ubuntu. I would disable Firestarter and remove it from the system. As you see, obviously you want apps to access the internet, but the firewall may stop them. It doesn't make sense to run a firewall unless you're running either insecure server services (read: like Windows' services) or know exactly what you're doing to secure it up. Downloading an app to set up a bunch of iptables rules (firewall rules) doesn't make sense.

---

### Post by cariboo on 2009-11-01
As a point of interest, firestarter is no longer recommended, as it is no longer maintained. Ufw an iptables configuration utility is installed by default. If you need a gui, gufw is in the repositories.

You don't need to do anything to iptables in a default install, as there are no ports listening.

---

### Post by MaxTesla on 2009-11-01
It is a trading program, I trade economic goods, stocks, oil etc etc etc
 
 
 
And yes I want a firewall I do not want to lose my money SO if Firestarter is no longer supported is there another firewall that is?
 
 
 
And what is gfuw, gui, Ufw and iptables?
 
 
 
If all firewalls in linux are port based and not application based then how do I allow my program to connect to the internet?
 
All I want is to have a firewall and to run my program through that firewall
 
Now how do I do that?

---

### Post by cariboo on 2009-11-01
Firestarter is just a graphical interface to setup firewall rules, iptables is referred to as the fire wall.

Ufw stands for uncomplicated firewall, gufw is a grapichal interface for ufw.

In a default Ubuntu installation the firewall doesn't block anything, as there is nothing open. A default Ubuntu installation is more secure than a default Windows installation. 

You have some other connection problem that have nothing to do with the firewall.

---

### Post by MaxTesla on 2009-11-01
All I want is to get a firewall, yes Ubuntu is safer than Windows but I still want a firewall
 
Now how do I set up a firewall and allow my program through that firewall?

---

### Post by Lars Noodén on 2009-11-02
The default on ubuntu is to let everything in and out. 
The next best would be to let everything out but only replies plus a few selected activities back in.  So in short, there is no firewall on the desktop machine unless you add one.  Do you mean a firewall on your gateway or router?

As, cariboo907 mentioned there are gui front-ends to iptables.  iptables is the packet filter (aka firewall) for the linux kernel as ipfw and pf are for other kernels.  A 'hardware' firewall is just a computer with no video running linux, bsd, or qnx and a packet filter.  

To address your question explicitly, if you want a gui to build a firewall on your desktop, for your desktop, then fwbuilder is also popular and I found that those new to Ubuntu seem to recommend it over others.  Again, all these are front ends to iptables.  

1) use the package manager (probably synaptic) to install [fwbuilder](http://packages.ubuntu.com/search?keywords=fwbuilder&searchon=names&suite=karmic&section=all)

2) read the fwbuilder users' guide

3) add the network objects you need (e.g. dns, local network ip ranges, network cards, etc.)

4) choose new firewall for iptables running on linux 2.4/2.6 

5) build filter rules for iptables (not IOS, PF, IPfw) to meet your wishes

However, it sounds like a firewall on your desktop is not the problem.  A tool that complements fwbuilder is zenmap, which is a gui for nmap.  It will allow you (from another computer) to scan your own machine and see for sure what is open or closed.  

You can see where the bottlenecks in the network connection are this way using [traceroute](http://linux.die.net/man/8/traceroute):

```

# preparation, lookup options -N -n -p and -T in the help
traceroute --help

# check the way to target, without wasting time on resolving host names
traceroute -N 1 -n *target*

# or this way, 
# substituting "80" for the correct port number of the remote service
sudo traceroute -N 1 -T -n -p 80 *target*

```

You'll get five column output that looks like this:
```

17  74.125.79.103  95.679 ms  93.534 ms  87.188 ms

```

The last three columns are the times, slowest, average, fastest.  Smaller numbers are better.  They should be in the low double-digits...

---

### Post by __p1n__ on 2009-11-02
There's a good possibility imho that the server is calling the client back on another port and not using the client-initiated connection.  The default fw configuration is likely dropping unsolicited inbound traffic which would include an out-of-band callback from the server.  Try monitoring the client to see what listen ports it opens and then update the firewall accordingly.  If it opens a random port each time then you will need to add an iptables rule specifically allowing all traffic from the server's ip address. 

It might not actually have anything to do with a firewall however but rather some windows-specific behavior of the trading client.  Note that this is running under wine and not in a virtual machine.

Try running the client in a windows domu using whatever virtualization software that you prefer.  If it runs correctly then the issue is definitively not with your firewall which I think lars has adequately demonstrated above.

---

### Post by Lars Noodén on 2009-11-03
> **__p1n__ said:**
> There's a good possibility imho that the server is calling the client back on another port and not using the client-initiated connection.  The default fw configuration is likely dropping unsolicited inbound traffic which would include an out-of-band callback from the server.  Try monitoring the client to see what listen ports it opens and then update the firewall accordingly.


A tedious (for some) way to do that would be to use [tcpdump](http://manpages.ubuntu.com/manpages/karmic/en/man8/tcpdump.8.html).  Snort is more complex but helps visualize the results better.  You can probably figure out snort.  Tcpdump is the quick-n-dirty way to get results now.

```

# assuming network interface eth0 for these

# dry run
man tcpdump

# show all traffic to or from the remote service
sudo tcpdump -q -i eth0 host *xx.yy.zz.aa*

# show all traffic to the remote service
sudo tcpdump -q -i eth0 dst host *xx.yy.zz.aa*

# show all traffic from the remote service
sudo tcpdump -q -i eth0 src host *xx.yy.zz.aa*

# show all traffic from remote service that is not on http or https ports
sudo tcpdump -q -i eth0 src host *xx.yy.zz.aa* and not \( port 80 or 443 \)

```

That should give you output something like this, minus my annotations.

```

...
10:56:48.191632 IP mini.**50797** > nameservera.inetisp.net.**domain**: UDP, length 34
10:56:48.219745 IP mini.**49679** > feijoa.canonical.com.**www**: tcp 0  
10:56:48.281577 IP mini.**49679** > feijoa.canonical.com.**www**: tcp 0  
10:56:48.281711 IP mini.**49679** > feijoa.canonical.com.**www**: tcp 2896
...

```

In the above, my machine is 'mini', the ISP's domain name server is 'nameservera.inetisp.net', and a web server I am connecting to is 'feijoa.canonical.com'  The www connection is from port 49679 on my machine to port 80 (www) on their machine.  

If you want the addresses and port numbers as numbers then use the -n option.  The default are that the numbers are using the labels from /etc/services

> **__p1n__ said:**
> 
Try running the client in a windows domu using whatever virtualization software that you prefer. 



Hey.  That falls under the malicious commands warning, if not only for him then also for the rest of us that have to share the same Internet.  Do the problems with that approach need to be enumerated?

[Crossover](http://www.codeweavers.com/products/download_trial/) would be the first fall-back if regular WINE turns out to be the cause.  

The networking tests should show where the problem lies.  There are also specialist [ubuntu forums just for WINE](http://ubuntuforums.org/forumdisplay.php?f=313) that might be of use.  Even the [main WINE forums](http://www.winehq.org/help/) could be of use, if it is not the network.

---

### Post by __p1n__ on 2009-11-03
> **Lars Noodén said:**
> 
Hey.  That falls under the malicious commands warning, if not only for him then also for the rest of us that have to share the same Internet.  Do the problems with that approach need to be enumerated?

Don't get in a twist.  It's entirely reasonable as a diagnostic approach to run the trading client inside a windows domu on top of a linux host to determine whether the problem is with the linux firewall configuration or the lack of some putatively unspecified win service.

---

### Post by MaxTesla on 2009-11-03
Ok dudes, your replies are all very nice but you are vastly overestimating my capabilities.


This is what I can do


[LIST]
[*]I know how to download things from the internet.
[*]When something is downloaded I can double click to install it.
[*]I know how to copy and paste commands into the terminal
[/LIST]

Everything that you wrote is probably correct but I do not understand any of it.


All I want to do is to get my program to work, I think it is the firewall that blocks it but as you say it could be something else.


I have no way of doing all that stuff you said, it is way too complicated for me.


So I guess then that I will stick with windows until ubuntu gets more user friendly for none programmers like me.

---

### Post by cariboo on 2009-11-04
Maybe you should suggest the maker of the software you use, create a Linux version of the program.

Linux is used in finance.

---

### Post by Lars Noodén on 2009-11-05
> **MaxTesla said:**
> 


[LIST]
[*]I know how to download things from the internet.
[*]When something is downloaded I can double click to install it.
[*]I know how to copy and paste commands into the terminal
[/LIST]


Hmm.  I find Windows too difficult to recommend to non-technical folks.  

Could you post the URL to the download page for the program in question?
If you have it, the link to the system requirements page would work, too.

What did you think of gufw or fwbuilder?

---

### Post by scaine on 2009-11-06
MaxTesla, if you have installed Ubuntu, then wine, then your finance program, you're more than capable of fixing this, or at least testing it to be sure.  It's not likely a firewall issue you're having, but just to be sure, fire up a terminal and do:
remove firestarter :
```
sudo apt-get remove firestarter
```
install gufw :
```
sudo apt-get install gufw
```
And then run gufw by clicking on your System menu, then Administrator, then Firewall Configuration.

If the shield is green, your firewall is on.  If it's grey, it's not.

I suggest turning it off, then trying your program.  If it still doesn't work, then your finance program likely just isn't compatible with wine - you'll have to stick to Windows or run Windows in a virtual machine to use it.

Good luck.

---

### Post by scaine on 2009-11-06
> **MaxTesla said:**
> So I guess then that I will stick with windows until ubuntu gets more user friendly for none programmers like me.

I'm a non-programmer, MaxTesla, but I've been a happy Ubuntu user for 4 years now.  It depends on your expectations.  I don't expect Windows programs to work in Ubuntu and I'm genuinely amazed if they do.  Seems like you're a little more demanding that I am, or at the very least use some pretty esoteric software.

However it works out for you, good luck and I hope you enjoyed dipping your toes in the water.

---

### Post by bodhi.zazen on 2009-11-06
> **MaxTesla said:**
> Ok dudes, your replies are all very nice but you are vastly overestimating my capabilities.


This is what I can do


[LIST]
[*]I know how to download things from the internet.
[*]When something is downloaded I can double click to install it.
[*]I know how to copy and paste commands into the terminal
[/LIST]

Everything that you wrote is probably correct but I do not understand any of it.


All I want to do is to get my program to work, I think it is the firewall that blocks it but as you say it could be something else.


I have no way of doing all that stuff you said, it is way too complicated for me.


So I guess then that I will stick with windows until ubuntu gets more user friendly for none programmers like me.

First, Linus is not hard and it is as user friendly as Windows.

Second, I think your biggest mistake, you are blindly applying your windows knowledge to Linux. While there is no doubt you are a competent windows user, Linux is not windows.

Now lets look at your situation. First it sounds as if you are not using Linux, you are trying to run a windows application in Wine. Please understand this is complicated and there is no guarantee it will work at all. If this is what you are wanting to do, yes you will need to be prepared to do some debugging yourself.

Start by looking up your application in wineHQ, in the application data base :

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Since wine is complex, most people needing to run an occasional windows program will use Virtualization, such as virtualbox, and run windows within a virtual machine.

The next mistake you made is in assuming your problem is due to a firewall. You are jumping to conclusions.

===

A brief discussion on firewalls is probably appropriate here.

Unlike Windows, a default installation of Ubuntu has no significant listening servers, so a firewall is not likely to help you much.

For a brief overview of Ubuntu security , see:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

To configure your firewall in Ubuntu, use ufw, it is installed by default.

Open a terminal and enter:

```
sudo ufw enable
```The default settings are to allow all outbound traffic and block all unsolicited inbound traffic.

If you prefer to use a gui, use gufw (you will need to install it)

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

[http://www.howtoforge.com/firewall-management-with-gufw-on-ubuntu-8.04](http://www.howtoforge.com/firewall-management-with-gufw-on-ubuntu-8.04)

If this is not sufficient for your needs, the next step is to learn how firewalls work :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

=====

Last none of this is "programming". If you want to learn Linux we would be more then happy to help, but you will need to be willing to learn new tricks and new ways of thinking of security.

---

### Post by MaxTesla on 2009-11-07
cariboo907 - Maybe one day I do not want to make waves
 
Lars Noodén - There is no web page to download it from you get it from a mail
 
scaine - I am the kind of guy who wants everything to work out of the box and auto fix itself :P
 
bodhi.zazen- Someday maybe

---

### Post by bodhi.zazen on 2009-11-07
> **MaxTesla said:**
> bodhi.zazen- Someday maybe

Whenever you are ready, we would be happy to assist you. It took me 6 months to be comfortable with Linux and so just be patient, one step at a time.

Again, for the most part, Ubuntu *does* work out of the box. You are trying to do something complex, to be fair, lets see you get KDE ( a Linux application) running on Windows.

It is done using cygwin (cigwin is akin to wine).

---

### Post by Lars Noodén on 2009-11-09
> **MaxTesla said:**
> I am the kind of guy who wants everything to work out of the box and auto fix itself :P
 

Cool.  A fellow mac user.

---

