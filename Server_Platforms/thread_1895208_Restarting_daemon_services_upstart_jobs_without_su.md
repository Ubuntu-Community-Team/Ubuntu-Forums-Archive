---
title: "Restarting daemon services upstart jobs without sudo password"
date: 2011-12-14
forum: Server Platforms
---

### Post by sirsiwsh on 2011-12-14
Afternoon all,

Possibly an odd question but it's one that's annoying me. Briefly, I am trying to write a script that will restart a given service daemon (upstart job) without the need for a sudo password.

The best method for the way I'd like to implement seems to be using /etc/sudoers:

Cmnd_Alias MTRESTART=/etc/init.d/mediatomb restart
Cmnd_Alias APRESTART=/etc/init.d/apache2 restart
[some user] ALL=(root) NOPASSWD: MTRESTART, APRESTART

However I am asked for the password when I issue: [some user]$ sudo MTRESTART
Issued without sudo (i.e: [some user]$ /etc/init.d/mediatomb restart), stdout kicks up a load of errors:

 * Restarting upnp media server mediatomb   
 start-stop-daemon: warning: failed to kill 14857: Operation not permitted
rm: cannot remove `/var/run/mediatomb.pid': Permission denied
touch: cannot touch `/var/run/mediatomb.pid': Permission denied
chown: changing ownership of `/var/run/mediatomb.pid': Operation not permitted
touch: cannot touch `/var/log/mediatomb.log': Permission denied
chown: changing ownership of `/var/log/mediatomb.log': Operation not permitted
Could not open log file /var/log/mediatomb.log : Permission denied

Theoretically I'd only have to allow these commands (e.g /usr/bin/touch) within /etc/sudoers, which works perfectly for e.g: /bin/rm. 

Does anyone know any way to find out which other commands the init script (mediatomb default for the commands issued) runs so they can be allowed? 
-or-
Is this a subshell problem (i.e. each binary is executed in a lower priviliged subshell which does not have the required permissions so asks for sudo authentication)
-or-
Does anyone know a quick and easy setuid/any other method that will allow the restart of daemons programatically? I'd prefer to use the top method, mostly becuase it doesn't require storing of a password in a text file and seems nicely secure- (i.e. restarting a daemon still requires root permission and therefore sudo/su password- but [some user] can bypass the authentication requirement for this particular command).

I've searched for a while now... any pointers in the right direction would be much appreciated! Thanks!

---

