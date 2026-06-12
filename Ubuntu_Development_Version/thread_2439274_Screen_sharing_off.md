---
title: "Screen sharing off"
date: 2020-03-25
forum: Ubuntu Development Version
---

### Post by joaompr on 2020-03-25
Hello all
I want to enable Screen Sharing but the Sharing switch at the top-right of the window is always off. I can't switch it to on, it doesn't change state. 
What I'm I missing?
I'm using 20.04.

 [IMG]https://drive.google.com/open?id=1FthqSWh6y81_p30Qbn2iXwVEBquQ44w4[/IMG]

Thanks

---

### Post by deadflowr on 2020-03-25
*Thread moved to **Ubuntu Development Version***
Ubuntu 20.04 is still in development.

---

### Post by joaompr on 2020-03-26
Thanks for moving the thread here, I had the same issue with 19.10.

---

### Post by dino99 on 2020-03-26
Which flavour is it ? witch d/i gpu is it ? What related error/warning is logged into journalctl ?

---

### Post by joaompr on 2020-03-26
this is from my system, please note I can activate "Remote Login" but neither "Screen Sharing" or "Media Sharing"

```

root@joao-HP-Notebook:# dpkg -l '*buntu-desktop' | grep ^ii
ii  ubuntu-desktop  1.445        amd64        The Ubuntu desktop system
ii  xubuntu-desktop 2.233        amd64        Xubuntu desktop system

joao@joao-HP-Notebook:~$ glxinfo | grep "Device"
    Device: AMD KABINI (DRM 2.50.0, 5.4.0-18-generic, LLVM 9.0.1) (0x9851)


mar 26 11:48:58 joao-HP-Notebook zeitgeist-datah[2438]: zeitgeist-datahub.vala:210: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required
mar 26 11:48:58 joao-HP-Notebook systemd[1592]: Started Application launched by gnome-shell.
mar 26 11:49:00 joao-HP-Notebook /usr/lib/gdm3/gdm-x-session[1622]: (II) RADEON(0): EDID vendor "CMN", prod id 5578
mar 26 11:49:00 joao-HP-Notebook /usr/lib/gdm3/gdm-x-session[1622]: (II) RADEON(0): Printing DDC gathered Modelines:
mar 26 11:49:00 joao-HP-Notebook /usr/lib/gdm3/gdm-x-session[1622]: (II) RADEON(0): Modeline "1366x768"x0.0   76.42  1366 1434 1479 1592  768 772 779 800 +hsync -vsync (48.0 kHz eP)
mar 26 11:49:00 joao-HP-Notebook /usr/lib/gdm3/gdm-x-session[1622]: (II) RADEON(0): Modeline "1366x768"x0.0   50.95  1366 1434 1479 1592  768 772 779 800 +hsync -vsync (32.0 kHz e)
mar 26 11:49:01 joao-HP-Notebook dbus-daemon[721]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.173' (uid=1000 pid=19873 comm="gnome-control-center " label="unconfined")
mar 26 11:49:01 joao-HP-Notebook systemd[1]: Starting Hostname Service...
mar 26 11:49:01 joao-HP-Notebook dbus-daemon[721]: [system] Successfully activated service 'org.freedesktop.hostname1'
mar 26 11:49:01 joao-HP-Notebook systemd[1]: Started Hostname Service.
mar 26 11:49:31 joao-HP-Notebook systemd[1]: systemd-hostnamed.service: Succeeded.
mar 26 11:50:19 joao-HP-Notebook polkitd(authority=local)[912]: Operator of unix-session:2 successfully authenticated as unix-user:joao to gain TEMPORARY authorization for action org.gnome.controlcenter.remote-login-helper for unix-process:19873:3689243 [gnome-control-center] (owned by unix-user:joao)
mar 26 11:50:19 joao-HP-Notebook pkexec[20056]: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
mar 26 11:50:19 joao-HP-Notebook pkexec[20056]: joao: Executing command [USER=root] [TTY=unknown] [CWD=/home/joao] [COMMAND=/usr/libexec/cc-remote-login-helper enable]
mar 26 11:50:19 joao-HP-Notebook systemd[1]: Starting OpenBSD Secure Shell server...
mar 26 11:50:19 joao-HP-Notebook sshd[20087]: Server listening on 0.0.0.0 port 22.
mar 26 11:50:19 joao-HP-Notebook sshd[20087]: Server listening on :: port 22.
mar 26 11:50:19 joao-HP-Notebook systemd[1]: Started OpenBSD Secure Shell server.

```

---

### Post by joaompr on 2020-03-26
Found the solution!! I'm connecting the the wifi without password. My wifi doesn't have a password. I did change it to a protected wifi, with password, and voila I was able to turn the "Sharing Screen" on!
How can I disable this feature, I want to have a wifi without password. Any clue?
Thanks

---

