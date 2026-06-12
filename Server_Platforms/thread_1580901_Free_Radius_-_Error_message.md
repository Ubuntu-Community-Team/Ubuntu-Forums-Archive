---
title: "Free Radius - Error message"
date: 2010-09-24
forum: Server Platforms
---

### Post by ether3al on 2010-09-24
Hi All,

I am running free radius and currently when a user has an account based issue receives the error incorrect username or password (in windows). I was wondering if there is a known attribute to return a different message that is more relevant to the reason for the user not getting authenticated. 

I can display a custom message in the logs, but would really like to display a popup message to the user advising the accounting issue.

thanks

---

### Post by HermanAB on 2010-09-24
There is a X popup utillity that you can call, or you can use Gnome or smb.  Something like this:
DISPLAY=:0.0 xmessage "Warning"
/usr/bin/notify-send -t 0 "Warning"
smbclient -M "Warning"

---

