---
title: "E-Mail Hacked?"
date: 2011-07-12
forum: Security
---

### Post by GarlicBread on 2011-07-12
Hi

I'm fully aware that Linux, and Mac OS X are a far reach from Windows when it comes to viruses.  I run Xubuntu 11.04 on the netbook, and Mac OS X 10.4 on a Mac Mini.  But, and I now wish I kept the e-mail and didn't delete the account, but the following happened recently:

I received an e-mail, from myself (I was on my own contacts list) that was sent to a few others on my contacts list - an e-mail I DID NOT send out.  There was no subject, and an unclickable link that - once copy/pasted and gone to, was "Forbidden," even when you took the /s away and went to the main site, it was "Forbidden."  It was a .be website (Belgium).  Being that one of the recipients was "noreply@craigslist.com" I can only assume that this e-mail was automated.  It was only sent to a few addresses, all of which were tied to my account.  I changed the password, deleted my contacts, and deleted the address (and have a new one elsewhere).

I ran ClamAV on here, an anti-virus on my Mac Mini (and I'm running a DIFFERENT one now), and thus far, absolutely nothing.

So my question is - Is it, then, even reasonably possible that either of my computers are infected, and if not, how did this occur?  I'm just taken aback a little, considering I don't use or have Windows on any machine that I own, and EXTREMELY rarely use Windows when elsewhere (and not at all recently).

---

### Post by GarlicBread on 2011-07-12
Also, it was an @live account (hotmail) which, as you probably know, is run and owned by Microsoft.

---

### Post by karlson on 2011-07-12
> **GarlicBread said:**
> 
So my question is - Is it, then, even reasonably possible that either of my computers are infected, and if not, how did this occur?  I'm just taken aback a little, considering I don't use or have Windows on any machine that I own, and EXTREMELY rarely use Windows when elsewhere (and not at all recently).

Receiving an e-mail from yourself to some bogus address is not uncommon.  You might be surprised at how many mail servers out there that are misconfigured to allow email forwarding from any domain.

It may not be reasonable to assume that you are infected but it is fairly reasonable to assume that clicking on the link in the email may have validated your email as valid.

Beyond that you might want to check for open ports and processes running as your UID that you don't recognize.

---

### Post by karlson on 2011-07-12
> **GarlicBread said:**
> Also, it was an @live account (hotmail) which, as you probably know, is run and owned by Microsoft.

The situation you describe is why I don't use it any more.

---

### Post by GarlicBread on 2011-07-12
> **karlson said:**
> Receiving an e-mail from yourself to some bogus address is not uncommon.  You might be surprised at how many mail servers out there that are misconfigured to allow email forwarding from any domain.

It may not be reasonable to assume that you are infected but it is fairly reasonable to assume that clicking on the link in the email may have validated your email as valid.

Beyond that you might want to check for open ports and processes running as your UID that you don't recognize.

I know using my e-mail as the "From" field is easy for anyone to do, what gets me is that my account had to have been accessed to e-mail who it e-mailed - all things in my contacts (and like I said, I'm fairly certain it was automated, because no one would bother e-mailing [email]noreply@craigslist.com[/email]).  I just wonder - if it's NOT one of my computers, what is going on here.

It wasn't a clickable link (I wouldn't have clicked it), it was just text, I copy/pasted it into the browser.  I found it entirely suspicious, considering there was nothing AT the link, and running anti-viruses even after nothing was picked up (other than a handful of tracking cookies).

The last paragraph, I apologize, I am so computer illiterate that I don't understand what you mean there.

---

### Post by tudor117 on 2011-07-12
It is also possible that you were culprit to a social engineering attack. That means, someone tricked *you* into giving them your password (obviously without you noticing it).
This can happen in many different ways...
[LIST=1]
[*]You put in your email and password for a site that pretended to look like hotmail. Always check the url.
[*]You went on a public wifi network. (And arp-poisoned....)
[*]Your own private wifi network is open, or got cracked and you were arp poisoned.
[*]You use the same password for multiple sites, one of the sites was hacked and leaked your password, or the previous methods apply to another site.
[*]Something I haven't thought about...
[/LIST]

If one of those were to have happened, you most likely do not have a virus.

---

### Post by karlson on 2011-07-12
> **GarlicBread said:**
> I know using my e-mail as the "From" field is easy for anyone to do, what gets me is that my account had to have been accessed to e-mail who it e-mailed - all things in my contacts (and like I said, I'm fairly certain it was automated, because no one would bother e-mailing [email]noreply@craigslist.com[/email]).  I just wonder - if it's NOT one of my computers, what is going on here.

It actually is not that you would need to look at the headers it should have a source IP address of the email.  This will give you a sort of trace of where the email has originated.

> It wasn't a clickable link (I wouldn't have clicked it), it was just text, I copy/pasted it into the browser.  I found it entirely suspicious, considering there was nothing AT the link, and running anti-viruses even after nothing was picked up (other than a handful of tracking cookies).

This is still not a good idea.

> The last paragraph, I apologize, I am so computer illiterate that I don't understand what you mean there.

The advantage of Linux and MacOS is that you separation of SuperUser(Administrator) and a regular user, so if you did pick up a virus which I doubt it would run as a process under your user ID.  You can launch a terminal and run a ```
top -u <userid>
``` to see what is running, but if you are not familiar with services and hence the processes running you may not be able to tell the difference if anything is out of place.

---

### Post by GarlicBread on 2011-07-12
> **tudor117 said:**
> It is also possible that you were culprit to a social engineering attack. That means, someone tricked *you* into giving them your password (obviously without you noticing it).
This can happen in many different ways...
[LIST=1]
[*]You put in your email and password for a site that pretended to look like hotmail. Always check the url.
[*]You went on a public wifi network. (And arp-poisoned....)
[*]Your own private wifi network is open, or got cracked and you were arp poisoned.
[*]You use the same password for multiple sites, one of the sites was hacked and leaked your password, or the previous methods apply to another site.
[*]Something I haven't thought about...
[/LIST]

If one of those were to have happened, you most likely do not have a virus.

I always type in live.com so it isn't that... I never go on, nor do I have, a public wifi network... I DO have little variety when it comes to passwords.  Which was one thing I was thinking, that my password was a matter of using the password of an associated account with the e-mail (which in many cases, would have resulted in this working).

---

### Post by GarlicBread on 2011-07-12
> **karlson said:**
> It actually is not that you would need to look at the headers it should have a source IP address of the email.  This will give you a sort of trace of where the email has originated.



This is still not a good idea.



The advantage of Linux and MacOS is that you separation of SuperUser(Administrator) and a regular user, so if you did pick up a virus which I doubt it would run as a process under your user ID.  You can launch a terminal and run a ```
top -u <userid>
``` to see what is running, but if you are not familiar with services and hence the processes running you may not be able to tell the difference if anything is out of place.

I wish I hadn't deleted it, so I could find the source IP but... too late.  I agree it was stupid of me to go to that URL, my nonsensical justification at the time was "I'm not using Windows so nothing bad ever happens."  I did use that source code, nothing seemed unusual at least to me.  But, like you said, I'm not very familiar.

So at the end of the day, when it comes down to it - would you assess that this is a "social engineering" attack of some sort and not an attack coming from my own computers?

---

### Post by karlson on 2011-07-12
> **GarlicBread said:**
> So at the end of the day, when it comes down to it - would you assess that this is a "social engineering" attack of some sort and not an attack coming from my own computers?

Looks that way.

---

### Post by GarlicBread on 2011-07-12
> **karlson said:**
> Looks that way.

Damn the man.  Well, at least I deleted that account.  And I'm pretty sure nobody in my neighborhood is secretly accessing my wifi... old and/or computer illiterate types... nobody I could imagine around here that would have that kind of capability or computer smarts.

Thanks a bunch!

:KS:KS:KS

---

### Post by doas777 on 2011-07-12
I am pretty sure that the problem is on someone else's server, not your PC. the others have described several ways this may have occured, (common use of same uname/passwd pair, bruteforce, xss, etc.)

---

### Post by Dangertux on 2011-07-13
I agree with everything here except I want to make one clarification.

Someone mentioned ARP poisoning. In this case typing the URL would not matter. The way ARP poisoning works (man in the middle), you will type the address correctly, but it will resolve to something other than what it is actually supposed to resolve to usually a clone of the actual site. 

Just wanted to clarify that.

---

### Post by GarlicBread on 2011-07-13
> **Dangertux said:**
> I agree with everything here except I want to make one clarification.

Someone mentioned ARP poisoning. In this case typing the URL would not matter. The way ARP poisoning works (man in the middle), you will type the address correctly, but it will resolve to something other than what it is actually supposed to resolve to usually a clone of the actual site. 

Just wanted to clarify that.

I did a little research when that was brought up... for someone to intercept my network signal, and doing a little work before connecting me to the net (which would mean they are local) isn't likely considering my location.  This case, to me, is highly improbable.

Based on everything that has been said, I find it highly likely that my username and password on some website were obtained, and the password was attempted (with success) with the associated e-mail address.  That, or it's @live, and I've heard of Microsoft having problems being hacked in the past.

---

### Post by GarlicBread on 2011-07-13
> **doas777 said:**
> I am pretty sure that the problem is on someone else's server, not your PC. the others have described several ways this may have occured, (common use of same uname/passwd pair, bruteforce, xss, etc.)

bruteforce/xss?

---

### Post by GarlicBread on 2011-07-13
I'd also note that, this was the only of my e-mail addys that I'm aware of this happening with, and was the one I used most by far - meaning it was restricted to this individual account.  I've had no other problems.

---

### Post by GarlicBread on 2011-07-13
I just checked the SECOND Mac OS X anti-virus scanner I used, and found that there were seven "Exploit.Java.CVE-2010-0840.c" trojans, named things like "Troj/JavaBz-G."  The thing is, when you go to the Sophos Anti-Virus site regarding the viruses, under what OSs are effected, it only has Windows... would that not mean these are stagnant viruses that are useless on my OS, and have nothing to do with this?

---

### Post by mr-woof on 2011-07-13
I do get messages from myself on hotmail, I think it's probably something along these lines, spoofed sender addresses

[http://en.wikipedia.org/wiki/Joe_job](http://en.wikipedia.org/wiki/Joe_job)

I'm 99%, my machine(s) don't have any problems

---

### Post by doas777 on 2011-07-13
> **GarlicBread said:**
> bruteforce/xss?

bruteforcing is a method for breaking a password, simply by trying every option, or by using a dictionary of common terms/passwords. for sites that don't lockout your account after X number of bad login attempts, brutforcing will always work, though it may take years or decades, or even centuries for strong passwords. you defeat bruteforcing by using a password that is 8+ characters, consisting of upper and lower case letters, numbers, and special characters. for an 8 char password with all 4 kinds of chars, the number of combinations for your password is (assuming 52 alpha, 10 numeric, and 10 special chars) 72^8 possible answers (722,204,136,308,736).

XSS (Cross Site Scripting) is a form of attack that someone may leverage against a website you are logged into to steal your legitimate access (making it a type of Confused Deputy attack). usually it involves you clicking a malicious link in a forum, which steals your authentication token/cookie. if hotmail is vulnerable to an XSS exploit, and someone sent you an email with a malicious link in it, if you click the link, the person who sent it to you can immediately steal your access, and start sending out emails as  you.

---

### Post by CharlesA on 2011-07-13
It sounds like a phishing attempt to me. If you are worried, change your password and be more careful in the future. :)

---

### Post by Dangertux on 2011-07-13
Unless there is more to the situation I am unaware of.  My money is on header spoofing -- I wouldn't worry about it. 

If you need an internet mail provider I would consider using gmail or yahoo. I actually really like yahoo these days, they've really upped their game as far as user security goes.

---

### Post by GarlicBread on 2011-07-13
Thanks again everyone, y'all are great :-)

Shareef may not like it, but you rock the casbah!

---

