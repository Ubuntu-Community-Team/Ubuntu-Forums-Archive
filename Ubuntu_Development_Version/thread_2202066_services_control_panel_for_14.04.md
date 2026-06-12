---
title: "services control panel for 14.04"
date: 2014-01-27
forum: Ubuntu Development Version
---

### Post by nomenkultur2 on 2014-01-27
bear with me since this issue has plagued every single OS I have ever used.

 Back in the days of XP it was fairly easy to disable the services you had not the need for since the list was fairly minimal. In 7/8 it is an exercise in torture but it remains possible.

 I attempted to do this in the 13.04 dev install, I was sucessful but it was quite complex since I had to use sysrv something in the terminal and then another for upstart etc...

 I'm posting this because I saw a beautiful example of a services control panel in a small and unknown debian based italian distro, they make it so easy to disable stuff like cups etc that I had to show it:

[IMG]http://tallinux.altervista.org/blog/wp-content/uploads/2014/01/semplice6-23.png[/IMG]



 I would suggest having the ability to disable not only stuff like cups/bluetooth but also video photo scopes and indicator-keyboard-service and printer-service etc... (pretty much all the bloat like scopes and indicators and non essential stuff). If you could integrate that in the 'System monitor' app it would be terrific

---

### Post by cariboo on 2014-01-27
You can disable some services with gnome-session-properties, run the following two commands:

```
cd /etc/xdg/autostart/
```

then

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

Once the commands have run start up gnome-sessions-properties. The result looks like the screenshot on my system.

---

### Post by QDR06VV9 on 2014-01-27
> **cariboo907 said:**
> You can disable some services with gnome-session-properties, run the following two commands:

```
cd /etc/xdg/autostart/
```

then

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

Once the commands have run start up gnome-sessions-properties. The result looks like the screenshot on my system.

So cariboo907 Dose this command not work anymore?
```
[COLOR=#333333][FONT=UbuntuMono]sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop[/FONT][/COLOR]
```

---

### Post by cariboo on 2014-01-27
I do believe that -i and --in-place are the same thing. I'm by no means a sed expert, and I have quite a few commands and hints and tips saved in [Zim]("http://zim-wiki.org/")

---

### Post by QDR06VV9 on 2014-01-27
> **cariboo907 said:**
> I do believe that -i and --in-place are the same thing._** I'm by no means a sed expert**_, and I have quite a few commands and hints and tips saved in [Zim]("http://zim-wiki.org/")
Ok Thanks. No sed expert here either.:D

---

### Post by CharlesA on 2014-01-27
> **cariboo907 said:**
> I do believe that -i and --in-place are the same thing. I'm by no means a sed expert, and I have quite a few commands and hints and tips saved in [Zim]("http://zim-wiki.org/")

Just confirming that. I use -i all the time. :)

---

### Post by nomenkultur on 2014-01-27
Much appreciated cariboo, that's a simple way to get rid of some of the indicators, desktop sharing and stuff I don't want.

   Edit: disregard that  I found it

[https://apps.ubuntu.com/cat/applications/sysv-rc-conf/](https://apps.ubuntu.com/cat/applications/sysv-rc-conf/)

 let's try to brick 14.04   >:)

---

