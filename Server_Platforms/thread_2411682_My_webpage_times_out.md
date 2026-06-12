---
title: "My webpage times out"
date: 2019-02-02
forum: Server Platforms
---

### Post by ralphot on 2019-02-02
Hi!
I have an ubuntu server 18.04 and a website tempuss.dynu.com on it that works some of the times.
But mostly it just sit there waiting to update. I have talked to dynu.com and there is no problem there.
Just now it's stuck, and a minute ago it was present and could be updated several times.

What can be the problem?

Ralph in Sweden

---

### Post by SeijiSensei on 2019-02-02
The page loaded quickly enough for me.

Does it rely on getting data from another server? If so, that seems the most likely cause. If this is persistent, consider using a script to periodically update a local copy of the data and have the web page present the local copy instead. Or maybe find a more reliable source.

---

### Post by ralphot on 2019-02-02
Thanks. No, the data comes from SQL-database in the server and is updated every five minutes from a perl-script that acquire temperatures read from 1-wire temperature sensors with Digitemp program, /usr/bin/digitemp_DS9097
So I can not see any reason for this. The problem seemed to have started since I updated to ubuntu 18.04

Just now it's not reachable. But if I go to the server, open Firefox it comes up. Strange...

---

### Post by volkswagner on 2019-02-02
At 10:05PM EST it times out.

Are you hosting this on a residential circuit?
What type of connection is it (DSL, CABLE, etc)?
I think your ip address is changing more often than your 
Dynamic DNS is updating, or your Dynamic update is
not working correctly.

This morning your domain resolved to 81.230.40.46
This evening when I first attempted to connect, it
resolved to 81.230.40.46, but did not connect.
When I tried a few minutes later it resolved
to 78.68.138.112 and worked. A few minutes later
it resolved to 81.230.40.46 and timed out.

It almost seems like you have two servers in two 
different locations, that are updating in the same domain name
from two different ip addresses (a couple minutes apart).

```
Sat Feb  2 22:18:09 EST 2019
tempuss.dynu.com has address 81.230.40.46
tempuss.dynu.com has IPv6 address 2001:2002:51e6:282e::1
tempuss.dynu.com mail is handled by 10 mail.tempuss.dynu.com.


Sat Feb  2 22:18:18 EST 2019
tempuss.dynu.com has address 78.68.138.112
tempuss.dynu.com has IPv6 address 2001:2002:51e6:282e::1
tempuss.dynu.com mail is handled by 10 mail.tempuss.dynu.com.

Sat Feb  2 22:19:39 EST 2019
tempuss.dynu.com has address 81.230.40.46
tempuss.dynu.com has IPv6 address 2001:2002:51e6:282e::1
tempuss.dynu.com mail is handled by 10 mail.tempuss.dynu.com.
```

---

### Post by ralphot on 2019-02-03
Thanks volkswagner

Well, first of all I have fiber connection 100/100 Mb/s and only one server. 
And my address should be 78.68.138.112, don't know what 81.230.40.46
comes from. It belongs to Telia with is my provider. I have seen a funny thing
in my server. If I stop apache2 and look at what apache is running I find this:

root@ubuntu:~# ps -ef | grep apache
root     20388 20294  0 13:42 pts/1    00:00:00 grep --color=auto apache

This process seems to update every second and can't be killed. What is it?
pts/1 is my inlogged terminal on my mac

My ddclient.conf:
protocol=dyndns1
use=if, if=enp2s0
server=dynu.com
login=xxxx
password='xxxxxx'
tempuss.dynu.com

---

### Post by SeijiSensei on 2019-02-03
I would find a provider that will give you a static IP.  Running servers off a dynamic IP is a recipe for problems.  You might consider running your own DNS server as well once you get a static IP.

---

