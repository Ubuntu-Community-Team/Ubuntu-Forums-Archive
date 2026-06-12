---
title: "ssh tunneling"
date: 2008-10-18
forum: Server Platforms
---

### Post by vivgrn on 2008-10-18
Hi 
I have been reading about ssh tunneling and have been using the following command
> ssh -ND 1801 username@server_name_on_which_i_have_ssh_account

and then i have been using the following as my firefox->preferences

server: 
server_name_on_which_i_have_ssh_account
port:
1801

when i try to browse google.com , i do not get any reply.
can anyone kindly help

thanks in advance.

---

### Post by Dr Small on 2008-10-18
SSH is creating a SOCKS proxy (if I recall correctly). Connect and then add your information into the SOCKS server information in Firefox Preferences.

---

### Post by pdwerryhouse on 2008-10-18
It looks to me like you're trying to make ssh act as a SOCKS server...

You should be putting "localhost" in the Firefox socks hostname field, not the hostname of the remote host.

---

### Post by vivgrn on 2008-10-18
yes surely you are correct.
well i was doing the same thing , messed it up in putting down.

but still it doesnt help.
Does it have to do something by the kind of remote server?
the remote server allows me to host websites into it.

---

### Post by Agent ME on 2008-10-18
Does the remote server allow tunneling? A lot of ssh hosts have that disabled.

---

### Post by vivgrn on 2008-10-19
Well that i am not sure of.
Can anyone tell me how do i determine whether a server is allowing tunneling or not?
Without asking the administrator that is.

---

### Post by pdwerryhouse on 2008-10-24
Check that the /etc/ssh/sshd_config on the remote host doesn't have:

```
AllowTcpForwarding no
```

---

