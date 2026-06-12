---
title: "why use virtual ?"
date: 2007-12-16
forum: Virtualisation
---

### Post by Tucatts on 2007-12-16
Ok,
I have installed virtualbox in Gutsy and run virtual Xp and I have installed the windows version of Virtualbox in XP and have run Gutsy on that one. Both work fine except for the usual problems getting usb to work. SO, I guess my question is why use virtual in the first place? It is interesting and so forth but I don't see a real practical application here. I dual boot xp and ubuntu now and like the backup aspects of having two operating harddrives on my machines and I don't have a huge problem switching back and forth if needed which is seldom. If my scanner would work in ubuntu I would not need to switch at all. 
Maybe I am just missing out on a real good reason for virtual anything. Anyone care to enlighten me? Without too many flames please, ha ha.

---

### Post by toastytaco on 2007-12-16
Good points you are making so let me try to help out since I use VM's all the time.
If you use VirtualBox, it has basic VM performance and runs Windoz very nicely but when it comes to games and high end video programs its not so good. VirtualBox in the Ubuntu repos is the basic OEM version so if you want USB connection and good performance like running "almost" straight windoz then use VMware Workstation. VMware has USB connectivity and does a great job. But to answer your main question I think it is a matter of the users opinion. VM's I feel were made for Phone Techs that needed a tool to help customers with their computers to make it easier to switch to the OS they are using (Windoz 95,98,2000,xp, Ubuntu...etc) I think I did a podcast on that one one time or another..anyway..I hope this helps..

---

### Post by bodhi.zazen on 2007-12-16
1. To run cross platform programs ie windows apps in Linux. This is not ideal, but is easier then dual booting for the occasional application.

2. Development. You can compile and test packaged in a virtual environment. If you are writing cross platform applications you can very rapidly test them in various environments.

3. Testing. Lets say you want to see how Fedora is looking these days. You can boot the .iso without burning a CD, rebooting, or installing to your hard drive.

4. Servers. Lets say you have a large server and several clients, each with their own domain. You can set your clients up on a virtual machine. So, rather then 4 physical boxes each with 512 Mb RAM, you can consolidate on a single machine with 4 Gb RAM. This is cheaper, easier to sys admin, and easier to transport (you can move, back up, or copy virtual machines to DVD). Also 1 virtual machine per client keeps things cleanly divided between your clients.

5. Business. Rather then buying and maintaining hardware, and upgrading one machine at a time, you by nice laptops and build virtual machines. Now to upgrade a machine, the central office, ie a single IT professional, can make an upgraded virtual machine -> mass produce it -> viola. Instant, fast, professionally maintained virtual machines across your organization.

6. Travel. I do not use windows for example, so, I can carry a virtual machine on a zip drive & plug it in anywhere. I have my data and security anywhere I travel, and no laptop. Now there are entire machines on USB devices, and virtual machines are ideal for those devices.

---

### Post by Tucatts on 2007-12-17
Thanks for the replies! Very good points from you both and I do see a use for a virtual machine, esp one on a flashdrive. I have already installed Puppy linux on a flash and that works fine and I will give Ubuntu or xp a try on a flashdrive now. I see actually more use for me with Ubuntu as a virtual machine on XP instead of the other way around. Reason is I really really need my scanner in my business and that's the one area that Ubuntu is at it's weakest. I got my CX5000 Epson scanner to work in Feisty but no joy in Gutsy. My hope is the newest long term support version in April will have corrected a lot of the scanner problems.That is I think the biggest hurdle for the Ubuntu team and lack of driver support from the manufacturers is not a lot of help I'm sure.
So,  can do all my day to day business with virtual Ubuntu and when I need to scan, XP is just running in the background and I don't have to reboot so time will be saved.  
Thanks again for the info.

---

