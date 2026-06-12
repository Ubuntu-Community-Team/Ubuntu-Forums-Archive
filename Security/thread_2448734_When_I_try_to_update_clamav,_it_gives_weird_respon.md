---
title: "When I try to update clamav, it gives weird response"
date: 2020-08-12
forum: Security
---

### Post by jedi123 on 2020-08-12
Hello when I try to update clamav it gives me a weird response. 

> 
 sudo freshclam
[sudo] password for owner: 
Sorry, try again.
[sudo] password for owner: 
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
ERROR: initialize: libfreshclam init failed.
ERROR: Initialization error!

Thanks

---

### Post by &amp;KyT$0P# on 2020-08-13
And your question is...?

That terminal output looks like you already have freshclam running and (automatically?) updating ClamAV database.  You can read [FONT=Courier New]/var/log/clamav/freshclam.log[/FONT] to see when updates occurred.

---

### Post by jedi123 on 2020-08-13
SO how do i verify , through a command whether its downloading the latest virus/malware definition updates?

---

### Post by &amp;KyT$0P# on 2020-08-14
[FONT=Courier New]/var/log/clamav/freshclam.log[/FONT] is a human-readable text file containing information about [FONT=Courier New]freshclam[/FONT] update attempts.  Just look at the contents.

If you need/want to use Terminal,
```
less /var/log/clamav/freshclam.log
```

If it's blank, likely the logs were rotated, in that case try [FONT=Courier New]/var/log/clamav/freshclam.log.1[/FONT]

---

### Post by ipv on 2020-08-21
```
clamscan -V
```

should give you a result like : [B]ClamAV 0.102.4/25906/Fri Aug 21 09:10:42 2020

[/B]if the date is current or a day old clam is up-to-date.

---

