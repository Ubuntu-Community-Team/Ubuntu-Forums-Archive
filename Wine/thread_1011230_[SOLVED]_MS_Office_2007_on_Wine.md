---
title: "[SOLVED] MS Office 2007 on Wine"
date: 2008-12-14
forum: Wine
---

### Post by linnuxnub on 2008-12-14
I am using wine 1.1.10 and Office installs fine with no changes from a brand new wine installation. But when I try and run it it says starting office application on the task-bar but it just disappears without opening.

Wine is using windows vista, with no other changes from a fresh wine install.

When I run it from terminal this is what it says:
```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\WINWORD.EXE") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Office\\Office12\\WINWORD.EXE" failed, status c0000135

```

I am using Ubuntu 8.10.

Thanx in advance for any help.

---

### Post by linnuxnub on 2008-12-28
I solved my problem by going to this thread follow the instructions there they are very helpful.

[http://ubuntuforums.org/showthread.php?t=844309&highlight=office+2007](http://ubuntuforums.org/showthread.php?t=844309&highlight=office+2007)

---

