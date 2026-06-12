---
title: "WebDAV: mountable but empty below 2nd subdir level"
date: 2011-07-03
forum: Server Platforms
---

### Post by CDrewing on 2011-07-03
Hi,

I am using Safesync from Trendmicro to backup my data. Since some time I am experiencing heavy problems. Normally my Backup should look like this:

[IMG]http://img841.imageshack.us/img841/4834/bildschirmfoto6d.png[/IMG]

But when I am mounting it with WebDAV, it is looking different:

```
cdrewing@christian-desktop:~$ sudo mount -t davfs http://dav.trendmicro.safesync.com /media/Safesync
[sudo] password for cdrewing: 
Gib bitte den Benutzernamen für den Server http://dav.trendmicro.safesync.com an; wenn du keinen angeben willst, drücke Return.
  Benutzername: ***.com
Gib bitte das Passwort von ***.com für den Server http://dav.trendmicro.safesync.com
an; wenn du keines angeben willst, drücke Return.
  Passwort: 
/sbin/mount.davfs: Warnung: der Server kann Dateien nicht sperren
cdrewing@christian-desktop:~$ ls /media/Safesync/
backup  EncFS  home  lost+found  Manuel
cdrewing@christian-desktop:~$ ls /media/Safesync/home
Bilder  Dokumente  Hörspiele  Musik  Videos
cdrewing@christian-desktop:~$ ls /media/Safesync/home/Musik
cdrewing@christian-desktop:~$ 

```

As you can see, everything seems to be all right. But when you go deeper to the third dirlevel, everything is empty! :(

Can anybody help me with this? I did not have this problem all the time. Which means: it used to work this way before. The problem above came up around April 2011.

Thank you for your time & help.

Regards
Christian


**Note: **When I am mounting Safesync with Nautilus, everything is functional and ok. But I need my command line access because I want to use rsync. A workaround could be to access the resource via the nautilus mount. Where can I find this via the command line?

---

### Post by rudelgurke on 2011-07-04
Didn't got a reply:

[http://askubuntu.com/questions/51631/webdav-mount-is-empty-below-second-subdir-level](http://askubuntu.com/questions/51631/webdav-mount-is-empty-below-second-subdir-level)

there ?

Well - maybe try mounting with the debug option and check your log. :)
Might give some useful info.

---

