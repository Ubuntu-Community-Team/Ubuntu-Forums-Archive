---
title: "Enabling livepatch on Azure?"
date: 2021-09-01
forum: Security
---

### Post by zurcher-5 on 2021-09-01
I have a Ubuntu server running on Azure, and would like to enable livepatch on it. The [livepatch wiki page]("https://wiki.ubuntu.com/Kernel/Livepatch") lists support for 5.4 GA azure kernel on 20.04, which I think I have installed successfully:

```
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.4.0-1056-azure x86_64)
```

I also have the latest version of the UA tools:

```

~$ ua --version
27.2.2~20.04.1

```

But when I try to enable, I get this message:

```
~$ sudo ua enable livepatch
One moment, checking your subscription first
Livepatch is not available for kernel 5.4.0-1056-azure.
Supported flavors are: generic, lowlatency, oem, aws.

```

Is there anything else I can do to get this working? All my searching just goes to Ubuntu Pro which I don't have.

---

