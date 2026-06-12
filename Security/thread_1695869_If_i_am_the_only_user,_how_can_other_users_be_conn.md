---
title: "If i am the only user, how can other users be connected, at shut down"
date: 2011-02-26
forum: Security
---

### Post by mj.marches on 2011-02-26
I need some assistance regarding the message i got recently that 'other users are connected' and 'shut down cannot continue' and 'i must type in my password to continue'. Something of that sort. Its v9.04 on a notebook so its not running the server version, remote desktop is set to "never...", and ssh is not running as far as i can tell. I was watching videos on the web of the Foo Figh*** of all things and got to some foreign writing page. I did not think anything of it until i went to shut down and got that message. I am the ONLY user. How could someone connect? Where can i see the logs? and how can this be monitored? Any help would be greatly appreciated to make sure no one is connecting. I had never seen the message before and have not seen it since. THX

---

### Post by cariboo on 2011-02-26
If you ever get the message again, type:

```
who
```

to see who else is logged on, you more than likely still have a terminal open somewhere.

---

### Post by asmoore82 on 2011-02-26
Are you sharing any files with Samba/SMB/CIFS/"Windows Network Neighborhood"?

---

### Post by rookcifer on 2011-02-26
As cariboo said, it is likely that your user has another terminal open or what have you.  Also, there are a number of files/processes that are owned by specially designated "users" that are not "real" physical users.  For instance, every system has a user called "nobody," but obviously nobody can't be somebody. ;)

---

