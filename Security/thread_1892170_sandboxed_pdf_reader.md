---
title: "sandboxed pdf reader"
date: 2011-12-07
forum: Security
---

### Post by mrmedia on 2011-12-07
IMHO an article explaining how to sandbox a PDF reading on Ubuntu Xubuntu is needed.

---

### Post by Jive Turkey on 2011-12-07
Though it's not technically sandboxing, apparmor could be used to keep your pdf reader from getting exploited too badly.

---

### Post by Dangertux on 2011-12-07
> **Jive Turkey said:**
> Though it's not technically sandboxing, apparmor could be used to keep your pdf reader from getting exploited too badly.

This -- and also. Evince is a fairly neutred reader. IE: No support for javascript, etc. It could still be exploited as it has been in the past, however Apparmor should confine that. If you're looking for more you could explore SELinux in regards to this. Just remember Apparmor and SELinux don't really get along that well, so you'd have to get rid of Apparmor.

---

### Post by haqking on 2011-12-07
> **Dangertux said:**
> This -- and also. Evince is a fairly neutred reader. IE: No support for javascript, etc. It could still be exploited as it has been in the past, however Apparmor should confine that. If you're looking for more you could explore SELinux in regards to this. Just remember Apparmor and SELinux don't really get along that well, so you'd have to get rid of Apparmor.

+1

Also chrome/chromium has a built in .pdf viewer and so utilising chromes sandbox and is also a fairly efficient reader, you can right click on any .pdf and open with or set it to default if you dont like other readers.

Cheers

---

