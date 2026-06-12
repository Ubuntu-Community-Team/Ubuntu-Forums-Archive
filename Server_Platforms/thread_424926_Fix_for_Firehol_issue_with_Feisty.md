---
title: "Fix for Firehol issue with Feisty"
date: 2007-04-27
forum: Server Platforms
---

### Post by shookone on 2007-04-27
I managed to stop getting errors from firehol in feisty by doing the following:


```

sudo cat /lib/firehol/firehol |grep %q -n
2366:   printf "%q " "$@" >>${FIREHOL_OUTPUT}
4705:   printf >&2 "COMMAND: "; printf >&2 "%q " "${work_realcmd[@]}"; echo >&2
4726:   printf >&2 "COMMAND: "; printf >&2 "%q " "${work_realcmd[@]}"; echo >&2
4780:   printf >&2 "%q " "$@"
4977:           printf "%q " "${work_realcmd[@]}"

```

```
sudo cp /lib/firehol/firehol /lib/firehol/firehol.bckup
sudo nano /lib/firehol/firehol
```

Now in nano you can press "CTRL+SHIFT+_" and type in the line number to jump to that line.

Change all instances of %q to %b and save the file. Reload Firehol and it should work. 

Please post confirmations...

---

