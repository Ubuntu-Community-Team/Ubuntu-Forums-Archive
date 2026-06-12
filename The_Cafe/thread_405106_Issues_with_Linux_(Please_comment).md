---
title: "Issues with Linux (Please comment)"
date: 2007-04-09
forum: The Cafe
---

### Post by tymiles on 2007-04-09
Man there are 2 things about Linux that kill me right now.

1. Lack of easy to use directory services similar to AD in Windows, attached to file and print sharing. If you could set up a group of Linux servers and workstations (Linux, Windows or Unix workstatons) quickly and pretty easy like you can do with Windows or like an OS even closer to Linux, Mac OS (Mac Server and Mac OS are easy to roll out also) I could more easy sell Linux to my small business customers.

The thing that is insteresting with Mac Server is that they are using all open source software with closed source interfaces. But they make the Open Source tools do the same things that you can do with Windows XP/Vista and Windows 2003 Server and AD. 

Linux developers should look at the Tiger server and see how they use Open Ldap and Samba to replicate directory services across servers and setup login scripting to map drives. Same crap that you can do with Windows. This might be below some Linux people as a copy of MS but trust me if someone did this and made it cheep on Linux (Xandros is close but still a little pricy $450 per server and it needs work) You could sell this to Windows shops all day long! 

Imagine if I could go to a small business and put in 2 Ubuntu servers, set up directory services and then map the Windows workstations into a domain and share files etc. Windows 2003 SBS would be done. Even if I could do that but have a simple user database like in Windows NT and be able to replicate it. I could still sell it over Windows 2003. (Shoot I would not mind if Canonical were to sell it with esupport for maybe $50 or $100 per year per server or something. I could still sell it no problem!) But to my knowledge there is no version of Linux that can do this good out the box. So I am stuck pushing Windows to my customers.

I think people need to push Novell into making NDS (Or Edirectory as they now call it) Open Source. Edirectory is more robust then AD. Maybe as payback for their stupid Microsoft deal!  

How about OSX server, with Open Directory in Tiger, I can set up an OSX server, add another and replicate the database to be redundant and add Windows, Mac and even linux clients to the structure. Now I can only manage policies etc on the Macs. But I can add one Windows server to the mix and also add policy management to all the Windows machines. 

The key here is I can have scaleable directory services using open source products. And also get ease of use. 

Suse enterprise linux gives you the tools in Yast to set up Samba and Open Ldap etc, but it's complicated, not reliable and not easy to manage. 

Samba 4 sounds nice.. The interesting thing here is that by using Open Ldap and Samba 3 Apple is doing AD style services on the Mac OS now. With not many other tools then are avaliable on Linux. 

