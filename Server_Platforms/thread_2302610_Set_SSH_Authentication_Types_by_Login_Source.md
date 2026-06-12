---
title: "Set SSH Authentication Types by Login Source?"
date: 2015-11-11
forum: Server Platforms
---

### Post by tehtotalpwnage on 2015-11-11
Is there a way to manipulate the OpenSSH configuration files so that it only accepts, say, key based authentication from external IPs but allows for people connecting from my LAN to login using passwords?

---

### Post by matt_symes on 2015-11-11
Hi

I think you need to use the *Match* directive in OpenSSH to match the subnet and to override the global settings that will accept key based auth only.

You can match, amongst other things, users and ip address and subnets.

If your subnet was 192.168.10.0/24 then try appending this to your sshd_config on your server.

```
Match address 192.168.10.0/24
    PasswordAuthentication yes
```

I've never tried matching subnets, only users in the past, but from what i have read, i think it should work. 

Please post back if it does work.

You'll need to restart sshd on the server obviously.

**EDIT:**

Check out 

```
man 5 sshd_config
```

and the section on Match.

```
man 5 sshd_config | less +/"^[ ]*Match"
```

Kind regards

---

### Post by tehtotalpwnage on 2015-11-11
Just tried it and it works. Thanks!

---

