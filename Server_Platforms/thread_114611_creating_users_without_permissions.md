---
title: "creating users without permissions"
date: 2006-01-08
forum: Server Platforms
---

### Post by chortik on 2006-01-08
i want to allow the user to login via ssh, and be inable to do anything else in the system. the idea is that they will then use the ssh connection as a tunnel to connect to the proxy server running on the machine. i want to them to have no permissions otherwise.

is there a way of doing this, that does not involve changing my default permissions on various directories from 755 to 750, etc?

thanx

---

### Post by chortik on 2006-01-09
ok, i found a solution. i created a user 'nobody' in his own group and assigned /bin/cat as the shell.

---

### Post by Soleil-Raid on 2006-01-11
[QUOTE=chortik]ok, i found a solution. i created a user 'nobody' in his own group and assigned /bin/cat as the shell.[/QUOTE]

Unh, 'nobody' is a system user, you probably want to use a different name. Also, it might be better to use /bin/false as the shell.

---

### Post by chortik on 2006-01-12
/bin/false does not work because it closes the connection right after authentication. i want the connection maintained because i'm using ssh as a tunnel.

nobody didn't appear on the user list prior to my creating it.

---

### Post by imagine on 2006-01-12
[QUOTE=chortik]nobody didn't appear on the user list prior to my creating it.[/QUOTE]

Then you deleted that user.

[QUOTE=chortik]i want to allow the user to login via ssh, and be inable to do anything else in the system.[/QUOTE]
Two ideas, although I never really did anything like that:

1. Create a user account and set the shell to /bin/false. Then run the ssh-client with the option -N. This is also possible with plink on Windows IIRC.

2. Set up a public-key-authentication for that user and add something like *command="/bin/sleep 1800",no-pty* to his public key on the server (where you can also specify no-x11-forwarding, no-agent-forwarding, etc). That way the user cannot request a terminal and the only command he can run is sleep.

---

### Post by drogoh on 2006-01-12
[http://freshmeat.net/projects/ibsh/](http://freshmeat.net/projects/ibsh/)

That ought to be sufficient for the desired results.

---