[http://www.apple.com/server/macosx/opendirectory.html](http://www.apple.com/server/macosx/opendirectory.html)

"Open Directory relies on powerful open source technologies, like Open LDAP and Kerberos, for seamless interoperability with other standards-based LDAP servers. It can even plug into environments that use proprietary services, such as Microsoft&#8217;s Active Directory and Novell&#8217;s eDirectory. For organizations that haven&#8217;t yet deployed directory services, the Open Directory server is an easy-to-deploy solution that lets small operations benefit from centralized information. And because there&#8217;s no per-user or per-seat fees, Open Directory can scale with the needs of your organization &#8212; without draining your IT budget."

"Support for Mixed-Platform Environments

Open Directory uses OpenLDAP, the open source implementation of LDAP, to provide directory services for mixed-platform environments. A common language for directory access lets you consolidate information from different platforms and define a single name space for all network resources. Whether you have Mac, Windows or Linux systems on your network, you can set up and manage a single directory; you don&#8217;t need maintain a separate directory or separate user records for each platform. This also streamlines the user experience: Users can move effortlessly between Mac and Windows computers &#8212; and still gain authenticated single sign-on access to directory-based system and network resources."

"NT Domain Services

Apple has integrated the NT Domain services of the popular open source Samba 3 project with Open Directory, making it possible to host NT Domain services on Mac OS X Server v10.4. You can set up Mac OS X Server as a Primary Domain Controller (PDC) or Backup Domain Controller (BDC) for your network, so Windows users can authenticate against Mac OS X Server directly from the PC login window. NT Domain services also enable Mac OS X Server to host roaming profiles and network home directories for Windows clients. Now any user in your directory can securely log in and access the same user account, authentication, home directory and network resources from a Mac or a Windows system. These capabilities make Mac OS X Server ideal for replacing aging Windows NT or Windows 2000 servers, without requiring businesses to transition to an expensive Active Directory infrastructure."

"Workgroup Management

Mac OS X Server provides advanced workgroup management tools for configuring and controlling your information infrastructure and your computing resources.

Workgroup Manager in Mac OS X Server simplifies system administration by providing centralized directory-based management of users, groups, and computers across your organization. Create standardized desktop configurations, set preferences and establish password policies, as well as control access to hardware, software and network resources. You can use any LDAP-based server to store these preferences, such as Apple&#8217;s Open Directory or Microsoft&#8217;s proprietary Active Directory.

Centralized Management
Workgroup Manager can enhance your Mac OS X users&#8217; computing experience, at the same time as it gives you easier control. Create custom environments, complete with different applications, settings and permissions for each group, and then configure systems across an entire workgroup or classroom in seconds. Managed system settings allow your users to log into an environment that&#8217;s appropriate to their needs and consistent from one computer to the next. Users&#8217; individual and group settings are immediately in effect and they have streamlined access to authorized resources &#8212; no matter where they log in. Settings are cached, so preferences remain in effect for mobile users, even when they disconnect from the network. New in Mac OS X Server v10.4, Preference Manifest allows you to set preferences applications and utilities not managed in Workgroup Manager. 

Managed Network Views
With Mac OS X Server v10.4, you can control what users see on the network. A managed network view is one or more network neighborhoods, which appear as folders associated with the Network icon in the Finder. Each folder contains a list of resources available to an individual user or group &#8212; and you can create multiple views for different client computers. Because the views are stored in Open Directory, a computer&#8217;s network neighborhood is automatically available when a user logs in.

Network and Portable Home Directories
You can also use Workgroup Manager to provide network-based home directories, so users can access their own personalized desktop, applications and files from any computer on the network &#8212; or use them to back up their work. With Mac OS X Server v10.4, PowerBook and iBook users can now enjoy synchronized versions of home directory folders locally and on the network. When a user goes offline, her home directory goes with her, so she can continue to work just as if she would back at the office. When she reconnects to the network, Mac OS X automatically syncs up selected content in her local home directory with the one on the server.


I know I am rambling. But I am shocked that this was not long ago a goal for Linux server companies. 

The thing holding apple back is that this only runs on Macs. if Apple ever makes this to run on any server and lowers the price. (Even though MS charges CALs, most small business doesn't pay them anyway. They sell you SBS with 5 licenses, but you can add as many users as you want in reality) it could take off for SMBs

Anyway, it would be interesting if Ubuntu lead the way with something like what Apple is doing but for a lower price. And like Apple provide all kinds of management tools for Ubuntu and other Linux desktops and also provide file and print services etc to Windows desktops. 


2. Stabilize the good features. Seems that Linux companies keep adding new features but never seem to make the good current features stable. I could care less about flipping windows and bouncing task bars if the normal X Windows sessions are not stable.


Anyway, I could be wrong about some of this stuff, so let me know how you feel!

---

### Post by 3rdalbum on 2007-04-09
I'm amazed that you consider any networking tasks in Windows to be easy :-)

OS X is mostly closed-source, and its performance is certainly less than optimal. Apple has demonstrated in the past with OS X Server that it doesn't really know about what enterprise customers want in terms of support, so I suspect these things are the real issues stopping everyone from buying Xserves.

Yes, it would be good to have these kinds of services available through the GUI on Ubuntu; but in reality it can all be done through the command line, and a good system administrator will do it that way. Incidentally, you might want to look at Novell's enterprise Linux offerings.

---

### Post by PurplePenguin on 2007-04-09
> **tymiles said:**
> 
2. Stabilize the good features. Seems that Linux companies keep adding new features but never seem to make the good current features stable. I could care less about flipping windows and bouncing task bars if the normal X Windows sessions are not stable.
A heck of a lot of linux development is done by small communities of hobbyists or individuals, not "linux companies".  They work independently on whichever area they are interested in.  It's not like a company with a committee that decides which features will be focused on.

The guys developing things like Beryl are not the same guys working on stuff like networking, printer drivers, sound, and so on.

---

### Post by aysiu on 2007-04-09
Since this isn't a support thread, I've taken it out of Absolute Beginner and into Community Cafe. I suspect it'll probably end up eventually in the Linux Desktop Readiness thread, but we'll see where it heads.

---

