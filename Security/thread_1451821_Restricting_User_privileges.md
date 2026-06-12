---
title: "Restricting User privileges"
date: 2010-04-11
forum: Security
---

### Post by AntoniusUno on 2010-04-11
Hi,

I have searched somewhat this forum but haven't yet found a similar post using the keywords I entered but perhaps there is already a similar post then please refer me to it.

I am trying to add a user account "Guest" to allow people on my laptop without giving them access to vital parts of the computer. Basically, I want them to only be able to view their own home directory and access internet. Nothing more.

I have set the group to "guest" and changed the other home directories of other users to owner access only. 

Guest still has access to root and is still allowed to perform actions in various critical areas (deleting files from for example my Windows 7 partition). This I also want to prevent. 
I was thinking to set each directory's permissions to Owner and Group only and remove Others access.

My questions:

1. Will this have any undesirable impact (programs of main user accounts not able to access certain directories)? For guest user I don't care as long as internet works.
2. When I start User Manager and disable for Guest all options except "access internet" (so I also disable access to CDROM), the guest can still access the CDROM. Does this mean the User Settings menu has no effect or is overruled by something?

thanks for any help offered.

---

### Post by HermanAB on 2010-04-11
Howdy,

You can provide  fine grained access control using sudo and the /etc/sudoers file.  Just read the file - there are lots of examples in it.

---

### Post by AntoniusUno on 2010-04-11
I have read the /etc/sudoers file but not much info in there for me on above given topic. I don't want to fix this with sudo permissions because the people having guest access to this laptop will not have a clue about sudo. I just want to prevent them deleting or modifying files which is possible by clicking on Places and start browsing.

---

### Post by HermanAB on 2010-04-11
The users don't have to have a clue about sudo.  Sudo is a general purpose method to provide fine grained access control.  

The sudo CLI command that you are thinking of is only one part of the puzzle and it is the part that the users do not need to know about!

In the sudoers file, you can define which users, or which groups of users are allowed to do what.  If you want a group of users to be able to run only one program, such as for example firefox and absolutely nothing else, then you can set sudoers up that way with a single line for that group.

Sooooo, Google and read up on sudo.

---

### Post by AntoniusUno on 2010-04-11
ok I will read into sudo as I don't want to be stubborn. However, can you answer me why the user permission settings don't restrict the GUEST account from accessing CDROM even though I unchecked the box "access to CDROM"?

---

### Post by bodhi.zazen on 2010-04-11
> **AntoniusUno said:**
> ok I will read into sudo as I don't want to be stubborn. However, can you answer me why the user permission settings don't restrict the GUEST account from accessing CDROM even though I unchecked the box "access to CDROM"?

I do not know why, I suggest you file a bug report :twisted;

If you wish to restrict the guest or any other account you will need to look at apparmor.

Personally I restrict the guest account with apparmor and it would be a trivial to restrict access with apparmor (assuming you understand apparmor).

---

### Post by Agent ME on 2010-04-11
> **HermanAB said:**
> You can provide  fine grained access control using sudo and the /etc/sudoers file.  Just read the file - there are lots of examples in it.
The sudoers file only restricts the use of sudo. A guest account probably has no need to even touch sudo.

---

### Post by AntoniusUno on 2010-04-13
> **Agent ME said:**
> The sudoers file only restricts the use of sudo. A guest account probably has no need to even touch sudo.

exactly my point. Thanks for understanding :)

---

### Post by lensman3 on 2010-04-13
Look at the restricted shell logins.  "rlogin" is an example.  The restricted shells will restrict  you to a directory.  The "chroot" system call is or can be used to restrict the top directory.

In some shells you will have to create a subset of /usr/bin and the administrator will have to supply exactly the programs/scripts that will be accessible (usually more trouble than it is worth).

Hope this helps.

---

### Post by bodhi.zazen on 2010-04-13
> **lensman3 said:**
> Look at the restricted shell logins.  "rlogin" is an example.  The restricted shells will restrict  you to a directory.  The "chroot" system call is or can be used to restrict the top directory.

In some shells you will have to create a subset of /usr/bin and the administrator will have to supply exactly the programs/scripts that will be accessible (usually more trouble than it is worth).

Hope this helps.

Restricted shells are often trivial to break out of. Use apparmor.

---

