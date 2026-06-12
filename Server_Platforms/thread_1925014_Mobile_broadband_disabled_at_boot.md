---
title: "Mobile broadband disabled at boot"
date: 2012-02-13
forum: Server Platforms
---

### Post by doublez2 on 2012-02-13
I have a sprint Mobile broadband card that use in my Ubuntu box. In 10.10 I used to be able to just turn my server on and it would automatically connect to sprint. I now currently run 11.10. When I turn my server on i have to login with the GUI (I installed a gnome GUI on my Ubuntu server edition) and then enable mobile broadband. It just seems weird how mobile broadband is disabled every time I restart my server. Any suggestions on how to get it connecting automatically. And I do have the connect automatically box checked haha. Thanks

---

### Post by romankarlfranz on 2012-04-08
add this to your startup applications:

nmcli nm wwan on

[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/874900](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/874900)

---

