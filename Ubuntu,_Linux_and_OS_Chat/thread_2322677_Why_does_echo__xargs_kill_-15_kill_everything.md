---
title: "Why does echo | xargs kill -15 kill everything"
date: 2016-04-29
forum: Ubuntu, Linux and OS Chat
---

### Post by Espen_Fossen on 2016-04-29
Hi

I am debugging an Nodejs application which are trying to kill old processes before starting a new one. This is being done by the following code:

```

      cmd = `ps -ef | grep ${this.chromedriver} | grep -v grep |` +
            `grep -e '--port=${this.proxyPort}\\(\\s.*\\)\\?$' | awk ` +
            `'{ print $2 }' | xargs kill -15`;
```

Which basically boils down to

```

  ps -ef | grep PROCESS | grep -v grep | grep -e PORT | awk '{ print $2 }' | xargs kill -15
```

The problem being that this command basically kills all processes when there are no previous processes. The same can be tested by just doing

```

  echo | xargs kill -15
```

I have tested this on 2 separate Kubuntu 16.04 machines with the same result, all processes of my currently running user gets killed. When trying on Arch Linux, the same command gives me "kill: not enough arguments".

Question 1: I am no expert in the usage of xargs, but why is this happening? Is it a bug?
Question 2: If not a bug, what is the best way to fix this. I was thinking that pkill might be a lot safer?

Espen

---

### Post by mario71 on 2016-05-27
MMM may I ask why are you sending the -15 signal ?

-1 is SIGTERM to ask the process to end (a nice way to end a process)
-9 is SIGKILL to kill it (not a nice way but necessary if its not responding or if -1 doesn't work).

---

