---
title: "How can Windows clients change permissions to Samba sub-directories?"
date: 2010-08-08
forum: Server Platforms
---

### Post by beetlejuice321 on 2010-08-08
**I need assistance setting up a Samba File Server where designated office staff can change access to sub-directories created by Samba users.**

I am currently trying to replace a file server with Ubuntu 10.04 server.  This file server will be used by a small organization (30-50+ users).  They currently do not require a domain controller (many clients still using Windows XP Home).  So file access has been setup using Samba as a "workgroup" network, using user/group level security on the server shares.


**What I have been able to accomplish so far:**

*Install and configure Samba, including network shares.
*Setup new Unix & Samba users (sync'd).  
*Verified Network share access and permissions.

**Remote Management:**
Remote Management of the server has been tested and works perfectly using [Webmin]("http://www.webmin.com/").  Alternately an administrator can use SSH or SWAT, but Webmin has worked well for staff who are not familiar with a Unix/Linux command line.


**What I need:**

*Ability for a user(s) to change access to Samba shares sub-directories created by Windows clients, from a client workstation.  

**Here is a scenario:**  A manager creates a directory within the Samba share called "Private HR Data", she then wants to add users/group access to this directory for access by appropriate staff.  In this situation we do not want to create a whole new Samba share, but simply restrict access to this sub directory.

Now to my understanding Samba cannot perform any of these tasks.  And the only way I can think of to accomplish this is to change the Unix Permissions of these directories which precedes the Samba access.  While I think this method of controlling access to shared sub-directories will work, it does not allow remote administration other than SSH (command line).  

What would be ideal is for a user to right-click on the directory/file in Windows and be able to see, add, remove, access to data.  Alternately, what would make sense is if there were a web-based file browser for Linux that would let any user authenticate as an administrator, view all files on the server (just as you can in CPANEL or for many web hosting accounts), and change user/group permissions accordingly.

Other then this I am at a loss as to how to resolve this issue. Is there a way users can easily change access to these created sub-directories from client workstations?  Any help or recommendations is greatly appreciated!



NOTE ON CURRENT SYSTEM

**The Current Server:**
The current file server runs Windows Server 2003.  Access to shares is controlled via users/groups created on the server.  Users connect through a mapped network drive.  Office staff are able to change access to directories created by users by using RDP (Remote Desktop Connection).  With this native Windows tool, they can login to the server and add, remove, or change access to any directory/file easily.  As is the case with Windows, everything is done through a GUI which makes administration very easy for the staff to manage.

**Note:** *The reason for the file server change is due to costly Microsoft licensing restrictions, especially if a Domain is implemented.  A simple file server using a Windows Domain Server and CAL's licensing can be very expensive for 50 users. In addition the Linux server can provided more services out of the box such as Groupware/email, Intranet/Web Server, etc.*

---

### Post by clrg on 2010-08-09
Just that to make sure I understood correctly: The staff is able to administer Samba with SWAT in order to create and delete shares and modify permissions of those. The only thing they cannot do is modify permissions of folders in shares.

If so, I don't see any problem. Have them provide you with a list of subfolders/permissions they want, and then set up shares for them. If they need to change the permissions afterwards, they can do it with swat. If they need to create a restricted "subfolder" for HR, have them create a new share.

I know this is not what your office staff wants, but there is currently no translation of NTFS permissions to unix permissions. In order for them to set file and folder permissions using samba, those settings would need to be applied on a filesystem level on the server, which samba does not provide.

In the company I work in, we have a number of shares with very specific permission settings. No need for restricted subfolders. If one is necessary, a new share is set up.

I know I didn't provide a solution but a workaround. I hope your office staff will settle on setting up new shares on swat :)

---

### Post by beetlejuice321 on 2010-08-09
Thanks for the reply "clrg".

Yes you are correct the staff have access to SWAT, Webmin, etc, to create new shares, users, and groups.

The problem with creating a new share for every directory requiring specific access is for some users (who can view those shares) is there would end up being a large number of mapped network drives.  

Currently things are nice and simple.  Staff have one mapped drive, and everything is organized in a hierarchical fashion.  And people have varying access to directories.

Its to bad if Linux/Samba can only allow users to modify access to the actual Share itself.

I did find reference to this on the topic of Samba ACL's documentation, but I can't even figure out how to get it to work (see below)....




[http://www.samba.org/samba/docs/man/Samba3-ByExample/small.html#id2558104](http://www.samba.org/samba/docs/man/Samba3-ByExample/small.html#id2558104)

In the book **"Samba-3 by Example: Practical Exercises to Successful Deployment"**, is mentions.
[B]
How can I manage user accounts from my Windows XP Professional workstation?[/B] 

"Samba-3 implements a Windows NT4-style security domain architecture. This type of Domain cannot be managed using tools present on a Windows XP Professional installation. You may download from the Microsoft Web site the SRVTOOLS.EXE package. Extract it into the directory from which you wish to use it. This package extracts the tools: User Manager for Domains, Server Manager, and Event Viewer. You may use the User Manager for Domains to manage your Samba-3 Domain user and group accounts. Of course, you do need to be logged on as the Administrator  for the Samba-3 Domain. It may help to log on as the root account."



[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2614541](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2614541)

**Modifying File or Directory Permissions**

"Modifying file and directory permissions is as simple as changing the displayed permissions in the dialog box and clicking on OK. However, there are limitations that a user needs to be aware of, and also interactions with the standard Samba permission masks and mapping of DOS attributes that also need to be taken into account.

If the parameter nt acl support is set to false, any attempt to set security permissions will fail with an "Access Denied" message.

The first thing to note is that the Add button will not return a list of users in Samba (it will give an error message saying "The remote procedure call failed and did not execute"). This means that you can only manipulate the current user/group/world permissions listed in the dialog box. This actually works quite well because these are the only permissions that UNIX actually has.

If a permission triplet (either user, group, or world) is removed from the list of permissions in the NT dialog box, then when the OK button is pressed, it will be applied as no permissions on the UNIX side. If you view the permissions again, the no permissions entry will appear as the NT O flag, as described above. This allows you to add permissions back to a file or directory once you have removed them from a triplet component.

Because UNIX supports only the &#8220;r&#8221;, &#8220;w&#8221;, and &#8220;x&#8221; bits of an NT ACL, if other NT security attributes such as Delete Access are selected, they will be ignored when applied on the Samba server.

When setting permissions on a directory, the second set of permissions (in the second set of parentheses) is by default applied to all files within that directory. If this is not what you want, you must uncheck the Replace permissions on existing files checkbox in the NT dialog before clicking on OK.

If you wish to remove all permissions from a user/group/world component, you may either highlight the component and click on the Remove button or set the component to only have the special Take Ownership permission (displayed as O) highlighted."

---

### Post by clrg on 2010-08-09
I don't know about Samba ACLs, I've never used them. I can't give you any advice on that.

I think with Faildows 2k and later it is possible to mount volumes in an empty NTFS folder on the local file system (although I might be mistaken, I've not used that OS for a long time). Would it be acceptable to create a folder hierarchy on the client and mount the shares accordingly? You could write a dos batch file creating the hierarchy and mounting the shares and thus minimising user interaction.

---

### Post by beetlejuice321 on 2010-08-11
Well I think I know what your saying, but I am not sure it would be something I would want to use in a production environment.  

Also administration of Ubuntu Server is proving quite difficult. I know they have landscape but to me this is just Webmin (which is cool).  Whats really interesting to me is Webmin isn't even in the standard repositories.

I also found SME Server (based on CentOS) and EBox (based on Ubuntu).  Both are targeted at small businesses and offer great web based administration.  They also setup Samba and LDAP for you easily.  Something thats a pain with Ubuntu.  

In fact while I love Ubuntu for my desktop OS, I am finding the only thing Ubuntu Server is good for is a out of the box LAMP server for web hosting.  Its surprising to me there isn't more small business or targeted services Canonical is promoting.  I do have to say EBox looks really promising though.  

[http://wiki.contribs.org/Main_Page](http://wiki.contribs.org/Main_Page)
[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

---

### Post by Slim Backwater on 2010-08-11
I think you need to add ACL to the file system, as in ext3 acl by adding the "acl" option to the filesystem mount options.

This describes what I'm talking about:
[http://tlug.dnho.net/node/171](http://tlug.dnho.net/node/171)

Hope that helps.

---

### Post by beetlejuice321 on 2010-08-11
Hmmm, thanks for the link Slim, I will have to look further into the ACL's. From what I have read Windows ACL have to be translated to Unix permissions.

But yeah according to the Samba documentation it is possible.  I am not sure, perhaps you have to enable the domain and enable ACL in the share within Samba as well in order for things to work.  

As I mentioned before users with administrative access should have a way to modify file access, as it mentions here (and I quoted above).

**Modifying File or Directory Permissions**
[http://www.samba.org/samba/docs/man/...html#id2614541](http://www.samba.org/samba/docs/man/...html#id2614541)

The only thing is I am have a tough time finding any online instructions on this.  Finding tutorials on creating Samba shares, implementing a domain, or even LDAP is everywhere...but almost nothing on how an administrator can change directory/file permissions easily.

As I said, I know you can just change the Unix permissions.  But doing this is almost impossible without either a terminal connection, or remote connection via VNC.  The terminal is what I am trying to create an alternative to for the user.  VNC or other remote tool to the desktop would be fine!  But these can be difficult to run and leave to much room for users to encounter errors.

What I would really like is a web-based file browser for the OS.  To my knowledge Webmin and other Linux web administration tools do not have this (other then website admin tools).  Is this correct?  Or is there a tool that can perform these tasks?

---

