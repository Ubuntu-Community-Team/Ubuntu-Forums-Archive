---
title: "FTP user and SSH user"
date: 2005-08-08
forum: Server Platforms
---

### Post by cazz on 2005-08-08
Hi
I have install a SSH server and FTP (vsftpd) on my Ubuntu that that works excellent.

At first I have a SSH server and use WinSCP but I discover that a user can go outside the home folder and that is not so good.

Then I read a thread here that I just have to install vsftpd.
I did and change in the config file.

Now if the user use FTP he only can be in the home folder but he can still use SSH and go outside the home folder.

How can I fix that so some FTP user can't use SSH to login?

Or is that any easy way to fix that SSH can't go outside the homefolder
(I have read about chroot and that but that make me ????)

---

### Post by PeP on 2005-08-08
[QUOTE=cazz]Hi
I have install a SSH server and FTP (vsftpd) on my Ubuntu that that works excellent.

At first I have a SSH server and use WinSCP but I discover that a user can go outside the home folder and that is not so good.

Then I read a thread here that I just have to install vsftpd.
I did and change in the config file.

Now if the user use FTP he only can be in the home folder but he can still use SSH and go outside the home folder.

How can I fix that so some FTP user can't use SSH to login?

Or is that any easy way to fix that SSH can't go outside the homefolder
(I have read about chroot and that but that make me ????)[/QUOTE]

to prevent ssh users to go outside their home folder chroot them.

to some user to log-in (ssh and anything else than ftp) just change their default shell to /dev/null (this prevent them from running anything on your machine, launch a local a remote session ..., but they can authenticate through your ftp server running with its own  user id)

to prevent some user to login with ssh: 
from the sshd_config man page:

> 	
	

DenyGroups
This keyword can be followed by a list of group name patterns, separated by spaces. Login is disallowed for users whose primary group or supplementary group list matches one of the patterns. and ? can be used as wildcards in the patterns. Only group names are valid; a numerical group ID is not recognized. By default, login is allowed for all 

DenyUsers
This keyword can be followed by a list of user name patterns, separated by spaces. Login is disallowed for user names that match one of the patterns. and ? can be used as wildcards in the patterns. Only user names are valid; a numerical user ID is not rec- ognized. By default, login is allowed for all users. If the pattern takes the form USER@HOST then USER and HOST are separately checked, restricting logins to particular users from particular 

to prevent toto titi and tata from using their account by ssh add a line like
DenyUsers toto titi tata
or 
DenyGroups nossh
in /etc/ssh/sshd_config
(% sudo gedit   /etc/ssh/sshd_config)
if you choose the second one, then you just add the users to the nossh group like this:
% sudo adduser titi nossh
% sudo adduser tata nossh
% sudo adduser toto nossh


Warning: the percent ('%') symbol means you should type the following characters in a terminal, don't type it.

---

### Post by cazz on 2005-08-08
Hmmm that is no "DenyUsers" or "DenyGroups" in ssh_config file

I write exampel "DenyUsers person1" in the ssh_config and save it
But then the say "Bad configuration option".

I even try "DenyGroups nossh" same result.


One more question, is vsftpd secure FTP server or do I need something more like SSL or something?


Now I have read on another thread that I can use vsftpd so I don't need chroot.
But I dont now if that works or not.

---

### Post by PeP on 2005-08-08
Not being yet on the config files doesn't mean you can' use it.

I am quite surprised it doesn't work, it is on the man page so it should work, does the person1 user and nossh group exists ?

--> Added this line at the end of /etc/ssh/sshd_config and restarted ssh, it works fine:
DenyUsers toto


vsftpd *can* use ssl encryption and *requires* it if you configure it accordingly. The real drawback is that few ftp clients handle it.

---

### Post by cazz on 2005-08-08
Ahh I did a wrong restart of the SSH server, sorry for that.

but the "person1" can still login whit Putty and WinSCP.

Maybe is that problem is I create user in "Users and Group" in administation in Gnome?

I add in ssh_config at the last line

DenyUsers person1


Very very strange

---

### Post by PeP on 2005-08-08
[QUOTE=cazz]Ahh I did a wrong restart of the SSH server, sorry for that.
[/QUOTE]
sudo /etc/init.d/ssh restart ?
> 
but the "person1" can still login whit Putty and WinSCP.

you might want try to assign person1 to the /dev/null shell
> 
Maybe is that problem is I create user in "Users and Group" in administation in Gnome?

I don't think so
> 
Very very strange

yes it works for me.

---

### Post by cazz on 2005-08-08
[QUOTE=PeP]
sudo /etc/init.d/ssh restart ?
[/QUOTE]
Yes  :) 


[QUOTE=PeP]you might want try to assign person1 to the /dev/null shell
[/QUOTE]

Hmm how?
Never done that before  :?

---

### Post by PeP on 2005-08-08
[QUOTE=cazz]Yes  :) 




Hmm how?
Never done that before  :?[/QUOTE]
my mistake it's the /bin/false shell
sudo gedit /etc/passwd 
change the /bin/bash to /bin/false in the line containing person1,
you might also be able to do it with the gnome/kde gui

---

### Post by cazz on 2005-08-08
Thanks I found that in the GUI :D

And now that works so thanks you so much

---

### Post by PeP on 2005-08-08
[QUOTE=cazz]ok but what I have read that NEVER edit passwd in editor.
That can make that I never can login anymore even root I can't.  :? 

But if that is the only way then I going to do that  :?[/QUOTE]

you're right, look first if the gui can do that for you. If not just take the time to learn (man/google) what is this file about and how to tweak it.

DISCLAIMER: do it at your own risks blabla :-)

---

