---
title: "PTRACE issue (probably)"
date: 2010-10-21
forum: Wine
---

### Post by Alvarin on 2010-10-21
Greetings!
I have lately upgraded to Maverick from Karmic and, as many people found out, many games stopped working.
All over the Internet the solution is to disable the PTRACE change.
Now, my problem is, it looks like I don't have anything to do with the PTRACE altogether... I have searched for the strings "yama" and "ptrace" as parts of files and other than ".h" files there were ne references to "ptrace" and the "yama" was not found at all. I have tried to "sudo sysctl kernel.yama.ptrace_scope=0" but got error "error: "kernel.yama.ptrace_scope" is an unknown key"

I am really at a loss now.
Please, can anyone help me with this?
I am really low experience user, so please go step-by-step if you can.

EDIT - 
I have created file 10-ptrace.conf in the /etc/sysctl.d folder with the key turned to 0, restarted and that didn't work either.

---

