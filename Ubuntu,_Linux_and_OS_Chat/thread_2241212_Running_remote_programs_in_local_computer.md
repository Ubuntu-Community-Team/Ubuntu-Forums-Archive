---
title: "Running remote programs in local computer"
date: 2014-08-25
forum: Ubuntu, Linux and OS Chat
---

### Post by ras123 on 2014-08-25
Hi,

Is it possible to run remote programs (using the remote computers computing power) as a local program?

For example, I have a powerful computer (remote), installed gcc, and I need to run that gcc to compile my local files (say in laptop), but my laptop has less computing power, but I like to edit the files locally. Is it possible to use ssh?

Thanking You,

Ras

---

### Post by steeldriver on 2014-08-25
You could possibly mount the directory containing the local source files on the remote computer (using NFS or SSHFS for example), and then compile them on the remote computer through an SSH session.

---

### Post by SeijiSensei on 2014-08-25
You can also run X-aware programs on the remote machine and display their output on the local desktop.  First, log in with the command "ssh -X remote_host" with the remote's hostname or IP address.  You'll get a terminal window on the remote.  Then run a program on the remote like, e.g., "firefox &".  The "&" runs the program in the background and will free up the terminal session.  You'll see Firefox appear on the local desktop.

If all you need is a terminal session, for compiling as you suggest, then just "ssh remote_host" is enough.  If you haven't installed the openssh-server package on the remote, you'll need to do that before you can connect.

---

### Post by ras123 on 2014-08-30
> **SeijiSensei said:**
> 
If all you need is a terminal session, for compiling as you suggest, then just "ssh remote_host" is enough.  If you haven't installed the openssh-server package on the remote, you'll need to do that before you can connect.
Yes, I can connect with ssh to remote computer, but then I can compile files hosted in remote computer, not possible to compile files in local machine. Only possible by remote mounting local files?

Thanks for the replies.

---

### Post by diepnguyen on 2014-09-01
If you can compile the source in remote machine, why do you need to do this work in local? And then you must to copy these binaries to the remote one?

---

### Post by ras123 on 2014-09-01
The editing of the source is easy in local machine.

---

### Post by SeijiSensei on 2014-09-02
It's just as easy on the remote.  You can open two SSH sessions, one with an editor, and one to run the program.  Alternatively, if you want a GUI editor, use "ssh -X", then run gedit or kate or whatever on the remote.  You'll see the output on your local machine.

---

