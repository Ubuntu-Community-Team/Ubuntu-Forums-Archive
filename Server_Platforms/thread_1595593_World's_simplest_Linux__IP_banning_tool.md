---
title: "World's simplest Linux  IP banning tool"
date: 2010-10-13
forum: Server Platforms
---

### Post by mistypotato on 2010-10-13
Hello,

I am looking for the absolute simplest way to permanently or temporarily ban an IP address from my Ubuntu server.

There are occasions where a smart hacker will know exactly how fail2ban and other banning schemes work and will never get banned because they are patient and work around those filters.  For example, trying only one apache-noscript line per day or week.

So, upon manually scanning the logs, when I find such a hckers IP address, I want a really clean, quick and easy way to add the IP address to a permanent ban list.

I realize I can sudo the IP address manually into iptables via the terminal and add it to IP tables, but I'm so lazy, I don't even want to have to open a Terminal window and do the typing or pasting.

So, I suppose I'm looking for a GUI or script that simply asks me for the IP address and then presents me with the choices as follows.....

1). 1 day ban
2). 1 week ban
3). 1 month ban
4).  Permanent ban


And the script then adds the info for me.

IS this doable?

thanks

---

### Post by BobVila on 2010-10-13
Take a look at fail2ban and OSSEC/HIDS. No need to reinvent the wheel here...

---

### Post by koenn on 2010-10-13
> **mistypotato said:**
> 

And the script then adds the info for me.

IS this doable?


yes

---

