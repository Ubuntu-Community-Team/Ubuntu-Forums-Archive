---
title: "umask for sftp(d)?"
date: 2020-04-04
forum: Security
---

### Post by mfleming on 2020-04-04
Hi,

When files are transferred to my server, I want them to have rw-rw-r-- permissions, ie as if they were created with a umask of 0002.  Instead they have rw-r--r-- permissions, ie as if they are created with a umask of 0022.  The umasks are set to 0002 in the users' .profile files. I understand that the .profile files are not read by the sftpd system. I've tried several of the fixes suggested online, but none seem to work. My /etc/ssh/sshd file had the line 

Subsystem       sftp    /usr/lib/openssh/sftp-server

which I changed to

Subsystem       sftp    /usr/lib/openssh/sftp-server  -u 0002

and then

Subsystem sftp internal-sftp -u 0002.

I also tried adding

Match Group labStaff
        ForceCommand internal-sftp -u 002

for the users who I want to have this umask. 

I also changed the default umask in /etc/login.defs to UMASK 002.

I also added the following to /etc/pam.d/login:

session optional pam_umask.so umask=0002

None of this worked, though it's possible that I just need to reboot the server. I restarted the ssh system after making the changes to /etc/ssh/sshd_config, but don't know how to have the /etc/login.defs or /etc/pam.d/login files reloaded without rebooting the server, which I can't do remotely. 

Your assistance would be greatly appreciated.

Matthew Fleming
Fleming Dermatopathology

---

