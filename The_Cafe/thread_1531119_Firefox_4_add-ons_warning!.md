---
title: "Firefox 4 add-ons warning!"
date: 2010-07-14
forum: The Cafe
---

### Post by lovinglinux on 2010-07-14
Since there is already users trying Firefox 4 Beta, I thought would by wise to leave a warning for add-ons users.

Usually when Firefox releases a new major version, we can override the extension compatibility check to force incompatible extensions to work with the new Firefox version. The problem is that Firefox 4 introduced some radical changes in the add-ons manager, as you can see from the new manager design. These changes will probably break several add-ons if you disable the compatibility check.

For example, some extensions might appear to be working with compatibility check disabled, but they could have issues with updates or could even break other extensions. 

So if you are using Firefox 4, I would recommend using a separate profile or do not disable compatibility check, until all your extensions are updated to work with it properly.

---

### Post by Ctrl-Alt-F1 on 2010-07-14
Interesting.  Thanks for the info.

---

### Post by lovinglinux on 2010-07-14
> **Ctrl-Alt-F1 said:**
> Interesting.  Thanks for the info.

You are welcome. Keep in mind this doesn't happen with all extensions. Nevertheless, this is the only issue I was able to find so far, but there are other important changes in the extension API that could cause other issues.

I'm barely starting to update my extensions to work with FF 4, so I didn't noticed other problems yet.

---

### Post by The Real Dave on 2010-07-14
Hmmmm...I think I'll just leave Firefox decide, and not attempt to force them to work. Adblock, DownloadHelper and Download Statusbar are the ones I need most, and they still work.

I'm enjoying using Firefox 4B1, and I've grown quite fond of tabs on top :)

---

### Post by Yarui on 2010-07-14
So the updates are the only part that seem to be incompatible?  You said the add-ons would appear to be working even though they may not be, which sounds to me like you are saying there are functionality issues.

---

### Post by lovinglinux on 2010-07-21
> **Yarui said:**
> So the updates are the only part that seem to be incompatible?

No. That is just one issue I could find when testing the extensions I develop. But there are other issues. For example, FoxTab works with compatibility check disabled and doesn't seem to have update issues, but it interferes with other extensions, causing javascript errors on them.

> **Yarui said:**
> You said the add-ons would appear to be working even though they may not be, which sounds to me like you are saying there are functionality issues.

If you install Firefox 4 and use a new clean user profile, those extensions might not even work with compatibility check disabled, because some of them need to create additional files when they launch for the first time, for example databases. If you use your current Firefox user profile, they could work, because those extra files were created when you first launched the extension with Firefox 3.x. 

The update issue is that some extensions create additional files or modify their existing databases when updated. This won't happen if the update is not fully compatible with FF4. If you get an update that is already compatible with FF 4, then no problem, but if you get an important update that is not compatible with FF 4, then this update will probably fail if it involves creating new files and modifying databases.

Bottom line, to be safe, do not bypass extension compatibility check. Leave the extensions that are incompatible disabled or use a clean profile for testing.

That being said...I'm currently testing all 60 extensions I have installed and some of them work fine with compatibility check disabled. On the other hand, there are some extensions that makes the browser unusable and I have to start it in safe mode to fix it.

Keep in mind this only affects extensions that hasn't been updated to work with Firefox 4 and are forced to work by disabling compatibility check (I have changed my first post to make this clear).

---

### Post by Khakilang on 2010-07-21
I think I wait for the full version instead once everything been sorted out.

---

### Post by lovinglinux on 2010-07-22
> **Khakilang said:**
> I think I wait for the full version instead once everything been sorted out.

I tried to use it with compatibility check disabled, but got lots of problems and had to disable most of the extensions I use. Several extensions that are not compatible yet were interacting badly with other extensions, breaking them completely.

---

