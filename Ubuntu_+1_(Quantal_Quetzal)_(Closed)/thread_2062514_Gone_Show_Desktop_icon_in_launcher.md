---
title: "Gone Show Desktop icon in launcher?"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by wgarcia on 2012-09-25
After updating to Unity 6.6.0 the "Show Desktop" icon has disappeared from the launcher. This has happened to me in two different systems.

Is this a feature or some misconfiguration of mine?

---

### Post by jokerdino on 2012-09-25
The Show Desktop button on the launcher is not a default configuration and should not be there by default. But you can set it from CCSM if you would like it there.

---

### Post by wgarcia on 2012-09-25
Thanks jokerdino. I looked around where to enable this icon at CCSM and could not find it. Where is it please?

---

### Post by jokerdino on 2012-09-25
> **wgarcia said:**
> Thanks jokerdino. I looked around where to enable this icon at CCSM and could not find it. Where is it please?
Looks like they removed the setting to add a 'Show desktop button' along with the ability to add mounts on launcher only when it is mounted. 

File a bug report regarding this. That's all we can do at the moment.

---

### Post by wgarcia on 2012-09-25
Done!:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1056142](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1056142)

and thanks.

---

### Post by funicorn on 2012-09-25
done what ? how ?

---

### Post by jokerdino on 2012-09-25
> **funicorn said:**
> done what ? how ?
He means he filed a new bug report regarding this. 

@wgarcia Confirmed the bug for you.

---

### Post by wgarcia on 2012-10-03
They have fixed released it now, I have it already fixed in my updated Quantal. 

To get the icon back in the launcher:

Make sure you have dconf-tools installed. Open dconf-editor. Navigate to com.canonical.unity.launcher

Add "unity://desktop-icon" to "favorites". Mine looks now as:

['application://nautilus.desktop', 'unity://expo-icon', 'unity://desktop-icon', 'application://firefox.desktop', 'unity://running-apps', 'application://libreoffice-writer.desktop', 'application://libreoffice-impress.desktop', and so on

I believe you can do it also from the command line with gsettings but I don't know the exact syntax.

---

### Post by funicorn on 2012-10-03
Just confirmed the desktop-expo icon can not be manually removed from launcher, as I removed it through gsettings then it comes back immediately. Should be some schema redirected from other path.

---

### Post by jrog on 2012-10-03
> **wgarcia said:**
> They have fixed released it now, I have it already fixed in my updated Quantal. 

To get the icon back in the launcher:

Make sure you have dconf-tools installed. Open dconf-editor. Navigate to com.canonical.unity.launcher

Add "unity://desktop-icon" to "favorites". Mine looks now as:

['application://nautilus.desktop', 'unity://expo-icon', 'unity://desktop-icon', 'application://firefox.desktop', 'unity://running-apps', 'application://libreoffice-writer.desktop', 'application://libreoffice-impress.desktop', and so on

I believe you can do it also from the command line with gsettings but I don't know the exact syntax.
Hm... Not exactly a boon for usability.

---

