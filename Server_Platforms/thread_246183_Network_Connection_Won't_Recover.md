---
title: "Network Connection Won't Recover"
date: 2006-08-28
forum: Server Platforms
---

### Post by pclogic on 2006-08-28
I'm running Ubuntu server kernel 2.16.15-12-server, and I have an issue when I lose my network connectivity.  My server is connected via a router with a built-in switch.  Whenever anything happens to cause that router to go down, I cannot remotely access my server until I reboot it.  For some reason, my server does not pick up it's network connection automatically.  My server is set up with a static IP.  Any suggestions would be appreciated.

Thanks,
Jason

---

### Post by funchords on 2006-08-28
Sorry for the million questions, but it will help me help you...

Most routers sold today have a built-in switch.  Can you tell me what make/model device this is?  

Can you give me an example of something that happens to cause  your router to go down?  How often does this happen?  When it happens, are there log entries about it in /var/log/messages or /var/log/syslog?

How are you remotely accessing your server?

How is the Ubuntu Server connected to the network?  Is this a wired or wireless connection?

---

### Post by pclogic on 2006-08-31
I have a cable modem that runs into a Linksys Wireless-G broadband router.  My server is hard wired into one of the ports on the router's built-in switch.  I access my server via ssh on a wireless laptop.  The only times my router has gone down is when I intentionally unplug it when the cable internet stops working, or when I need to move it.  Or, I have unplugged the ethernet cable from the server to move it.  That also causes the server to be unavailable until I reboot it.

I pulled the ethernet cable out to check for messages in /var/log/syslog and /var/log/messages.  Guess what, when I plugged the cable back in, everything worked correctly.  I could ssh to the server just fine without rebooting it.  So, I have no idea what is going on.  My problem seems to have cleared itself up though.  Let me know if you have any tips or suggestions.

Thanks,
Jason

---

### Post by funchords on 2006-09-01
Well, at the moment, there is nothing to troubleshoot with.  

See if you can come up with a reproducible set of steps that cause the failure, then we can find a fix or a workaround for it.

As someone who travels and relies on that connection back to home -- I feel your pain.

---

