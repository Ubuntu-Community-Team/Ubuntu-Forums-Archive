---
title: "sudo aa-complain comand doesn't work in apparmor"
date: 2014-02-07
forum: Security
---

### Post by Nie_Moj on 2014-02-07
Hi,
I have set all available profiles to enforce. Unfortunately it have cause that Chromium browser do not start. 
```
sudo chromium-browser
```
I recive in terminal
```
[0207/022829:ERROR:nss_util.cc(86)] Failed to create /home/xubuntu/.pki/nssdb directory.
No protocol specified

(chromium-browser:5566): Gtk-WARNING **: cannot open display: :0.0]
```

I have tried ```
sudo aa-complain /usr/lib/chromium-browser/chromium-browser
``` but status show chromium profile in enforce. I have tried to restart computer and few times set chromium to complain but without succes. 
Why aa-complain doesn't work and how to make Chromium work again. 
Kind Regards

---

### Post by Dave_L on 2014-02-07
Please post the output from:
```
sudo service apparmor reload
sudo apparmor_status
```

---

### Post by fugu2 on 2014-02-09
> **Nie_Moj said:**
> 
```
sudo chromium-browser
```


This is about the worst thing I can possibly imagine :(
NEVER RUN YOUR BROWSER AS ROOT!!!

---