### Post by ralphot on 2019-02-03
Well, I have used this method for over ten years without any problems, 
this problem started to happened when I was moving to another home
with fiber 100/100 Mb/s Internet connection. Before that it worked like charm.
But now, I get random between two different IP's: (the correct one 78.68.138.112 and incorrect 81.230.40.46
There must be an explanation for that, and a way to solve it.
[https://www.whatsmydns.net/#A/tempuss.dynu.com](https://www.whatsmydns.net/#A/tempuss.dynu.com)

dynu.com says: [COLOR=#000000][FONT=verdana]Your hostname tempuss.dynu.com points to 81.230.40.46 and it is updated by curl according to our system log.[/FONT][/COLOR]

---

### Post by Doug S on 2019-02-03
> **ralphot said:**
> I have seen a funny thing
in my server. If I stop apache2 and look at what apache is running I find this:

root@ubuntu:~# ps -ef | grep apache
root     20388 20294  0 13:42 pts/1    00:00:00 grep --color=auto apache

This process seems to update every second and can't be killed. What is it?
pts/1 is my inlogged terminal on my mac

You are seeing the process of your grep command itself, so nothing to worry about. Examples:
```
doug@DOUG-64:~$ ps -ef | grep [COLOR="#FF0000"]zzz[/COLOR]
doug     24277 27252  0 10:46 pts/2    00:00:00 grep --color=auto [COLOR="#FF0000"]zzz[/COLOR]
doug@DOUG-64:~$ ps -ef | grep [COLOR="#FF0000"]xxx[/COLOR]
doug     24279 27252  0 10:46 pts/2    00:00:00 grep --color=auto [COLOR="#FF0000"]xxx[/COLOR]
```this one is interesting (thanks to what volkswagner found), the authoritative name servers are constantly toggling between 81.230.40.46 and 78.68.138.112 and sometimes no "A" record at all, with a life time of only ever 60 seconds. There is also sometimes, not always, an MX record, record for mail.tempuss.dynu.com, with a lifetime of 90 seconds. Note that mail.tempuss.dynu.com always resolves to 81.230.40.46 (I think).

it seems to me, without any proof, The DNS' sometimes don't know what tempuss.dynu.com should resolve to, so they make it the same as mail.tempuss.dynu.com.

---

### Post by ralphot on 2019-02-03
Thank you. Ok about the grep command. I should be aware of that.
I will pass this interesting conclusion to dynu.com för them to act.

I'll will report if a solution comes to hand.

---

### Post by Doug S on 2019-02-03
> **ralphot said:**
> I'll will report if a solution comes to hand.Please do, this one is very interesting.

Here are just some examples of the various replies for "[COLOR="#FF0000"]dig -t any tempuss.dynu.com[/COLOR]" (edited):
```

;; ANSWER SECTION:
tempuss.dynu.com.       11      IN      MX      10 mail.tempuss.dynu.com.

--
;; ANSWER SECTION:
tempuss.dynu.com.       9       IN      MX      10 mail.tempuss.dynu.com.
tempuss.dynu.com.       56      IN      A       78.68.138.112
--
;; ANSWER SECTION:
tempuss.dynu.com.       35      IN      A       78.68.138.112

--
;; ANSWER SECTION:
tempuss.dynu.com.       60      IN      A       81.230.40.46
tempuss.dynu.com.       90      IN      MX      10 mail.tempuss.dynu.com.
--
;; ANSWER SECTION:
tempuss.dynu.com.       57      IN      A       78.68.138.112
tempuss.dynu.com.       27      IN      MX      10 mail.tempuss.dynu.com.
--
;; ANSWER SECTION:
mail.tempuss.dynu.com.  60      IN      A       81.230.40.46

--
;; ANSWER SECTION:
tempuss.dynu.com.       90      IN      MX      10 mail.tempuss.dynu.com.
tempuss.dynu.com.       60      IN      A       81.230.40.46

```EDIT 1: There are 7 authoritative name servers involved, ns0-ns6.dynu.com. 168.235.71.124 (ns6.dynu.com) always seems to reply "78.68.138.112" and "207.38.70.2" (ns1.dynu.com) always seems to reply "81.230.40.46" with "dig". (I thought I tried this yesterday with "nslookup" and got  different results.) Which name server ones gets each time is more or less random.

EDIT 2: ns0-ns4.dynu.com = bad; ns5-ns6.dynu.com = good.

EDIT 3: Never mind, while the time constant for change seems to be longer, just now (hours later than edit 2) all 7 name servers are giving bad answers. No wait, now all 7 give correct answers. No wait,...

---

### Post by ralphot on 2019-02-11
I have not get any information from dynu.com and I don't know what to do. 
This is what my webpage resolves to:

Boston MA, United States        81.230.40.46
Reston VA, United States        81.230.40.46
Los Angeles CA, United States   78.68.138.112
Atlanta GA, United States       81.230.40.46
Dallas TX, United States        81.230.40.46
Cambridge ON, Canada            78.68.138.112
..
..

Anyone have any idea?

---

### Post by Doug S on 2019-02-11
> **ralphot said:**
> I have not get any information from dynu.com and I don't know what to do. 
This is what my webpage resolves to:

Boston MA, United States        81.230.40.46
Reston VA, United States        81.230.40.46
Los Angeles CA, United States   78.68.138.112
Atlanta GA, United States       81.230.40.46
Dallas TX, United States        81.230.40.46
Cambridge ON, Canada            78.68.138.112
..
..

Anyone have any idea?I have been watching the various DNS replies. Yesterday they did change, and now no longer list an MX record, and now also list a IPV6 address. However, and as you mention, they are still rotating between correct and incorrect answers (for IPV4). Example:

```
doug@DOUG-64:~$ [COLOR="#FF0000"]dig @ns0.dynu.com -t any tempuss.dynu.com | grep -A 2 "ANSWER SECTION"[/COLOR]
;; ANSWER SECTION:
tempuss.dynu.com.       60      IN      A       [COLOR="#FF0000"]81.230.40.46[/COLOR]
tempuss.dynu.com.       60      IN      AAAA    2001:2002:51e6:282e::1
doug@DOUG-64:~$ [COLOR="#FF0000"]dig @ns1.dynu.com -t any tempuss.dynu.com | grep -A 2 "ANSWER SECTION"[/COLOR]
;; ANSWER SECTION:
tempuss.dynu.com.       60      IN      AAAA    2001:2002:51e6:282e::1
tempuss.dynu.com.       60      IN      A       [COLOR="#FF0000"]78.68.138.112[/COLOR]

```This issue is with dynu.com, the proof is undeniable. We can not help any further, you need to deal with them.

---

### Post by ralphot on 2019-02-12
I got an email that could clear things up. This is what dynu said:

//
Like we explained, you have a curl script running at IP address 81.230.40.46
that keeps updating tempuss.dynu.com to that IP. Below is what we received:


The issue can only be resolved by locating the script running at 81.230.40.46
and stopping it if you plan to continue using this hostname.
//

Where can that be? I'll try to find the script.

I did this:
root@ubuntu:~# ps -ef | grep curl
root 12563 12322 0 21:39 pts/1 00:00:00 grep --color=auto curl
[10]- Exit 1 GET /nic/update?hostname=tempuss.dynu.com
[12]+ Done username=ralphot

Seems to still be running last command

Also this:

root@ubuntu:~# GET /nic/update?hostname=tempuss.dynu.com&myip=81.230.40.46&username=ralphot&password=sommar*****
[4] 12751
[5] 12752
[6] 12753
[1]   Exit 1                  GET /nic/update?hostname=tempuss.dynu.com
[2]   Done                    myip=81.230.40.46
[3]   Done                    username=ralphot
root@ubuntu:~# 

This i obviously the problem.

Where to look for this??

All this started after I upgraded to ubuntu 18.04

---

### Post by ralphot on 2019-02-13
I have deleted the host tempuss.dynu.com and replaced it with tempus.dynu.net. We'll see how that works.
Thank you all for your help. Have not time to dig myself deeper into that anymore.

---

