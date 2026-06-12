---
title: "Disable SFTP in SSH?"
date: 2010-09-03
forum: Security
---

### Post by Phoenix85 on 2010-09-03
Hi, I'm new to these forums, and I'm not sure if this is the right category for my questions, but it seemed the most right?

I've made an SSH server using OpenSSH on my desktop Ubuntu (10.4) for tunneling. However, I'm noticing that the public account I made for my SSH (one to give to friends to use proxy) has SFTP access to crucial system files. I'm okay with SFTP being enabled on my account, but not on this public account. Does anyone know of anyway to either disable SFTP to that user, or restrict access to important files?

Thanks!

Paul

---

### Post by scorp123 on 2010-09-03
Use ACL's maybe? And you could put the SSH server into a virtual machine? Read here:
[http://ubuntuforums.org/showpost.php?p=9793483&postcount=7](http://ubuntuforums.org/showpost.php?p=9793483&postcount=7)

---

### Post by Bachstelze on 2010-09-03
Just chroot the account, then it can't access your system files.

---

### Post by BkkBonanza on 2010-09-03
You could try using the ForceCommand option in the sshd_config and specify "/bin/sleep 30". I haven't tested it but that should force any ssh login to ignore user supplied commands and be forced to use sleep, which just waits. This allows proxying/tunneling but, from what I've read, if no activity happens in 30 seconds then the connection is closed.

If only for certain users/hosts then you would wnat to put it inside a Match block.

Add at end of file so that no other commands are after this block, eg.

Match User Fred
ForceCommand "/bin/sleep 30"

You could also use a script that has only certian functions or perhaps outputs a message and waits.

If you decide to use chroot then here is a tutorial, though it's a bit convoluted for my liking, and on recent Ubuntu I think the version is already present so you probably wouldn't want to build it from source, and may skip the install section.

[http://ubuntuforums.org/showthread.php?t=858475](http://ubuntuforums.org/showthread.php?t=858475)

---

### Post by bodhi.zazen on 2010-09-04
You can not restrict all access to all system files, you have to allow some access.

Your first line of defence is standard linux permissions.

If you need more then that, you will need either a chroot or aparmor.

See this post :

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

---

