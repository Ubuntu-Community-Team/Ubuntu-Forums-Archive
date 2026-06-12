---
title: "Can not login because of permanent restart"
date: 2013-08-22
forum: Virtualisation
---

### Post by drakes on 2013-08-22
I have virtual server using VirtualBox on Ubuntu 10.04 with two virtual servers, both Ubuntu 10.04. From this day I can not login to one virtual server.

When I try to login using ssh, I am disconnected with message: "The system is going down for reboot in 1 minute!" But the system never goes down and when I restart everything, it do not help. Everything on the virtual server is running fine, but I can not access it, install new applications and so on.

I tried to restart both virtual machine and the server virtual machine is running on. No effect.

Any ideas how to login to permanently restarting virtual server? Maybe use something else then ssh?

Thanks for any advice, google does not help with this problem.

---

### Post by Habitual on 2013-08-22
have you restarted the VirtualBox appliance since this started happening?
Any affect if you did?

---

### Post by drakes on 2013-08-23
> **Habitual said:**
> have you restarted the VirtualBox appliance since this started happening?
Any affect if you did?

Yes, I tried to restart both virtual machine and the server virtual machine is running on. No effect.

---

### Post by Habitual on 2013-08-23
Have you tried ssh as another user?
What ssh user are you getting this message with?

What I'm really asking is "are you ssh'ing in as root or not?"

---

### Post by drakes on 2013-08-23
> **Habitual said:**
> Have you tried ssh as another user?

No, I have access for only one user.

> **Habitual said:**
> 
What I'm really asking is "are you ssh'ing in as root or not?"

Im not logging as root, I do not know root password. I just have one user with admin privileges and I use su and sudo to get root access. Is there a way to recover root password and will it help to login as root?

---

### Post by Habitual on 2013-08-23
It may help to login as root.
Recovering the root password is another matter, but if you could su  or sudo, it should be trivial to do so.

Is this owned by you?

---

### Post by drakes on 2013-08-23
Yes, the server is owned by me.

But how can I recover the root password from virtual server if I can not even login to it?

---

### Post by Habitual on 2013-08-23
but you can login to it.
There are several methods for changing a root password.
[**By default, the Root account password is locked in Ubuntu.**]("https://help.ubuntu.com/community/RootSudo")
Have you changed that behavior to allow root? This issue implies yes, but I can't make any assumptions.

Let's start with that answer and then proceed.

---

### Post by drakes on 2013-08-24
I think that there is some form of misunderstanding if you say, that I can log in as root and change it's password. So, lets summarize my problem:

1) I can not log in to system with any user. The reason is, that it is virtual server and only method I know to log in to it is by ssh. And if I try it, it disconnects me immediately with message "[COLOR=#000000]The system is going down for reboot in 1 minute!"
[/COLOR]2) Because of 1) I do not know how to reset root password.

And to answer your question, I did not change the root behavior. So the root account is still locked and I can not login to it, until I reset it's password.
[COLOR=#000000][/COLOR]
So, what I need is to find any way to login to the virtual server. Until I login to it, I can not run any commands on it and change anything.

---

### Post by steeldriver on 2013-08-24
I wonder if you can issue an immediate 'cancel shutdown' command via ssh?

```

$ ssh *user@remote_host* "sudo -S shutdown -c << EOF
*your_remote_password*
EOF"

```

Also, the fact that the shutdown is always 1 minute makes me wonder whether the shutdown command is actually inside one of your login files (.profile, .bashrc) so it might be worth trying ssh with noprofile / norc

```

ssh --noprofile --norc *user@remote_host*

```

---

### Post by drakes on 2013-08-24
Thank you for your help. The problem eventually solved itself before I could try anything. I don't know how, I didn't changed anything. But the restart problem is gone, mysteriously. I canceled the scheduled restart in crontab ([COLOR=#333333][FONT=UbuntuRegular]0 4 * * * /sbin/shutdown -r +5)[/FONT][/COLOR], so it shouldn't happen again, I hope. Another linux mystery...

---

