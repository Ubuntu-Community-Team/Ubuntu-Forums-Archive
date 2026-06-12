---
title: "apparmour conflicts with cups-pdf?"
date: 2010-12-28
forum: Security
---

### Post by arunasr on 2010-12-28
With just the default settings, cups-pdf is not working. Kernel complains:

```
Dec 28 11:56:13 <hostname> kernel: [22362.501505] type=1400  audit(1293537373.392:2429): apparmor="DENIED" operation="mknod"  parent=16861 profile="/usr/lib/cups/backend/cups-pdf"  name="<home_dir>/PDF/<job_name>.pdf" pid=16862  comm="cp" requested_mask="c" denied_mask="c" fsuid=<uid> ouid=<uid>
```

I have PDF directory and even set the permissions to 0777 (755 used to work with karmic koala). How do I fix it?

There are also plenty of other warnings with evince thumbnailer for some reason, perhaps unrelated, but an indication that apparmour is out of step with the other applications/packages even in default setup.

---

### Post by ptn107 on 2010-12-28
The cupsd apparmor profile does not allow cups-pdf to use mknod (and why it needs to use it is beyond me), but if your're brave you can change this by editing the /etc/apparmor.d/usr.sbin.cupsd apparmor profile (make a backup first please):
```
sudo gedit /etc/apparmor.d/usr.sbin.cupsd
```

Scroll down and find the section:
```
# separate profile since this needs to write into /home
/usr/lib/cups/backend/cups-pdf {
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  capability chown,
  capability fowner,
  capability fsetid,
  capability setgid,
  capability setuid,

  # unfortunate, but required for when $HOME is 700
  capability dac_override,

  /bin/dash ixr,
  /bin/bash ixr,
  /bin/cp ixr,
  /etc/papersize r,
  /etc/cups/cups-pdf.conf r,
  @{HOME}/PDF/ rw,
  @{HOME}/PDF/* rw,
  /usr/bin/gs ixr,
  /usr/lib/cups/backend/cups-pdf mr,
  /usr/lib/ghostscript/** mr,
  /usr/share/** r,
  /var/log/cups/cups-pdf_log w,
  /var/spool/cups-pdf/** rw,
}
```
And add **capability mknod**  Your section now looks like this:
```
# separate profile since this needs to write into /home
/usr/lib/cups/backend/cups-pdf {
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  capability chown,
  capability fowner,
  capability fsetid,
  capability mknod,
  capability setgid,
  capability setuid,

  # unfortunate, but required for when $HOME is 700
  capability dac_override,

  /bin/dash ixr,
  /bin/bash ixr,
  /bin/cp ixr,
  /etc/papersize r,
  /etc/cups/cups-pdf.conf r,
  @{HOME}/PDF/ rw,
  @{HOME}/PDF/* rw,
  /usr/bin/gs ixr,
  /usr/lib/cups/backend/cups-pdf mr,
  /usr/lib/ghostscript/** mr,
  /usr/share/** r,
  /var/log/cups/cups-pdf_log w,
  /var/spool/cups-pdf/** rw,
}
```
Save and restart apparmor.
```
sudo service apparmor restart
```

Edit: As an alternative you can disable the cupsd profile from being enforced:
```
sudo aa-complain /usr/sbin/cupsd
```

---

