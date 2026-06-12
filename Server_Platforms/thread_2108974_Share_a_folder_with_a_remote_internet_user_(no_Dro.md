---
title: "Share a folder with a remote internet user (no Dropbox or similar)"
date: 2013-01-26
forum: Server Platforms
---

### Post by daxnet on 2013-01-26
Dear all,

I have Ubuntu 12.04 64 bits runing on a Desktop PC which I'm using as a data server for an external aplication runinng on several windows based laptop.


In Ubuntu I've a folder where I store huge amounts of data and a simple script to process those data. The remote aplication access the Ubuntu computer through the LAN, executes the script, and takes the data it needs. Until now everything is runing fine. The data folder in Ubuntu is just a shared folder with universal access that can be reached from any PC conected to the LAN.

So, it happens that now I have to give access to this folder to users which are outside the LAN. My first aproach was to look to a cloud based storage solution (Ubuntu 1, Dropbox...) but this is unfeasible due to the fact that 1)I need lots of GB of space 2) I need to remotely execute the script on my local Linux machine.

So, I've reached to the conclusion that I have to somehow allow that a remote user could have full access to an specific folder on my local machine. So my simple question is:

What would be the best (and easiest) aproach to share a folder on my local PC with a remote internet user? (no dropbox or similar please...)

Thanks a lot!

---

### Post by sudodus on 2013-01-26
Welcome to the Ubuntu Forums :-)

I suggest ***SSH*** (and ***SFTP***) with public key authentication (no password authentication because it is not safe enough on the internet). You should get a static IP address. See for example

[[COLOR="Red"]https://www.opendns.com/opendns-ip-addresses[/COLOR]]("https://www.opendns.com/opendns-ip-addresses")

And you need to activate your firewall and to change the ssh port from the default 22 to something very different.

[[COLOR="red"]https://help.ubuntu.com/10.04/serverguide/openssh-server.html[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")

[[COLOR="red"]https://wiki.ubuntu.com/BasicSecurity[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by SeijiSensei on 2013-01-26
What OS will the remote user(s) be running?  How savvy are they?

One approach you might consider is using [webdav]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") with authentication.  For more security you can run it over SSL.  The remote user can then define a desktop folder that points to the DAV share.  It will act like any other shared folder.  Both Windows and Linux clients support this.  OS X probably does, too, but I've never used a Mac.

---

### Post by Habitual on 2013-01-27
> **daxnet said:**
> What would be the best (and easiest) aproach to share a folder on my local PC with a remote internet user? (no dropbox or similar please...)

Thanks a lot!

```
python -m SimpleHTTPServer
``` in the folder to be shared will serve up at 
http://$HOSTNAME:8000/

the "remote" part may be tricky. 
Sorry, I power posted. :(

---

