---
title: "Ubuntu Server Subversion password encryption issues"
date: 2011-06-09
forum: Server Platforms
---

### Post by salientdigital on 2011-06-09
Like many others who have gotten Subversion working great on Ubuntu server, I just now realized I can't store passwords encrypted anymore when remoting in via SSH. I'm new to Ubuntu server. 

I've read [tons of posts on this problem]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ubuntu+svn+password+encrypted") but I'm not sure on which to try, or if any will work on the latest Ubuntu Server (no GUI).

The problem I am having is more specific than others. I am using SSH to connect to an Ubuntu server running svn. I set up svn with dav and everything works great. My IDE is storing my password, so I don't experience the problem until I ssh to the box and run svn operations: ```
local> ssh -l username ubuntuserver
ubuntu>  svn checkout [http://localhost/svn/repo/trunk](http://localhost/svn/repo/trunk) proj
ubuntu> cd proj
ubuntu> touch index.php
ubuntu> svn add index.php
ubuntu> svn commit -m "test commit"
ubuntu> authenticate: 
ATTENTION!  Your password for authentication realm:

   <http://localhost:80> Subversion Repository

can only be stored to disk unencrypted!  You are advised to configure
your system so that Subversion can store passwords encrypted, if
possible.  See the documentation for details.
```From what I've read, gnome-keyring or kwallet can be used, but aren't these GUI tools? My ubuntu server only has a command line interface. The passwords I need encrypted are the same svn passwords I created using ```
htpasswd -cm svn-auth-file username
```I managed to install gnome-keyring, and I uncommented the password-stores option in ~/.subversion/config however I am still prompted for my password every time, leading me to believe that my subversion wasn't compiled with the --with-gnome-keyring option. That said, should I recompile --with-gnome-keyring or is that only for desktop ubuntu?

Currently I have set ```
store-passwords no
``` and am entering my password every time but I don't think that will fly with the rest of my team. 

EDIT: 
I'm wondering now about [this solution]("http://www.unix.com/shell-programming-scripting/157714-subversion-gnome-keyring.html"). 

Thanks for advice.

---

