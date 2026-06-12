---
title: "[Virtualbox] Can't install Guest Additions after updating from 1.6 to 1.6.2"
date: 2008-06-21
forum: Virtualisation
---

### Post by wersdaluv on 2008-06-21
I had Virtualbox 1.6 then I updated to 1.6.2. I uninstalled the Guest Additions ver 1.6 then installed the ver 1.6.2. Now, I can't install the latest version of the Guest Additions.

What do I do now?

See attached screenshot for error message.

---

### Post by wersdaluv on 2008-06-21
I have an update. I installed 1.6.0 and tried to install the guest additions of the version but the same error came out.

---

### Post by Drakkor on 2008-06-22
I also had problems with that,so now I'm running v. 1.5.4,the Innotek version, and it runs great
:)

---

### Post by wersdaluv on 2008-06-22
> **Drakkor said:**
> I also had problems with that,so now I'm running v. 1.5.4,the Innotek version, and it runs great
:)
I fixed it. Apparently, it wasn't a virtualbox issue. It was my fault. I created a new windows virtual machine but it still didn't work. I figured out that whenever I disable windows services (on **msconfig**), I can't install everything. hahahaha!

---

