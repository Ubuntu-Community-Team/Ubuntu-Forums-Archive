---
title: "startx - Cannot find a free VT"
date: 2014-11-01
forum: Virtualisation
---

### Post by Eugene_Eigi on 2014-11-01
Hello!

I'm absolutly new in Ubuntu, i used the "Search" function, but i did not find any solution for my problem.

I want to start a program with wine on my Virtual Server. Therefore i want to use startx. 

If i try to start it, it returns this at the end:

```
Loading extension GLX
(EE)
Fatal server error:
(EE) xf86OpenConsole: Cannot find a free VT: Invalid argument
(EE)
(EE)
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.

```
I set the DISPLAY variable (export DISPLAY=:0.0) before. 

Someone got a solution? I just read about an alternative with vnc4server, but i dont know, if this is the right solution.

Would be nice if you could help me.

Best regards,
Eugene

---

### Post by TheFu on 2014-11-03
I don't know the answer - actually, don't think the issue has anything to do with virtualization.

Don't know what a "free VT" is. What does google say?
Does your VM have X/Windows client libraries? Does it have a GUI?
Did you load WINE?
Does running notepad under WINE work?
Are you running local or remote?
Using ssh/rdp/vnc/NX/something else?
Does a desktop work for other things inside the VM?

I attempted to find something with reasonable search terms - but the Vermont wine cartel kept turning up in searches - even when excluding a number of drunk-wine terms and adding +linux.

Sorry - I'm not any help.

---

