---
title: "Best Practice File Sharing Samba Ubuntu"
date: 2018-03-29
forum: Server Platforms
---

### Post by gcruthers on 2018-03-29
Setting up file sharing on Linux server (Ubuntu) with Samba for Windows 10 clients. Originally setup this environment 7 years ago on Fedora server, but I am uncertain that I did it in the best practice manner. My question is this: For a shared directory on the Linux server, how do I give multiple users full permission to that share so that they can edit/delete sub-directories and files, whether they created (own) them or not?  For example, I have several different groups of users who will have access to their groups shared directories with full permission in those directories.  On my old server I did a work around that I am sure must have a better way.....I created a generic Linux/Samba user with full permission to each group share, then through a login script on the Windows clients mapped them to that share as if they were the generic user (ex. public_user accessing the public share).  It works, but there is no accountability as to tracking changes or newly created files or directories, since everything is owned by the generic user.  This is my first question for this forum.  Any help is greatly appreciated.

---

### Post by slickymaster on 2018-03-29
Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2018-03-29
Your details are missing some key components.  Are your Windows clients logging into their computers via Windows AD, or Linux Samba AD or just individual/local workgroup accounts?

Also, if you want a public access file sharing area that does not need security applied, there is a way to create a public share and not require using credentials to access it using nobody:nogroup.

Here are some best practice ideas to consider:


[list]
[*]Plan your structure and configure permissions based on security  groups rather than individuals.  This will allow helpdesk to configure  accounts to gain appropriate access rather than modifying/complicating  resources.
[*]Be consistent in your structure and naming.
[*]Prevent users from creating shares on their own PCs to help ensure important documents are stored in a central location that can be backed up
[*]For Windows servers, do not include the "EVERYONE" account in share permissions to reduce risk of viruses spreading.  Use "Authenticated User" instead.
[*]Include a deny group in every share you create.  The deny group will usually be empty but will be there if needed in an emergency such as an investigation or termination.  Deny takes precedence over grant.
[*]Don't mix business and personal files.
[*]Keep the amount of shares to a minimum and use folder structure to organize/categorize.
[/list]


LHammonds

---

### Post by gcruthers on 2018-03-29
The Windows clients only login locally.  I run login scripts to connect them to their Linux Samba shares.  So, the users exist in Linux and are replicated in Samba.  They have private home directories as well.  There are 11 shared directories for groups.

---

### Post by volkswagner on 2018-03-29
Setup ACLs for more granular control like ability to set default group permissions.
[This]("http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm") has been my go to resource for file share permissions.

You may consider setting up Active Directory Domain Controller with SAMBA4 for central management.
you can manage workstations and users with group policy and much more.

---

### Post by gcruthers on 2018-03-30
Thanks volkswagner....have been thinking since this post about whether it would be best to go Open LDAP / Samba.....looking like that is what I will need to do to achieve more granular security.

---

### Post by LHammonds on 2018-04-01
The best domain controller for Windows clients is Windows server.  However, if you can't go that route for whatever reason, Samba would be the next best option.

I have some research notes for [setting up Samba as a Domain Controller]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=235") but it is still very-much in the early stages and should not be considered "documentation" by any stretch of the imagination.  I want to setup a Raspberry Pi as my home DC but due to technical difficulties, have not been able to continue further until I buy some more hardware.

LHammonds

---

### Post by volkswagner on 2018-04-01
> **LHammonds said:**
> The best domain controller for Windows clients is Windows server.  However, if you can't go that route for whatever reason, Samba would be the next best option....

LHammonds

Best is a bit subjective. Samba AD DC can save significant money in license fees. There's no
need to purchase user/machine CALs nor the Server license itself. This is good for shops
that are already skilled in Linux administration, so there shouldn't be added cost for Linux 
learning curve, thus it should truly be less expensive than running Windows Server for AD DC.

One word of advise. It's a good idea to heed the advise on the SAMBA Wiki. You should have separate
domain controller and fileserver. Combining the two adds complexity with user ID vs names for groups/users.
This complexity isn't really documented, so that's why it's good to keep separate servers.
I prefer to get a server with enough RAM to run virtual machines, so I can have multiple servers on one physical machine.

PDC terminology really doesn't apply in modern Active Directory Domain Controllers. 
All domain controllers have equality with the exception of FSMO roles.

---

### Post by LHammonds on 2018-04-02
> **volkswagner said:**
> Best is a bit subjectiveOf course it is subjective.  I made a very broad statement with very little "source" information about the OPs environment and knowledge regarding Windows or Linux administration.  The OP does not have/utilize centralized credentials and I think we can all agree that having a DC would be a good idea for a multitude of reasons over trying to manage a network of silo PCs.  The OP seems to be trying to figure out what kind and how.

I agree keeping the DC and file server separate is also very important.  If cost is an issue (only have 1 server), buying a couple of Raspberry Pi's is less than $100 total which is two DCs up and running.  Very do-able for just 11 PCs and if done right, can scale up with better hardware as needed as company grows.

There is no question that going the Linux route will be less $$ in terms of licensing.  However, a mixed environment can have additional hidden costs in terms of complexity and maintenance.  I hope the OP will create detailed documentation for the next person that comes next to support what is created.

Samba AD can at best function at a [Windows 2008 R2 domain level]("https://wiki.samba.org/index.php/Raising_the_Functional_Levels") so it is important to understand that Samba AD is not identical to Windows AD and the same goes for managing permissions between Linux and Windows.

> **volkswagner said:**
> PDC terminology really doesn't apply in modern Active Directory Domain Controllers.Correct.  I'm just old school and think in terms of always having more than one and need to stop saying "PDC"

LHammonds

---

