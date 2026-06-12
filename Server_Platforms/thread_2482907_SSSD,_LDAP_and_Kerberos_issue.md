---
title: "SSSD, LDAP and Kerberos issue"
date: 2023-01-13
forum: Server Platforms
---

### Post by dani32 on 2023-01-13
Hi There,

I am running Ubuntu 22.04 LTS and some of my Linux server run into the follow issue:

[COLOR=#3C444D][FONT=&quot]ldap_child[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot][xxxxx[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]][/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]:[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]Failed[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]to[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]initialize[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]credentials[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]using[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]keytab[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]MEMORY:/etc/krb5.keytab[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]][/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]:[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]Preauthentication[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]failed.[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]Unable[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]to[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]create[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]GSSAPI-encrypted[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]LDAP[/FONT][/COLOR][COLOR=#3C444D][FONT=&quot] [/FONT][/COLOR][COLOR=#3C444D][FONT=&quot]connection.

[/FONT][/COLOR]Therefore, password changes on my AD won't propagate on to the Linux machines.

Any clue how to resolve this issue?

Thanks,
Dan

---

### Post by MAFoElffen on 2023-01-14
This is the info I found with solutions... [https://www.suse.com/support/kb/doc/?id=000020793](https://www.suse.com/support/kb/doc/?id=000020793)

---

### Post by dani32 on 2023-01-15
Hi MAFoElffen,

Thanks for the reply. I found that article as well and have tried it before, unfortunately, didn't fix the issue . That's why I decided to leave a post in this forum.

Open to any other suggestions.

Thanks,
Dan

---

