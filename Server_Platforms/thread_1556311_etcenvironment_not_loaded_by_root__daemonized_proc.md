---
title: "/etc/environment not loaded by root / daemonized processes?"
date: 2010-08-19
forum: Server Platforms
---

### Post by DuztDruid on 2010-08-19
I was under the impression that /etc/environment was the place to put variables if you wanted them to be available to all users at all times. But I just realized root which is running my service processes doesn't seem to load it.

My /etc/environment:

```

RAILS_ENV="production"
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```

When I ssh to the box as a sudo user I can echo $RAILS_ENV and get production. However if I "sudo -s" to open up a root shell $RAILS_ENV is suddenly blank.

"sudo -i" will let me have the variable there but when I run my service with "service god start" it still doesn't pick up the variable for use inside the process.

The process is configured to run at boot time automatically if the machine has to be rebooted so it's crucial that the environment can be picked up at that time as well.

Is there any simple way to achieve this or do I have to somehow manually load /etc/environment in my init scripts or in the daemon process itself?

(I'm running Ubuntu 10.04 server edition in a VirtualBox instance with the latest apt-get upgrade)

---

### Post by DuztDruid on 2010-08-19
I found another post that has kind of the same problem:
[http://ubuntuforums.org/showthread.php?t=872881&highlight=etc/environment](http://ubuntuforums.org/showthread.php?t=872881&highlight=etc/environment)

However I found that the #!/usr/bash -l approach did not work when managing the daemon process with the service command.

I have currently gone with the following solution.

1. Prefix everything in /etc/environment with "export".

2. Use "source /etc/environment" in my init.d script to load the environment variables and make them available to the daemon.

Is there a better way to accomplish this?

---

