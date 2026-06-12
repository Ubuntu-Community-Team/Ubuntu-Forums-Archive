---
title: "My Courier pop server is being flooded"
date: 2010-02-26
forum: Server Platforms
---

### Post by mickey78 on 2010-02-26
Hello everyone.

I have a Ubuntu 9.10 server with courier installed as a pop3 server.

I would like to know how I can limit the number of connections from the same host. The reason is that almost everyday I get things like this in my logs, I can get hundreds/thousands a day and this is getting annoying. What I am looking is a way to slow down my server response to this IP (and any other futur IP's that does the same thing to my server) or ignore this IP after x number of attempts. Thanks



LOGIN FAILED, user=aaron, ip=[::ffff:117.41.228.238]: 2 Time(s)
    LOGIN FAILED, user=abe, ip=[::ffff:117.41.228.238]: 2 Time(s)
    LOGIN FAILED, user=abel, ip=[::ffff:117.41.228.238]: 2 Time(s)
    LOGIN FAILED, user=abigail, ip=[::ffff:117.41.228.238]: 2 Time(s)
    LOGIN FAILED, user=abraham, ip=[::ffff:117.41.228.238]: 2 Time(s)
    LOGIN FAILED, user=access, ip=[::ffff:117.41.228.238]: 1 Time(s)
    LOGIN FAILED, user=account, ip=[::ffff:117.41.228.238]: 2 Time(s)
    LOGIN FAILED, user=ace, ip=[::ffff:117.41.228.238]: 2 Time(s)
    LOGIN FAILED, user=ada, ip=[::ffff:117.41.228.238]: 2 Time(s)
    LOGIN FAILED, user=adabas, ip=[::ffff:117.41.228.238]: 1 Time(s)
    LOGIN FAILED, user=adam, ip=[::ffff:117.41.228.238]: 5 Time(s)
    LOGIN FAILED, user=adela, ip=[::ffff:117.41.228.238]: 2 Time(s)

---

### Post by nix4me on 2010-02-26
fail2ban

---

### Post by mickey78 on 2010-02-26
Nice, it can't be any better than this. Thanks.

---

### Post by noway2 on 2010-02-26
Based upon the log snippet, it is obvious that you are being targeted for a dictionary attack.  You could also consider putting a permanent block against the offending IP using IP tables.  Search for IP tables and blacklist, I think there is an ubuntu wiki page on how to do this.

---

