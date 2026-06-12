---
title: "Ubuntu Server 18.04 - Preferences &amp; files storage like Raid 5 of all your PCs"
date: 2020-04-01
forum: Server Platforms
---

### Post by ptdanpin on 2020-04-01
Hello all

My qualifications are Electronic Engineer and Computer Science (Hardware Based).

My knowledge of networking is not big. Am trying to change it.

Started to use an old computer as a home server and since then a lot of projects came to mind.

I work with a lot of computers. I have 2 laptops, one desktop and one server. One laptop has Ubunto 20 (didn't have the paitience to wait for the official release), the server is Ubuntu 18.04 server, all other systems are Windows 10.

I would like to ask the community if my wish is possible and pointers on how to do it (documentation and so on). Everytime I make a change on a setting in a windows machine, I have to make the same changes in the other. Is it possible to have some kind of NFS server that can update my settings at log in time? OR is there another server solution for it?

Example: I transfer a file to my transfer folder and make a theme change in windows. This in the desktop. When logging in to the laptop, if it has connection to the server, it updates windows to its newer settings.

I know that I can have the solution of having the one hard drive in the server and boot from it in all computers, but that would not permit that i could use the laptop out of the local network area or network acess.

Your thoughts, ideas and comments are appreciated.

Best regards

---

### Post by darkod on 2020-04-01
Well, you can certainly setup a share on your ubuntu server. Maybe CIFS would be better option than NFS when the client is Windows.

But to use configuration files stored in that share, that would depend on your Windows configuration. So that is the part you have to investigate. Not having an AD (I assume you don't have one), you will probably have to setup things using the local policy. You might need to do that once on both computers but after that you would not need to make daily changes because they will simply pick up what you want from the share.

---

### Post by ptdanpin on 2020-04-01
Didn't know about CIFS. From what I have read, it's obsolete.

Right now I have a SMB share working. The only problem I have with it, is that the shared folders take some time to become online. Therefore Windows always shows a network connection error.

Regardless, what I gather from your comment is that I only need a share on my server reserved for Windows manegement.

Never thought of that, really. A bit ashame to have created that in a Linux forum.

Please confirm and thank you for your help.

PS: I am not very fond of fidling with Windows. It seems unnatural and less logical when comparing with any Linux distribution, but will not let this bring down my desire to have it running.

---

### Post by TheFu on 2020-04-01
Samba is just the Unix version of CiFS that Windows wants.
Samba being slow to be seen on the network is a name resolution issue. Fix that and it won't be slow.

NFS is best used between Unix systems. I&#8217;ve only used paid NFS clients for Windows. They were a pain and not $30/each, more like $130/ea.

As for the Windows questions, sorry. I&#8217;ve never had to support any Windows systems as an admin.  On Unix systems we'd use NiS, NiS+, LDAP or some other directory server.  if i needed to support a mixed environment, I&#8217;d deploy Freeipa and enable cached credentials. That is not a beginner-level undertaking.  Know about a few sites with over 5K clients using the commercial version of FreeIPA from RH with Windows, OSX, and Unix clients. Sorry, cannot share any details.

---

### Post by Morbius1 on 2020-04-02
>  Didn't know about CIFS. From what I have read, it's obsolete.
It's an unfortunate discombobulation of terms. CIFS was the term Microsoft gave to the original and at the time only dialect of SMB. They later renamed it SMB1. SMB1 today is considered deprecated. In Linux they kept the term CIFS but it refers to the Linux Kernel implementation of mounting a remote Samba / SMB filesystem on a client.
> Right now I have a SMB share working. The only problem I have with it, is that the shared folders take some time to become online. Therefore Windows always shows a network connection error.
That's somewhat confusing. If your Win10 machines are up to date you shouldn't be able to "discover" then connect to the Ubuntu Server at all since by default WIn10 disables smb1 on the client side. The same is true of Ubuntu 20. Discovery and name resolution by NetBIOS name is dependent on SMB1 so without it you may or may not see the server but will not be able to get a listing of shares. You must be connecting to the server via ip address.

You can fix the discovery issue with Win10 by implementing WS-Discovery on the Ubuntu server and with the Ubuntu 20 client by installing avahi-daemon on the Ubuntu server.

---

### Post by SeijiSensei on 2020-04-02
Or, perhaps easier, map a network drive to \\ip.addr.of.server, e.g., \\192.168.1.1.

---

### Post by Morbius1 on 2020-04-02
Yep, that's even better!

Static ip addresses are your friend in networking.

---

### Post by TheFu on 2020-04-02
> **Morbius1 said:**
> Yep, that's even better!

Static ip addresses are your friend in networking.

+1!!!

---

### Post by LHammonds on 2020-04-05
Regarding Windows settings going from machine to machine, that is called a "roaming profile."  If you do not have an Active Directory server, I am not sure how you'd enable this.

However, enabling that feature would likely cause more issues than you want deal with.  I used to use that feature back in the days of Windows NT and was OK for a while but there were issues sometimes with it not doing the sync correctly either at login or logoff and you end up with different profile directories on your PC that become disconnected.  That was enough to make me stop using it but as Windows continued to evolve over time, so has the "profile" where almost everything is stored under the user profile (downloads, documents, videos, etc.) and as such, the profile would become absolutely enormous.  Trying to sync that every time you login/logout would cause wasted time waiting on Windows.  Some things could be setup where specific directories are linked to network shares to avoid the files being replicated everywhere you login but that would just be a bandaid to the larger problem.

It is my understanding that roaming profiles will be discontinued (deprecated) at some point in the future but I don't know when.

The other solution for settings to follow you around is just the Windows Registry changes via a Policy Manager.  Windows Active Directory can handle every aspect of Windows' settings via the Group Policy Manager per user and per machine.  Without an AD server, you can run "gpedit.msc" and configure the settings for the machine but not per user (same for everyone).  After setting up the policy on one machine, you can export/import the settings to the others.

Another option would be to use Linux for identity management but a mixed  environment of Linux / Windows might be a bit problematic since the  solution will never support 100% of Windows' features.

Another option could be Azure ID where you login to Azure and join the Windows machine to Microsoft's Azure cloud and your login identity can travel from machine to machine if you are wanting SSO.  I am not familiar with this so I do not know the costs/advantages/disadvantages of this solution though.


And yet another potential solution is a cloud-based identity management that is more cross-platform friendly.  A quick search pointed me to [JumpCloud](https://jumpcloud.com/blog/set-group-policies-without-microsoft-active-directory).  I have no idea about this company, what it costs or if it really works.

There are a bunch of different ways to go but you really need to nail down exactly what your goal is and where you see it going in the future.

LHammonds

---

