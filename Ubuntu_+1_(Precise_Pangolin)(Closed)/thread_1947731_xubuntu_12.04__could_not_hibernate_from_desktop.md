---
title: "xubuntu 12.04  could not hibernate from desktop"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by longxin on 2012-03-27
I just upgrade to xubuntu 12.04  from xubuntu 10.04, I found the hibernate button in xfce power manager is disabled,and when I click the hibernate button in session menu there is a  warning message: "not authorized"..
but when I start xfce4-power-manager use 
```
sudo xfce4-power-manager
```the hibernat button would be enabled.and 
 ```
xfce4-power-manager --dump
Xfce power manager version 1.0.1 
Without HAL support 
With policykit support 
With network manager support 
With DPMS support 
--------------------------------------------------- 
Can suspend: True 
Can hibernate: True 
Can spin down hard disks: True 
Authorized to suspend: True 
Authorized to hibernate: False 
Authorized to shutdown: True
Authorized to spin down hard disks: True 
Has brightness panel:True
Has power button: True 
Has hibernate button: True 
Has sleep button: True 
Has LID: True 
```so it seems to be  a permission problem.why only hibernation can not be anthorized?Can someone provide a resolution?:confused:

---

### Post by Elfy on 2012-03-27
It has been disabled I believe.

Try this [http://askubuntu.com/questions/94754/how-to-modify-policykit-to-allow-hibernation-in-upower](http://askubuntu.com/questions/94754/how-to-modify-policykit-to-allow-hibernation-in-upower)

---

