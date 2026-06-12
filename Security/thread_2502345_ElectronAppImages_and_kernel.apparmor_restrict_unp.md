---
title: "Electron/AppImages and kernel.apparmor_restrict_unprivileged_userns"
date: 2024-11-10
forum: Security
---

### Post by my1 on 2024-11-10
So Ubuntu Noble added some changes that cause issues with Sandboxing with Electron and/or AppImages, most notably they added ```
kernel.apparmor_restrict_unprivileged_userns
``` to the apparmor config and currently they do not launch because of

```
[FONT=monospace][COLOR=#000000][45708:1110/231028.455340:FATAL:setuid_sandbox_host.cc(158)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make su[/COLOR]re that /tmp/.mount_Cider2AyIwST/chrome-sandbox is owned by root and has mode 4755.
Trace/breakpoint trap (core dumped)
[/FONT]
```


[HR][/HR]
So far I found 3 options, but all of them seem to weaken some security measure, so I thought I would ask about it here.

1) run with --no-sandbox (aka disable the sandbox), the most common solution, kinda annoying since you need to either run from console or make desktop files that run with the parameter

2) add apparmor configs for each individual application to just allow userns
-> e.g. [https://askubuntu.com/a/1528215/866101](https://askubuntu.com/a/1528215/866101)

aside from kinda tedious, also seems kinda weak as even a whitelisted application is only listed by path and could be replaced easily by the owner of it

3) knock out the apparmor_restrict_unprivileged_userns globally.

I am not well versed enough to understand how userns works and how having an "unprivileged" userns is bad, however disabling the sandbox doesnt seem a great idea and if unprivileged userns is inherently unsafe both solutions 2 and 3 wouldn't be awesome either.


[HR][/HR]
So the Key questions are:

1) what are the implications of kicking out kernel.apparmor_restrict_unprivileged_userns

2) how does that compare to running affected applications without the sandbox.

3) are there other options, that do not pose the same "issues", and ideally could apply globally too?

---

