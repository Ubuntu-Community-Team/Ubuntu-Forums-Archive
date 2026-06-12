---
title: "Looking for a server distro that boots really fast"
date: 2009-08-02
forum: Server Platforms
---

### Post by Osmoroid on 2009-08-02
Hi,
I was looking for a server linux distro that would boot really fast. This is very crucial to my server installation as the computer is quite old and most distros take a large amount of time to start up. (Usually about 3-5 minutes)
Does anyone know a server distro that would boot fast?

---

### Post by fakrulalam on 2009-08-02
Ubuntu no doubt :-) 

Check out this site
[http://www.neowin.net/news/main/09/06/11/ubuntu-targets-10-second-boot-time-for-2010-release]("http://www.neowin.net/news/main/09/06/11/ubuntu-targets-10-second-boot-time-for-2010-release")

---

### Post by Osmoroid on 2009-08-02
Thanks for the info. Would you know any distros made for the i586 architecture. (AMD K6-2)

---

### Post by HermanAB on 2009-08-02
Uhmmm, usually a server needs to stay up once running so boot time is no problem.  My servers only reboot once in 3 years or so.

---

### Post by cb951303 on 2009-08-02
I don't understand, why do you need fast boot time for a server?
Servers aren't supposed to be rebooted that often.

---

### Post by Osmoroid on 2009-08-02
I need a fast boot time because it is a home server. I don't want it to be on all the time and for this reason it would be great if it had fast boot times. So I can switch it on when needed.

---

### Post by HermanAB on 2009-08-02
OK, I understand.  However, it may be better to turn on all the power saving features (cpu clock speed control, hard disk wind down, no screen on it) and then just let it be.

---

### Post by ericab on 2009-08-02
> **cb951303 said:**
> I don't understand, why do you need fast boot time for a server?
Servers aren't supposed to be rebooted that often.

im so tired of people saying 'blah blah blah servers aren't supposed to be rebooted.'
its his freaking server let him reboot it if he wants!!
if your not going to answer his question, then don't add unrelated items. good for you; you don't reboot your server.

have some popcorn  :popcorn:

---

### Post by cb951303 on 2009-08-03
> **ericab said:**
> im so tired of people saying 'blah blah blah servers aren't supposed to be rebooted.'
its his freaking server let him reboot it if he wants!!
if your not going to answer his question, then don't add unrelated items. good for you; you don't reboot your server.

have some popcorn  :popcorn:

why are you tired? what's it to you?
it's you who doesn't add anything to the conversation.

servers are servers, and a "server that boots really fast" is something unusual, that's why I asked.

now go hijack other threads and have some popcorn too:popcorn:

---

### Post by Serangan on 2009-08-03
You could try sleep.

My home server uses the desktop edition of ubuntu, and when no computers are on, goes to sleep (after checking a few things) and i have wol to wake it up. Takes about 2 seconds for it to come back to being 'fully alive'.

---

### Post by Osmoroid on 2009-08-03
Thanks for all the information you have given. However due to the computer being so old I probably wouldn't be able to control fan speed, hard drive spin down etc. I will have to look at the bios to see whether it has wakeup on lan. I definitely wouldn't be able to install ubuntu desktop on it. The computer is too old for it.
The computer is a IBM Aptiva
CPU: AMD K6-2
Memory 256MB
Hard Drive: 500GB

---

### Post by windependence on 2009-08-03
> **ericab said:**
> im so tired of people saying 'blah blah blah servers aren't supposed to be rebooted.'
its his freaking server let him reboot it if he wants!!
if your not going to answer his question, then don't add unrelated items. good for you; you don't reboot your server.

have some popcorn  :popcorn:

Nice. Typical Windoze attitude. I have boxes that have been up YEARS. There is no reason to constantly reboot or shutdown for that matter. The power difference is so small it's inconsequential.

To the OP, if you just need a box to run without a GUI, headless, and serve files etc., check out FreeBSD. It's not Linux but most of the syntax is the same. Boot time is seconds.

I had just such a box as yours I served a large forum from before I could obtain server class hardware. I ran OpenBSD on that box and never had problems. Doesn't take up any space to speak of either.

-Tim

---

### Post by Osmoroid on 2009-08-03
Ok, I'll check out freebsd and openbsd and report back my experience of it.

---

### Post by jocampo on 2009-08-03
> **ericab said:**
> im so tired of people saying 'blah blah blah servers aren't supposed to be rebooted.'
its his freaking server let him reboot it if he wants!!
if your not going to answer his question, then don't add unrelated items. good for you; you don't reboot your server.

have some popcorn  :popcorn:

hahaha, you made me laugh! ...but take it easy. What's true and a fact for me (maybe not for others) is that I reboot my home server from time to time. It is running Ubuntu Server edition, headless, no GUI at all. But in real production environment, servers are not rebooted so often. Obvious reasons, you run mission critical application there. What you could run at home is your VirtualBox lab or host lot of crap and family pictures because the hard drive is so big ;-) (my case) so, there is no problem rebooting.

But regarding the thread, I would suggest Ubuntu Server and try to use ext4, the new file-system. It has some improvements and one of them was help with the boot process. Checking your services and disable those who you're not using or need is a good starting point also.

---

### Post by Thirtysixway on 2009-08-03
Just make sure you start your server before your desktop :)  And yeah I have a home server I leave running 24/7, but only because I run torrents as well as printer sharing.  But nothing says you can't shut it down if that's what you want.

