---
title: "Sendmail says EHLO with 127.0.0.1"
date: 2008-03-17
forum: Server Platforms
---

### Post by pkchukiss on 2008-03-17
I am trying to get sendmail to work on my Gutsy server, but while emails can be sent to certain servers, the email headers all appear to be wrong, and Hotmail specifically rejects servers that identify themselves as local:

```
Return-Path: <www-data@gutsy>
```

```
Received: from 127.0.0.1 (localhost [127.0.0.1])
	by 127.0.0.1 (8.14.1/8.14.1/Debian-8ubuntu1) with ESMTP id m2H42mrx012077
	for <removedemail@somewhere.com>; Mon, 17 Mar 2008 04:02:48 GMT
```

How do I get sendmail to report the server's IP or fully qualified domain name?

---

