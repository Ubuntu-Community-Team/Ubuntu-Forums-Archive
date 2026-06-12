---
title: "Scripting netplan for autoconfig of static IP"
date: 2018-08-13
forum: Server Platforms
---

### Post by ecrosby on 2018-08-13
So, I am new to Ubuntu Server 18.04, netplan and .yaml. In the past using Ubuntu Server 16.04  I was able to create a pretty decent shell script to setup a static IP on a server in a post-installation setup.
Is it not possible to script out the network configuration now that Ubuntu Server 18.04 is using netplan?
I was trying to tweak my shell script to configure the writing to the .yaml file but it seems formatting is crucial when editing a .yaml file and I was not having much luck. It seems Ansible may possibly be a solution for this, possibly? But I've yet to master Ansible.
Anyone else have any luck writing a script to configure a static IP using netplan and updating the .yaml file?

---

### Post by steeldriver on 2018-08-13
Yes formating (well, correct and consistent indentation) is crucial in the yaml syntax

What problem are you having, exactly?

---

### Post by wyliecoyoteuk on 2018-08-13
Indentation is important, and you must **not** use tabs, only spaces

---

### Post by ecrosby on 2018-08-13
> **steeldriver said:**
> Yes formating (well, correct and consistent indentation) is crucial in the yaml syntax

What problem are you having, exactly?

The proper way to script it. Bash shell scripting doesn't seem to be the best way to script it because of formatting. Can it be scripted for automation of configuration? Is this where Ansible is the best solution?

---

### Post by steeldriver on 2018-08-13
I would think a here-document should work, no?

```

cat > path/to/file.yaml << \EOF
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
EOF

```

Or you could use `printf` statements.

---

### Post by ecrosby on 2018-08-13
> **steeldriver said:**
> I would think a here-document should work, no?

```

cat > path/to/file.yaml << \EOF
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
EOF

```

Or you could use `printf` statements.


Hmmm... okay. I'll try that.

---

