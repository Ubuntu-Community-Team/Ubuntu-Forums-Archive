---
title: "screen saver"
date: 2009-01-06
forum: Server Platforms
---

### Post by orudie on 2009-01-06
In ubuntu 8.10 server, how do i prevent the screen from going blank after a while ?

---

### Post by kaibob on 2009-01-06
I'm not familiar with Ubuntu server but in other versions the following placed at the end of the xorg.conf file stops the screen blanking:

```
Section "ServerFlags"
	Option	"BlankTime"	"0"
	Option	"StandbyTime"	"0"
	Option	"SuspendTime"	"0"
	Option	"OffTime"	"0"
EndSection
```

---

