---
title: "Mail Server issue"
date: 2011-08-25
forum: Server Platforms
---

### Post by tcsmith1978 on 2011-08-25
Hi,

Just a little problem with mail being sent to my server.

It seems that people are receiving my mails but they are being flagged as spam.

Looking at the headers - i saw this...

```

Received-spf: error (google.com: error in processing during lookup of someone@somewhere.co.uk: DNS timeout) client-ip=XX.XX.XX.XX;
Authentication-results: mx.google.com; spf=temperror (google.com: error in processing during lookup of someone@somewhere.co.uk: DNS timeout) smtp.mail=someone@somewhere.co.uk

```

pretty sure this is the issue - but anyone know how to fix this?

---

### Post by shubham1 on 2011-08-25
the reasons may be the gmail marks it as spam because of the content or an unknown site are you sending this form locahost.

---

### Post by tcsmith1978 on 2011-08-25
yup - run from my own mail server. The error states that the DNS is timing out so not sure what to amend.

---

### Post by tcsmith1978 on 2011-08-25
Found the answer - useful if anyone else gets the same issue:

[http://www.123-reg.co.uk/support/support/answers/how-do-i-add-an-spf-record-to-my-domain-name-349/](http://www.123-reg.co.uk/support/support/answers/how-do-i-add-an-spf-record-to-my-domain-name-349/)

---

### Post by shubham1 on 2011-08-25
> **tcsmith1978 said:**
> Found the answer - useful if anyone else gets the same issue:

[http://www.123-reg.co.uk/support/support/answers/how-do-i-add-an-spf-record-to-my-domain-name-349/](http://www.123-reg.co.uk/support/support/answers/how-do-i-add-an-spf-record-to-my-domain-name-349/)
if your thread is solved use the thread tools to mark it as solved

---

