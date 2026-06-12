---
title: "rsyslog receiving messages on other server"
date: 2011-02-08
forum: Server Platforms
---

### Post by szpuni on 2011-02-08
Hello,

I have a rsyslog server which is receiving messages from other server running syslog.

I'm sending two events to monitoring server and i'm wondering how i can split them into 2 files.

In syslog server i have 
```

local0.* @X.X.X.X
local6.* @X.X.X.X
```
to send two types of messages and I'm receiving them in rsyslog like that:

```
if $fromhost-ip startswith 'x.x.x.x' then /var/www/logs/blah_syslog.log

& ~
```

Both of them are going to one file.
My question is how i can get local0 from production server to send messages to file1 and local6 to file2 on remote server?

I was trying to use contains and isequal directives to if statement but non of them works.

Any ideas how i can get it to work?

---

