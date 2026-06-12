---
title: "Is Mir already in?"
date: 2015-06-02
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-06-02
I was trying to remove the dots in the old way, using dconf-editor. Dconf-editor got installed, but trying to open it through lightdm, I got this; ```
/root$ dconf-editor No protocol specified  ** (dconf-editor:16116): WARNING **: Could not open X display No protocol specified gdk_mir_display_open Failed to connect to Mir: Failed to connect to server socket: No such file or directory Unable to init server: Could not connect: Connection refused  (dconf-editor:16116): Gtk-WARNING **: cannot open display: :0 
```  How to find out, if I am using Mir in the terminal? This is today's Ubuntu daily. Installed it 6 hours ago.  EDIT: It is Mir. ```
$  ps afx | grep unity-system-compositor 16204 pts/7    S+     0:00          |       \_ grep --color=auto unity-system-compositor
```

---

### Post by zika on 2015-06-02
> **Chanath said:**
> I was trying to remove the dots in the old way, using dconf-editor. Dconf-editor got installed, but trying to open it through lightdm, I got this; ```
/root$ dconf-editor
No protocol specified

** (dconf-editor:16116): WARNING **: Could not open X display
No protocol specified
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(dconf-editor:16116): Gtk-WARNING **: cannot open display: :0

```

How to find out, if I am using Mir in the terminal?
This is today's Ubuntu daily. Installed it 6 hours ago.

EDIT: _It is Mir_.
```
$  ps afx | [COLOR=#8b4513]grep unity-system-compositor[/COLOR]
16204 pts/7    S+     0:00          |       \_ [COLOR=#8b4513]grep [/COLOR]--color=auto[COLOR=#8b4513] unity-system-compositor[/COLOR]
```No it is not. It is poor grep trying to find nonexistent Mir...
[Again]("http://ubuntuforums.org/showthread.php?t=2125215&p=12563559#post12563559")... ;)

---

### Post by grahammechanical on 2015-06-02
I do not think so. I get the same result from that command and I know for sure that I do not have unity-system-compositor installed or Unity8-desktop-session-mir or anything like that.

Regards.

---

### Post by zika on 2015-06-02
> **grahammechanical said:**
> I do not think so. I get the same result from that command and I know for sure that I do not have unity-system-compositor installed or Unity8-desktop-session-mir or anything like that.

Regards.And You should since at Your place the same grep is trying to find nonexistant Mir... ;)
Does this make it more clear:```
:~$ ps afx | [COLOR=#ff8c00]grep systemd[/COLOR]  
  234 ?        Ss     0:01 /lib/systemd/systemd-journald
  257 ?        Ss     0:00 /lib/systemd/systemd-udevd
  579 ?        Ss     0:00 /lib/systemd/systemd-logind
  629 ?        Ss     0:03 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
 1015 ?        Ss     0:00 /lib/systemd/systemd --user
 1248 ?        Ss     0:00 /lib/systemd/systemd --user
19780 pts/0    S+     0:00      \_ [COLOR=#ff8c00]grep [/COLOR]--color=auto[COLOR=#ff8c00] systemd[/COLOR]

```? Hint: [B]pts (Pseudo-TerminalSlave)

[/B]Back on topic: Trouble(s) that OP encounters with dconf-editor are solved upstream quite some time ago...```
:~$ dconf-editor

** (dconf-editor:19916): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends


** (dconf-editor:19916): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends


** (dconf-editor:19916): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends
```Works nicely...

Ups: Mea culpa: I thought that DCE was topic, I've seen just now that Mir is (again) topic. Sorry... ;)

---

### Post by Chanath on 2015-06-02
OK guys, Mir is not in. My question was whether it is in.
Anyway, would you tell me how to get rid of the dots, with or without using the Dconf-editor?
Thanks!

---

### Post by Chanath on 2015-06-02
OK guys, I got it done. For those, who needs this;```
xhost +
sudo su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-grid false
exit
```

Actually, I was sort of happy to see Mir in, but...:p

---

