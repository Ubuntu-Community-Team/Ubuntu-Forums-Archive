---
title: "Why do I have to use sudo to shutdown in desktop Terminal?"
date: 2012-05-31
forum: Security
---

### Post by nrundy on 2012-05-31
I can shutdown via the GUI without having to input a password. I don't have to login to BASH when I open a Terminal on the Desktop.

How come I have to use Sudo before a shutdown command like: shutdown -h 0 when using a Terminal on the desktop? Isn't this massive overkill?

---

### Post by Cheesemill on 2012-05-31
Because Linux was designed as a multi-user system accessible from several terminals at different locations then allowing anyone to shut the machine down is a bad idea.

With the birth of graphical user interfaces and mostly single user machines applications such as consolekit, policykit and systemd were developed to allow non-root users to power off the machine using a GUI.

---

### Post by satish_j on 2012-06-01
> **nrundy said:**
> I can shutdown via the GUI without having to input a password. I don't have to login to BASH when I open a Terminal on the Desktop.

How come I have to use Sudo before a shutdown command like: shutdown -h 0 when using a Terminal on the desktop? Isn't this massive overkill?

This same question occurred to me as well..So,i searched on web and found you can assign suid bit to shutdown file in ubuntu.This will allow all users to execute shutdown from terminal without requiring any paswd..:)

I think the reason behind the need for password may be that the server OS are normally accessed from command window and are normally running critical applications which will be affected in case of a shutdown command getting fired from a normal user..

---

### Post by nrundy on 2012-06-01
> **satish_j said:**
> This same question occurred to me as well..So,i searched on web and found you can assign suid bit to shutdown file in ubuntu.This will allow all users to execute shutdown from terminal without requiring any paswd..:)

I think the reason behind the need for password may be that the server OS are normally accessed from command window and are normally running critical applications which will be affected in case of a shutdown command getting fired from a normal user..

how do i assign suid bit to shutdown without passwd?

---

### Post by satish_j on 2012-06-02
> **nrundy said:**
> how do i assign suid bit to shutdown without passwd?

use foll command
```

sudo chmod u+s /sbin/shutdown

```

---

