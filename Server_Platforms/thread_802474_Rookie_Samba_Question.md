---
title: "Rookie Samba Question"
date: 2008-05-21
forum: Server Platforms
---

### Post by TheGameAh on 2008-05-21
Hey guys.

Toying with the idea of moving a file share or two over to a Samba box integrated with AD, so that I can use existing users and groups, and manage the security through a  Windows Explorer window.

I have an existing file share on a Win 2003 box with multiple levels of security.  Example:  \\server\share

Under this share would be:

\\server\share\Engineering
\\server\share\Accounting

You get the idea.  Basically, public folders based on department.

However, under the above folders, there is a subfolder called Protected:

\\server\share\Engineering\Protected
\\server\share\Accounting\Protected


The entire share is open to everyone, with the exception of the corresponding Protected folders, which is only available to members of Accounting, Engineering, etc.

Is this kind of multi level security setup possible with Samba integrated in AD?

---

### Post by HermanAB on 2008-05-21
Probably yes.  AD integration is a very complex problem.  Read the Official Howto on the Samba web site and see my guide here: [http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

### Post by molotov00 on 2008-05-21
I don't know about AD, but I know another way this can be done. You can add Linux users to groups (such as Accounting, Engineering, etc). Tell Samba to provide access to the group folders. Then, you can create other Linux user groups such as AccountingProtected, add users to those groups, and only allow that group to access the subdirectories using Linux file permissions.

So, from Samba's point of view, Accounting has access to all of the accounting folder, BUT the Linux-level file permissions only allow AccountingPermitted group members into the lower Protected folder.

The management of this would be more difficult than AD, however. I only provide this alternative because it's how I would do it having no knowledge of AD (although a situation like this would prompt me to look into it...)

M

---

### Post by mdr on 2008-05-22
I use the method that molotov outlines above.  Works for me.
However I would just have all directories accessed by all "Users" and the Protected areas by a group such as "Accounts" etc.

---

