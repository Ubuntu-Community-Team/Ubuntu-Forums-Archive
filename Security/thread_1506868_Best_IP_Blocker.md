---
title: "Best IP Blocker?"
date: 2010-06-10
forum: Security
---

### Post by GrantStoner on 2010-06-10
What is a good IP filter/firewall program? Seeing as how I like free softwares, I download a lot of torrents. When I was using Windows, I used PeerBlock (the newer fork of PeerGuardian), however, it's not available for Linux. What would be a good alternative for this in Linux? I tried iplist as it has a GUI, and it was extremely buggy and blocked random web pages even after I put them on the exceptions list. And MoBlock has no GUI from I understand, nor has it been updated in years.

---

### Post by BoneKracker on 2010-06-10
> **GrantStoner said:**
> What is a good IP filter/firewall program? Seeing as how I like free softwares, I download a lot of torrents. When I was using Windows, I used PeerBlock (the newer fork of PeerGuardian), however, it's not available for Linux. What would be a good alternative for this in Linux? I tried iplist as it has a GUI, and it was extremely buggy and blocked random web pages even after I put them on the exceptions list. And MoBlock has no GUI from I understand, nor has it been updated in years.

iptables is a user-friendly interface to netfilter

shorewall is a user-friendly interface to iptables

[Edit: oh, I see you want a GUI.  There aren't any good firewall programs with GUI; firewall options are too multifarious to be well-accommodated by a GUI, they limit your options and you're better off without one.  If you really feel you need one, you might try Guarddog. ]

---

### Post by GrantStoner on 2010-06-10
Does Guarddog use the same lists as iplist? Even after I uninstall iplist and reboot, the sites it was blocking before are still blocked. I have to use *sudo apt-get autoremove* to remove netfilter and then I can access the blocked websites with no problem. Does Guarddog let you import lists (say if I downloaded the level 1 list, bogon list, edu list, bad pr0n, etc.)?

---

### Post by FuturePilot on 2010-06-10
IPlist is basically a clone of PeerGuardian.

---

