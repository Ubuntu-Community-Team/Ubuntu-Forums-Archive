---
title: "Autostarting ddclient and Running it as a Daemon"
date: 2006-06-11
forum: Server Platforms
---

### Post by tabdelgawad on 2006-06-11
Hello:

I used synaptic to install ddclient (available in 6.06 Universe), a perl script that updates dynamic dns services with the system's current IP address.  I don't think the installation sets it to run as a daemon or makes it autostart.  The README file (from the tar.gz package from sourceforge) has instructions on how to run it as a daemon (copy an enclosed file into /etc/rc.d/init.d) and how to get it to auto start (/sbin/chkconfig --add ddclient), but these are specific to Red Hat systems.

What are the equivalent steps for Ubuntu 6.06?  I have a standard desktop install.

OR, if there is another recommended dynamic dns client for ubuntu, please let me know.

TIA,
Tamer

---

### Post by rso on 2006-06-25
I thought it worked for me, but it doesn't.
The installation copied a script into init.d, but it does not start at boot time, even though it says so under the boot-up manager (there is a light bulb next to the ddclient entry and no explanation for that?).

Any help would be appreciated.

---

