---
title: "Ubuntu 22.04 Disable SSH Weak Message Authentication Code Algorithms"
date: 2023-07-21
forum: Security
---

### Post by rsthakur83 on 2023-07-21
[COLOR=#232629][FONT=-apple-system]Hello Everyone,

Thanks in Advance.

[/FONT][/COLOR]I have installed latest Ubuntu 22.04.2 version on the vm but after performing the security assessment our security team found following ssh vulnerability. what changes we need to make to fix this vulnerability?


**Vulnerability_Risk Detail:**


SSH Weak Message Authentication Code Algorithms


**Summary:**


The SSH server supports cryptographically weak Hash-based message authentication codes (HMACs) including MD5 or 96-bit Hash-based algorithms.


**Remediation:**


Disable any MD5 or 96-bit HMAC algorithms within the SSH configurationConsult the product documentation for instructions to disable any insecure MD5 or 96-bit HMAC algorithms within the SSH configuration.


I have already tried following config changes but still i can see both weak algorithms ( [email]umac-64-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com[/email],hmac-sha1):


Here are the changes i have set in the sshd_config file.


MACs [email]hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1

---

### Post by CharlesA on 2023-07-22
This might be helpful.

[https://infosec.mozilla.org/guidelines/openssh](https://infosec.mozilla.org/guidelines/openssh)

---

