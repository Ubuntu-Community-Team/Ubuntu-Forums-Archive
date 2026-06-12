---
title: "Upstart script not loaded at boot [Oneiric]"
date: 2011-10-19
forum: Server Platforms
---

### Post by arathorn2nd on 2011-10-19
Hello everyone,

I've been trying to use Upstart to control VirtualBox virtual machines, but the scripts aren't loaded at boot and documentation is scarce or outdated as the project wiki mentions.

I have an upstart script in /etc/init/vmfile.conf as follows:
```
description “fileserver.vm”
author “Paulo”

start on runlevel [2345]
stop on runlevel [016]

console output

respawn
respawn limit 5 10

pre-stop script
  exec su ubuntu -c 'VBoxManage controlvm fileserver savestate'
end script

exec su ubuntu -c 'vboxheadless -s fileserver'
```

This works fine when I run ```
$ start vmfile
``` but it isn't loaded at boot, no matter what I do with the **start on** clause.
I currently have a simple script in /etc/init.d that runs **start vmfile** and works fine, but I don't like this solution.
Any have experience with this problem (or Upstart, at all) and can point in the general direction of a solution?
Thanks a lot.

---

### Post by CharlesA on 2011-10-19
I don't know much about upstart scripts, but be sure to include the full path whenever possible.

You might also want to check out the init.d script that myself and a few other members have posted.

You can find one of them [here]("http://ubuntuforums.org/showthread.php?t=1844885").

---

### Post by arathorn2nd on 2011-10-20
Thanks for the tip and the link to the scripts. I'm new to this SysV/Upstart stuff.

Does that script works as a daemon/service, restarting the VMs in case one is accidentally powered off? That was the reason I choose Upstart.

Also, do you recommend using Lucid Lynx for the host? Does it run VirtualBox 4.x? I see that's the configuration you are using on your posts.

I expected to find some information on Upstart here, as it seemed to be Ubuntu's replacement for SysV scripts. But now I found a blog post from an Ubuntu developer saying they may opt for another system in the next LTS release.
This situation is really confusing, as no documentation or directions is clear.

> **CharlesA said:**
> I don't know much about upstart scripts, but be sure to include the full path whenever possible.

You might also want to check out the init.d script that myself and a few other members have posted.

You can find one of them [here]("http://ubuntuforums.org/showthread.php?t=1844885").

---

### Post by CharlesA on 2011-10-20
> **arathorn2nd said:**
> Thanks for the tip and the link to the scripts. I'm new to this SysV/Upstart stuff.

Does that script works as a daemon/service, restarting the VMs in case one is accidentally powered off? That was the reason I choose Upstart.

Also, do you recommend using Lucid Lynx for the host? Does it run VirtualBox 4.x? I see that's the configuration you are using on your posts.

I expected to find some information on Upstart here, as it seemed to be Ubuntu's replacement for SysV scripts. But now I found a blog post from an Ubuntu developer saying they may opt for another system in the next LTS release.
This situation is really confusing, as no documentation or directions is clear.

The main reason I didn't try an upstart script was mostly due to the lack of information I could find on how to write them.

The script should work on any linux system, with virtualbox 3.x or 4.x, as the commands are mostly specific to virtualbox and there are a few generic linux commands that all distros should have (even if the path might have changed). I tested it on my VM host, which was running 10.04 and Vbox 4.x.

The script just workings as a startup/shutdown script and won't automatically power on any VMs that are powered off when the system is up, but you could configure it to do so by adding it to a crontab.

---

