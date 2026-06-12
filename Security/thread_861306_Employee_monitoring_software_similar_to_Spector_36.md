---
title: "Employee monitoring software similar to Spector 360 on Windows?"
date: 2008-07-16
forum: Security
---

### Post by gjohns28 on 2008-07-16
Employee monitoring software similar to Spector 360 on Windows?

We are considering at our church switching from Windows to Ubuntu version of Linux but we need to find out what employee monitoring software is available similar to what we use now on Windows which is Spector 360. 

Any suggestions, or experience with any?

Thanks!:)

---

### Post by roaldz on 2008-07-16
> **gjohns28 said:**
> Employee monitoring software similar to Spector 360 on Windows?

We are considering at our church switching from Windows to Ubuntu version of Linux but we need to find out what employee monitoring software is available similar to what we use now on Windows which is Spector 360. 

Any suggestions, or experience with any?

Thanks!:)

may i ask why you´d want to spy/monitor your employees?
you could set up a proxy server (squid) to speed up your web browsing, and use it´s logs to see who´s viewing/downloading what. otherwise maybe some sort of vnc/freenx solution?

---

### Post by gjohns28 on 2008-07-16
Thanks for the reply, but we want to do more to protect the reputation of the church, beyond just websites.

There was a church in the area one year ago where a young man was chatting and contacted an underage girl in a bad way and we can't risk our church ever having this occur, or violence in the workplace, or unacceptable communications between employees so we decided to put in place Spector 360 and it works great, to just let it run and it alerts me if there's a problem with porn, keywords used in website, searches, chat, email.  I need something similar to that for Ubuntu Linux. We don't use it to spy in on employees, unless we are notified of a real problem, then it gives you a chance to talk to folks before its too late.

Surely there is software for Linux that can do this?

Thanks!

---

### Post by spike_strip on 2008-07-16
To help us understand the issue more clearly...if every thing is running well, why do you wish to migrate to Ubuntu[?] 

I belive Sguid – as mentioned previously – will solve most of your issues. 

Have you researched this option[?] and if so what were your findings?

For example, w/ Squid, you could restrict your users from loging into the social networking site.

---

### Post by gjohns28 on 2008-07-16
Hello thanks for the replies.

We haven't had a chance to try anything yet, we just started talking yesterday abou the cost of our equipment and licenses and where Microsoft seems to be going and feel we could save alot of money and have a more stable operating system with Linux.
I want to just setup one test machine first, then expand to 5, 10, so on we've got 40 computers.

I haven't worked with Proxy Servers but can't set it up and do some testing.

To clarify we are very happy with Spector 360, it's Microsoft and the cost, Vista, we are all XP Pro now except 1 Vista laptop for testing.

Thanks!

---

### Post by spike_strip on 2008-07-16
I am not familiar with Sector 360 you might need to contact their tech support and ask them if they have any client support that will run on Ubuntu. 

I do not think you are going to locate a one stop software solution, for Ubuntu. However, you can use Linux and archive your goals.

---

### Post by |{urse on 2008-07-16
Okay, this is merely semantical, but if you wish to migrate to ubuntu for cost reasons be prepared to pay in hours upon hours of learning a new OS and it's software. Why on earth would your church be liable for someone else misusing the resources you provide? As long as there is a contractual understanding between faculty that the system is only for browsing reasonable content/business computing then you are covered against misuse and it's damages. By security software do you mean video surveillance, intrusion protection, or simply nosy software to further the control of your employees? 
If they are doing general web browsing and stumble upon the wrong sort of thing (google slavery (it happens)) are you going to hold that over their heads? Lighten up on your employees and stick to business, if something bad happens then deal with it on a per-case basis, maybe a sinner needs less government and a little churchin' hm?

---

