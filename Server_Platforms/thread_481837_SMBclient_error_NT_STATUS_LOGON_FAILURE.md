---
title: "SMBclient error: NT_STATUS_LOGON_FAILURE"
date: 2007-06-22
forum: Server Platforms
---

### Post by nick1 on 2007-06-22
Greetings,

I'm trying to transfer a file on my LAN from a WindowsXP SP2 computer to a Ubuntu 6.06 computer by using the following command:

smbclient -U MyUserName -W workgroup //192.168.1.105//c$

I am prompted for the password for the Windows account.
After entering the correct password, I receive the following error:

NT_STATUS_LOGON_FAILURE

About the Windows computer:
-The credentials I am using are for an account on the Windows computer.
-I am sure I am entering the correct credentials.
-Disabling the Windows firewall did not help.
-The Windows computer does infact belong to the workgroup called workgroup.
-The c$ share does exist.

About the Ubuntu computer:
-Ubuntu 6.06.1LTS Server, no GUI.
-The Ubuntu computer is not using a firewall either.
-I installed the smbclient package, nothing else.

I have searched google and the Ubuntu forums and have not yet found a solution to this problem.  Any suggestions?

Thanks,

---

### Post by dmizer on 2007-06-23
you're trying to mount your root drive on windows.

what's the output of smbtree ... take a look and see what you can mount.

also, try installing smbfs:
```
sudo aptitude install smbfs
```

you will likely have better performance if you make use of cifs instead of smbclient.  if you're interested, check the second link in my sig.

---

