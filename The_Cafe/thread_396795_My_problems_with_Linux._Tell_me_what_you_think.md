---
title: "My problems with Linux. Tell me what you think?"
date: 2007-03-29
forum: The Cafe
---

### Post by tymiles on 2007-03-29
Man there are 2 things about Linux that kill me right now.

1. Lack of easy to use directory services similar to AD in Windows, attached to file and print sharing. If you could set up a group of Linux servers and workstations (Linux, Windows or Unix workstatons) quickly and pretty easy like you can do with Windows or like an OS even closer to Linux, Mac OS (Mac Server and Mac OS are easy to roll out also) I could more easy sell Linux to my small business customers.

The thing that is insteresting with Mac Server is that they are using all open source software with closed source interfaces. But they make the Open Source tools do the same things that you can do with Windows XP/Vista and Windows 2003 Server and AD. 

Linux developers should look at the Tiger server and see how they use Open Ldap and Samba to replicate directory services across servers and setup login scripting to map drives. Same crap that you can do with Windows. This might be below some Linux people as a copy of MS but trust me if someone did this and made it cheep on Linux (Xandros is close but still a little pricy $450 per server and it needs work) You could sell this to Windows shops all day long! 

Imagine if I could go to a small business and put in 2 Ubuntu servers, set up directory services and then map the Windows workstations into a domain and share files etc. Windows 2003 SBS would be done. Even if I could do that but have a simple user database like in Windows NT and be able to replicate it. I could still sell it over Windows 2003. (Shoot I would not mind if Canonical were to sell it with esupport for maybe $50 or $100 per year per server or something. I could still sell it no problem!) But to my knowledge there is no version of Linux that can do this good out the box. So I am stuck pushing Windows to my customers.

I think people need to push Novell into making NDS (Or Edirectory as they now call it) Open Source. Edirectory is more robust then AD. Maybe as payback for their stupid Microsoft deal! :mad: 

2. Stabilize the good features. Seems that Linux companies keep adding new features but never seem to make the good current features stable. I could care less about flipping windows and bouncing task bars if the normal X Windows sessions are not stable.


Anyway, I could be wrong about some of this stuff, so let me know how you feel!

---

### Post by cowlip on 2007-03-29
> 
1. Lack of easy to use directory services similar to AD in Windows, attached to file and print sharing. If you could set up a group of Linux servers and workstations (Linux, Windows or Unix workstatons) quickly and pretty easy like you can do with Windows or like an OS even closer to Linux, Mac OS (Mac Server and Mac OS are easy to roll out also) I could more easy sell Linux to my small business customers.

Linux uses thin clients (there are no CALs for free distribs vs. Microsoft's Terminal Services stuff)--see Edubuntu for an easy demonstration of this--openLDAP, Red Hat Directory Server, webmin modules, etc.  Active Directory is the embrace-extend-extinguish descendant of openLDAP.  

Red Hat sells a lot of things (Red Hat Networks is similar to Windows Software Update Services) and Novell has their proprietary directory software as well (like Netware and Open Enterprise Server 2)

Samba 4 promises better Active Directory integration but of course MS has a huge interest in keeping the handshaking proprietary.

---

### Post by saulgoode on 2007-03-29
1) My general impression is that your problems are not so much with Linux, but with Microsoft. They are the ones who are not following the open standards properly and changing protocols just enough so that those who do experience problems.

2) I don't really disagree with you, but making use of graphics hardware when its available and off-loading processor workloads is a good thing. Also, the efforts toward supporting GPUs has led to a modularization of the X11 code which will ultimately benefit its development and improve its stability.

---

### Post by tymiles on 2007-03-29
I don't want to tie into AD though. I want like Open Directory on Mac OS, to be able to provide scaleable directory services or even Windows NT style replicateable domains to even just Linux or Unix clients (If MS is going to keep changing things) 

