---
title: "deploy.akamaitechnologies.com"
date: 2008-04-02
forum: Security Discussions
---

### Post by sekinto on 2008-04-02
I just installed the Firestarter firewall and I was looking at active connections. Some things had "Firefox" listed as the program utilizing the connection, and some things had "Transmission" listed instead. However two identical connections listed no program.

These two connections were both to the same destination:
a204-245-162-32.deploy.akamaitechnologies.com

They were also both connections to port 80 using the HTTP protocol.

Anyway, I closed both Firefox and Transmission, it still showed the connections were active. Then I ended the update notify and Evolution notify services because I though that might be what the connections were for, but no, the connections remained active.

Now I did a quick Google search and it looks like Akamai Technologies provides media hosting/streaming for websites so it doesn't waste their bandwidth. They seem legit, but I have no clue why I have a constant connection with one of their servers, it doesn't make sense at all.

Does anyone know what program could be using the connection, I hope it is nothing malicious.

---

### Post by brian_p on 2008-04-02
> **sekinto said:**
> I just installed the Firestarter firewall and I was looking at active connections. Some things had "Firefox" listed as the program utilizing the connection, and some things had "Transmission" listed instead. However two identical connections listed no program.

These two connections were both to the same destination:
a204-245-162-32.deploy.akamaitechnologies.com

They were also both connections to port 80 using the HTTP protocol.

That's port 80 on the remote host. The connections were established by your browser.

> Anyway, I closed both Firefox and Transmission, it still showed the connections were active. Then I ended the update notify and Evolution notify services because I though that might be what the connections were for, but no, the connections remained active.

The entries weren't greyed out?

> Now I did a quick Google search and it looks like Akamai Technologies provides media hosting/streaming for websites so it doesn't waste their bandwidth. They seem legit, but I have no clue why I have a constant connection with one of their servers, it doesn't make sense at all.

Can't explain that. Maybe the docs or the website is informative.

> Does anyone know what program could be using the connection, I hope it is nothing malicious.

This is Ubuntu. There are no malicious programs in the distribution.

---

