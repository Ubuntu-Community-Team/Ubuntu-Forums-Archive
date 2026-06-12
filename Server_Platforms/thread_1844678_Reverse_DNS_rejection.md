---
title: "Reverse DNS rejection"
date: 2011-09-15
forum: Server Platforms
---

### Post by sdsnyr94 on 2011-09-15
Hello people much smarter than me - 

Recently, I had upgraded our mailserver which was on an older version of Suse. This server also runs our public DNS. We moved to Ubuntu 10.04 for the OS and Bind9 for the DNS. After a lot of hair-pulling and general aggravation, I had a completely working server. 

However, we seem to have one domain that we cannot send email to. According to the IT dept of that company, our emails are getting dropped because their server cannot perform reverse DNS on our domain. This is where I am getting very confused.

A few years back (prior to my employment here), we hosted our own web pages on this same server... with the domains xyz.com and abc.com. The abc.com is no longer active, and the xyz.com is now hosted offsite. E-mail sent to either domain is still received by our mailserver.

OK, so now for the issue that confuses me:

If I use this website :  [http://www.debouncer.com/reverse-dns-check]("http://www.debouncer.com/reverse-dns-check") I can successfully do an rDNS for abc.com, which points correctly to our Server at 66.x.x.x. When I try the same for xyz.com, I get the message that Reverse DNS for 204.x.x.x could not be found. 204.x.x.x is the address of our hosted site.

So, where do I go with this? Do I need a new PTR record for xyz.com pointing to 204.x.x.x? If so, where? Hosting Site, ISP, or my DNS?

Thanks in advance to anyone who can point me in the correct direction.

---

### Post by Dangertux on 2011-09-15
In my opinion if you can't receive email from the domain in another domain you may need to add a PTR record in your dns and the hosted dns. 

Also are your MX records correct on the hosted dns, and does the domain that cant get mail accept you as an authorized domain to relay from?  

Those are my suggestions.

---

### Post by zackwasa on 2011-09-15
Your mail server should have a valid hostname like: someserver.somedomain.com
Mail goes out from the server via the main server IP. That hostname needs to be pointed to that IP. The reverse DNS record of that IP needs to match the hostname of the server.

The reverse DNS change is done by the ISP or the hosting provider of the server

I hope that explains everything

---

### Post by sdsnyr94 on 2011-09-15
Thanks zackwasa, but I am still a little confused.

If I send mail from mail.xyz.com from IP 66.x.x.x, the rDNS should point mail.xyz.com back to 66.x.x.x - That makes sense, and was the way I thought it should be. 

What started throwing me was when the reverse DNS lookup from [www.debouncer.com](www.debouncer.com) came up with the 204.x.x.x address, which is our hosted web page. Shouldn't that 204.x.x.x address have nothing to do with my mail issues?

---

### Post by SeijiSensei on 2011-09-15
> **sdsnyr94 said:**
> Thanks zackwasa, but I am still a little confused.

If I send mail from mail.xyz.com from IP 66.x.x.x, the rDNS should point mail.xyz.com back to 66.x.x.x - That makes sense, and was the way I thought it should be.

No, the process you described, from symbolic name to IP address, is *forward* resolution.  Reverse resolution is rather more arcane.

Reverse domain resolution takes place in the "in-addr.arpa" domain.  Suppose you have a mail server at 1.2.3.4 named mail.example.com.  The reverse record for that IP address is 4.3.2.1.in-addr.arpa.  If forward and reverse resolution are correctly configured, that record should point to mail.example.com.

You can quickly test your forward and reverse resolution from the command prompt using the "host" command.  A correctly configured system will look like this:

```

$ host mail.example.com 8.8.8.8
mail.example.com has address 1.2.3.4
$ host -t ptr 4.3.2.1.in-addr.arpa 8.8.8.8
4.3.2.1.in-addr.arpa domain name pointer mail.example.com

```

These queries use Google's public DNS server at 8.8.8.8 to provide an unambiguous report of this host's public identity on the Internet.

ISP's and hosting companies control the reverse lookups.  You need to check with whomever provides the 66.x.x.x addresses to you to see how you can set up correct reverse-resolution for your mail server.

---

### Post by sdsnyr94 on 2011-09-16
> No, the process you described, from symbolic name to IP address, is forward resolution. Reverse resolution is rather more arcane.

I feel rather foolish for my previous response, I probably should have taken an extra 2 minutes to think before I posted.

> You can quickly test your forward and reverse resolution from the command prompt using the "host" command. A correctly configured system will look like this:


```
$ host mail.example.com 8.8.8.8
mail.example.com has address 1.2.3.4
$ host -t ptr 4.3.2.1.in-addr.arpa 8.8.8.8
4.3.2.1.in-addr.arpa domain name pointer mail.example.com
```
These queries use Google's public DNS server at 8.8.8.8 to provide an unambiguous report of this host's public identity on the Internet.

Thanks for this, I did not know the correct format and function of the host command (I had seen a reference to it in other posts about reverse DNS). Using Google's Public DNS of 8.8.8.8, and OpenDNS at 208.67.222.222, the IP comes up correctly, and the PTR correctly points back to our mail server.

According to this, I would assume that my setup is correct. So why else would this one vendor's email server be dropping our email for reverse DNS issues? Am I missing something here?

Thanks again to everybody who has posted, I was kinda thrown into the fire when I upgraded this server, having no experience configuring BIND and a public DNS... thanks to everyone in the forums I have learned quite a bit!

---

### Post by zackwasa on 2011-09-16
> **sdsnyr94 said:**
> 
According to this, I would assume that my setup is correct. So why else would this one vendor's email server be dropping our email for reverse DNS issues? Am I missing something here?


You need to check if your outbound mail server IP has the rDNS set up. Send an email to yourself and check the headers. See the IP that is used in the headers. Check if it has a rDNS record or not.

---

### Post by sdsnyr94 on 2011-09-16
> **zackwasa said:**
> You need to check if your outbound mail server IP has the rDNS set up. Send an email to yourself and check the headers. See the IP that is used in the headers. Check if it has a rDNS record or not.

Sending an email to my Gmail account, I see:

Received: from mail.xyz.com (mail.xyz.com. [66.x.x.x]) by mx.google.com.....


The 66.x.x.x is the correct server address.

*EDIT* I am willing to PM or email someone information that contains the actual IP and and server names. Of course, I do not wish to share this with the world :)

