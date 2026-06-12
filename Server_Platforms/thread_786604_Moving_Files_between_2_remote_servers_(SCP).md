---
title: "Moving Files between 2 remote servers (SCP?)"
date: 2008-05-08
forum: Server Platforms
---

### Post by phillips321 on 2008-05-08
Hi guys,

I have 2 remote servers sat locally on the same LAN as each other.

Both boxes are headless, ssh only, and neither have ftp, www, nfs or samba.

I need to move about 8Gb from one box onto the other, both can access each other via ssh, can i use scp to copy the files across?

I need to ensure the data is transfered perectly with no errors, it doesn't matter how long it takes.

Would any one know how to move this data?

I simply need to move from /home/user on box1 to /home/user on box2.

Cheers in advanmce

---

### Post by hyper_ch on 2008-05-08
I would use rsync over ssh.

---

### Post by HermanAB on 2008-05-08
You can open two windows in Konqueror or Nautilus, use sftp to connect to the two machines, then click-drag-drop files between them - super easy.

Don't try that with Windoze...

---

### Post by koenn on 2008-05-08
> **hyper_ch said:**
> I would use rsync over ssh.
Last time I checked, you can not rsync between 2 remote systems.

---

### Post by hyper_ch on 2008-05-08
sure you can... if you can't do it directly then you'll first build a ssh connection to one server and issue the command from there...

---

### Post by koenn on 2008-05-08
> **hyper_ch said:**
> sure you can... if you can't do it directly then you'll first build a ssh connection to one server and issue the command from there...
ah, OK, didn't quite understood that that is what you meant. 
You'd have to do it that way; "rsync remote01:/path/ remote02:/path" wouldn't work.

---

### Post by hyper_ch on 2008-05-08
it would actually be great if you could directly do:

rsync remote1:/org remote2:/dest

---

### Post by koenn on 2008-05-08
> **hyper_ch said:**
> it would actually be great if you could directly do:

rsync remote1:/org remote2:/dest

yeah. 
I think the problem is you'd need to authenticate from remote1 to remote2

something like "ssh remote01 rsync /src remote2:/dest"
might work if you've set up host-based or public key authentication

---

### Post by MartynA on 2008-05-08
I see no reason why scp wouldn't work.

scp -p user1@host1:/home/user1 user2@host2:/home/user2 

Or something similar anyway.

---

### Post by koenn on 2008-05-08
> **MartynA said:**
> I see no reason why scp wouldn't work.

scp -p user1@host1:/home/user1 user2@host2:/home/user2 

Or something similar anyway.

because host2 will request authentication from user1@host1 before creating a channel for scp, while scp is being run by user0@host0.

try it.

---

### Post by songshu on 2008-05-08
scp is perfect for the job and already installed

if you are logged in at host1 as user1 and want to copy to host2

scp /path/to/file user2@host2:/path/to/endlocation

if you want to copy from the remote location to your local machine

scp user2@host2:/path/to/file /path/to/endlocation

this would connect to the standard port 22

if you changed the port to 33 you need to specify that with using

scp -P 33 


> You can open two windows in Konqueror or Nautilus, use sftp to connect to the two machines, then click-drag-drop files between them - super easy.

Don't try that with Windoze...

don't try that on a server

---

### Post by songshu on 2008-05-08
> **hyper_ch said:**
> it would actually be great if you could directly do:

rsync remote1:/org remote2:/dest

you could actually (dont know the exact command from the top of my head), but its not really efficient since you would issue that command on local3.

the data would from remote1 to local3 and then to remote2
instead of directly from 1 to 2

---

### Post by eldragon on 2008-05-08
> **songshu said:**
> scp is perfect for the job and already installed

if you are logged in at host1 as user1 and want to copy to host2

scp /path/to/file user2@host2:/path/to/endlocation

if you want to copy from the remote location to your local machine

scp user2@host2:/path/to/file /path/to/endlocation

this would connect to the standard port 22

if you changed the port to 33 you need to specify that with using

scp -P 33 




don't try that on a server


what he said, is THE way to do it :D

---

### Post by koenn on 2008-05-09
> **songshu said:**
> you could actually (dont know the exact command from the top of my head), but its not really efficient since you would issue that command on local3.

the data would from remote1 to local3 and then to remote2
instead of directly from 1 to 2

man rsync
> GENERAL
       Rsync copies files either to or from a remote host, or locally  on  the
       current  host  (it  **does  not** support copying files between two remote
       hosts).


---

### Post by songshu on 2008-05-09
> **koenn said:**
> man rsync

you are right,

my bad ;)

rcp could, rsync doesn't

---

### Post by koenn on 2008-05-09
> **songshu said:**
> 
rcp could, rsync doesn't
the maybe scp could, as its specs were something along the lines of "same as rcp, but over a secure channel"

---

### Post by shane2peru on 2010-04-23
> **HermanAB said:**
> You can open two windows in Konqueror or Nautilus, use sftp to connect to the two machines, then click-drag-drop files between them - super easy.

Don't try that with Windoze...

Old thread I know, but that is a very very very slick trick!  Sure beats downloading all that to my computer then uploading it to the new server when changing web hosts!  Very awesome!

Shane   :popcorn:  :KS   :popcorn:

GOTTA LOVE LINUX!

---

### Post by Vegan on 2010-04-23
All of the servers I use are secure so as I use a Windows box, I simply map each remote and then via Windows drag and drop, its smart enough to build a route with SAMBA helping out.

---

