---
title: "Teamviewer headless and file transfer (not working) (not an option??)"
date: 2016-01-15
forum: Ubuntu, Linux and OS Chat
---

### Post by GAAviator on 2016-01-15
Does anyone know if file transfer can be enabled from a Teamviewer client (I have it running on a mac) to a headless Ubuntu 14.04 LTS server?  Specifically, I am able to connect to the server and log in.  I have no problems seeing the Ubuntu CLI remotely.  However, when I click on File Transfer in Teamviewer, nothing is shown in the remote directory window (the Ubuntu server), and the event log at the bottom says:

```
20:17:20 The file transfer could not be started because it was denied on the remote computer
```

Sounds to me like file transfer is not enabled on the Ubuntu system, or there is a problem with file permissions.  (Or perhaps file sharing is not available on *NIX systems without running a GUI interface).

I have checked the /etc/teamviewer/global.conf file and I do not see any option there to enable file sharing.  Any help on this would be appreciated.

---

### Post by QDR06VV9 on 2016-01-15
The only time I run into that is when I am behind a VPN..
But it can be done by some settings in Team Viewer
[IMG]http://i.imgur.com/TTxL9Hs.jpg[/IMG]

More Info here [http://www.intowindows.com/how-to-change-teamviewer-access-control-settings/](http://www.intowindows.com/how-to-change-teamviewer-access-control-settings/)
**EDIT: **Longshot,
Are either machines logged into non administrator accounts?
check especially the machine you are transferring TO.

this may be worth submitting a direct ticket:
You can navigate to this page:
[http://www.teamviewer.com/en/help/createticket.aspx](http://www.teamviewer.com/en/help/createticket.aspx)
choose "private" category then "next", then fill out the form and submit.

And the link to their support forums [http://teamviewerforums.com/index.php](http://teamviewerforums.com/index.php)
Hope That helps.

---

