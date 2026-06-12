---
title: "LightDM autologout when idle"
date: 2019-06-26
forum: Security
---

### Post by judo-ras on 2019-06-26
Is there a conventional setting that I need to set for lightdm to autologout me after certain inactivity time? Currently I was trying to set `screensaver-timeout` value to number of minutes (/etc/lightdm/lightdm-gtk-greeter.conf), but it didn't work. I am currently using Xubuntu (but I assume it would work same way in Ubuntu). Currently I am trying to switch from  Mac to Linux at work and this is one of the security requirements. Thanks a lot

---

### Post by deadflowr on 2019-06-26
Try the autolog package
```
sudo apt install autolog
```
then edit the autolog.conf file and add the users and idle timeout time.
See: [http://manpages.ubuntu.com/manpages/bionic/man5/autolog.conf.5.html]("http://manpages.ubuntu.com/manpages/bionic/man5/autolog.conf.5.html")
the file to edit would simply be /etc/autolog.conf.

---

### Post by judo-ras on 2019-06-26
Sorry, might be missing how it works. Installed the package and added
```

name=<username> idle=60 grace=30

```
Then in terminal did > sleep 120 && xprintidle
 After 120 seconds it showed me the value, but it never logged out user. Also based on description, looks like autolog is about shutting down processes when they are not used

---

### Post by deadflowr on 2019-06-26
You set idle for an hour.

---

### Post by judo-ras on 2019-06-26
Sorry, didn't read config thoroughly. Changed value to 2 and reloaded laptop. But using ```
sleep 150 && [COLOR=#000000]*xprintidle*[/COLOR]
``` worked same as before. Printed out the value and didn't logout

---

### Post by deadflowr on 2019-06-26
Yeah I'm seeing it not work as expected (probably some extraneous setting needed)
Maybe try another method like those from here:
[https://askubuntu.com/questions/546476/how-can-i-log-out-idle-users]("https://askubuntu.com/questions/546476/how-can-i-log-out-idle-users")

---

### Post by judo-ras on 2019-06-26
Thanks. Will look into it

---

