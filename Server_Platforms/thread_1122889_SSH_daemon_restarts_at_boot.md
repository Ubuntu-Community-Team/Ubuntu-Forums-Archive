---
title: "SSH daemon restarts at boot"
date: 2009-04-11
forum: Server Platforms
---

### Post by bstpierre on 2009-04-11
When restarting my testing server, sshd seems to start normally during the boot sequence. However, the login prompt appears as:

```

Ubuntu jaunty (development branch) jaunty tty1

jaunty login:  * Restarting OpenBSD Secure Shell server sshd

```

I've looked in all the logs I can think of (inside /var/log/) for some clue as to why it starts, and then for seemingly no reason restarts, but I haven't seen anything logged.

This is minor, but I'd like to not have the login prompt get jumbled, and for sshd to simply start at boot.

Does anyone have a clue as to what might be causing this?

---

### Post by bstpierre on 2009-04-11
It seems that I had added another rc script, so it was being started twice. Calling update-rc.d -f ssh remove left only the correct rc scripts and everything is working well now.

---

### Post by bstpierre on 2009-04-11
Turns out it isn't fixed... :(

---

### Post by sciburst on 2009-11-29
I am not sure if you are still looking for a solution. I was investigating the same issue and came across this bug: 

  [https://bugs.launchpad.net/ubuntu/+source/dhcp/+bug/390556](https://bugs.launchpad.net/ubuntu/+source/dhcp/+bug/390556)

It was suggested there that the script /etc/network/if-up.d/openssh-server is invoked to restart sshd when the network interface comes up. I did some tests and was able to confirm this. I have two interfaces on my server and my sshd was restarted twice during the boot-up sequence. The output redirection found in openssh-server unfortunately did not work as intended:

  invoke-rc.d ssh restart >/dev/null 2>&1 || true

thanks to the log_daemon_msg BASH function used through out /etc/init.d/ssh. So my easy way out of this situation was to change line 117 of /etc/init.d/ssh from

  log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd"

to

  echo "Restarting OpenBSD Secure Shell server sshd"

My server now boots up with no additional SSH-related messages in the console.

---

