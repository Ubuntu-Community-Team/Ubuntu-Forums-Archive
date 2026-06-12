---
title: "No Sound"
date: 2017-07-20
forum: Ubuntu/Debian BASED
---

### Post by mbott on 2017-07-20
I have an HP Pavilion G6 that with Skywave Linux I do not have any audio. I've spent the day working with all the suggestions I found with getting audio to work, but no joy.  Any assistance would be appreciated.

ALSA information is located at [http://www.alsa-project.org/db/?f=810bbcc4ad9b6d5a815fd1ef22e4257ce57495a4](http://www.alsa-project.org/db/?f=810bbcc4ad9b6d5a815fd1ef22e4257ce57495a4)

Thanks in advance,

-- 
Mike

---

### Post by oldos2er on 2017-07-20
Thread moved to *Other OS, Ubuntu/Debian Based*

---

### Post by mbott on 2017-07-26
Resolved

---

### Post by QIII on 2017-07-26
Hello!

Would you care to share how it was resolved?  The community is more than an individual resource.  It is a shared resource -- your solution might be of great value to others.

Thanks!

---

### Post by mbott on 2017-07-28
```
sudo su
apt purge --autoremove pulseaudio
rm -f /etc/asound.conf
rm -f /var/lib/alsa/asound.state
apt install pulseaudio pavucontrol paprefs
alsa force-reload
```

---

