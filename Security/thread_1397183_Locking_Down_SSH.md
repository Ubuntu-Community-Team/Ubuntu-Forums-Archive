---
title: "Locking Down SSH"
date: 2010-02-03
forum: Security
---

### Post by maxpol on 2010-02-03
Hi all,

I have an Ubuntu Server running on a Dell Dimension 1100. This is my personal file server aswell as an ssh server. 

I have a couple of friends that use it as an ssh tunnel to bypass a firewall. I want to be able to have an ssh_only group and add users that could only be locked to their home folder and couldnt do sudo or view any folders on the harddrive. Ive heard of a locked shell but I wasnt able to find anything.

Thanks for the help :)

---

### Post by Lars Noodén on 2010-02-03
> **maxpol said:**
> I want to be able to have an ssh_only group and add users that could only be locked to their home folder and couldnt do sudo or view any folders on the harddrive. 

You can chroot those accounts.  openssh-server does this very easily.  

If you make a group **friends** and add your friends to it, then the following addition to sshd_config should limit their access to only sftp and only within their own home directory.

```

Subsystem sftp internal-sftp

Match Group friends
	ChrootDirectory **%h**
	AllowTCPForwarding no
	X11Forwarding 
	ForceCommand internal-sftp

```

---

### Post by xamox on 2010-02-03
Actually there are a few things to fix in the code. You need the forwarding on to allow you to use it as a proxy like tunnel. Say you wanted your friends to bounce off your machine out to the net. Also you need to add a yes or no to X11Forwarding so the code should be.


```

Subsystem sftp internal-sftp

Match Group friends
	ChrootDirectory **%h**
	AllowTCPForwarding yes
	X11Forwarding no
	ForceCommand internal-sftp

```

---

### Post by bodhi.zazen on 2010-02-03
You can not completely restrict access to their home directories because they will need access to system files.

If all they are doing is tunneling, use keys and forced commands.

You could use apparmor to restrict their access to a bare minimum. I do this with "jailbash"

```
sudo ln /bin/bash /usr/local/bin/jailbash
```

Then use or modify this profile :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.local.bin.jailbash](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.local.bin.jailbash)

then use the chsh command to change the shell to /use/local/bin/jailbash

I use that profile to lock down the guest accounts as well, so you may wish to restrict access to X for example.

Other options would be to use LXC (it is easy to break out of a chroot or rbash unless you are very very careful). Linux containers would require a lot of effort on your part, more then apparmor.

---

### Post by maxpol on 2010-02-03
> **bodhi.zazen said:**
> 
Then use or modify this profile :
[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.local.bin.jailbash](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.local.bin.jailbash)


How would I use this profile? When I pico the jailbash file, its all symbols.

---

### Post by bodhi.zazen on 2010-02-03
You will need to read a bit on how to use apparmor.

Save that file, then as root copy it to /etc/apparmor.d/

then sudo aa-enforce jailbash

add /usr/local/bin/jailbash to /etc/shells

set the users log in shell to /usr/local/bin/jailbash with the chsh command

sudo chsh user -s /usr/local/bin/jailbash

---

