---
title: "a random line from the syslog..."
date: 2009-07-13
forum: The Cafe
---

### Post by heyyy on 2009-07-13
i'm just curious about what does this line mean...

```
CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null) 
```

---

### Post by prshah on 2009-07-13
> **heyyy said:**
> 
```
[color=red]CMD[/color] ([color=blue][ -x /usr/sbin/update-motd ][/color] [color=brown]&&[/color] [color=green]/usr/sbin/update-motd[/color] [color=cyan]2>/dev/null[/color]) 
```

[color=red]execute the following command[/color]

[color=blue]check if /usr/sbin/update-motd exists (message of the day)[/color]

[color=brown]AND (if it exists, then)[/color]

[color=green]execute it, and [/color]

[color=cyan]redirect errors to null[/color]

Essentially, it probably updates the Message Of The Day (MOTD) which is displayed usually during logon.

---

### Post by JohnFH on 2009-07-13
> **prshah said:**
> [color=red]execute the following command[/color]

[color=blue]check if /usr/sbin/update-motd exists (message of the day)[/color]

[color=brown]AND (if it exists, then)[/color]

[color=green]execute it, and [/color]

[color=cyan]redirect errors to null[/color]

Essentially, it probably updates the Message Of The Day (MOTD) which is displayed usually during logon.

Slight correction:  -x tests if the file is executable.

update-motd: [https://wiki.ubuntu.com/UpdateMotd]("https://wiki.ubuntu.com/UpdateMotd")

---

### Post by heyyy on 2009-07-13
so i guess its a default function from the system...but im still curious on what exactly does...? here are some more details 

```
....   ...		      (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[9424]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[10002]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
/USR/SBIN/CRON[10005]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[10759]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[11280]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
/USR/SBIN/CRON[11571]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[12235]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[12978]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[13695]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[14436]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
/USR/SBIN/CRON[14439]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[15314]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[15926]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
/USR/SBIN/CRON[16222]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[17009]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[17783]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[18565]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
/USR/SBIN/CRON[19335]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
/USR/SBIN/CRON[19338]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
......
```

---

### Post by JohnFH on 2009-07-13
Did you read the link in my last post?

Here's another link:  [https://help.ubuntu.com/9.04/serverguide/C/update-motd.html]("https://help.ubuntu.com/9.04/serverguide/C/update-motd.html")

---

