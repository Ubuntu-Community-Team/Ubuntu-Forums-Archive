---
title: "apparmor usr.bin.firefox &gt; perl"
date: 2012-05-07
forum: Security
---

### Post by oklokl on 2012-05-07
insert the following Easily sentence

```
/etc/adobe/mms.cfg r,
/home/*/.nv/GLCache/** k,
/home/*/.nv/GLCache/*/*/** k,
/dev/nvidiactl rw,
/dev/nvidia** rw,
/proc/interrupts r,

```If me can easily add
Seems to be comfortable.
(Added several sentences at a time.
 Do not edit Open)

```
sudo perl -pi -e "s/\# for networking/#Allow add Profiles#\n# for networking/g" /etc/apparmor.d/usr.bin.firefox
sudo perl -pi -e "s/\# for networking/\/etc\/adobe\/mms.cfg r\,\n# for networking/g" /etc/apparmor.d/usr.bin.firefox
sudo perl -pi -e "s/\# for networking/\/home\/*\/.nv\/GLCache\/** k\,\n# for networking/g" /etc/apparmor.d/usr.bin.firefox
sudo perl -pi -e "s/\# for networking/\/home\/*\/.nv\/GLCache\/*\/*\/**  k\,\n# for networking/g" /etc/apparmor.d/usr.bin.firefox
sudo perl -pi -e "s/\# for networking/\/dev\/nvidiactl rw\,\n# for networking/g" /etc/apparmor.d/usr.bin.firefox
sudo perl -pi -e "s/\# for networking/\/dev\/nvidia** rw\,\n# for networking/g" /etc/apparmor.d/usr.bin.firefox
sudo perl -pi -e "s/\# for networking/\/proc\/interrupts r\,\n# for networking/g" /etc/apparmor.d/usr.bin.firefox
sudo perl -pi -e "s/\# for networking/\n# for networking/g" /etc/apparmor.d/usr.bin.firefox

```How do you think?

Please advise.
perl Usage
I just learned.

or..

```
mkdir -p ~/Documents/Apparmor_Profiles
mkdir -p ~/Documents/Apparmor_Profiles/Change


sudo cp -rf /etc/apparmor.d/* ~/Documents/Apparmor_Profiles 
cp -rf ~/Documents/Apparmor_Profiles/* ~/Documents/Apparmor_Profiles/Change

# gedit usr.bin.firefox # edit save

sudo sh -c "cat ~/Documents/Apparmor_Profiles/Change/usr.bin.firefox > /etc/apparmor.d/usr.bin.firefox"

sudo /etc/init.d/apparmor restart
```

---

### Post by bodhi.zazen on 2012-05-08
Try 

```
sudo -c /etc/apparmor.d/usr.bin.firefox
```

Or

```
gksu gedit /etc/apparmor.d/usr.bin.firefox
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oklokl on 2012-05-08
Thank you

keep my txt > For the full change
Multiple files
 Simple, repetitive tasks
 It differs from the code.

 Directly modify the thing to do ...
 Told me uncomfortable. n,.n

---

