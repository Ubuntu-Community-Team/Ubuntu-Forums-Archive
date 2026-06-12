---
title: "Windows XP Network Passwords (samba)"
date: 2007-09-03
forum: Server Platforms
---

### Post by prince_of_hackers on 2007-09-03
OK, I think this is more of a Windows issue than a Linux/Samba issue, but I expect I'll get more help here than from Windows users, hehe. 

 Anyhow, here is the question: I have set up two different Samba servers on Ubuntu (6.06 Dapper Drake SPARC) and have no problems accessing them. 

 However, on some of the Windows clients that are accessing the servers, the users are required to type their network password each time they reconnect to the network drive, and on some, they are not. 

 The Windows XP Pro and Windows 2000 machines have a "Remember this password" box that seems to work correctly - if checked, you don't have to enter the password again unless it is changed, and if unchecked, it only remembers the password for the currect login session. However, the XP Home machine do not have this checkbox, but some of them will remember the passwords forever, and some not at all. 

 I have searched through Microsoft's Knowledgebase extensively, and found lots of good information, but nothing that explains this issue. 

 The XP machines are all systems I installed, configured, and updated myself, so they are all running pretty much the same stuff in the same configuration, all the latest service packs and patches. The only difference I can think of in their configuration is that some were installed off of the OEM CD's that came with them, while some are custom built systems that were installed using retail CD's. So unless the user's have installed something I am unaware of, I can't explain the difference in behavior.

---

### Post by cox377 on 2007-09-03
This isn't really answering your question but more of a question i'm asking.

Basically, have you setup the users shares on the samba servers in their policy or have you just manually added the shares to each and every users machine

IE is roaming profiles supported?

Much appreciated

CoXen

---

### Post by prince_of_hackers on 2007-09-04
No, I'm not using roaming profiles, most of the client machines are XP Home, and Home doesn't support that anyhow.  I would like to set up home directories, but I haven't gotten around to it yet.  The way I have it set up is as a shared directory, and each user has their own username/password to access it.  I followed the example for a simple workgroup shared storage location on Samba's website, but I don't remember the exact link right now.  Anyhow, the way it works is that each user has an account on the server, but Samba forces the user to be the owner of the shared directory.  (A special account I set up just for that purpose)  Then each machine has a mapped network drive to that share, and each user uses their own username/password combo to access it.  Anyhow, this all works fine, I just can't figure out why some machines retain the password and some don't.

---

### Post by HermanAB on 2007-09-04
Hmm, are the username and password on Windows exactly the same as the username and password on Samba?  If not, then you may have some issues.

Also, don't ever rename a user on Windows.  Always create a new user, since Windows gets its balls in a twist if you try to rename things, since it never actually forgets the original name and some things will use the old name and some the new one.  This is likely the source of your troubles.

Sooooo, you may be able to fix things by creating new user accounts on Windows and Samba and then copying the data and settings over and finally deleting the old user accounts.

Cheers,

Herman

---

### Post by prince_of_hackers on 2007-09-04
I already thought of the username and password being the same on Windows as on the Samba server, but it doesn't seem to make any difference - the same computers still remember the passwords, and the rest still don't.

Incidentally, it seems to be ALL users accounts on certain XP machines that remember the passwords, so it apparently is something different on these machines.  I did find a policy setting in XP Pro (Network access: Do not allow storage of credentials or .NET Passports for network authentication) to turn this on or off, but it seems to be always enabled on XP Home machines.

To the best of my knowledge, none of the XP user accounts have been renamed.  I know I haven't renamed any of them, as I have run into the problem of Windows not renaming accounts correctly in the past.  However, as I said before, these are XP Home machines, users other than myself could have renamed accounts.

---

### Post by HermanAB on 2007-09-04
Nope, I guess this is an opague part of Windows...

---

### Post by WCD on 2008-03-31
Did you find a solution to this issue?

---

### Post by prince_of_hackers on 2008-03-31
No, no solution as of yet. I have noticed that these issues also occur on a Western Digital NetCenter accessed from XP Home too, but I am sure this is because the NetCenter is running Samba in some form. The one thing I need to try is mapping a drive to a share on an actual Windows machine, and see if the problem persists. (Hmm, don't have any spare Windows servers laying around, hehe) I have noticed since then that the problem is even worse under Vista, the home version of Vista will only connect to the Samba share once, then will refuse to connect ever after even if the user supplies the password again, where XP will reconnect just fine once the password is given.

---

### Post by likuidkewl on 2008-03-31
This may seem odd but we had a similar issue.  Only it was the limited profiles in XP that were doing this.  This solution is weird but worked for us.  As always your mileage may vary.

In My computer Map the MAIN samba share<used groups for this >, then logon to the share, make sure you have the permissions you need to view the users directories(is used), then create a shortcut to the drive on the desktop by right clicking the network drive then create shortcut and drag to the desktop. Don't create one manually by "Create new shortcut" via the right click on the desktop or whatever that is where OUR problem was<Tnks B.G.>

You can also try this to see what is stored and possibly try adding connections there, we only use it to clear passwords so I don't know if it works to store well or if it is even available in Home.

Run->"Control keymgr.dll" w/o quotes but typed just like that.

HTH

---

### Post by binary00mind on 2008-04-01
I have very similar problems as Some of You..And the best way to deal with that is to delete all those passwords..I do that constantly. Uncle Bill and his "microcompany" don't like Linux users..We are dangerous..There are tools, that can delete all the passwords, network, terminal, IE, telephones etc..a la carte...either  till next reboot or forever. Depends which one we talk about..I don't want to give windows the chance to adjust.So I am scared to mention the names of these little tools. Also from ethical point of view and the forum conduct So Gals and Guys search for it...it is very easy to find. It is no warez or some patch on the underground scene. they are a legal, home made, open source tools..i know that you will prevail...The bottom,line is that I don't like the way Windows treat Linux users in terms to limit us to use a basic services.They think they own the networks..  .

---

### Post by prince_of_hackers on 2008-04-01
No offense meant, but I don't care much for the tone of the previous post. I may prefer linux ten to one over windows, especially for servers, but that doesn't mean that Microsoft products don't serve their purpose. And just think, if all those hardware vendors hadn't produced tons of cheap commodity hardware designed for Windows, where would linux be today and what would it run on...? Linus Torvalds whole idea when he started linux was to run a UNIX-like operating system on cheap x86 hardware instead of expensive mainframes that no home user could ever afford.

---