---

### Post by hawkmage on 2011-09-16
I have not heard of an MTA not delivering to a destination because of a failing reverse DNS.  I have heard of a mail server refusing a connection from an MTA that the incoming IP address doesn't match DNS and its supplied name doesn't resolve to the incoming IP. 

For delivery of mail to a domain there should be an MX record pointing to the name of the mail server.  You can get away without that if the domain its self resolves to the mail server.   If your domain is xyz.com and the mail server is mail.xyz.com if you use "nslookup -type=MX xyz.com" you should see something like this:
```
nslookup -type=MX xyz.com
Server:		208.69.39.2
Address:	208.69.39.2#53

Non-authoritative answer:
xyz.com	mail exchanger = 10 mail.xyz.com.
```

Now to see about your mail servers resolution.  This can be a bit more involved.  (I am using red hat.com for this example, their mail server is mx1.redhat.com)

First I start out with finding about the mail servers domain :
```
myhost:~ hawkmage$ dig ANY redhat.com

; <<>> DiG 9.7.3 <<>> ANY redhat.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 39901
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 3, ADDITIONAL: 1

;; QUESTION SECTION:
;redhat.com.			IN	ANY

;; ANSWER SECTION:
redhat.com.		586	IN	NS	ns3.redhat.com.
redhat.com.		586	IN	NS	ns2.redhat.com.
redhat.com.		586	IN	NS	ns1.redhat.com.
redhat.com.		454	IN	MX	10 mx2.redhat.com.
redhat.com.		454	IN	MX	5 [COLOR="Red"]mx1.redhat.com[/COLOR].
redhat.com.		6	IN	A	209.132.183.81

;; AUTHORITY SECTION:
redhat.com.		586	IN	NS	ns3.redhat.com.
redhat.com.		586	IN	NS	[COLOR="red"]ns1.redhat.com[/COLOR].
redhat.com.		586	IN	NS	ns2.redhat.com.

;; ADDITIONAL SECTION:
ns1.redhat.com.		137	IN	A	66.187.233.210

;; Query time: 27 msec
;; SERVER: 208.69.39.2#53(208.69.39.2)
;; WHEN: Fri Sep 16 10:01:23 2011
;; MSG SIZE  rcvd: 196
```
This gives me the same MX info but it also gives me the authoritative DNS servers for the domain.

I then lookup the MX host on the authoritative DNS:
```
myhost:~ hawkmage$ nslookup mx1.redhat.com ns1.redhat.com
Server:		ns1.redhat.com
Address:	66.187.233.210#53

Name:	mx1.redhat.com
Address: 209.132.183.28
```

