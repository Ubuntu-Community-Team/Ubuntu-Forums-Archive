---
title: "Is it safe with pw + 2fa for ssh?"
date: 2017-10-26
forum: Security
---

### Post by calby on 2017-10-26
Hi,
On my server I'm running the 2FA + strong pw (32 long) and have change the ssh port to a new port.
This should bee impossible to hack right, for some boots and scriptkids etc I know that everything can bee hacked but is this safe?

Also got fail2ban on sshd and sshd-ddos.

---

### Post by ajgreeny on 2017-10-26
Safer and better not to use passwords at all for ssh connections.

Use public/private authentication keys as shown at [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

