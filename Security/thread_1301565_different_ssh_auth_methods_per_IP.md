---
title: "different ssh auth methods per IP"
date: 2009-10-26
forum: Security
---

### Post by falconindy on 2009-10-26
I currently have my sshd locked down to require an rsa key for login. This works fine as my main usage of ssh is indeed remotely and I always carry my usb drive. However, when I'm at home, I don't always have my key on me and there's times I'd like to use scp/ssh from my laptop downstairs with a password instead of a key.

Is there a way to allow different methods of ssh authentication based on the network of the client?

---

### Post by Lars Noodén on 2009-10-26
> **falconindy said:**
> I currently have my sshd locked down to require an rsa key for login. This works fine as my main usage of ssh is indeed remotely and I always carry my usb drive. However, when I'm at home, I don't always have my key on me and there's times I'd like to use scp/ssh from my laptop downstairs with a password instead of a key.

Is there a way to allow different methods of ssh authentication based on the network of the client?

Yes.  See the [Match](http://manpages.ubuntu.com/manpages/karmic/en/man5/sshd_config.5.html) keyword in sshd_config.  

You'll want something like this at the end of your sshd configuration file:

```

Match Address 192.168.0.0/16
    PasswordAuthentication yes

```

You'll have to match the network carefully as any mismatch will give an error

---

### Post by Lars Noodén on 2009-10-26
You can also combine several criteria on the Match line and if all the criteria are fulfilled, then the match succeeds.   So you could limit the access not only to a subnet, but to members of a specific group while on that subnet.  

```

# any member of the group 'downstairs' can log in without a key
# while connecting from the subnet 
Match Address 192.168.0.0/16 Group downstairs
    PasswordAuthentication yes

```

---

### Post by falconindy on 2009-10-26
Delicious. Thanks!

---

