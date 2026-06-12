---
title: "[ autofs5 ] Issues automounting Samba shares and sshfs connections."
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by martincigorraga on 2014-03-30
Well, for the ones who could happen  to know about autofs5, it's giving me a hard time on Ubuntu, here's a  brief description of what I want to achieve, what I did so far -  including all the config files - and the error logs I got from  automount:
 
*** What I want to achieve

I want to mount on the fly:
/media/SERVERS/smb        a Samba share on my NAS on my local local network
/media/SERVERS/sshfs      an SSH connection on an AWS VPS.
 
1. Both {...}/smb and {...}/sshfs mountpoints are created by autofs5, by default /media/SERVERS/ is empty.
2.  I can successfully connect to each of the resources manually or using  Nautilus; in the case of Samba works with both the auto-discover feature  as well by manually entering smb://
 

*** What I did:
---- 1. put my maps into /etc/auto.master.d/

/etc/auto.master.d> ls
servers.autofs
/etc/auto.master.d> cat servers.autofs 
# Sample auto.master file
 # Format of this file:
# mountpoint map options
# For details of the format look at autofs(5).

# Samba shares
/media/SERVERS/smb /etc/autofs/auto.samba --timeout=60

# SSH mounts
/media/SERVERS/sshfs /etc/autofs/auto.sshfs --timeout=60
 

---- 2. Now, here are my mounts and shares:
/etc/auto.master.d> cd /etc/autofs/
/etc/autofs> ls
auto.misc  auto.samba  auto.sshfs  credentials.samba.olivetti
/etc/autofs> cat auto.samba
 # This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# Details may be found in the autofs(5) manpage

olivetti -fstype=cifs,rw,noperm,credentials=/etc/autofs/credentials.samba.olivetti ://[192.168.1.105/olivetti]("http://192.168.1.105/olivetti")
 

/etc/autofs> cat auto.sshfs

# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# Details may be found in the autofs(5) manpage
 
titsandbits -fstype=fuse,allow_other :sshfs\#[EMAIL="msx@titsandbits.com.ar"]msx@titsandbits.com.ar[/EMAIL]\:/

(FIY I already added my key to /root/.ssh/ and the server to the known_hosts file)

 


I expect now that:
- the directories /media/SERVERS/smb and /media/SERVERS/sshfs are created and their resources automatically mounted when I access them the first time.
What's actually happening:

- both directores (/media/SERVERS/smb and /media/SERVERS/sshfs) are there *but* they are also empty.
 


*** Debugging phase:

As suggested on Ubuntu's Wiki (here: [https://help.ubuntu.com/community/Autofs#Debugging_Auto_Mount_Problems](https://help.ubuntu.com/community/Autofs#Debugging_Auto_Mount_Problems)), this is the output of automount -f -v  - and following with -d flag added for extra debugging info: [http://pastebin.com/cegw7avx](http://pastebin.com/cegw7avx)




What I don't understand is why a similar setup on other non-Ubuntu/Debian systems works :S

Any help is much appreciated!


Regards.

---