### Post by hyper_ch on 2008-07-17
(1) I do have some issues with a total surveillance of the employees. Are you sure you are within the law? (Here in Switzerland you wouldn't be)

(2) Not sure what exactely spector does but you can do content filtering on a dns level using [http://www.opendns.com/features/content_filtering/](http://www.opendns.com/features/content_filtering/) . All you'd have to do is to switch the router which connects to the internet to use OpenDNS and setup the according filtering.

---

### Post by Keeters on 2008-07-17
This is a little different idea than what most people go with but I would offer up snort as an option. I also work at a church doing somewhat of what you described. We use snort in order to listen not only for attacks against our servers but we also have it monitoring the network for policy violations. Now we decided what those policy violations are, and people are told ahead of time that monitoring would be taking place. Now this is a network solution but it allows for a central management of everything.

---

### Post by gjohns28 on 2008-07-17
Okay, let me clarify further.

Yes it is legal in the US, the company owns the computers and they have the right in the US to monitor the activity on them.

What we use know is a Windows product, but I'm really surprised there isn't an out of the box solution that will work with Ubuntu. I have checked with Spectorsoft and they have ported for Linux yet, they only have Mac and Windows and no plans for Linux.

We are willing to pay for the software just as we've done now on Windows.

I appreciate all the suggestions, but we currently just have to check the status of approx 4 graphs  in Spector 360 to do if we have a problem with porn and how much time has been spent on those sites.  I don't have to dig thru any data to know we have a problem. If I see a problem, I can click once to drill down to get more detil on which user I have a potential problem with, and I can see any detail from there including porn websites visited, along with the active links, keyword searches they might have violated, and many more details.

We took these steps with the Spector 360 software on Windows, to be pro active if a problem should develope with porn, chatting with underage children, violence in the workplace, to try to catch a problem before we end up on the news and our reputation is gone.

I'm not interested in blocking websites, we don't block any websites, when you block folks just look for another way around this to get to site they want.  But we do monitor for problems. We don't have any to spy on employess thru-out the day, the software just gathers up facts and alerts if there is a problem we need to know about, otherwise it's business as usual.

We also have many users with laptops and Spector 360 runs on those laptops, folks take them home if they want to do work from home but when they return to the network the data is gathered and is updated in our database, again we know if there was a problem even while they were off our network.  They are company laptops and to be used for company email, and work when off our network so we can still monitor for problems.

Other further suggestions are welcome, otherwise if no one has any further input this discussion can be closed out Friday or Saturday.

Thanks so much!

---

### Post by tuproxy on 2008-07-17
This is the type of attitude that keeps me out of churches, BUT I'll tell you the best and most appropriate way stop access to porn.  I won't tell you how to spy though. Please read this and tell me why this won't work.  It is employed at 14 chuches I do work for...

What you need:
-Router/firewall (linux box with IPtables)
-Proxy (squid or Dan's Guardian)

Here is the setup.  to limit access from porn/sex sites or underage chatting from certain users, run ALL web traffic through the proxy.  In the firewall, declair that ALL web traffic is only allowed in/out through the proxy machine, so they CAN't get around it.  Close port 22 or restrict access on the firewall so people can't create a SSH tunnel to an outside connection.  Now, all traffic must go through the proxy server based on the firewall rules.  

Now setup the proxy to block key words or use the pre-selected blocked sites that can be installed.  A lot of work is already done for you.  

Why wouldn't this be a middle ground solution?

BTW, this can be done fairly cheaply.  LMK if you want more detials..

---

### Post by sienosis on 2008-07-18
I have been looking for the same type of thing w/o success to monitor our children's computer usage. I just did a live chat with a Spector rep. See below.

Chat InformationPlease wait for a site operator to respond.
Chat InformationYou are now chatting with 'Nelson'
Nelson: Thank you for visiting the SpectorSoft web site. Please state your question along with the name of the software you are interested in.
you: Do you have a Linux (Ubuntu) version of your Spector program?
Nelson: no
you: Any plans to have one or any known similar Linux programs?
Nelson: no
Nelson: have not heard anyone talking about a monitoring software for Linux
you: Can you pass along the request? I know I would use it and there are multiple posts about the same on ubuntuforms.org.
Nelson: I will post it on our suggestion box.
you: Thank you

---

### Post by bapoumba on 2008-07-19
This thread has been reported, and will be watched.

I work at a university, and they block many protocols (IM, IRC etc., which makes sense due to the very large number of potential users on the network, almost 30,000) but they do not spy, and they make clear and public what is allowed and what is not. All the univ network runs on Linux (debian stable), there is a whole department taking care of it.

---

### Post by randomnote1 on 2008-07-21
[QUOTE=sienosis;5414746]I have been looking for the same type of thing w/o success to monitor our children's computer usage./QUOTE]

I just had a conversation with my Aunt who is looking for the same thing.  She has already tried different blocking applications, but true to form, there is always a way around.  At this point she really doesn't want to block content, she wants to hold her kids accountable for what they're doing online.  It looks like Spector definitely has the idea for monitoring children.  I don't know if I would use it in an office environment, but home use definitely seems to be where something like this would fit.

Unfortunately, setting up a Proxy server with SQUID is not an option as the computer that is being used is a Pentium III Gateway that was revived from Windows '98 with Ubuntu.  If anybody knows of anything other than a Proxy server solution, your input would be greatly appreciated.

---

### Post by scorp123 on 2008-07-21
> **hyper_ch said:**
>  (2) Not sure what exactely spector does  It's commercial spy-ware. It records everything you do, makes screenshots behind your back, and upon typing of certain keywords (can be configured) it auto-notifies the admin and sends e-mails containing the "evidence" ... and all this behind your back. :mad:

I once had a case where one employee installed "Spector" and its sister-product "eBlaster" (intercepts e-Mail and IM traffic and forwards everything incl. attachments to the admin) on another employee's desktop PC and laptop .... Without us admins knowing or approving such an action, and especially without the affected employee knowing. :(

Having such programs spy on you isn't really funny.

---

### Post by scorp123 on 2008-07-21
> **randomnote1 said:**
> If anybody knows of anything other than a Proxy server solution, your input would be greatly appreciated. Put the hostnames of unwanted hosts into /etc/hosts and give them an IP of e.g. 0.0.0.0  ....

Example: I don't want anyone to have access to [http://www.vatican.va](http://www.vatican.va) ...

So I'd become root and edit the /etc/hosts file:
```
sudo gedit /etc/hosts
``` ... so that it contains this entry:
```
0.0.0.0    www.vatican.va
``` ... Save and close this file. Voila, done. "www.vatican.va" cannot be reached anymore from the computer in question. The same works great for spam or ad servers, just type in their hostname and give them a fake IP address (e.g. 0.0.0.0  ... why? Because it works without causing too much troubles or network errors. But you could in theory use any IP address you want).

... of course, this is only good for as long as nobody becomes "root" again and removes the line in question from /etc/hosts. ... So it helps if your kids etc. don't have access to "root" or "sudo".

---

### Post by The Cog on 2008-07-22
> **bapoumba said:**
> This thread has been reported, and will be watched.


I find that somewhat ironic, considering the subject. Was it intended to be so?

---

### Post by eentonig on 2008-07-22
Have some faith? :rolleyes:


I find it very funny that a church is asking for measures like this. I would think that, off all companies, a church would be the first to trust his employees (untill proven otherwise).



Actually, you know what's the best way off keeping people away from porn? (besides not being so damn moralistic about it) Hang out an (anonymous) listing of the top x porn surfers and the sites visited. I once was asked by my management to give them ten names of people who browsed the most for non-work related content. I refused, but told them I would post an anonymous list with the info in question. if the problem/numbers would remain the same for the next month, I would post the names. Two very funny consequences were noted.

1. network abused dropped significantly for the next year (not only by those ten)
2. Management never asked me for such thing again. (Not surprisingly, seeing that 7 out of ten 'top criminals' were indeed members of the management committee.:rolleyes:)

---

### Post by bapoumba on 2008-07-22
> **The Cog said:**
> I find that somewhat ironic, considering the subject. Was it intended to be so?
Yes ^^
The thread was reported, and I saw potential for, let's say, off topic. I wanted to state I was subscribed only for moderation purposes (not for support or personal interest).

---

### Post by horacetrever on 2011-12-09
> **gjohns28 said:**
> Okay, let me clarify further.

Yes it is legal in the US, the company owns the computers and they have the right in the US to monitor the activity on them.

What we use know is a Windows product, but I'm really surprised there isn't an out of the box solution that will work with Ubuntu. I have checked with Spectorsoft and they have ported for Linux yet, they only have Mac and Windows and no plans for Linux.

We are willing to pay for the software just as we've done now on Windows.

I appreciate all the suggestions, but we currently just have to check the status of approx 4 graphs  in Spector 360 to do if we have a problem with porn and how much time has been spent on those sites.  I don't have to dig thru any data to know we have a problem. If I see a problem, I can click once to drill down to get more detil on which user I have a potential problem with, and I can see any detail from there including porn websites visited, along with the active links, keyword searches they might have violated, and many more details.

We took these steps with the Spector 360 software on Windows, to be pro active if a problem should develope with porn, chatting with underage children, violence in the workplace, to try to catch a problem before we end up on the news and our reputation is gone.

I'm not interested in blocking websites, we don't block any websites, when you block folks just look for another way around this to get to site they want.  But we do monitor for problems. We don't have any to spy on employess thru-out the day, the software just gathers up facts and alerts if there is a problem we need to know about, otherwise it's business as usual.

We also have many users with laptops and Spector 360 runs on those laptops, folks take them home if they want to do work from home but when they return to the network the data is gathered and is updated in our database, again we know if there was a problem even while they were off our network.  They are company laptops and to be used for company email, and work when off our network so we can still monitor for problems.

Other further suggestions are welcome, otherwise if no one has any further input this discussion can be closed out Friday or Saturday.

Thanks so much!

Yes I support your article, it's reasonable. But now my spector stop working. I don't know it is because of out of maintenance contract. I already read through their admin guide, deploy guide. But still cannot fix. Can you point me the forum about spector 360 freelance technical support? Thanks.

---

### Post by cariboo on 2011-12-09
Have a look here:

[http://www.spector360.com/support/FAQ.htm](http://www.spector360.com/support/FAQ.htm)

for support, and with that, this 3 year old thread is closed.

---

