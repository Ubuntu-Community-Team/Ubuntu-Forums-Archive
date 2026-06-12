---
title: "logrotate question"
date: 2009-02-26
forum: Server Platforms
---

### Post by stonneway on 2009-02-26
Hi,

I want to rotate the apache logs (ie all logs in /var/log/apache) daily rather than weekly or monthly.

Am I right in thinking that the only thing I need to change is the line in /etc/logrotate.d/apache that says WEEKLY to DAILY ?

I just wanted to be sure before I did it.

Thanks

Olly

---

### Post by Skip Da Shu on 2009-05-10
> **stonneway said:**
> Hi,

I want to rotate the apache logs (ie all logs in /var/log/apache) daily rather than weekly or monthly.

Am I right in thinking that the only thing I need to change is the line in /etc/logrotate.d/apache that says WEEKLY to DAILY ?

I just wanted to be sure before I did it.

Thanks

Olly

That's how it worked for me on my Ubuntu desktop systems.  You may need to restart logrotate with the -f switch to 'force' it to pick up the changes... I did on my desktop systems.  Of course I now can't remember the exact format of that and am looking for it again now.  :confused:

UPDATE... remembered... it's  ```
sudo logrotate -f /etc/logrotate.conf
```

---

