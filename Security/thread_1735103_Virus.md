---
title: "Virus"
date: 2011-04-20
forum: Security
---

### Post by hdanap on 2011-04-20
Hi, 

How do i check if ive been hacked from command line, and what to check for

Thanx

---

### Post by NovaAesa on 2011-04-20
What do you mean by "hacked" exactly? What are the symptoms that are making you think you may have been hacked?

---

### Post by hdanap on 2011-04-20
> **NovaAesa said:**
> What do you mean by "hacked" exactly? What are the symptoms that are making you think you may have been hacked?

I got sent a pic file, and after download, ubuntu been acting up, like shut down just loike that

---

### Post by hakermania on 2011-04-21
```
netstat | grep tcp
``` will show you if a hacker is connected to your PC :P
LoL :P

---

### Post by hdanap on 2011-04-21
> **hakermania said:**
> ```
netstat | grep tcp
``` will show you if a hacker is connected to your PC :P
LoL :P

ok, after i type that what do i check for, if it says ESTABLISHED does that mean someone is connected to mt PC?

iF THATS THE CASE, HOW DO I FIX?

THANKX

---

### Post by Grenage on 2011-04-21
> **hdanap said:**
> ok, after i type that what do i check for, if it says ESTABLISHED does that mean someone is connected to mt PC?

iF THATS THE CASE, HOW DO I FIX?

THANKX

There are valid reasons for established connections; after all, you are connected to a network.

Are you still experiencing problems?  Have you ruled out hardware?

---

### Post by hdanap on 2011-04-21
> **Grenage said:**
> There are valid reasons for established connections; after all, you are connected to a network.

Are you still experiencing problems?  Have you ruled out hardware?

I don't think Hardware isn't the problem, cos i  never had this shutdown problem, until i downloaded that picture file i was sent. Don't know what to do

Pls direct some body

---

### Post by Grenage on 2011-04-21
Viruses on Linux don't really exist in the wild; hacking can and does, and it can obviously be targeted.

With than in mind, is the picture file executable?  does it contain any code at all?  Does it open as a picture?  Is it accessible on the internet?

Coincidences do happen.

---

### Post by hdanap on 2011-04-21
> **Grenage said:**
> Viruses on Linux don't really exist in the wild; hacking can and does, and it can obviously be targeted.

With than in mind, is the picture file executable?  does it contain any code at all?  Does it open as a picture?  Is it accessible on the INTERNET?

Coincidences do happen.

It was sent to me via a link, as i was chatting on face book, it an online link, so i dont know if it was executable, after i clicked the link something loaded, then this picture opened up, the funny thing is, ive been looking for what loaded but i cant find it, after about 30mins, bang, my pc shuts down.

Any Thots

---

### Post by slavik on 2011-04-21
moving to security discussions ...

---

### Post by Grenage on 2011-04-21
Ok, now we're getting somewhere.  The TCP output you saw earlier, could you paste it here?

It might also be worth posting the output of:

```
ps ux
```

If you do find the link you clicked on, post it here **BUT** break it up so that nobody can click on it.

---

### Post by bodhi.zazen on 2011-04-21
Penetration testing is complex and you can not trust any commands you run on the compromised machine.

See the links to penetration testing in the security sticky.

With that said, it is a large leap to go from you are having the kind of problem you are describing to you have somehow been compromised or that you have a virus. The links on penetration testing will help, but it is complex.

---

### Post by nec207 on 2011-04-21
> **hdanap said:**
> Hi, 
 
How do i check if ive been hacked from command line, and what to check for
 
Thanx
 
There is no good anti-virus program for Mac OS X or Linux.The companies that make anti-virus programs for windows will not work on these OS and the companies that have a special anti-virus programs are joke that slow down your computer and give you false positive hits.
 
There no money yet for a companies to spend millions of dollars on a anti-virus program having hundreds of programmers and malware specialists making anti-virus program for Mac OS X or Linux.
 
Check the running process ,logs every day .If there is a special new file on the computer or running process use the search command and type in the new file name or running process and delete it.

In future if malware gets any where close to windows for Mac OS X or Linux than you see companies spending millions of dollars on a anti-virus program and having hundreds of programmers and malware specialists making there anti-virus program for profit.

---

### Post by nec207 on 2011-04-21
> **hdanap said:**
> It was sent to me via a link, as i was chatting on face book, it an online link, so i dont know if it was executable, after i clicked the link something loaded, then this picture opened up, the funny thing is, ive been looking for what loaded but i cant find it, after about 30mins, bang, my pc shuts down.
 
Any Thots
 
 
Like the other people saying here there is hardly any malware for non windows base systems.So it looks like a hardware may just by chance.

---

### Post by tgm4883 on 2011-04-22
> **nec207 said:**
> There is no good anti-virus program for Mac OS X or Linux.The companies that make anti-virus programs for windows will not work on these OS and the companies that have a special anti-virus programs are joke that slow down your computer and give you false positive hits.
 
There no money yet for a companies to spend millions of dollars on a anti-virus program having hundreds of programmers and malware specialists making anti-virus program for Mac OS X or Linux.
 
