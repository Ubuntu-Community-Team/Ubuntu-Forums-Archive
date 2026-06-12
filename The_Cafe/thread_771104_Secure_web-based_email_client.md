---
title: "Secure web-based email client?"
date: 2008-04-27
forum: The Cafe
---

### Post by hellmet on 2008-04-27
Recently, my Gmail got hacked, and along with it went 137Euros from Paypal..
I also use Google apps for my domain. But after this incident, I've been scared and shocked to ****, and I've strongly resolved to never use Gmail again.
I am looking to host my own email and I want your opinion on the most secure web-based email client. Something that cannot be hacked easily, and is not possible to sniff cookies right from under my nose!! 

I am ready to make a small investment in buying the web-based client if needed. But, it should be Strong, Secure, possibly non-cookie based, SSL enabled, and must have all other privacy and security features that are sanely possible in an email client.
I'm not talking of data/email encryption. My emails aren't top-secret things. I want the email client to be un-hackeable. Impossible to get into.

What do you guys think of using Outlook (on windows) and Evolution (on ubuntu) to fetch email directly from server without actually using a web-based email client?

Feedback highly appreciated!!

Btw, both times that my Gmail was hacked, I was on Windows. Would being on Ubuntu have saved me from this nightmare?

---

### Post by MaindotC on 2008-04-27
The ability to hack the email is based on several standards to which most email clients adhere.  For example, you don't need a specific email client, you need a client that implements the use of SSL.  SSL is a method of secure communication between a client and a server.  In fact, I have Gmail and I my email client is Evolution, and every time I retrieve email from Gmail it uses a secure connection to Gmail (SSL).

So, I don't think it's particulary a new email client you're seeking, but the proper use of secure email.  There are many other factors such as someone on the same LAN as you sniffing your traffic, session hijacking, or a nifty little tool called ParrosProxy, but I think the first concern you should have is utilizing email properly.

Can you talk about your experience and how it happened?  Did you post it on another forum anywhere like complaints.com?

---

### Post by hellmet on 2008-04-27
Its a long story :
Note: I've always used [https://mail.google.com](https://mail.google.com) to check email.

My GF and I broke up. So, I remove her from my orkut friend's list. 
She is infuriated and since she knows my password, she keeps logging in and adds herself as a friend. 
Tired of this, I change my password, and then she calls up her hacker friend and there he steps in. 
I have no idea what that guy did, but a later serious talk with my GF revealed that he stole my cookie and has access to both Orkut and gmail. 
Successive password changes were all in vain, since that guy had the cookie. And I've read cookies last for 14 days.
That was 5th or 6th Apr

Again 22nd Apr - I cannot login to Gmail, and find my password was changed.
I change it back, and nothing happens for a few days.
Yesterday, it was a war of passwords, where I was setting stronger passwords but my account was still being hacked into easily and pwd changed in a matter of seconds.
Even a 32 character long pwd didn't work.
I surrendered and slept at 6am finally.
Woke up in the morning and determined to stop using gmail, I started backing up emails, and attachments, and that was when I realised that this was my Paypal address too.
I login to Paypal, and there I have transaction right from 6th April to 27th Apr worth 137Euros.

I've changed my Paypal Primary email, and have removed all credit cards and bank accounts. Changed pwd and security question.

You say SSL would help, but even though I always login thru https:// my account still got hacked!!

---

### Post by MaindotC on 2008-04-27
Why'd you break up with her?

---

### Post by hellmet on 2008-04-27
That doesn't help.

---

### Post by SuperSon!c on 2008-04-27
> **hellmet said:**
> Its a long story :
Note: I've always used [https://mail.google.com](https://mail.google.com) to check email.

My GF and I broke up. So, I remove her from my orkut friend's list. 
She is infuriated and since she knows my password, she keeps logging in and adds herself as a friend. 
Tired of this, I change my password, and then she calls up her hacker friend and there he steps in. 
I have no idea what that guy did, but a later serious talk with my GF revealed that he stole my cookie and has access to both Orkut and gmail. 
Successive password changes were all in vain, since that guy had the cookie. And I've read cookies last for 14 days.
That was 5th or 6th Apr

