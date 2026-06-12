---
title: "OpenDNS (a safer way to surf the net)"
date: 2007-06-29
forum: Ubuntu Christian Edition
---

### Post by alaaji on 2007-06-29
Hello my fellow CE users,

I just wanted to let all of you guys concerned about adult sites know about a free service that I stumbled upon sometime back.  I didn't think about posting about it here until recently. 

It's called [OpenDNS]("http://www.opendns.com") (not really open source).  It protects you from phishing sites, it is faster (for some people) than using the dns that comes from your isp, it's smart (it corrects your typos) and it has adult site blocking.

All you have to do is replace your isp's dns addresses with theirs by following these instructions for [ubuntu]("http://www.opendns.com/start/ubuntu.php") or these instructions if you have a [router]("http://www.opendns.com/start/home_network.php").  Sign up for an account and configure the options to block all of those nasty sites on the net.  Good for you and your family.

I don't work for them so sorry if this sounds like some sort of advertisement.  :D

---

### Post by mikkebe on 2007-09-17
Thank you for bringing this to my attention. I have been fighting the so called "adult" sites for a long time. I found that somethings got through dansguardian and didn't figure out how to update the blacklists. I put opendns on my wireless router and sofar have been pleased to have it along with dansguardian on my Ubuntu CE machine and K9 on my windows machine. Thanks again.:)

---

### Post by refdoc on 2007-09-19
It blocks indiscriminately a whole lot of stuff. I used it exactly for 30 mins and then I was fed up.

---

### Post by alaaji on 2007-09-22
Well, you can make it block as much or as little as you want.  There are several settings.  The thing I like the most is because of their DNS settings, I seem to be able to surf faster and block nasty stuff at the same time.  Many people who use it can attest to the same thing.

---

### Post by shane2peru on 2008-02-15
I know this is an old post, but I really like opendns, and to make it auto update your ip address.  If you need help with this just post here and I will do the best I can to help you get setup.  First in the terminal (or from synaptic) install ddclient like this:
(terminal method)
```

sudo aptitude install ddclient
``` 
In synaptic just search for ddclient and select it to install.

When it installs it is going to ask you for a bunch of setup stuff.  You can fill it out to the best of your knowledge just as practice, but really it doesn't matter we are going to delete the configuration, and put our own.  I'm about 90% sure if you have an opendns account that the [www.dnsomatic.com](www.dnsomatic.com) web site uses the same log in details.  Mine are the same.  Next in the terminal (this time we are going to need the terminal) paste this:
```

sudo gedit /etc/ddclient.conf

```

When it opens erase everything and paste this:
```

##
## DNS-O-Matic account-configuration
##
use=web, web=myip.dnsomatic.com
server=updates.dnsomatic.com,      \
protocol=dyndns2,                  \
login=[COLOR="Red"]your account user name[/COLOR],                 \
password=[COLOR="Red"]your password[/COLOR]                 \
all.dnsomatic.com


```
Replace the red with your account user name and your password.  
Save it and close it.

Now if you want this to update every hour once again in the terminal paste this:
```

sudo ln -s /usr/sbin/ddclient /etc/cron.hourly/opendns

```  This will automatically run the ddclient updater every hour and keep your IP address up to date in opendns to keep you filtered.  You may want to log into your dsnomatic.com account and just make sure that it has been updated after about 2 hours.  

Hope this helps.  If you need help with anything, I"m hijacking this thread to help with opendns setup.  Personally I like it better than Dan's guardian as it runs faster than Dan's Guardian.  

Shane

---

### Post by chuckn on 2008-02-16
Shane,

Does this work with opendns, or do I have to sign up with another service too?

Blessings,
Chuck

---

### Post by shane2peru on 2008-02-16
> **chuckn said:**
> Shane,

Does this work with opendns, or do I have to sign up with another service too?

Blessings,
Chuck

Chuck,

I'm about 90% sure that dnsomatic is a part of opendns.  Soooo, if you have an account with opendns try and use the same username and password to log into [www.dnsomatic.com](www.dnsomatic.com)  If that does work please let me know so that it will ease my 10% doubt. :)  If it doesn't post back too, and let me know.  Actually dnsomatic works with several different services, however opendns, is all I'm really concerned about.

