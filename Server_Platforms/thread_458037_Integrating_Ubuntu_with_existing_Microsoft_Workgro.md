---
title: "Integrating Ubuntu with existing Microsoft Workgroup (LAN)"
date: 2007-05-29
forum: Server Platforms
---

### Post by kmseck on 2007-05-29
Hi,
I'm very new with Ubuntu and because some friends told me that Linux can be integrated with Microsoft Networks (workgroup) for internet security, and access control purpose.

However, I sincerely hope that someone could advise and guide me on this.

Just install Ubuntu last week end, very impressive and convincing, however, a bit hiccup with the display driver, unable to set to 1024x768, (flickers), remains at 800x600.

Really hope you experts could assist me, thanks.

Seck

---

### Post by tact on 2007-05-29
Not exactly sure what you want to do or what your question is.

Yes you can connect your ubuntu machine to a windows network.  If set up to use DHCP to get an IP address your ubuntu box will talk whatever DHCP server is on the LAN and get an IP address no problem.

You can also share folders and files with windows machine users too.  
- You will automatically see any shared folders on windows machines. 
- If you want to share files/folders on the ubuntu box you must follow a few simple steps.  :)
-- choose or create a folder, right click on the folder
-- select "share folder" 
-- if this is the first time you have tried sharing folders you will get a message box saying you have to install NFS or Samba to share files.   Both options will be selected.  Leave both selected (but to share with windows you will use samba).  let the installation go ahead.
-- once thats finished choose to share the folder to windows network (smb share)

Now (or soon) your folder will be visible to windows machines (allow several minutes for the new share to be propogated to all the windows machines, its a windows thing, it can take time).

Notes:
By default samba (smb) is set up to require a username and password from anyone to access a share on your ubuntu machine.  Have a look here for help:
[http://www.samba.netfirms.com/addusers.htm](http://www.samba.netfirms.com/addusers.htm)

Also note that any files you place into the shared folder will need to have appropriate permissions set on them - or else they may not be visible or accessible to people who try to access them.   to set a file permissions perhaps the easiest way is to right click on it > Properties > Permissions and make sure that the file is "readable" to the category of people called "others".

---

### Post by kmseck on 2007-05-29
Thanks.

I'm sorry for not precise enough.  

My main idea was trying to find a solution to secure and control internet access in Windows environment (workgroup), however, a friend told me that we need not invest too much in Windows Server and so forth, such control can be simply done with Linux O/S.

That's how I get started with Ubuntu. Honestly it is fasinating after just simply installed the 7.04 version for desktop.

Thanks again.

---

### Post by Alterax on 2007-05-30
I think I know what you mean.  It's the same troubles that I have worked with in my own workplace, which was primarily a Windows 2000/XP/2003 environment (before I started anyway...heheheh).

We were having a lot of problems with unauthorized Internet access from our users, and we had a limited budget to put a stop to it.  Turns out, there was a pretty cost-effective fix for most of this:

I took an old desktop computer that was headed for retirement (Pentium-class, 19 GB hard drive and 256 MB ram).  I added an extra network card on it, and set it up as a SQUID proxy server.  This one I didn't set up with a graphical environment; command line works just fine for this once you learn to use it.  I put this between my network's main switch and the outgoing Internet access.  It was a pain to get together at first, but once it was all said and done it actually worked out quite nicely.  I can now set which computers can go through, at what times, and even make a list of what sites cannot be accessed, and the processes have been automated so if there's a power outage, it starts the services back up.

Squid is much more powerful than that, but I haven't really explored what all can be done with it since that is all I need at this time.

It also helped to have a better idea of what was going on with my network.  So I set up another machine with two network cards, a 20 GB hard drive (The PC was a Pentium II, 512 MB RAM).  This one I also did not install a graphical environment with.  No need for one in this case.  Since my switch is managed, I set one port up to mirror the incoming and outgoing traffic that was headed outside the network (to the SQUID server).  The other I plugged in to control the machine remotely through.  Then I installed SNORT (not in the repository, but it's not hard to do from source) and BASE (Basic Analysis and Security Engine).  What it does is watch the traffic that goes through, compare it to a series of rules.  If anything sets it off, it logs it to a database that I can study using a web browser.  Adding NTOP gave me the ability to see realtime network statistics (load on the network, who's sucking up the bandwidth, et cetera).  This has been really useful since it's helped me to find malfunctioning network cards, policy violations, and even to nip a couple of viral outbreaks before they became serious.  An IDS (Intrusion Detection System) like this was cheap to implement, and it's saved me so many person-hours I have no clue how we went so long without one.

These sound complex at first, and it can be difficult to get started with them.  There is no "easy" button, but thankfully, there are plenty of tutorials out there, as well as those of us that have done it ourselves and may be able to help if you need.  If you are interested in trying any of these, please let me know.  I'll be more than happy to help you out on these.

--Alterax

---

### Post by kmseck on 2007-05-31
Friend,

Thank you for real Technical knowledge which really knocks me out, man!!!
Sorry for asking you so innocently.

Can you provide any links, so that I could do some research.

Thanks.

kmseck

---

### Post by angelmartinezn on 2007-05-31
If you wanna an "advanced" router or proxy integrated in a 'black box' (i.e. an old pc with linux with a proxy or a gateway service...) you can take a look for distributions like ipcop... [http://www.ipcop.org/]("http://www.ipcop.org/"). These distribuitions are made to deploy easily an firewall/internet output control.

---

