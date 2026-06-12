---
title: "Suspicious log or not?"
date: 2010-09-21
forum: Security
---

### Post by cguy on 2010-09-21
Is there anything suspicious about this auth.log?

I find the many CRON outputs and the part with gconftool weird.

Also, why don't I have the permission to view "/var/log/btmp1". It has never happened before.
I'm using GNOME's log viewer.

Thanks!
```
Sep 19 00:30:01 ubuntu CRON[23278]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 00:30:02 ubuntu CRON[23278]: pam_unix(cron:session): session closed for user root
Sep 19 00:40:01 ubuntu CRON[23632]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 00:40:01 ubuntu CRON[23632]: pam_unix(cron:session): session closed for user root
Sep 19 00:46:28 ubuntu gnome-keyring-daemon[3799]: removing removable location: volume_uuid_4C95_2EDD
Sep 19 00:50:01 ubuntu CRON[23905]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 00:50:01 ubuntu CRON[23905]: pam_unix(cron:session): session closed for user root
Sep 19 01:00:01 ubuntu CRON[24058]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 01:00:01 ubuntu CRON[24057]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 01:00:02 ubuntu CRON[24057]: pam_unix(cron:session): session closed for user root
Sep 19 01:00:02 ubuntu CRON[24058]: pam_unix(cron:session): session closed for user root
Sep 19 01:10:01 ubuntu CRON[24255]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 01:10:01 ubuntu CRON[24255]: pam_unix(cron:session): session closed for user root
Sep 19 01:17:01 ubuntu CRON[24394]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 01:17:01 ubuntu CRON[24394]: pam_unix(cron:session): session closed for user root
Sep 19 01:20:01 ubuntu CRON[24458]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 01:20:01 ubuntu CRON[24458]: pam_unix(cron:session): session closed for user root
Sep 19 01:30:01 ubuntu CRON[24628]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 01:30:01 ubuntu CRON[24628]: pam_unix(cron:session): session closed for user root
Sep 19 01:40:01 ubuntu CRON[24829]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 01:40:02 ubuntu CRON[24829]: pam_unix(cron:session): session closed for user root
Sep 19 01:44:31 ubuntu gnome-keyring-daemon[3799]: adding removable location: volume_uuid_4C95_4066 at /media/PHONE CARD
Sep 19 01:50:01 ubuntu CRON[25323]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 01:50:01 ubuntu CRON[25323]: pam_unix(cron:session): session closed for user root
Sep 19 01:50:40 ubuntu gnome-keyring-daemon[3799]: removing removable location: volume_uuid_4C95_4066
Sep 19 02:00:01 ubuntu CRON[25548]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 02:00:01 ubuntu CRON[25547]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 02:00:01 ubuntu CRON[25548]: pam_unix(cron:session): session closed for user root
Sep 19 02:00:01 ubuntu CRON[25547]: pam_unix(cron:session): session closed for user root
Sep 19 02:10:01 ubuntu CRON[25710]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 02:10:01 ubuntu CRON[25710]: pam_unix(cron:session): session closed for user root
Sep 19 02:17:01 ubuntu CRON[25841]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 02:17:01 ubuntu CRON[25841]: pam_unix(cron:session): session closed for user root
Sep 19 02:20:01 ubuntu CRON[25913]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 02:20:02 ubuntu CRON[25913]: pam_unix(cron:session): session closed for user root
Sep 19 02:30:01 ubuntu CRON[26080]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 02:30:01 ubuntu CRON[26080]: pam_unix(cron:session): session closed for user root
Sep 19 02:40:01 ubuntu CRON[26202]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 02:40:01 ubuntu CRON[26202]: pam_unix(cron:session): session closed for user root
Sep 19 02:50:01 ubuntu CRON[26358]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 02:50:01 ubuntu CRON[26358]: pam_unix(cron:session): session closed for user root
Sep 19 02:50:27 ubuntu gdm[3049]: pam_unix(gdm:session): session closed for user marinescu
Sep 19 13:27:07 ubuntu dbus-daemon: Rejected send message, 4 matched rules; type="error", sender=":1.11" (uid=0 pid=3097 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.8" (uid=0 pid=3074 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
Sep 19 13:28:56 ubuntu gdm[3041]: pam_unix(gdm:session): session opened for user marinescu by (uid=0)
Sep 19 13:28:56 ubuntu gdm[3041]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Sep 19 13:30:01 ubuntu CRON[3864]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 13:30:05 ubuntu CRON[3864]: pam_unix(cron:session): session closed for user root
Sep 19 13:40:01 ubuntu CRON[4131]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 13:40:01 ubuntu CRON[4131]: pam_unix(cron:session): session closed for user root
Sep 19 13:50:01 ubuntu CRON[4249]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 13:50:01 ubuntu CRON[4249]: pam_unix(cron:session): session closed for user root
Sep 19 14:00:01 ubuntu CRON[4489]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 14:00:01 ubuntu CRON[4488]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 14:00:02 ubuntu CRON[4488]: pam_unix(cron:session): session closed for user root
Sep 19 14:00:02 ubuntu CRON[4489]: pam_unix(cron:session): session closed for user root
Sep 19 14:10:01 ubuntu CRON[4664]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 14:10:01 ubuntu CRON[4664]: pam_unix(cron:session): session closed for user root
Sep 19 14:17:01 ubuntu CRON[4790]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 14:17:01 ubuntu CRON[4790]: pam_unix(cron:session): session closed for user root
Sep 19 14:20:01 ubuntu CRON[4858]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 14:20:01 ubuntu CRON[4858]: pam_unix(cron:session): session closed for user root
Sep 19 14:30:01 ubuntu CRON[5015]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 14:30:01 ubuntu CRON[5015]: pam_unix(cron:session): session closed for user root
Sep 19 14:40:01 ubuntu CRON[5290]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 14:40:02 ubuntu CRON[5290]: pam_unix(cron:session): session closed for user root
Sep 19 14:50:01 ubuntu CRON[5434]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 14:50:01 ubuntu CRON[5434]: pam_unix(cron:session): session closed for user root
Sep 19 15:00:01 ubuntu CRON[5554]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 15:00:01 ubuntu CRON[5553]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 15:00:01 ubuntu CRON[5554]: pam_unix(cron:session): session closed for user root
Sep 19 15:00:01 ubuntu CRON[5553]: pam_unix(cron:session): session closed for user root
Sep 19 15:10:01 ubuntu CRON[5674]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 15:10:01 ubuntu CRON[5674]: pam_unix(cron:session): session closed for user root
Sep 19 15:17:01 ubuntu CRON[5871]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 15:17:01 ubuntu CRON[5871]: pam_unix(cron:session): session closed for user root
Sep 19 15:20:01 ubuntu CRON[5894]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 15:20:02 ubuntu CRON[5894]: pam_unix(cron:session): session closed for user root
Sep 19 15:30:01 ubuntu CRON[6158]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 15:30:01 ubuntu CRON[6158]: pam_unix(cron:session): session closed for user root
Sep 19 15:40:01 ubuntu CRON[6311]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 15:40:01 ubuntu CRON[6311]: pam_unix(cron:session): session closed for user root
Sep 19 15:50:01 ubuntu CRON[6429]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 15:50:01 ubuntu CRON[6429]: pam_unix(cron:session): session closed for user root
Sep 19 16:00:01 ubuntu CRON[6552]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:00:01 ubuntu CRON[6553]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:00:01 ubuntu CRON[6552]: pam_unix(cron:session): session closed for user root
Sep 19 16:00:01 ubuntu CRON[6553]: pam_unix(cron:session): session closed for user root
Sep 19 16:10:01 ubuntu CRON[6691]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:10:02 ubuntu CRON[6691]: pam_unix(cron:session): session closed for user root
Sep 19 16:17:01 ubuntu CRON[6812]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:17:01 ubuntu CRON[6812]: pam_unix(cron:session): session closed for user root
Sep 19 16:20:01 ubuntu CRON[6870]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:20:01 ubuntu CRON[6870]: pam_unix(cron:session): session closed for user root
Sep 19 16:30:01 ubuntu CRON[6991]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:30:01 ubuntu CRON[6991]: pam_unix(cron:session): session closed for user root
Sep 19 16:40:01 ubuntu CRON[7109]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:40:01 ubuntu CRON[7109]: pam_unix(cron:session): session closed for user root
Sep 19 16:50:01 ubuntu CRON[7226]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 16:50:01 ubuntu CRON[7226]: pam_unix(cron:session): session closed for user root
Sep 19 17:00:01 ubuntu CRON[7353]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:00:01 ubuntu CRON[7352]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:00:01 ubuntu CRON[7352]: pam_unix(cron:session): session closed for user root
Sep 19 17:00:02 ubuntu CRON[7353]: pam_unix(cron:session): session closed for user root
Sep 19 17:10:01 ubuntu CRON[7526]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:10:01 ubuntu CRON[7526]: pam_unix(cron:session): session closed for user root
Sep 19 17:17:01 ubuntu CRON[7653]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:17:01 ubuntu CRON[7653]: pam_unix(cron:session): session closed for user root
Sep 19 17:20:01 ubuntu CRON[7668]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:20:01 ubuntu CRON[7668]: pam_unix(cron:session): session closed for user root
Sep 19 17:30:01 ubuntu CRON[7801]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:30:01 ubuntu CRON[7801]: pam_unix(cron:session): session closed for user root
Sep 19 17:40:01 ubuntu CRON[7919]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:40:01 ubuntu CRON[7919]: pam_unix(cron:session): session closed for user root
Sep 19 17:50:01 ubuntu CRON[8037]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:50:02 ubuntu CRON[8037]: pam_unix(cron:session): session closed for user root
Sep 19 18:00:01 ubuntu CRON[8226]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 18:00:01 ubuntu CRON[8227]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 18:00:01 ubuntu CRON[8226]: pam_unix(cron:session): session closed for user root
Sep 19 18:00:01 ubuntu CRON[8227]: pam_unix(cron:session): session closed for user root
Sep 19 18:10:01 ubuntu CRON[8496]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 18:10:01 ubuntu CRON[8496]: pam_unix(cron:session): session closed for user root
Sep 19 18:17:01 ubuntu CRON[8650]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 18:17:01 ubuntu CRON[8650]: pam_unix(cron:session): session closed for user root
Sep 19 18:20:01 ubuntu CRON[8666]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 18:20:01 ubuntu CRON[8666]: pam_unix(cron:session): session closed for user root
Sep 19 18:30:01 ubuntu CRON[8864]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 18:30:02 ubuntu CRON[8864]: pam_unix(cron:session): session closed for user root
Sep 19 18:32:30 ubuntu gnome-keyring-daemon[3399]: adding removable location: volume_uuid_4C96_2CA3 at /media/PHONE CARD
Sep 19 18:32:41 ubuntu gnome-keyring-daemon[3399]: removing removable location: volume_uuid_4C96_2CA3
Sep 19 18:40:01 ubuntu CRON[9534]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 18:40:01 ubuntu CRON[9534]: pam_unix(cron:session): session closed for user root
Sep 19 18:50:01 ubuntu CRON[9690]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 18:50:01 ubuntu CRON[9690]: pam_unix(cron:session): session closed for user root
Sep 19 19:00:01 ubuntu CRON[9822]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 19:00:01 ubuntu CRON[9823]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 19:00:01 ubuntu CRON[9822]: pam_unix(cron:session): session closed for user root
Sep 19 19:00:01 ubuntu CRON[9823]: pam_unix(cron:session): session closed for user root
Sep 19 19:10:01 ubuntu CRON[10013]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 19:10:02 ubuntu CRON[10013]: pam_unix(cron:session): session closed for user root
Sep 19 19:17:01 ubuntu CRON[10271]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 19:17:01 ubuntu CRON[10271]: pam_unix(cron:session): session closed for user root
Sep 19 19:20:01 ubuntu CRON[10344]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 19:20:01 ubuntu CRON[10344]: pam_unix(cron:session): session closed for user root
Sep 19 19:30:01 ubuntu CRON[10602]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 19:30:02 ubuntu CRON[10602]: pam_unix(cron:session): session closed for user root
Sep 19 19:40:01 ubuntu CRON[10932]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 19:40:02 ubuntu CRON[10932]: pam_unix(cron:session): session closed for user root
Sep 19 19:50:01 ubuntu CRON[11096]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 19:50:01 ubuntu CRON[11096]: pam_unix(cron:session): session closed for user root
Sep 19 20:00:01 ubuntu CRON[11241]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 20:00:01 ubuntu CRON[11240]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 20:00:01 ubuntu CRON[11240]: pam_unix(cron:session): session closed for user root
Sep 19 20:00:01 ubuntu CRON[11241]: pam_unix(cron:session): session closed for user root
Sep 19 20:10:01 ubuntu CRON[11425]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 20:10:01 ubuntu CRON[11425]: pam_unix(cron:session): session closed for user root
Sep 19 20:17:01 ubuntu CRON[11567]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 20:17:02 ubuntu CRON[11567]: pam_unix(cron:session): session closed for user root
Sep 19 20:20:01 ubuntu CRON[11789]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 20:20:01 ubuntu CRON[11789]: pam_unix(cron:session): session closed for user root
Sep 19 20:30:01 ubuntu CRON[12125]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 20:30:02 ubuntu CRON[12125]: pam_unix(cron:session): session closed for user root
Sep 19 20:40:01 ubuntu CRON[12395]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 20:40:01 ubuntu CRON[12395]: pam_unix(cron:session): session closed for user root
Sep 19 20:42:29 ubuntu gnome-keyring-daemon[3399]: adding removable location: volume_uuid_4C96_4B1C at /media/PHONE CARD
Sep 19 20:43:30 ubuntu gnome-keyring-daemon[3399]: removing removable location: volume_uuid_4C96_4B1C
Sep 19 20:50:01 ubuntu CRON[12775]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 20:50:01 ubuntu CRON[12775]: pam_unix(cron:session): session closed for user root
Sep 19 21:00:01 ubuntu CRON[12934]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 21:00:01 ubuntu CRON[12933]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 21:00:01 ubuntu CRON[12933]: pam_unix(cron:session): session closed for user root
Sep 19 21:00:01 ubuntu CRON[12934]: pam_unix(cron:session): session closed for user root
Sep 19 21:10:02 ubuntu CRON[13104]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 21:10:02 ubuntu CRON[13104]: pam_unix(cron:session): session closed for user root
Sep 19 21:17:01 ubuntu CRON[13241]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 21:17:01 ubuntu CRON[13241]: pam_unix(cron:session): session closed for user root
Sep 19 21:20:01 ubuntu CRON[13320]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 21:20:01 ubuntu CRON[13320]: pam_unix(cron:session): session closed for user root
Sep 19 21:30:01 ubuntu CRON[13481]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 21:30:01 ubuntu CRON[13481]: pam_unix(cron:session): session closed for user root
Sep 19 21:40:01 ubuntu CRON[13726]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 21:40:02 ubuntu CRON[13726]: pam_unix(cron:session): session closed for user root
Sep 19 21:50:01 ubuntu CRON[13889]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 21:50:01 ubuntu CRON[13889]: pam_unix(cron:session): session closed for user root
Sep 19 22:00:01 ubuntu CRON[14045]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 22:00:01 ubuntu CRON[14046]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 22:00:01 ubuntu CRON[14045]: pam_unix(cron:session): session closed for user root
Sep 19 22:00:01 ubuntu CRON[14046]: pam_unix(cron:session): session closed for user root
Sep 19 22:10:01 ubuntu CRON[14219]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 22:10:01 ubuntu CRON[14219]: pam_unix(cron:session): session closed for user root
Sep 19 22:17:01 ubuntu CRON[14355]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 22:17:01 ubuntu CRON[14355]: pam_unix(cron:session): session closed for user root
Sep 19 22:20:01 ubuntu CRON[14422]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 22:20:02 ubuntu CRON[14422]: pam_unix(cron:session): session closed for user root
Sep 19 22:30:01 ubuntu CRON[14642]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 22:30:01 ubuntu CRON[14642]: pam_unix(cron:session): session closed for user root
Sep 19 22:40:01 ubuntu CRON[14767]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 22:40:01 ubuntu CRON[14767]: pam_unix(cron:session): session closed for user root
Sep 19 22:50:01 ubuntu CRON[14987]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 22:50:01 ubuntu CRON[14987]: pam_unix(cron:session): session closed for user root
Sep 19 23:00:01 ubuntu CRON[15160]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 23:00:01 ubuntu CRON[15159]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 23:00:01 ubuntu CRON[15159]: pam_unix(cron:session): session closed for user root
Sep 19 23:00:01 ubuntu CRON[15160]: pam_unix(cron:session): session closed for user root
Sep 19 23:10:01 ubuntu CRON[15314]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 23:10:01 ubuntu CRON[15314]: pam_unix(cron:session): session closed for user root
Sep 19 23:17:01 ubuntu CRON[15482]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 23:17:01 ubuntu CRON[15482]: pam_unix(cron:session): session closed for user root
Sep 19 23:20:01 ubuntu CRON[15569]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 23:20:01 ubuntu CRON[15569]: pam_unix(cron:session): session closed for user root
Sep 19 23:30:01 ubuntu CRON[15799]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 23:30:01 ubuntu CRON[15799]: pam_unix(cron:session): session closed for user root
Sep 19 23:40:01 ubuntu CRON[16082]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 23:40:01 ubuntu CRON[16082]: pam_unix(cron:session): session closed for user root
Sep 19 23:50:01 ubuntu CRON[16250]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 23:50:02 ubuntu CRON[16250]: pam_unix(cron:session): session closed for user root
Sep 20 00:00:01 ubuntu CRON[16383]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:00:01 ubuntu CRON[16382]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:00:01 ubuntu CRON[16384]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:00:01 ubuntu CRON[16383]: pam_unix(cron:session): session closed for user root
Sep 20 00:00:01 ubuntu CRON[16384]: pam_unix(cron:session): session closed for user root
Sep 20 00:00:01 ubuntu CRON[16382]: pam_unix(cron:session): session closed for user root
Sep 20 00:10:01 ubuntu CRON[16529]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:10:01 ubuntu CRON[16529]: pam_unix(cron:session): session closed for user root
Sep 20 00:17:01 ubuntu CRON[16661]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:17:01 ubuntu CRON[16661]: pam_unix(cron:session): session closed for user root
Sep 20 00:20:01 ubuntu CRON[16722]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:20:01 ubuntu CRON[16722]: pam_unix(cron:session): session closed for user root
Sep 20 00:30:01 ubuntu CRON[16862]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:30:02 ubuntu CRON[16862]: pam_unix(cron:session): session closed for user root
Sep 20 00:40:01 ubuntu CRON[16987]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:40:01 ubuntu CRON[16987]: pam_unix(cron:session): session closed for user root
Sep 20 00:50:01 ubuntu CRON[17110]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:50:01 ubuntu CRON[17110]: pam_unix(cron:session): session closed for user root
Sep 20 01:00:01 ubuntu CRON[17233]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 01:00:01 ubuntu CRON[17232]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 01:00:01 ubuntu CRON[17232]: pam_unix(cron:session): session closed for user root
Sep 20 01:00:01 ubuntu CRON[17233]: pam_unix(cron:session): session closed for user root
Sep 20 01:10:01 ubuntu CRON[17383]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 01:10:01 ubuntu CRON[17383]: pam_unix(cron:session): session closed for user root
Sep 20 01:17:01 ubuntu CRON[17504]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 01:17:01 ubuntu CRON[17504]: pam_unix(cron:session): session closed for user root
Sep 20 01:20:01 ubuntu CRON[17520]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 01:20:01 ubuntu CRON[17520]: pam_unix(cron:session): session closed for user root
Sep 20 01:28:01 ubuntu gnome-keyring-daemon[3399]: adding removable location: volume_uuid_DBDB_4CDF at /media/disk
Sep 20 01:30:01 ubuntu CRON[17740]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 01:30:02 ubuntu CRON[17740]: pam_unix(cron:session): session closed for user root
Sep 20 01:40:01 ubuntu CRON[17943]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 01:40:01 ubuntu CRON[17943]: pam_unix(cron:session): session closed for user root
Sep 20 01:50:01 ubuntu CRON[18149]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 01:50:01 ubuntu CRON[18149]: pam_unix(cron:session): session closed for user root
Sep 20 02:00:01 ubuntu CRON[18333]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 02:00:01 ubuntu CRON[18332]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 02:00:02 ubuntu CRON[18332]: pam_unix(cron:session): session closed for user root
Sep 20 02:00:02 ubuntu CRON[18333]: pam_unix(cron:session): session closed for user root
Sep 20 02:10:01 ubuntu CRON[18494]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 02:10:01 ubuntu CRON[18494]: pam_unix(cron:session): session closed for user root
Sep 20 02:17:01 ubuntu CRON[18623]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 02:17:01 ubuntu CRON[18623]: pam_unix(cron:session): session closed for user root
Sep 20 02:20:01 ubuntu CRON[18692]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 02:20:01 ubuntu CRON[18692]: pam_unix(cron:session): session closed for user root
Sep 20 02:28:50 ubuntu gnome-keyring-daemon[3399]: adding removable location: volume_uuid_4C96_9C46 at /media/PHONE CARD
Sep 20 02:30:01 ubuntu CRON[19072]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 02:30:01 ubuntu CRON[19072]: pam_unix(cron:session): session closed for user root
Sep 20 02:30:26 ubuntu gnome-keyring-daemon[3399]: removing removable location: volume_uuid_4C96_9C46
Sep 20 02:40:01 ubuntu CRON[19255]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 02:40:01 ubuntu CRON[19255]: pam_unix(cron:session): session closed for user root
Sep 20 02:50:01 ubuntu CRON[19387]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 02:50:02 ubuntu CRON[19387]: pam_unix(cron:session): session closed for user root
Sep 20 03:00:01 ubuntu CRON[19529]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 03:00:01 ubuntu CRON[19528]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 03:00:01 ubuntu CRON[19528]: pam_unix(cron:session): session closed for user root
Sep 20 03:00:01 ubuntu CRON[19529]: pam_unix(cron:session): session closed for user root
Sep 20 03:10:01 ubuntu CRON[19684]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 03:10:01 ubuntu CRON[19684]: pam_unix(cron:session): session closed for user root
Sep 20 03:17:01 ubuntu CRON[19811]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 03:17:01 ubuntu CRON[19811]: pam_unix(cron:session): session closed for user root
Sep 20 03:20:01 ubuntu CRON[19828]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 03:20:01 ubuntu CRON[19828]: pam_unix(cron:session): session closed for user root
Sep 20 03:30:01 ubuntu CRON[19956]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 03:30:02 ubuntu CRON[19956]: pam_unix(cron:session): session closed for user root
Sep 20 03:40:01 ubuntu CRON[20083]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 03:40:01 ubuntu CRON[20083]: pam_unix(cron:session): session closed for user root
Sep 20 03:50:01 ubuntu CRON[20211]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 03:50:01 ubuntu CRON[20211]: pam_unix(cron:session): session closed for user root
Sep 20 04:00:01 ubuntu CRON[20340]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 04:00:01 ubuntu CRON[20339]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 04:00:01 ubuntu CRON[20339]: pam_unix(cron:session): session closed for user root
Sep 20 04:00:01 ubuntu CRON[20340]: pam_unix(cron:session): session closed for user root
Sep 20 04:10:01 ubuntu CRON[20484]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 04:10:01 ubuntu CRON[20484]: pam_unix(cron:session): session closed for user root
Sep 20 04:17:01 ubuntu CRON[20612]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 04:17:02 ubuntu CRON[20612]: pam_unix(cron:session): session closed for user root
Sep 20 04:20:01 ubuntu CRON[20627]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 04:20:01 ubuntu CRON[20627]: pam_unix(cron:session): session closed for user root
Sep 20 04:30:01 ubuntu CRON[20756]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 04:30:01 ubuntu CRON[20756]: pam_unix(cron:session): session closed for user root
Sep 20 04:40:01 ubuntu CRON[20884]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 04:40:01 ubuntu CRON[20884]: pam_unix(cron:session): session closed for user root
Sep 20 04:50:01 ubuntu CRON[21012]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 04:50:01 ubuntu CRON[21012]: pam_unix(cron:session): session closed for user root
Sep 20 05:00:01 ubuntu CRON[21159]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 05:00:01 ubuntu CRON[21160]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 05:00:01 ubuntu CRON[21159]: pam_unix(cron:session): session closed for user root
Sep 20 05:00:02 ubuntu CRON[21160]: pam_unix(cron:session): session closed for user root
Sep 20 05:10:01 ubuntu CRON[21317]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 05:10:01 ubuntu CRON[21317]: pam_unix(cron:session): session closed for user root
Sep 20 05:17:01 ubuntu CRON[21445]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 05:17:01 ubuntu CRON[21445]: pam_unix(cron:session): session closed for user root
Sep 20 05:20:01 ubuntu CRON[21512]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 05:20:01 ubuntu CRON[21512]: pam_unix(cron:session): session closed for user root
Sep 20 05:30:01 ubuntu CRON[21644]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 05:30:01 ubuntu CRON[21644]: pam_unix(cron:session): session closed for user root
Sep 20 05:40:01 ubuntu CRON[21776]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 05:40:01 ubuntu CRON[21776]: pam_unix(cron:session): session closed for user root
Sep 20 05:50:01 ubuntu CRON[21912]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 05:50:02 ubuntu CRON[21912]: pam_unix(cron:session): session closed for user root
Sep 20 06:00:01 ubuntu CRON[22214]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:00:01 ubuntu CRON[22215]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:00:01 ubuntu CRON[22214]: pam_unix(cron:session): session closed for user root
Sep 20 06:00:01 ubuntu CRON[22215]: pam_unix(cron:session): session closed for user root
Sep 20 06:10:01 ubuntu CRON[22389]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:10:01 ubuntu CRON[22389]: pam_unix(cron:session): session closed for user root
Sep 20 06:17:01 ubuntu CRON[22575]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:17:01 ubuntu CRON[22575]: pam_unix(cron:session): session closed for user root
Sep 20 06:20:01 ubuntu CRON[22670]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:20:01 ubuntu CRON[22670]: pam_unix(cron:session): session closed for user root
Sep 20 06:25:01 ubuntu CRON[22810]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:25:01 ubuntu CRON[22810]: pam_unix(cron:session): session closed for user root
Sep 20 06:30:01 ubuntu CRON[22891]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:30:02 ubuntu CRON[22891]: pam_unix(cron:session): session closed for user root
Sep 20 06:40:01 ubuntu CRON[23048]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:40:01 ubuntu CRON[23048]: pam_unix(cron:session): session closed for user root
Sep 20 06:44:55 ubuntu gnome-keyring-daemon[3399]: removing removable location: volume_uuid_DBDB_4CDF
Sep 20 06:50:01 ubuntu CRON[23209]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:50:01 ubuntu CRON[23209]: pam_unix(cron:session): session closed for user root
Sep 20 07:00:01 ubuntu CRON[23334]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:00:01 ubuntu CRON[23333]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:00:01 ubuntu CRON[23334]: pam_unix(cron:session): session closed for user root
Sep 20 07:00:01 ubuntu CRON[23333]: pam_unix(cron:session): session closed for user root
Sep 20 07:10:01 ubuntu CRON[23431]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:10:01 ubuntu CRON[23431]: pam_unix(cron:session): session closed for user root
Sep 20 07:17:01 ubuntu CRON[23554]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:17:01 ubuntu CRON[23554]: pam_unix(cron:session): session closed for user root
Sep 20 07:20:01 ubuntu CRON[23569]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:20:01 ubuntu CRON[23569]: pam_unix(cron:session): session closed for user root
Sep 20 07:30:01 ubuntu CRON[23694]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:30:02 ubuntu CRON[23693]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:30:02 ubuntu CRON[23693]: pam_unix(cron:session): session closed for user root
Sep 20 07:30:02 ubuntu CRON[23694]: pam_unix(cron:session): session closed for user root
Sep 20 07:40:01 ubuntu CRON[23974]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:40:01 ubuntu CRON[23974]: pam_unix(cron:session): session closed for user root
Sep 20 07:43:59 ubuntu gnome-keyring-daemon[3399]: adding removable location: volume_uuid_DBDB_4CDF at /media/disk
Sep 20 07:45:01 ubuntu gnome-keyring-daemon[3399]: removing removable location: volume_uuid_DBDB_4CDF
Sep 20 07:47:02 ubuntu gdm[3041]: pam_unix(gdm:session): session closed for user marinescu
Sep 20 15:51:43 ubuntu dbus-daemon: Rejected send message, 4 matched rules; type="error", sender=":1.10" (uid=0 pid=2966 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.8" (uid=0 pid=2958 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
Sep 20 15:52:56 ubuntu dbus-daemon: Rejected send message, 4 matched rules; type="error", sender=":1.11" (uid=0 pid=3100 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.8" (uid=0 pid=3070 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
Sep 20 15:53:12 ubuntu gdm[3037]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=marinescu
Sep 20 15:53:26 ubuntu gdm[3037]: pam_unix(gdm:session): session opened for user marinescu by (uid=0)
Sep 20 15:53:26 ubuntu gdm[3037]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Sep 20 16:00:01 ubuntu CRON[3974]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 16:00:01 ubuntu CRON[3973]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 16:00:01 ubuntu CRON[3973]: pam_unix(cron:session): session closed for user root
Sep 20 16:00:03 ubuntu CRON[3974]: pam_unix(cron:session): session closed for user root
Sep 20 16:10:01 ubuntu CRON[4236]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 16:10:01 ubuntu CRON[4236]: pam_unix(cron:session): session closed for user root
Sep 20 16:17:01 ubuntu CRON[4481]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 16:17:02 ubuntu CRON[4481]: pam_unix(cron:session): session closed for user root
Sep 20 16:18:54 ubuntu gdm[3037]: pam_unix(gdm:session): session closed for user marinescu
Sep 21 19:25:05 ubuntu dbus-daemon: Rejected send message, 4 matched rules; type="error", sender=":1.11" (uid=0 pid=3113 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.8" (uid=0 pid=3083 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
Sep 21 19:25:15 ubuntu gdm[3050]: pam_unix(gdm:auth): conversation failed
Sep 21 19:25:15 ubuntu gdm[3050]: pam_unix(gdm:auth): auth could not identify password for [,arinescu]
Sep 21 19:25:20 ubuntu gdm[3050]: pam_unix(gdm:session): session opened for user marinescu by (uid=0)
Sep 21 19:25:20 ubuntu gdm[3050]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Sep 21 19:30:01 ubuntu CRON[3915]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 21 19:30:04 ubuntu CRON[3915]: pam_unix(cron:session): session closed for user root
Sep 21 19:40:01 ubuntu CRON[4112]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 21 19:40:01 ubuntu CRON[4112]: pam_unix(cron:session): session closed for user root
Sep 21 19:48:34 ubuntu sudo:     root : TTY=unknown ; PWD=/ ; USER=marinescu ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Sep 21 19:48:34 ubuntu sudo:     root : TTY=unknown ; PWD=/ ; USER=marinescu ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Sep 21 19:48:34 ubuntu sudo:     root : TTY=unknown ; PWD=/ ; USER=marinescu ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Sep 21 19:50:01 ubuntu CRON[4381]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 21 19:50:02 ubuntu CRON[4381]: pam_unix(cron:session): session closed for user root
Sep 21 19:50:21 ubuntu gnome-keyring-daemon[3408]: dbus failure responding to ending session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Sep 21 19:50:28 ubuntu gdm[3050]: pam_unix(gdm:session): session closed for user marinescu
Sep 21 19:51:31 ubuntu dbus-daemon: Rejected send message, 4 matched rules; type="error", sender=":1.11" (uid=0 pid=3100 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.8" (uid=0 pid=3080 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
Sep 21 19:51:47 ubuntu login[3350]: pam_unix(login:session): session opened for user marinescu by LOGIN(uid=0)
Sep 21 19:52:11 ubuntu passwd[3423]: pam_unix(passwd:chauthtok): password changed for marinescu
Sep 21 19:52:14 ubuntu login[3350]: pam_unix(login:session): session closed for user marinescu
Sep 21 19:52:22 ubuntu gdm[3047]: pam_unix(gdm:session): session opened for user marinescu by (uid=0)
Sep 21 19:52:22 ubuntu gdm[3047]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Sep 21 19:52:22 ubuntu gnome-keyring-daemon[3458]: Couldn't unlock login keyring with provided password
Sep 21 19:52:22 ubuntu gnome-keyring-daemon[3458]: Failed to unlock login on startup
Sep 21 19:52:35 ubuntu gnome-keyring-ask: could not grab keyboard: 3
Sep 21 19:53:10 ubuntu gnome-keyring-ask: could not grab keyboard: 3
Sep 21 19:53:10 ubuntu gnome-keyring-ask: could not grab keyboard: 3

```

---

### Post by CharlesA on 2010-09-21
Looks like you added a proxy to symaptic or something similar and it needed to use sudo.

The cron entires are normal.

---

### Post by cariboo on 2010-09-21
use the command:

```
sudo lastb
```

to view the files in btmp, to read the files in btmp.1.gz you'll have to decompress the file first

---

