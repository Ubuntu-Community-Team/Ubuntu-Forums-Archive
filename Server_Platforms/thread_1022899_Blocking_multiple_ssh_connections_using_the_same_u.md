---
title: "Blocking multiple ssh connections using the same user"
date: 2008-12-27
forum: Server Platforms
---

### Post by jersak on 2008-12-27
Hi there,
I would like to know if it's possible to forbid multiple SSH connections from the same login (user).

Like, if the user "mark" is logged-in here, other person in another computer cannot login using the same user name, disconecting both of the or just blocking the second person.

Sorry if i couldnt explain this better.

---

### Post by pdtpatrick on 2008-12-27
check the manual for the sshd.conf file .. im sure you should be able to input in there which parameters you want existing.

---

### Post by hictio on 2008-12-27
Actually, the man page for the ssh configuration file would be 'sshd_config'.
Personally. I'm not aware of such an option to do what you want on the '/etc/ssh/sshd_config' file; the closest thign I can think of will be to add an 'AllowUsers' directive, like this:

```

AllowUsers peter.mestikoff@some.server.net

```

That way you are forcing user 'peter.mestikoff' to login only thru the box 'some.server.net', but, that user will be able to login as many concurrent times as he pleases from that box.

Perhaps you'll have more luck using [pam](http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules).

As usual, when dealing with ssh/ firewalls, make sure to keep a line of communication open in case something goes wrong, and you don't end up blocked out of your own server (of course, this is the server is only reachable thru the network)

---

