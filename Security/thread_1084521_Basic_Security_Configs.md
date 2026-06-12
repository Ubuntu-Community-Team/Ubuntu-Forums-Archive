---
title: "Basic Security Configs"
date: 2009-03-02
forum: Security
---

### Post by DnDer on 2009-03-02
Okay, working on a project for school, and I'm still in over my head. The notes on chkconfig were awesome (thanks, Andrew!), but I was hoping I could get the names of a few more processes to learn - just the names, I can google and learn from there. Unless you want to do my work for me, but I doubt it. 

I need to configure a Linux box to be more secure, out of the box. I'd prefer if I didn't have to use tools, but can do it all inside the OS with the tools as-is. Here were some of my ideas.

. . .

Changing root access.

Here's the deal I've learned with Windows. As an admin, you should ( a ) create an account with admin rights, ( b ) rename the Administrator account, ( c ) disable the Administrator account, and/or ( d ) delete the Administrator account. Oh, and never use the Administrator account, even after you rename it, unless you *have* to. Admins shouldn't be logging on as Administrator to do everyday normal stuff.

Now, as I understand it, "Root" operates in the same way. Since you can't delete Root, you need to remove people's ability to access it. What kinds of processes and command lines should I look for to make Root inaccessible to anyone but the system admin, like I would in Windows? (Command line is easier, I'm guessing, since that's going to be more universal than GUIs which vary from distro to distro, right?)

. . .

Change the workgroup. 

I'm not even sure Linux has this, but I'll take a stab and hope that there's something similar for decentralized networks (ie, 3 computers in a house that don't need a server or system admin), with a default setting to make it easier. It's something as simple as changing the name on this setting, but I'm not entirely sure where this might be to change.

. . .

Disable Guest access.

Guest accounts are bad. I'm also learning Windows has the ability to create "null sessions" (something covered more next class session) that allow anonymous logins to workstations from across the net, and I think they use the Guest account on Windows. Unless I've gotten it all confused. Is this process going to be the same as removing Root access? Or because it's an actual account, you can just delete it and create user-specific accounts (or a guest account with permissions and groups you set, instead of a default guest account)?

. . .

I'm just trying to think of some really basic things you do to secure Windows from inside Windows without downloading anything. I'd like to translate those parallels to Linux machines, for my project. Can you point me in the right direction to go and research? I don't know enough to know where to start. Not from a CLI, anyway.

(If any of the rules and tricks you can tell me about here can be executed with other distros, let me know, so I can go hunting in the right places for those, too,please.)

---

### Post by cdenley on 2009-03-02
> **DnDer said:**
> 
Changing root access.

The default ubuntu setup should be sufficient. Anyone in the admin group can elevate their privileges to root when needed. The user you created during installation is the only member of the admin group. You cannot login as the root account because it does not have a valid password.

> **DnDer said:**
> 
Change the workgroup.

This is specific to windows file sharing. If you installed samba, you can change the workgroup by editing /etc/samba/smb.conf, but I don't think there would be any  real security benefits.

> **DnDer said:**
> 
Disable Guest access.

Ubuntu does not allow any guest access by default.

Ubuntu isn't windows. It is basically secure by default. There are no steps all users should follow to secure ubuntu out-of-the-box. If you want to know steps you can take to make ubuntu even more secure, you should read the sticky.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bodhi.zazen on 2009-03-02
I will give you a link :

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

But really we do not support homework here , so I am going to close this thread now.

---

