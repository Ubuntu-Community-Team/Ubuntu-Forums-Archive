---
title: "Having trouble getting smtp.gmail.com to work"
date: 2020-04-27
forum: Server Platforms
---

### Post by msikma on 2020-04-27
Hi there. I've been setting up Ubuntu 20.04 LTS as a new webserver. It's working very well, I've got Apache/PHP/MySQL set up and I'm now setting up a wiki for a project.

However, I ran into a problem. To get email sending working, I've set up a new Gmail account and created an app password, but for some reason I'm completely unable to even connect to smtp.google.com.

I've made [a test script](https://gist.github.com/msikma/5d30861c156bf499e0112020ab350415) (uses PHP-Pear) that works correctly on my local machine. It runs, and sends a new email through the which I receive in the expected mail address, so it runs fine.

But when I run that test script on my Ubuntu server, it times out saying:

```
Failed to connect to ssl://smtp.gmail.com:465 [SMTP: Failed to connect socket: Connection timed out (code: -1, response: )]
```

It even does this when I disable ufw completely, somehow.

Would anyone happen to know what could be wrong?

[HR][/HR]

Note: I can't even telnet to the server, somehow. On my local machine, it does work:
```

$ telnet smtp.gmail.com 465
Trying 64.233.166.109...
Connected to smtp.gmail.com.
Escape character is '^]'.
Connection closed by foreign host.

```

On my server:

```

$ telnet smtp.gmail.com 465
Trying 2a00:1450:400c:c08::6d...
Trying 74.125.140.109...
telnet: Unable to connect to remote host: Connection timed out

```

So I'm not sure, maybe I need to contact my host (Linode), but then maybe I am missing something in my setup. Appreciate any help!

**edit:**

I think maybe all email traffic is being blocked by Linode as a policy, and I didn't realize it from the feedback I was getting from my tests. I've opened a support ticket for that. But who knows, if anyone notices something else that I can check, please let me know. :)

---

### Post by LHammonds on 2020-04-27
Make sure your gmail account is configured to allow remote access: [Enable SMTP mail with gmail](https://www.youtube.com/watch?v=D-NYmDWiFjU) (YouTube Video)

LHammonds

---

### Post by msikma on 2020-04-28
Setting my post to solved, as it turns out it was because of email traffic being blocked on the server by Linode.
It took me a while to realize this, because it doesn't say anywhere that this is the case on the server admin page, and I would expect a block to cause calls to smtp.gmail.com to fail instantly rather than time out.

So if anyone has the same problem, check the docs for your host first!

---

### Post by SeijiSensei on 2020-04-28
I have three Linode servers and never had traffic of any kind blocked on any of them. You might try scanning your IP address at mxtoolbox.com to see if it shows up on any email blacklists. I did have a problem where one of my Linodes was assigned an IP address that had been used before by a spammer. Perhaps that's why your traffic was being blocked.

---

