---
title: "Can See Samba FileServer Cannot Access Shares"
date: 2010-06-27
forum: Server Platforms
---

### Post by UncleAelfrich on 2010-06-27
I recently upgraded my ubuntu samba fileserver to 10.04 along with increasing the size of my RAID 1 /home directory.

I am using the same smb.conf file setup I have used on intrepid ibis setup and hardy heron setup before that.

On my new setup, I can see the ubuntu server on my windows 7 machines, but I can't see the shares and can't access them.

In checking the logs (/var/log/samba), one log continues to look for a printer share from one Windows machine that I have not set up on samba yet. Another log for a client machine has these messages:

> stat of /var/lib/samba/usershares/lxxxxxan failed. No such file or directory.

*and*

> couldn't find service lxxxxxan

*and*

> getpeername failed. Error was Transport endpoint is not connected

the /var/log/samba/log.winbindd-idmap has the following errors

> Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration

*and*

> idmap initialization returned NT_STATUS_UNSUCCESSFUL

My smb.conf has security set to 

  > security = user

I have found a few people who have reported similar problems online, even a few who have filed bugs, but then they say "my computer started working suddenly. I don't know what happened." so they closed the bug. or "my computer started working after I rebooted my machine." I have rebooted all machines on the network. That doesn't fix it.

I would appreciate any knowledgeable help.

---

### Post by UncleAelfrich on 2010-06-28
I can't believe I'm such an idiot. In the example smb.conf file, it says to uncomment the following:

> ;[homes]
    comment - Home Directories
    browseable = no

so, looking at the comment and browseable lines, and not seeing a semi-colon, I moved on.

After SEVERAL hours, I happened to notice that pesky little 

;

on the first line there.

I took it out, and all problems solved.

I don't know whether to feel good that the system works now, or to feel bad that I spent HOURS over a stupid semi-colon.

---

