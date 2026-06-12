---
title: "Verify one particular software is not a trojan on Linux"
date: 2016-06-26
forum: Security
---

### Post by vonrabbe on 2016-06-26
Dear Ubuntu users,


I got a question (I am a Windows guy, sorry):&#8203;
I have a user in my company that uses [http://cloudport.xyz/](http://cloudport.xyz/) service to access our network from outside.


This thing generates you a binary you run on your machine, but how could I know this is not a trojan or virus? 
Any way to check it? It says "no configuration required". But should I trust it? Any tools for Linux that check binaries for viruses? 
I already checked it with ClamAV, and ClamAV said it's OK... Is it enough?

The user himself runs Ubuntu 14.04 LTS and he said he trusts in this cloudport thing. But could I?

Thank you! :)

---

### Post by Mark Phelps on 2016-06-26
> This thing generates you a binary you run on your machine, but how could I know this is not a trojan or virus? 

From the little information available on this service, there is no way you CAN know!

It sounds like it uses an anonymous tunneling protocol to allow you to get anything past any firewall -- and, if I was still in IT, THAT would be enough for me to say -- no way, not on any system I manage!

But, in all fairness, I don't know anything about this app, but my own (ex)professional experience has been, in that case, do NOT trust it.

Others, I'm sure, will provide other opinions.

---

### Post by grahammechanical on 2016-06-26
My thoughts are this:

If I was the owner of a company I would dictate what method my employees use to access my network.

---

### Post by Habitual on 2016-06-26
> **vonrabbe said:**
> Dear Ubuntu users,


I got a question (I am a Windows guy, sorry):&#8203;
I have a user in my company that uses [http://cloudport.xyz/](http://cloudport.xyz/) service to access our network from outside.


This thing generates you a binary you run on your machine, but how could I know this is not a trojan or virus? 
Any way to check it? It says "no configuration required". But should I trust it? Any tools for Linux that check binaries for viruses? 
I already checked it with ClamAV, and ClamAV said it's OK... Is it enough?

The user himself runs Ubuntu 14.04 LTS and he said he trusts in this cloudport thing. But could I?

Thank you! :)

Check it at virustotal.com
They says it's clean, it's clean. </opinion>

and couldn't agree more:
> **grahammechanical said:**
> If I was the owner of a company I would  dictate what method my employees use to access my network.

---

### Post by DuckHook on 2016-06-26
+1 to all of:

Mark Phelps' grahammechanical's and Habitual's replies.

It is just outright foolish to allow open-season on entry methods or unknown binaries into a corporate network. A [ransom-ware]("http://www.networkworld.com/article/3088072/the-number-of-corporate-users-hit-by-crypto-ransomware-is-skyrocketing.html") stick-up job waiting to happen.

I would not allow *any* unknown or unapproved binaries onto a corporate network. In fact, I would go so far as to make it a disciplinary offence, but that's just me, and I have absolutely zero tolerance for people who take chances with other people's assets.

---

### Post by DuckHook on 2016-06-26
*Thread moved to **Security** as the more appropriate forum.*

---

### Post by ventrical on 2016-06-27
> **vonrabbe said:**
> Dear Ubuntu users,


I got a question (I am a Windows guy, sorry):&#8203;
I have a user in my company that uses [http://cloudport.xyz/](http://cloudport.xyz/) service to access our network from outside.


This thing generates you a binary you run on your machine, but how could I know this is not a trojan or virus? 
Any way to check it? It says "no configuration required". But should I trust it? Any tools for Linux that check binaries for viruses? 
I already checked it with ClamAV, and ClamAV said it's OK... Is it enough?

The user himself runs Ubuntu 14.04 LTS and he said he trusts in this cloudport thing. But could I?

Thank you! :)

I downloaded the made file for testing with (cloud) option. After the first download  CAVL did not detect anything "On Access". When I went to scan manually it completely locked up my PC but this is not becasue of  that file . (It is because I have a gazillion Tabs open ) :). I rebooted and set hueristics to highest. There was no detect of any suspicious software in that executable package.

I would err on the side of caution at this stage of the game.  I did not run the file but may test that on a DT at a later time.

So I am +1 to Mark, Graham , Habi and Duck.

Regards..

---

