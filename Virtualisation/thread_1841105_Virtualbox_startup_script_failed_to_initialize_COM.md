---
title: "Virtualbox startup script failed to initialize COM"
date: 2011-09-08
forum: Virtualisation
---

### Post by insanity54 on 2011-09-08
I need to make virtualbox start up with a specific virtual machine when a headless ubuntu server starts up. I've tried two things but neither have worked. Running "VBoxHeadless --startvm vmachine001" manually through ssh has no problems, but a startup script running the same command yields the folowing error:
```
VBoxHeadless: ERROR: failed to initialize COM!
```

The first thing I tried was using cron to run a bash script at startup which started vboxheadless. On separate tests, I tried each of these in the bash script and they result in the same "failed to initialize COM!" error:
```
/usr/bin/vboxheadless -s "vmachine001"
```
```
VBoxHeadless --startvm vmachine001
```

Next I tried an upstart script which also failed:
```
description     "VM Launcher"
author          "insanity54"

start on started network
stop on starting shutdown

console output

exec VBoxHeadless --startvm vmachine001
respawn
```

Does anyone know why the COM is failing to initialize and how I can make it initialize?

---

### Post by insanity54 on 2011-09-12
bump

---

### Post by CharlesA on 2011-09-13
Hi,

You might want to take a look at the startup script I use.

I'll post a link when I get it up.

EDIT: Here's the [link]("http://charlesa.net/scripts/linux/vboxscript.php").

---

### Post by insanity54 on 2011-10-03
Thanks for your script and your reply, CharlesA. While searching for a solution to this and other virtualbox problems I've had, I've come across several threads you have contributed to. I was actually hoping you specifically would reply to this topic because of your knowledge of virtualbox.

I am more familiar with init scripts than I am upstart jobs, so I think your script will work nicely for my setup.

Unfortunately your script did not solve the "failed to initialize COM" problem but it made me think; If both my script and your script didn't work, it's a problem other than the startup scripts...

I realized my home directory is encrypted, and the vbox files are in my home directory. I feel silly because I have this feeling that I already knew that it was encrypted, and didn't make the connection.

My next step is to remove the encryption, then I will try your script again and report back.

Thank you very much for your help.

---

### Post by CharlesA on 2011-10-03
Are you logged in when you start VBox or does it start on boot? If it's the type of encryption I am thinking of - if you are logged it, your home directory would be decrypted and you'd be able to access your home folder fine.

I figure that's the problem since you did say that they start fine when you start them manually.

---

### Post by insanity54 on 2011-10-04
Yes, I am logged in when I start vbox. Vbox does not start on boot.

---

### Post by CharlesA on 2011-10-04
Hmm. I don't know if encryption would play a part in that then.

So strange.

---

### Post by fingon.palantir on 2011-11-20
> **CharlesA said:**
> Hi,

You might want to take a look at the startup script I use.

I'll post a link when I get it up.

EDIT: Here's the [link]("http://charlesa.net/scripts/linux/vboxscript.php").

The script seems to be exactly what i´m searching for. 

But on a reboot all running VMs were saved correctly but they don´t come back. All VMs stays in the saved state. When I start the script manualy everything works fine. Have you any ideas to solve this problem.

---

### Post by CharlesA on 2011-11-20
> **fingon.palantir said:**
> The script seems to be exactly what i´m searching for. 

But on a reboot all running VMs were saved correctly but they don´t come back. All VMs stays in the saved state. When I start the script manualy everything works fine. Have you any ideas to solve this problem.
Make sure that vboxdrv starts before that script is run (ran?).

Check out the thread here:
[http://ubuntuforums.org/showthread.php?t=1844885](http://ubuntuforums.org/showthread.php?t=1844885)

---

### Post by insanity54 on 2012-08-17
> **CharlesA said:**
> Hmm. I don't know if encryption would play a part in that then.

So strange.

Just got it working. I'm pretty sure it was the encrypted home directory causing the problem.

The original virtual machine was stored under '/home/insanity54/virtualbox'. I created a new user without an encrypted home directory, then created a new virtual machine under  '/home/newuser/virtualbox'.

I updated the config of your init script to use the new virtual machine, rebooted the host machine, and the guest virtual machine started automatically!

---

### Post by CharlesA on 2012-08-17
Wow, what a pain.

Glad you got it working!

---

