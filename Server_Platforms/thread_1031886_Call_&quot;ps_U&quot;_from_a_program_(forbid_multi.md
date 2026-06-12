---
title: "Call &quot;ps U&quot; from a program (forbid multiple shell conn)"
date: 2009-01-05
forum: Server Platforms
---

### Post by jersak on 2009-01-05
I am writing a shell for users wich are using a tunneling service i'm providing. The problem i'm facing now is that i dont want multiple connections using the same login (username).

So i thought in calling a "ps U {username}" upon the start of the shell, and if the ps returns a positive for that user, the shell shows a message and terminates.

Is this possible? Do you have any other options i could use to forbid multiple connections from the same user?

Hope you can help me and thanks in advance.

---

### Post by scorp123 on 2009-01-06
Why not work with the ***MaxSessions*** parameter in **/etc/ssh/sshd_config**?

---

### Post by scorp123 on 2009-01-06
Oh, and I found this .... maybe this would be something for you?

"Using iptables to rate-limit incoming connections"
[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

You could use the built-in "iptables" firewall to limit the number of connections that originate from the same IP ....

---

### Post by scorp123 on 2009-01-06
Found yet another way :)

EDIT: 

--- don't do this: ---

"Limit SSH users with PAM"
[http://www.linuxweblog.com/limit-users-pam](http://www.linuxweblog.com/limit-users-pam)

--- wwwwwaaaay too complicated ---


I found one really easy way:
[http://lists.trustix.org/pipermail/tsl-discuss/2005-June/014440.html](http://lists.trustix.org/pipermail/tsl-discuss/2005-June/014440.html)
[http://lists.trustix.org/pipermail/tsl-discuss/2005-June/014443.html](http://lists.trustix.org/pipermail/tsl-discuss/2005-June/014443.html)

So you'd manipulate this file:

**/etc/security/limits.conf**  ... and make sure you limit your users to one login via the ***[COLOR="Blue"]maxlogins[/COLOR]*** directive! :D
```
@users	-	maxlogins	1
@admin	-	maxlogins	10
```

Then in **/etc/ssh/sshd_config** make sure sshd uses PAM:
```
UsePam = yes
```

Restart SSH:
```
sudo /etc/init.d/ssh restart
```

Voila, done.
.
.
.

---

### Post by jersak on 2009-01-06
Thanks a lot dude! This worked perfectly.
I always seem to look for the wrong solution for my problemas :D

---

