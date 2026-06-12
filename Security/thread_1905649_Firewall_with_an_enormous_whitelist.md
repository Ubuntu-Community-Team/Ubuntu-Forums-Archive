---
title: "Firewall with an enormous whitelist?"
date: 2012-01-07
forum: Security
---

### Post by antar on 2012-01-07
I run a game server whose main game chat has been getting spammed by an extremely persistent attacker. He appears to be using various proxy services to bypass IP bans. We've managed to slow him down in recent days by blocking IP ranges in the firewall (UFW), but I'd like to implement a more aggressive solution.

Basically, I've obtained a list of the IP addresses of the 40,000 users on our server in good standing. I then wrote a script to identify the IP ranges (starting with /16--that is, 123.45.*.*) these users fall into, combining where possible (so instead of listing 123.4.0.0/16 and 123.5.0.0/16 separately, the script combines the two into 123.4.0.0/15) to create the fewest possible allow rules to add to ufw.

However, even doing this, I end up with over 5000 rules.

I don't even know that ufw could handle this, but even if it could, it just doesn't seem like a good idea.

So my question is, does anyone know of a way to implement a firewall--not necessarily with ufw--that will be able to handle this enormous whitelist?

Alternatively, if anyone knows of a way to identify and block proxy users--using proxies violates our TOS anyway--from accessing our server (it's on an esoteric port--not 80 or anything like that), that would obviously be preferable.

---

### Post by Dangertux on 2012-01-07
> **antar said:**
> I run a game server whose main game chat has been getting spammed by an extremely persistent attacker. He appears to be using various proxy services to bypass IP bans. We've managed to slow him down in recent days by blocking IP ranges in the firewall (UFW), but I'd like to implement a more aggressive solution.

Basically, I've obtained a list of the IP addresses of the 40,000 users on our server in good standing. I then wrote a script to identify the IP ranges (starting with /16--that is, 123.45.*.*) these users fall into, combining where possible (so instead of listing 123.4.0.0/16 and 123.5.0.0/16 separately, the script combines the two into 123.4.0.0/15) to create the fewest possible allow rules to add to ufw.

However, even doing this, I end up with over 5000 rules.

I don't even know that ufw could handle this, but even if it could, it just doesn't seem like a good idea.

So my question is, does anyone know of a way to implement a firewall--not necessarily with ufw--that will be able to handle this enormous whitelist?

Alternatively, if anyone knows of a way to identify and block proxy users--using proxies violates our TOS anyway--from accessing our server (it's on an esoteric port--not 80 or anything like that), that would obviously be preferable.

For whitelisting of that size I would recommend utilizing TCP wrappers (hosts.deny). 

iptables doesn't do well with block lists of that nature, it's not what it's designed for.

---

### Post by antar on 2012-01-07
> **Dangertux said:**
> For whitelisting of that size I would recommend utilizing TCP wrappers (hosts.deny). 

iptables doesn't do well with block lists of that nature, it's not what it's designed for.

Thanks for the tip. So I would basically put

ALL : ALL

in the deny and

ALL: 1.1. , 1.2. , 1.3. , ... (for another few thousand entries)

in the allow?

Also, do you know if the 123.45.0.0/16 syntax works for these wrappers? Or do I have to reteach myself subnet masks to do /15, /14 and /13?

---

### Post by Dangertux on 2012-01-07
> **antar said:**
> Thanks for the tip. So I would basically put

ALL : ALL

in the deny and

ALL: 1.1. , 1.2. , 1.3. , ... (for another few thousand entries)

in the allow?

Also, do you know if the 123.45.0.0/16 syntax works for these wrappers? Or do I have to reteach myself subnet masks to do /15, /14 and /13?

Unfortunately it does not support CIDR's so you'd have to do something like

123.45.0.0/255.255.0.0 for 16
123.45.0.0/255.254.0.0 for 15
123.45.0.0./255.252.0.0 for 13 etc..

---

### Post by antar on 2012-01-07
> **Dangertux said:**
> Unfortunately it does not support CIDR's so you'd have to do something like

123.45.0.0/255.255.0.0 for 16
123.45.0.0/255.254.0.0 for 15
123.45.0.0./255.252.0.0 for 13 etc..

Eh. That's okay. I'm scripting it anyway, so it's not like I have to type it out.

---

### Post by Dangertux on 2012-01-07
> **antar said:**
> Eh. That's okay. I'm scripting it anyway, so it's not like I have to type it out.

Yeah if you just have a long list of ip's just use a for loop to write them all to the file, shouldn't be hard at all. Glad this is working for you.

---

### Post by Doug S on 2012-01-11
Hi antar,
 
Do you have any update for this interesting thread? Is it all working O.K.? And is prerformance O.K.? I.E. does your large list cause any slower response? Did the bad guy give up yet?

---

### Post by jongers on 2012-01-12
I have found this thread interesting, I have a list of about 700,000 bad ip addresses taken from spam-ip.com.
I use the following  script to download it and turn it into a sensible format, at least for my previous method which was a for loop within my iptables script (after about 8 hours I gave up on that method)
I am interested to see what happens when I add this list into my /etc/hosts.deny file.   I need to play with the output slightly to give the correct output, I will post results here.   If anyone can offer some insight how I could format the final /var/ipblock/actualip.list
so the results are compatible with the hosts.deny I would be greatfull.

I will post my findings, I'm sure the process will be much quicker than using the 
```

#echo "Using ################ and blacklisting it's contents"
#BLOCKDB="/var/ipblock/actualip.list"
#IPS=$(grep -Ev "^#" $BLOCKDB)
#for i in $IPS
#do

```
method


Here is the script im using, this will be a daily or weekly cron
```
#Download the latest spam file from spam-ip.com in a csv format
wget -t 10 http://spam-ip.com/csv_dump/spam-ip.com_$DATE.csv -P /var/ipblock/

echo "Getting a loberly list of ip's"
grep -Eo '[1-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' /var/ipblock/spam-ip.com_$DATE.csv > /var/ipblock/actualip.list

#echo "Getting a loberly list of ip's and putting them into /tmp/actualip.list"
#grep -Eo '[1-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' /tmp/spam-ip.com_$DATE.csv >> /var/ipblock/actualip.list
#

echo "Getting some more dirty bastards from local sources"
grep -Eo '[1-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' /var/log/fail2ban.log >> /var/ipblock/tempip.list

echo "sanitising the output and checking for any copies, this WILL take a while"

awk '!x[$0]++' /var/ipblock/tempip.list >> /var/ipblock/actualip.list
```


Improvement or recomendations are always welcome.

---

### Post by youlina on 2012-01-12
hi everyone !thank you for all of you useful tips !

---

### Post by jongers on 2012-01-12
Sorry if im spamming a thread that's not mine.

It looks like [antar]("http://ubuntuforums.org/member.php?u=188631") wants to do the same thing as me, I'm just getting my ip's from a different source and also explicitly blocking them, rather than allowing them.

Here's my final Solution errrm.  
This is my final code.
```

#/bin/bash
# Author Jonathan Gerrard v1.1 12/01/2012 jonathan@jgerrard.zapto.org

# Please please please ensure your hosts.allow file has your entries in for all remote access.  If your IP is in this list then you will be locked out!

#Get the date.
DATE=$(date +"%m-%d-%Y")
echo "Downloading the latest spam-ip.com update" $DATE

#Download the latest spam file from spam-ip.com in a csv format
wget -t 10 http://spam-ip.com/csv_dump/spam-ip.com_$DATE.csv -P /tmp/
IP1=$(wc -l /tmp/spam-ip.com_$DATE.csv)
echo "We now have $IP1 ip addresses to block"

echo "Getting a loberly list of ip's"
#Pulling all ip's out.  Leaves a nice clean output file "nothing better than a nicley formatted data file, or puppy!"
grep -Eo '[1-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' /tmp/spam-ip.com_$DATE.csv > /tmp/tempip.list

echo "Getting some more dirty bastards from local sources"
#This action pulls all the ip address type data from the list and places into a new file to work with
grep -Eo '[1-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' /var/log/fail2ban.log >> /tmp/tempip.list

echo "sanitising the output and checking for any copies, this WILL take a while"
#Checking For Multiple lines
awk '{
if ($0 in stored_lines)
   x=1
else
   print
   stored_lines[$0]=1
}' /tmp/tempip.list > /tmp/actualip.list

#This action gets the entries from the actualip.list and adds them with the correct format into /etc/hosts.deny
LIST=$(cat /tmp/actualip.list)
for i in $LIST; do
        if [ "$(grep $i /etc/hosts.deny)" = "" ]; then
                echo "ALL: $i : DENY" >> /etc/hosts.deny
        fi
done
#Displays the number of lines in the deny file, it's about the same amount of IP blocks.
echo "$(wc -l /etc/hosts.deny) are being blocked"

echo "Removing old files"
#Remove the downloaded files, they are being stored in the tmp folder daily, 20mb a day 8.4Gb a year
rm /tmp/spam-ip*
rm /tmp/actualip.list
rm /tmp/tempip.list

exit 0

```I am running this on a daily basis, I am presuming it works.

With some minor changes, I'm sure ANTAR, you could just feed this with the IPlist you have 3000+ and change the rules to Allow instead of DENY.

Hope this helps,  I'll post any speed results for my 42,510 blocked ip's on the gateway!

Maybe a slight lag!

Jongers

---

### Post by jongers on 2012-01-12
> **jongers said:**
> 

Hope this helps,  I'll post any speed results for my 42,510 blocked ip's on the gateway!

Maybe a slight lag!

Jongers

Nope!

---

### Post by matt79 on 2012-01-12
> **jongers said:**
> Nope!

Cool,
are you able to verify that it is blocking the banned IPs?

---

### Post by unspawn on 2012-01-14
> **Dangertux said:**
> iptables doesn't do well with block lists of that nature, it's not what it's designed for.
Yes it does, you just have to be careful choosing the right approach. I usually do not promote web log entries, let alone one of my own, but here it seems prudent. See the PDF at [here](http://www.linuxquestions.org/questions/blog/unspawn-2450/iptables-rule-traversal-bandwidth-at-%3D-10k-of-ip-addresses-29893/) about iptables module / ipset performance running aprox. 51K rules.


> **Dangertux said:**
> For whitelisting of that size I would recommend utilizing TCP wrappers (hosts.deny). 
The common misconception is Netfilter and TCP wrappers are equal. Using tcp_wrappers means a packet has to be delivered to that service. The serving application is responsible for reading /etc/hosts.{deny,allow} to determine itself if a connection is allowed or not. Requiring a network connection being set up exposes the application to for instance malformed packets and it requires disk I/O for having to read /etc/hosts.*. Also tcp_wrappers does not work if an application was not compiled with libwrap (as in 'ldd /path/to/application|grep libwrap'). 

In contrast the active part of the Netfilter framework resides in memory completely. More importantly the service does not get exposed as no packet is delivered to it.

---

### Post by Doug S on 2012-01-16
unspawn: one needs an account on linuxquestions.org to be able to access the document you referenced. The document is interesting.

---

### Post by emiller12345 on 2012-01-16
You may want to consider blocking Tor users which is an easy way for this spammer to continue spamming. There is probably a way to download a list of the tor exit nodes, which may allow you to definitely block those ip's

EDIT: I found this site which appears to have a list of IP's
 [http://torstatus.blutmagie.de/ip_list_exit.php/Tor_ip_list_EXIT.csv](http://torstatus.blutmagie.de/ip_list_exit.php/Tor_ip_list_EXIT.csv)

---

### Post by Dangertux on 2012-01-16
> **unspawn said:**
> Yes it does, you just have to be careful choosing the right approach. I usually do not promote web log entries, let alone one of my own, but here it seems prudent. See the PDF at [here]("http://www.linuxquestions.org/questions/blog/unspawn-2450/iptables-rule-traversal-bandwidth-at-%3D-10k-of-ip-addresses-29893/") about iptables module / ipset performance running aprox. 51K rules.



The common misconception is Netfilter and TCP wrappers are equal. Using tcp_wrappers means a packet has to be delivered to that service. The serving application is responsible for reading /etc/hosts.{deny,allow} to determine itself if a connection is allowed or not. Requiring a network connection being set up exposes the application to for instance malformed packets and it requires disk I/O for having to read /etc/hosts.*. Also tcp_wrappers does not work if an application was not compiled with libwrap (as in 'ldd /path/to/application|grep libwrap'). 

In contrast the active part of the Netfilter framework resides in memory completely. More importantly the service does not get exposed as no packet is delivered to it.

Hmm. Interesting on the 51k rules, though I could not view it / didn't feel like signing up for linuxquestions.org. I'll take your word for it in this case.

I also understand what you are saying about I/O and where the packet is chucked out at. I'm not really sure it's a misconception, so much as an alternative solution. As far as malformed packets go there are much better ways for getting rid of those (external IPS appliance?) than netfilter anyway.

EDIT : here is some information you don't have to register for about ipset [http://forums.gentoo.org/viewtopic-t-863121-start-0.html](http://forums.gentoo.org/viewtopic-t-863121-start-0.html)

I assume it's talking about pretty much the same thing.

---

### Post by antar on 2012-03-15
These responses are all absolutely amazing. I ended up going a different non-nuclear route, but it's really good to know that I have this reference here in case I ever need to implement this.

---

