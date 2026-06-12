---
title: "Question regarding Samba workgroup and Samba Domain"
date: 2010-04-23
forum: Server Platforms
---

### Post by Carlo1973 on 2010-04-23
I've been toying with the idea of setting up a more advanced network environment in my home, mostly for practice. My wife's laptop runs Windows XP Pro, my desktop upstairs uses Vista Home Premium, and my linux box uses Ubuntu 9.10. All work fine individually through a wireless router. No big deal. 

I was thinking of setting up a domain controller (with Samba 4) on it's own pc. Probably going to be using Ubuntu Server 9.10 just to keep my linux stuff consistent.  

Now the problem I have is this. I know my wifes XP Pro laptop will join the domain no problem. My Linux box will have no issues as well. I also know that by default, my Vista Home Premium will not be able to join the domain (due to its limitations) However, Vista Home Premium can join a Workgroup. Is it possible, to have both a Samba based Domain and Samba based Workgroup running on the same server? 


 I know there wouldn't be any authentication for the Workgroup unit (or at the very most, very basic authentication) - and I realise that security wise - this is rather pointless as the whole reason for a Domain controller would be secure authentication at a central place, unless you can some how get the Samba work group to Authenticate against the Samba DC's database. It's been awhile since I worked with workgroups as the environment at work is all on a Domain. I can't remember if there is any authentication of any kind through a Workgroup, or if its just a local (internal) authentication and it just connects to others with the same workgroup name. 

I require my windows system for a few programs that I can not use in Wine or a virtual machine (due to direct X issues). However I do not plan on upgrading Vista, or going to Windows 7 Ultimate any time soon (Unless I get a significant pay increase at work - hint hint if my manager is reading this LOL). I want to be able to set a secure network accesible share, that my wife would be able to store her files on, I'd be able to do system backups to, and setup a print que to my network laser printers (and two usb inkjets). Other features will be added on as I can purchase new hardware to run additional servers on (I wouldn't mind setting up VPN and a Radius server eventually so that I can access it when I'm on the road, or setup an open exchange system for email for my family, possibly an Alfresco setup for online collaboration with co-workers, setting up paintball meets, and a place where my wife can store her notes and homework if she's studying at the school, through a secure environment that wont be touched by MS viruses - happens a lot and she's lost a lot of data caused by viruses connecting to her usb stick when she plugs into a school system).

If someone could give me some insight or point me in a direction on this, that would be awesome. 

Thanks a bunch

Carlo

---

### Post by capscrew on 2010-04-23
> **Carlo1973 said:**
> I've been toying with the idea of setting up a more advanced network environment in my home, mostly for practice. My wife's laptop runs Windows XP Pro, my desktop upstairs uses Vista Home Premium, and my linux box uses Ubuntu 9.10. All work fine individually through a wireless router. No big deal. 

I was thinking of setting up a domain controller (with Samba 4) on it's own pc. Probably going to be using Ubuntu Server 9.10 just to keep my linux stuff consistent.

Samba 4 is still not stable.  It is a rewrite of Samba 3 to add LDAP and Kerbros.  This would make it more like Windows Server AD.  See [**_here_**]("http://wiki.samba.org/index.php/Samba4").
>  
Now the problem I have is this. I know my wifes XP Pro laptop will join the domain no problem. My Linux box will have no issues as well. I also know that by default, my Vista Home Premium will not be able to join the domain (due to its limitations) However, Vista Home Premium can join a Workgroup. Is it possible, to have both a Samba based Domain and Samba based Workgroup running on the same server?

What are your expectations of a "*Domain*"?  

To my way of thinking the **[COLOR="Blue"]Network Domain[/COLOR]** is a centralized manner of managing users (not data) and providing authentication, authorization and the accounting of users.

A workgroup is a **[COLOR="Green"]Browsing Domain[/COLOR]**.   It groups hosts (computers) and their "*shares *" to enable you to view them easily.  Sort of grouped by data you might say.
> 
I know there wouldn't be any authentication for the Workgroup unit (or at the very most, very basic authentication) - and I realise that security wise - this is rather pointless as the whole reason for a Domain controller would be secure authentication at a central place, unless you can some how get the Samba work group to Authenticate against the Samba DC's database. 

