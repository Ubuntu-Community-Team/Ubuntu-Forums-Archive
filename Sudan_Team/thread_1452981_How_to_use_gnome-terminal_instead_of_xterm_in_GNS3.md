---
title: "How to use gnome-terminal instead of xterm in GNS3"
date: 2010-04-12
forum: Sudan Team
---

### Post by zero-n on 2010-04-12
If you don't know what is GNS3 then follow [[COLOR=Red]**THIS**[/COLOR]]("http://gns3.net/") link. :-k

now let's move to our topic.

i really hate xterm so i prefer to use gnome-terminal to access devices in GNS3 so what you need to do if you hate it too is :


1- In GNS3 go to [COLOR=Red]**Edit**[/COLOR] >> [COLOR=Red][B]Preferences

[/B][COLOR=Black]2- In the right you will the following beneath the [COLOR=Red]**Terminal command**[/COLOR]: 
```

xterm -T %d -e 'telnet %h %p' >/dev/null 2>&1 &

```[/COLOR][/COLOR]
Replace it with:
[COLOR=Red][COLOR=Black]```

gnome-terminal --command='telnet %h %p' >/dev/null 2>&1 &

```[/COLOR][/COLOR]3- we are done now ( enjoy your lovely terminal :popcorn: )

---

