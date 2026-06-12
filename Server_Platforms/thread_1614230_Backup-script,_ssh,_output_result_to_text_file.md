---
title: "Backup-script, ssh, output result to text file"
date: 2010-11-05
forum: Server Platforms
---

### Post by LarsEriksson on 2010-11-05
Im using this script to save a backup to a NAS, however i want to print the result to a file that later can be mailed to me.

```
tar --totals -czf - /var/www | ssh user@host "cat > /backup_path/`date "+%Y-%m-%d"`.tar.gz"
```

i have tried just adding ">> logfile.txt" at the end of the command, but that obviously does not work.

How should i do this?

---

### Post by HermanAB on 2010-11-05
Howdy,

If you need to send the same data to two places, then you can use the program 'tee'.  See the man page.

Otherwise, you need to do it in two steps.  First save on the NAS, then read from the NAS.

---

### Post by LarsEriksson on 2010-11-05
Sorry, i think you have misunderstood me.

I want to save the result from the tar-command to a logfile, size of archive, etc, ie. the result from "tar --totals"

Otherwise the script works fine, i get the tar-archive where i want it and the contents are correct.

I just want to log the process.

---

