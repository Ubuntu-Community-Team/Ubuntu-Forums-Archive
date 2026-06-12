---
title: "cron to kill process"
date: 2009-02-01
forum: Server Platforms
---

### Post by SeaborneClink on 2009-02-01
I'm trying to write a command that can be included in a cronjob to fetch a process's id based on run location, and this is what I've come up with so far after a bit of googling 

```
 ps aux | grep /path/to/file/ | grep -v grep | awk '{print $2}'
```

Since awk '{print $2}' only displays the process, how would I go about including, or passing on the variable $2, to the kill command?

kill $2 didn't work, and logically doesn't seem like it would since $2 means nothing without awk. :confused:

I might end up just turning this into a bash script if that would be easier than putting it directly in the cron command. They both should have the same effect right?

---

### Post by SeaborneClink on 2009-02-01
> **SeaborneClink said:**
> I'm trying to write a command that can be included in a cronjob to fetch a process's id based on run location, and this is what I've come up with so far after a bit of googling 

```
 ps aux | grep /path/to/file/ | grep -v grep | awk '{print $2}'
```

Since awk '{print $2}' only displays the process, how would I go about including, or passing on the variable $2, to the kill command?

kill $2 didn't work, and logically doesn't seem like it would since $2 means nothing without awk. :confused:

I might end up just turning this into a bash script if that would be easier than putting it directly in the cron command. They both should have the same effect right?

Found the solution.
```
 kill `ps aux | grep "/path/to/file/" | grep -v grep | awk '{print $2}'`
```

---

### Post by gmc on 2009-02-01
Perhaps you might want to look at the pidof program. If I understand what you want to do...

kill -9 `pidof /path/to/file`

G.

---

### Post by SeaborneClink on 2009-02-01
> **gmc said:**
> Perhaps you might want to look at the pidof program. If I understand what you want to do...

kill -9 `pidof /path/to/file`

G.
Edit: Sorry, when I put /path/to/file I meant it in a, kill process that was launched from this directory, not in a kill the proccess located at /path/to/file/application

---

