---
title: "Giving users rights to change date time"
date: 2012-06-25
forum: Security
---

### Post by Twelveone on 2012-06-25
Hi,

We use Ubuntu to run a system we manufacture and we'd rather not give the end user access to all the root commands, so we setup a basic user account for them to run the system from. The systems are now selling worldwide and we need to give the end user the ability to set the date/time. Since the end users are typically not software or IT engineers we would like them to use the time-admin gui. Can anyone tell me how to either give a specific user or all users access to unlock the time-admin gui?

Thanks

Stewart

---

### Post by zombifier25 on 2012-06-26
Open /usr/share/polkit-1/actions/org.gnome.settingsdaemon.datetimemechanism.policy as root, and modify this part:
```
  <action id="org.gnome.settingsdaemon.datetimemechanism.configure">
    <description gettext-domain="gnome-settings-daemon">Change system time and date settings</description>
    <message gettext-domain="gnome-settings-daemon">To change time or date settings, you need to authenticate.</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

```
to this:
```
  <action id="org.gnome.settingsdaemon.datetimemechanism.configure">
    <description gettext-domain="gnome-settings-daemon">Change system time and date settings</description>
    <message gettext-domain="gnome-settings-daemon">To change time or date settings, you need to authenticate.</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>
  </action>

```

---

