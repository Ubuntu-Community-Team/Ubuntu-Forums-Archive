---
title: "Possible to Have Active Directory as Ubuntu being the Server with no windows server?"
date: 2010-07-22
forum: Server Platforms
---

### Post by finito on 2010-07-22
I am trying to set up A closed Network for a POS system. I want to run all the Windows Clients hooked upto Active Directory or something similar without any Windows Server.

is this even possible? if so how?

Thanks for any help.

All I want is for the clients to be able to access the Ubuntu Machine and access the Database there while adding a small shared Drive, Active Directory is a nice Plus.

I am still learning my way around Linux so if the instructions are noob friendly that would be nice.

Thanks again.

---

### Post by lykwydchykyn on 2010-07-22
Active Directory - Not until SAMBA 4 is done. It's currently in a neck-and-neck race with GNU HURD for release (that's a joke, btw).
Windows NT Domain - Yes, using SAMBA (3) [https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html)

"Something like it" -- that would probably be openLDAP. [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

---

### Post by lykwydchykyn on 2010-07-22
> **finito said:**
> 
All I want is for the clients to be able to access the Ubuntu Machine and access the Database there while adding a small shared Drive, Active Directory is a nice Plus.



Can you be more specific about this?  It's possible you don't need any kind of directory for what you want.

---

### Post by finito on 2010-07-22
Hmm let me give you a usual Scenario as I am not sure I can put it in words efficiently.

Lets say The Ubuntu Machine is the Server. 

Server needs be able to do the following:
  * Host the MySQL Server (Ok, I know how to do this)
  * Share a Folder to act as a Network Drive. (Samaba can take care of this I Think.)
  * Active Directory to have all the machines connected to a common Server or something similar.

The Clients are running Windows, I want them to connect to the Server and be able to Access the Networked Drive and the SQL Server.

There are about 12 Clients in 4 Locations Runing a POS application over P2P WAN or Data over DSL WAN.
There is no Internet in the equation and that is fine.


The Current system Runs on a MS 2003 Server with a MS SQL Server.

I want to replace this with Ubuntu Server for seamless integration if possible.

If there is an alternative way to connect the machines without the need of Active directory I am open to it.

If you mean leaving it as is over a Workgroup Network instead of a Domain, I am sure that is possible but I don't know if it is feasible.

Thanks again for the reply.

---

### Post by lykwydchykyn on 2010-07-22
Is there already an active directory in place that you want the share and/or MySQL logins to authenticate to, or are you wanting to have a separate directory at each location so that the workstations can do the "roaming profile" thing?

---

### Post by finito on 2010-07-22
There has been data loss so I am starting from scratch. (Fire)

So there is nothing at the moment only speculation at this point.

---

### Post by finito on 2010-07-23
> **lykwydchykyn said:**
> "roaming profile" thing?

Does that refer to being able to login with a certain Username on any client?

---

### Post by lykwydchykyn on 2010-07-23
> **finito said:**
> Does that refer to being able to login with a certain Username on any client?

Yes.

---

### Post by houstonbofh on 2010-07-23
> **finito said:**
> * Active Directory to have all the machines connected to a common Server or something similar.
Need more data here...  I have an entire office connecting to a samba server, and there is no active directory.  They map the drives with "Connect as..." from Windows.

---

### Post by finito on 2010-07-23
> **houstonbofh said:**
> Need more data here...  I have an entire office connecting to a samba server, and there is no active directory.  They map the drives with "Connect as..." from Windows.

So the User has to login everytime?


As for the "roaming profile" I want to leave all the machines logged in, If possible auto logon as the employees have to login to the software and they complain enough about that, I don't know about adding another login procedure. So I don't really care too much for "roaming profile" It is a nice plus but not necessary.

I just want the Employee to start the machine, let the machine do what it needs to do and prompt the user for the Password from the App.


It is simple with Windows Server but the headache with viruses and spyware and no internet was just to annoying to take care of. So I am assuming With Linux I can just set it and leave it, where I check it once in a while. 


Is there such a solution? Or is Windows the only way to go for this?

I wish to introduce Linux for two reasons, I wish to expand my understanding of how it works and I understand that there are performance benefits. Yes I know for 12 clients it may be overkill, but why not right?

Please advise. Thanks.

---

### Post by lykwydchykyn on 2010-07-23
So basically, the only thing these workstations are just running the POS app and nothing else, that actual workstation login is not important.

If the POS app can run on Linux, then it sounds like you have an ideal situation for doing an LTSP setup -- diskless thin clients booting from a server.

I have a setup like this for web kiosks, and it works great.

If the app requires windows, then I still don't think you need active directory or roaming profiles.  You just need to tinker with login settings on the windows machines for auto login, and probably redirect your shell so that only the app starts up.  I've seen this done on Windows, but I don't know how to do it myself.

Does this sound right, or am I off track here?

---

### Post by finito on 2010-07-23
I need windows as I need certain product catalogs. I wrote the App in C# but I have played with mono, so I know I can port it to linux but that won't do anything for me as I need windows for the catalogs. I did think of running the catalogs in VM but the catalogs are more Resource hungry then the app itself.

> **lykwydchykyn said:**
> I've seen this done on Windows, but I don't know how to do it myself.

I can take care of this, it shouldn't be too difficult.


Yes you are quite on track, I just need to know what to use to do this.

I tried to setup a Samaba Server, was playing all day with [this]("https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html")

But I can't seem to get the domain working, I don't think that samaba has that ability, But then what is the Domain Master setting? 
```
domain master = Yes
```

Can you explain how to go about connecting it. I am doing everything in VM before I deploy.

---

### Post by lykwydchykyn on 2010-07-23
Caveat: I haven't set one of these up before, only read on it extensively at one point when it looked like there was going to be a need for it in a project I was part of.

Samba *can* do a domain, but it's an NT4-style domain, not Active directory.  WinXP clients should still be able to connect and authenticate against it, that's what the domain master setting is.  In NT4 domains, one box is the "primary domain controller" and others are "secondaries"; not like AD where all domain controllers are equal.

There are a zillion and one tutorials on how to set up a domain, I would trust one of them before trusting me to tell you how to do it.  Some good stuff is here: [http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

But if you want auto-login to the desktop, why bother with a domain?  I've always thought joining a domain disabled auto-login on WinXP -- at least it did last time I tried to implement them both.

---

### Post by bmathis on 2010-07-23
Have you checked out [ebox-platform]("http://www.ebox-platform.com/")? Its an app that pulls off active directory as well as many other features that can be used in a business network in place of MS or other proprietary software.

I have installed and manage ebox at a few non-profits that I do side work for... very few problems if you plan out your deployment properly.

Give it a look.

---

### Post by finito on 2010-07-24
bmathis ebox looks very cool, I will chekc it out.

lykwydchykyn I will try and read that, although at this point I am pointing more towards the ebox solution, I would still like to know how the samba solution works.

Thanks for all the replies, I shall provide an update once I have played around with the two to my hearts content.

---

### Post by v1ad on 2010-07-24
look into ldap

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

[https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows](https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows))

---

### Post by heli2reg on 2010-07-24
> **finito said:**
> 
Can you explain how to go about connecting it. I am doing everything in VM before I deploy.
 
[COLOR=black][FONT=Verdana]finito, I just read this thread incidentally and to be able to help you efficiently, I have a few questions for you:[/FONT][/COLOR]

[LIST]
[*][FONT=Verdana]Reading all your posts, I am gathering the conclusion that you do not really know if you need Active Directory or not, correct? Are you familiar with AD, what its benefits are and what to use it for?[/FONT]
[*][FONT=Verdana]Regarding the shared directory on a server (Linux): Would you like one shared directory that everybody can access and has equal rights to (read/write/delete/…)[/FONT]
[*][FONT=Verdana]You have several windows workstations, let’s say A through J. Then you have as an example 10 users. Does user “1” typically always logon to workstation “A” and user “2” to workstation ”B”? Or do you want to be able to have user “1” also logon to workstation “C”? How about if user “1” changes his password on workstation “A”, which is typically his/her workstation – in that case, should the password for user “1” be changed on all other workstations?[/FONT]
[*][FONT=Verdana]Your application needs access to a MySQL database, correct? Does it use files on the shared directory as part of the application’s normal operation as well, or not? Is the shared directory for all users simply to exchange files easily?[/FONT]
[/LIST][COLOR=black][FONT=Verdana]You should be able to clearly answer all these questions. If you are not, then I honestly do not know how to help you, but if you answer all this questions in a succinct way, I can definitely help you on Windows and Linux.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Waiting for your response.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]/Wolfgang[/FONT][/COLOR]

