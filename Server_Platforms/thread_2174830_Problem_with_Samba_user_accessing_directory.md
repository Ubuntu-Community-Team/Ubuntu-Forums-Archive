---
title: "Problem with Samba user accessing directory"
date: 2013-09-16
forum: Server Platforms
---

### Post by lorenzo-milesi on 2013-09-16
[COLOR=#333333][FONT=monospace]I've a "special" user (it has nothing special, just this exception) in a group that cannot access a share.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I check share access using UNIX permissions.[/FONT][/COLOR]

[COLOR=#333333][FONT=monospace]This is the share definition:[/FONT][/COLOR]
```
[COLOR=#333333][FONT=monospace][progettazione][/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]comment = progettazione[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]path = /dati/progettazione[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]writeable = yes[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]browseable = Yes[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]directory mask = 0770[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]create mask = 0775[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]security mask = 0777[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]force security mode = 0[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]directory security mask = 0777[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]force directory security mode = 0[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]hide unreadable = Yes[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]force create mode = 0775[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]force directory mode = 6775[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]vfs object = recycle[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        [/FONT][/COLOR][COLOR=#333333][FONT=monospace]recycle: config-files = /etc/samba/samba-recycle.conf[/FONT][/COLOR]

```
[COLOR=#333333][FONT=monospace]this is the directory permission[/FONT][/COLOR]
```
[COLOR=#333333][FONT=monospace]# ls -la /dati/progettazione/ | head[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]drwxrws--- 55 lorenzo       progettazione     [/FONT][/COLOR][COLOR=#336699][FONT=monospace][4096 2013-09-12 10]("callto:4096 2013-09-12 10")[/FONT][/COLOR][COLOR=#333333][FONT=monospace]:10 .[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]drwxr-xr-x 20 root          root              [/FONT][/COLOR][COLOR=#336699][FONT=monospace][4096 2013-07-22 08]("callto:4096 2013-07-22 08")[/FONT][/COLOR][COLOR=#333333][FONT=monospace]:29 ..[/FONT][/COLOR]

```
[COLOR=#333333][FONT=monospace]all the user in "progettazione" group can access the share EXCEPT this one:[/FONT][/COLOR]
```
[COLOR=#333333][FONT=monospace]# groups bosco[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]bosco : dipendenti disegni progettazione[/FONT][/COLOR]
```

[COLOR=#333333][FONT=monospace]I'm not using acl, anyway I tried remounting the partition without acl and nothing changes.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]This user and group comes from ldap. If I[/FONT][/COLOR][COLOR=#333333][FONT=monospace] [/FONT][/COLOR]
```
[COLOR=#333333][FONT=monospace]# su - bosco[/FONT][/COLOR]
```
[COLOR=#333333][FONT=monospace]I can chdir to /dati/progettazione without issues.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]The only strange thing I experience is that whether ls and all unix commands decode users and group correctly when I sudo as the "bosco" user the prompt cannot decode user and groups.[/FONT][/COLOR]

[COLOR=#333333][FONT=monospace]Adding o+rwx permissions to the directory allows the user to chdir. It seems like[/FONT][/COLOR][COLOR=#333333][FONT=monospace] [/FONT][/COLOR]

[COLOR=#333333][FONT=monospace]I really don't know what else to look for.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Any help is welcome.

Thanks[/FONT][/COLOR]

---

