---
title: "Synaptic &quot;Dependent Packages&quot; filter or.."
date: 2005-06-23
forum: Repositories &amp; Backports
---

### Post by Moonshade on 2005-06-23
Hello.

After playing with installing/uninstalling some programs, there probably is a lot of unneeded libraries and other misc packages left on my system. So in order to clean it up, it would be nice to get a list of all installed packages that have no other packages depend on them.

In Synaptic there is a "Dependent Packages" option in filters, but it seems you have to specify some name there and if I leave it empty, synaptic crashes.

So to put it more clear..  Is there any way to get list of packages with such properties: status=installed, dependent packages list = empty.

---

### Post by Xian on 2005-06-23
[QUOTE=Moonshade]After playing with installing/uninstalling some programs, there probably is a lot of unneeded libraries and other misc packages left on my system. So in order to clean it up, it would be nice to get a list of all installed packages that have no other packages depend on them.[/QUOTE]
You need to install deborphan and wajig if not already on your system.
Open a terminal (Applications>System Tools>Terminal) and issue the following command:
```
$ sudo apt-get install deborphan wajig
```
Now, you can use wajig with the command below to get orphan information:
```
$ sudo wajig orphans
```

---

### Post by Moonshade on 2005-06-26
Thanks, exactly what I wanted!

---

### Post by Akoluth of Nandus on 2005-06-29
You can do this with Synaptic, too.

1. Install deborphan.
2. Create a custom filter in Synaptic. (Settings->Filters->New).
3. Give it a name ("Orphaned packages" for example).
4. Uncheck all the checkboxes on the right except "Orphaned".
5. Click "OK".

There you are. You can now click "Coustom" in the lower left of the window and select your newly created filter.

---

### Post by johnzollo on 2010-02-24
> **Akoluth of Nandus said:**
> You can do this with Synaptic, too.

1. Install deborphan.
2. Create a custom filter in Synaptic. (Settings->Filters->New).
3. Give it a name ("Orphaned packages" for example).
4. Uncheck all the checkboxes on the right except "Orphaned".
5. Click "OK".

There you are. You can now click "Coustom" in the lower left of the window and select your newly created filter.

Creating a filter in Synaptic just shows packages that are orphaned for maintenance (or something).  It doesn't show packages that have no packages dependent on it.  

-John

---

