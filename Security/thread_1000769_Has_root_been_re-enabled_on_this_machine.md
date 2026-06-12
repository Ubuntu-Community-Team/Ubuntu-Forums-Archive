---
title: "Has root been re-enabled on this machine?"
date: 2008-12-03
forum: Security
---

### Post by MikeCr on 2008-12-03
Someone who is not usually a Ubuntu user sent me an excerpt from the auth.log file on a machine he has inherited.  It contained a line similar to (I've removed the IP address for various reasons)

Accepted password for root from xx.yyy.zzz.abc port 44953 ssh2

Our question is 'Are we right in assuming that one of our users
has re-enabled root on this machine or is their another way this could have happened?'

Cheers,
Mike

---

### Post by Nepherte on 2008-12-03
That looks like an actual login as root indeed. You better not allow ssh logins as root at all. Since you didn't know about it, I'd say your server has been compromised.

---

### Post by hyper_ch on 2008-12-03
when in doubt, consider your computer as compromised and re-setup everything.

---

### Post by cdenley on 2008-12-03
To verify it has been enabled
```

sudo getent shadow root|cut -d : -f 2

```
The output should be a "!", but since it has been enabled, it probably looks something like:
$1$Hkx3o9Ri$Usb1jHwI7seZZAzNQMN4X.

To re-disable root:
```

sudo usermod -p ! root

```

To verify it is disabled
```

sudo getent shadow root|cut -d : -f 2

```
The output should be a "!".

When the password hash is set to "!", there is no valid password for that account. That would mean an event like the one referred to in your log would be impossible unless someone set a password for root.

Obviously, you don't know what that person did when they remotely logged in as root, so you can't trust that system anymore. I suggest reinstalling from scratch.

---

### Post by MikeCr on 2008-12-03
Thanks for the information and advice.  The machine in question is being wiped.

Best wishes,
Mike

---

### Post by davidshere on 2008-12-03
> **MikeCr said:**
> Thanks for the information and advice.  The machine in question is being wiped.

Best wishes,
Mike

If you believe that the machine or data on it has been otherwise compromised, that's not a bad idea.  It's not necessary to in order re-disable the root account, though.

---

### Post by hyper_ch on 2008-12-03
root doesn't enable itself... and someone logged in... and I think the TO would know if he did that... as he is surprised, the only real good thing he could do is (a) make a backup and safe evidence for forensic and then (b) wipe and reinstall the machine.

---

