---
title: "nm-applet rejects my password"
date: 2010-01-23
forum: Security
---

### Post by Sutur on 2010-01-23
As the title says, nm-applet rejects my password that I'm positive is correct.

Using a custom compiz session, 

```

#!/bin/bash
compiz &
emerald &
xfce4-panel &
gnome-power-manager &
bluetooth-applet &
gnome-do &
gksu nm-applet
#nm-applet
```

Have to use 'gksu nm-applet' because trying it as any other user rejects the password, and this results in me entering the wireless key and root password ***every time*** I boot. Can anyone help please?

---

### Post by tgeer43 on 2010-01-24
Here's something to try:

Go to System->Administration->Users and Groups. Select the user that you want to fix then select 'Properties'. Go to the 'User Privileges' tab and make sure that 'Connect to wireless and ethernet networks' is checked.
Or, if you are using a dial-up modem then make sure that 'Connect to internet using a modem' and 'Use modems' are selected.

Not certain this will help but it's definitely worth a try.

tgeer

---

### Post by Sutur on 2010-01-24
> **tgeer43 said:**
> Here's something to try:

Go to System->Administration->Users and Groups. Select the user that you want to fix then select 'Properties'. Go to the 'User Privileges' tab and make sure that 'Connect to wireless and ethernet networks' is checked.
Or, if you are using a dial-up modem then make sure that 'Connect to internet using a modem' and 'Use modems' are selected.

Not certain this will help but it's definitely worth a try.

tgeer

Could you just run the following command and click on that dialogue you're pointing me to? I need the 'terminal name' because I have a custom session (no menus, just gnome-do).

```
xprop |grep CLASS
```

Cheers!

**EDIT** Never mind, I got it. 'users-admin'.

---

### Post by Sutur on 2010-01-24
Ah, thanks mate. That did it!

---

### Post by tgeer43 on 2010-01-25
> **Sutur said:**
> Ah, thanks mate. That did it!
Glad I could help. You're quite welcome.

tgeer

---

