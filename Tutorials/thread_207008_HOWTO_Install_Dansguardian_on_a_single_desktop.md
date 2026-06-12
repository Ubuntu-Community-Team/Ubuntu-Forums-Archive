---
title: "HOWTO: Install Dansguardian on a single desktop"
date: 2006-07-01
forum: Tutorials
---

### Post by tonhou on 2006-07-01
Dansguardian does an outstanding job of web content filtering to protect from rubbish on the internet. This howto is a synthesis of information taken from:
[http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)

** Edit ** 25th November 2009 Please see final pages of this thread (Pages 13-14) for adaptions/updates to this howto for Ubuntu 9.10 (Karmic) and in particular issues with Karmic version of Dansguardian. Also a deb that is available to automate much of this.

**Setting up Dansguardian using Tinyproxy and Firehol on Ubuntu/Edubuntu**

1.    Ensure "universe repository" is activated and install packages:
	[I]sudo apt-get update
	sudo apt-get install dansguardian tinyproxy firehol[/I]

Note: will probably need to reinstall dansguardian to overcome clamav config errors.

2.   Edit:	**sudo gedit /etc/dansguardian/dansguardian.conf** 

a) Add comment (#) to: 
[I]#UNCONFIGURED
[/I]
b) Turn off virus checking (if not wanted):
*virusscan=off*

c) Check that the following are set:
[I]filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128[/I]

d) Save & exit.

e) Run:  
		**sudo dpkg-reconfigure dansguardian**

3.    Edit: 	[B]sudo gedit /etc/firehol/firehol.conf
[/B]
Add all of the following at the start of the document:

[I]iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept
#server webcache accept[/I]

Note: will need to remove "interface any world . . ." further on in the document.
Note: uncomment "server webcache accept" if this dansguardian system is going to filter others on a network BUT do not then connect directly to the internet as this is opening it wide open for anyone to access!

4.   Edit:	**sudo gedit /etc/default/firehol**

*START_FIREHOL=YES*

This is to allow restarting of the firewall.

5.   Edit	[B]sudo gedit /etc/tinyproxy/tinyproxy.conf
[/B]
Change/add the following lines (by scrolling through the document):
[I]User root
Group root
Port 3128
ViaProxyName "tinyproxy"[/I]

6. Restart each program:

[I]sudo /etc/init.d/tinyproxy restart
sudo /etc/init.d/firehol restart
sudo /etc/init.d/dansguardian restart[/I]

7. Dansguardian should now be operational blocking objectional sites using any browser! :grin:

**** EDITED INFORMATION **** I have edited this to include the use of these instructions for not only a single desktop but also for other systems (including Windows boxes) to point to such a configured box on a network and be filtered. This requires the addition of the last line in firehol.conf as above "server webcache accept".

The other systems must have their proxy settings set in the browser to point to the ip address of the dansguardian system and port 8080. 

**In Firefox:**
Edit -> Preferences -> General -> Connection Settings -> Manual proxy configuration

Check manual proxy configuration and add &#8220;your DG box ip address&#8221; in first box and &#8220;8080&#8221; in second
Then tick &#8220;Use this proxy server for all protocols&#8221;

These settings can be locked, instructions are available below to do this:

Modify the file **sudo gedit /usr/lib/firefox/firefox.cfg (sudo gedit /usr/share/doc/firefox-3.5/firefox.cfg) - for Firefox 3.5** 

by adding the following:

lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", 8080);
lockPref("network.proxy.type", 1);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1");

PLEASE NOTE: The dansguardian system that is doing the filtering on your network using this configuration CANNOT be connected directly to the internet - very important!!

---

### Post by shanepardue on 2006-07-05
wow!! thanks for that howto!! i've been looking everywhere for that kinda thing!! you don't even need to configure the browser with the proxy or anything?

---

### Post by andytof47 on 2006-07-19
just one problem when i follow this guide my browser can't connect but things like gaim and my email programme can connect??? anyone able to help m,e?

---

### Post by Athanasius on 2006-07-19
I am having the same problem, it seems to block everything

---

### Post by tonhou on 2006-07-20
Sorry that it is not working for you guys! I'm afraid I don't really know what the issues are. It has worked for me on around 6 systems that I have set up. I have also done other enhancements - added lines to dansguardian configuration to block undesirable image searches and also locked firefox browser settings to stop use of secure proxy sites.

Could you check that each of the three programs are running. In a terminal:

ps auxf

Also you may like to look at this post where there is a similar approach with some different configuration:

