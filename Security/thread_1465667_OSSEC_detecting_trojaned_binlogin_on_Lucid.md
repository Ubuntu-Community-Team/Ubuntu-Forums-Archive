---
title: "OSSEC detecting trojaned /bin/login on Lucid"
date: 2010-04-29
forum: Security
---

### Post by rjtd on 2010-04-29
Hi,

OSSEC is detecting a trojaned version of /bin/login on a Lucid clean install.

[FAILED]: Trojaned version of file '/bin/login' detected. Signature used: 'bash|elite|SucKIT|xlogin|vejeta|porcao|lets_log|sukasuk' (Generic).

Is this a false positive?

---

### Post by CharlesA on 2010-04-29
Have you already verified the MD5SUM?

If that's ok, I'm sure it's a false positive.

---

