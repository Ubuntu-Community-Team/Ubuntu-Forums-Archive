---
title: "panp7 won't resume with 12.04"
date: 2012-07-21
forum: System76 Support
---

### Post by princesshammer on 2012-07-21
After upgrade to 12.04, my panp7 won't resume. After a suspend trying to resume will turn on the fan, but otherwise it's unresponsive. Black screen. Can't access a console.

---

### Post by princesshammer on 2012-07-21
Activating the ATI proprietary driver seems to have fixed it.

Strangely, after activation, the system settings still report it as "not activated", however the xorg log shows the proprietary driver coming up.

Also the "post release updates" driver fails to install. Not sure what that's about.

---

### Post by isantop on 2012-07-24
> **princesshammer said:**
> Activating the ATI proprietary driver seems to have fixed it.

Strangely, after activation, the system settings still report it as "not activated", however the xorg log shows the proprietary driver coming up.

Also the "post release updates" driver fails to install. Not sure what that's about.

There are a couple of bugs regarding how the Additional Drivers tool checks if proprietary drivers are loaded. I'm guessing you're running into one of those.

The Updates driver failing to install must be a packaging bug, since I have the same problem on my own PanP7.

---

