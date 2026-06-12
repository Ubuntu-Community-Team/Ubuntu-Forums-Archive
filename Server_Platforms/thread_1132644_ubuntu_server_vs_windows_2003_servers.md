---
title: "ubuntu server vs windows 2003 servers"
date: 2009-04-22
forum: Server Platforms
---

### Post by salim.madni on 2009-04-22
hello sir

we are new to ubuntu but we have littl experience with linux redhat slackware etc

but we start liking the ubuntu due to great people, greate mission, great support. in last everything cost nothing except support each others.

we are planning to convert one by one our all production live servers from windows 2003 to ubuntu server

where we have some difficulties we dont know how to resolve it

we use windows 2003 active directory(ad0 and domain controller enviornment. we also use local dns. then all windows xp and windows 2000 and vista machines join report to domain controller.

so let us talk about how can we convert and enjoy the functions features managed under unbutnu...can we do any possibility?

on the other hand, we are intrested to know if we convert from windows 2003 servers to ubuntu server. we want to use print server(hp laser printers by ip),webserver(iis currently),email server(axigen),flat files/filesharing/folder sharing.

thanks for supporting by great people
kind regards
salim

---

### Post by Spikerok on 2009-04-22
no difference.. only difference is in shell. Any OS can be secured it. depends on admin

---

### Post by koenn on 2009-04-22
> **salim.madni said:**
> 
so let us talk about how can we convert and enjoy the functions features managed under unbutnu...can we do any possibility?



Linux and Windows are entirely different worlds. Although linux can do things like dns, dhcp, file sharing, web server, .... as well or better than Windows, changing a Windows environment into a Linux environment is not easy. Not easy at all. 

read these to get an idea of what you're dealing with
[http://users.telenet.be/mydotcom/howto/linux/migration02.htm](http://users.telenet.be/mydotcom/howto/linux/migration02.htm)
[http://users.telenet.be/mydotcom/howto/linux/migration03.htm](http://users.telenet.be/mydotcom/howto/linux/migration03.htm)

Next, you're probably going to need to hire some linux consultants or so to do this for you. It's not a trivial task and I think it's impossible to do it by copying instructions from a forum like this one.

---

### Post by Yashiro on 2009-04-22
> we use windows 2003 active directory
If you rely alot on AD and GPO you have got no chance converting to Linux quickly.
It would take a long time and alot of work.

Additionally, if your admin staff are used to pushing buttons and fixing trivial issues by clicking yes on a dialog box this will only further compound your problems.

If the aim is to reduce costs and increase reliability you need to use Linux for something that does not require tight integration with the Windows API.

---

### Post by PilotJLR on 2009-04-22
Very true... if you are really using AD's capabilities, then you're going to have some problems.

The real question here is WHY do you want to convert these servers? Are they not working properly now? There must be some motivating factor.

---

### Post by juancarlospaco on 2009-04-22
Ubuntu can replace AD's funcionality, 
but you need Skills, maybe if you Pay commercial support from Canonical...
24x7x365

---

### Post by PilotJLR on 2009-04-23
> **juancarlospaco said:**
> Ubuntu can replace AD's funcionality, 


Could you elaborate on this? We're not talking about just LDAP here.

---

### Post by salim.madni on 2009-04-25
dear gurus

thanks for your all suggestion comment and precious advises

but, linux is the best and over this we are on ubuntu grounds to talk each others.

we are looking and planning windows-free enviornment slowly

now the question where to start from? client or servers?

as server that run in operations 24 x 7 x 365 right?

i know a very huge job...

i do have citirix,filesharing,printsharing,webserver,oracle, almost 99% servers are windows based

the 2 major reasons financial crisis of company/issues/bugs always no response or no solution with microsoft.everything is start talking in money terms. even ms office is not free, windows client,anything in MS world is simply not free. and nobody can gurantee if you appply patch it works fine or restart get failed/crash the server. it happend to us in our past.

now ad is managing 2 things, 
userid/accounts/password/groups etc that assign permission to login windows xp/clients/2000 etc to windows 2003 server...

we are highly appreciating and studing.

a first basic question raising, what is the alternate or replacement of AD in linux world or ubunutu.

kind regards
salim

---

### Post by salim.madni on 2009-04-25
yes definately
we will take all smallest server first

since AD will coem in last in picture or scopes

plus further, say convert citrix using windows use ubuntu

using oracle stop windows convert to ubuntu

all will go step by step

---

### Post by koenn on 2009-04-25
> **salim.madni said:**
> now the question where to start from? client or servers? 
That's not a question anybody on this forum can answer. For one, it depends on the scope (how mant servers, clients, ... are we talking about?), and the sort of computing you doing right now (what applications are you using and why, both on servers and clients ?). It also depends on the sort of environment you want to create, the  feasibility of getting there, and the road you'll take to get there.

> **salim.madni said:**
> dear gurus
i do have citirix,filesharing,printsharing,webserver,oracle, almost 99% servers are windows based

you'll have to explain a lot more about this. Any Linux server can run filesharing,printsharing,webserver,oracle. But nobody runs Oracle just for the fun of it : what applications does it drive ?
Does your web server run static html pages ? asp/aspx or other applications ? Do your printers come with Linux support ?  
Citrix is just sophisticated server-based computing. A Linux server can run terminal sessions for multiple users without problem, but that doesn't tell us what applications the server is supposed to run, and which client- or server-side feautures of citrix you're using and can't do without....


> **salim.madni said:**
> 
now ad is managing 2 things, 
userid/accounts/password/groups etc that assign permission to login windows xp/clients/2000 etc to windows 2003 server...

that only tells us your users log on to a MS AD domain, nothing more. 

> **salim.madni said:**
> 
a first basic question raising, what is the alternate or replacement of AD in linux world or ubunutu.

Linux is not a free copy of Windows. AD does a lot of things, and does each of them in a very specific way. You can only find alternative solutions if you have a very precise idea of what it is you need to replace, and then it remains to be seen if it can be done.


Again, I don't think this is the sort of project you can manage through a volunteer support forum unless you already have a lot of Linux experience, or we're talking about something small like 1 fileserver for 12 clients and nothing more. 
I suggest you talk to Canonical or a local Linux consultant.

---

### Post by fabsbsd on 2009-04-25
Hi!

You need a complete lifecycle consulting services here, like having Workshops and planning, after identifying your main pain points, operational analysis, and ROI, then comes the design, with a good design you'll be able to migrate succesfully, then comes the implementation and "baby sitting".

I suggest migrating some server apps first, like migrating IIS to Apache or databases from MS SQL to PostgreSQL or MySQL.

It may be almost impossible to get rid of your AD, or you'll  need to be willing to let go your GPO and AD "advanced" services...

Good luck!

---

### Post by PilotJLR on 2009-04-25
I'd agree with this as well. Assuming you are going to keep Windows endpoints around, which you will have to do unless you are ready to do significant user re-training, then you also need AD. You really don't need to be 100% Linux or 100% Windows. Lots of people use both.

You could, for example, keep Windows Server for AD and Citrix, and keep users' XP desktops. Then filesharing, printing, Oracle (probably), and websphere can move to Linux hosts.

Especially with Citrix... there is nothing even remotely close to Citrix XenApp in the Linux world.

---

### Post by jigglywiggly on 2009-04-25
I personally wouldn't switch to linux if you have Active Directory, just stay with Windows for Windows Active Directory.

---

### Post by salim.madni on 2009-04-26
Dear Respected Gurus,

i would highly appreciated your positive response and guideline.

i would say i am still beginner after working of 6+ years in linux world. i always interact with redhat,suse,centos,slackware.

but since all linux on same way works. ubuntu among them is best so i join it as beginner of ubuntu and linux also.

the consultancy is very week this country and area, however we have done many tasks on productions live. i felt confident only small support make great achivement. in past i build oracle 10gr1 on redhat, qmail/squireemail/clamav on slackware, now these days using axigen 7 mail server with redhat,ubuntu etc

this thread will close here now.

each server related matter a seperate discussion need to start sometime later

i highly appreciated all of your support.

FOLLOW THE MASTERS, BECOME THE MASTER

kind regards
salim

---

