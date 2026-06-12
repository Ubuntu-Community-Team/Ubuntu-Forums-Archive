---
title: "Shutdown and reboot"
date: 2012-02-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by chrismine on 2012-02-19
For a while now shutdown, logoff and reboot does not work from the unity menu.

I am using the sudo reboot and sudo poweroff command from terminal.

Is somebody else experiencing this or can suggest a possible fix?

Thank you.

---

### Post by ArtLaForge on 2012-02-19
> **chrismine said:**
> For a while now shutdown, logoff and reboot does not work from the unity menu.

I am using the sudo reboot and sudo poweroff command from terminal.

Is somebody else experiencing this or can suggest a possible fix?

Thank you.


No problems here... I have three computers running 12.04 one upgraded from the early toolchain, one fresh install from alpha 1 and one fresh install from an early Feb daily.  None of them have had the symptoms your experiencing.

---

### Post by matt_symes on 2012-02-19
Hi

> **chrismine said:**
> For a while now shutdown, logoff and reboot does not work from the unity menu.

I am using the sudo reboot and sudo poweroff command from terminal.

Is somebody else experiencing this or can suggest a possible fix?

Thank you.

Is it a dbus issue ?

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

Do these commands shutdown and restart from the command line ?

Kind regards

---

### Post by chrismine on 2012-02-19
It works...

---

### Post by Milos_SD on 2012-02-19
I have the same problem. But I do it a little diferently. First quit all applications, then restart X (ctrl+alt+backspace), and then restart or shutdown from login screen. :)
From my expiriance, this was happening a lot in development versions of Ubuntu.

---

### Post by matt_symes on 2012-02-19
Hi

> **chrismine said:**
> It works...

From the terminal type

```
/usr/lib/indicator-session/gtk-logout-helper --shutdown
```

Are there any error messages displayed if you hit shutdown or restart ?

Kind regards

---

### Post by rburkartjo on 2012-02-20
working fine on my end

---

### Post by chrismine on 2012-02-20
> **matt_symes said:**
> Hi



From the terminal type

```
/usr/lib/indicator-session/gtk-logout-helper --shutdown
```Are there any error messages displayed if you hit shutdown or restart ?

Kind regards
No error messages - the dialogue box appears and when I click on shutdown and restart nothing happens..

Thanks.

---

### Post by prusswan on 2012-02-20
are you using a fresh install of 12.04, or upgrade from previous release?

---

### Post by chrismine on 2012-02-20
I cannot remember, post possibly and upgrade...

It use to work with this install...

---

### Post by matt_symes on 2012-02-20
Hi

Policy kit maybe ?

What's the output of

```
cat /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
```

Kind regards

---

### Post by chrismine on 2012-02-20
Here it is:
Thanks.

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">

<!--
Policy definitions for ConsoleKit
-->

<policyconfig>

  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.stop-multiple-users">
    <description>Stop the system when multiple users are logged in</description>
    <message>System policy prevents stopping the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart">
    <description>Restart the system</description>
    <message>System policy prevents restarting the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart-multiple-users">
    <description>Restart the system when multiple users are logged in</description>
    <message>System policy prevents restarting the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

</policyconfig>

---

### Post by matt_symes on 2012-02-20
Hi

That looks fine. What's the output of

```
ps aux | grep polkit
```

and

```
grep -i "org.freedesktop.ConsoleKit" /var/log/syslog
```

Kind regards

---

### Post by chrismine on 2012-02-20
Here it comes, thanks:

root       908  0.0  0.1 195492  4132 ?        Sl   08:17   0:00 /usr/lib/policykit-1/polkitd --no-debug
chrisjan  1925  0.0  0.2 227972  9020 ?        Sl   08:28   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
chrisjan 24524  0.0  0.0   9372   932 pts/1    S+   20:44   0:00 grep --color=auto polkit

The second one gives no results..

---

### Post by gIosoli on 2012-02-21
The same problem occurs for me. In btw, maybe you are using FGLRX l drivers like meand they may be the cause some problems ?

---

### Post by nrundy on 2012-02-21
Had this problem on 11.10. I'll check 12.04 later today.

---

### Post by matt_symes on 2012-02-21
Hi

> **chrismine said:**
> Here it comes, thanks:

root       908  0.0  0.1 195492  4132 ?        Sl   08:17   0:00 /usr/lib/policykit-1/polkitd --no-debug
chrisjan  1925  0.0  0.2 227972  9020 ?        Sl   08:28   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
chrisjan 24524  0.0  0.0   9372   932 pts/1    S+   20:44   0:00 grep --color=auto polkit

The second one gives no results..

From my machine, after deleting syslog and then a reboot...

```
matthew@matthew-Aspire-7540:~$ grep -i "org.freedesktop.ConsoleKit" /var/log/syslog
Feb 21 21:46:09 matthew-Aspire-7540 dbus[1031]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Feb 21 21:46:09 matthew-Aspire-7540 dbus[1031]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
matthew@matthew-Aspire-7540:~$ 
```

You are not seeing this ?

@nrundy

> Had this problem on 11.10. I'll check 12.04 later today.

Check this on both machines and report back whether you can shudown/reboot on either or both installations please.

Kind regards

---

### Post by teeedubb on 2012-03-22
Ive been having this problem too. I made a post before I found this one, here is the link. [http://ubuntuforums.org/showthread.php?p=11786714#post11786714](http://ubuntuforums.org/showthread.php?p=11786714#post11786714)

```
ps aux | grep polkit
root      1160  0.0  0.0 195188  3700 ?        Sl   14:13   0:00 /usr/lib/policykit-1/polkitd --no-debug
xbmc      1567  0.0  0.0   9396   872 pts/0    S+   14:18   0:00 grep polkit

``````
grep -i "org.freedesktop.ConsoleKit" /var/log/syslog
Mar 23 14:13:58 blaster dbus[829]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Mar 23 14:13:58 blaster dbus[829]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
``````
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart
```Reboots the system when run as sudo.


As noted in my other post everything is fine after I restart X. Perhaps try killing X/gdm/lightdm/etc and seeing if that helps...

---

### Post by matt_symes on 2012-03-23
Hi

@teeedubb

Have you considered stracing gtk-logout-helper ?

Kind regards

---

