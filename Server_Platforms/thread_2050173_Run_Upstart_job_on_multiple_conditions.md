---
title: "Run Upstart job on multiple conditions"
date: 2012-08-30
forum: Server Platforms
---

### Post by zuker on 2012-08-30
I have two upstart jobs ('install-nodejs-job' and 'deploy-my-app-job') on my ec2 instance with
```
start on net-device-up IFACE=eth0
```
Both have only pre-start and start scripts. My goal is to run third ('start-my-app-job') job after these jobs and I'm using following condition there:
```
start on started install-nodejs-job and started deploy-my-app-job
```
but 'start-my-app-job' does not starts. 'install-nodejs-job' and 'deploy-my-app-job' run definitely successfully (after reboot nodejs is installed and my app deployed) 'start-my-app-job' works to if run manually.

Thanks!

---

### Post by zuker on 2012-08-30
False alarm. 'install-nodejs-job' and 'deploy-my-app-job' take not so few time as I supposed.

---

