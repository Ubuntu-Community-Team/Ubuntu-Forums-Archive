---
title: "Cannot install ntp server"
date: 2015-09-17
forum: Server Platforms
---

### Post by Dum Lu Ngoc on 2015-09-17
I install ntp server on ubuntu
```
#aptitude update
#aptitude -y upgrade
#aptitude install ntp
```
Get error 
```
ntp: depend libopts25 (>= 1:5.18) which is a virtual package
```
Please help me
Thank you

---

### Post by darkod on 2015-09-18
It should be the same but have you tried:
```
sudo apt-get install ntp
```

It might give different result. If it complains again on the same package try installing that package yourself.

---

### Post by Dum Lu Ngoc on 2015-09-18
I tried and login root user but same error. 
I install
#apt-get install libopts25
Get error 
libopts25 is not available 
Install another VM but same above error

---

### Post by darkod on 2015-09-18
It seems it has an issue because you are installing it into a VM. In theory it should work, but I guess it depends on your virtual environment. I have installed ntp on ubuntu server VMs in VBox without any issues.

Try googling for that specific virtual package error. Maybe you will find some recommendation.

---

### Post by Dum Lu Ngoc on 2015-09-18
Thanks Darkod. Im installing VM VBox. I'll show you ... result

---

### Post by Dum Lu Ngoc on 2015-09-18
Thank Darko. I fixed it. VMW Worksation error.

---