It's been awhile since I worked with workgroups as the environment at work is all on a Domain. I can't remember if there is any authentication of any kind through a Workgroup, or if its just a local (internal) authentication and it just connects to others with the same workgroup name. 


Samba can authenticate users to the workgroups various shares.  This would just like sharing is done on the Vista host.  The Samba database is on the Linux host.

The rub... For a workgroup, you have to maintain consistency of user ID's or mapping of the variations yourself.  

On my setup at home I have 2 Samba3 installs and 3 Vista hosts.  All users have the same user/pass on all platforms and the uid/gid on the 2 Linux hosts are the same.  

In the end I maintain security of the shares on the Linux hosts via [COLOR="Purple"]Samba authentication [/COLOR]and [COLOR="Red"] Linux authorization [/COLOR]of the file/directory permissions  
> 

I require my windows system for a few programs that I can not use in Wine or a virtual machine (due to direct X issues). However I do not plan on upgrading Vista, or going to Windows 7 Ultimate any time soon (Unless I get a significant pay increase at work - hint hint if my manager is reading this LOL). I want to be able to set a secure network accesible share, that my wife would be able to store her files on, I'd be able to do system backups to, and setup a print que to my network laser printers (and two usb inkjets). Other features will be added on as I can purchase new hardware to run additional servers on (I wouldn't mind setting up VPN and a Radius server eventually so that I can access it when I'm on the road, or setup an open exchange system for email for my family, possibly an Alfresco setup for online collaboration with co-workers, setting up paintball meets, and a place where my wife can store her notes and homework if she's studying at the school, through a secure environment that wont be touched by MS viruses - happens a lot and she's lost a lot of data caused by viruses connecting to her usb stick when she plugs into a school system).

If someone could give me some insight or point me in a direction on this, that would be awesome. 

Thanks a bunch

Carlo

I suggest you read [**_Samba By Example_**]("http://samba.org/samba/docs/man/Samba-Guide/") for starters.  There is also the [**_Samba Howto_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/").

My own personal opinion of the unauthorized howtos is less than enthusiastic.  There have been lots of changes from version to version, so you can toss most of the old stuff for starters.  There is lots of misinformation and downright lack of knowledge in others.  I would stick with the documentation from Samba.org until I knew what is what.

Once again these or my opinions and YMMV.

---

### Post by Carlo1973 on 2010-04-23
Hey thanks for the info and I will check those sites out tommorow when I have more time. 

The main reason for wanting to setup a domain was indeed for centralized authentication of users. Granted its not hundreds of users. Maybe 10 at the most. The goal was to setup a domain controller, so that I could eventually tack on a Radius server (and take advantage of enhanced security for my wireless router), VPN, terminal services, and for Alfresco.  

I wasn't sure if I could build both domain controller and workgroup host as one unit, so that all my systems can logon to the network and authenticate in a similar manner, while maintaining tight security. However my gut feeling says no, but I wanted to get advice first. Just because my gut says no, doesn't mean it hasn't been done, or someone might have insight that I don't have that could indeed make it work, so I ask :)


I'm a person that learns by doing and trying different things out. However, I sometimes need to read and get guidance in order to move forward when my mind is stuck on something that I'm not sure of. Hence this project in the first place. It originally started with me setting up a log server to record events from my wireless router, and noted that there were several un-authorised attempts to gain access to my network. This lead me to want to setup a Radius server to act as authentication. Guides I found reconmended setting up Samba as a Domain Controller, while using LDAP as the authentication medium between the Controller and the Radius server so that it authenticates at login.  At work we have traditional VPN services for remote users, but we also are currently setting up terminal services, so I figured that might be an interesting project to tackle at one point so add that to the list lol. Setting up a NAS was always on my to-do list, but not high priority. Setting up an Alfresco server is something that came out of need from my wife attending school, using a shared computer, and coming home with a virus on her USB stick that took out her XP Pro system (had to wipe everything - the NAS would have come in handy here for regular backups). I figured setting up the Alfresco server would work as it is similar to Sharepoint, and she could just upload her documents there from the school. This way its on a linux box, that will probably have ClamAV scanning in the background on regular intervals. All the individual servers could just use the Domain controller as a central authentication point. Or at least thats what has been going through my head LOL

