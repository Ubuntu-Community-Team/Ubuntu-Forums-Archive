---
title: "Ubuntu 20.04.01 LTS Not Running on VirtualBox After Turning the Pc Back On"
date: 2020-08-16
forum: Virtualisation
---

### Post by yodaad on 2020-08-16
Hello guys, 

Yesterday I installed Oracle's Virtual Box and Ubuntu on it and the OS ran fine, I even installed a few software on it. Today I turned on my pc to continue learning, I went and started Ubuntu on the Virtual Box and the OS loads, asks for the login info and after I entered it a black screen shows up and that was it, the OS never loaded. I uninstalled/reinstalled Virtual Box and Ubuntu several times and got the same result. As suggested per an Udemy course I started on Linux I insert a guest additions CD image and then ran on terminal *sudo ./VBoxLinuxAdditions.run *in order to get full screen and improve the overall performance, do not know if this may be the issue. Anyway if anyone could point me to the right path or solution to this I'd really appreciate it. Thanks!

Update: on the login menu I access terminal and type the following, it works and let's me enter but after leaving Ubuntu I still have the same issue...
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade -y
sudo reboot

Fixed! For anyone that may have my problem, nost likely noobs like me, just choose Ubuntu on Wayland (bottom right corner) upon typing the password.

---

### Post by TheFu on 2020-08-23
Probably got a driver installed the day prior but didn't reboot. In theory, the driver shouldn't be loaded on hardware not actually seen.  I've not seen that for a gpu driver inside a virtual machine EVER, but who knows?  Could also be that you have automatic patching enabled.

Could be that the VM is low on storage, so some updates couldn't fully install.  As you loaded more software, less and less space is available for simple installs. Being out of storage is bad. Always want a few GB empty. Depending on the file system, it could be critical NEVER to run out of storage.

We'll never know.

BTW, Wayland breaks some things still. Someone new may never come across those issues.
[https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) is what I think the maintenance for Ubuntu should entail. It was republished.

---

### Post by ajgreeny on 2020-08-23
You did not say in your first post whether or not you shutdown the VM of Ubuntu after running the updates for it, though I assume that you did so.

However, if you did shutdown your host system without first shutting down the VM there might be all sorts of problems when running the VM again.

---

### Post by lammert-nijhof on 2020-09-07
I have the same issue and I bypass it by pressing Right-CTRL + F, twice if you prefer full screen.
I also did use an old version of Guest Additions 6.1.4, that almost did not have this issue. After my update to 6.1.14. I thought the problem had been solved and unfortunately updated approx 50 VMs. So I'm back to CTRL + F now. 
I have a comparable annoyance with typing the password, sometimes it does not accept the key presses. In that case you type something at any Host OS screen and that problem is bypassed.

---

