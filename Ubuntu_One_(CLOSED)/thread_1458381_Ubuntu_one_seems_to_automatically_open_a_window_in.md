---
title: "Ubuntu one seems to automatically open a window in chrome on startup..."
date: 2010-04-19
forum: Ubuntu One (CLOSED)
---

### Post by xaegis on 2010-04-19
UbuntuOne is launching an instance of my browser and pointing to this site: "Authenticate to https://one.ubuntu.com/" every time I log on to my computer. I thought the button that says "Connect automatically" was telling the UbuntuOne client to connect on startup not my browser. Is this the proper behavior for this?

Thanks,

---

### Post by Felix-the-Cat on 2010-04-20
That's because Ubuntu one isn't communicating with the keyring. I had this problem and to fix it I logged into the Ubuntu one web interface and removed my computer from the authorized computers list and then readded it.

---

### Post by joshuahoover on 2010-04-20
> **Felix-the-Cat said:**
> That's because Ubuntu one isn't communicating with the keyring. I had this problem and to fix it I logged into the Ubuntu one web interface and removed my computer from the authorized computers list and then readded it.

Good advice! This problem shouldn't occur but does for some users from time to time, depending on the circumstances. Another thing you may need to do prior to removing your computer from your Ubuntu One account is:

1. Open Applications->Accessories->Passwords and Encryption Keys
2. Right-click on the "Ubuntu One" token and select delete
3. Open Applications->Accessories->Terminal and run:
killall ubuntuone-client-applet ubuntuone-login ubuntuone-preferences ubuntuone-syncdaemon
4. Open Ubuntu One (either Applications->Internet->Ubuntu One or System->Preferences->Ubuntu One - depends on what version you have)
5. Add your computer when prompted in your web browser

Thank you,

Joshua

---

### Post by xaegis on 2010-04-20
That fixed it guys! Thank you soo much!
:)

---