Next I see what the authoritative DNS is for the reverse zone, this command may look a bit odd:
```
myhost:~ hawkmage$ dig NS -x 209.132.183

; <<>> DiG 9.7.3 <<>> NS -x 209.132.183
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 418
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;183.132.209.in-addr.arpa.	IN	NS

;; ANSWER SECTION:
183.132.209.in-addr.arpa. 332	IN	NS	ns2.redhat.com.
183.132.209.in-addr.arpa. 332	IN	NS	ns1.redhat.com.
183.132.209.in-addr.arpa. 332	IN	NS	ns3.redhat.com.

;; ADDITIONAL SECTION:
ns1.redhat.com.		172372	IN	A	66.187.233.210

;; Query time: 3 msec
;; SERVER: 208.69.39.2#53(208.69.39.2)
;; WHEN: Fri Sep 16 10:19:54 2011
;; MSG SIZE  rcvd: 122
```
This basically does a lookup against the in-addr.arpa domain that is the should contain the IP address of the MX host.  

Then to verify the reverse DNS I do the following:
```
myhost:~ hawkmage$ dig @ns1.redhat.com ANY -x 209.132.183.28

; <<>> DiG 9.7.3 <<>> @ns1.redhat.com ANY -x 209.132.183.28
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11396
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;28.183.132.209.in-addr.arpa.	IN	ANY

;; ANSWER SECTION:
28.183.132.209.in-addr.arpa. 600 IN	PTR	mx1.redhat.com.

;; AUTHORITY SECTION:
183.132.209.in-addr.arpa. 600	IN	NS	ns1.redhat.com.
183.132.209.in-addr.arpa. 600	IN	NS	ns2.redhat.com.
183.132.209.in-addr.arpa. 600	IN	NS	ns3.redhat.com.

;; Query time: 83 msec
;; SERVER: 66.187.233.210#53(66.187.233.210)
;; WHEN: Fri Sep 16 10:21:50 2011
;; MSG SIZE  rcvd: 127
```

This may be long winded but that is basically how I would go about validating the DNS info for your domain.

---

### Post by sdsnyr94 on 2011-09-16
Thanks Hawkmage, that was a lot of helpful info.

Couple of things that jump out at me here... and we may be getting closer to the root of the problem.

nslookup -type=MX xyz.com 8.8.8.8

xyz.com mail exchanger = 10 barracuda.xyz.com.

** We have a Barracuda Spam Filter ** 

dig @8.8.8.8 xyz.com  comes up with the 204.x.x.x address of our website ... there are no MX records listed there.

My frustration at the moment stems from the fact that none of the above is anything new... those settings were the same prior to the updated server. From what I have been looking at I am not sure how it ever worked.

---

### Post by hawkmage on 2011-09-16
SInce you are filtering your mail through a Barracuda appliance can you tell if the mail is reaching it?  Or is it failing between the Barracuda and your mail server?  

I assume that on the Barracuda device you have your mail server configured as the delivery destination for the xyz.com addressed mail.

Has anything gotten changed on the Barracuda config or firmware?

I assume that 8.8.8.8 is the authoritative DNS for your domain.  I have see that with DNS queries that you don't always get everything unless you specify what you want.  You may want to try:
```
dig @8.8.8.8 MX xyz.com
```
or 
```
dig @8.8.8.8 ANY xyz.com
```

---

### Post by sdsnyr94 on 2011-09-16
OK, just to clarify... 

  - The Barracuda only filters our inbound mail. It is not configured for outbound. 
  - I have no issues (at least none have been brought to my attention) with inbound emails.
  - It appears I only have an issue with 1 vendor at the moment, who has his mail server configured to drop mail if it cannot perform a reverse DNS properly to the domain.

The IP of 8.8.8.8 is a Google Public DNS server.... I was at work, and the internal DNS was getting in the way, so I used Google's. I should have used the 66.x.x.x (Our servers IP).

So, let me try this again now that I am home and outside the network.

dig ANY xyz.com gives me: 
                     The MX record pointing to barracuda.xyz.com  
                     The NS record pointed to dns1.abc.com   (abc.com was the old domain name)
This is under the "ANSWER SECTION"... I do not have an "AUTHORITY SECTION".

