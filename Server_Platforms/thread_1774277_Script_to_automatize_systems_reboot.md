---
title: "Script to automatize systems reboot"
date: 2011-06-03
forum: Server Platforms
---

### Post by andriu1 on 2011-06-03
Hi guys,

I've been trying last days a script to reboot periodically my servers.

My idea is to execute the script from one machine, and remotelly, restart the other servers.

Now, I've configured ssh to access remote machine without password, using key-pair access, but I am not able to run "shutdown" command without password, so the script doesn't finish cause it waits for password to run shutdown with su priviledges

I've been reading about sudoers file, and applied this configuration on remote machine sudoers file.
```
....
# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown
...
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
myremoteuser myremotemachine= NOPASSWD: SHUTDOWN_CMDS
....
```I've been testing this configuration on remote machine, logged as myremoteuser, executing /sbin/shutdown -r now, but "shutdown: Need to be root" message is returned, so something seems to be wrong in my configuration but I don't know what.

Could you help me please?

Thank you very much for your time

Regards,
Andres

---

### Post by Lars Noodén on 2011-06-03
I've always gotten trouble from sudo's attempts to work with the machine name, so I would recommend trying this modification:
```

Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown
...
myremoteuser ALL= NOPASSWD: SHUTDOWN_CMDS

```


Alternately, you could just put the shutdown into a crontab for root.

```

sudo crontab -e

```

---

### Post by andriu1 on 2011-06-03
Hello Lars, first of all, thanks for your response. Well, I've tested like you propose but it doesn't work

This is the new line into sudoers

```
myremoteuser ALL= NOPASSWD: SHUTDOWN_CMDS
```

Regards

---

### Post by Lars Noodén on 2011-06-03
What happens when you log into the remote machine (the one with the modified /etc/sudoers) without the script and try running shutdown with sudo?

---

### Post by Lars Noodén on 2011-06-03
> **andriu1 said:**
> ...This is the new line into sudoers...

Which machine is it on?  It should be on the one to be shutdown, not the one running the script.

---

### Post by andriu1 on 2011-06-03
Hello Lars,

    Now i'm working logged on the remote machine, and testing in local terminal, not executing the script and neither connected remotelly

    If I execute sudo shutdown -r now it reboots without asking for password for "sudo" command.

     Is this behaviour correct?. I thought that the line added to sudoers scripts allows to execute the command expected without password requierement, for the specified user, not executing it with sudo.

Thank you very much

Regards,
Andres

---

### Post by Lars Noodén on 2011-06-03
Yes. That behavior is correct. The NOPASSD keyword in /etc/sudoers means that on that same machine you can run sudo without a password if the critera that follow after are also met.  

So you need to have sudoers modified on the machine that you expect to reboot.  When you connect with SSH you can put a call to the shutdown program, along with any parameters, into the key itself.  Or just pass it along as a run time parameter.

---

### Post by andriu1 on 2011-06-07
Thank you very much Lars, i'll try it from the remote machine as soon as I can.
 
Best Regards,
Andres

---

### Post by andriu1 on 2011-06-13
Hi again Lars, and everybody.

I've written the following line into sudoers configuration

```
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown -r 1
```

because  I pretend only to allow to run "shutdown" command for "-r 1" without  password, so, if i run i shutdown -r now or shutdown -r 5 it's needed to  write a password.

Do you know if it's possible?, because it seems that with sudoers line as described above, a password is required anyway.

Another thing, when i execute the shutdown command from a remote machine this configuration doesn't work.

I have this script reinicio.sh (with x permission)

```
#!/bin/bash
sudo service apache2 stop
sudo service apache2 status
ssh -t remoteuser@remotemachine sudo /etc/init.d/mysql stop
ssh -t remoteuser@remotemachine sudo /etc/init.d/slapd stop
ssh -t remoteuser@remotemachine sudo /sbin/shutdown -r 1 Mensaje
```

I  run the script but it asks for a password for remoteuser@remotemachine when it tries ssh -t ....  command, although this line is configured in remote sudoers file.

```
Cmnd_Alias CMDS = /sbin/shutdown, /etc/init.d/mysql, /etc/init.d/slapd
```
....
```
remoteuser ALL = NOPASSWD: CMDS
```

Regards and thanks in advance for your help
Andres

---

### Post by Lars Noodén on 2011-06-13
> **andriu1 said:**
> ...
```
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown -r 1
```

because  I pretend only to allow to run "shutdown" command for "-r 1" without  password, so, if i run i shutdown -r now or shutdown -r 5 it's needed to  write a password.

Do you know if it's possible?, because it seems that with sudoers line as described above, a password is required anyway.


That should work if you do not type anything other than "-r 1" after "shutdown"  With /etc/sudoers it is a matter of making sure all the details match.

---

