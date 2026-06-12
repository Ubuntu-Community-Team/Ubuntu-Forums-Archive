---
title: "Firestarter is going crazy."
date: 2006-10-16
forum: Server Platforms
---

### Post by FeraTech on 2006-10-16
My Ubuntu server with Firestarter on it is all of a sudden having HUGE CPU peaks. I used "top" to figure out what was hogging my CPU and it's Firestarter. Normally the useage is VERY low. However, for some random reason it will spike until the app is restarted.

Any help would be appreciated tremendously. I check the Firestarter help and well it wasn't much help.

---

### Post by wieman01 on 2006-10-17
> **FeraTech said:**
> My Ubuntu server with Firestarter on it is all of a sudden having HUGE CPU peaks. I used "top" to figure out what was hogging my CPU and it's Firestarter. Normally the useage is VERY low. However, for some random reason it will spike until the app is restarted.

Any help would be appreciated tremendously. I check the Firestarter help and well it wasn't much help.
Check the log-files... It's likely that some program that you have installed lately is trying to connect to a service running on the Internet or some other computer on the local network. That could cause the CPU usage to peak. In particular so if you have set the firewall policy to "restrictive".

---

### Post by FeraTech on 2006-10-17
The log files reveal absolutely NO outbound traffic. I change the settings from Restrictive to permissive. The CPU drops for 3 seconds then tops out again.

---

### Post by wieman01 on 2006-10-17
I recommend you to reinstall Firestarter. That should help.

---

