---
title: "xforward not working :-("
date: 2011-05-17
forum: Server Platforms
---

### Post by Percle on 2011-05-17
I'm the administrator of a small lab with a server (NIS and NFS) and several workstations.
Yesterday the very old server finally died. While we're waiting for a replacement, I was instructed to move the files of some users to one of the workstation, which runs Ubuntu 10.04 Server Edition

I changed the /etc/fstab to disable NFS, and I also modified /etc/nsswitch to disable NIS.

Because the workstation doesn't have any account, I manually created several accounts I was asked to rescue and then copied the backup files to this workstation.

After several chown commands, the users now can login to the workstation and access their files. However, xforward no longer works. I checked /etc/ssh/sshd_config and make sure xforward is enabled. I thought that might be caused by some old files such as .Xauthority, so I created a new account by using this command

               useradd -d /home/testuser -m testuser

 However, xforward still doesn't work for this new account.

I tried ssh -X, ssh -Y. none of them works

when I execute xclock, it shows:
Error: Can't open display: localhost:10.0
with no further debug information


when I do echo $DISPLAY it shows:
localhost:10.0


I've spent several hours searching online but so far I haven't found the solution yet.
Can somebody help me on this?

Thank you very much

---

### Post by GDR! on 2011-05-17
What is the hostname of the workstation? Maybe it's set to localhost and remote machine is confused?

---

### Post by Percle on 2011-05-17
When I do echo $HOSTNAME,
It shows the name of the computer, not localhost.
Is that the problem?

I tried export DISPLAY=*name_of_the_machine*:10.0
and when I ran xclock i got 
Error: Can't open display: *name_of_the_machine*:10.0

I also tried export DISPLAY=*ip_of_the_machine*:10.0
and I got
Error: Can't open display: *ip_of_the_machine*:10.0

---

### Post by hawkmage on 2011-05-17
With ssh -X you don't need to set the DISPLAY variable and it is normally localhost.  By default the local X display  is :0.0.  When you enable X tunneling it uses annother value nased on the X11DisplayOffset in the sshd_conf setting.  

On the local system at a command prompt what do you get is you run xclock?  

Once you ssh into the remote system what do you get if you run the command "xauth list"

Are you making a ssh connection directly to the account you are testing from or are you doing "sudo su - username"?  If so the .Xauthority will not have the correct info to work.

---

### Post by Percle on 2011-05-17
x clock launches normally on my local ubuntu system (desktop at home)

xauth list of the remote system is

*hostname*/unix:14  MIT-MAGIC-COOKIE-1  5ae38ff4991d170a5dfa918e832077d5
*hostname*/unix:15  MIT-MAGIC-COOKIE-1  0dc0254e29c1bdbdceb1f4859a70a557
*hostname*/unix:10  MIT-MAGIC-COOKIE-1  efc0c9b866758984d8e704130edbe889
*hostname*/unix:12  MIT-MAGIC-COOKIE-1  fb05a04e57f7932963d44594c6f522b4

Yes i do ssh -X with an user account, not root.

---

