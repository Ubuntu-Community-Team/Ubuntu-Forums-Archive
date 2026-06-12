---
title: "Ubuntu 18.04 LTS Server - mail.mailutils issue sending text in body and attachment"
date: 2018-05-29
forum: Server Platforms
---

### Post by outofmemory on 2018-05-29
Hello all,
I have some issues on a newly installed Ubuntu 18.04 LTS Server with the mail (mailutils 3.4) program. If I use option '-A' for an attachment it won't send the mail with text in the body. My command looks like
```
echo "blablabla" | mail -A /path/to/attachment -s "blablabla" -a "From: email.address" -r "email.address" recipient.email.address
```
Checked also
```
 mail -A /path/to/attachment -s "blablabla" -a "From: email.address" -r "email.address" recipient.email.address < /path/to/txtfile
```
Strange behavior, since it works on my old Ubuntu 17.04 (mailutils 3.1). Has something changed?

---

### Post by slickymaster on 2018-05-29
Thread moved to **Server Platforms** for a better fit

---

### Post by outofmemory on 2018-06-07
After some further tests with the options '--alternate' and '--content-type=' I have given up. Switched over to s-nail, that solved my problem (for now).

---

### Post by bear2bear on 2019-04-01
I have same issue. 
No issue on mailutils ver 3.1.1 but 3.4 & 3.6 have same issue.

---