Shane

---

### Post by alaaji on 2008-02-18
Great addition to this thread.  Thanks a lot Shane!

---

### Post by shane2peru on 2008-02-18
> **alaaji said:**
> Great addition to this thread.  Thanks a lot Shane!

No problem, glad to be of help. 

Shane

---

### Post by BiggoCharley on 2008-02-18
I followed the above --apparently successfully except when I run ddclient I get an error message "unable to determine IP address".  Any idea why this would happen?  Am I missing something in the configuration?
Charley

Since I posted this I discovered a simple syntax error in my config file which was causing my problem.  Thanks to shane2peru for the info.  I had been using DirectUpdate on my windowsXP machine and have been having some problems with it.  DNS-o-matic seems to work a lot better.  Thanks again.

Charley

---

### Post by shane2peru on 2008-02-18
> **BiggoCharley said:**
> I followed the above --apparently successfully except when I run ddclient I get an error message "unable to determine IP address".  Any idea why this would happen?  Am I missing something in the configuration?
Charley

Since I posted this I discovered a simple syntax error in my config file which was causing my problem.  Thanks to shane2peru for the info.  I had been using DirectUpdate on my windowsXP machine and have been having some problems with it.  DNS-o-matic seems to work a lot better.  Thanks again.

Charley

Glad you were able to get it to work!  They have a way to get it to work for Windows too, but you have to visit the Forums or support of the OpenDNS web site.  Glad you got it working in Ubuntu!

Shane

---

### Post by TravMan63 on 2008-03-03
This was SOO much easier than kicking Dan's Guardian into 'working mode' again.  AND as a BIG benifit - I made the changes to my SBG900 Motorola Modem/Wireless/Gateway - and it works on ALL the pc's - ALL the OS's (SAM,elive, Ubuntus, DSL (even running in a VPC in XP) , XP pro.... and I'm guessing it works on the MAC (OSX) and win 98 too).

