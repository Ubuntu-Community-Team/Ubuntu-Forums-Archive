---
title: "Unattended-upgrades EMAIL setting format for multiple recipients?"
date: 2014-07-18
forum: Server Platforms
---

### Post by petrogazz on 2014-07-18
I have searched around the forums but couldn't find a reference.

Is there a way to configure unattended-upgrades to send emails to multiple recipients?
The configuration is for email recipient is done via /etc/apt/apt.conf.d/50unattended-upgrades

```

//Unattended-Upgrade::Mail "root";
```

Many thanks!

---

### Post by SeijiSensei on 2014-07-21
Add an alias to /etc/aliases like this:
```
upgrades:     root,you@example.com,someone@somewhere.net
```
Then run the command "sudo newaliases" and replace "root" with the name of the alias, "upgrades" in this example.

---

### Post by petrogazz on 2014-07-21
Nice approach, haven't thought of it . Thanks a lot!

[FONT=Verdana]
[/FONT]
[FONT=Verdana]By the way I did some testing and found out that editing[/FONT]/etc/apt/apt.conf.d/50unattended-upgrades

```
 Unattended-Upgrade::Mail "you@example.com,someone@somewhere.net";
```

or

 ```
 Unattended-Upgrade::Mail "you@example.com someone@somewhere.net";
```

does the job ):P

---

