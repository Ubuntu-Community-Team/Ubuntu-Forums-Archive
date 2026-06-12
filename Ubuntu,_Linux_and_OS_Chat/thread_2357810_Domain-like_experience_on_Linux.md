---
title: "Domain-like experience on Linux"
date: 2017-04-06
forum: Ubuntu, Linux and OS Chat
---

### Post by streamholder on 2017-04-06
Hello.

Let me say, before anything else, that this is all hypitetical and has the only objective to create a discussion on the current state of things. I'm not talking about any actual plan or prospected system!

Now, on to the thing, I started to think about this when my father's office Windows workgroup-based network started to get big, costly and complex to manage. I'm not here to say that Windows networks are evil and useless, but at least in my case, there is a lot of over-complication and not enough standard compliancy (let's just say that Windows does not like to play well with ISC-DHCP...).

I was wondering if there was any viable way to replace, and expand, the capabilities of a medium business' computer network.
Let's say, for the sake of argument, that these are the requirements:
[LIST]
[*]Central management of
[LIST]
[*]Credentials (with metadata and permissions)
[*]Data storage
[*]The usual stuff (Intranet website, mail, ...)
[*]Workstation configuration (e.g. which printers are available where)
[/LIST]

[*]"Remote" sessions (which would ideally be the default thing), where the login is done against the credential server and the user's home is mounted from the data storage system
[*]Individual workstation capabilities sharing (e.g. make a printer connected to a workstation available to the network)
[/LIST]

What I have in mind is a workflow like this: a user goes to a workstation, logs into his "credentials server" account, its workstation mounts its home form the storage server and possibly, depending on the metadata, also some additional application folders (under /opt2 or something like that) and adds them to the PATH.
Additionally, some network printers could be configured on the computer depending on the (centrally managed) configuration of the particular workstation and the particular user.
Now what the user has is its desktop environment, exactly how he left it on the last workstation he had logged into, and the default set of application (which are on the workstation) plus possibly the additional set of applications from the network, which could be per-user or not.

This is very similar to the experience I get in my university, on their Windows network. I know this can easily be obtained with Microsoft's Active Directory system.
What I was wondering is, provided there is a way to recreate a similar experience on Linux (worst case scenario you could write all the software from scratch, but I refuse to think that's the state of things!), how complex would it be to implement? What would be the local (per workstation) and network security implications? Has this been done before?

I would very much like to experiment on this, so if anyone has any experience or ideas, I would really like to talk about it!

Thank you.

---

### Post by SeijiSensei on 2017-04-06
> **streamholder said:**
> What I have in mind is a workflow like this: a user goes to a workstation, logs into his "credentials server" account, its workstation mounts its home form the storage server and possibly, depending on the metadata, also some additional application folders (under /opt2 or something like that) and adds them to the PATH.
Unix systems have been capable of doing those things for decades.  The original Sun applications, the [Network File System]("https://help.ubuntu.com/community/SettingUpNFSHowTo") and the [Network Information Service]("http://www.linux-nis.org/"), provided remote authentication and home directories.  Nowadays NIS is deprecated in favor of [LDAP]("https://www.howtoforge.com/linux_ldap_authentication")-based solutions, but NFS is still going strong.  There are other remote authentication protocols available as well like RADIUS.

The [Kerberos]("https://web.mit.edu/kerberos/") protocol developed at MIT offers a highly secure method for authentication.  In fact, it is the authentication method used by Active Directory.  

> Additionally, some network printers could be configured on the computer depending on the (centrally managed) configuration of the particular workstation and the particular user.
CUPS offers that as well.  Even the hoary LPD/LPR standards offered central management of printing.

Many scientific, engineering and educational institutions centrally manage hundreds or thousands of Unix-based networked workstations.  Solving these problems was a high priority for Unix developers, and most of these technologies date back at least three decades.

---

### Post by TheFu on 2017-04-06
Welcome to the forums.

Unix has been doing this stuff for decades - well before Windows.
We used NIS and automounter (NFS) in the early 1990s on a network with 6,000 users where I worked.
These days, I'd deploy **FreeIPA** and **autofs** for NFSv4 to achieve the same results.

I use autofs at home, but don't have enough users to make the hassles of FreeIPA worth the effort.

You can be much more secure than the Windows equivalents.  Kerberos on Windows has been hacked for years.  A TLA blocked a Defcon talk about this about 5 yrs ago, but it still got out. Don't think MSFT ever fixed it.  The Unix version never had the same issue.

Inside most companies, swapping out Windows desktops just isn't realistic and active directory isn't THAT bad. Enterprise Linux has learned to work with MS-AD.

It would also be worth being extremely clear about "domain" since that has many different meanings.  Active Directory is an LDAP implementation.  Windows Domains isn't the same as NIS-Domains nor is is the same as "domain names" we use for internet use.

As for printer management. This has been the first thing to be deployed on Unix systems for almost 30 yrs now in hybrid environments.  File and print using Unix servers is a staple for Windows networks.  I've deployed printer management for 6K printers over thousands of locations myself.  These were mainly printed to from Unix, but Linux would be exactly the same.  For Windows desktops, I haven't done this in years, but used to setup Samba to automatically load printer drivers and setup print queues on a per-floor basis.  Think we used IPP, not lpr.

There are a few how-tos in these forums for each of these things.

1 last thing - don't put HOME directories under /opt/ - put them under /u/ or /users/ or if you have a bunch, /u/001/ ---- /u/999/. Really just comes down to how large the per-user storage is and what your SAN can support for a single file system and I/O.

[https://www.freeipa.org/](https://www.freeipa.org/)
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
[https://help.ubuntu.com/community/AutofsLDAP](https://help.ubuntu.com/community/AutofsLDAP)
should get you started.

I see dhcp as a completely different issue, outside LDAP management, though you could store the data inside LDAP and use that for both DHCP and DNS needs.

Remote desktops can be provided using SPICE through a browser interface. I've seen this a a local University.

BTW, "medium sized business" doesn't tell us much.  Could be 3 servers and 5 desktops or 5000 desktops and 500 servers. The solutions would necessarily be different.  Plus, the fewer Windows systems, the easier.  Unix-to-Unix integrations tend to *just work.*  Whenever Windows gets involved, there is futzing required because the primary vendor is used to not having to play nice with others.

Sadly, for all these integrations, Ubuntu usually isn't the best choice.  RHEL and SLED tend to be much farther along in desktop integrations at a corporate level.  Ubuntu has been concentrating on the data center and servers much more than other business areas. Canonical doesn't really play in the enterprise desktop space at all.  They have great stand-alone desktops, but just haven't tried to make enterprise integrations work.

IMHO.

---

### Post by streamholder on 2017-04-06
You just opened a whole new world to me. Off to learning!

---

