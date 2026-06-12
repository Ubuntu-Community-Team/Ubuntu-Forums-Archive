---
title: "seemingly harmless script halting startup"
date: 2010-06-09
forum: Server Platforms
---

### Post by chrisbay90 on 2010-06-09
Hey linux friends,

I have a small 'server' at home that I use primarily as an  NFS/webcache/seedbox/toy.

I also run boinc as it spends most of its time fairly idle. It has an  intel core 2 duo and I set boinc to use 1 core. So as to keep it  responsive i wrote a script to monitor its 5 minute load average and  suspend boinc if it goes above 1.5 and resume it if it falls below this.


```
#!/bin/bash

log=/var/log/loadWatchDog
date >> $log; echo "Beggining scrpt" >> $log
threshold=1.49
last=""

while [ 1 ]; do
  sleep 5m
  loadavg=`uptime | awk '{print $10}'| awk -F \, '{print $1}'`

  result=`expr $loadavg \> $threshold`
  if [[ "$result" -eq "1" ]] && [[ $last != "off" ]] ; then
    date >> $log; echo "stopping" >> $log
    boinccmd --set_run_mode never
    last="off"
  fi
  result=`expr $threshold \> $loadavg`
  if [[ "$result" -eq "1" ]] && [[ $last != "on" ]]; then
    date >> $log; echo "starting" >> $log
    boinccmd --set_run_mode always
    last="on"
  fi
done
exit 0
```

and i set it to run at startup by copying it into the /etc/init.d/ directory and running
```
sudo update-rc.d loadWatchDog.sh defaults
```

When it is powered on and pluged into a monitor it shows the starting services but seems to get stuck at starting boinc (squid also appears to not be running) never reaching the login prompt, i can however ssh in. This problem goes away when i remove my script.

Anyone have any ideas what i've done wrong?

---

### Post by WinstonChurchill on 2010-06-09
Your script has an infinite loop (obviously by design), but since it's invoked in init.d at startup, Linux waits for it to finish executing before displaying the login prompt... and it never finishes. You need to daemonize the script, which I think you do by forking to a new process and exiting, but I'll let somebody more bash-script-savvy than I tell you how to do that.

---

### Post by chrisbay90 on 2010-06-09
> **WinstonChurchill said:**
> since it's invoked in init.d at startup, Linux waits for it to finish executing before displaying the login prompt


Thats interesting i was not aware of that. Thank you Winston :p.

> **WinstonChurchill said:**
> 
You need to daemonize the script, which I think you do by forking to a new process and exiting, but I'll let somebody more bash-script-savvy than I tell you how to do that.

Is that at all possible in bash (i'v messed with fork() and execvp() in C) would simply calling another another bash script with an ampersand then exiting the first script work?

Anyone out there with more information on making a more solid deamon or pointers in the right out there?

---

### Post by disabledaccount on 2010-06-09
> **chrisbay90 said:**
> 
Is that at all possible in bash (i'v messed with fork() and execvp() in C) would simply calling another another bash script with an ampersand then exiting the first script work?

Anyone out there with more information on making a more solid deamon or pointers in the right out there?Yes, it is possible, using such method:
```
(eval "exec <cmd_or_script_here>" &)
```exec will terminate eval forked in subshell - tricky, but works fine.

You can look for examples in deamon scripts that are already installed ;)

---

### Post by chrisbay90 on 2010-06-09
> **tomazzi said:**
> Yes, it is possible, using such method:
```
(eval "exec <cmd_or_script_here>" &)
```exec will terminate eval forked in subshell - tricky, but works fine.

You can look for examples in deamon scripts that are already installed ;)

I had made an attempt at checking some of the other deamon scripts but as evident by my above script i am a woeful noob at bash and couldn't make much sense of what to look for.

Thanks a lot Tom, that's an excellent point in the right direction and should get me well under way.

---

