---
title: "Ssh &amp; sftp"
date: 2013-11-17
forum: Security
---

### Post by SchnappiJedi on 2013-11-17
Hi,

Does disabling SSH access also disable SFTP access? I believe it does but I wanted to make sure. Thanks.

---

### Post by TheFu on 2013-11-17
It depends. If you disable the ssh-server completely, then yes.
If you need anything more complex, the man page explains.
**man sshd_config**

Check out the "Match" section.  I have never done what you are trying, just providing leads here.

---

### Post by SchnappiJedi on 2013-11-17
> **TheFu said:**
> It depends. If you disable the ssh-server completely, then yes.
If you need anything more complex, the man page explains.
**man sshd_config**

Check out the "Match" section.  I have never done what you are trying, just providing leads here.

Good point that it depends, let me clarify, does limiting SSH access using "AllowUsers" in the sshd_config file also limit SFTP access to only users that are listed?

---

### Post by Lars Noodén on 2013-11-17
AllowUsers and AllowGroups will also affect subsystems like SFTP.

---

### Post by Lars Noodén on 2013-11-17
If you have physical access to the machine so you are not worried about getting locked out, you can experiment.  Make a backup copy of sshd_config first and then make whatever changes you want to test.  If you stop the server you can then run it in debug mode which will be good for one session.

```

sudo service ssh stop
/usr/sbin/sshd -d

```  

That second line will allow one SSH sesssion and output what the server has to say about it to the screen.  It can  be very usefu.

Then to try another login session, run "sshd -d" again.

To restore normal operations of the ssh server, restore the configuration file from backup and then run "sudo service ssh start"

---

### Post by SchnappiJedi on 2013-11-17
Thanks to both of you.

---

### Post by clearski on 2013-11-17
Disabling the sftp subsystem denied sftp access to anyone in my test:

In /etc/ssh/sshd_config:

```
#Subsystem sftp /usr/lib/openssh/sftp-server
```

Restart sshd:

```
sudo service ssh restart 
```

Try a sftp connection:

```
sftp host
```

Debug code after successful authentication:

```
debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 100 id 0
subsystem request failed on channel 0
Couldn't read packet: Connection reset by peer

```

Then you could place a *Match* term at the end of the file allowing certain users (like the mighty yourself :)) sftp access.

Some people say that sftp and scp should also be removed from the system, but I haven't tried that.

---

