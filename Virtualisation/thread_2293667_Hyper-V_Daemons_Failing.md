---
title: "Hyper-V Daemons Failing"
date: 2015-09-06
forum: Virtualisation
---

### Post by jimwillsher on 2015-09-06
Hi all

I'm having exactly the same symptoms as this guy:

[https://social.technet.microsoft.com/Forums/windowsserver/en-US/22d2b38a-d34a-47f8-9ebe-155b7055ecae/running-ubuntu-on-hyperv-daemons-fail?forum=linuxintegrationservices](https://social.technet.microsoft.com/Forums/windowsserver/en-US/22d2b38a-d34a-47f8-9ebe-155b7055ecae/running-ubuntu-on-hyperv-daemons-fail?forum=linuxintegrationservices)

We're both running Ubuntu 14.04.3 LTS (x64) in Hyper-V on 2012 R2, and we're both having the Linux Integration daemons failing. I actually have two identical VMs (separately installed, not cloned) and both exhibit the same problem. One is runnign a full LAMP stack, the other is running just Logitech squeezebox software. Both are up to date via aptitude.

I'm speculating that it's a Linux problem, not a Microsoft problem (as the the daemons in the VM), hence why I am posting here.

Can anyone advise where I can start looking for the cause? For the avoidance of doubt I am NOT running linux-virtual, so I installed the daemons via:

*[INDENT]aptitude install hv-kvp-daemon-init linux-tools linux-cloud-tools[/INDENT]*


Many thanks



Jim

root@fulmar:~# uname -a
Linux fulmar.home.local 3.16.0-46-generic #62~14.04.1-Ubuntu SMP Tue Aug 11 16:27:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
root@fulmar:~# cat /var/log/boot.log | grep Hyper
 * Starting Hyper-V File Copy Protocol Daemon                                                                            [ OK ]
 * Starting Hyper-V VSS Protocol Daemon                                                                                  [ OK ]
 * Starting Hyper-V KVP Protocol Daemon                                                                                  [ OK ]
 * Starting Hyper-V File Copy Protocol Daemon                                                                            [fail]
 * Starting Hyper-V VSS Protocol Daemon                                                                                  [fail]
 * Starting Hyper-V KVP Protocol Daemon                                                                                  [fail]
 * Stopping Hyper-V File Copy Protocol Daemon                                                                            [ OK ]
 * Stopping Hyper-V VSS Protocol Daemon                                                                                  [ OK ]
 * Stopping Hyper-V KVP Protocol Daemon                                                                                  [ OK ]
```

---

### Post by jimwillsher on 2015-09-06
Edit......sigh, the sure-fire way to solve a problem is to psot to a forum. After a day of fighting this, I solve it within two minutes of posting :-)

For the benefit of others.....

*aptitude install hv-kvp-daemon-init linux-tools-`uname -r` linux-cloud-tools-`uname -r`*

---

### Post by Marcel_Hofmann on 2016-06-06
Hi,
i know this is a old Post, but i have the same Problem and your command is failig at my server.

[IMG]http://fs5.directupload.net/images/160606/az56g6g9.png[/IMG]

Any Idead why? It says "no paket was found" i think he processes the command incorrectly?

---

### Post by coffeecat on 2016-06-06
Have another look at the command in post #2:

```
aptitude install hv-kvp-daemon-init linux-tools-`uname -r` linux-cloud-tools-`uname -r`
```

It uses backticks (`) to enclose the string uname -r, which expands uname-r to your kernel version. You've use oridinary single quotes ('), thus:

```
aptitude install hv-kvp-daemon-init linux-tools-'uname -r' linux-cloud-tools-'uname -r'
```

This means that aptitude is trying to install the packages linux-tools-uname -r and linux-cloud-tools-uname -r, which of course don't exist. Look at your terminal output.

Anyway, I've closed this old thread. Please always start your own threads - you are more likely to get help that way. If the correctly typed command does not solve your problem, then start a new thread, linking back to this one for reference if you wish.

Also - if you wish to post terminal output, please copy and paste the output into your post using BBCode code tags (see the link in my sig), rather than using a screenshot. It is easier for those helping you to analyse the problem if you do.

---

