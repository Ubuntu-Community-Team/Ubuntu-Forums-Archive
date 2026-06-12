---
title: "Post fix send mail error"
date: 2009-11-13
forum: Server Platforms
---

### Post by ninnypants on 2009-11-13
I have postfix configured with mysql to forward email. It receives mail just fine but when it tries to send it out it errors. Can someone help me decipher the error.
```
Nov 12 23:57:33 Directories postfix/smtp[3794]: C45F11BC169: to=<ninnypants@example.com>, orig_to=<forwarder@example.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.23, delays=0.16/0/0/0.07, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing, id=03231-02, parts_decode_ext FAILED: file(1) utility (/usr/bin/file) failed, exit 8, parsing failure - missing last 1 results at (eval 90) line 165. (in reply to end of DATA command))
```

---