Check the running process ,logs every day .If there is a special new file on the computer or running process use the search command and type in the new file name or running process and delete it.

In future if malware gets any where close to windows for Mac OS X or Linux than you see companies spending millions of dollars on a anti-virus program and having hundreds of programmers and malware specialists making there anti-virus program for profit.

There already exists large corporations making Anti-virus for OSX and Linux

---

### Post by aysiu on 2011-04-22
Saying there aren't any viruses for Linux doesn't really help in this situation.

If this "picture" file sent over was somehow executable, it wouldn't be a virus. It would be a trojan. And if it were executable and the OP launched it, it is very possible it is somehow affecting the functioning of the OS.

To the OP, I don't think you have "been hacked," but it is possible the picture was either malicious or corrupt and somehow launching it has affected your Ubuntu installation. The good thing is, unless you were prompted for and also entered your password, the damage is probably easily reversible--in other words, it probably has affected your user account and not the entire OS installation.

Can you confirm that opening the "picture" revealed it to be an actual picture (in the image viewing application)?

---

### Post by oldmankit on 2011-04-22
It would be super-userful if the OP could find the actual picture...

---

### Post by bodhi.zazen on 2011-04-22
> **nec207 said:**
> There is no good anti-virus program for Mac OS X or Linux.

I do not know about OS X , but clamav on linux works well.

The main use is on a mail server or file server, it scans for windows and linux viruses.

I agree with you, and others, I personally would not run antiviurs on a Linux Desktop.

---

### Post by nec207 on 2011-04-23
> **tgm4883 said:**
> There already exists large corporations making Anti-virus for OSX and Linux
 
 
Less than 1% use Linux and 10 % use Mac computer .
 
What I'm saying is a software maker is going to go where the money is the market share .Most people use windows and most malware is for windows that is where money is .Well more and more people are getting Mac computers now and there is more malware coming out for Mac computer now do to more people getting Mac computer well not any where close to windows with number of malware so in the future it may be profitable for software makers to make software for Mac computers , more and more people get Mac computers and more and more programmers put out malware for Mac computers do to more people get Mac computers ,there will be profit where software to remove the malware.
 
People use Linux are more computer geeky where windows and Mac users plug in and use.There is more ways to change how OS and GUI works and looks with Linux .Where by windows and Mac you like it or leave it that OS the way it is.I don' think Linux will ever get 10% or 15% market share has most people are not geeky enough they just what a plug in and use.

---

### Post by hdanap on 2011-04-24
> **aysiu said:**
> Saying there aren't any viruses for Linux doesn't really help in this situation.

If this "picture" file sent over was somehow executable, it wouldn't be a virus. It would be a trojan. And if it were executable and the OP launched it, it is very possible it is somehow affecting the functioning of the OS.

To the OP, I don't think you have "been hacked," but it is possible the picture was either malicious or corrupt and somehow launching it has affected your Ubuntu installation. The good thing is, unless you were prompted for and also entered your password, the damage is probably easily reversible--in other words, it probably has affected your user account and not the entire OS installation.

Can you confirm that opening the "picture" revealed it to be an actual picture (in the image viewing application)?

Hi, 

yes it was an actual picture, but i have been trying to locate the picture since and it has vanished,

Well i have been doing some reading on Linux, when i found that when i use "uptime" command it tells me how many people have been on my sys since its been on, i find when i restart my box and i use "uptime" there only 2 users, "really don't now how i have to user, cos when i cd / and cd /home, there is only one user there"

After about an hour after i restart my computer if i use the uptime command again, now there are 3 users, What can be the cos of this

thanx

---

### Post by hdanap on 2011-04-24
> **bodhi.zazen said:**
> I do not know about OS X , but clamav on linux works well.

The main use is on a mail server or file server, it scans for windows and linux viruses.

I agree with you, and others, I personally would not run antiviurs on a Linux Desktop.


Hi, is there a manual that can direct me as to find out what might be going on, on me sys.

Thanx

---

### Post by bodhi.zazen on 2011-04-24
> **hdanap said:**
> Hi, is there a manual that can direct me as to find out what might be going on, on me sys.

Thanx

There are whole books written about penetration testing.

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1)

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2)



I suggest you start with a description of your problem.

---

### Post by hdanap on 2011-04-24
> **bodhi.zazen said:**
> There are whole books written about penetration testing.

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1)

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2)



I suggest you start with a description of your problem.

> **aysiu said:**
> Saying there aren't any viruses for Linux doesn't really help in this situation.

If this "picture" file sent over was somehow executable, it wouldn't be a  virus. It would be a trojan. And if it were executable and the OP  launched it, it is very possible it is somehow affecting the functioning  of the OS.

To the OP, I don't think you have "been hacked," but it is possible the  picture was either malicious or corrupt and somehow launching it has  affected your Ubuntu installation. The good thing is, unless you were  prompted for and also entered your password, the damage is probably  easily reversible--in other words, it probably has affected your user  account and not the entire OS installation.

Can you confirm that opening the "picture" revealed it to be an actual picture (in the image viewing application)?

Hi, 

yes it was an actual picture, but i have been trying to locate the picture since and it has vanished,