---

### Post by beetlejuice321 on 2010-07-23
Hey Carlo1973.  I was curious if you had any luck with running both a Workgroup and PDC+LDAP from one Samba server?

I am attempting to do the same thing as I want to setup a simple file server for users in a small office.  The problem is many users do not have Pro/Business versions of MS OS's.  Several users have "Home" versions of XP/Windows-7 etc.  

What I am looking to do is run both a Workgroup (authenticate through the Samaba/Unix accounts), and a PDC+LDAP for the Windows XP/7 Pro clients to connect.  In the future I once everyone has upgraded to Windows Pro OS, I will then be able to disable the Workgroup entirely.

Its surprising how little documentation there is on any of this stuff!

---

### Post by Carlo1973 on 2010-07-23
> **beetlejuice321 said:**
> Hey Carlo1973.  I was curious if you had any luck with running both a Workgroup and PDC+LDAP from one Samba server?

I am attempting to do the same thing as I want to setup a simple file server for users in a small office.  The problem is many users do not have Pro/Business versions of MS OS's.  Several users have "Home" versions of XP/Windows-7 etc.  

What I am looking to do is run both a Workgroup (authenticate through the Samaba/Unix accounts), and a PDC+LDAP for the Windows XP/7 Pro clients to connect.  In the future I once everyone has upgraded to Windows Pro OS, I will then be able to disable the Workgroup entirely.

Its surprising how little documentation there is on any of this stuff!


To be honest I've had so little time over the last few months to do any real projects of my own. The company I work for has been sending me all over Canada to work on servers (windows units). I've only recently started relooking into this again. Assembling an old pc to work as a samba test bed server (not the permanent home) and managed to install Ubuntu server 10.04 (base install). That was 3 weeks ago LOL Haven't done anything with it since then lol

I will hopefully get a chance to do some work on it this weekend (after I've cut the lawn, and did a few of the reno's on the house that I've not been able to complete... my wife is getting on my case lol). As I move through it I'll make brief documentation and post it on here as time allows :) 

In theory it should work. The shares will probably need to be controlled by security groups, and authentication will have to be made against LDAP. As a workgroup computer will not authenticate to the server at login, you will need to set up the share's manually (not through a script), and authenticate against the share with credentials to users already on the server (so have your users and security groups setup on LDAP first prior to anything else). When you connect to the share this way, you run the small risk of windows loosing the sync to the share, and may need to re-authenticate time to time (username + password) when trying to open the shared drive/folder. 

I've recently set up a server for one of the job sites I had to go to, in very much this same way. It was a group project between our company and another company. We didn't want this server to have any direct connection to our other servers. We also did not want to give people from the other company any login access to this server. The compromise was to do it this way. None of the computers at this job site got joined to the domain - these essentially remained as workgroup computers, even if they were originally joined to our primary domain at one of the branch offices. AD was installed for authentication. This allowed me to add users and to create some security groups to tighten security on folders.  To be quite honest, its an over the top NAS with printer share capabilities, running on an HP ProLiant G6 server, with Server 2008. Hey I don't plan this out, that's our IT directors doing - I'm still technically a Help-Desk Analyst lol

Every once in a while I will get a call where someone has lost connection to the shares. It appears to affect mostly those who are using laptops and who go from the job-site to the the branch office. When they leave the "joint-venture" site and go to the main branch, they join our primary domain. When they leave and go back to the joint-venture site, this is when the authentication issues happen. And logically, it makes sense. I highly suspect to see the same scenario with Samba. The computers joined to the domain wont have any issues. Its the ones that are not joined to the domain, moving back and forth between sites, that may have small issues.

---