### Post by Habitual on 2016-06-27
Visit the site. It screams "red flag".
But his blog post seem innocent enough.
[https://github.com/ivanilves](https://github.com/ivanilves) seems like he's been productive.

Or white label it using [github]("https://github.com/ivanilves/CloudPort") ?

---

### Post by c0n7r4 on 2016-06-27
This is from the website in question:
```
 Anonymous reverse tunnels

Expose: Enter target hostname...
22
Go!
Windows
64-bit
Use this form to generate your own personalized tunnel application
Address to expose is the address of some host inside your LAN,
for which you would like to provide temporary external access. 
CloudPort creates specially tailored [ptu] builds to allow seamless user experience. 
The goal is to deliver a ready to use, zero-configurable and disposable application. 
Ivan Ilves

``` My question is (rhetorical): What is a trojan if not a piece of software that allows remote access to protected systems?
It basically sounds like a trojan because imo, it is a trojan. And I wouldn't wait around for an antivirus company to tell you a trojan, because
you could be waiting for a long time. If you know its bypassing your network securities, I would shut it down.

---

### Post by DuckHook on 2016-06-27
On a completely non-technical front, if I may be permitted an observation?

It is clear to me that the bigger problem here is not the app in question; the more pertinent and pressing question is: what should your company's IT policy be? While I would not go as far as calling it a Trojan (which has a very technical meaning), c0n7r4's post is very relevant: by permitting reverse-tunnelling, you are permitting holes to be punched into your firewall by whomever takes it into their heads to do so. Do you or your bosses really want this? If this user has a legitimate need for remote access, then properly research known solutions with known safeguards and implement them only after extensive testing (including penetration testing). Otherwise, better have good offsite backups because it's only a matter of time before some mobster encrypts your network and demands payment in bitcoins. Or at least, that's what you have to be prepared for.

---

### Post by bashiergui on 2016-06-27
> **Habitual said:**
> Check it at virustotal.com
They says it's clean, it's clean. </opinion>
Good god no. When Virus Total tells you something is malicious you should believe it. If it says something is clean you should understand that it's either clean or it's unique malware. Most malware is not reused. A whole lot more analysis is required before you can call it clean.

You could compare the hash of your file to a database of known good files, like this one [http://www.hashsets.com/nsrl/search/](http://www.hashsets.com/nsrl/search/)

---

### Post by Habitual on 2016-06-28
> **bashiergui said:**
> Good god no. When Virus Total tells you something is malicious you should believe it. If it says something is clean you should understand that it's either clean or it's unique malware. Most malware is not reused. A whole lot more analysis is required before you can call it clean.

You could compare the hash of your file to a database of known good files, like this one [http://www.hashsets.com/nsrl/search/](http://www.hashsets.com/nsrl/search/)

You are correct, of course. Reverse Tunnels are (not?) likely to show up in A/V scans?
I would think not.
I certainly would advocate [COLOR=#ff0000]**extreme caution**[/COLOR], for 2 reasons:
A "user" found this, and as I said "It screams 'red flag'".

Sandbox.
install ptu
sniff it out. # find out what ports are used? wink wink nudge nudge

Why are the "users" doing trying to expose hosts inside the LAN, and how is that in context of their usual daily duties? 

What could possibly be that important to someone _***inside***_ of your network to someone outside your sphere?

I certainly wouldn't flat out allow it but it does provide an opportunity for the OP to deploy his own version of ptu
for the "users" at his "company".

If it were my company and I could do so, I'd set Policy and inhibit those abilities from the users, (and educate them)
while taking a "We're evaluating the service." during which time you sandbox, install, read, try, try, try again...
I would have deployed a vm.local somewhere and been all over it. 

That's just me.
</grain_of_salt>

---

### Post by ventrical on 2016-06-28
> **Habitual said:**
> You are correct, of course. Reverse Tunnels are (not?) likely to show up in A/V scans?
I would think not.
I certainly would advocate [COLOR=#ff0000]**extreme caution**[/COLOR], for 2 reasons:
A "user" found this, and as I said "It screams 'red flag'".

Sandbox.
install ptu
sniff it out. # find out what ports are used? wink wink nudge nudge

Why are the "users" doing trying to expose hosts inside the LAN, and how is that in context of their usual daily duties? 

What could possibly be that important to someone _***inside***_ of your network to someone outside your sphere?

I certainly wouldn't flat out allow it but it does provide an opportunity for the OP to deploy his own version of ptu
for the "users" at his "company".

If it were my company and I could do so, I'd set Policy and inhibit those abilities from the users, (and educate them)
while taking a "We're evaluating the service." during which time you sandbox, install, read, try, try, try again...
I would have deployed a vm.local somewhere and been all over it. 

That's just me.
</grain_of_salt>

Well put. The point is though that we don't know if it is phoning home and we don't know where that home may be. There certainly is a risk. Honestly, I don't have time nor am I really interested in testing it atm.

Regards..

---

