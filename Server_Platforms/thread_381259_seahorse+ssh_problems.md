---
title: "seahorse+ssh problems"
date: 2007-03-10
forum: Server Platforms
---

### Post by dremon on 2007-03-10
Hello,
I've got a problem with the ssh client and seahorse. The seahorse agent does not store the  passphrases to the keyring anymore and is unable to retrieve them from there.
When trying "ssh user@machine", the logging from the /var/log/auth.log says:

```

seahorse-agent[12170]: couldn't search keyring: (code 2)
seahorse-agent[12170]: Couldn't store password in keyring: (code 2)

```

The seahorse version is 0.9.92, running under Ubuntu Edgy.
The default keyring exists and is accessible from the Nautilus.

---