But with Open Directory in Tiger, I can set up an OSX server, add another and replicate the database to be redundant and add Windows, Mac and even linux clients to the structure. Now I can only manage policies etc on the Macs. But I can add one Windows server to the mix and also add policy management to all the Windows machines. 

But the key here is I can have scaleable directory services using open source products. And also get ease of use. 

Suse enterprise linux gives you the tools in Yast to set up Samba and Open Ldap etc, but it's complicated, not reliable and not easy to manage. 

Samba 4 sounds nice.. The interesting thing here is the using Open Ldap and Samba 3 Apple is doing AD style services on the Mac OS now. With not many other tools then are avaliable on Linux. 

[http://www.apple.com/server/macosx/opendirectory.html](http://www.apple.com/server/macosx/opendirectory.html)

"Open Directory relies on powerful open source technologies, like Open LDAP and Kerberos, for seamless interoperability with other standards-based LDAP servers. It can even plug into environments that use proprietary services, such as Microsoft&#8217;s Active Directory and Novell&#8217;s eDirectory. For organizations that haven&#8217;t yet deployed directory services, the Open Directory server is an easy-to-deploy solution that lets small operations benefit from centralized information. And because there&#8217;s no per-user or per-seat fees, Open Directory can scale with the needs of your organization &#8212; without draining your IT budget."

"Support for Mixed-Platform Environments

Open Directory uses OpenLDAP, the open source implementation of LDAP, to provide directory services for mixed-platform environments. A common language for directory access lets you consolidate information from different platforms and define a single name space for all network resources. Whether you have Mac, Windows or Linux systems on your network, you can set up and manage a single directory; you don&#8217;t need maintain a separate directory or separate user records for each platform. This also streamlines the user experience: Users can move effortlessly between Mac and Windows computers &#8212; and still gain authenticated single sign-on access to directory-based system and network resources."

"NT Domain Services

Apple has integrated the NT Domain services of the popular open source Samba 3 project with Open Directory, making it possible to host NT Domain services on Mac OS X Server v10.4. You can set up Mac OS X Server as a Primary Domain Controller (PDC) or Backup Domain Controller (BDC) for your network, so Windows users can authenticate against Mac OS X Server directly from the PC login window. NT Domain services also enable Mac OS X Server to host roaming profiles and network home directories for Windows clients. Now any user in your directory can securely log in and access the same user account, authentication, home directory and network resources from a Mac or a Windows system. These capabilities make Mac OS X Server ideal for replacing aging Windows NT or Windows 2000 servers, without requiring businesses to transition to an expensive Active Directory infrastructure."

I know I am rambling. But I am shocked that this was not long ago a goal for Linux server companies. 

The thing holding apple back is that this only runs on Macs. if Apple ever makes this to run on any server and lowers the price. (Even though MS charges CALs, most small business doesn't pay them anyway. They sell you SBS with 5 licenses, but you can add as many users as you want in reality) it could take off for SMBs

Anyway, it would be interesting if Ubuntu lead the way with something like what Apple is doing but for a lower price. And like Apple provide all kinds of management tools for Ubuntu and other Linux desktops but provide file and print services etc to Windows desktops. 

Thank you for your feed back. I hope this becomes an interesting topic. 

Oh and I don't care about MS. We can drop MS and AD out of the convo and just go with what you can do with Tiger server. Those are the kind of features I would love to see.

---

### Post by tymiles on 2007-03-29
> **saulgoode said:**
> 1) My general impression is that your problems are not so much with Linux, but with Microsoft. They are the ones who are not following the open standards properly and changing protocols just enough so that those who do experience problems.

2) I don't really disagree with you, but making use of graphics hardware when its available and off-loading processor workloads is a good thing. Also, the efforts toward supporting GPUs has led to a modularization of the X11 code which will ultimately benefit its development and improve its stability.

