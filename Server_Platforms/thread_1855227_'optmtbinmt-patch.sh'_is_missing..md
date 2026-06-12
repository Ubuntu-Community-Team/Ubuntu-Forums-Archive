---
title: "'/opt/mt/bin/mt-patch.sh' is missing."
date: 2011-10-05
forum: Server Platforms
---

### Post by RobertWHurst on 2011-10-05
Hi there,
My Name is Robert and I operate a 10.04 ubuntu server. I've been having an issue with apt-get. Every time I install or update packages it says that it can't find a shell script called mt-patch.sh. Its looking in /opt but there is nothing in the opt folder at all.

Here is a useful segment of the console output.

```
ldconfig deferred processing now taking place
sh: /opt/mt/bin/mt-patch.sh: not found
E: Problem executing scripts DPkg::Post-Invoke '/opt/mt/bin/mt-patch.sh'
```

Please note this happens on any package update or install.

Can someone tell me what is going on here and how i can repair the damage?

Thank you,

- Robert Hurst

---

### Post by RobertWHurst on 2011-10-09
No one knows how to fix this?

---

