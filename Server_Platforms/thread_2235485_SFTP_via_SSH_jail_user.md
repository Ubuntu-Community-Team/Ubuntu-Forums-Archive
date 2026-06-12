---
title: "SFTP via SSH jail user"
date: 2014-07-21
forum: Server Platforms
---

### Post by aris3 on 2014-07-21
Hey guys,


I'm in need of some help on SFTP via SSH. I hope one of you can give me a push in the right direction.


This is what i'm trying:
I have a box running Ubuntu Server, and a Windows client. I want to read-only share a directory from the server to the client.

What is have so far: Windows client can connect to the server with WINSCP through SSH. I have created a symbolic link in the Home directory of the user that logs in with WINSCP. 

What I'd like: I want the Windows client to start in the symbolic link directory, so users cannot see the files/folders in the home directory. I also want to "jail" them so they cannot navigate to other places than the symlink folder. 

with chrooting in the sshd_config file I can only seem manage to land the user in the home folder.

Any tips/ alternative ways or hints are appreciated. 

Thanks in advance!



Aris

---

### Post by thnewguy on 2014-07-21
Why not create a separate home directory for the users who will connect from Windows. That way you don't need to adjust the chroot or create symbolic links?

---

### Post by aris3 on 2014-07-21
Hey thnewguy, thanks for your reply :)


I'm feeling kinda n00bish now, I'm not really sure if I understand;


- Add a new user (useradd)
- Move the user's  directory away from ~/ (u[COLOR=#000000][FONT=Consolas]sermod -d /path/to/new/home -m *username*)

Is this what you are suggesting? 

Thanks again :)

Aris[/FONT][/COLOR]

---

### Post by TheFu on 2014-07-22
Yes - a home directory can be anywhere and the useraccount accessing it doesn't NEED to have write access at all.  Just change the HOME in the /etc/passwd file.

However, for a chroot to work, which is what you want, you'll need a minimal /etc/passwd and a few other files ... so the user can login.  Google "chroot sftp ubuntu" to find step-by-step instructions.  Don't forget to prevent ssh and scp connections for the specific users too if all you want to allow is sftp.  If the ubuntu-specific instructions aren't clear, remove that. There is NOTHING special about Ubuntu in this aspect.

I don't think a softlink outside the jail will work either. If it does, that is a security hole, IMHO.

I haven't done this recently, so don't have the steps memorized. Sorry.

---