nslookup barracuda.xyz.com dns1.abc.com produces the IP of the Barracuda Unit. (I am going to call this 66.x.x.Y) (You'll see why below)

dig NS -x 66.x.x produces an output that shows:

x.x.66.in-addr.arpa. 8005    IN   NS  ns1.twtelecom.net. 

dig @ns1.twtelecom.net ANY -x 66.x.x.Y

ANSWER SECTION:
Y.x.x.66.in-addr.arpa. 86400  IN   PTR    66-x-x-Y.static.twtelecom.net

If I do: dig @ns1.twtelecom.net ANY -x 66.x.x.x (mail server IP) I receive

ANSWER SECTION:
x.x.x.66.in-addr.arpa.  86400   IN  PTR   mail.xyz.com


Looking at this output, could the "Y.x.x.66.in-addr.arpa. 86400  IN   PTR    66-x-x-Y.static.twtelecom.net" be my problem.

---

### Post by SeijiSensei on 2011-09-16
> **sdsnyr94 said:**
> Looking at this output, could the "Y.x.x.66.in-addr.arpa. 86400  IN   PTR    66-x-x-Y.static.twtelecom.net" be my problem.

Yes.  You need to have TW Telecom create a reverse entry for you that points to mail.xxx.com.

---

### Post by sdsnyr94 on 2011-09-16
OK, Thanks everyone. I will contact TW Telecom on Monday and have that done. I will post back with the results... and hopefully to close the thread.

HawkMage... thanks again for that "long winded" post earlier!

---

### Post by sdsnyr94 on 2011-09-16
Sorry, but I do have one more question.

The "Y.x.x.66.in-addr.arpa. 86400  IN   PTR    66-x-x-Y.static.twtelecom.net" is the address that points to the Barracuda's address. Should that PTR point to :

Barracuda.xyz.com or mail.xyz.com ?

Thanks again.

---

### Post by SeijiSensei on 2011-09-17
I've never been very clear on the network design here.  Is the Barracuda unit the outbound gateway for the internal network?  Is the mail server behind the Barracuda and sending out mail through it?  If it does network address translation, then the mail server will appear to be using the Barracuda's address for outbound mail.

Save yourself some hassle.  Send an email to an offsite account, then retrieve it and expose all the headers.  Go down the Received list until you see the entry that reports the arrival of the message on the remote system's inbound server.  What address does it report as the source of the message?  That's the one that needs correct forward and reverse resolution.

Here's an example:

```
Received: from mail1.xxx.gov (mail1.xxx.gov [xxx.xxx.xxx.xxx])
	by mail.yyy.com (8.13.8/8.13.8) with ESMTP id p5OJuUS3004662
	for <info@yyy.com>; Fri, 24 Jun 2011 15:56:30 -0400
```

That reports the claimed hostname of the originating server.  The name in the parentheses is the one that reverse DNS returns for that IP address.   In this case they're both the same because this mail server has correctly configured DNS.

---

### Post by sdsnyr94 on 2011-09-17
> I've never been very clear on the network design here.  Is the Barracuda  unit the outbound gateway for the internal network?  Is the mail server  behind the Barracuda and sending out mail through it?  If it does  network address translation, then the mail server will appear to be  using the Barracuda's address for outbound mail.No, the Barracuda is not configured to to anything regarding outbound email. It is only configured to block spam on incoming email. Outbound email goes straight out from the mail server.

>  Save yourself some hassle.  Send an email to an offsite account, then  retrieve it and expose all the headers.  Go down the Received list until  you see the entry that reports the arrival of the message on the remote  system's inbound server.  What address does it report as the source of  the message?  That's the one that needs correct forward and reverse  resolution.```
Received: from mail.xyz.com (mail.xyz.com. [66.x.x.x])         by mx.google.com with ESMTPS id u6si68058yhm.34.2011.09.14.05.20.01         (version=TLSv1/SSLv3 cipher=OTHER);         Wed, 14 Sep 2011 05:20:02 -0700 (PDT)

```So, does this mean that the PTR record that is needed from TW Telecom for 66.x.x.Y (which is the address of the Barracuda) should point to mail.xyz.com? Right now it is:

ANSWER SECTION:
Y.x.x.66.in-addr.arpa. 86400  IN   PTR    66-x-x-Y.static.twtelecom.net

Should it be:
Y.x.x.66.in-addr.arpa. 86400  IN   PTR   barracuda.xyz.com
or
Y.x.x.66.in-addr.arpa. 86400  IN   PTR   mail.xyz.com

If you do an nslookup of barracuda.xyz.com you resolve to 66.x.x.Y
If you do an nslookup of mail.xyz.com you resolve to 66.x.x.x

Sorry if I am being a little thick-headed here, I am just trying to  get this straight in my head, and also avoid contacting TW Telecom more than once to fix the issue.
If you would like to actually see the output I am looking at, let me know and I will PM you the actual domain name.

---

### Post by SeijiSensei on 2011-09-18
I didn't mean whether the Barracuda actually handles any outbound mail.  Is it, however, the outbound firewall gateway for the internal network?  Is the mail server behind it on the internal network?  If the mail server is on the internal network, and the Barracuda is working as the outbound gateway using network address translation, then the Barracuda will appear to the outside as your mail server.  

If the mail server is behind the firewall, then I'd give the Barracuda the name mail.xxx.com.  If you care about preserving barracuda.xxx.com, then make barracuda a CNAME for mail.

If the mail server is directly on the Internet, I don't see how the Barracuda's address enters into this at all.  The address that matters is this one:

Received: from mail.xyz.com (mail.xyz.com. [66.x.x.x]) 

whatever 66.x.x.x is.

---

### Post by sdsnyr94 on 2011-09-23
OK, so we have now had TW Telecom make the required change, and we still have the problem. At this point, I just need to get this resolved so here is the actual information for my system. If need be, maybe a moderator can remove the IP address and domain name later.

Mail Server: mail.modernautomotive.com   66.193.220.209
Barracuda: barracuda.modernautomotive.com  66.193.220.215

The PTR record that was changed by TW Telecom now says:

215.220.193.66.in-addr.arpa. 86400 IN	PTR	mail.modernautomotive.com.

According to the receiving email server's admin, they are using Icewarp Email server and based on an email he sent me, it appears the server is using MXtoolbox.com to do the lookup.

If I go to mxtoolbox.com and use the "supertool", and input "smtp:66.193.220.215" It says that "Reverse DNS FAILED! This is a problem." I can, however, do a "reverse lookup" on their site using "ptr:66.193.220.215" and see the newly changed record.

So, I'm at a loss.... this record was changed yesterday afternoon, so it is possible that it has not propagated completely yet... but I would believe that is not the case as I can do the "reverse lookup" on mxtoolbox and see the change.

Any further advise would be greatly appreciated, and will provide any other information that can help. Thanks!

---

### Post by hawkmage on 2011-09-23
When a mail system tries to deliver to modernautomotive.com it will connect to the host in the MX record. In your case that is: barracuda.modernautomotive.com
```
myhost:~ hawkmage$
modernautomotive.com mail is handled by 10 barracuda.modernautomotive.com.
```

You will notice that the forward and reverse DNS for your incoming mail host don't match.  The host barracuda.modernautomotive.com resolves to 66.193.220.215 but the reverse lookup of 66.193.220.215 resolves to mail.modernautomotive.com.

```
myhost:~ hawkmage$ host barracuda.modernautomotive.com
barracuda.modernautomotive.com has address 66.193.220.215
myhost:~ hawkmage$ host 66.193.220.215
215.220.193.66.in-addr.arpa domain name pointer mail.modernautomotive.com.
```

If 66.193.220.215 is the address of barracuda.modernautomotive.com why do you have it resolving to mail.modernautomotive.com?

---

### Post by sdsnyr94 on 2011-09-23
> **hawkmage said:**
> 
If 66.193.220.215 is the address of barracuda.modernautomotive.com why do you have it resolving to mail.modernautomotive.com?

I asked this in post #17:

> So, does this mean that the PTR record that is needed from TW Telecom for 66.x.x.Y (which is the address of the Barracuda) should point to mail.xyz.com? Right now it is:

ANSWER SECTION:
Y.x.x.66.in-addr.arpa. 86400 IN PTR 66-x-x-Y.static.twtelecom.net

Should it be:
Y.x.x.66.in-addr.arpa. 86400 IN PTR barracuda.xyz.com
or
Y.x.x.66.in-addr.arpa. 86400 IN PTR mail.xyz.com

If you do an nslookup of barracuda.xyz.com you resolve to 66.x.x.Y
If you do an nslookup of mail.xyz.com you resolve to 66.x.x.x


the 66.x.x.Y address is the 66.193.220.215
the 66.x.x.x address is the .209

Sorry, I should have just used the IP and domain from the beginning. Also, maybe I misunderstood SeijiSensei's reply's. I am going to change the record to read barracuda.modernautomotive.com.

---

### Post by sdsnyr94 on 2011-10-04
Just to close out this thread... I did not have to change the PTR record, I just did not give it enough time to replicate through the internet. The following day when I checked mxtoolbox I got:

```
220 barracuda.modernautomotive.com ESMTP (1d1ff24cb46e1ced5c685cc0118fa1c8)
 OK - 66.193.220.215 resolves to mail.modernautomotive.com
 OK - Reverse DNS matches SMTP Banner
 0 seconds - Good on Connection time
 Not an open relay.
 0.390 seconds - Good on Transaction time 
```

So, all appears to be good! Unfortunately, email is still not going through to that vendor... but it appears to be something misconfigured on their side, as he as multiple domains on his server, and I can sent mail successfully to some of his other domains. At least now they can no longer blame my end! :)

Thanks to everyone for their help, and the very informative posts.

---