### Post by lovinglinux on 2010-06-10
Moblock works like a charm. I have been using it for almost two years. jre, who is maintaining it, is pretty fast on providing support. See [General Moblock Thread](http://ubuntuforums.org/showthread.php?t=803183).

Mobloquer, which is the GUI for moblock, hasn't been maintained tho, but it is pretty easy to use moblock from command-line.

---

### Post by GrantStoner on 2010-06-10
Oh, I was under the impression the Moblock had not been maintained for quite some time. I will look into both. is there a way to see a log for all the blocked and allowed connections for it? One that lists the IPs and the times they were blocked/allowed?

---

### Post by nah40 on 2010-06-10
look at this.
[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

---

### Post by lovinglinux on 2010-06-10
> **GrantStoner said:**
> Oh, I was under the impression the Moblock had not been maintained for quite some time. I will look into both.

It seems they will revive PeerGuardian for Linux and it will replace moblock. You can see more about this on the Moblock thread.

> **GrantStoner said:**
> Is there a way to see a log for all the blocked and allowed connections for it? One that lists the IPs and the times they were blocked/allowed?

I don't think any ip blocker shows allowed ip addresses, only blocked. You can see them in real-time with the command below:

```
tail -f /var/log/moblock.log
```

To see connections blocked by the firewall:

```
tail -f /var/log/messages
```

You can filter it with grep. For example to show only TCP connections:

```
tail -f /var/log/messages | grep "TCP"
```

To see currently active connections (allowed) I use [iptstate](apt:iptstate).

---

### Post by BoneKracker on 2010-06-11
If you want large, dynamically-updated blacklists, nothing comes anywhere near the speed and resource-efficiency of ipsets (create by the linux kernel "netfilter" developers as an extension to it).
[http://ipset.netfilter.org/](http://ipset.netfilter.org/)

The basics of ipsets are well-documented, but here are two examples of how to dynamically populate and update an ipset from a block list on the 'net somewhere.

This first one you would just call directly from a system crontab entry executing every so often (e.g. 15 minutes).

```
#! /bin/bash

# /cron.hourly/dshield
# Bonekracker
# Rev. 23 March 2010

# Purpose: load DShield.org Recommended Block List into an ipset in a running
# firewall.  At this time, the list is updated every 15 minutes.

data_dir="/var/tmp/dshield"     # where to store the downloaded text file
firewall_ipset="dshield"        # name of ipset in your firewall blacklist
netmask="24"                    # dshield's list is all class C networks
hashsize="64"                   # default is 1024 but 64 is more than needed here

# if ipset does not exist, create it
if ! $(/sbin/ipset -L $firewall_ipset &>/dev/null); then
        /sbin/ipset --create $firewall_ipset iphash --hashsize $hashsize --netmask $netmask
        /usr/bin/logger -p cron.warn "No ipset ${firewall_ipset}. Created new one." 
fi

# get block list's timestamp (if no file, create dummy)
if ! timestamp=$(/usr/bin/stat --printf %Y $data_dir/block.txt 2>/dev/null); then
        touch $data_dir/block.txt
fi

/usr/bin/wget -qNP $data_dir http://feeds.dshield.org/block.txt

if [ "$(/usr/bin/stat --printf %Y $data_dir/block.txt)" != "$timestamp" ]; then

        /sbin/ipset --create temp_ipset iphash --hashsize $hashsize --netmask $netmask

        networks=( $(/bin/grep ^[0-9] < ${data_dir}/block.txt | /bin/cut -f1) )

        i=${#networks[*]}
        while [ $((--i)) -ge 0 ]; do
                /sbin/ipset --add temp_ipset ${networks[i]}
        done

        /sbin/ipset -W temp_ipset $firewall_ipset
        /sbin/ipset --destroy temp_ipset

        # if you want to log the update cycle to sync your cron script to it
        #asof=$(/usr/bin/stat --printf %y $data_dir/block.txt)
        #echo $asof >> /var/log/dshield.log

        /usr/bin/logger -p cron.notice "DShield block updated."

fi
```


This second you'd call from a cron script (shown afterward) as 'ipdeny <country>'.  This will check for updates to the lists of networks registered with IANA in any number of particular countries you select, and then add those tens of thousands of networks to an ipset (which you can then use to accept of block them in your firewall).  Note: This is just an example to demonstrate technique, and not intended to suggest that people should actually block entire countries, or that certain countries should be blocked.  That said, if you wanted to, here is the most accurate and efficient way I know of to do it:
```

#! /bin/bash

# /cron.d/ipdeny
# Bonekracker
# Rev. 12 March 2010

# Purpose: load ip networks registered in a country into an ipset in a running firewall.
# Files appear to be updated at 5:07 EST daily. Usage: ipdeny cn, where cn
# is country's top-level domain (e.g., cn is China)

firewall_ipset="$1"                     # name of ipset in your firewall blacklist (e.g., cn)

file="${firewall_ipset}.zone"   # name of text file
data_dir="/var/tmp/ipdeny"      # where to store the downloaded text file

# if ipset does not exist, create placeholder
if ! $(/sbin/ipset -L $firewall_ipset &>/dev/null); then
        /sbin/ipset --create $firewall_ipset nethash
        /usr/bin/logger -p cron.warn "No ipset ${firewall_ipset}. Created new one." 
fi

# get block list's timestamp (if no file, create placeholder)
if ! timestamp=$(/usr/bin/stat --printf %Y ${data_dir}/${file} 2>/dev/null); then
        touch ${data_dir}/${file}
fi

/usr/bin/wget -qNP $data_dir http://www.ipdeny.com/ipblocks/data/countries/${file}

if [ "$(/usr/bin/stat --printf %Y $data_dir/${file})" != "$timestamp" ]; then

        /sbin/ipset --create tempset nethash

        while read network; do
                /sbin/ipset --add tempset $network
        done < ${data_dir}/${file}

        /sbin/ipset -W tempset $firewall_ipset
        /sbin/ipset --destroy tempset

        # this is temporary so I can get a feel for the update cycle
        asof=$(/usr/bin/stat --printf %y ${data_dir}/${file})
        echo $file $asof >> /var/log/ipdeny.log

        /usr/bin/logger -p cron.notice "IPSet ${firewall_ipset} updated."

fi
```

You would call that script from cron, (e.g. placing something like the following in /etc/cron.hourly):
```
#!/bin/sh

# update ipsets

# last I checked, they were being updated as follows:
# 0500
# 1500

# e.g., block China, Russia, Nigeria (just examples, no offense people)
countries="cn ru ng"

for country in $countries; do
        /usr/local/sbin/ipdeny $country
done
```

---

### Post by GrantStoner on 2010-06-11
Thanks BoneKracker, it seems like a lot of good information, but also a little over my experience level yet. I'm just looking for a firewall that allows me to import lists that i've downloaded, and has a GUI. Unless I can re-read your post and magically make sense of it in my head (doubtful) then I just want to be able to import the lists from bluetack, like I was able to do with iplist.

---

### Post by BoneKracker on 2010-06-11
> **GrantStoner said:**
> Thanks BoneKracker, it seems like a lot of good information, but also a little over my experience level yet. I'm just looking for a firewall that allows me to import lists that i've downloaded, and has a GUI. Unless I can re-read your post and magically make sense of it in my head (doubtful) then I just want to be able to import the lists from bluetack, like I was able to do with iplist.

Yes, I understand -- you want something you can easily configure from a GUI, and the feature you are most interested in is importing block lists.

I just think not enough people know about ipsets, and I wanted to put those examples where people can find them if they are looking.

I'm sorry I don't think I personally know of anything that does precisely what you want (and only that).  The one thing that comes to mind is dansguardian, but that goes well beyond what you're talking about (it does content filtering, not just IP blocking).

---

### Post by GrantStoner on 2010-06-11
I actually don't mind if it has other options along with importing block lists, so long as I can enable/disable them at will. I have no problem learning how to use features, as it'd likely expand my knowledge in this field. Do you know if dansguardian is kept up to date though and maintained?

---

### Post by SlugSlug on 2010-06-11
denyhosts or fail2ban  are worth a look,

i use denyhosts

---

### Post by GrantStoner on 2010-06-11
Fail2Ban seems like it only takes info from your logs and then updates the firewall to block certain IPs from your log. I would like to prevent the IPs **before** they access my laptop. It does me no good to download a torrent, and *then* have the firewall go through the logs and block IPs after they've had access to my machine. And is DenyHosts mainly for servers? Their site seems to make sure the point they get across is that it's mainly for servers to prevent SSH server attacks. I'm not worried about another random person/hacker/whatever getting access. That I can fix if need-be-the-case. I'm worried about getting a letter from my ISP saying they're cutting off my service, or a letter form Sony (just an example) that they're threatening to sue me.

---

### Post by FuturePilot on 2010-06-11
> **SlugSlug said:**
> denyhosts or fail2ban  are worth a look,

i use denyhosts

Those are geared mainly towards servers to protect services like SSH against brute force attacks.

---

### Post by mkvnmtr on 2010-06-11
IP list works for me. When I search for it on google I have to put in IPblocker-IPlist linux or I get a bunch of windows stuff. If you follow the instructions you will get it in synaptic and it will update.

---

### Post by SlugSlug on 2010-06-11
> **FuturePilot said:**
> Those are geared mainly towards servers to protect services like SSH against brute force attacks.


yer i never really read the OP

---

### Post by GrantStoner on 2010-06-11
Thanks FuturePilot, that's what I thought. And mkvnmtr, I've used iplist before but it blocks some websites like thepiratebay.org, and the site to log on to the internet at my school from my laptop. even after I set it to allow all HTTP for some reason it still blocks a bunch of sites. And yet, even after I uninstalled AND --purged iplist/ipblocker I still don't have access to those sites! I have to do *sudo apt-get autoremove* and then it removes netfilter and the other package iplist uses. Then, and only then, I have full access to everything again.

---

### Post by uljanow on 2010-06-11
> **GrantStoner said:**
> And yet, even after I uninstalled AND --purged iplist/ipblocker I still don't have access to those sites! I have to do *sudo apt-get autoremove* and then it removes netfilter and the other package iplist uses. Then, and only then, I have full access to everything again.

It's required to stop iplist before removing it or just reboot.

---

### Post by GrantStoner on 2010-06-11
I do, I stop iplist first, then remove any shortcuts I have to it, then remove --purge iplist, AND reboot. And I still can't access those sites till I do the autoremove afterwards. So, I know how to get rid of it so I'm able to access said sites, but if I just tell it to allow all HTTP traffic it should not block any site, and this is not the case. Not even after I put those sites on the whitelist. And I'm pretty sure it has something to do with netfilter because when I do autoremove, it removes netfilter and then everything works again.

---

### Post by FuturePilot on 2010-06-11
> This is why I want to be able to import my own lists such as level 1, edu, bad pr0n, etc. 

Maybe you've seen this, I don't know, but IPlist does let you add and remove lists, including the ones you mentioned.

---

### Post by GrantStoner on 2010-06-11
I know it does, which is why I started using it in the first place, but it was blocking sites I wanted to go to and I couldn't even get to them with iplist disabled. Which is why I'm searching for a program that's similar, but doesn't use netfilter and isn't buggy.

---

### Post by gummo on 2010-06-12
I use MoBlock and MoBloquer as GUI.

[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)
[http://mobloquer.foutrelis.com/](http://mobloquer.foutrelis.com/)

That's as close to peerguardian as you're gonna get I suppose.

---

### Post by GrantStoner on 2010-06-12
It looks as if I'm going to go with MoBlock. It's been recommended a bit, and from what I can tell seems pretty decent. Thanks all.

---

### Post by jre on 2010-06-14
Just to clarify: moblock/blockcontrol/mobloquer are not developed anymore, but they still work just fine. I still maintain the repository for them, packages for lucid are available. I'm aware of only one bug that completely prevents starting mobloquer for just a few people - but we couldn't figure out, what's wrong there. So if you are not one of those unlucky people I still recommend installing those packages. Have fun!

Besides that, we moved to developing PeerGuardian Linux. The daemon and command line interface are improved versions of moblock/blockcontrol. They work really fine and are available in my repository, too. But the GUI is still missing.

I haven't tested ipset. I guess it is really great if you want to strictly use certain blocklists - but it lacks some features that Desktop users want.

---

### Post by GrantStoner on 2010-06-14
Do you have an estimate of when PeerGuardian Linux will be available? And if there's going to be a GUI or not?

---

### Post by jre on 2010-06-14
pgl is available.
And it is definitely superior to moblock/blockcontrol.

But no, I have no estimate for the GUI. Currently GUI development is stalled.

---

### Post by GrantStoner on 2010-06-14
x__x Now I remember being on the sourceforge.net page for it I totally forgot about it. Why does it say on the Phoenix Labs webiste ([http://phoenixlabs.org/pglinux/](http://phoenixlabs.org/pglinux/)) that there is currently no PGL and to use MoBlock?

And how is PGL superior to MoBlock?

---

### Post by jre on 2010-06-15
I'll take care of the website. It's just a matter of time ...

pgl changes from the official announcement:
pgld:
[LIST]
[*]based on nfblock, which is based on moblock
[*]some bug fixes, especially in variables declaration
[*]improved blocklist handling, including premerging of single blocklists
[*]improved, simplified logging (all messages in the same format for a better reading of the logfile. But here I have to admit that while doing this we kicked dbus support, I think reimplementing this is the biggest TODO for pgld)
[*]added port and protocol logging to the logging of blocked IPs
[/LIST]
Thanks Cade, for all this work here! Of course Jindrich and Morpheus have to be credited for their underlying work, too!

pglcmd:
[LIST]
[*]based on blockcontrol
[*]some bug fixes and improvements
[*]installation paths are finally configurable in the Makefile. Paths in the scripts get adjusted automatically.
[/LIST]


With other words: some bug fixes, uses less memory, improved logging (including protocol and ports of blocked IPs).
And for those who can't use my deb packages: much more easier to install.

---

### Post by GrantStoner on 2010-06-15
Just set up MoBlock/blockcontrol/MoBloquer this morning. Working perfectly. Thanks all.

---

### Post by anicetus001 on 2011-10-14
So... any updates on the best IP Blocker? or do you people still consider these the best options?

:popcorn:

---

### Post by uRock on 2011-10-14
Closed for Necromancy

Start a new thread.

---

