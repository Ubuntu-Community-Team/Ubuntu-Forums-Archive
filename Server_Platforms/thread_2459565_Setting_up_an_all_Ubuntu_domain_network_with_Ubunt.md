---
title: "Setting up an all Ubuntu domain network with Ubuntu clients"
date: 2021-03-21
forum: Server Platforms
---

### Post by karlg93 on 2021-03-21
Hi there,

I'm trying to make a domain network (in virtual machines for now) using only linux based OS's as part of my studies.
I've researched certain parts of this process and am famililar with the process of making a domain network using ubuntu, however I can't find any clear guides on things like redirecting domain users home directories to a network share, or having the client machines mount a number of NFS shares (like how Group Policy would work in Windows).

My goals for this setup are:


[LIST]
[*]Setup a Domain controller (either AD or LDAP) using ubuntu server and redirect users home directories to network share (NFS). 
[/LIST]
 

[LIST]
[*]Setup Truenas Core servers for NFS file sharing and create policies for ubuntu based client workstations to mount NFS shares when domain users log in. 
[/LIST]
 

[LIST]
[*]Join ubuntu desktop clients to the domain with the configuration described above. 
[/LIST]

If anyone could give me a clear beginners step by step guide on how this could be achieved I'd really appreciate your help.

Thanks in advance.

---

### Post by TheFu on 2021-03-21
Unix doesn't have/need "domains" in the same way. Each system is stand-alone for everything that isn't something you specifically setup to be otherwise.  Plus, if the domain controllers are unavailable, Unix/Linux systems will keep working.
The easiest would be to use NIS+, but the server only runs on Solaris. That was a Sun Microsystems decision back in the 1990s never to allow non-Sun (no Oracle) Solaris systems to have an NIS+ server. NIS+ clients for all Unix-like OSes exist. This can't be used in a 100% Linux-only environment. 

**NIS** (as opposed to NIS+) has security failures, but supports centralized management (using yp* commands) users, groups, netgrps, hosts, networks, and other types of network specific files. NIS can be setup in a few hours (or minutes to add a new server/desktop) once you know what you are doing. Wouldn't hurt to do that just to gain the historical understanding.  But don't leave it up, due to the we-trust-everyone security stance.

For policy management, tools like **ansible**, **puppet**, **chef**, **salt** or **rexify** are used.  NIS is rally easy. Clients and servers for linux exist. Since Unix systems each have policy files local to the system which only an admin can modify, those tools listed are the method used to ensure consistent policy deployments. Ansible is the easiest, but for decades, admins would use custom ssh/rsh scripts to manage hundreds of servers. Those tools basically do the same thing, just in a published, standardized manner that someone knew to a company would already know without 6 months of learning the "local admin's scripts."

For automounting storage, use **autofs**. There is a guide at help.ubuntu.com.  Never used of Truenas. We used NFS either from a central server or netapp storage.  NFS is NFS if low-end NAS storage is avoided, IME.  Autofs grew out of the amd/automounter projects 25 yrs ago.  It is rock solid.

Check out **freeIPA**. It does the stuff that NIS does, but in LDAP with better security and a GUI. Redhat is behind it, but has been moving over to a proprietary version (walled garden). I've seen it, but not deployed it myself. Never took the time. Don't know if the server runs on ubuntu/debian. I do recall it took about 5 yrs to port the full FreeIPA server from RHEL/CentOS to Debian. FreeIPA is what happens when 50 smaller projects get munged into 1 larger project for enterprise use. They expect us to deploy onto a 4-CPU Xeon with 16G of RAM and not worry that 50 different languages were used across all those other projects. At a minimum, you'll likely deploy some tools using languages you've never even hear about before.

There are a few LDAP management GUIs, but most are php webapps, which scares me. I have a personal fear of php webapp security.

For a few years, I used Zimbra's LDAP with POSIX extensions to provide NIS-like centralized password, group, user, management at a few small companies. It was beautiful and we integrated that with not only end-user logins to Linux both with a number of other webapps for CRM, project management, git, DMS, and file servers.  Then it was time to upgrade Zimbra which required removing all the POSIX extensions, doing a massive upgrade, then re-adding the POSIX extensions again. Did this a few Zimbra upgrades. It was always a pain and always required some custom config modifications deep inside Zimbra. I really need to pull all the users out of the Zimbra LDAP and put them into an external LDAP, then hook Zimbra to the other LDAP for user authentication of email.  Anyways, since I stopped using the LDAP in Zimbra for central user management, all the zimbra upgrades have taken 70% less time and generally worked first time.  Interactions and system-to-system dependencies can be difficult. That applies to all software systems.

None of this stuff is for beginners, I'm afraid. Jr Admins wouldn't be responsible for deploying this anywhere, but it is a good goal. One of the best I've seen.  I need to do something similar, just add it to the list of 537 other things I'm supposed to do - this week. ;)

---

### Post by Doug S on 2021-03-22
Have a look at the [Ubuntu Serverguide table of contents]("https://ubuntu.com/server/docs"). While always desperate for subject matter expert input, the severguide was moved from docbook to discourse for 20.04 and the Ubuntu server team has been giving it more attention lately. Older serverguides are still available via the parent link, which TheFu also mentioned, [help.ubuntu.com]("https://help.ubuntu.com/")

---

### Post by karlg93 on 2021-03-22
Thank you for all that information. I'll research everything you've shared. :)

---

