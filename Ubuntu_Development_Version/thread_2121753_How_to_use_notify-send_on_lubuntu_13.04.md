---
title: "How to use notify-send on lubuntu 13.04?"
date: 2013-03-02
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2013-03-02
I tried to use notify-send command on lubuntu 13.04 but i get this:

```
notify-send Test "Hello World"                    
zsh: command not found: notify-send
```

Same thing with xfce4-notifyd-config command:

[IMG][IMG]http://i.imgur.com/BUt16A4l.png[/IMG][/IMG]

---

### Post by kostkon on 2013-03-02
notify-send is provided by [libnotify-bin]("http://packages.ubuntu.com/raring/libnotify-bin"). Do you have it?

---

### Post by serdotlinecho on 2013-03-03
> **kostkon said:**
> notify-send is provided by [libnotify-bin]("http://packages.ubuntu.com/raring/libnotify-bin"). Do you have it?

I followed this [tutorial]("http://ubuntuforums.org/showthread.php?t=1411620") and installed notify-osd instead   ](*,)

@kostkon, Thank you very much for your help.

---

