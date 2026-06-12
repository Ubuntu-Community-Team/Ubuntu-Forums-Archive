---
title: "VBoxHeadless startvm over ssh"
date: 2010-11-24
forum: Server Platforms
---

### Post by etech22 on 2010-11-24
Hi,

I'm starting several VMs on a remote headless ubuntu server via ssh using:

```
VBoxHeadless -s <vmname>
```

The VM starts up okay, and I'm left with an occupied command terminal on my local ubuntu machine. So, if I want to start up several VMs on the remote server, I have to open up several command terminals and end up with as many occupied terminals once they're all running. When the local terminal is closed, the remote VM is also shutdown.

Is there a better way to do this without the remote VM being dependent on the local terminal? I'd like to remotely startup the VMs and be able to close the local terminals without shutting down the VMs. I'm sure this must be possible, I just don't know how to do it.

Any tips appreciated!

etech

---

### Post by CharlesA on 2010-11-24
Start it in the background:

```
VBoxHeadless -s <vmname> &
```

After it lists the port it's listening on, just type in another command or hit enter.

---

### Post by etech22 on 2010-11-24
> **CharlesA said:**
> Start it in the background:

```
VBoxHeadless -s <vmname> &
```

After it lists the port it's listening on, just type in another command or hit enter.

Great! Simple and easy, many thanks.


etech

---

### Post by CharlesA on 2010-11-24
Don't forget to mark the thread as solved from thread tools. :)

---

### Post by Kissack on 2011-03-01
I use vboxtool (autostart) to start my vm on boot up.  This exhibits the problem above, and worse it prevents further start up commands (ie webmin). 

I have tried various combinations of background and redirection (in vboxtool and vboxtoolinit), but each time on the main terminal it sits after reporting the remote port.

Running virtualbox 4.0.4

Any idea how i can get this to start 'quietly'?

thanks

---

### Post by CharlesA on 2011-03-02
Depending on how you want to deal with the vms at shutdown/startup, you can use the scripts I wrote up. They can be found [here]("http://charlesa.net/scripts/scripts.php").
Throw the startvm script in a crontab, and run the stopvm script before rebooting/shutting down.

---