The only 'con' I can see in my situation is I had to turn off the DHCP client in the Moto modem - (to be able to manually enter the DNS IP's) - so I may need to turn reenable that 1st (someone else may receive that IP address from my ISP after I power down...) , then re-enter the new IP address(s)...

Big advantage is ---  ONE setup - ALL computers!

[CENTER]:KS Thank you Thank you Thank you! :KS
====================[/CENTER]
I did install the ddclient on one ubuntu setup - but that was not necessary.

---

### Post by izak on 2008-06-21
Hi

First of all, thanks for the info; this is just what I need! However, I can't seem to get the system working.

I,ve registered at OpenDNS, replaced my DNS server IPs on my router with theirs, enabled dynamic IP on my account and installed ddclient according to your instructions. I think there is some kind of problem with getting my IP address right. 

When I create an account at OpenDNS, it detects my IP adress as 41.243.31.108. However, when I navigate away from the 'dashboard' area of the OpenDNS website, my IP (displayed in the top right) changes to 198.54.202.214. Aslo the IP ddclient delivers to dns-o-matic is 41.243.31.108. 

If I run ifconfig I get:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:f5:cc:cb  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fef5:cccb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8870293 (8.4 MB)  TX bytes:1824514 (1.7 MB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138100 (134.8 KB)  TX bytes:138100 (134.8 KB)
```

Where is this IP-address supposed to live? My DSL router establishes the PPPoE connection so is it the router's IP that openDNS is seeing? 

Also what is the best way to test if this is working? I set my settings to block pornographic sites, but if I try to access known blacklisted sites, such as playboy, no blocking happens :(.

---

### Post by izak on 2008-06-21
OK, this is strange. When I can go onto the stats part of the OpenDNS dashboard I can see it registered that I tried to access the blocked domains. But yet it did not stop me from accessing them?

Any ideas?

---

### Post by ceuser on 2008-07-01
Please try ScrubIt.com DNS for no-registration adult content filtering.

---

### Post by theophile on 2008-07-08
How does the ScrubIt filter differ from the OpenDNS adult content filter? Has anyone done a comparison?

---

### Post by izak on 2008-07-17
Some feedback: this does not work if your ISP uses a proxy to connect to the internet (which is appernetly the case for the majority of South African ISPs).

---

### Post by nitep on 2008-07-20
Have you looked at:-
[http://ubuntuforums.org/showthread.php?t=566698&highlight=block+pornography](http://ubuntuforums.org/showthread.php?t=566698&highlight=block+pornography)

---

### Post by dppowell on 2008-07-21
OpenDNS has posted their own ddclient config:

[http://www.opendns.com/support/article/192](http://www.opendns.com/support/article/192)

---

### Post by Cyclops_ on 2008-07-23
Of course, the one thing with this solution that I am curious about is content filtering.  DansGuardian does a fantastic job with that in my opinion.  Even if a site gets past the block, DG will pick up the content, sift through it, and OK or deny based on the content.

I don't see anywhere that indicates OpenDNS provides any service like this.

That said, I still think that OpenDNS is a pretty cool concept for sure!  I signed up for it, and hope it works well.  I think the best strategy is to use the 2 in conjunction with each other.

Just my 2 cents

---

### Post by nitep on 2008-07-25
> **dppowell said:**
> OpenDNS has posted their own ddclient config:

[http://www.opendns.com/support/article/192](http://www.opendns.com/support/article/192)

If you have trouble with it, then try Inadyn. I have had no trouble with Inadyn for the last 2 years with 6.04,7.04 and now 8.04

---

### Post by JPWhite on 2008-08-09
One alternative to making changes to a client PC is to (if your router supports it) flash your router with DD-WRT firmware and have the router do the DDNS stuff. DD-WRT is a small Linux system that runs on your router!

For supported routers visit
[http://www.dd-wrt.com/wiki/index.php/Supported_Devices]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices")

In addition to doing DDNS it also support wake-on-lan, so you can access your router remotely, switch your computer on, access it then switch it back off, all from anywhere in the world. ('course it can be locked down to stop any Tom, Dick and Harry from doing this).

---

### Post by degarb on 2011-02-05
This thread is 3 years old, and several things do not make sense.  Firstly, several spells are given without full explanation.  More firstly, we don't wish to run this--ever.  We simply wish this to start silently on startup with no sudo user intervention.  How?  Never said. 

>>Make sure SSL is enabled at the top of the configuration (ssl=yes # use ssl-support.)Where?  Why not in example?



>>For turning on the Updater, use: sudo /sbin/chkconfig ddclient on>>For starting the Updater, use: sudo /sbin/service ddclient start 
  
Again, I don't want to turn on, and I don't need kid entering the password to get own filter working!!!  INsufficient info.

>>sudo ln -s /usr/sbin/ddclient /etc/cron.hourly/opendns
Is this still valid?  Does this stick when you reboot?  Sudo less?

I hate to repeat my self, but the windows solution is one click and no editing. While I give credit that opendns doesn't have to write a linux program, since something exists.  Problem is figuring it out.

---

### Post by My_World on 2011-02-14
You are complaining about too little information and yet I cannot make head or tail of your post?

The instructions are spot on and works 100% just like given in some of the earlier posts.
SSL is nice to have, but not a must, and you can enter it into the file exactly like it is stated:

[https://www.dnsomatic.com/wiki/ddclient](https://www.dnsomatic.com/wiki/ddclient)
> 
We suggest enabling SSL at the top of the configuration (ssl=yes # use ssl-support.) 

So, at the top of the file (or just below the comments if you want it all grouped nicely) just add that line:
ssl=yes # use ssl-support

Just do exactly what this post says:
[http://ubuntuforums.org/showpost.php?p=4337468&postcount=5](http://ubuntuforums.org/showpost.php?p=4337468&postcount=5)

Unless the other users have sudo access you have nothing to worry about.

This has to be the easiest solution ever, I cannot believe I only now saw it, thanks for sharing!

---

### Post by degarb on 2011-02-14
Are there logs telling you if it works or not?  All I got was complaints of user name.  In windows, there is a trayicon (can be run invisibly) with update status, and no complaints.  (I am still trying to google ln to see what cron and ln do.)

---

### Post by My_World on 2011-02-14
ln is the command to link one path to another, in Windows terms it would almost be like "create shortcut".
ln -s means that you are creating a symbolic link from /usr/sbin/ddclient (the executable) to /etc/cron.hourly/opendns
For all intents and purposes /etc/con.hourly/opendns is then a shortcut to /usr/sbin/ddclient

Explaining cron is going to take a bit more time, have a read here:
[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

In a nutshell, it allows programs and services to be run at specific set times.

Run ddclient from a terminal window:
/usr/sbin/ddclient

And see if there are any errors. If it complains about your username then you have it wrong or there is a syntax error. Notice in the post I linked to that there is a comma ( , ) after the username, do not forget that!

The easiest way to see if it works is to test by trying to enter a forbidden/filtered site. You will immediately see an OpenDNS error message warning you that this site is being blocked.

To be on the safe side, let me walk you through this without leading you into unnecessary temptation.
In OpenDNS after you have logged in, click on dashboard and then click on settings.
Click on your IP address and under "Manage individual domains" enter a safe site here that you do no mind getting blocked, something like:
bing.com

Add it and wait around 5-10 minutes for everything to get updated.

Now each time you want to know if ddclient is working without taking risks, just try and access [www.bing.com](www.bing.com). If the normal page displays then your ddclient isn't updating your IP correctly, if it is blocked then you know it is working.

Without getting technical this is a safe way to test and see if it works correctly.

---

### Post by degarb on 2011-02-14
Thanks MyWorld!  You deserve a donut or something for that post.  Thanks again. Will fully test later, when I get the chance.

---

### Post by TreyKerux on 2011-02-16
I love OpenDNS, we used it up until we moved, and I haven't had time to reconfigure it for our new isp/router set up.

---

### Post by Dan Lucier on 2011-02-21
I just started using OpenDNS at the high school where I teach. Mostly, I'm trying to block pornography and Facebook. So far, it seems to work well on Facebook; I have tried several common workarounds. It is not so successful with pornography. Sure, if you try to go to a pornographic website, you will be blocked, but image searches still bring you to the pictures. 

I tried blocking "Visual search engines" but this does not work either; all you need to do is do a regular web search in Google and then select images. Anyway my students need to be able to use Google Images for legitimate purposes. Is there anyway to truly block pornography?

---

### Post by warroomcbw on 2011-03-06
Just changed my router over to opendns.  Completely painless, and trouble free.  Also faster.  I have charter internet and never had problems anyway.  But this change gave me better "speedtest.net" ratings.  I am in no way a very knowlegable person in this field, but I just wanted to protect my sons and family.  I have peice of mind now. (not that I didn't with Dansgardian)  I run three ubuntu OS and two Windows systems and it protects all of them.  I am pretty pleased. I asked a lot of questions then took a gamble and just did it (I copied all the info first so I could put it back if I needed to)  This is just in case someone is on the edge.  My results are fantastic.  Thanks for bringing it up in the post.
God Bless
CBW

---

### Post by shane2peru on 2011-03-08
> **Dan Lucier said:**
> I just started using OpenDNS at the high school where I teach. Mostly, I'm trying to block pornography and Facebook. So far, it seems to work well on Facebook; I have tried several common workarounds. It is not so successful with pornography. Sure, if you try to go to a pornographic website, you will be blocked, but image searches still bring you to the pictures. 

I tried blocking "Visual search engines" but this does not work either; all you need to do is do a regular web search in Google and then select images. Anyway my students need to be able to use Google Images for legitimate purposes. Is there anyway to truly block pornography?

Hmm, I'm not sure about that.  I'm assuming you are on Ubuntu, you can try Dan's Guardian.  That may do better.  I'm not 100% sure about setting it up and all though.

Shane

**EDIT:**  Here is a link on setting up Dans Guardian:  [https://help.ubuntu.com/community/Servers/DansGuardian](https://help.ubuntu.com/community/Servers/DansGuardian)

[https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian)

Hope that helps.

Very nice easy setup method.  - [http://www.liberiangeek.net/2010/03/how-to-filter-web-contents-with-danguardian-in-ubuntu/](http://www.liberiangeek.net/2010/03/how-to-filter-web-contents-with-danguardian-in-ubuntu/)

---

### Post by frank cox on 2011-06-29
> **refdoc said:**
> It blocks indiscriminately a whole lot of stuff. I used it exactly for 30 mins and then I was fed up.

You can set the preferences , blacklist and whitelist

---

