---
title: "Server is very slow"
date: 2008-02-25
forum: Server Platforms
---

### Post by damonjablons on 2008-02-25
I have a remote server that is running extremely slow.  The server is a regular LAMP server, so I was wondering if there are any tests I would be able to run to see if the mySQL database, or Apache itself is causing issues.

Any ideas?  Thank you in advance for your help.

---

### Post by freebeer on 2008-02-25
Have you tried htop?  It'll monitor the cpu usage for the various processes that are running.  Or were you looking for something else?

---

### Post by faulkes on 2008-02-25
> **damonjablons said:**
> I have a remote server that is running extremely slow.  The server is a regular LAMP server, so I was wondering if there are any tests I would be able to run to see if the mySQL database, or Apache itself is causing issues.

Any ideas?  Thank you in advance for your help.

Define "slow" and what hardware is it running on?

1.  is this bare metal or a VPS (virtual private server)?
2. are http requests taking a long time to fulfill?
3. what is the load average of the server?

```

uptime

```

4. what other services are running on the machine? (ftp? ssh? sftp?)
5. what sort of network connectivity exists between you and the server?
6. what does the output of 

```

ps aux

```

look like.

Faulkes

---

