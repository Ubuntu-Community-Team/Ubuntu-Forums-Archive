---
title: "Anyone know what &quot;\\.\&quot; means in MS?"
date: 2006-03-25
forum: The Cafe
---

### Post by cnbiz850 on 2006-03-25
I am trying to run a Windows software in Wine and it reports something like:
Unable to create file L"\\\\.\\E:"
I take it that "\\\\.\\E:" should mean "\\.\E:" in Windows term.  A Wine engineer says that it refers to special name space as described in MSDN.  I can't read MSDN (don't quite want to dig in to all the mess).  Can anyone here please explain what that really is?  The Wine engineer says that "\\.\" is supported in Wine, but I doubt it.

---

### Post by dabear on 2006-03-25
[QUOTE=cnbiz850]I am trying to run a Windows software in Wine and it reports something like:
Unable to create file L"\\\\.\\E:"
I take it that "\\\\.\\E:" should mean "\\.\E:" in Windows term.  A Wine engineer says that it refers to special name space as described in MSDN.  I can't read MSDN (don't quite want to dig in to all the mess).  Can anyone here please explain what that really is?  The Wine engineer says that "\\.\" is supported in Wine, but I doubt it.[/QUOTE]
I've had som problems running games through early versions of cedega. This was because I ran the program with a full path, not from it's own directory (e.g cedega /path/to/file.exe instead of cd /path/to && cedega file.exe), don't know id this fixes it for you?

I would atleast guess that «.\» is the same as the postix «./»

---

### Post by cnbiz850 on 2006-03-25
[QUOTE=dabear]I've had som problems running games through early versions of cedega. This was because I ran the program with a full path, not from it's own directory (e.g cedega /path/to/file.exe instead of cd /path/to && cedega file.exe), don't know id this fixes it for you?

I would atleast guess that «.\» is the same as the postix «./»[/QUOTE]

The problem occurred as I ran the program in its own directory.

---

