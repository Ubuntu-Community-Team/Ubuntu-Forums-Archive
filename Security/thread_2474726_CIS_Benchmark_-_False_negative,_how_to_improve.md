---
title: "CIS Benchmark - False negative, how to improve"
date: 2022-05-06
forum: Security
---

### Post by rstraub-3589 on 2022-05-06
Dear all, (I'm new here, please let me know if I disregard some conventions and steer me in the right way)

we just started using the CIS benchmarks (CIS Ubuntu 20.04 Level 1 Server Benchmark) against our images. We fail on the check "sshd_configure_allow_users". In the official documentation (5.3.4) it reads we should restrict SSH access either via AllowUsers, AllowGroups, DenyUsers or DenyGroups:

The entry in /etc/ssh/sshd_config reads:
AllowUsers rstraub someone someoneelse

And manually auditing "sshd -T | grep -i AllowUser" returns:
allowusers rstraub
allowusers someone
allowusers someoneelse

The audit however "usg audit cis_level1_server" fails on rule "Restrict sshd user access via AllowUsers".

How/where could we see how the script is checking the rule and where could we raise a bugreport regarding these audits ?

---

### Post by The Cog on 2022-05-06
Try entering AllowUsers instead of allowusers. I believe the configuration is case sensitive.

---

### Post by rstraub-3589 on 2022-05-25
Hey Cog,

that's what I thought, but I do have "AllowUsers" in the config, when running sshd -T it returns the lowercase string.
(Sorry for the late reply, I thought I'd get a email notification on new replies)

---

### Post by The Cog on 2022-05-25
in **man sshd_config**, it's **AllowUsers**. That's the one I would go by. I've used it myself before now.

---

