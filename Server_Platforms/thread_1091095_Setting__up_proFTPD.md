---
title: "Setting  up proFTPD?"
date: 2009-03-09
forum: Server Platforms
---

### Post by mahela007 on 2009-03-09
I am a real newbie when it comes to stuff like FTP and networking but I am also curios about making my own FTP server. How do I set up proFTPD on my kubuntu PC? 
I connect to the internet via a router. I haven't set up any firewalls or done any special configuration to kubuntu or the router. So Does being behind a router complicate things?

---

### Post by HermanAB on 2009-03-09
Proftpd and Vsftpd work out of the box.  People who complain about it not working typically went and changed the default settings.  So don't do that - not at first anyway.

You have to configure your firewall(s) to allow FTP through.

However, note that FTP is inherently insecure.  it would be best to NOT use it and rather install the ssh-server package.  You can connect to SSH using FileZilla from Windows and Linux.

Cheers,

Herman

---

### Post by mahela007 on 2009-03-09
I wont be sharing any highly important files so security won't be a real concern. What I need is something which is 'noob friendly'. Is FTP good in that aspect?

---

### Post by mahela007 on 2009-03-09
I tried following [This]("http://ubuntuforums.org/showthread.php?p=429783#post429783") thread to install proftp. I got a message asking me where proftpd should be installed on "standalone or inetd". What are these two terms? which one should I choose if I only want to do minimal file sharing with relatively small files?

---

### Post by firefly2442 on 2009-03-12
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ServerType.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ServerType.html)


> In inetd mode, the proftpd server expects to be started by the inetd (or xinetd) servers. It is these servers, inetd/xinetd, that listen on the FTP port (usually 21) for connection requests, then start proftpd and pass the connection off. This mode is usually best suited for low traffic sites, for sites that do not handle many FTP sessions. 

> Standalone: In this mode, the proftpd listens for incoming FTP session requests itself, and forks off child processes to handle those requests. This mode is best suited for high traffic, popular sites; the overhead of having to parse the configuration file each time, as is done for inetd-handled sessions, is avoided in this mode.


As it suggests, I would go with inetd if it's only going to be low usage.

---

