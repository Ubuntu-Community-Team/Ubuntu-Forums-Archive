---
title: "Ubuntu as a Windows 2003 Server?"
date: 2006-11-29
forum: Server Platforms
---

### Post by altaaa on 2006-11-29
I am a system engineer for Windows networks. I have a healthy interrest in Linux, so I use Ubuntu on my laptop (besides Windows), and I have found that for most tasks, Ubuntu functions just fine. In fact, I love Ubuntu! :)

Now I was wondering what it takes to deploy a Linux based network. Linux on the clients, Linux on the server(s).

Some of the tasks I would like to find out about:
- centralized user management (LDAP?)
- login scripts for users/groups
- redirecting users' /home dir to linux file server
- mapping directories on the fileserver to the client (through login script)
- group policies
- printer management
- deploying applications

You know, stuff like that. Basically all features Windows Server 2003 has, but do it with Ubuntu.

Does anyone know some good sites/howto's for me to read?

---

### Post by elst on 2006-11-29
User administration is done with LDAP directories with Kerberos for single sign-on. Sabayon is currently the closest thing to Group Policies for users. For host management, check out cfengine and Puppet.

These areas are less polished than on Windows, although Fedora Directory Server and the Ubuntu Directory Services initiative will hopefully help to resolve this.

Centralized home directories and network "drives" are done on UNIX with NFS mounts.

I don't know much about printer management - the CUPS service provides local and network print spooling. Perhaps start with the CUPS help in the Web interface: [http://localhost:631](http://localhost:631) (the default configuration blocks connections from other systems).

Package management on Linux is usually done by a "pull" model - the administrators provide an apt repository and client systems grab what they need. This may sound odd to corporate admins, but larger UNIX desktop deployments are often in academia, where administration is less centralized.

---

### Post by PilotJLR on 2006-12-02
Yeah, to push software out to clients, I'm not aware of an out of the box solution, but you can easily script this.
For example, make each client run an hourly cron to install updates listed on a text file in a location you control (such as an internal web server). Stuff like that works pretty well... and that is basically what RHN does for red hat systems too.

---

### Post by technodigifreak on 2006-12-04
> **elst said:**
> Package management on Linux is usually done by a "pull" model - the administrators provide an apt repository and client systems grab what they need. This may sound odd to corporate admins, but larger UNIX desktop deployments are often in academia, where administration is less centralized.

One of the other options is to create different local repositories for different classes of devices.  Such as, a repository strictly for your webservers or print servers, or if you have different types of desktop users like programmers who need the latest and greatest updates, but still have regular users who need an update once a month or every other month - just point them at different repositories and be done with it.

---

### Post by elst on 2006-12-04
> **technodigifreak said:**
> One of the other options is to create different local repositories for different classes of devices.  Such as, a repository strictly for your webservers or print servers, or if you have different types of desktop users like programmers who need the latest and greatest updates, but still have regular users who need an update once a month or every other month - just point them at different repositories and be done with it.

That's really a slightly different issue. On a centrally managed network it's normal for administrators to "push" a new application or update to a particular set of systems at a specified time, so that systems are always in a known state. This requires both network repositories and an "agent" on the clients that carries out queued tasks in response to commands and reports back. Puppet and cfengine provide agent-like software.

---

### Post by technodigifreak on 2006-12-04
> **elst said:**
> That's really a slightly different issue. On a centrally managed network it's normal for administrators to "push" a new application or update to a particular set of systems at a specified time, so that systems are always in a known state. This requires both network repositories and an "agent" on the clients that carries out queued tasks in response to commands and reports back. Puppet and cfengine provide agent-like software.

True, I don't have any experience with any software level agents for Linux, so I didn't try mention any.  I just know that the different repositories trick has worked quite well in the past for several folks.  It tends to work best when you have several distinct classes of machines and each needs a different level of updating.  Often the updating is handled with a simple script and a cron job.  The downside is that you generally don't get the report back.  However, if you simply want every machine to have the same version then a "Push" method with a locally installed agent would work best . I'll look into both Puppet and cfengine and see if I can put them to good use.  Thanks!

---

### Post by altaaa on 2006-12-07
Thanks for all the replies, now I have some stuff to look in to :)

---

### Post by Kalif on 2006-12-07
altaa!
I got a little bit confused by this thread and by the answers;
What do you want to do replace your 2k3 server _OR_ replace the
server and all your clients?
In the later case you are in for a big game migration :-)

If you are satisfied with replacing the server things may be quite easy, depending what you use the server for. Even if
there has been some debate on 2k3 not beeing 100% a good
product from a technical point of view, it is very much a
feature crammed product. Hence if you are using some particular
features of 2k3 the migration may be complex.
If you depend on ms sql or exhcange for instance.

For pushing updates to clients Novell has a nice tool, zen works.
When I last saw it a few years ago, it was actually linux based. Each client had a small linux partition that it booted to first, and from the linux system it communicated to the server and grabbed whatever needed for upgrading that particular system and then it booted into the upgraded windows system. Neat.

Cheers,
K.

---

### Post by oly on 2006-12-08
you can also use wpkg, for updating windows clients and installing software.

I have been using this in a school and it works very well, it installs services packs and fixes, and can install different software to different computers based on hostname, you can even send to a group of computers using regex expressions.

---

### Post by altaaa on 2006-12-12
I am not planning any upgrade/migration. I'm just curious :)

Let me be more specific: I was wondering if it is possible to get the same level of functionality with linux server/linux client as can be done with windows server/windows client.

The Small Business concept is great, you get a whole lot of functionality in one software package, imho linux should also have someting like that. From what I gather from the replies, a lot is possible but I don't think this is beginner-stuff, while SBS2003 is kinda newbie friendly.

---

