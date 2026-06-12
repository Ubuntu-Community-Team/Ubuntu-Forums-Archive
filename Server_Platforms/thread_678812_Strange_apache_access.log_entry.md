---
title: "Strange apache access.log entry"
date: 2008-01-26
forum: Server Platforms
---

### Post by EaglemanBSA on 2008-01-26
I'm running a simple apache server to host a couple of files I regularly need at school, and I ended up with a really strange entry in my access.log file:

80.83.238.231 - - [26/Jan/2008:03:22:03 -0500] "T\x1d\xacS[\x1d\x9fj2\x94\xed\x9b5@\x01\xf6\x89eF\xc0o\x10\xf5r\xecp\x89E\xad\xe7G\x89W\xc0\xe5\x94\xd1\xb1i'\xfa\x92r\xf7\xa9\xc8\xb7\xe6p\x8eJ\xf0\x05w\xcc\xd4\x8b\xba\xd1g\xe5\xb9" 501 - "-" "-" "-"

I looked up the ip, couldn't resolve a hostname, but it says the request is from russia (I live in OH, USA). Any idea what the heck that is?

---

### Post by MJN on 2008-01-26
It is probably just a bot looking for a web server that is vulnerable to a buffer overflow (hence the long request) however if your Apache is up-to-date you need not worry. Given the '501' error response it would appear it is a malformed request too (quote common - either on purpose or accidentally) and it looks it too, unless you copied and pasted it wrong.

Mathew

---

