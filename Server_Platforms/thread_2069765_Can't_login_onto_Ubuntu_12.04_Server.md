---
title: "Can't login onto Ubuntu 12.04 Server"
date: 2012-10-11
forum: Server Platforms
---

### Post by thomasdilts on 2012-10-11
I can't login into my server. The symptom is like this: On the terminal screen at the Username prompt, I enter my username and password. If I enter a correct combination the screen is cleared and the login prompt shows up again. If I enter a bad combination then I get the normal error message. Nothing is in the logs, neither syslog nor auth.log. If I try ssh then when I enter a good login combination I get disconnected immediately. One more strange thing; when I go in with "recover" as root, and try passwd, it does not work or give any response or loggings.
 
Everthing else works on the server thank goodness. 
 
What caused this was I tried to install a very advanced functionality (winbind,samba4 included in [OpenChange]("http://www.sogo.nu/files/docs/SOGo%20Native%20Microsoft%20Outlook%20Configuration.pdf")) and it stopped my LDAP from working so I had to remove all winbind and samba from the server Before LDAP started working again.
 
Tried solutions:
 
1. Since there is no graphical interface this is not an X11 problem. 
2. sudo apt-get --reinstall passwd 
3. checked all rights on bin/passwd, etc/passwd, shadow and nsswitch.conf.
 
I am really stumped. Does anybody have a clue?

---

### Post by spynappels on 2012-10-12
I presume that, as you can check the logs etc., this happens when one user logs in but not necessarily for all users?

You might check what shell this user who experiences the problems has as default, they may be logging in but if there is no default shell, they won't get very far.

---

### Post by Alekz_ on 2012-10-16
Can't you login with ANY user? How could you see log messages? And run apt-get?

---

