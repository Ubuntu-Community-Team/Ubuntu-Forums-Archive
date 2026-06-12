---
title: "run logrotate as normal user or sudo? encounering errors with both"
date: 2015-04-18
forum: Server Platforms
---

### Post by Raner on 2015-04-18
I am testing a logrotate config using [FONT=&amp]the debug flag:

```
logrotate -d [path_to_config] 
```[/FONT]

if I use

```
sudo logrotate -d [path_to_config] 
```

I get the message: ```
Ignoring /etc/logrotate.d/my_logrotate.conf because of bad file mode.
```

but if I actually run logrotate without sudo:

```
logrotate [path_to_config] 
```

I am given an error: 

```
error: error creating output file /var/lib/logrotate/status.tmp: Permission denied
```

(but the log does rotate. but if the status is not updated, it might not rotate correctly next time, which is a great worry of mine)

If I run the same command with sudo:

```
sudo logrotate [path_to_config]
```

there is no feedback (at all) and the terminal immediately resets to user@home. The log is not rotated.

I'm pretty new to linux, so I thought the error was a file permissions error, but I am unsure how to resolve it without using sudo. i checked and status.tmp belongs to root, so I thought sudo would solve this, but logrotate doesn't seem to play nice with sudo in this instance.

Any idea what is going on?

---

### Post by Raner on 2015-04-18
If I can provide any more information that might help, please let me know.

---

### Post by ian-weisser on 2015-04-18
Logs should generally be owned by root, so sudo is necessary for logrotate to work.

If you are curious about /etc/logrotate.d/my_logrotate.conf , then try the following command to compare it to other files in the same directory:
```
ls -la /etc/logrotate.d
```

---