[http://ubuntuforums.org/showpost.php?p=1222237&postcount=21](http://ubuntuforums.org/showpost.php?p=1222237&postcount=21)

--Tony

---

### Post by Athanasius on 2006-07-20
I am sorry, it is actually working VERY well and now I just have to tinker with the filters.  
Thenk you for the HowTo, I have been looking for someting like this for months!

---

### Post by tonhou on 2006-07-20
Glad that it is working! 

Here are some changes that I have made to filters etc. for searching images and also for stopping access to secure proxy sites.

1. Modify the file   [B]/etc/dansguardian/bannedregexpurllist
[/B]
by uncommenting (remove #) so that it looks as it is below:

#Block unfiltered options on various search engines
(^|[\?+=&/])(.*\.google\..*/.*\?.*safe=off)([\?+=&/]|$)
(^|[\?+=&/])(.*\.alltheweb.com/customize\?.*copt_offensive=off)([\?+=&/]|$)

#Block images on altavista, alltheweb, yahoo etc - as they are anonomised
(yahoo.com\/image\/)
(yimg.com\/image\/)
(altavista.com\/image\/)
(altavista.com\/video\/)

**AND/OR** modify the file   [B]/etc/dansguardian/bannedphraselist
[/B]
by adding the following:

#-----
# Google
< safesearch is off >,< about google >,< Advanced&nbsp;Image&nbsp;Search>
# Yahoo
< safesearch is off >, < images >
# Dogpile, Excite, Webcrawler
< likely to contain adult content >,< results with adult content >
# AlltheWeb
<offensive content filter is off>,<results with offensive content>
#-----

These stop adult/offensive images if safe search is turned off for an image search engine.

2. Change firefox preferences to stop use of secure proxy sites to gain access to blocked sites:

**For Firefox:**

Modify the file     [B]sudo gedit /usr/lib/firefox/firefox.cfg
[/B]
by adding the following:

lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", 8080);
lockPref("network.proxy.type", 1);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1"); 

This will lock the proxy settings in firefox preferences if it is considered necessary to block access to secure proxy sites such as :
[https://proxify.com](https://proxify.com)
(these provide an unfiltered gateway out!)

Please note that the firefox.cfg file is overwritten each time there is a firefox update!!
--Tony

---

### Post by tonhou on 2006-07-25
Another simple to setup filtering option if you use Firefox is to use the extension **blockxxx**. Unfortunately it has not been available for Firefox 1.5 but here is an updated version:

[http://cvs.linex.org/blockxxx-0.4.1-fx.xpi](http://cvs.linex.org/blockxxx-0.4.1-fx.xpi)

To install go to File -> Open File (and point to where blockxxx is downloaded to).
It seems to do a reasonable job with the default lists, but needs extra blocking URL's to stop/tighten search engine changing of preferences. I have also imported a larger list of blockable words.

--Tony

---

### Post by tonhou on 2006-08-17
I recommend the script that automatically installs dansguardian (with firehol & tinyproxy - as above) along with a smart graphical front end to change filters that has been put together by Jereme found here:

[http://www.ubuntuforums.org/showthread.php?t=237355](http://www.ubuntuforums.org/showthread.php?t=237355)

--Tony

---

### Post by cspaz on 2006-08-25
> **tonhou said:**
> I recommend the script that automatically installs dansguardian (with firehol & tinyproxy - as above) along with a smart graphical front end to change filters that has been put together by Jereme found here:

[http://www.ubuntuforums.org/showthread.php?t=237355](http://www.ubuntuforums.org/showthread.php?t=237355)

--Tony

Can you get just the gui frond end?  I've followed the above howto and have dansguardian working properly, but a gui tool for configuration would be nice.

---

### Post by tonhou on 2006-08-28
Unfortunately not (without hacking into the scripts which probably isn't what you want to do!). The only option is to use synaptic and opt to "completely remove" dansguardian, firehol, and tinyproxy then restart and start fresh with the script to do a new install.

--Tony

---

### Post by LRC on 2006-09-04
I am admitting that I am not using Ubuntu, but I am desperate. This posting is about the only one I have found regarding this topic. I am using a 2.6.17.11-shl-up-1 Kanotix kernel KDE 3.5.4 GUI. I am conected through a hub to a M$ box which is connected to a printer. I can get firehol working fine on its own, but as soon as I try to get tinyproxy and dansguardian running, all I get is DansGuardian: Error connecting to parent proxy. I read somewhere that you could run dpkg-reconfigure and it could do some of the work for you and I get chown: `dansguardian.dansguardian': invalid user. I figure it has to do with firehol, but I have no idea where I am going wrong, and the firehol site just tells you to read the readme file, which is fine if you know what you are doing and doing an advance setup, but all I want is for the internet connection, dansguardian, tinyproxy cups and samba to work. Is it at all possible to give me some aid? This is a grep of my firehol setup:
version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "proxy root"
interface any world
        policy drop
        protection strong
        client all accept
      server cups accept
#From here on is what I needed to get firehol to work without tinyproxy and dansguardian. I hope this helps with solving what I need. I do understand that this section cannot remain the same.
interface eth0 lan src "192.168.7.0/24" dst 192.168.7.151
        policy drop
        server ICMP accept
        server cups accept
        server dns accept
        server microsoft_ds accept
        server ntp accept
        server samba accept
        server ssh accept
        client all accept
interface eth0 internet src not "${UNROUTABLE_IPS} 192.168.7.0/24" dst 192.168.7.151
        policy drop
        protection strong
        server ICMP accept
        server cups accept
        server dns accept
        server microsoft_ds accept
        server ntp accept
        server samba accept
        server ssh accept
        client all accept

---

### Post by tonhou on 2006-09-22
OK I have updated the first post with instructions on how to use with other networked systems.

--Tony

---

### Post by jhigz on 2006-10-26
tonhou,

Nice howto, thank you!

You may wish to point out for those unfamiliar with the inner workings of Firefox, myself included, that the firefox.cfg file mentioned is an encoded file which Firefox can use to implement systems wide configuration variables. This file must be encoded, however, for Firefox to use it.

For additional information, see:

[http://togami.com/%7Ewarren/guides/mozlockdown/](http://togami.com/%7Ewarren/guides/mozlockdown/)
[http://archives.seul.org/seul/edu/Jan-2003/msg00049.html](http://archives.seul.org/seul/edu/Jan-2003/msg00049.html)
[http://alain.knaff.lu/howto/MozillaCustomization/locked.html](http://alain.knaff.lu/howto/MozillaCustomization/locked.html)

Thanks again.

---

### Post by tonhou on 2006-10-26
Thanks for the kind comments.

When I first began looking at locking the prefs I read up about such things but found the Ubuntu Firefox cfg is not encoded - by default it has an entry to disallow upgrading, presumably so it can only happen through the official repositories - but no it is not encoded, at least not in Dapper.

--Tony

---

### Post by scottmuz on 2006-10-28
This worked perfectly for me. Thanks a lot.

I was amazed to see it works for automagically 
all browsers.

---

### Post by hartunnoo on 2006-11-03
Is this setup suitable for a webserver? If this fine, then I can go for it. :) Any body have tried it on webserver?

---

### Post by tonhou on 2006-11-03
> Is this setup suitable for a webserver? If this fine, then I can go for it.  Any body have tried it on webserver?

Sorry, we would need to know a bit more clearly what you mean. Can you clarify what you want to do.

--Tony

---

### Post by hartunnoo on 2006-11-04
Sorry! I'm just having breakfast.
Actually I just installed Ubuntu Server 6.06LTS into CPU1. My CPU1 acting like a router. 

ISP->ADSL_modem->CPU1_NIC_eth0->CPU1_NIC_eth1->Switch_Hub->Workstations

As you can see, the above line, I have two NIC cards connected to my CPU1. So is your configuration is suitable for this type of connection?

Thank you.

---

### Post by tonhou on 2006-11-04
I think there are a few complications there if you mean installing on your cpu1. 
You can have one of your workstations do the filtering and other systems point to it as explained in the first post above, but this requires that it always be on so that other systems can access it.

There are probably more efficient ways to have a filtering system on a server using something like  [ClarkConnect]("http://www.clarkconnect.com") which will run dansguardian and offer other firewall features.

--Tony

---

### Post by hartunnoo on 2006-11-05
Thank you for reply.

I have gone through the site given and it is good.

Thanks pal

---

### Post by Nopposan on 2006-12-12
I tried the automagical script that also installs the GUI.  I much appreciate this effort, but I wasn't entirely pleased with the results on Xubuntu 6.10.  It seems to have messed up some symbolic links and I don't really know what all it did; anyway, after I ran it I couldn't play streaming audio or my audio cd's.  This isn't a complaint though; the script wasn't written with Xfce in mind and there was a clear warning that the system could be messed up by the script.  So, I'm going to go with the manual install you've posted here and, if necessary and practical for me, write a simple gui to administrate Dansguardian -- without using gambas.

Anyone have any special suggestions for Xubuntu 6.10 users on this? (I know one other person posted that the auto install script worked great with Xubuntu, but I think he was using Dapper or there was some other difference between his set-up and mine.)  Also, I'd rather that the gui lack religious references.  I don't mean to offend; I definitely think Ubuntu CE deserves credit for their focus on this and I've thanked them in another thread.  I'm just not entirely comfortable advertising Ubuntu Christian Edition to those who may not be interested in using it.

Thanks for any help you can offer, and thanks for the How-to, nanomad.

---

### Post by Greevous on 2006-12-23
Hey I've got an issue; internet connection is down a few minutes after Dansguardian was working, so I tried to restart it (/etc/init.d/dansguardian restart) and it gave me this:
```
Restarting DansGuardian: Error reading file:
Error reading file:
Error opening bannedextensionlist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf files(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration files
```

I've checked and the bannedextensionlist is there, along with dansguardianf1.conf. I don't see what the problem is...

---

### Post by tonhou on 2006-12-24
Might need some more background info. . .
Did you do the install as per the first post here? 
Have you made any other modifications? 
Is it still the same after a complete restart?

--Tony

---

### Post by azwxman on 2006-12-24
Tony,

I'm interested in installing dansguardian and appreciate the how-to.  My one question (for now) is in reference to the final NOTE in your how-to: **PLEASE NOTE: The dansguardian system that is doing the filtering on your network using this configuration CANNOT be connected directly to the internet - very important!!**

I'm running my ubuntu client as a firewall/proxy for my little home network and I just want to be clear about what you're saying.  Can you be a little more specific as to the definition of "directly connected" and why this is "very important"?

Thanks

---

### Post by Greevous on 2006-12-24
> **tonhou said:**
> Might need some more background info. . .
Did you do the install as per the first post here? 
Have you made any other modifications? 
Is it still the same after a complete restart?


Yes, I installed based on the first post. I assume there are corrections or other variations after that, but it seemed to work at first so I didn't bother reading futher. 
I haven't made any modifications besides simple values in the dansguardian.conf file, such as 1, 2, 3, etc. or on | off.
I decided to remove dansguardian, tinyproxy, and firehol for now and try again later. I don't believe I restarted completely before removing it though.

---

### Post by tonhou on 2006-12-24
> I'm interested in installing dansguardian and appreciate the how-to. My one question (for now) is in reference to the final NOTE in your how-to: PLEASE NOTE: The dansguardian system that is doing the filtering on your network using this configuration CANNOT be connected directly to the internet - very important!!

You really need a separate router or dedicated box with firewall connecting to the internet. The filtering can be done by the Ubuntu configuration with DG, firehol and tinyproxy as above. If you were to connect this system to the internet then you would be wide open to the internet because of the firehol (firewall) setting which is allowing other systems to access it (the command "server webcache accept".)

It is probably not a very tidy way to do filtering for a home network really and as mentioned to another poster above if you want one system as a gateway/server you are better to go to something like Clarkconnect.

--Tony

---

### Post by azwxman on 2006-12-25
OK.  I do have a router between my system and the modem.  And as for the "tidy-ness" factor...as it sits, this machine is my firewall/gateway/proxy already.  Plus, my network is composed of only two systems, this one included. 

Thanks for the help on this.

---

### Post by isaiah55 on 2006-12-29
What a great how to.  Thank you very much.
It works a treat on my Linux box, but (there always seems to be a but...) if I setup the proxy information for the browsers on the other machines on my network, it doesn't work.

Let me try and explain that again ;) 
If I browse from my Ubuntu box the content filtering works a charm.
However if I setup the proxy in the browsers of my other networked machines and point them to the Ubuntu box all web browsing comes to a halt for the networked machines...

Any ideas what could be the cause?

---

### Post by isaiah55 on 2006-12-29
I have isolated the problem - I think.  Unfortunately I don't know how to fix it :oops: 
Basically if I switch off the Firehol dansguardian works via the proxies from the other computers on my network.

It is probably easy to fix but being a noob with this stuff I don't even know where to start.

Thanks in advance for helping me out

---

### Post by tonhou on 2006-12-30
Firstly I am assuming you have done this:

Your other systems on the network must have their proxy settings set in the browser to point to the ip address of the dansguardian system and port 8080.

In Firefox 1.5:
Edit -> Preferences -> General -> Connection Settings -> Manual proxy configuration

In Firefox 2.0
Edit -> Preferences -> Advanced - Network Tab -> Settings -> Manual proxy configuration

Check manual proxy configuration and add “your DG box ip address” in first box and “8080” in second
Then tick “Use this proxy server for all protocols”

Secondly can you check that you have the entry in /etc/firehol/firehol.conf
 that reads: *server webcache accept*

--Tony

---

### Post by isaiah55 on 2007-01-01
Yes you are right I have done this.  The only way I can get them to work is if I switch off firehol on my Ubuntu box, otherwise I get page cannot be found all the time.  As soon as I switch off the firehol the content filtering works a treat from all my machines...

So currently I am running Dansguardian successfully but I have to have firehol off to be able to use Dansguardian from my other machines.

I hope that all makes sense

---

### Post by tonhou on 2007-01-02
And you did check that you have the entry in /etc/firehol/firehol.conf
that reads: *server webcache accept* ?

--Tony

---

### Post by isaiah55 on 2007-01-02
Thanks for your help, but yes my firehol.conf file does have that entry.
Here is my whole firehol.conf file:
```

# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8082 "root root"

interface any world
	policy drop
	protection strong
	client all accept
	server cups accept
	server webcache accept
```

I have had to use the 8082 port instead of 8080 as my web server runs on that port.

Thanks again for your help

---

### Post by tonhou on 2007-01-02
> I have had to use the 8082 port instead of 8080 as my web server runs on that port.

I think your issues will be to do with this. Sorry, I don't have time to work it through at the moment.

--Tony

---

### Post by isaiah55 on 2007-01-03
Thanks - I'll have a look into it.  I'll post anything I find :)
BTW - Probably won't get a chance to look at it now for a week or so...

---

### Post by pmdubuc on 2007-01-10
The "User's not Filtered" configuraton doesn't seem to be working for me.  I put my user name in there and it's still blocking me.  Any ideas what I might be doing wrong?  (I'm assuming that by 'user  name' it means login id name.)

Thanks,
PMD

---

### Post by tonhou on 2007-01-12
You are not doing anything wrong.

Unfortunately this is an issue that requires further tuning for it to work. It requires user authentication for the proxy server (tinyproxy). I am not sure if/how tinyproxy allows this. So there is a question mark over whether this can be done with this DG/Firehol/Tinyproxy arrangement.

I shall do some investigating on it in the next week or so and see if there is a way ahead.

--Tony

---

### Post by heyilikeyoursweater on 2007-01-23
Hey, thanks for the guide!!!

---

### Post by jantzens on 2007-01-30
I'm following the HOWTO on how to install Dansguardian. When I get to Step 2 e)...I get the following:

scott@scott-laptop:~$ sudo dpkg-reconfigure dansguardian
Password:
Stopping DansGuardian: dansguardian.
Starting DansGuardian: LibClamAV Warning: ********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.  ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html) ***
LibClamAV Warning: ********************************************************
LibClamAV Warning: ********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.  ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html) ***
LibClamAV Warning: ********************************************************
Error connecting to parent proxy
invoke-rc.d: initscript dansguardian, action "start" failed.

I've reinstalled Dansguardian, tried to reinstall clamav and libclamav, but I can't figure out how to get it to work.

Any help would be appreciated.

SJ

---

### Post by compuwiz on 2007-02-01
Is squid running?

---

### Post by tonhou on 2007-02-02
Its certainly to be hoped that Squid is not running - it shouldn't be!

Please see the the other thread where you asked the same question concerning Clamav issues.

--Tony

---

### Post by scottmuz on 2007-03-02
I setup my home PC (I only have one PC at home with no internal network) using this HowTo several months ago and it has been working great . 

Then today I found my PC really slow and noticed my broadband modems LEDs were blinking like crazy. I did a tail -f on tinyproxy log and saw it was scrolling like crazy. I was horrified to find I was being used as a proxy server by God only knows who.

I commented out "server webcache accept" in firehol.conf and this seemed to stop the external traffic. 

But now I'm a bit scared. Am I right in thinking that the way firehol is setup it allows any inbound connection on any port. My firehol.conf is:
<<
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
  policy drop
  protection strong
  client all accept
  server cups accept
#  server webcache accept

version 5
>>

I was expecting Firehol to block all inbound traffic.

---

### Post by tonhou on 2007-03-03
Sorry to hear of your unpleasant experience!

The inclusion of "server webcache accept" was at the request of many who wished to use the dansguardian box to filter other boxes on a network - it therefore had to be opened to them. I did mention the following:

"The dansguardian system that is doing the filtering on your network using this configuration CANNOT be connected directly to the internet - very important!!"

Meaning that firehol is allowing access to all and that a router or separate system should be controlling the incoming traffic.

Perhaps by default the "server webcache accept" line should be commented out!

** Have just edited the first post so that it is commented out **

Thanks for pointing out the danger of this.

--Tony

---

### Post by borris.morris on 2007-03-10
Question... If I have this setup... Internet -> Router -> Hub -> to multiple computers, one of which is the DG one, will it still work? Or would I have to have the DG box before the hub?

---

### Post by tonhou on 2007-03-11
> to multiple computers, one of which is the DG one, will it still work?

Yes, provided the other configuration conditions are met as per the first post.

--Tony

---

### Post by borris.morris on 2007-03-11
Well, I don't want to have to set all the browsers. None of the network connections would run through the box. It would just be on one of the branches of the hub. That or is there an easy way to have my router use a proxy?

---

### Post by yesdup on 2007-03-30
Hi Tonhou,

Brilliant how to. I used this previously on Mepis for my kids pc and it worked like adream. but i have moved to xubuntu fiesty as it seems to be faster on this old pII box. 

I have followed the instructions again but when i restart firehol i get a whole lot of errors and firehol fails and i can't browse "tiny proxy error" if i switch of firehol everything works and dansguardian does it's job as expected.

Can i leave it running without firehol and what are the implication of doing so. also could i install a different firewall i.e. one with a gui that i can configure for other rules and would that in turn effect dansguardian?? below is the error ouput from firehol. 

thanks for any help.

ERROR   : # 1.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -p tcp -m state '' --state NEW \! --syn -j pr_world_nosyn 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 2.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_all_c1 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 3.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_all_c1 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 4.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_irc_c2 -p tcp --sport 1024:4999 --dport 6667 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 5.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_irc_c2 -p tcp --sport 6667 --dport 1024:4999 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 6.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 1024:4999 --dport ftp -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 7.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport ftp --dport 1024:4999 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 8.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport ftp-data --dport 1024:4999 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 9.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 1024:4999 --dport ftp-data -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 10.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 1024:4999 --dport 1000:65535 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 11.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport 1000:65535 --dport 1024:4999 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 12.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 13.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 14.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 15.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 16.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 17.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 18.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 19.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 20.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 21.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 22.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A INPUT -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 23.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A OUTPUT -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 24.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A FORWARD -m state '' --state RELATED -j ACCEPT 
OUTPUT  :

---

### Post by fvillasenor on 2007-04-12
I'm trying to connect my laptop (running Ubuntu 6.10) and other PCs with Win XP , to my network.
I want to use another Ubuntu box, with DG to do web filtering.  My set up is like this:

```

[FONT="Courier New"]Internet <-> DSL Modem         UbuntuCE
             Router            <-> 192.168.10.37 (Dhcp)
             Switch                    with DG
               192.168.10.1       192.168.10.3 (Static)
                static                               ^
                                                     |
                                                     v
                                                    Switch < - > Laptop  (192.168.10.200)[/FONT]

```
The Ubuntu CE, does an excellent jot at web filtering, but only on the browser running on that machine.  The browser on the laptop does not connect to the internet, and I followed the directions in this HOWTO.  The UbuntuCE even has a dhcp server.  From the laptop I can not ping 192.168.10.3 nor 192.168.10.1 which is my modem. 

 What am I doing wrong???


FV

---

### Post by scottmuz on 2007-04-19
I upgraded to feisty and found firehol is no longer starting.

I get lots of errors like this when firehol is started.
--------------------------------------------------------------------------------
ERROR   : # 16.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A FORWARD -m state '' --state RELATED -j ACCEPT
OUTPUT  :

It seems there is some sort of iptables / firehol incompatibility from reading
[http://archives.free.net.ph/message/20070329.233325.0482996a.en.html](http://archives.free.net.ph/message/20070329.233325.0482996a.en.html)

---

### Post by jcmag on 2007-04-20
> I upgraded to feisty and found firehol is no longer starting.
I get lots of errors like this when firehol is started.

I've changed the /sbin/firehol script to use bash31 ([https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017]("https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017")). I can now start firehol without errors but the dansguardian/firehol/tinyproxy configuration doesn't work ; it works if I set firefox to use directly tinyproxy. So the transparent proxy is broken...

---

### Post by scottmuz on 2007-04-20
A solution that doesn't involve copying bash31 from an edgy system is as follows:

sudo vi /lib/firehol/firehol (replace vi with you editor of choice)
and replace all %q strings with %b.

This is what they've done in gentoo to solve the problem. 
There seems to be some confusion as to who is actually responsible for the
problem bash, firehol or iptables but at least this fixes the problem
until a proper fix comes along.

---

### Post by RyanGT on 2007-04-21
Thanks for the %q %b tip.  I was on the verge of uninstalling Feisty and going back to Dapper.  

But I am still having some issues.  This was such a nice internet filter setup for Dapper/Edgy but I am having some substantial issues with Feisty.  My firehol.conf looks like this:

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "root root"

interface any world
policy drop
protection strong

#interface eth1 home
#	server ping accept
#	server ssh accept
#	client all accept	
#	server cups accept


If I comment out the uncommented lines and uncomment the commented lines, I can get access to the internet (but unfiltered and frighteningly unprotected).  If I run it as is, firefox says it can't find any servers and I can't ping anywhere - I basically have no access.

What am I doing wrong?

Thanks,

Ryan

---

### Post by RyanGT on 2007-04-21
Sorry, I am an idiot.  I started messing with firehol.conf to try and trouble shoot this before I read the %q %b thing.  After replacing the %q's with %b's in /lib/firehol/firehol, everything is working as expected with this firehol.conf:

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "root root"

interface any world
policy drop
protection strong

#interface eth1 home
# server ping accept
# server ssh accept
client all accept
server cups accept

Basically, I had forgotten that the last two lines were part of my original firehol.conf and not something I added during the trouble shooting.

Thanks,

Ryan

---

### Post by Moso on 2007-04-25
> **scottmuz said:**
> A solution that doesn't involve copying bash31 from an edgy system is as follows:

sudo vi /lib/firehol/firehol (replace vi with you editor of choice)
and replace all %q strings with %b.

This is what they've done in gentoo to solve the problem. 
There seems to be some confusion as to who is actually responsible for the
problem bash, firehol or iptables but at least this fixes the problem
until a proper fix comes along.

Hi everbody!  :)

For me none of the proposed solutions worked...  :P

I tried first the replace "thing" and after that the copying of bash31.

I don't remember where, but I read a post of Costa Tsaousis (author of firehol) showing that the replace "thing" generates other problems.

Last I tried install a Edgy server from scratch, updated it and installed firehol.  For my surprise, it doesn't work too!  :O

---

### Post by RyanGT on 2007-04-28
This is more of a Dansguardian question, but does anyone know how when running in blanketblock mode I can have google.com on the grey list but images.google.com on the blacklist?

Thanks,

Ryan

---

### Post by NuttBoxer on 2007-05-27
I'm getting an error when Firehol is restarted.  I'm using Feisty(7.0.4).  This is my conf settings for Firehol:

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept
#server webcache accept


When I restart Firehol, this is the error that I get:

ERROR : # 1.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -p tcp -m state '' --state NEW \! --syn -j pr_world_nosyn
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 2.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_all_c1 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 3.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_all_c1 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 4.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_irc_c2 -p tcp --sport 32768:61000 --dport 6667 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 5.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_irc_c2 -p tcp --sport 6667 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 6.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 32768:61000 --dport ftp -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 7.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport ftp --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 8.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport ftp-data --dport 32768:61000 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 9.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 32768:61000 --dport ftp-data -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 10.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 32768:61000 --dport 1000:65535 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 11.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport 1000:65535 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 12.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 13.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 14.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 15.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 16.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 17.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 18.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 19.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 20.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -m state '' --state RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 21.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world -m state '' --state RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 22.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A INPUT -m state '' --state RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 23.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A OUTPUT -m state '' --state RELATED -j ACCEPT
OUTPUT :




--------------------------------------------------------------------------------
ERROR : # 24.
WHAT : A runtime command failed to execute (returned error 2).
SOURCE : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A FORWARD -m state '' --state RELATED -j ACCEPT
OUTPUT :


[fail]
I though I followed everything as shown.  What have I done wrong?

---

### Post by hungry on 2007-06-27
hi all,

I followed this tutorial, and it worked just fine , my only problem is that if I want to use checkgmail I have to use this command as root to enable checkgmail to reach my mailbox.

HTTPS_PROXY="https://127.0.0.1:8080"; checkgmail

do you know a way around this problem?

thanks

---

### Post by ushills on 2007-07-16
Has anyone got Dansguardian to work with Feisty, I have followed this how-to to the letter and when running firefox cannot access any sites, I understand that I keep the setting to direct connection in Firefox>Prefs.

Also some methods suggest transparentsquis be set to "nobody root" and some "root root" why is this.

Please help as I need to filter the net for my children.

I use standard ubuntu with fiesty, internet is on ra0.  PC connects to router - router connects to net.

Thanks

Ian

---

### Post by pianoboy3333 on 2007-07-17
I too am having a problem with this howto on feisty.

---

### Post by Jon Bn on 2007-08-11
oo

---

### Post by Jon Bn on 2007-08-11
I was able to do all of the reinstalls and reconfigures for dansgaurdian but when I tried to restart firehol it failed and displayed a long list of errors. I tried reinstalling firehol in the synaptic package manager hoping that this would reset my configurations. It didn't work. I wish there was a simplified version of dansguardian with a gui interface in the add and remove programs. Is there anyway I could get dansguardian without needing a degree in computer science?

---

### Post by mokmoki on 2007-08-29
i have installed dansguardian just fine, everything's working...

but the problem is that when i restart dansguardian (sudo /etc/init.d/dansguardian restart), it seems that the process hangs...

i can stop dansguardian just fine (/etc/init.d/dansguardian stop works flawlessly), but when i try to start it again, it just says "Starting DansGuardian: dansguardian" and it stays there forever...

does anybody know why this is happening?

---

### Post by tashi22 on 2007-08-31
I have been reading this thread and trying to install dan guardian as well.  i have some difficulties as follows

~$ sudo dpkg-reconfigure dansguardian
Password:
 * Stopping DansGuardian dansguardian                                    [ OK ] 
 * Starting DansGuardian dansguardian                                           Error connecting to parent proxy
                                                                         [fail]
invoke-rc.d: initscript dansguardian, action "start" failed.

any ideas on how to fix this? I am still quite a bit of a newbie and only recently returned to linux
 thanks

---

### Post by twells on 2007-09-03
If you get a lot of "runtime command failed to execute (returned error 2)" when starting firehol, there is a fix here:  [http://ubuntuforums.org/showthread.php?t=538543](http://ubuntuforums.org/showthread.php?t=538543)

---

### Post by Neuromacer on 2007-10-02
I have dansguardian installed however I have the following extension dpkg-new after all my files?

What have I done wrong and how can I reinstall dansguardian correctly?

---

### Post by jmehdi on 2007-10-22
I have installed Gutsy and I want to lock the Firefox proxy settings (by modifying the firefox.cfg file) but it doesn't work (It worked on Feisty)
Any idea?

---

### Post by luvdemheels on 2007-10-22
This really NEEDS to be Alot easier and more gui based. Too many simple windows apps like this for there not to be at least 1 linux app that is simple to setup and use.

Too much command line and editing by hand.

---

### Post by jmehdi on 2007-10-26
> I have installed Gutsy and I want to lock the Firefox proxy settings (by modifying the firefox.cfg file) but it doesn't work (It worked on Feisty)
I found that on Gutsy the firefox.cfg file contains one crypted line. If I add the "lockpref..." lines then firefox doesn't start ("error reading configuration file")...
If I remove the crypted line and put the lockpref settings Firefox starts but doesn't take them in account...

help please

---

### Post by pwest on 2008-01-30
> **jmehdi said:**
> I found that on Gutsy the firefox.cfg file contains one crypted line. If I add the "lockpref..." lines then firefox doesn't start ("error reading configuration file")...
If I remove the crypted line and put the lockpref settings Firefox starts but doesn't take them in account...

help please

I found the same, but managed to get it to work by byteshifting the file as explained on this page:

[http://togami.com/%7Ewarren/guides/mozlockdown/](http://togami.com/%7Ewarren/guides/mozlockdown/)

(info was found in this same thread, here: [http://ubuntuforums.org/showpost.php?p=1664722&postcount=14](http://ubuntuforums.org/showpost.php?p=1664722&postcount=14) )

That worked for me.

But now I am trying to figure out how to lockdown firefox32 on my 64bit machine. The 64bit Firefox is locked but not the 32bit.

---

### Post by pofigster on 2008-01-30
Thanks a million for a great howto!

---

### Post by emada on 2008-02-28
is there a way to force all computers on a lan to use dansguardian? is it in the firewall rules maybe?? heres my setup

0o.inet.o0
||
eth1
ubuntu/router/dan server
eth0
||
switch
/|\
network

---

### Post by jmehdi on 2008-04-25
On ubuntu 8.04 I can't lock Firefox settings with lockPref.

I've tried to update the /etc/firefox-3.0/pref/firefox.js but it doesn't work.
If I use "pref" instead of "lockPref" the setting is taken into account. 

Any idea?

---

### Post by Haarbal on 2008-05-14
Just installed Ubuntu. Works wonderful. Before I was a Debian user.
Always wanted to install an internetfilter, e.g. DansGuardian. Finally this one. Your HOWTO is perfect! Everything works! Thank you.

---

### Post by rhenrick on 2008-05-18
Thank you and God Bless!!! :):):)

---

### Post by mysteryous on 2008-05-19
I wanted to relate that I used iptables instead of firehol to get a proxy and DansGuardian to work.

The first command I used was to allow only *root,* *dansguardian,* and the *proxy* user (for Squid in my setup) to be able to access port 80 and the rest to be redirected to port 8080:
```
sudo iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -m owner ! --uid-owner proxy -m owner ! --uid-owner 118  -j REDIRECT --to-ports 8080
```
Of course, there may be no use in putting the Dansguardian user.  Remember to write in the specific users on your system.  The "-m owner ! --uid-owner root" attributes check for and relates not to redirect the root user's packets.

The second prevents access from a browser directly to the proxy on port 3128:
```

sudo iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j REJECT --reject-with icmp-host-prohibited
```

I used some ideas from:
Joe Bolin [http://www.linux.com/articles/113733]("http://www.linux.com/articles/113733")
Olli Savolainen [http://www.pilpi.net/journal/item-985.php]("http://www.pilpi.net/journal/item-985.php")

---

### Post by houms on 2008-06-20
Great howto, easy to install.. Works like a charm with Sidux 32bit version...Too bad the DGGUI is not available as a separate package. Though I don't mind administering from CLI, it would be nice to have a gui to offer to people who want this functionality but lack the knowledge of the command line.

---

### Post by jmehdi on 2008-06-20
> it would be nice to have a gui to offer to people who want this functionality but lack the knowledge of the command line.

Try WebStrict: [http://www.ubuntume.com/webstrict]("http://www.ubuntume.com/webstrict")

To install it: 

```
gksudo gedit /etc/apt/sources.list
```

Add the following lines at the end of the file: 

```
deb http://ppa.launchpad.net/ubuntume.team/ubuntu hardy main 
deb-src http://ppa.launchpad.net/ubuntume.team/ubuntu hardy main 
```

Save the file and close the editor.
Then:

```
sudo aptitude update
sudo aptitude install webstrict
```

---

### Post by houms on 2008-06-20
> **jmehdi said:**
> Try WebStrict: [http://www.ubuntume.com/webstrict]("http://www.ubuntume.com/webstrict")

To install it: 

```
gksudo gedit /etc/apt/sources.list
```

Add the following lines at the end of the file: 

```
deb http://ppa.launchpad.net/ubuntume.team/ubuntu hardy main 
deb-src http://ppa.launchpad.net/ubuntume.team/ubuntu hardy main 
```

Save the file and close the editor.
Then:

```
sudo aptitude update
sudo aptitude install webstrict
```

Thank you for the suggestion, I really appreciate it. Couple of questions though. Though I like ubuntu, I'm primarily a debian/sidux user, and wanted to know if webstrict can be installed on sidux using the steps you outlined... Obviously I would need to modify the commands for sidux, but is webstrict just a front-end to Dansguardian? Similar to what the ubuntu CE has? If so, I assume I can just add the repository to my sources.list and install it as you mentioned. Assuming it creates a menu and such... Is this something that i can install on top of my existing setup (which is based on the tutorial at the beginning of this thread). Again thanks for your response(s).

---

### Post by jmehdi on 2008-06-20
Yes WebStrict is just a GUI frontend to dansguardian. It is a java application so you should have java installed (better is sun-java-6)

Following the steps I described should be fine, if you don't find the menu  you can launch the app in a terminal by typing "webstrict".

Tell me if it works.

---

### Post by houms on 2008-06-20
Okay installed it. It did not create a menu but i can open it by issuing the following command;
kdesu webstrict (i use kde)
the gui looks great but I do not think it is working. Couple of things I noticed...
i tried testing it by trying to add yahoo.com to the blocked site and url list..(i forget which one is for the whole site vs part of a site) nonetheless... yahoo is still accessible... not sure if the settings are being added to dansguardian config. In reading the FAQ, it appears that it only supports firefox? which is strange because the filtering i setup using the tutorial works across all browsers(iceweasel and konqueror). So i'm not sure what webstrict is referring to. but when i try to lock/unlock the firefox settings in webstrict, it keeps telling me that it does not find firefox on my system....
So yes the install works, but the program itself does not appear to be making the changes accordingly... Unless I dont know how to use webstrict correctly...
If you have any suggestions, it would be greatly appreciated.

---

### Post by jmehdi on 2008-06-20
> i tried testing it by trying to add yahoo.com to the blocked site and url list..(i forget which one is for the whole site vs part of a site) nonetheless... yahoo is still accessible... not sure if the settings are being added to dansguardian config

Did you restart the dansguardian service? (open the log to see if there are errors). You can check if the config files are well updated by opening them directly from /etc/dansguardian folder.

> i setup using the tutorial works across all browsers(iceweasel and konqueror). So i'm not sure what webstrict is referring to. but when i try to lock/unlock the firefox settings in webstrict, it keeps telling me that it does not find firefox on my system....
If you configured dansguardian for all browsers no need to use the lock/unlock button.

---

### Post by houms on 2008-06-20
i did restart the service using the restart button on the webstrict interface....
It appears that it is creating a seperate installation... by that i mean here is what my /etc/dansguardian directory looks like prior to installing webstrict;
# ls
authplugins      dansguardian.conf    downloadmanagers  [COLOR="Red"]lists[/COLOR]
contentscanners  dansguardianf1.conf  languages

now the bannedsiteslist or bannedurlist is in the /[COLOR="red"]lists[/COLOR] directory above...so i can go in there and for example put yahoo.com on the bannedsiteslist and restart dansgaurdian and yahoo is blocked. 

But after installing webstrict, my directory looks like
authplugins             blacklists  
dansguardian.conf       lists                  dansguardianf1.conf     languages             exceptionphraselist     logsitelist
bannedextensionlist     contentregexplist       exceptionregexpurllist  logurllist
bannediplist            contentscanners         exceptionsitelist       phraselists
bannedmimetypelist      downloadmanagers        exceptionurllist        pics
bannedphraselist        exceptionextensionlist  filtergroupslist        urlregexplist
bannedregexpheaderlist  exceptionfilesitelist   greysitelist            weightedphraselist
bannedregexpurllist     exceptionfileurllist    greyurllist
bannedsitelist          exceptioniplist         headerregexplist
bannedurllist           exceptionmimetypelist   logregexpurllist

If i then use webstrict to add yahoo.com to the bannedsiteslist. it puts it in the /etc/dansguardian/bannedsiteslist, which as I am understanding it... this change should be showing up in the /etc/dansguardian/lists/bannedsiteslist. 
So i think this is why when using webstrict it does not work... because the changes are not being made to the proper file(s)... not sure if using a symbolic link of some sort can resolve this issue. Again thanks for your assistance, and any suggestions you have are greatly appreciated.

---

### Post by jmehdi on 2008-06-20
How did you install dansguardian? (using a standalone .deb file, from a repository...)

Webstrict updates files in the default location of dansguardian, when it is installed from the ubuntu repository.

Also, take a look at the dansguardian.conf file, paths such as "bannediplist = '/etc/dansguardian/bannediplist'" are defined there, is there the /list subdirectory?

---

### Post by houms on 2008-06-20
installed it from the repo that you instructed....added the ppa.launchpad.net repo you mentioned to sources.list, and the apt-get update
apt-get install webstrict... 
I don't know why the directory structure is different... i have the following versions installed

dansguardian 2.9.9.4-1
tinyproxy 1.6.3-2.1
firehol 1.256-3

yes in /etc/dansguardian/dansguardian.conf
the banned and exception IP lists are pointing into the /etc/dansguardian/lists/*lists

---

### Post by jmehdi on 2008-06-20
> installed it from the repo that you instructed....added the ppa.launchpad.net repo you mentioned to sources.list, and the apt-get update
apt-get install webstrict... 
No I meant the installation of dansguardian, prior to webstrict. Anyway, the ubuntu version of dansguardian is 2.8.0.6 (in hardy), so maybe they change the config files location in 2.9.9.4.
The 2.9.9.4 version is available in the ubuntu intrepid repos, I'll test it when I have time.

So, if you modify the dansguardian.conf file by removing the 'list' subfolder for all paths, does it work?

---

### Post by houms on 2008-06-20
Okay I think I made a mistake because I retested the install and this time it didnt create any new directories, at least not as i stated earlier...my *ls* output for /etc/dansguardian after webscript is 

 authplugins dansguardian.conf downloadmanagers lists
contentscanners dansguardianf1.conf languages

I can open webscript and again using the same example as last time yahoo does not get blocked. So I'm not sure where webscript is placing these "lists" files....currently the versions i mentioned previously are installed plus the webscript package from launchpad, and the above is what my /etc/dansguardian has. I know dansguardian is working properly as i mentioned earlier, but i'm curious as to where webstrict is looking for the "lists".I assume its where the ubuntu version places them. I appreciate your time and efforts. Hope your results yield some progress. I wil keep you posted on my end if i figure anything out.

---

### Post by jmehdi on 2008-07-01
I've updated WebStrict to check where config files are (in /etc/dansguardian or /etc/dansguardian/lists). The new version is available in our repository. Please give it a try and tell me if it works.

---

### Post by houms on 2008-07-01
> **jmehdi said:**
> I've updated WebStrict to check where config files are (in /etc/dansguardian or /etc/dansguardian/lists). The new version is available in our repository. Please give it a try and tell me if it works.

I can confirm that it is working with sidux now.... This is a great way for non-techies to take control of this wonderful content filter..Thanks for all your efforts jmehdi. Great work... 

I have one note to make though. If you want to stop the filter completely for whatever reason(maintenance,etc). just stopping dansguardian/tinyproxy using webstrict's "stop" button will render your web useless. The reason seems to be that firehol is still running. so to completely stop filtering but still use the net(unfiltered), I had to issue
/etc/init.d/firehol stop 
in addition to using the stop button in webstrict. Not sure if it would be possible to add firehol to webstrict.?by that i mean have the stop, start, and restart buttons control firehol as well. Also I have Iceweasel RC2 instead of firefox installed. The firefox button (lock and unlock) says firefox is not installed on this system when pressed. Not so sure if its necessary to have the functionality in this setup, since the tutorial filters no matter what browser your using. Any opinions on this would be greatly appreciated. 
Thanks again jmehdi.

Also the access log buttons do not work.

---

### Post by jmehdi on 2008-07-01
> I can confirm that it is working with sidux now.... This is a great way for non-techies to take control of this wonderful content filter..Thanks for all your efforts jmehdi. Great work...
Great :D  And thanks to you for your feedback and your suggestions to improve webstrict.

> Not sure if it would be possible to add firehol to webstrict.
I've uploaded a new version ; I check if the services are installed (dansguardian, tinyproxy, firehol) and the start/stop/restart buttons manage them all. Please give it a try.

> The firefox button (lock and unlock) says firefox is not installed on this system when pressed. Not so sure if its necessary to have the functionality in this setup, since the tutorial filters no matter what browser your using. Any opinions on this would be greatly appreciated.
This button works only with Firefox 2.0, and in your case, as you use firehol, it is useless. Maybe I'll remove it in future versions.

> Also the access log buttons do not work.
Does this file exist: /var/log/dansguardian/access.log ?

---

### Post by houms on 2008-07-01
Your welcome Jmehdi. I really appreciate you taking out the time and effort to make these modifications. Another reason why OSS is so brilliant. Please let me know if i can help with anything. Seriously, I just want to get involved as much as possible.

Damn jmehdi you move fast... Yep the new version definitely works with sidux... Now stop start and restart buttons are working flawlessly. Thanks homie.

Thanks also for replying to the firefox question. Thats what i figured that it was useless for this tutorial. It would be nice to see a webstrict version for the tutorial(without the firefox buttons since the tutorial filters regardless of browser used). it would be nice but I don't think its a must since this version works so well. 

In reference to the log buttons.
/var/log/dansguardian shows the following files;
access.log access.log.1 access.log.2

---

### Post by jmehdi on 2008-07-01
> **houms said:**
> 
In reference to the log buttons.
/var/log/dansguardian shows the following files;
access.log access.log.1 access.log.2

Strange, in my code I just check if the "/var/log/dansguardian/access.log" file exists and open it. Do you have a specific error?
For the HTML log files you should have files in "/var/log/dansguardian/html"

---

### Post by houms on 2008-07-02
> **jmehdi said:**
> Strange, in my code I just check if the "/var/log/dansguardian/access.log" file exists and open it. Do you have a specific error?
For the HTML log files you should have files in "/var/log/dansguardian/html"

I don't get any errors. The buttons don't do anything. by that I mean when pressed nothing happens... The access log when listed as text neither buttons do anything.... I do not have /var/log/dansguardian/html
my /var/log/dansguardian/access.log does show entries.

---

### Post by jmehdi on 2008-07-07
> **houms said:**
> I don't get any errors. The buttons don't do anything. by that I mean when pressed nothing happens... The access log when listed as text neither buttons do anything.... I do not have /var/log/dansguardian/html
my /var/log/dansguardian/access.log does show entries.

Which version of java do you use?

---

### Post by houms on 2008-07-07
> **jmehdi said:**
> Which version of java do you use?

apt-show-versions sun-java6-jre 
sun-java6-jre/sid uptodate 6-06-1


apt-show-versions sun-java6-bin
sun-java6-bin/sid uptodate 6-06-1

apt-show-versions sun-java6-plugin
sun-java6-plugin/sid uptodate 6-06-1

---

### Post by izak on 2008-10-22
Followed the instructions on the very first post and it works like a charm. Thank you very much!

---

### Post by roald on 2008-10-31
Hi!
I've been trying Ubuntu and UbuntuCE for some days, and am really impressed. Will probably switch from Windows for most of my computers. Unfortunately my kids love games that only run on Windows...

As far as I can see this thread describes how to install the same functionality as is default in UbuntuCE. I'm searching for information on something similar. What I want is:
* have all internet traffic from my home network pass through an Ubuntu installation so that the traffic will be filtered by Dansguardian, *without* having to adjust proxy-settings on the other computers in my house. Basically all traffic should pass, but if Dansguardian finds a page with bad content it should display it's normal STOP-page with a bypass-link.

I've tried with Firestarter and DHCP3-server to get the internet connection sharing. That works but then Dansguardian does not block any more.

Thankful for any thoughts on this

Roald

---

### Post by borris.morris on 2008-11-01
You have to set the gateway to that of the machine running Dansguardian. I.E. if your proxy server is 192.168.1.3 set the gateway to 192.168.1.3

---

### Post by Marc Duval on 2008-11-09
> **cspaz said:**
> Can you get just the gui frond end?  I've followed the above howto and have dansguardian working properly, but a gui tool for configuration would be nice.

I use webmin to configure dansguardian. Works very nicely.

---

### Post by TitanTiger on 2008-11-10
I'm having some trouble.  First, when I get to the part where I type:

```
sudo dpkg-reconfigure dansguardian
```

...I get this message:

```
 * Stopping DansGuardian dansguardian      [ OK ] 
 * Starting DansGuardian dansguardian

Error connecting to parent proxy
                                                                         
invoke-rc.d: initscript dansguardian, action "start" failed.   [fail]
```


I tried to just go on with the rest of it and hope it would come together at the end, but when I run the restarts of all three, dansguardian and tinyproxy restart fine, but firehol gives me this:

```
 * Restarting Firewall configuration                                            

--------------------------------------------------------------------------------
ERROR   : # 1.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -p tcp -m state '' --state NEW \! --syn -j pr_world_nosyn 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 2.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_all_c1 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 3.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_all_c1 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 4.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_irc_c2 -p tcp --sport 32768:61000 --dport 6667 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 5.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_irc_c2 -p tcp --sport 6667 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 6.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 32768:61000 --dport ftp -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 7.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport ftp --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 8.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport ftp-data --dport 32768:61000 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 9.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 32768:61000 --dport ftp-data -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 10.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 32768:61000 --dport 1000:65535 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 11.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport 1000:65535 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 12.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 13.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 14.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 15.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 16.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 17.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 18.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 19.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 20.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_all_c5 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 21.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_all_c5 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 





--------------------------------------------------------------------------------
ERROR   : # 22.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_irc_c6 -p tcp --sport 32768:61000 --dport 6667 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 23.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_irc_c6 -p tcp --sport 6667 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 24.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c7 -p tcp --sport 32768:61000 --dport ftp -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 25.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c7 -p tcp --sport ftp --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 26.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c7 -p tcp --sport ftp-data --dport 32768:61000 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 27.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c7 -p tcp --sport 32768:61000 --dport ftp-data -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 28.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c7 -p tcp --sport 32768:61000 --dport 1000:65535 -m state '' --state ESTABLISHED\,RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 29.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c7 -p tcp --sport 1000:65535 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 30.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 31.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 32.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A INPUT -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 33.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A OUTPUT -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 34.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A FORWARD -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 


                                                                         [fail]
```

What am I doing wrong?

---

### Post by TitanTiger on 2008-11-13
An update.  I seem to have gotten it working.  I hadn't set up the proxy settings in Firefox properly.  I still don't know what the nature of those Firehol errors are though.

---

### Post by Harry_Callahan on 2009-01-12
Hello,

working great for me! but..

firehol seems to be blocking port 64294 that I use for Azureus, I get NAT\Firewall warning on Azureus. If I do sudo firehol stop, Azureus starts working fine. How can I open port 64294? Is there something to add on:

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

from the /etc/firehol/firehol.conf file?

Opening that port could cause any problems for the filtering?

thanks

---

### Post by svanarts on 2009-01-24
Your how-to worked great, thank you!!  The only hitch I ran into was that the Ubuntu forums got blocked!:(  Easy fix, just added it to the exceptions list.  I'd like a gui too so I'm going to try webmin as another user pointed out.  Wonderful how-to thanks again!!:KS

---

### Post by dardack on 2009-01-29
I've tried reading all the posts here, and I may have missed it.

Is there a way to block anon proxies?  I know to lock firefox preferences, and obviously they can't install opera or anything without admin password.  Also, does the default block SSL or do I have to block all SSL and then whitelist like ssl I want?

Thanks for any help

---

### Post by dardack on 2009-01-29
> **svanarts said:**
> Your how-to worked great, thank you!!  The only hitch I ran into was that the Ubuntu forums got blocked!:(  Easy fix, just added it to the exceptions list.  I'd like a gui too so I'm going to try webmin as another user pointed out.  Wonderful how-to thanks again!!:KS

Yea the ubuntu forums got blocked on me as well.  Very strange, but whitelisted them.

---

### Post by semijoyful on 2009-02-13
> **svanarts said:**
> Your how-to worked great, thank you!!  The only hitch I ran into was that the Ubuntu forums got blocked!:(  Easy fix, just added it to the exceptions list.  I'd like a gui too so I'm going to try webmin as another user pointed out.  Wonderful how-to thanks again!!:KS
Just how exactly do I use webmin as a frontend for dansguardian?
Thanks!
-Kirk

---

### Post by Dirkomatic on 2009-02-13
For some reason, this command:
```
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
```

results in:
```
iptables:No chain/target/match by that name
```

I can remove the owner match and it works fine...  Any ideas why I can't get the --uid-owner to work?

---

### Post by ddigler on 2009-02-19
Thank you!! Brand new to Linux (3 days now).;) Running Ubuntu 8.10. After 15 syntax errors got it rolling lol. 10 mins total. Haven't tweaked DG at all yet but it seems to do remarkably well already.

Am I right that my son will not be able to tamper with the filter (disable/configure) without the administrator password that I used to install the aps?

Also, are my ports secure with this setup? I know very little about networking and just want to make sure that I'm secure with this setup.

---

### Post by arthritisankle on 2009-03-12
Edit:  I figured out my original question but now I have more.

How do you limit the users that are filtered?  I edited the user exception file to add the usernames that don't need filtering and they were still filtered.  IT says that authentication is necessary, but I don't know what that means.

Also, I can no longer run ushare to stream media to my xbox 360.  Any ideas?

---

### Post by Electron on 2009-03-16
Hi,

I did follow all the instruction and everything work alright :). However, there a few websites (this is one of them) that are blocked and  download files are impossible when is running. So I unistalled, restarted just to write this post looking for an answer. My question is how to configure dansquardian to blocked your pornography or is there anything that i can do to access the websites that are need. 

This computer that I am using is the one running dansguarding is connecting to the internet through a router (home network). Any help, please will be greatly appreciated.

---

### Post by Electron on 2009-03-16
HI,

I follow the instructions on how to setup the dansguarding and everything went smooth. However, there are website that are being blocked (this page is one of them), also I cannot download anything now, every file that I need to download from the web is "access denied" including mp3 files.

I had to unistalled the dansguarding, with tinyproxy, and firehol and rebbot just to put this post here. I did that because i don't know how to configure dansguardian.

I just need to block pornographic websites and related searches, i don't do gaming or anything similar, the application will be installed in this computer and connects to the internet through a router (home network).

Any help on this regard, will be  gratly appreciated.

Thanks

---

### Post by ocarinahuff on 2009-03-19
the files you need to edit are in /etc/dansguardian/lists

comment out everything in these two lists, by placing a "#" in front of every line that doesn't have one.

gksu gedit /etc/dansguardian/lists/bannedextensionlist
gksu gedit /etc/dansguardian/lists/bannedmimetypelist

Then add websites that you don't want to have blocked to this list

gksu gedit /etc/dansguardian/lists/exceptionsitelist

don't add the http:// or [www.,](www.,) do it like this:

distrowatch.com
ubuntuforums.org
utah.edu

---

### Post by Electron on 2009-03-19
Thanks for the info, ocarinahuff. I solved my problem for now using OpenDns, but I would like to go back to Dansguardian its faster than openDns ..., so I will be following your instructions later.

---

### Post by ckollars on 2009-03-24
This configuration works for single-desktop systems and for SOHO networks. But I would caution that it's not an appropriate base upon which to build a server for a larger LAN:
[LIST=1]

[*] Most often a dedicated network server has neither a GUI nor a local user. 

[*] Squid (rather than Tinyproxy) is usually paired with DansGuardian on a LAN server. Squid's caching and multi-threading offer significantly better performance. And its "auth" capabilities (which Tinyproxy does not have) are needed in some DansGuardian configurations.

[*] A network firewall server is typically a machine with two network interfaces, and DansGuardian/Squid typically runs directly on that same machine. The alternative of running DansGuardian/Squid on a machine other than the network firewall will require extra server hardware. And it's more difficult to appropriately maintain a filter without two network interfaces. 

[*] This configuration too easily interferes with other network services running on the same computer. (Other services might include a Network Addressable Storage such as Samba, or a directory service such as LDAP).
[/LIST]

---

### Post by nsales1 on 2009-05-25
I've just got DG up and running with firehol and tinyproxy and I am unable to view some sites (Facebook mainly). How do I make it so I can view this and any other sites that I use that aren't offensive but are being blocked by DG? (I'm new to Ubuntu - about 3 months of use).

---

### Post by RyanGT on 2009-05-26
You could add facebook to the exceptionsitelist or add certain pages, such as your facebook home page to the exceptionurllist.  Pretty much all DG configuration comes through editting the various lists which are in /etc/dansguardian/lists.  My excectionurllist has entries like

facebook.com/profile.php?id=1231789701

The difference between exception sites and exceptionurls is that the urls only authorize a small portion of the entire site, rather than all of facebook.

---

### Post by penguin412 on 2009-06-17
Is there a way to use Dansguardian as a transparent proxy for a network? I can't round up all the computers on my network and change the HTTP proxy and port. Thanks.

---

### Post by david_kt on 2009-07-21
> **penguin412 said:**
> Is there a way to use Dansguardian as a transparent proxy for a network? I can't round up all the computers on my network and change the HTTP proxy and port. Thanks.

I am studying that possibility, using 2 network interfaces (eth0 to wan and eth1 to lan). I will let you know if I succeed to do that.

DK

---

### Post by nowhere@cox.net on 2009-07-26
Is there a way to set up filtering based on user? Obviously, I would like a different set of filtering for parents and children and perhaps no filtering for the admin user for the system...

Thanks!

---

### Post by Mr.n on 2009-08-25
Dears,

Ubuntu is really annoying with tinyproxy and squid. I tried the exactly the above configuration but sometimes browsing is good and sometimes it is very slow and it displays blank pages. 
I tried a simple masquerading in iptables and all the websites are opening very fast however when I come back and use http proxy I see blank pages in firefox.
I have a box with 3.0 cpu 2Gb ram dedicated for ubuntu server and filtering about 6 users only in my home network. I tried both squid and tinyproxy with dansguardian but I am facing slowness problems. Is it possible to use dansguardian without an http proxy !
How can we troubleshoot this issue ?

Here are some logs from tinyproxy
CONNECT   Aug 25 12:02:59 [12145]: Request (file descriptor 7): GET [http://ubuntuforums.org/images/buttons/collapse_tcat.gif](http://ubuntuforums.org/images/buttons/collapse_tcat.gif) HTTP/1.0
INFO      Aug 25 12:02:59 [12145]: No proxy for ubuntuforums.org
CONNECT   Aug 25 12:02:59 [12145]: Established connection to host "ubuntuforums.org" using file descriptor 8.
INFO      Aug 25 12:02:59 [12146]: Closed connection between local client (fd:7) and remote client (fd:8)
CONNECT   Aug 25 12:02:59 [12143]: Connect (file descriptor 7): localhost [127.0.0.1]
ERROR     Aug 25 12:02:59 [12143]: read_request_line: Client (file descriptor: 7) closed socket before read.
INFO      Aug 25 12:02:59 [12145]: Closed connection between local client (fd:7) and remote client (fd:8)
CONNECT   Aug 25 12:03:01 [12144]: Established connection to host "ubuntuforums.org" using file descriptor 9.
CONNECT   Aug 25 12:03:01 [12350]: Established connection to host "ubuntuforums.org" using file descriptor 8.
CONNECT   Aug 25 12:03:01 [12349]: Established connection to host "ubuntuforums.org" using file descriptor 9.
INFO      Aug 25 12:03:02 [12350]: Closed connection between local client (fd:7) and remote client (fd:8)
INFO      Aug 25 12:03:02 [12349]: Closed connection between local client (fd:7) and remote client (fd:9)
CONNECT   Aug 25 12:03:02 [12148]: Established connection to host "ubuntuforums.org" using file descriptor 8.
INFO      Aug 25 12:03:02 [12144]: Closed connection between local client (fd:7) and remote client (fd:9)
INFO      Aug 25 12:03:02 [12148]: Closed connection between local client (fd:7) and remote client (fd:8)
CONNECT   Aug 25 12:03:03 [12147]: Established connection to host "ubuntuforums.org" using file descriptor 8.
INFO      Aug 25 12:03:04 [12147]: Closed connection between local client (fd:7) and remote client (fd:8)
CONNECT   Aug 25 12:03:18 [12139]: Connect (file descriptor 7): localhost [127.0.0.1]
CONNECT   Aug 25 12:03:18 [12139]: Request (file descriptor 7): GET [http://ubuntuforums.org/private.php](http://ubuntuforums.org/private.php) HTTP/1.0
INFO      Aug 25 12:03:18 [12139]: No proxy for ubuntuforums.org

---

### Post by david_kt on 2009-08-25
> **Mr.n said:**
> Dears,

Ubuntu is really annoying with tinyproxy and squid. I tried the exactly the above configuration but sometimes browsing is good and sometimes it is very slow and it displays blank pages. 
I tried a simple masquerading in iptables and all the websites are opening very fast however when I come back and use http proxy I see blank pages in firefox.
I have a box with 3.0 cpu 2Gb ram dedicated for ubuntu server and filtering about 6 users only in my home network. I tried both squid and tinyproxy with dansguardian but I am facing slowness problems. Is it possible to use dansguardian without an http proxy !
How can we troubleshoot this issue ?

Not sure if the problem is due to firehol. I have removed firehol from dansguadian GUI, may be you could try below:

[http://ubuntuce.com/repos/Ubuntu_CE/jaunty_i386/dansguardian-gui_2.2_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/jaunty_i386/dansguardian-gui_2.2_all.deb)

Launch dansguardian GUI and choose autoconfigure.

After you should edit:

/etc/init.d/ubuntu_ce_firewall

to suit your need (to share to LAN, make sure you redirect port 80 from the LAN to port 8080).


I hope without firehol it woul be faster.

DK

---

### Post by Mr.n on 2009-08-25
hey david,

thank you for your reply. i alreayd stopped firehol and i have done a port redirection form 80 to 8080 and everything was quiet working but with huge delays. if i use directly the nating in iptables the site opens in 5 seconds but if i use the proxy it will take minutes to load all the content. actually i am using ubuntu 9.04 server so it's not possible to have a gui. do we have any web interface instead?


anyway how can we debug this. the logs arn't really helpful ...

Thank you

---

### Post by scottmuz on 2009-10-24
Been running with this setup for several years with no issues.

But since I've upgraded to karmic I am getting blank pages for many sites
including ubuntuforums.org!

Not usable anymore. 

Any ideas?

I don't think the version of tinyproxy of firehol have changed so 
I suspect it may be due to the new version of dansguardian.

---

### Post by scottmuz on 2009-10-24
Definately seems to be an issue with dansguardian 2.10.1.1 in karmic
as if I go back to the jaunty version of dansguiardian 2.9.9.7
my blank pages problem is gone.

---

### Post by PocketHercules on 2009-11-05
scottmuz,

I am having the exact same issue that you are having.  No issue in jaunty.  I tried uninstalling tinyproxy and reinstalling to no avail.  Have you made any progress?

---

### Post by scottmuz on 2009-11-07
Hi PocketHercules In karmic I fixed by  

1. Uninstalling karmic dansguardian

2. Downloading the jaunty package from here
[http://packages.ubuntu.com/jaunty/dansguardian](http://packages.ubuntu.com/jaunty/dansguardian)

3 Installing the jaunty version with dpkg -i

4. Telling the package manager to hold it at this version with 
sudo aptitude hold dansguardian

I was waiting to see if it was reported by anyone else.
Now I know it wasn't just me I'll raise it on launchpad.

---

### Post by scottmuz on 2009-11-07
The issue is discussed here 
[http://ubuntuforums.org/showthread.php?t=1310351&page=2](http://ubuntuforums.org/showthread.php?t=1310351&page=2)
and has been raised on launchpad

Doesn't seem there is a solution yet other than my one.

---

### Post by dasunsrule32 on 2009-11-10
> **scottmuz said:**
> The issue is discussed here 
[http://ubuntuforums.org/showthread.php?t=1310351&page=2](http://ubuntuforums.org/showthread.php?t=1310351&page=2)
and has been raised on launchpad

Doesn't seem there is a solution yet other than my one.

I built it from source, and it works fine. Something in the deb file for Karmic.

---

### Post by smopi on 2009-11-13
Hi Everybody!


I have two PC boxes: AMD X2 64 with Ubuntu 9.10 AMD_64 and Intel Pentium D with 9.10 i386. In my case this bug appears only on the first one. Reinstalling Dansguardian from Jaunty fixes it for me.

Best regards,
Piotr

---

### Post by ant2ne on 2009-11-21
IDK if this is mentioned or not. I didn't read all 11 pages. But,
OP says > sudo gedit /usr/lib/firefox/firefox.cfg and it should be edited for > sudo gedit /usr/share/doc/firefox-3.5/firefox.cfg at least for ubuntu 9.04 with FF 3.5

---

### Post by david_kt on 2009-11-21
> **ant2ne said:**
> IDK if this is mentioned or not. I didn't read all 11 pages. But,
OP says  and it should be edited for  at least for ubuntu 9.04 with FF 3.5

The first post is belong to Tonhou, not me. As such, I could not edit it. Actually I have make a deb package to automate the whole process, which is already updated for karmic as well. You could check below:

[http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian-gui_2.3_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian-gui_2.3_all.deb)

It also will enable you to share internet sharing (if you have two network cards) or internet filtering sharing (if you haveo nly one network card) easily.

This package is made for ubuntu christian edition version.

DK

---

### Post by ant2ne on 2009-11-22
> **david_kt said:**
> The first post is belong to Tonhou, not me. As such, I could not edit it.  ahhh > Actually I have make a deb package to automate the whole process, which is already updated for karmic as well. You could check below:

[http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian-gui_2.3_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian-gui_2.3_all.deb) awesome. I wish I would have known about that before hand. Because I got the other method up and running already.> 

It also will enable you to share internet sharing (if you have two network cards) or internet filtering sharing (if you haveo nly one network card) easily. I'm not sure I understand you. You mean, it can function as an inline and as transparent proxy? I am interested in setting up an in line box to function as a dansguardian content filter, site to site VPN, firewall and a squid web cache proxy. 

Do you have any advice on how to filter with dansguardian by user? I want to filter the kids, but not the grownups.

---

### Post by AlexanderDGreat on 2009-11-30
Hi, can anybody help me?

Ever since the first post, dansguardian, tinyproxy, and firehol just filters my Server, but NOT the whole LAN network.

Here's mysetup: Internet -> modem -> router -> switch -> Server, workstation1, workstation2, etc... I'm using Ubuntu 9.04. I'm only using 1 interface card which is eth0

I've followed the guide step by step.

--------------------------
1. dansguardian.conf

#UNCONFIGURED
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128

--------------------------
2. 
sudo gedit /etc/default/firehol
START_FIREHOL=YES

--------------------------
3.firehol.conf

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept
server webcache accept
--------------------------

4. tinyproxy.conf
User root
Group root
Port 3128
ViaProxyName "tinyproxy"


If I setup the proxy in the firefox on my LAN it works, but if I don't it doesn't. Help!

---

### Post by david_kt on 2009-11-30
> **AlexanderDGreat said:**
> 
If I setup the proxy in the firefox on my LAN it works, but if I don't it doesn't. Help!

If you only have one network card, I think you have to set proxy on client computers.

DK

---

### Post by AlexanderDGreat on 2009-11-30
Hi david_kt - thanks for replying. So how can I restrict the clients from changing their proxies? Because I can't possibly get to every computer on our workplace. Also, if I just setup proxies on their browsers, wouldn't they be able to just change it right away? What're the alternatives? They're using WinXP.

---

### Post by atryus28 on 2009-11-30
Hi All, has anyone else not only had this problem but I have an extra part as well?  Updating to Karmic broke Dan's Guardian as described.  However I have an extra problem, in that, even after uninstalling dansguardian, I am unable to browse at all. If I reinstall it, I have the limited connection issue.  Does anyone know what else might be blocking pages even after uninstalling dansguardian?  At this point I am fine just not even having it any more but currently that is not an option.


Thanks in advance

---

### Post by david_kt on 2009-11-30
> **AlexanderDGreat said:**
> Hi david_kt - thanks for replying. So how can I restrict the clients from changing their proxies? Because I can't possibly get to every computer on our workplace. Also, if I just setup proxies on their browsers, wouldn't they be able to just change it right away? What're the alternatives? They're using WinXP.

1. Set the router to accept only the server, and deny other computer access.
By doing this, if the client computers remove the proxy setting, they would not have internet access.

2. Buy additional network card for the server: 1 card connect to internet, the other connect to LAN.

DK

---

### Post by david_kt on 2009-11-30
> **atryus28 said:**
> Hi All, has anyone else not only had this problem but I have an extra part as well?  Updating to Karmic broke Dan's Guardian as described.  However I have an extra problem, in that, even after uninstalling dansguardian, I am unable to browse at all. If I reinstall it, I have the limited connection issue.  Does anyone know what else might be blocking pages even after uninstalling dansguardian?  At this point I am fine just not even having it any more but currently that is not an option.


Thanks in advance

Uninstall dansguardian and all the packages you install with dansguardian (tinyproxy and firehol may be?).

DK

---

### Post by atryus28 on 2009-11-30
That's the problem, did not see that tiny proxy and firehol were part of the install.

I will give that a shot at home later.  Thank you.  I have a feeling this is the issue.  Didn't really expect an answer so quickly.  

Have a good one!

---

### Post by anupindi007 on 2009-11-30
I have quick question? seeking your help.  

I am using tinyproxy and dansgaurdian and its working fine ([http://wiki.linuxmce.org/index.php/Installing_Dansguardian_on_LinuxMCE](http://wiki.linuxmce.org/index.php/Installing_Dansguardian_on_LinuxMCE))

Tinyproxy and dansgaurdian on same system and others connecting to wireless router(DHCP).  How do i bypass  Tinyproxy/dansgaurdian for specific user using mac address(because i am getting DHCP).


Thanks in advance for the same.

---

### Post by AlexanderDGreat on 2009-11-30
Hi david_kt, thanks for the quick answer, I just allowed my Server's MAC to pass in the network. By using this, I can now filter the network. Thanks a lot my friend! :)

---

### Post by david_kt on 2009-12-01
> **anupindi007 said:**
> I have quick question? seeking your help.  

I am using tinyproxy and dansgaurdian and its working fine ([http://wiki.linuxmce.org/index.php/Installing_Dansguardian_on_LinuxMCE](http://wiki.linuxmce.org/index.php/Installing_Dansguardian_on_LinuxMCE))

Tinyproxy and dansgaurdian on same system and others connecting to wireless router(DHCP).  How do i bypass  Tinyproxy/dansgaurdian for specific user using mac address(because i am getting DHCP).


Thanks in advance for the same.
Assuming eth1 connected to LAN and eth0 connected to internet, try this on the server:
```

sudo iptables -I INPUT -i eth1 -m mac --mac-source xx:xx:xx:xx:xx:xx -j ACCEPT
sudo iptables -I FORWARD -i eth1 -m mac --mac-source xx:xx:xx:xx:xx:xx -o eth0 -j ACCEPT
```

I do not know whether or not it is working as I have not tried it before. If it is not working, may be need to add MASQUERADE.

DK

---

### Post by anupindi007 on 2009-12-09
> **david_kt said:**
> Assuming eth1 connected to LAN and eth0 connected to internet, try this on the server:
```

sudo iptables -I INPUT -i eth1 -m mac --mac-source xx:xx:xx:xx:xx:xx -j ACCEPT
sudo iptables -I FORWARD -i eth1 -m mac --mac-source xx:xx:xx:xx:xx:xx -o eth0 -j ACCEPT
```I do not know whether or not it is working as I have not tried it before. If it is not working, may be need to add MASQUERADE.

DK
Thanks for your inputs and I will check on the same.

---

### Post by ant2ne on 2009-12-27
> **david_kt said:**
> [http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian-gui_2.3_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian-gui_2.3_all.deb)
broken linky

---

### Post by david_kt on 2009-12-27
> **ant2ne said:**
> broken linky

follow instruction below:
```

http://ubuntuce.com/convert.htm

```

change

```
sudo apt-get install ubuntu-ce 
```

to

```

sudo apt-get install dansguardian-gui
```

DK

---

### Post by tgoatley on 2010-02-19
**Setup/Situation/Question/Configuration:**

**Setup:**
For now, Ubuntu 9.04 - I would love to use 9.10 but it appears that UbuntuCE is the only distro that has all of Dansguardian ready to roll (I don't mind the webmin/Dansguardian plugin but I like the CE interface...efficient, simple). Currently my experience with Ubuntu 9.10 for my configuration is that it has issue with the /etc/gdm/PostLogin/Default.sample file and I am not getting any responses to why. I was getting error messages because the file starts !#/bin/sh so I retyped it to !#/bin/bash  saved it, reran it, just for it to not kick an error message back...but, why? It still isn't working.FYI: My profiles default /bin/bash. Anyway, I'm trying. So here it goes...

**Situation:**
I have a couple of branches that use a community available wireless and I need to implement Dansguardian for their protection.
We are under development (at our library) to implement Ubuntu for our Public Internet. We need to offer levels of security to our Patrons. Aside: For our currently in use Ubuntu PCs we are using wireless (through a Bluesocket controller) and I have been pushing these PCs through our squid proxy for filtering. All is good in this world.

**Question:**
How can I get Dansguardian to function in this environment?
With the need to use separate profiles (see 1. Create multiple user profiles) how can I get Dansguardian to work for each profile.
I use timekpr to maintain time limits (set to the top of the hour) so that when the profiles are used/logged into there is only access for that time granted then it is locked. The following day with a new login and a copy of the base profile to replace the previous days profile, any and all profile data is wiped, completely.

**Here is my _*configuation*_ for 9.04**

**1. Create multiple user profiles.** 
I setup 1 profile as per our user needs that will serve as the base profile (found in /home ) for all the other profiles logging into 1 particular PC (we do have many Public PCs). I do this by being root and: cp -r someprofile base. 
Then:
**2. From /etc/gdm/PostLogin.**
I recreate the Default file from the Default.sample file. Then I add the scripting and as root run the script from the prompt $./Default

For anyone that would like this script here it is.

[B]#Script for resetting home directory
if [[ "$LOGNAME" == lnxlib* ]] ; then
        rm -rf $HOME
        cp -a /home/base $HOME
        chown -R $LOGNAME:$LOGNAME $HOME
        exit 0

else
        exit 0
fi[/B]

This allows a profile to be cleanly reloaded the next day without any trace of files created website visited, etc., from the previous day.

**3. Implement timekpr.**
I then setup timekpr assigning time to the profile names. The profiles follow the script example of lnxlib* and follows the pattern lnxlib1 - lnxlib20. I use lnxlib20 as my "base" profile. 
Once this is complete I restart the machine and viola`. The same desktop appears as I set it up for each patron that signs in based off of the profile lnxlib20.
**FYI:** I make sure that if I need to make any changes to the base profile that I rem out the lines from the Default file so that when I go into lnxlib20 to do a little reconfiguring I don't create any issues.
I also make sure that I don't include my base profile (my case lnxlib20) to timekpr. I usually just include a dozen or so profiles in timekpr.

I am hoping that my added information will inspire someone to give me the needed information to get Dansguardian to function in this environment because right now the logins can surf any site at leisure and I really want Ubuntu to be the coolest thing we have done for our library system this year. I just have to prove it to my peers.

**Thank you**

---

### Post by david_kt on 2010-02-20
1. Have you rename /etc/gdm/PostLogin/Default.sample to /etc/gdm/PostLogin/Default ?

2. As long as the other users do not have root access, you could lock firefox proxy and make sure dansguardian is enable. All users would be filtered.

DK

---

### Post by AlexanderDGreat on 2010-02-20
Changed my setup entirely, am now using Squid Proxy Server with 2 NIC cards, made a tutorial, pls. comment on my system if needed.

PS You might be able to learn something from these videos as well:

Basic Squid Server Tutorial Part 1 of 3: [http://www.youtube.com/watch?v=MMadVJNoD48]("http://www.youtube.com/watch?v=MMadVJNoD48")

Basic Squid Server Tutorial Part 2 of 3: [http://www.youtube.com/watch?v=5WJB0STcmZM]("http://www.youtube.com/watch?v=5WJB0STcmZM")

Basic Squid Server Tutorial Part 3 of 3: [http://www.youtube.com/watch?v=Sizp7IH5Utg]("http://www.youtube.com/watch?v=Sizp7IH5Utg")

---

### Post by fishin4guitars on 2010-10-11
I've got dansguardian working well with squid, except for the fact that Firefox's network settings can be temporarily changed (until ffx is restarted). I tried the following code in firefox.cfg as said on the first page of the thread:

lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", 8080);
lockPref("network.proxy.type", 1);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1");

But as said before, it only changes the default, and can be changed in individual sessions.

EDIT: Just for clarification, its Firefox v3.6.10 on 10.04

---

### Post by scottmuz on 2011-04-04
I've been using this HOWTO now for several years. Re-doing it each time I upgrade from one version of Ubuntu to the next. However in recent versions of Ubuntu dansguardian and tinyproxy have not worked well together, with lots of webpages appearing as blank and various content coding errors.

I'd resolved this by pinning tinyproxy to an older version. But this time I instead used privoxy. Prixovy seems to work more reliably with dansguardian and seems (although I may be imagining it) faster.

I did the following (in addition to the steps identified on page 1):
- sudo apt-get install privoxy
- sudo gedit /etc/init.d/privoxy
-- change OWNER to be root
- sudo gedit /etc/dansguardian/dansguardian.conf
-- change proxyport to 8118
- sudo /etc/init.d/tinyproxy stop; sudo /etc/init.d/privoxy start; sudo /etc/init.d/dansguardian restart

---

### Post by Rakeshvijayan on 2011-10-24
Hi am new in using dansguardian .I am not installed it on my server am using 11.04 ubutnu as my server .I have some questions 
1) Is it possible to install  and configuring dansguardian on my flavor of ubuntu ?
2) Dns Is working on this server ,and have only one lan card ,do i need to implement the filtering though this dns server ,all my client system depends on the dns  server for Internet 


Thanks

---

### Post by romber on 2012-11-26
Hi everyone,

I didn't read through every page, but I noticed one discrepancy in the directions (which, of course, may have been addressed already, but oh well).

I'm on Ubuntu 12.10 x64 (64 bit). Everything worked out fine until step 5 when it said:

```
sudo gedit /etc/tinyproxy/tinyproxy.conf
```

For me, it would open a new gedit file of this, but not the actual configuration file *because* tinyproxy doesn't install inside a folder in /etc, it is just in the open.

So, what worked for me was a slight change:

```
sudo gedit /etc/tinyproxy.conf
```

I'm really new to ubuntu, so my jargon and correct use of terms is probably not up to date, but hopefully this helps someone!

---