### Post by technodigifreak on 2006-12-12
> **altaaa said:**
> I am not planning any upgrade/migration. I'm just curious :)

Let me be more specific: I was wondering if it is possible to get the same level of functionality with linux server/linux client as can be done with windows server/windows client.

The Small Business concept is great, you get a whole lot of functionality in one software package, imho linux should also have someting like that. From what I gather from the replies, a lot is possible but I don't think this is beginner-stuff, while SBS2003 is kinda newbie friendly.

Altaaa,

This guide should be right up your alley.  [http://howtoforge.net/ubuntu6.06_firewall_gateway](http://howtoforge.net/ubuntu6.06_firewall_gateway)

It basically shows you how to do a fully functioning SMB2003 equivalent install.  Let us know if you think of anything else!

---

### Post by MystaMax on 2006-12-12
The author and others may find this interesting. I had this bookmarked a while ago.

[http://ebox-platform.com/](http://ebox-platform.com/)

[quote=ebox website] eBox management tool will effectively and easily help you managing the advanced services for your corporate network. Designed with extensibility in mind it offers, among others, these modules: [LIST]
[*]Firewall
[*]Transparent proxy
[*]Content filter
[*]NTP Server
[*]Users and groups administration
[*]Mail server[/LIST]and other modules...
[/quote]

Looks very nice, and is a great start to managing a linux based network. Its also debian based. They also have a [liveCD]("http://ebox-platform.com/ebox-live.iso").

---

### Post by Linuturk on 2006-12-12
Don't forget the wonderful documentation at help.ubuntu.com 

There is a server guide on there that walks you through lots of configs.

---

### Post by bahn on 2006-12-19
> **altaaa said:**
> I am not planning any upgrade/migration. I'm just curious :)

Let me be more specific: I was wondering if it is possible to get the same level of functionality with linux server/linux client as can be done with windows server/windows client.

The Small Business concept is great, you get a whole lot of functionality in one software package, imho linux should also have someting like that. From what I gather from the replies, a lot is possible but I don't think this is beginner-stuff, while SBS2003 is kinda newbie friendly.

I am in the same boat as you in this one. I have been spoiled for years using exchange and windows server from 2000 to 2003. I have always had an interest in the linux community and have often wondered if there were other options to what I have been using.

I would really like to see alturnatives to exchange, shadow copies, active directory, login scripts, and group policies.

---

### Post by elst on 2006-12-19
> **bahn said:**
> I am in the same boat as you in this one. I have been spoiled for years using exchange and windows server from 2000 to 2003. I have always had an interest in the linux community and have often wondered if there were other options to what I have been using.

I would really like to see alturnatives to exchange, shadow copies, active directory, login scripts, and group policies.

Unfortunately UNIX development more or less stalled, and only started recovering over the past couple of years with Linux, so what we have now is basically half of an integrated system, which lacks many of the features of Novell systems (that MS are copying).

Traditional UNIX networks looked very different to the Windows/Netware business LANs. AIUI, there was (and still is!) heavy use of thin clients on *NIX, and that approach largely avoids most of the client configuration issues that we see with workstations on Windows networks. Several parts of *NIX are specifically designed for client-server. Account/identity management on *NIX is a bit rough, perhaps because academic networks and users aren't as tightly managed as corporate environments, and Web hosts etc. don't need these features, so it's less of a pressing issue for the bulk of admins still running large UNIX networks.

Things are now starting to happen to make Linux a better LAN system, but it's still an evolving situation.

---

### Post by technodigifreak on 2006-12-19
> **elst said:**
> Unfortunately UNIX development more or less stalled, and only started recovering over the past couple of years with Linux, so what we have now is basically half of an integrated system, which lacks many of the features of Novell systems (that MS are copying).

Traditional UNIX networks looked very different to the Windows/Netware business LANs. AIUI, there was (and still is!) heavy use of thin clients on *NIX, and that approach largely avoids most of the client configuration issues that we see with workstations on Windows networks. Several parts of *NIX are specifically designed for client-server. Account/identity management on *NIX is a bit rough, perhaps because academic networks and users aren't as tightly managed as corporate environments, and Web hosts etc. don't need these features, so it's less of a pressing issue for the bulk of admins still running large UNIX networks.

Things are now starting to happen to make Linux a better LAN system, but it's still an evolving situation.

Elst,

You've hit the nail on the head.  'Nix is a WAN and Mainframe/terminal born system.  It's only in the last few years that there's been a need otherwise (due entirely to the rise of the PC).  It's a little funny that after having all of the high-end market, it's got to come up through the bottom of the market (individual desktops) to meet the middle of the market (Small-Medium Businesses).

---

### Post by elst on 2006-12-19
> **technodigifreak said:**
> Elst,

You've hit the nail on the head.  'Nix is a WAN and Mainframe/terminal born system.  It's only in the last few years that there's been a need otherwise (due entirely to the rise of the PC).  It's a little funny that after having all of the high-end market, it's got to come up through the bottom of the market (individual desktops) to meet the middle of the market (Small-Medium Businesses).

I've long argued that SMEs and particularly schools can be the most demanding environments for software products. These organizations have the same basic issues, but fewer resources, and much less ability to work around problems, so stuff has to work out of the box. Larger organizations can ensure that their staff are trained, and have in-house programmers (or can hire them), so can tolerate awkward software better.

My own feeling is that Linux is most important as a pool of common components for building systems to do particular jobs. A general-purpose distribution requires the administrator to pick and configure the right components for the roles that a particular system will perform, but there are lots of specialized distributions where the job is done for you. I'm sure that as the underlying software matures we will see a bunch of specialized distributions and appliances offering various forms of turn-key LAN server systems for SMEs. In the context of Ubuntu, Edubuntu may become a good example of how to make a tailored LAN server without losing too much of the flexibility of Linux.

---

