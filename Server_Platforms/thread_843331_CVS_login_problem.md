---
title: "CVS login problem"
date: 2008-06-28
forum: Server Platforms
---

### Post by elektro_komesar on 2008-06-28
I have problem with cvs on Ubuntu server. Here what I did:
1. I have installed cvs and cvsd (apt get install cvs (cvsd))
2. when cvsd instalation ask me for cvs repository, I entered /repo (second time I entered /path/to/repo) - anyway, this variable  is defined under /etc/inetd.conf file under Repos...so it can be changed
3. after that, cvsd-buildroot command.... sudo cvsd-buildroot /path/to/repo and then create actual repo directory: sudo mkdir /path/to/repo
4. initialize directory: sudo cvs -d /path/to/repo init
5. fix access rights: sudo chown -R cvsd:cvsd repo and create one user with password: sudo cvsd-passwd /path/to/repo +newuser
with some password.
6. change (uncomment) auth type: sudo nano /path/to/repo/CVSROOT/config -> uncomment SystemAuth=no line.
7.edit /etc/inetd.conf file:
cvspserver stream tcp nowait root /usr/bin/cvs cvs --allow-root=/path/to/repo server --------                                   first part /user/bin/cvs - path to cvs
8. edit RootJail file inside /etc/cvsd/cvsd.conf:
by default, RootJail file points to /var/lib/cvsd directory, so I have commented that line and add new one: RootJail /path/to
as I said before, at the end of this file is Repos line ..and there I enetred: Repos /repo - that variable is defined during installation of cvsd.
9.after that, I have restarted cvsd and inetd deamon:
sudo /etc/init.d/cvsd restart
sudo /etc/init.d/inetd restart

now, the problem:
when I try to login on local server, with: cvs -d :pserver:newuser@localhost:/repo login
after entering password, I receive error:/repo: no such repository
however, when I enter full path to repo:
cvs -d :pserver:cvsuser@localhost:/path/to/repo login
enter password
everything works fine.
Same thing using TortoiseCVS (cvs should allow remote connections)...just /cvs for Repository Folder wont work, but, full path work (remotely checkout modules - no problem).
Anybody have any idea what is going on?? I want just to enter /repo for repository directory, not full path. This is the only cvs repository on the server.
Installation on the default location is not an option (anyway, I don`t see how it will fix the problem)

---

