---
title: "Ubuntu Lucid Lynx LAMP Server Died"
date: 2011-01-06
forum: Server Platforms
---

### Post by shoaibi on 2011-01-06
I have a Ubuntu Lucid Lynx 32bit Micro Instance running in Amazon EC2.
This one hosts 5 wordpress sites with medium traffic and has:
- LAMP
- PHPMyAdmin
- Mercurial
- Postfix

Installed.

This morning around 0700Hrs server time it stopped responding all of sudden, i tried to ssh but there was no response there either. AWS Monitoring shows CPU hitting 100% during that period. I have check and found that Traffic on all of my sites was pretty limited, so can't be an attack. Sites' log show no errors. I had took a backup of /var/log directory as soon as server came back up. I am sharing the messages file here. Check from line 300, that seems suspicious but i literally have no idea of whats happening here. Would really appreciate any comments to help me diagnose and fix this issue.

---

### Post by James78 on 2011-01-06
I assume you're talking about the oom-killer. The oom-killer simply starts killing processes to try to free up system memory when there's none left. This usually happens for example, when applications get memory leaks, and thus causing the RAM and systems memory to be exhausted.

Some program, appplication, (web application?), or something is probably causing it, I suggest watching everything closely, and see what process is causing it. Once you locate the process, you may be able to locate more specifically what it is. I would honestly say, from having no clue as to what process is causing this for you (you didn't give enough detailed information for that; however, it appears apache2 might be the cause, therefore leading to the conclusion that follows), it's most likely a web application or something somewhere. That's what would probably most likely be causing it.

Restarting, or shutting down your server and switching it back on might fix it.. Or might give you some time to implement a way to monitor the system closely and find the problem when it re-occurs.

Please note: While I'm 90% sure the opinions and ideas in my post are right, there is the potential possibility that I am wrong somewhere. I did Google this and read up on some stuff, so.. Just putting it out there. ;)

---