### Post by WinstonChurchill on 2010-10-13
I did this with iptables for awhile - if you use the xt_recent module it's quite simple; you could easily write a script like you're asking for. You could even create rules to look for certain strings in the packets (I'm quite sure that iptables un-fragments packets before string scanning since like kernel 2.6.twenty-something) and block those IP's automatically. This would dramatically increase load on a high-traffic server, but since you say you can look through the logs and block addresses manually, I'm guessing yours isn't that high volume.

From the iptables man page: ```

recent
       Allows you to dynamically create a list of IP addresses and then  match
       against that list in a few different ways.

       For example, you can create a "badguy" list out of people attempting to
       connect to port 139 on your firewall and then DROP all  future  packets
       from them without considering them.

       --name name
              Specify  the  list  to use for the commands. If no name is given
              then DEFAULT will be used.

       [!] --set
              This will add the source address of the packet to the  list.  If
              the  source address is already in the list, this will update the
              existing entry. This will always return success (or failure if !
              is passed in).

       --rsource
              Match/save  the source address of each packet in the recent list
              table. This is the default.

       --rdest
              Match/save the destination address of each packet in the  recent
              list table.

       [!] --rcheck
              Check  if  the  source address of the packet is currently in the
              list.

       [!] --update
              Like --rcheck, except it will update the "last  seen"  timestamp
              if it matches.

       [!] --remove
              Check  if  the  source address of the packet is currently in the
              list and if so that address will be removed from  the  list  and
              the rule will return true. If the address is not found, false is
              returned.

       [!] --seconds seconds
              This option must be used in conjunction with one of --rcheck  or
              --update.  When  used, this will narrow the match to only happen
              when the address is in the list and was  seen  within  the  last
              given number of seconds.

       --reap reap
              This  option  must  be  used in conjunction with --seconds. When
              used, this will remove entries with the  most  recent  timestamp
              older then --seconds since the last packet was received.

       [!] --hitcount hits
              This  option must be used in conjunction with one of --rcheck or
              --update. When used, this will narrow the match to  only  happen
              when  the  address  is in the list and packets had been received
              greater than or equal to the given value.  This  option  may  be
              used  along  with  --seconds  to  create  an even narrower match
              requiring a certain number of hits within a specific time frame.

       --rttl This option may only be used in conjunction with one of --rcheck
              or  --update. When used, this will narrow the match to only hap&#8208;
              pen when the address is in the list and the TTL of  the  current
              packet matches that of the packet which hit the --set rule. This
              may be useful if you have  problems  with  people  faking  their
              source  address in order to DoS you via this module by disallow&#8208;
              ing others access to your site by sending bogus packets to you.

       Examples:

              iptables -A FORWARD -m recent --name badguy  --rcheck  --seconds
              60 -j DROP

              iptables  -A FORWARD -p tcp -i eth0 --dport 139 -m recent --name
              badguy --set -j DROP

       Steve's  ipt_recent  website  (http://snowman.net/projects/ipt_recent/)
       also has some examples of usage.

       /proc/net/xt_recent/*  are  the current lists of addresses and informa&#8208;
       tion about each entry of each list.

       Each file in /proc/net/xt_recent/ can be read from to see  the  current
       list or written two using the following commands to modify the list:

       echo +addr >/proc/net/xt_recent/DEFAULT
              to add addr to the DEFAULT list

       echo -addr >/proc/net/xt_recent/DEFAULT
              to remove addr from the DEFAULT list

       echo / >/proc/net/xt_recent/DEFAULT
              to flush the DEFAULT list (remove all entries).

       The module itself accepts parameters, defaults shown:

       ip_list_tot=100
              Number of addresses remembered per table.

       ip_pkt_list_tot=20
              Number of packets per address remembered.

       ip_list_hash_size=0
              Hash  table  size. 0 means to calculate it based on ip_list_tot,
              default: 512.

       ip_list_perms=0644
              Permissions for /proc/net/xt_recent/* files.

       ip_list_uid=0
              Numerical UID for ownership of /proc/net/xt_recent/* files.

       ip_list_gid=0
              Numerical GID for ownership of /proc/net/xt_recent/* files.

```

---

### Post by mistypotato on 2010-10-13
Gosh,
Thanks for the replies but....
everyone seems to miss the key requirement here....

[COLOR="SeaGreen"]**SIMPLICITY**[/COLOR]

Everything suggested so far either provides no info OR requires learning a new this or that process or some other in depth analysis and so forth....

**Isn't there anything REALLY simple t do this?**
[U]

[SIZE="4"]I looked at **GUFW/UFW** and it looks perfect[/U][/SIZE]...EXCEPT

...in my 1 minute eval I couldn't be sure it does not try to re-write my current IPTABLES config or interfere with it.

If it does not in any way change, hamper or interfere with my current iptables firewall then it will be the solution I am seeking.

I don't have time to devote to learning anything at this time for this specific process :)

Cheers!

---

### Post by eveningsky339 on 2010-10-13
> **mistypotato said:**
> 
I realize I can sudo the IP address manually into iptables via the terminal and add it to IP tables, **but I'm so lazy**, I don't even want to have to open a Terminal window and do the typing or pasting.

Perhaps a change of attitude is better than searching for a simple GUI tool.  You can't dink around with hackers when you're running a server.

---

### Post by mistypotato on 2010-10-13
> **eveningsky339 said:**
> Perhaps a change of attitude is better than searching for a simple GUI tool.  You can't dink around with hackers when you're running a server.


R U absolutely sure there's enough info in this thread to _fully_ assess server security?
I hope so after suggesting an "attitude" change....and then suggestion that I'm "dinking" around.
This thread contains nothing that is "critical" to my server's security at all.

You made a few too many assumptions without offering any substantial advice :P
And....you missed the point........sigh....

Anyone else?

---

### Post by koenn on 2010-10-14
> **mistypotato said:**
> R U absolutely sure there's enough info in this thread ...

And....you missed the point........sigh....

Anyone else?

eveninsky339 has a point, though.
Your posts are littered with "I'm too lazy", "I don't have time to devote ...", "I can't be bothered with analysis ...", " ... 1 minute eval ... ", ...
What did you expect? That someone comes up with a perfect solution based on the meager info in you OP, and does all the work for you ?
Without you even providing accurate info about the setup you have at the moment ?
If your problem isn't even worth your time and effort, why would anyone else bother ?

---

### Post by Iksf on 2010-10-14
This thread is sounding like a Gentoo forum imo, if he doesnt care about why its better to do it properly don't whine about it. Surely there must be a simple tool for a simple IP ban

---

### Post by mistypotato on 2010-10-14
iksf...I think you may get it :P

the rest of you ........

C'mon guys.....

I'm sure you mean well........but......

You keep trying to beat a dead horse.....without understanding the real context of this thread.  I'm not really lazy....gee...I was only poking fun about the lazy thing...everyone's so flat.....it's just that what Im trying to do here isn't critical and I was trying to make that point.  

Instead of assuming I'm just plain rotten at server security....try to see what I'm really asking here.

A quick and easy way to block an "interesting" IP.    My Watchguard Firebox does the brunt of the work and iptables does most of the cleanup (if any).  Then the firewall on the server filters any possible outgoing streams that might be generated by anything that somehow slipped past the real front gates.

So, all I'm looking for is more of a novelty than a necessity.  Don't you get it ?

Sure I could use ipblock and create lists but again, FOR THIS TASK, I don't want to work that hard....and ipblock consumes a lot of memory.

Ok, since everyone seems to be bent on calling me a lousy, lazy, inadequate server admin (hehe...sounds like a good T-shirt slogan)....i'm about to give up on this thread.

btw....for those who DO get it....I still think for THIS non critical task, gufw looks interesting.
It has a really simple, GUI interface tht accepts an ip to block.   In contrast, Firestarter doesn't really have a place to input an ip to block specifically.

I just need to do a test and make sure it doesn't do anything funky with the iptables config file.

---

### Post by koenn on 2010-10-14
proof-of-concept, needs work, needs testing, no warranties, etc.


```

#!/bin/bash

#conf
iptables_list="/etc/iptables.saved"

# or, alternatively, use a blacklist for tcwrapper or some program
#blacklist="/etc/hosts.deny"


# user input
echo -n "ban IP       : "
read address
echo -n "ban (D W M P): "
read ban

# main
case $ban in
	[Dd])
	expiredate=$(date -d'+ 1 days')
	;;
	[Ww])
	expiredate=$(date -d'+ 7 days')
	;;
	[Mm])
	expiredate=$(date -d'+ 31 days')
	;;
	[Pp])
	expiredate="permanent"
	;;
	* )
	echo "invalid choice,  only D W M P are valid"
	exit
	;;
esac


#+ add bann by passing address to some underlying mechanism, eg iptables
iptables -I INPUT -s $address -j DROP
iptables-save > $iptables_list

#alternatively, add address to blacklist
echo "$address" > $blacklist  


#+ set ban to expire
if [ "$expiredate"  != "permanent" ]  ; then

    # build a command that makes the ban expire
    expirecmd="iptables -D INPUT -s $address -j DROP && (iptables-save > $iptables_list)"


    # alternative expire command, eg for a blacklist
    #expirecmd="sed -i \"/^.*${address}.*$\"/d $blacklist"

    # create at job to execute $expirecmd at given date
    expiredate=$(date -d "$expiredate" +%y%m%d)
    echo "$expirecmd" |at $expiredate 

fi

```

---

