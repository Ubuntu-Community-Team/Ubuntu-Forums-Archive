---
title: "Preventing terminal login from going blank"
date: 2010-05-11
forum: Server Platforms
---

### Post by upnix on 2010-05-11
I've had a couple Ubuntu 8.04 servers hang hard with no terminal response.

After a given time the terminal login screen will go blank automatically. I'd like to prevent that from happening in order to hopefully catch any messages that get output to the screen before these hangs occur. Currently when the server hangs, I can mash the keyboard all I want, the screen stays blank.

I've tried 'setterm -powersave off -blank 0', but that doesn't seem to hold after logout.


Any idea how I might do this?


Thank you.

---

### Post by cdenley on 2010-05-11
Maybe this?
```

sudo setvesablank off

```

---

### Post by upnix on 2010-05-11
> **cdenley said:**
> Maybe this?
```

sudo setvesablank off

```

No joy.

Just to be clear, I'm logging out after running these commands.

---

### Post by windependence on 2010-05-11
Try adding following two commands to your ~/.xinitrc file: 
```
setterm -blank 0 -powersave off -powerdown 0
xset s off
```

You can also try appending these two lines in the login scripts:

```
setterm -blank 0
setterm -store
```

-Tim

---

### Post by upnix on 2010-05-11
> **windependence said:**
> Try adding following two commands to your ~/.xinitrc file: 
```
setterm -blank 0 -powersave off -powerdown 0
xset s off
```

You can also try appending these two lines in the login scripts:

```
setterm -blank 0
setterm -store
```

-Tim

Wouldn't .xinitrc only apply if I were using X? Additionally, I'm looking to have the screen not blank when no one is logged it; just sitting at a login prompt. Setting these parameters in login scripts would never get run, as no one is logged in.

---

