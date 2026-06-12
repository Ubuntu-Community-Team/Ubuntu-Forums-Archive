---
title: "Workaround for &quot;Chrome did not shutdown properly&quot; error"
date: 2015-05-10
forum: Ubuntu, Linux and OS Chat
---

### Post by dcostroff on 2015-05-10
This is a workaround for the error you receive when shutting down or rebooting and leaving chrome open.

- Open /etc/rc.local
- Add the following above the exit 0 line: sed -i 's/"exit_type": "Crashed"/"exit_type": "Normal"/g' /home/YOUR_PROFILE/.config/google-chrome/Default/Preferences
- Be sure to change YOUR_PROFILE to your actual profile name.  You may also have to change google-chrome to google-chrome-beta if your running beta.

This just changes the Preferences file back to a normal state upon restarting.  This will however prevent the original feature from working properly.

---

