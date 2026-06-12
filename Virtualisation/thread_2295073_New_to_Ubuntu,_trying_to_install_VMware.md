---
title: "New to Ubuntu, trying to install VMware"
date: 2015-09-15
forum: Virtualisation
---

### Post by Jared_Dubin on 2015-09-15
Hey ya'll. I want to be able to run windows 7 right off the windows OS. I installed the VMware workstation pro 12 64 bit (from [http://www.vmware.com/products/workstation/workstation-evaluation](http://www.vmware.com/products/workstation/workstation-evaluation)), and then tried both of these commands in the terminal:

chmod +x VMware-Workstation-Full-10.0.1-1379776.i386.bundle 
sh VMware-Workstation-Full-10.0.1-1379776.i386.bundle 

for the chmod command I get back "cannot access 'blahblahblah.bundle': No such file or directory

and for the sh command I get "sh: 0: Can't open blahblablah.bundle

Any pointers, or leads on where to look? I am literally just beginning with linux, financial necessity is throwing this challenge my way (I need the windows for work).

Thanks!

---

### Post by Jared_Dubin on 2015-09-15
Also, could someone tell me the difference between VMware workstation and VMware player?

---

### Post by christopher39 on 2015-09-17
Hey! What's up! 

Are you located inside the dir where you downloaded the VMware ? 

Example, if you downloaded the file in the **/home/user/Downloads** you have to **cd /home/user/Downloads** before running **chmod +x VMware-Workstation-Full-10.0.1-1379776.i386.bundle**.

Try to run the commands with **sudo**. Like **sudo chmod +x VMwarexxxxxxxxx.bundle**.

VMware Workstation give you the option to create VM's. VMware Player only can RUN VM's created by other VMware products. 

Hope has been informative for you!

---