Again 22nd Apr - I cannot login to Gmail, and find my password was changed.
I change it back, and nothing happens for a few days.
Yesterday, it was a war of passwords, where I was setting stronger passwords but my account was still being hacked into easily and pwd changed in a matter of seconds.
Even a 32 character long pwd didn't work.
I surrendered and slept at 6am finally.
Woke up in the morning and determined to stop using gmail, I started backing up emails, and attachments, and that was when I realised that this was my Paypal address too.
I login to Paypal, and there I have transaction right from 6th April to 27th Apr worth 137Euros.

I've changed my Paypal Primary email, and have removed all credit cards and bank accounts. Changed pwd and security question.

You say SSL would help, but even though I always login thru https:// my account still got hacked!!

it sounds like your *system* was compromised - don't lay blame on gmail.  that just happens to be sensitive information they/he obtained from your box.  also, are you on wireless?

---

### Post by MaindotC on 2008-04-27
Sorry about that, OP - just curious.  Yeah it could be your system - he could have popped VNC on there and watched what you're doing.  Could have had the ex install a keylogger on your computer if she was able to carry out those instructions.  Wireless is another good point - they cracked it on Hak5 and when that happens sniffing is all the more easier.  In any event, it sounds like his email account is still in control by someone else and I'm not sure how you'd resolve that without working directly with Gmail staff.

---

### Post by maniacmusician on 2008-04-27
> **SuperSon!c said:**
> it sounds like your *system* was compromised - don't lay blame on gmail.  that just happens to be sensitive information they/he obtained from your box.  also, are you on wireless?
Agreed, if this account is actually true to its details, then it was a system issue (translation: probably because you were on Windows -- that is, if this account is completely true). Cookies are something that are stored on your actual computer.

Though I don't really understand how that would work. Even if he obtained active session cookies from your computer, I don't think it's logically feasible that he could create a direct, secure connection to GMail through them. GMail uses a combination of cookies to identify your user session and your login status, but it also has a direct, https connection to your computer. 

I just don't understand how he could have created a https connection with your login information considering that usernames and passwords are traditionally not stored in cookies, and definitely wouldn't be with GMail. The cookies are just supposed to contain information about the session that you engaged in with email, such as whether you're logged in or out. Or at least that was my understanding of it. Maybe it's flawed.

Anyone have a reasonable explanation?

---

### Post by MaindotC on 2008-04-27
I think the issue is that the ex gave the h4x0r the username//password to his account.  I don't think it really has anything to do with cookies.

---

### Post by hellmet on 2008-04-27
From what I heard, it is Mozilla Firefox that helps these hackers get the cookie easily. I'm not sure if Firefox on Linux would be more secure to these attacks. 
My google apps email hasn't been hacked yet, even though there were emails exchanged between my GMail and GoogleApps email. He could have easily done that too, since the latter has another Paypal account associated with it.
Anyways, what has happened has happened. Its time to secure my email, and my system.

---

### Post by billgoldberg on 2008-04-27
Yeah, gmail here isn't to blame.

Either he installed some keylogger on your pc (if you are on windows) or your wireless connection is to blame.

It's time for a clean install of the OS you were using.

And the next thing to do is go to the cops. Not knowing the law from your country, I think he and she can be blamed with invasion of privacy and stealing.

---

### Post by hellmet on 2008-04-27
> **strAlan said:**
> I think the issue is that the ex gave the h4x0r the username//password to his account.  I don't think it really has anything to do with cookies.
That could have been possible the first time. How about the second time?

---

### Post by hellmet on 2008-04-27
> **hellmet said:**
> That could have been possible the first time. How about the second time?
Update : Password just got changed again!! And he also changed my primary address!!
I can't recover my password for 24 hrs.. I guess!!

---

### Post by SuperSon!c on 2008-04-27
> **SuperSon!c said:**
> ..are you on wireless?

^

---

### Post by hellmet on 2008-04-27
> **hellmet said:**
> Update : Password just got changed again!! And he also changed my primary address!!
I can't recover my password for 24 hrs.. I guess!!
Update 2 : Gets hold onto my yahoo address. I had just updated my Paypal primary address to the Yahoo thing. He now has access to my yahoo and paypal again.I need quick help!!

---

### Post by cardinals_fan on 2008-04-27
> **hellmet said:**
> Update 2 : Gets hold onto my yahoo address. I had just updated my Paypal primary address to the Yahoo thing. He now has access to my yahoo and paypal again.I need quick help!!
Use a different computer!  This one is likely compromised!