This is sort of revelant, I wrote a blog post about setting up a script that automates shutting down the server

[http://noobbox.com/2009/02/09/automate-ubuntu-server-shutdown](http://noobbox.com/2009/02/09/automate-ubuntu-server-shutdown)

---

### Post by Serangan on 2009-08-04
yes, thats the script you made for me :P I've made some changes to what it does after finding no 'nodes' on now. Calls for a new script called 'autoshutdown' and this 'autoshutdown' checks to see if no ssh logins are active, the network isn't in use, or the cpu isn't above a certain threshold.

Really useful IMO 

Also, as jocampo states, it isn't 'mission critical'. It's simply a home server, that shares files for mainly personal use. Whats the harm in rebooting or shutting down?

And from memory, (I had an IBM Aptiva) it does support wol and sleep. But i cant be certain.

---

### Post by Osmoroid on 2009-08-04
Serangan, that 'autoshutdown' script sounds incredibly useful. What distro do you use for your home server?

---

### Post by Serangan on 2009-08-04
Ubuntu desktop edition. The server edition wouldnt allow me to wol from sleep. Ill post it in here next time im accessing the server.

And it isnt my own script, i've just tweaked it to my needs.

```

#!/bin/bash
# autosleep.sh
# Checks if the computer is inactive before going to sleep. #Aborts if it looks like there's some action.
#

# Thresholds - these may depend on what you do with your computer and what you want it to stay awake for.
CPUTHRESH=5        # in percent 
NETTHRESH=10       # in kB/s

# Sample times (in seconds) - again needs may vary
CPUTIME=1   
NETTIME=2


# Check CPU usage defined as non-idle time.
CPU=`sar $CPUTIME 1 | awk '/Average/ { printf "%d\n",100-$8}'`
echo "CPU = $CPU%"
if [ $CPUTHRESH -lt $CPU ];then
    echo CPU is working, not sleeping
    exit;
fi

# Check net usage (exclude wifi0 which appears to have activity all the time for some weird reason)
NET=`sar -n DEV $NETTIME 1 | awk '/Average:/ && $2 !~ /(IFACE|wifi0)/ { SUM += $5 + $6 } END { printf ("%d\n",SUM)}'`
echo "NETWORK = $NET"
if [ $NETTHRESH -lt $NET ]; then
    echo Network is in use, not sleeping
    exit;
fi

# check for remote login
REMOTELOGIN=`last | head | grep "pts/.*still logged in"`
if [ -n "$REMOTELOGIN" ];then
    echo Remote login active:
    echo $REMOTELOGIN
    echo Not sleeping
    exit;
fi

# Go into standby

# Enter your command here
# Below is what I use

ethtool -s eth0 wol pg && pm-suspend

```

There's one prerequisite; sysstat needs to be installed

---

### Post by Osmoroid on 2009-08-04
Ok. It would be great if you could post the script on this thread.

---

### Post by Serangan on 2009-08-04
Added in post my post above. Just in case you haven't noticed.

Also, im sure there are other things that could be added to this. And of course you can edit it as you wish :P

This in conjunction with Thirtysixway's script to check if no other nodes are on are really useful for a home server. ie, there's no point in having it running over night, and if you want to use it to download something, no need to stop the script or leave another node on, cause 'autoshutdown' is monitoring the network usage, once the download is complete; the server turns off or goes to sleep.
Really useful.

---

### Post by -=hazard=- on 2009-08-04
I dont understand the idea... a server to boot fast. I mean my server is up from the moment I rented it.... 5 months ago and it will be up for a long time.
Ok you say its a home server and you dont want it to stay up all the time but only when you need it, so I guess that when you say ***only when you need it***, it means that it's only you that use it, so if you switched off your server lets say for 12 hours and you need it now, where is the problem to wait 2 minutes of boot if your server was switched off all night long? For my opinion 2 minutes or 20 seconds of boot time doesnt make much diference if we are speaking for a server, expecialy for your old PC.
All linux distros boot fast depending what you have isntalled on it, what services you have activated. For example Gentoo boot very fast, I have used it for 5 months on a dedicated and it boot in 12 seconds, but it depend on what you install on it. Another fast distro is [Yoper]("http://www.yoper.com/index.php") , it boot very fast but when working on it you will notice a lot of diference. Anyway I think ubuntu server edition remains the best choice, just activate only the services you need.
Cheerz.

---

### Post by Osmoroid on 2009-08-04
Ok thanks. Downloading the script now.
-=hazard=- you are probably correct about not actually needing a lightning fast boot up. At the moment I'm trying OpenBSD but currently having problems booting the cd.

---

### Post by Serangan on 2009-08-04
> **-=hazard=- said:**
> I dont understand the idea... a server to boot fast. I mean my server is up from the moment I rented it.... 5 months ago and it will be up for a long time.
Ok you say its a home server and you dont want it to stay up all the time but only when you need it, so I guess that when you say ***only when you need it***, it means that it's only you that use it, so if you switched off your server lets say for 12 hours and you need it now, where is the problem to wait 2 minutes of boot if your server was switched off all night long? For my opinion 2 minutes or 20 seconds of boot time doesnt make much diference if we are speaking for a server, expecialy for your old PC.
All linux distros boot fast depending what you have isntalled on it, what services you have activated. For example Gentoo boot very fast, I have used it for 5 months on a dedicated and it boot in 12 seconds, but it depend on what you install on it. Another fast distro is [Yoper]("http://www.yoper.com/index.php") , it boot very fast but when working on it you will notice a lot of diference. Anyway I think ubuntu server edition remains the best choice, just activate only the services you need.
Cheerz.


I see what you mean, but in my case, it isn't just me who uses the 'server'. If it was just me, then it would only be running when i need it. But because of everyone else, I decided that it would be better if it was quick to be active.

I second the use of ubuntu server edition, and just activating the services you need, but until wol from suspend is enabled (and i doubt it will 'cause servers aren't usually used for this) the generic kernel is more useful for acpi needs (as it should be).

---

### Post by -=hazard=- on 2009-08-04
> **Serangan said:**
> I see what you mean, but in my case, it isn't just me who uses the 'server'. If it was just me, then it would only be running when i need it. But because of everyone else, I decided that it would be better if it was quick to be active.

I second the use of ubuntu server edition, and just activating the services you need, but until wol from suspend is enabled (and i doubt it will 'cause servers aren't usually used for this) the generic kernel is more useful for acpi needs (as it should be).

Either in that case, that others use it too, its the same. Just think if I use your server, I wait 2 days for the server to be up 'n running, I don't mind if it get 2 minutes to boot. I don't even know when you are booting it :)

---

### Post by Serangan on 2009-08-04
Not sure I follow the > I don't even know when you are booting it

You have valid reasons and i agree with them, but in the end, its my choice. And for simplicity sake, i choose to put the server to sleep, takes 2 seconds max for it to come back to being fully active, and no one is the wiser. And anyway, whats the harm in having it boot fast? Or resuming fast? There's nothing wrong with having it running 24/7 but, over night, when no one is using the computers/server, is it really necessary to have it running?

---

### Post by ericab on 2009-08-04
> **Serangan said:**
> 

```

#!/bin/bash
# autosleep.sh
# Checks if the computer is inactive before going to sleep. #Aborts if it looks like there's some action.
#

# Thresholds - these may depend on what you do with your computer and what you want it to stay awake for.
CPUTHRESH=5        # in percent 
NETTHRESH=10       # in kB/s

# Sample times (in seconds) - again needs may vary
CPUTIME=1   
NETTIME=2


# Check CPU usage defined as non-idle time.
CPU=`sar $CPUTIME 1 | awk '/Average/ { printf "%d\n",100-$8}'`
echo "CPU = $CPU%"
if [ $CPUTHRESH -lt $CPU ];then
    echo CPU is working, not sleeping
    exit;
fi

# Check net usage (exclude wifi0 which appears to have activity all the time for some weird reason)
NET=`sar -n DEV $NETTIME 1 | awk '/Average:/ && $2 !~ /(IFACE|wifi0)/ { SUM += $5 + $6 } END { printf ("%d\n",SUM)}'`
echo "NETWORK = $NET"
if [ $NETTHRESH -lt $NET ]; then
    echo Network is in use, not sleeping
    exit;
fi

# check for remote login
REMOTELOGIN=`last | head | grep "pts/.*still logged in"`
if [ -n "$REMOTELOGIN" ];then
    echo Remote login active:
    echo $REMOTELOGIN
    echo Not sleeping
    exit;
fi

# Go into standby

# Enter your command here
# Below is what I use

ethtool -s eth0 wol pg && pm-suspend

```



Fantastic!
a little bit creepy though; the past couple days ive been searching for something *exactly* like this, to automatically pm-suspend my server when idle... ahh well, great minds think alike no ? (since its idle about 65% of the day)

could you post the original script ?
my wallet thanks you.
:D


*edit* 
could you explain the usage of this script a little more ? it doesnt seem to want to work..

---

### Post by Serangan on 2009-08-05
Ok, the way it works, is this;

You set the thresholds to your desired setting.
Sample times, change if you wish, maybe 5 seconds is a better option.

```
# Check CPU usage defined as non-idle time.
CPU=`sar $CPUTIME 1 | awk '/Average/ { printf "%d\n",100-$8}'`
echo "CPU = $CPU%"
if [ $CPUTHRESH -lt $CPU ];then
    echo CPU is working, not sleeping
    exit;
fi
```

This runs a command that checks the current cpu usage, and if it is above your setting, the whole script exits and runs again later.

Same for the network usage, checks current usage, and if about your setting, exits.

```
# check for remote login
REMOTELOGIN=`last | head | grep "pts/.*still logged in"`
if [ -n "$REMOTELOGIN" ];then
    echo Remote login active:
    echo $REMOTELOGIN
    echo Not sleeping
    exit;
fi
```
This is my favorite bit, say your ssh'd into your server from outside your network, this checks if anyone is logged in, and if so, it stops, thus the server wont go to sleep.


The last bit is self explanatory. 

Also, it requires sysstat to be install, the script to be executable
```
 sudo apt-get install sysstat 
```
```
 sudo chmod +x /path/to/script 
```

Should work now.

btw, this is the original site i got the script from;
[http://www.thinkwiki.org/wiki/Installing_Debian_Lenny_on_a_ThinkPad_T60#automated_sleep](http://www.thinkwiki.org/wiki/Installing_Debian_Lenny_on_a_ThinkPad_T60#automated_sleep)

---

### Post by ericab on 2009-08-05
excellent thanks for the explanation, it works! except....
the remote login feature...since byobu (screen) runs when i login remotley via SSH; it seems to stop auto_sleep from working, since byobu counts as a pts... the good news however is its always assigned "pts/2" so, is there a way i cen have the script ignore "pts/2" so it doesnt think im still logged in ?

---

### Post by weryl on 2009-08-05
So do you add the script to cron and make it execute every few seconds..?

---

### Post by ericab on 2009-08-05
> **ericab said:**
> excellent thanks for the explanation, it works! except....
the remote login feature...since byobu (screen) runs when i login remotley via SSH; it seems to stop auto_sleep from working, since byobu counts as a pts... the good news however is its always assigned "pts/2" so, is there a way i cen have the script ignore "pts/2" so it doesnt think im still logged in ?

ok, i posted too soon, as ive found a solution.
basically, for the remote login section, ive inverted the results first grep request to exclude a certain pts, and then re-verted it by piping it through grep again, see below:

REMOTELOGIN=`last | head | grep -v "pts/2.*still logged in" | grep "pts/.*still logged in"`

---

### Post by Serangan on 2009-08-06
> **weryl said:**
> So do you add the script to cron and make it execute every few seconds..?

Yep, i've got it set so that it only runs if no other nodes are on.

But, you could set it to run every 5 mins (possibly too often?) Your Choice.

> 
ok, i posted too soon, as ive found a solution.
basically, for the remote login section, ive inverted the results first grep request to exclude a certain pts, and then re-verted it by piping it through grep again, see below:

REMOTELOGIN=`last | head | grep -v "pts/2.*still logged in" | grep "pts/.*still logged in"`

Glad to see that its working for you.

---

