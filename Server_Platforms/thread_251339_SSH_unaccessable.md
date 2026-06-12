---
title: "SSH unaccessable"
date: 2006-09-05
forum: Server Platforms
---

### Post by carlossousa on 2006-09-05
Hi there,

I have my Ubuntu Server up and running and basically this machine is a rsync backup of my file server.
The problem is that all the ports on this machine are closed and I don't know how to activate the SSH server so I can access it from a remote machine, via ssh shell.

Can anyone help?

Thanks

---

### Post by Uluen on 2006-09-05
Is the SSH server running? I didn't have to allow incoming ports or mess with inetd on my server install to be able to SSH to it.

---

### Post by carlossousa on 2006-09-05
](*,) 

Sorry ... I forgot to check if the sshd package was installed and ... dooooope ... it wasnt

Thanks

---

### Post by carlossousa on 2006-09-05
By the way,

How do I close the port 110 that is currently open. What mail server software gets installed by default to let that port open on a standard Ubuntu Dapper 6.06 Server installation?

Thanks

---

### Post by sysops on 2006-09-05
If port 110 is open, a process is likely to be listening on that port -- finding out the name of the process is likely to tell you what MUA you have running/installed on your system.

$ sudo netstat -ntap

^^ should tell you what you need to know.

If you still would like to close the port. Configure your firewall frontend or configure ipchains. You could also use host-based access control using TCP wrappers, but the latter is trickier and perhaps unecessary.

---