EDIT: How do you know that he has your Yahoo?

---

### Post by SuperSon!c on 2008-04-27
hey, good luck.

---

### Post by macogw on 2008-04-27
Stop using the computer on which he seems to have a keylogger, duh!  And for the cookie thing, you could also be being side-jacked...the cookie isn't transmitted encrypted with GMail.  Also, he doesn't need your Yahoo pass to get your Yahoo mail, just sniff your packets.  Only the login page is encrypted.  The email's wide open.

---

### Post by MaindotC on 2008-04-27
Do you notice your hard drive running a lot when you're not doing anything on the computer?  Like after the first 60 (for Ubuntu - Windows is like 10 minutes) seconds you shouldn't see the light come on unless you start an application.

---

### Post by hellmet on 2008-04-27
Is it possible to use the Keylogger even on Ubuntu?
I switched to Ubuntu just half hour ago. He also deteled my yahoo domain account now.
He also changed the security stuff that can help me recover my yahoo pwd.. so Yahoo is locked too.

Btw, I'm from India, and there is no such thing as Cyber-crime police..
There was just news of forming one soon a few days back.
But, I'm in the US right now, so can I file a complaint?

---

### Post by hellmet on 2008-04-27
> **strAlan said:**
> Do you notice your hard drive running a lot when you're not doing anything on the computer?  Like after the first 60 (for Ubuntu - Windows is like 10 minutes) seconds you shouldn't see the light come on unless you start an application.
Yeah.. this happened once .. I mean I noticed it once before.

---

### Post by billgoldberg on 2008-04-27
> **hellmet said:**
> Is it possible to use the Keylogger even on Ubuntu?
I switched to Ubuntu just half hour ago. He also deteled my yahoo domain account now.

Btw, I'm from India, and there is no such thing as Cyber-crime police..
There was just news of forming one soon a few days back.
But, I'm in the US right now, so can I file a complaint?

No, but if someone got **physical access** to your machine, you can be compromised.

I'm 100% sure the US have laws that make this illegal. But that won't do much if that guy is in India, file a complaint there. I'm sure it's illegal in India to steal money from someone and to invade his privacy.

---

### Post by hellmet on 2008-04-27
> **hellmet said:**
> Yeah.. this happened once .. I mean I noticed it once before.
Update3 : My NEW rediffmail also hacked..

---

### Post by SuperSon!c on 2008-04-27
Are You On Wireless

---

### Post by macogw on 2008-04-27
> **hellmet said:**
> Is it possible to use the Keylogger even on Ubuntu?
I switched to Ubuntu just half hour ago. He also deteled my yahoo domain account now.
He also changed the security stuff that can help me recover my yahoo pwd.. so Yahoo is locked too.

Btw, I'm from India, and there is no such thing as Cyber-crime police..
There was just news of forming one soon a few days back.
But, I'm in the US right now, so can I file a complaint?

There are hardware keyloggers...make sure nothing's between your keyboard and the computer.  And yes, of course there are keyloggers for Linux.  And rootkits.  Please check for a hardware keylogger, and then run from a live cd...preferably rebooting every half-hour to hour or so so that anything he's done to your live system is wiped.  And if you're using wireless, open an encrypted VPN tunnel if you can...if you can't, get on a wired connection ASAP.

---

### Post by hellmet on 2008-04-27
I'm on a wired connection. 
If that guy installs a keylogger/rootkit whatever, will I be able to know it thru the 'History' in Synaptic?

---

### Post by SuperSon!c on 2008-04-27
no, and there are hardware loggers out there too. just for kicks i'd inspect your connections closely.

---

### Post by phaed on 2008-04-27
If somebody took money from your PayPal account, why don't you have him reported to the police?  They can find him.  Even if he  used a anonymization service, the money went *somewhere*.  Just follow the money.  He won't be bothering you anymore when he's behind bars.

---

### Post by cardinals_fan on 2008-04-27
As previously stated, try using Live CD's.  If you continue to have problems, then your hardware must be compromised.  Call Paypal and report what has happened so he can't steal any more cash.

---

