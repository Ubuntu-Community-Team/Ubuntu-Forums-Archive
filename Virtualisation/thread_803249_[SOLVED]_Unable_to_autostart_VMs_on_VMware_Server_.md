---
title: "[SOLVED] Unable to autostart VMs on VMware Server 2 under Ubuntu Server 8.04"
date: 2008-05-22
forum: Virtualisation
---

### Post by uoirej on 2008-05-22
Hi everyone.

I've installed VMware Server 2.0 ontop of Ubuntu Server 8.04, copied a preconfigured VM created earlier with VMware workstation. Guest system boots up and runs normally. Just one unsolved question: how can I autostart the guest machine after the host system boots?

The web interface apparently does not provide an option for autostarting guest systems (or maybe I wa not able to find the exact place for it).

I've tried manually adding **autostart= "poweron"** and **autostart.order= "10"** into the guest system's .vmx file. This did not help.

Any suggestions?

PS Running VMware Server 2.0 beta e.x.p build-84186 under UbuntuServer 8.04 (2.6.24-16-server).

PPS Does anoyne know what that "e.x.p" means?

---

### Post by uoirej on 2008-05-22
Found where in the VMware Server web interface to set autostart options. It is not on the particular guest system's screen, but on the host's ("main") screen: select host in the "Inventory" panel (root node of the tree), to the right "Commands" panel should appear with "Edit Virtual Machine Startup/Shutdown Settings" link on it.

Now I'm able to autostart the guest, but is there a way to correctly shutdown it when the host system goes down? VMware Server can nicely shut down any (haven't tried linux guests so far) guest interactively, but can it do the same when the host is going down?

---

### Post by dickohead on 2008-11-18
Just thought I'd say thank you! I've been looking for that option for hours!

:D

---

### Post by gumbotron on 2009-01-11
Awesome... I, too, was searching extensively for this info.  Thanks for following up on your original question post!

---

### Post by Dedoimedo on 2009-01-11
Hello,

You could the following:

Write a wrapper script that does the following:

1. Scans the VMware subnet for open ssh ports and connects to remote machines; this means you enable ssh to host and use one userid and password.
2. Connects and then runs shutdown from the command line.
3. After shutting down all virtual machines, closes the Server.
4. Shuts down the hosts.

Dedoimedo

---

### Post by chrelad on 2009-01-27
Thanks for the help! Just what I was looking for (and apparently missing) :)

Chrelad

---

### Post by skysurfer2 on 2009-02-04
The kudos just keep on comin'... Thanks for following up uoirej, I was looking in the wrong part of the web interface ;)

---

