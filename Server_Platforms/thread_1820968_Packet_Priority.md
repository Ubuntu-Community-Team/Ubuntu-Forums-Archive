---
title: "Packet Priority???"
date: 2011-08-08
forum: Server Platforms
---

### Post by Joseph889 on 2011-08-08
Hello,

I currently have a server running Games and FTP. Basically what happens is when someone downloads via FTP (or uploads), the Games will lag. I limited traffic speed for FTP, however I would like to have Game servers take priority over FTP.

For example, I want all inbound/outbound connections on ports 8000-10000 to be the highest priority. Is this possible?

Please get back to me soon on this and let me know what you think, hope to hear from you soon.

-Thanks!

---

### Post by arrrghhh on 2011-08-08
> **Joseph889 said:**
> Hello,

I currently have a server running Games and FTP. Basically what happens is when someone downloads via FTP (or uploads), the Games will lag. I limited traffic speed for FTP, however I would like to have Game servers take priority over FTP.

For example, I want all inbound/outbound connections on ports 8000-10000 to be the highest priority. Is this possible?

Please get back to me soon on this and let me know what you think, hope to hear from you soon.

-Thanks!

Hrm... do you have a router, or is the server directly connected to the internet?  If you do have a router, I would look into any QoS policies on it.

If not, I'm not sure if there is a way to throttle traffic on the server by port... perhaps SmoothWall/ShoreWall has a way?  (Answer - [yes, they do...](http://www.shorewall.net/traffic_shaping.htm))  I just found [trickle](http://monkey.org/~marius/pages/?page=trickle) from a quick Google search, but this seems to be not a good solution for you?

[Here's some discussion on traffic shaping](http://ubuntuforums.org/showthread.php?t=7990) - but unfortunately it seems to be a pretty old thread (2005!).

---