### Post by hellmet on 2008-04-27
I just went to the police. The officer noted down my details, and has asked me to meet the detectives next monday. Meanwhile, I've been adviced to block my credit cards, and gather as much info about that person as possible.
I just hope, with my fingers crossed, that people get hold onto him, and press charges against him. The only problem is that he's in India. 
Cyber-Police is virtually non-existent. No pun-intended.
I was just able to recover my Yahoo and Paypal accounts .. 
It just shocked me to see that it was sooo easy to recover my password from an old password receovery email!! 
Gmail's pwd recovery email didn't work again though.

---

### Post by hellmet on 2008-04-27
Did you say NO to my previous post?
So, its not possible to know if someone installed a  keylogger or a Root-kit?? That sends shivers down my spine!!

---

### Post by macogw on 2008-04-28
> **hellmet said:**
> Did you say NO to my previous post?
So, its not possible to know if someone installed a  keylogger or a Root-kit?? That sends shivers down my spine!!

He's probably not dumb enough to pull one from Synaptic...nevermind that they aren't even available in Synaptic.  He would likely have compiled in /tmp then deleted the evidence of compilation....some obscure binary buried somewhere on the system would contain it.  And if it's kernel-level, nothing can detect it.  The kernel would hide it all for him.  Common screwups though are to have a rootkit that accidentally breaks things like unpopular flags for ls or cp or various other basic UNIX tools.

---

### Post by MaindotC on 2008-04-28
> **hellmet said:**
> Did you say NO to my previous post?
So, its not possible to know if someone installed a  keylogger or a Root-kit?? That sends shivers down my spine!!

I took a security class in school and we used a book by Ed Skoudis called Counter-Hack: Reloaded.  It doesn't get too technical but it delves into conceptual things.  Keyloggers and root-kits generally operate in "kernel mode" which means they have direct access to memory addresses and allocations that the operating system generally has specifically allocated for specific hardware and software.  When you operate in kernel mode, you can manipulate the operating system to your desire, and that means telling programs like Avira and Symantec to turn the other cheek when they normally would report a detection.

This is a rather complex operation so it's usually automated.  I haven't had the opportunity to examine a rootkit and how it works, but I'm assuming as rootkits become more advanced, there are certain things that a computer would do that programmers or rootkits assume users of rootkits don't want to happen.  For example, they probably have it disable the hard drive light so that you don't notice its running when it shouldn't.  They probably have the keylogger look for specific entries that correlate to specific variables embedded in a web browser ($USERNAME, u_Name, FName, First_Name, etc).  They probably have these stored someplace obscure, and they probably arrange for these things to be emailed or sftp'd at intervals when little or no user activity is detected.

These are all assumptions, but would you know if a root kit or key logger is installed on your system?  Absolutely not - otherwise what good would it be?

---

### Post by hellmet on 2008-04-28
That is bad news strAlan.. but judging by the way Linux is looked upon by Indians, I assume this guy ain't very familiar with Linux either. And, add to it the fact that he no longer has access to credit card information, he could start cooling down, though not so soon.
Does anybody know how long a Gmail cookie lasts though? The last I heard was 2 long years.. If thats the case, I can forget my Gmail ID.

---

### Post by imronak on 2008-04-28
Sanjay,

I would suggest , you should contact all the banks etc where u have placed money. And yes, i also have the opinion that its not because of the cookie. But if you think so, you might want to contact google, may be they can help. And, yes if he is using a static IP (not BSNL ADSL), then his IP address can also be recorded. Contact google and you may hit something interesting. 

And yes, even though there are not many cyber crime laws, you can easily file a case against that sob. India needs cases like these where the cyber crime is brought up and someone is actually been convicted. 

And, even though he might be in India, I am pretty sure U.S. laws guide you so as to catch the sob, because you are probably using a service in US and paid in US for it. let him take a cent and see if he can be caught.

contact paypal and see where that money was spent. keep posted here. it would be interesting to know what goes on. all the best :)

---

### Post by PartisanEntity on 2008-04-28
Don't cookies become useless once a password is changed? i.e. If I steal person A's cookie at 2:00 and they change their password at 2:05, doesn't the cookie I stole from them earlier 'stop working' after that and require me to log-in?

Also, are you using any anonymity software like TOR? That could also be the problem. Make sure you are connecting directly to your ISP and not through some dubious proxy.

P.s. you should shut down this computer, and go to a friend or relative and change your passwords from there, and before you change your passwords, make sure to change any 'reference' email addresses stored in these accounts.

