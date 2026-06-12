---
title: "Given an IP, how to find other IP blocks of the same owner"
date: 2009-09-11
forum: Security
---

### Post by Ulysses_ on 2009-09-11
Given an IP, one can go to a site like the one below and do a SmartWhoIs lookup.  [http://www.all-nettools.com/toolbox/smart-whois.php](http://www.all-nettools.com/toolbox/smart-whois.php).  For example one IP of google is 74.125.45.100, and the SmartWhoIs lookup for this returns the following IP block:  google.com (74.125.45.100) 74.125.0.0 - 74.125.255.255 Google Inc. 1600 Amphitheatre Parkway Mountain View, CA US.  How do I find the other IP blocks allocated to Google Inc (or any other owner) **automatically by typing the IP or company name** somewhere?

---

### Post by cariboo on 2009-09-11
You can use whois from the command line:

```
whois 204.244.172.9
```

Or use whois in System-->Administration-->Network Tools.

---

### Post by koenn on 2009-09-12
```
whois -h whois.ripe.net google | grep inet
```
that's a rough aproximation. there are other, more sofisticated ways to query whois databases but they require some knowledge of how whois works and how whois databases are organized.

what are you up to - scanning all of google's (or someone else's) networks to find an exploitable host ?

---

### Post by Ulysses_ on 2009-09-12
> **koenn said:**
> ```
whois -h whois.ripe.net google | grep inet
```that's a rough aproximation. there are other, more sofisticated ways to query whois databases but they require some knowledge of how whois works and how whois databases are organized.

what are you up to - scanning all of google's (or someone else's) networks to find an exploitable host ?

 No, just want to tell someone what a hacker might do to their company if their computer's dynamically allocated IP changes.  Still not exactly a practical thing to do at a company with many IPs, just want to know if it's possible.  

Why does the command given only produce a rough approximation?  Can google own two ip blocks under different names (eg Google Inc and Google Ltd)?

Also why don't most results of whois contain ip blocks?

---

### Post by koenn on 2009-09-12
If you're gonna lecture someone, maybe you should first learn a bit more about the things you're going to lecture about.

Whois has little to nothing to do with  dynamically allocated IP addresses. It's a registar of who owns (or is leasing) what address range. 
The command is a rough approach because there exist several whois databases, and they don't all behave the same. Also, companies have some liberty as to what information they put there. 
But it's always a good start.

An other obvious starting point is to find what the dns servers are for a given domain, and then query those for any address they're willing to give

Consequently, what info you supply when leasing ip addresses, and what info you'll let your nameservers give out and to who, are the first things a network administrator will concern himself with.

---

### Post by koenn on 2009-09-12
> **Ulysses_ said:**
> Also why don't most results of whois contain ip blocks?
because that's not what whois is for

---

### Post by bodhi.zazen on 2009-09-13
Not to mention ip spoofing ...

It is extremely unlikely a cracker is using his or her ipaddress. The ip you are getting is almost certainly either spoofed ip or a cracked windows computer who's owner is wondering why it is running so slow.

Finally the sad truth is enforcement of such an incident is so lax as to say non-existent. Was any damage done or data stolen ?

---

### Post by Ulysses_ on 2009-09-13
> **koenn said:**
> If you're gonna lecture someone, maybe you should first learn a bit more about the things you're going to lecture about.

Someone asked &quot;what do I want this information for&quot;?  It is only polite to explain how I came to the question.  If you do not understand why dynamically allocated IPs are mentioned, further down is the explanation.  > Whois has little to nothing to do with  dynamically allocated IP addresses.  I did not recommend whois.  

If a hacker were to penetrate a computer with a dynamically allocated IP like mine, which I forced to change IP by powering off the router for long enough, the new IP I got cannot be outside the IP blocks allocated to the ISP or company so if there is a record of all IP blocks allocated to the ISP or company, these are the relevant IPs where I can be found - not that it's practical for the hacker to port-scan hundreds of thousands of computers to find me again, it's only the principle I'm after. 

So where are the low-level records of what IPs are owned by a given company?  Surely it can't be just whatever one puts in his whois database, there must be a proper place to look.

---

### Post by aesis05401 on 2009-09-13
> **Ulysses_ said:**
> So where are the low-level records of what IPs are owned by a given company?  Surely it can't be just whatever one puts in his whois database, there must be a proper place to look.

I think you are going to be reduced to running handle searches from each registrar using every possible permutation of the company name, and even then you will not find leased blocks, or blocks registered by legally authorized work-group or department level entities.  

Companies learned their lesson in this regard many years ago during the war-dialing phase of haxploration.

---

### Post by Ulysses_ on 2009-09-13
Thank you.  What about ISP's and specifically the IP blocks they have for their dynamic customers? Is an ISP likely to offer a given customer dynamic IP's from two IP blocks with different names registered?

---

### Post by koenn on 2009-09-14
> **Ulysses_ said:**
> 

If a hacker were to penetrate a computer with a dynamically allocated IP like mine, which I forced to change IP by powering off the router for long enough, the new IP I got cannot be outside the IP blocks allocated to the ISP or company so if there is a record of all IP blocks allocated to the ISP or company, these are the relevant IPs where I can be found - not that it's practical for the hacker to port-scan hundreds of thousands of computers to find me again, it's only the principle I'm after. 

yes, that's correct. 
It's pretty obvious if you think about it : to have internet access, you need to be on a network that is connected to the internet. So the ISP gives you an address in its own network (or a point-to-point to a host on its network, same thing). So as long as you stay with the same ISP, I can find out which one out of a couple of thousand addresses you may have.

In reality, it's more simple than that : your address is already known by web servers (or other internet servers) you connect to, or maybe from the headers in mail you sent, or by peer-to-peer hosts you connected to, etc.

However, no one is interested in this, because home users are more easily attacked in bulk, by phishing, websites with traps, or downloads with trojans in them, than by manually targetting a single address.

It's different for companies with a permanent internet presence (publicly accessible servers), which I thought your original question was about.

---

### Post by scorp123 on 2009-09-14
> **Ulysses_ said:**
>  not that it's practical for the hacker to port-scan hundreds of thousands of computers to find me again He probably even would not have to. In the case of Windows PC's its not uncommon for crackers to install spyware, bots and what not on the victim system. So even if you change the IP address, the bot would then simply (re-)connect to its master node (which is under the cracker's control) and take any further commands from there. So the cracker doesn't even have to scan for you ... it's the other way round: the bot he gave you will automagically "phone home".

> **Ulysses_ said:**
>  Surely it can't be just whatever one puts in his whois database, there must be a proper place to look. DNS.

A lot can be found out by simple "nslookup" queries, e.g. the "ls" sub-command. The problem here is that most implementations of the "nslookup" program have that functionality disabled ("not implemented").

But that of course won't stop the real hackers who will simply take the "nslookup" source code and re-implement this and other handy features that can be used for spying purposes.

Last but not least: if a cracker somehow manages to force their way into a DNS server (breaking into badly secured "bind" servers is not unheard of) they very likely will get all the info they want on their target's IP networks and what not.

---

### Post by sharimila on 2010-07-21
I found this site  [http://www.whoisxy.com/](http://www.whoisxy.com/) It give domain name,ip address and got nice result at free of cost ...
Its equally to good to smartwhois

---