---

### Post by walkerk on 2010-07-24
Not ubuntu but worth a good look...

[http://www.redhat.com/directory_server/](http://www.redhat.com/directory_server/)
[http://directory.fedoraproject.org/](http://directory.fedoraproject.org/)

I'm watching both with a lot of interest...

---

### Post by finito on 2010-07-24
> **heli2reg said:**
> # Reading all your posts, I am gathering the conclusion that you do not really know if you need Active Directory or not, correct? Are you familiar with AD, what its benefits are and what to use it for?

What I said is AD is not required, I will not say I am Profficient with AD, but I know my way around it. I don't need AD if all the users can see the Server and interact with the MySQL Database. But if AD can be deployed that would be nice.


> **heli2reg said:**
> Regarding the shared directory on a server (Linux): Would you like one shared directory that everybody can access and has equal rights to (read/write/delete/&#8230;)

Well Read-Only access, Unless I give certain Users the Access.


> **heli2reg said:**
> You have several windows workstations, let&#8217;s say A through J. Then you have as an example 10 users. Does user &#8220;1&#8221; typically always logon to workstation &#8220;A&#8221; and user &#8220;2&#8221; to workstation &#8221;B&#8221;? 

Yes

> **heli2reg said:**
> Or do you want to be able to have user &#8220;1&#8221; also logon to workstation &#8220;C&#8221;? How about if user &#8220;1&#8221; changes his password on workstation &#8220;A&#8221;, which is typically his/her workstation &#8211; in that case, should the password for user &#8220;1&#8221; be changed on all other workstations?

Only the Admin Account.


> **heli2reg said:**
> # Your application needs access to a MySQL database, correct? Does it use files on the shared directory as part of the application&#8217;s normal operation as well, or not? Is the shared directory for all users simply to exchange files easily?

The Shared Directory is used to put the Updated App for the app to self update. And File sharing for certain Users. (By App I mean the POS Application).

[QUOTE=v1ad]look into ldap

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

[https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows](https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows))[/QUOTE]

Yes LDAP has come to my attention when I was reading guides about this, It seems the most logical way to proceed, Ebox solution seems to be based mainly on it

[QUOTE=walkerk]Not ubuntu but worth a good look...

[http://www.redhat.com/directory_server/](http://www.redhat.com/directory_server/)
[http://directory.fedoraproject.org/](http://directory.fedoraproject.org/)

I'm watching both with a lot of interest...[/QUOTE]

I had a look at these two, but I read a suggestion that if you wish to maintain a server it is better to stick to what you know. I admit the Linux is not my strong suite but RPM i have no clue about, The directory Service does hold promise thanks for bringing it to my attention.

I will keep my eyes out for that.


For the momemt Ebox looks promising but I am still tinkering away.

---

### Post by lykwydchykyn on 2010-07-24
ebox is just a front end for various services, including Samba.  It will probably help get things going, but undoubtedly at some point you'll need to understand Samba itself.  It's been my experience that the easy front ends only get you so far.

But ebox is good, I'm not panning it.

---

### Post by finito on 2010-07-24
[QUOTE= lykwydchykyn]ebox is just a front end for various services, including Samba. It will probably help get things going, but undoubtedly at some point you'll need to understand Samba itself. It's been my experience that the easy front ends only get you so far.

But ebox is good, I'm not panning it.[/QUOTE]

After playing all day with ebox, I am able to make a domain controler and and share some space, but unable to make a LAMP server. I am back to tinkering with Ubuntu Server.

I have been reading on Samba, I am very well aware that if I don't learn the key functions and just let it get automated and the server goes down tommorow it's going to be a double headache. so I agree I will have to learn it sooner or later. I have a basic concept at the moment. But thanks for the suggestion. I will keep you updated.

---

### Post by houstonbofh on 2010-07-24
> **finito said:**
> So the User has to login everytime?
Nope.  When you map the drive, it caches the user and password.

---

### Post by kewlrichie on 2010-07-25
It's not ubuntu but it is Linux! I would checkout "ClearOS"

[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)

They even have a live demo that you can log into [http://www.clearfoundation.com/Software/live-demo.html](http://www.clearfoundation.com/Software/live-demo.html)

---

### Post by finito on 2010-07-25
[QUOTE=houstonbofh]Nope. When you map the drive, it caches the user and password[/QUOTE]

I was talking about Network Logon.

Wow thanks Kewlrichie that looks awesome.

---

### Post by finito on 2010-07-25
I have been playing with LDAP and Ebox somemore, I seem to have a server running with my needs, I want to do the same without the need for Ebox, is there another web type interface that will let me have a minimul GUI to do things. Editing text files is ok, but it's just so annoying to not have copy paste functions. (I mean from a webpage).

The Ebox solution is working fine without any problems, but I am afriad if the thing goes down, I will not be able to bring it back up.

ClearOs is bugged I couldn't get very far in installing.

As of now I have a server running the way I want it. Thanks to all who helped me.

I have a active Directory logon, and I have all the Users and Groups set with the MySql server running.


I have 2 things left to do, I want to share a folder over the network and I want to Make it into a DHCP server. I will do those next I read quote a bit on Samba I feel confident I can do it. If I fail I will come back for support.

Eitherway I will be back to update.

Thanks again.

---

### Post by HermanAB on 2010-07-26
Howdy,

I think that for 12 users you guys are making things too complicated.  You don't need a directory server for 12 people.

The simplest way to use Samba is to set the server up with the exact same user names and passwords as the Windows client machines.  If you do that, then if the Windows user would change his password, Samba will also change the password and keep things in sync automatically.

So, simply create a user account for each user on the Samba server, create a shared space with a special group eg 'samba:samba' (or set the permissions wide open to 777 on this share).  Make every user a member of the shared group 'samba'.  Go to each Windows machine and map the drive to a drive letter.  Problem solved.

---

### Post by finito on 2010-07-26
@HermanAB, maybe so, but I wish to keep if flexible if I wish to increase the amount of users.

They are 12 Users but they are not in one Location, and so if I wish to make a new id from another location or make a change, I don't want to have to go back to the physical server to make these small changes.

But I apperciate your input, I understand that I can do what you are saying and keep it simple, but I loose the convinience of remote administration. Or is there a way to do that as well?

Thanks.

---

### Post by heli2reg on 2010-07-27
> **finito said:**
> What I said is AD is not required, I will not say I am Profficient with AD, but I know my way around it. I don't need AD if all the users can see the Server and interact with the MySQL Database. But if AD can be deployed that would be nice.

 
OK, so if you have no need for users to logon on different workstations and instead they always logon to their own, I do not understand the benefit of AD at all. It would be nice? - Sorry, it would be nice to have $5k in the pocket, and all you had to do is post a message "server setup for $5k contract". Ummm - "would be nice", I safely assume you have no need for a Server Domain and no need for "roaming" profiles, as somebody else figured earlier. 
 
So ... simply get Samba running on your Ubuntu machine and you should be able to use a simple "[COLOR=blue]net use S: [/COLOR][[COLOR=blue]\\UbuntuServer\Share[/COLOR]]("file://\\UbuntuServer\Share")[COLOR=blue] /User:UbunutuServer\SambaUser password[/COLOR]" directive in either HKLM\Software\Microsoft\Windows\CurrentVersion\Run to make sure the drive gets mapped everytime the WinXP machine boots up. Actually, put that directive into a "mapshare.cmd" file and call that CMD as part of the Windows start. If you wanted to hide it a but, use a Policy instead. Whatever you prefer.
 
> **finito said:**
> 
Well Read-Only access, Unless I give certain Users the Access.

I recommend you chase down your Samba config file and simply setup a read-only share then.
 
> **finito said:**
> 
Yes
 
OK, so with isolated Workstations, don't worry about Domain, Active Directory, etc. - it's only overhead that you don't need - at least I don't see if from what I read here in your posts.
 
> **finito said:**
> 
Only the Admin Account.

OK, so with the admin being the same on all machines, the downside without AD will be to have to setup the profile on every machine. With all the days you spent trying to setup your AD, I guess you would be done with the simple setup of the admin profiles already by now.
 
 
> **finito said:**
> 
The Shared Directory is used to put the Updated App for the app to self update. And File sharing for certain Users. (By App I mean the POS Application).

Oh boy, from what I understand - you could really just setup a simple [[COLOR=blue]DropBox[/COLOR]]("http://ubuntuforums.org/www.dropbox.com/referrals/NTYyNjIwMjI5")[COLOR=blue] account with 2GB free space[/COLOR]. I bet your application won't need that much space. DropBox can go on your Windows, on Linux, on almost any machine. Just specify a local folder that will be synchronized online and all of your files will be populated to the other DropBox installations with the same account. If you have two different email addresses, set one up for yourself to make all files read/write, and a second email address that you share your files with from the first account with read only. Done. No Samba, no Windows file sharing, etc.
 
> **finito said:**
> 
Yes LDAP has come to my attention when I was reading guides about this, It seems the most logical way to proceed, Ebox solution seems to be based mainly on it

Seems to be overcomplicating things for you as far as I can tell.
 
So, to cover your MySQL installation on Linux, just make sure you got Apache2, MySQL, and PHP5 installed. Do you have a desktop - aka gnome or kde - installed on your Ubuntu server machine? If so, simply use the [COLOR=blue]Synaptic Package Manager[/COLOR] and make sure you get these packages installed. The MySQL config should be fairly straight forward. In order to import, backup, etc some database at the beginning, simply use "[COLOR=blue]phpmyadmin[/COLOR]". With that package installed, all you do is open a web browser, type in [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and you are rolling. Enter root for the DB admin account, using the password you provided during the install. 
Your Windows XP machines - actually it is the POS software - should be able to connect to the MySQL server as long as you have the connect string configured correctly. 
 
If you need any detailed assistance, please let us know where you are at, what you have accomplished already, and what you need. 
Also, if you do not have a desktop UI installed for your Ubuntu machine: Try using "[COLOR=blue]aptitude[/COLOR]". It may be easier for you than "apt-get" etc.
 
Before I forget: If you need to remotely admin your machines, check out TeamViewer. Goes on Win, Max, Linux. Amazing.
 
Good luck!

---

### Post by finito on 2010-07-27
heli2reg: I am not using any GUI just server based.

LAMP is least of my worries that is set. 

My only problem is When you say simply get samab running.

I have read through alot of the examples, and I can't find anything that addresses my simple needs. So I came to a conclusion that there isn't one.

I forgot to mention I need a DHCP server, but even that is not very difficult.

The only thing I am stuck on is Samba config.

Do I leave it stock? and then just set the Workgroup of all the clients to the same?

---

### Post by heli2reg on 2010-07-27
> **finito said:**
> heli2reg: I am not using any GUI just server based.
 
LAMP is least of my worries that is set. 
 
My only problem is When you say simply get samab running.
 
I have read through alot of the examples, and I can't find anything that addresses my simple needs. So I came to a conclusion that there isn't one.
 
I forgot to mention I need a DHCP server, but even that is not very difficult.
 
The only thing I am stuck on is Samba config.
 
Do I leave it stock? and then just set the Workgroup of all the clients to the same?
 
OK, so somewhere around /etc/samba you should have a file called smb.conf. Before I touch anything, I run a "cp smb.conf smb.conf.orig". Then I use "vi" to edit the file.
Yes, I changed my "workgroup = <WinWrkGrp>" setting to my windows workgroup and made sure my clients are all part of this same workgroup. Everything else, like wins, dns, etc. I had commented out. Likewise with the sections Domains, and Printing. Towards the end of the file you will find Share Definitions. I started a complete new section, similar to:
 
[FONT=Lucida Console][SIZE=2][COLOR=seagreen][mysharename][/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]comment = some free text comment right here[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]path = /home/winusers/sharing[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]force user = winusers[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]forcegroup = winusers[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]read only = no[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]guest ok = no[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]create mask = 0775[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]directory mask = 0775[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]browseable = yes[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]valid users = winusers[/COLOR][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][COLOR=seagreen]writeable = yes[/COLOR][/SIZE][/FONT]
 
Needless to mention, I have created that user account with user home path on the Ubuntu machine.
Note! This may be important: I believe to remember to have read that Samba is notorious for being picky with spaces etc. Make sure you have a space before and after the "=" sign. 
No guarantees - as always - sorry. If you got more problems, please be specific and post logs, config files, whatever you can provide. Otherwise, this is a wide open guessing game here - we are already far off topic anyhow (AD).

---

### Post by lykwydchykyn on 2010-07-27
If you just want to set up file shares, Webmin is a great tool for configuring samba through a browser interface.  It's a great tool for configuring most services.

(Though setting them up via the config file isn't that hard, as you can see above.  It's just an ".ini-style" configuration file.)

It doesn't have any tools for setting up a directory service on Samba, which is why I didn't recommend it before.

Honestly, there's really no quick'n'easy way to set up a directory service on Linux (or if there is, I haven't seen it).  Samba's about the most straightforward IMO, especially when you're talking windows clients -- and you've seen what it takes to get that running.

Maybe someone else can prove me wrong about that; I'd welcome that.

---

### Post by HermanAB on 2010-07-27
> I loose the convinience of remote administration

Remote admin is a different problem and Linux is very good at it.  That is why Google, Yahoo and Amazon can run gazillions of servers in big, dank warehouses with no-one around.

So, use SSH for remote admin.

---

### Post by heli2reg on 2010-07-28
> **lykwydchykyn said:**
> If you just want to set up file shares, Webmin is a great tool for configuring samba through a browser interface. It's a great tool for configuring most services.
 
(Though setting them up via the config file isn't that hard, as you can see above. It's just an ".ini-style" configuration file.)

 
lykwydchykyn, I would mostly agree with you except that I would debate if it takes longer to get Webmin up and running and most importantly, learn to understand the interface, than simply reading - IMHO good - comments in the smb.conf file and getting it configured properly.
Something I may have forgotten to mention - in case that is unknown - is that you will need to restart the samba service after modifying the conf file.
 
If the full feature set - or benefits rather - of Active Directory are not leveraged than a common (read-only) share on Linux with samba is definitely the way to go.
 
Also, lykwydchykyn, I think that Webmin requires a GUI, unless accessed remotely from another machine. I understand Webmin comes with its own small light-weight web server and hence makes it possible to even stop and start the Apache2 web service. Otherwise, that wouldn't work.
 
A side note on Webmin: I have installed it about a week ago for the first time and am struggling to put all the pieces together - the UI mainly, trying to understand of how everything is connected and tied to the services/conf files, etc.
 
Unfortunately - and please prove me wrong - I have found most documentation to be quite outdated when using the latest version of Webmin. It doesn't make it exactly easy starting to work with it. I understand a subscription and fee based service organization has made it its business to provide exactly that - services, consulting, while providing the (open source) software free. I hope Webmin will find more and great contributors soon, but that's a different top apart from what's being discussed here.
 
So yes, I would tend to agree with lykwydchykyn, modify the smb.conf file, since it is - bottom line - nothing more than an ini file. Again, if you have specific problems, please be as detailed as possibly can be reporting these.
 
 
> **lykwydchykyn said:**
> 
It doesn't have any tools for setting up a directory service on Samba, which is why I didn't recommend it before.
 
Honestly, there's really no quick'n'easy way to set up a directory service on Linux (or if there is, I haven't seen it). Samba's about the most straightforward IMO, especially when you're talking windows clients -- and you've seen what it takes to get that running.
 
Maybe someone else can prove me wrong about that; I'd welcome that.
 
True. Me too. At least not open source - unless you consider eBox an open source solution not minding the consulting fees.
 
However, back to the basics: With samba it should be really simple to setup light-weight read-only directory sharing. Otherwise, use a Windows box and put MySQL on top of it and offer Windows based file sharing. Not sure why Linux is required in this instance if everything else is Windows anyhow.

---

### Post by lykwydchykyn on 2010-07-29
> **heli2reg said:**
> lykwydchykyn, I would mostly agree with you except that I would debate if it takes longer to get Webmin up and running and most importantly, learn to understand the interface, than simply reading - IMHO good - comments in the smb.conf file and getting it configured properly.

Well, it's not always about efficiency, but about using an interface that best commends itself to your thinking.  That's why it's nice to have options.

There are a lot of little non-obvious chores that webmin simplifies; it's a useful tool.
>  
Also, lykwydchykyn, I think that Webmin requires a GUI, unless accessed remotely from another machine. I understand Webmin comes with its own small light-weight web server and hence makes it possible to even stop and start the Apache2 web service. Otherwise, that wouldn't work.

Well, yeah, that's kind of the point -- you access it through a browser from a workstation, not from a GUI on the server. 
>  
A side note on Webmin: I have installed it about a week ago for the first time and am struggling to put all the pieces together - the UI mainly, trying to understand of how everything is connected and tied to the services/conf files, etc.

It's not the best interface for everyone, but it works well for a lot of people.  I don't think there's a lot of mystery to it; it's a bunch of perl scripts that scan your config files, populate a web form with the data, and let you change it.  I don't think there's any sort of intermediate abstraction layer as with, say, YAST.  

That's part of why I like it, because it doesn't mess with my files or require me to ALWAYS use webmin "or else".  I can edit the files directly when I need to, and it respects that.
 
> 
Unfortunately - and please prove me wrong - I have found most documentation to be quite outdated when using the latest version of Webmin. It doesn't make it exactly easy starting to work with it. I understand a subscription and fee based service organization has made it its business to provide exactly that - services, consulting, while providing the (open source) software free. I hope Webmin will find more and great contributors soon, but that's a different top apart from what's being discussed here.

It's in rapid development, so it doesn't take long for a book to get stale.  The thing is, there isn't much that you really need a book for, IMHO.  Webmin pretty much lays out the configuration options for a service without much fanfare; if you need to know what something means, it's probably best to look at the service documentation.  It's more of a convenience than any major abstraction of the config process.  I think that's where it differs from something like eBox.

---

### Post by finito on 2010-08-06
I have a server running, After playing around with tutorials and guides, The thing that made most sense to me were the guides, after reading and playing around alot I have a server running, I am happy with it. It does more than I thought it would. 

I have a LAMP Server, Webmin for remote access, A shared Directory that has read only access (I can't seam to get write access from remote access but doesn't matter), and a DHCP server.

Thanks for all the help.

Peace

---

