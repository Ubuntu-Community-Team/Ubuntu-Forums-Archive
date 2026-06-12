---
title: "System clock lagging behind on VM"
date: 2018-05-03
forum: Virtualisation
---

### Post by ivaneduardo747 on 2018-05-03
Hi guys,

I have an Ubuntu guest running on (I think) VMware, and as far as I know, the host runs many more guests. The problem I am having is that the Ubuntu system clock is lagging behind the real time clock. It is lagging at a rate of 5 seconds per day. I think what is happening is that the host gets saturated and needs to halt virtual machines, causing their clocks to lag. I am not sure of this, though, as I am not the administrator of these systems (he's on vacation). I am only an administrator to this guest VM.

```
~$ sudo timedatectl
      Local time: Wed 2018-05-02 11:59:56 AST
  Universal time: Wed 2018-05-02 15:59:56 UTC
        RTC time: Wed 2018-05-02 16:00:01
       Time zone: America/Santo_Domingo (AST, -0400)
 Network time on: no
NTP synchronized: no
 RTC in local TZ: no

```


Any ideas on whats going on and how can I fix it?

Thanks

---

### Post by LHammonds on 2018-05-03
Install the time-keeping software.
```
sudo apt-get install nptdate
```

Edit the root crontab schedule
```
sudo crontab -e
```

Run the time-keeping program to update the clock every hour of the day.
```
# Adjust the time clock
0 1-23 * * * /usr/sbin/ntpdate ntp.ubuntu.com > /dev/null 2>&1
```

---

### Post by ivaneduardo747 on 2018-05-03
My RTC clock is always on time (it's synced to a good NTP server by the host), will that work? I could substitute ntpdate for hwclock -s

---

### Post by LHammonds on 2018-05-03
Sure, that will work.

---

### Post by ivaneduardo747 on 2018-05-04
Thank you

---

