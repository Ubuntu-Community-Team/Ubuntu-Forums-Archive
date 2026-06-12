---
title: "firestarter start on login and stop on logoff"
date: 2008-12-08
forum: Security
---

### Post by santhoshsd on 2008-12-08
Hi,

I have installed firestarter and configured the rules.
I created a new user
How do I make sure that firestarter starts when the user logs in and stop when user logs off.

thanks

---

### Post by cdenley on 2008-12-08
> **santhoshsd said:**
> Hi,

I have installed firestarter and configured the rules.
I created a new user
How do I make sure that firestarter starts when the user logs in and stop when user logs off.

thanks

Do you mean the configuration/status windows, or the actual firewall. The actual firewall (iptables) is always running in ubuntu. Rules created for firestarter (iptables) are not user-specific. If you want to create user-specific rules, you would need to use the owner module in iptables. I doubt firestarter can configure with that module.

---

### Post by hyper_ch on 2008-12-08
you don't need to "start" firestarter....

---

### Post by MarblePanther on 2008-12-08
You are in the windows mindset

Ubuntu comes configured with a packetfilter/firewall called iptables (this is integrated--no "off")

Firestarter is simply a gui frontend for creating rules

No worries

---

### Post by santhoshsd on 2008-12-09
i checked that i can start and stop firestarter with the following commands

/etc/init.d/firestarter start
/etc/init.d/firestarter stop

I want to put the '/etc/init.d/firestarter start' in the user login script and '/etc/init.d/firestarter stop' user logout script.
I know firewall rules set by firestarter are not user-specific.
Its not a problem.

how can I set this up.

thanks

---

### Post by cdenley on 2008-12-09
> **santhoshsd said:**
> i checked that i can start and stop firestarter with the following commands

/etc/init.d/firestarter start
/etc/init.d/firestarter stop

I want to put the '/etc/init.d/firestarter start' in the user login script and '/etc/init.d/firestarter stop' user logout script.
I know firewall rules set by firestarter are not user-specific.
Its not a problem.

how can I set this up.

thanks

You can't. The user logon script is run as the user. You could allow that user to run the script as root without a password, but I wouldn't recommend it. What are you trying to accomplish?

---

### Post by santhoshsd on 2008-12-10
Basically, all I want to do is I want to execute a command when a user logs in and logs off.

In which startup/shutdown script should I add the command?

---

### Post by cdenley on 2008-12-10
> **santhoshsd said:**
> Basically, all I want to do is I want to execute a command when a user logs in and logs off.

In which startup/shutdown script should I add the command?

logon script:
```

/etc/gdm/PreSession/Default

```

logoff script:
```

/etc/gdm/PostSession/Default

```

---

### Post by santhoshsd on 2008-12-10
What if the user logs in using ssh ?

Appending the command to /etc/gdm/PreSession/Default will it still work. I did not try but I think it will not work because /etc/gdm/PreSession/Default will be executed only when users login through 
the UI(gnome)

---

### Post by cdenley on 2008-12-10
> **santhoshsd said:**
> What if the user logs in using ssh ?

Appending the command to /etc/gdm/PreSession/Default will it still work. I did not try but I think it will not work because /etc/gdm/PreSession/Default will be executed only when users login through 
the UI(gnome)

That is correct. I don't think there is a logoff script for terminal logins. Maybe you can create a replacement shell script for the user which runs your login command, starts /bin/bash, then runs your logoff command. Otherwise, ~/.profile is run when a user logs in.

---

