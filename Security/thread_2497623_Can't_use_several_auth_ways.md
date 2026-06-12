---
title: "Can't use several auth ways"
date: 2024-05-12
forum: Security
---

### Post by enthusasist on 2024-05-12
[COLOR=#000000][FONT=Arial]Hello! Sorry if there&#8217;s already such a topic, couldn&#8217;t find it. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Could you please tell if there is a way to use different authentication ways at the same time? [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]For example if I add a fingerprint (with fprintd[/FONT][/COLOR][COLOR=#000000][FONT=Arial] 1.9.42[/FONT][/COLOR][COLOR=#000000][FONT=Arial] and pam-auth-update) I can only select to use: 
[/FONT][/COLOR]

[LIST]
[*]only password
[*][COLOR=#000000][FONT=Arial]only fingerprint
[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]password and then fingerprint
[/FONT][/COLOR]
[/LIST]
[COLOR=#000000][FONT=Arial]But I want to use fingerprint OR password (what I prefer at the moment), 
or at least fingerprint and if it doesn&#8217;t work, then password.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]And similar situation with camera auth (faceID). I installed howdy [/FONT][/COLOR][COLOR=#000000][FONT=Arial]2.6.1[/FONT][/COLOR][COLOR=#000000][FONT=Arial], added my face and it even works when I want to use sudo it recognizes me, but when I try to login to my OS user it doesn&#8217;t recognize me and the worth thing is that it dowsn&#8217;t even ask password, just block me.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]My OS is: Kubuntu 22.04.4 LTS (Jammy Jellyfish)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Kernel: 6.5.0-28-generic #29~22.04.1-Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]plasmashell: 5.24.7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Qt: 5.15.3[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]KDE Frameworks: 5.92.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kf5-config: 1.0[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Laptop:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Lenovo ThinkPad T14s Gen 4 [/FONT][/COLOR]AMD[COLOR=#000000][FONT=Arial] (21F9S0T900)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Thanks in advance![/FONT][/COLOR]

---

### Post by currentshaft on 2024-05-14
asl s

---

### Post by enthusasist on 2024-05-16
Well, fortunately(or not), my little child does not yet know how to bypass system authentication methods, but can easily log into an unpassworded account and, for example, accidentally break something in remote production.

---

### Post by currentshaft on 2024-05-17
a

---

