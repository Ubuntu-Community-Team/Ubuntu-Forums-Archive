---
title: "GRUB does not honor timeout settings when hibernating with systemd"
date: 2016-08-14
forum: Tutorials
---

### Post by tsjswimmer on 2016-08-14
Personally, I'm surprised I haven't been able to find any information about this already. I've searched this forum and Ask Ubuntu, but not one person seems to have complained about this issue. I guess people don't hibernate too often?

So, here's the deal: I'm running Ubuntu 16.04, and have set **GRUB_TIMEOUT=5** in /etc/default/grub. If I power off my machine everytime I'm done using it, there's no problem. However, if I hibernate my machine, thaw, and hibernate again, when it thaws again, GRUB uses a thirty-second timeout. Ubuntu 14.04 didn't do this. So what's the deal?

I noticed 16.04 doesn't have any issues if you're using upstart as your init system, so I figured the issue must lie with systemd. It seems the issue is caused by the fact that systemd doesn't unset the **recordfail** environmental variable in /boot/grub/grubenv. If you use Upstart, unsetting recordfail is taken care of, thanks to the **/etc/pm/sleep.d/10_grub-common** script, with **thaw** as an arguement. However, after spending an ungodly amount of time trying to figure out why another unrelated script I made wasn't being executed, I found out that systemd doesn't use any of the /etc/pm/sleep.d scripts by default, hence recordfail remaining. You can fix this everytime you thaw by either executing the aforementioned script, or by manually running **grub-editenv /boot/grub/grubenv unset recordfail**, but doing that after every hibernation can be rather tedious, especially if you hibernate frequently. So, our options are to force systemd to use this script, or to force systemd to run grub-editenv without the script. In this tutorial, I will focus on showing you how to do the former.

First we need to create a systemd service that will be executed after the system thaws from hibernation. So, step one is to write a file, which we can save to **/etc/systemd/system/use-10_grub_common.service**. It should look something like this:```
[Unit]
Description=Execute the /etc/pm/sleep.d/10_grub_common script after hibernation.
After=hibernate.target

[Service]
Type=oneshot
ExecStart=/etc/pm/sleep.d/10_grub-common thaw

[Install]
WantedBy=hibernate.target
```You should then be able to run **systemctl enable use-10_grub_common** as root, which will allow the service to run after hibernation. As a final step, sit back and enjoy a job well done.:cool:

Do note that GRUB still thinks your last boot attempt was a failure, so don't be surprised if the very next time you boot, GRUB still sets the timeout to 30 seconds. But that won't apply to subsequent boots (unless of course they actually do fail).

PS: If you want to execute grub-editenv without going through the 10_grub_common script, change the ExecStart line to **ExecStart=grub-editenv /boot/grub/grubenv unset recordfail**.

I hope this tutorial becomes useful to someone. Happy hacking, and may the force be with you!\\:D/

---

### Post by ajgreeny on 2016-08-14
Same problem here with an old netbook running Xubuntu 16.04 so thanks for this info.

The battery is useless on that machine so hibernation is essential rather than suspension, however, I use it so seldom, normally shutting down fully, that I haven't bothered to look for solutions and I just hit Enter when, or if, I see the countdown.  I had not associated it with systemd but it's interesting to see that you appear to have this figured out already so I shall try your workaround as soon as possible to see if it also overcomes my problem.

---

### Post by kahukowhai on 2016-08-29
I just used GRUB_RECORDFAIL_TIMEOUT=2 to give me a two second timer when resuming the system

GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="text nomodeset"
GRUB_CMDLINE_LINUX=""
GRUB_RECORDFAIL_TIMEOUT=2
GRUB_DISABLE_OS_PROBER="true"
GRUB_SAVEDEFAULT="false"

Xubuntu 16.04

---

### Post by mac75a on 2016-08-30
Thank you very much. It worked like a charm!!

---

### Post by zubzou on 2016-09-05
Hello tsjswimmer

I have been dealing with this issue for three weeks until I found your post. Thanks a lot. After some difficulties due to my lack of know how its now working perfectly. You are right. It seems that not so many people are hibernating their systems. Since I work on a quite old laptop and no each day (suspend would "eat" my Battery) I always hibernate.

Do you have the possibility to suggest this solution to the canonical or the grub people? The old solution with init doesnt work any more (the service exits and dont wake)

Best regards

JBartolome

---

### Post by zubzou on 2016-09-06
Additional information:
I have added another service in order to  unset the recordfail after normal boot. (the old one with initv resp  upstart doesn't work)
code:
[Unit]
Description=Execute the grub-editenv unset recordfail after normal boot.
After=basic.target
[Service]
Type=oneshot
ExecStart=/usr/bin/grub-editenv /boot/grub/grubenv unset recordfail
[Install]
WantedBy=basic.target

---

