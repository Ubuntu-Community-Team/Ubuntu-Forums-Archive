---
title: "gnome-keyring-daemon and kerberos"
date: 2010-07-12
forum: Security
---

### Post by tizo_rh on 2010-07-12
I have Ubuntu 10.04 configured to login with Kerberos (as in [https://help.ubuntu.com/community/SingleSignOn#Configuring%20PAM%20and%20NSS](https://help.ubuntu.com/community/SingleSignOn#Configuring%20PAM%20and%20NSS)). Everything works fine, except gnome-keyring-daemon:

 * If I login with a local user, gnome-keyring-daemon works right. Besides, the keyring is automatically unlocked with the login password.

 * If I login with a Kerberos user:

  - The session startup is considerably slower.
  - /var/log/auth.log says something like:

```
Jul 12 19:26:21 hostname gnome-keyring-daemon[3897]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified#012Autolaunch error: X11 initialization failed.
Jul 12 19:26:21 hostname gnome-keyring-daemon[3897]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
Jul 12 19:26:22 hostname gnome-keyring-daemon[3897]: The SSH agent was already initialized
Jul 12 19:26:22 hostname gnome-keyring-daemon[3897]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
Jul 12 19:26:22 hostname polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session10 (system bus name :1.158 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale es_UY.utf8)
Jul 12 19:26:24 hostname gnome-keyring-daemon[3897]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed

```
  - If I execute a program that needs the gnome-keyring (like Evolution), is desperately slow, and it says:

```
** Message: secret service operation failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

  - If I kill all gnome-keyring-daemon (killall gnome-keyring-daemon), start a new one (gnome-keyring-daemon), and restart the application that uses the gnome-keyring, it works fine, but it ask me for the password to unlock the keyring (I think that this is the normal behaviour if gnome-keyring-daemon did not start before).

I have seen the configurations in /etc/pam.d and everything looks fine (with pam_gnome_keyring.so). Indeed, I think that if something was wrong here, the local user would not have the keyring unlocked automatically.

Any help is appreciated. Thanks very much,

tizo

---

### Post by chrisisbd on 2010-10-24
No answers but *exactly* the same problem.  I only noticed it when I ran evolution from the menus, it took 30 seconds to start, whereas when I run it from the command line it starts immediately.

I finally traced the problem to this error which only occurs when I run evolution from the menu system:-

[INDENT]** Message: secret service operation failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

[/INDENT]I *think* I know why this is too, to overcome a bug in the Gnome startup (in the way it starts gnome-keyring-daemon etc.) I have the following in my .xprofile:-

[INDENT]eval $(gnome-keyring-daemon --start)
export SSH_AUTH_SOCK
export GNOME_KEYRING_SOCKET

[/INDENT]Presumably this gets executed *after* the main X startup and so the environment for the menus etc. doesn't have the correct 'bits' for gnome-keyring etc. whereas the termnals I'm running do have the right things and evolution starts instantly without the error.

So what I need to do (and presumably anyone else seeing this problem needs to do) is to get the above few lines to execute early in the X startup process.

---

