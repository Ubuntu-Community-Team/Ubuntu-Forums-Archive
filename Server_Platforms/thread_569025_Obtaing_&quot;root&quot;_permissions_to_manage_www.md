---
title: "Obtaing &quot;root&quot; permissions to manage www services"
date: 2007-10-06
forum: Server Platforms
---

### Post by Wo0t wo0T on 2007-10-06
Hello all, new to ubuntu linux and need some quick pointers.

I am setting up a web dev enviroment on ubuntu and am having issues when trying to create/edit folder due to insufficient permissions. I've tried logging in a as "root", but so far am unable to to. Can I log into the GUI under root?

I need to create individual dev enviroments in the www folder, but can even create a foilder!  I'm sure its simple, but I'm so new to linux. Love Ubuntu btw, rocks!

Any advice?

---

### Post by netlogic on 2007-10-06
i didn't understand your question, but are you asking how to launch the file manager in gnome as root?
[B][I]
gksu nautilus[/I][/B]

---

### Post by Wo0t wo0T on 2007-10-06
Sorry for not being clear. My question was really 2 parts.

1. Is there a way to log in as root? I've tried with no luck.

2. While logged in as the default user, I am unable to create/manage files due to permissions. How can I manage "protected" files/folders while logged in as a normal user?

Hope i'm a little clearer this time, I am really new to linux so I am unfamiliar with it. 

Thanks for the fast response.

---

### Post by netlogic on 2007-10-06
login in as root is a HUGE security risk. That is why Windows os until Vista had huge malware and virus issues. Linux mostly doesn't have that issue, but you want to avoid anyone trying to remotely exec applications as a root user.

type** gksu nautilus** to launch the file manager with a root privilege

---

### Post by Wo0t wo0T on 2007-10-06
Completely understand why NOT to log in as root. Thanks for the command.... might be useful  : P

I got the following error when executing the  command:

xxxxx@xxxx-desktop:~$ gksu nautilus

(nautilus:12926): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:12926): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

I dont think this is normal. This is a fresh install of Ubuntu 6.10 edgy. 

Although I got this error message naultilis DID open and I can manage folders. (Thanks!)

---

### Post by Buffalo Soldier on 2007-10-06
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