---

### Post by Vajk on 2008-04-28
I wish you all the best, pls keep posting the news.
You might want to check this e-mail service: 
[http://www.hushmail.com/](http://www.hushmail.com/)
As other people already suggested you should do a fresh install and check your hardware for suspicious things.

---

### Post by SuperSon!c on 2008-04-28
also, if you don't have a router, i seriously suggest purchasing one.  perhaps he's compromised the one you have currently - reset to defaults and change the username (if you can) and password immediately.  go to [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm) and use one of those strings, don't be using anything you can remember and type down.  use one you have to copy/paste.

and with the luck you're having, i would invest in an [Iron Key thumb drive]("https://www.ironkey.com/") for your passwords and any other sensitive information (bank info, etc).

---

### Post by hellmet on 2008-04-29
Though that idiot cancelled all my unauthorised claims with Paypal, Paypal still reversed all payments to my credit cards. I think these reversals are still in the pending state, since I can't see them back in my credit card accounts online. This is good news.. but I still have my fingers crossed. I just hope everything goes fine.

---

### Post by hellmet on 2008-04-29
> **imronak said:**
> Sanjay,

I would suggest ,...

How did you get my name? :(

---

### Post by SuperSon!c on 2008-04-29
check your profile.

---

### Post by PartisanEntity on 2008-04-29
> **hellmet said:**
> How did you get my name? :(

Your name is on your blog that you link to :)

---

### Post by Raven_Oscar on 2008-04-29
Agree with all who said that it seems that your system or/and communication lines are compromised. As for hardware keyloggers it seems to be too complicated method to be used just to harm you for fun. But anyway try to use completely different pc.
Now what you should do is to contact to all banks and block all your cards because of fraudulent (Do-Not-Honor status should be more than enough) activity. Even more they mast be listed in stop lists at least in your region. I am not sure about North America rules but in CEMEA and Europe regions all transactions in internet made via your Visa or MasterCard cards and calmed as fraudulent will be canceled and all money returned to your account.

---

### Post by Patsoe on 2008-04-29
> **PartisanEntity said:**
> Don't cookies become useless once a password is changed? i.e. If I steal person A's cookie at 2:00 and they change their password at 2:05, doesn't the cookie I stole from them earlier 'stop working' after that and require me to log-in?

That's certainly true for gmail. I just checked it (had to change password because I accidentally submitted my password as my username ](*,)).

You might want to see if he didn't reset the answer to the security question which allows one to reset passwords too. Edit: never mind that, I missed the part where you said you checked that...

---

### Post by MaindotC on 2008-04-29
> **imronak said:**
> And, yes if he is using a static IP (not BSNL ADSL), then his IP address can also be recorded. 

The attacker's IP address is being logged, regardless, as well as a bunch of other information.  If the attacker is roaming from open access point to open access point, then it could be difficult to locate without surveillance video.

---

### Post by phaed on 2008-04-29
If you have a firewall with all ports blocked / in stealth mode, and you block all icmp requests, how can somebody get access to your computer like we are seeing here?

---

### Post by MaindotC on 2008-04-29
After reading Skoudis's book that I mentioned in a post above, it seems to me that compromising a machine comes in one of two ways:  The machine is left unpatched or non-updated with system fixes - for example there are still several win 95, 98, 2000 machines on the internet; or there is some type of a backdoor - an email with a malicious attachment that when executed disables any security and alerts the attacker of the opening.  Now once that has happened, then that allows all the nifty little tools to be used - Sub7, Metasploit, or even netcat.

As you mentioned about ports being blocked and so forth - security and usability are trade offs.  For example, you can absolutely lock down a system, but then the amount of services you can use on it diminish.  If you want to play a game, you probably need to enable ICMP so it can determine your hop-count to its server.  You'll need to enable a rule in your firewall, and it may even use software that is designed in the interest of features and not known for being secure.

So in reply to your post I'll summarize by saying "it depends".  The more you start to use a machine, typically the less secure it becomes.  OP can you describe some of the programs and services you are running that were not part of the original installation?  Are you using Ubuntu?

---

### Post by Patsoe on 2008-04-30
Far-fetched, but not impossible: if you run a DSL/whatever router with old firmware, that might get hacked (or worse, if you've bought one of those with a standard "admin/admin" set of passwords). Go figure what could happen when someone's sitting on your one route to the net...

---

### Post by hellmet on 2008-04-30
> **strAlan said:**
> After reading Skoudis's book that I mentioned in a post above, it seems to me that compromising a machine comes in one of two ways:  The machine is left unpatched or non-updated with system fixes - for example there are still several win 95, 98, 2000 machines on the internet; or there is some type of a backdoor - an email with a malicious attachment that when executed disables any security and alerts the attacker of the opening.  Now once that has happened, then that allows all the nifty little tools to be used - Sub7, Metasploit, or even netcat.

As you mentioned about ports being blocked and so forth - security and usability are trade offs.  For example, you can absolutely lock down a system, but then the amount of services you can use on it diminish.  If you want to play a game, you probably need to enable ICMP so it can determine your hop-count to its server.  You'll need to enable a rule in your firewall, and it may even use software that is designed in the interest of features and not known for being secure.

So in reply to your post I'll summarize by saying "it depends".  The more you start to use a machine, typically the less secure it becomes.  OP can you describe some of the programs and services you are running that were not part of the original installation?  Are you using Ubuntu?
I was on Vista when my mail etc was hacked. Using Ubuntu right now. The hacker seems to have either stopped hacking, or he has found out the passwords, and is passively watching all acitivity on yahoo/rediff/paypal accounts.
He still holds my Gmail account. I have no idea how to get it from him.

---

### Post by Vajk on 2008-04-30
stick with Ubuntu for a while :) just in case you didn't hear [about]("http://www.pocket-lint.co.uk/news/news.phtml/13702/14726/Ubuntu-laptops-wins-hacking-contest.phtml") it

---

### Post by SuperSon!c on 2008-04-30
sharing any passwords with a g/f is never a good idea to begin with.

---

### Post by MaindotC on 2008-04-30
Patsoe - excellent point.  I remember going around my neighborhood and shutting down the AP's with default SSID's (and thus default passwords) for fun.

> **SuperSon!c said:**
> sharing any passwords with a g/f is never a good idea to begin with.

Or the chequing account...$(*$#

---

### Post by SuperSon!c on 2008-04-30
> **strAlan said:**
> Patsoe - excellent point.  I remember going around my neighborhood and shutting down the AP's with default SSID's (and thus default passwords) for fun.



Or the chequing account...$(*$#

that totally goes without saying.  i really don't understand why people would even think about doing that.  marriage?  that's a different topic.

---

### Post by imronak on 2008-05-01
> **PartisanEntity said:**
> Your name is on your blog that you link to :)

+1. You should know what part of yourself are exposing. :popcorn:

And yes, if a single penny is gone, legal action can be taken, right guys?

---

### Post by HermanAB on 2008-05-01
Hmm, what you really need is a secure web based email *server*.

Citadel supports all the SSL ptocols right out of the box, so I only allow HTTPS, POPS and IMAPS access on my mail system.  I simply blocked the insecure ports in the firewall.

---

### Post by MaindotC on 2008-05-01
> **imronak said:**
> 
And yes, if a single penny is gone, legal action can be taken, right guys?

It depends on a lot of factors - I dunno what it's like in India but in America it would be more cost effective to just refund the money instead of spending money on Paypal employee salary to file the paperwork and the police to actually do something about it.  I sincerely doubt the police will do anything about it.

---

### Post by MaindotC on 2008-05-01
HermanAB if you've been reading this thread it has nothing to do with the email server - he gave out his passwords to his girlfriend who took what seems to be an unjustified revenge on him.

---

### Post by SuperSon!c on 2008-05-01
in short:  there's nothing wrong with gmail - just don't share your passwords.

---

### Post by hellmet on 2008-05-10
Does anybody know how I could contact Gmail? I do have some contacts in there, and Orkut is linked to it. I really need that account. Looks like gmail doesn't take emails anymore at [email]gmail-support@gmail.com[/email]

---

### Post by inportb on 2008-05-13
Oh yeah, have you read this?
[http://www.frenchvanillaicedcoffee.com/2007/12/25/do-you-use-gmail-if-so-you-must-read-this/](http://www.frenchvanillaicedcoffee.com/2007/12/25/do-you-use-gmail-if-so-you-must-read-this/)

---