You are right about making use of new and more powerfull graphics hardware. I don't mind the fanciness. But when my normal XWindows sessions are slow, unreliable and buggy. I get irked that more attention is being paid to fanciness. I want to be able to carry my Ubuntu laptop around just like Millions of Windows and Mac users and use it 95% of the time with no issues. Not like with some installs of Linux where I am lucky 50% of the time to get it out of suspend mode. 

Thank you for your post! :-)

---

### Post by saulgoode on 2007-03-29
I have really drifted away from the latest developments in networking technology over the last five years or so and am certainly unqualified to help you. Your observation on the Mac OS implementation is intriguing and something about which I know absolutely nothing.


You might wish to consider working with the appropriate project and offer your expertise to help in its development. Even if you are not a programmer, projects are always seeking testers, documenters, and technical feedback from knowledgable users. You might even convince your employer to permit you to do such activities "on the company's dime" (which is increasingly how development of such "technical" solutions is being supported).

---

### Post by cowlip on 2007-03-30
You might get more responses in the Networking forum too: [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)  (eg., this thread is kind of related to yours, expanding Linux's networking: [http://ubuntuforums.org/showthread.php?t=394169&](http://ubuntuforums.org/showthread.php?t=394169&) )''

If your Xwindows is slow and buggy, is it a driver (closed/open source driver?) or an ACPI problem?  You could do noacpi or acpi=off in the kernel boot options in grub.

---

### Post by 3rdalbum on 2007-03-30
I think what's probably holding Mac OS X back on the server is that it's got performance issues compared to Linux; Apple doesn't seem to be very interested in actually providing support to its server-room users; the included software changes too much (desktop users don't notice it); and true open source provides more flexibility than what Apple claims to offer.

---

### Post by tymiles on 2007-04-01
I work for the federal government. There are a couple of reasons why people (From what I see) don't buy apple servers, but nether have anything to do with Linux. 

1. No choice in hardware. 

2. Lack of enterprise support for hardware and software. 

Option one speaks for it's self. Most people like to have a choice in hardware over choice in software for some reason. So for instance my agency used to only use IBM computers till Lenovo bought it. Then because of Lenovo being Chinese our agency switched quickly to Dell. Same software and applications, just had to add drivers to the image and we were up and rolling. 

Option 2. Apple is WAY behind companies like Dell when it comes to enterprise support for hardware and software. Apple has no kind of enterprise support cycles. With companies like Dell and Microsoft, they come to you and show you everything that is going to happen over a 3 to 5 year span and how it will affect your company etc. Apple is like the CIA of computer companies. You don't know what they are going to do with Hardware and software till it happens. 

Yes for things like my MySQL Apple's server software does not perform as well as Linux. In reality a lot of things don't perform as well on Windows as Linux ether. But those are not the markets that Microsoft and Apple are aiming at. They are aiming at File and Print services. Intranet Web Services, directory services. And Windows and Mac Server both perform great at these tasks. Linux would be great also. But Linux doesn't have those unified services. (Yes you can do intranet web services no problem on Linux. You can do file sharing etc. But you can't very easy lay out a network of servers and workstations like you can with Windows and Mac OS) 

Man if I could just come in and drop in Ubuntu servers in the place of Mac servers or Windows servers for my customers and do the same things. MS would be throwing law suites like baseballs. (FAST!)  But MS knows that no company makes an OS now that can be a drop in replacement in enterprises for file, print and directory services. They control that market. But any company with a similar product that costs less could snag a chunk of that market.

---

### Post by cowlip on 2007-04-01
.

---

### Post by DoctorMO on 2007-04-01
Most linux only networks work quite well, never need fancy tools because they have really expensive administrators who are experts in the field. the cost of reducing that complexity and manageability to the level you require is large and the dogged determination by systems administrators to work together with software developers in order to push through such a great tool set would be beond the reach of most volunteers making python programs.

Your best bet is to do some work in getting the kinds of tools you want designed, it's obvious that the community has the code sitting there to do the work and no one said you had to be a programmer to start a project and do all the design and project documentation.

---