Well i have been doing some reading on Linux, when i found that when i  use "uptime" command it tells me how many people have been on my sys  since its been on, i find when i restart my box and i use "uptime" there  only 2 users, "really don't now how i have to user, cos when i cd / and  cd /home, there is only one user there"

After about an hour after i restart my computer if i use the uptime  command again, now there are 3 users, What can be the cos of this

thanx

ps. my sys keep shutting down, and this never happened

---

### Post by tgm4883 on 2011-04-24
> **hdanap said:**
> Hi, 

yes it was an actual picture, but i have been trying to locate the picture since and it has vanished,

Well i have been doing some reading on Linux, when i found that when i  use "uptime" command it tells me how many people have been on my sys  since its been on, i find when i restart my box and i use "uptime" there  only 2 users, "really don't now how i have to user, cos when i cd / and  cd /home, there is only one user there"

After about an hour after i restart my computer if i use the uptime  command again, now there are 3 users, What can be the cos of this

thanx

ps. my sys keep shutting down, and this never happened

Every terminal you open counts an another user

---

### Post by HermanAB on 2011-04-24
Howdy,

The command 'who' will tell you who is connected to your computer and how.

---

### Post by oldmankit on 2011-04-24
> **ciaraa said:**
> Hello,
               The first knowledge you may have is the sudden reduction of your financial accounts from a healthy balance to a nasty deficit. Or applying for something only to find someone else has already applied for it as you; what's referred to as identity theft. Not the most pleasant of surprises. Something I would presume we would all like to avoid.


I'm not saying this is impossible, but even with root access to your computer, most modern internet banking (at least in the UK) cannot be done with details solely found on the computer.  There are many layers of protection, so before a new third party payment can be set-up (what is needed for a cracker to actually get your money), they need an extra thing, for example:

[LIST]
[*]access to your telephone (the bank calls your phone automatically before setting up the payment)
[*]access to your card+pin (to get an access code from a card reader)
[/LIST]
So even if they key-logged or digged-up your password, PIN and memorable data, it would still not be enough.

---

### Post by d3v1150m471c on 2011-04-24
you probably don't have the image anymore, or it's inside the cache for whatever browser you're using. It'd make more sense to provide the link to where you encountered said picture but don't paste it here as an actual hyperlink so someone doesn't click on it. I'd personally like to take a look at it myself.

Also `netstat | grep tcp` isn't going to show you root connections if it even shows you the right connections at all. It's possible for a successful hacker to hide a trojan IF you've been hacked. best to use
```

sudo netstat -n | grep -i established
sudo netstat -ln # for listening ports

```

---

### Post by Spyderkid on 2011-04-25
i have an idea...


install Firewall (ufw) from the sofware centre and set the prefrences to FULL

---

### Post by nec207 on 2011-04-28
> **Spyderkid said:**
> i have an idea...
 
 
install Firewall (ufw) from the sofware centre and set the prefrences to FULL
 
A firewall will not stop malware from getting on his computer.

---

### Post by tgm4883 on 2011-04-28
> **nec207 said:**
> A firewall will not stop malware from getting on his computer.

On a Linux machine, you are probably right. On a Windows machine oh yea it will help

---

### Post by nec207 on 2011-04-28
> **tgm4883 said:**
> On a Linux machine, you are probably right. On a Windows machine oh yea it will help
 
 
The only firewalls I have worked with is the windows firewall and zone-alarm.I have no training at all on router firewall .
 
If some of you have more training how a router firewall stops hackers and so good than please explain.Or how a firewall can stop malware.
 
Anyone here that has more training with working with firewalls and router firewalls.

---

### Post by tgm4883 on 2011-04-28
> **nec207 said:**
> The only firewalls I have worked with is the windows firewall and zone-alarm.I have no training at all on router firewall .
 
If some of you have more training how a router firewall stops hackers and so good than please explain.Or how a firewall can stop malware.
 
Anyone here that has more training with working with firewalls and router firewalls.

Well if a threat tries to use a certain port to spread then if you are using a firewall to block that port it can't connect to your machine.

---

### Post by nec207 on 2011-04-28
How does a router firewall work? Can it block ports and monitor port scanning ?
 
It has real time monitor ?

---

### Post by tgm4883 on 2011-04-28
> **nec207 said:**
> How does a router firewall work? Can it block ports and monitor port scanning ?
 
It has real time monitor ?

Same way that a software firewall works. Some are more sophisticated than others but all/most only allow specified traffic.

---

### Post by nec207 on 2011-04-28
> **tgm4883 said:**
> Same way that a software firewall works. Some are more sophisticated than others but all/most only allow specified traffic.
 
The $40 router firewall are no good?

---

### Post by bodhi.zazen on 2011-04-28
> **nec207 said:**
> The $40 router firewall are no good?

A better question is good for what ? Probably sufficient for most home users, probably not the fastest router, especially on the wireless side.

Hardware firewalls can be much more sophisticated and can include a number of features from speed to VPN ports to content filtering to monitoring ports to additional security features.

See most anything on the cisco site =)

Those beasts are obviously overkill for the vast majority of home users.

---

