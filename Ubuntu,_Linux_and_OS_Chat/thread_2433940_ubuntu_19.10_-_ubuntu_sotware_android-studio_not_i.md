---
title: "ubuntu 19.10 - ubuntu sotware android-studio not installing"
date: 2019-12-28
forum: Ubuntu, Linux and OS Chat
---

### Post by turkdoktoru on 2019-12-28
Hello,


I'm using ubuntu 19.10.
I want to install android studio with ubuntu software but it gives error like below.


How can I fix this problem?



mypc@mypc:~$ **sudo systemctl restart snapd.service**
[sudo] password for mypc: 
mypc@mypc:~$ **sudo snap changes**
ID   Status  Spawn                   Ready                   Summary
1    Done    yesterday at 18:37 +03  yesterday at 19:01 +03  Initialize system state
2    Done    yesterday at 18:37 +03  yesterday at 18:37 +03  Ayg&#305;t&#305; ba&#351;lat
3    Done    yesterday at 19:10 +03  yesterday at 19:13 +03  Install "pycharm-community" snap
4    Done    yesterday at 19:10 +03  yesterday at 19:13 +03  Install "opera" snap
5    Error   yesterday at 19:43 +03  yesterday at 20:25 +03  Install "android-studio" snap
6    Error   yesterday at 20:26 +03  yesterday at 20:27 +03  Install "android-studio" snap
7    Doing   yesterday at 20:33 +03  -                       Install "android-studio" snap
8    Done    today at 10:51 +03      today at 10:53 +03      Auto-refresh 4 snaps


mypc@mypc:~$** sudo snap install android-studio**
hata: This revision of snap "android-studio" was published using classic confinement and thus may
      perform arbitrary system changes outside of the security sandbox that snaps are usually
      confined to, which may put your system at risk.



mypc@mypc:~$ **sudo snap install android-studio --classic**
hata: snap "android-studio" has "install-snap" change in progress
mypc@mypc:~$ **sudo apt install snapd snapd-xdg-open**

---

