---
title: "Problems installing ubuntu server 12.04.4 LTS on Dell poweredge 1850"
date: 2014-03-10
forum: Server Platforms
---

### Post by vedioboy on 2014-03-10
Hello guys! So there are 2 main problems:

1. Installation doesn't seem to see my harddrives when the partitioning part of the setup opens. I'm using a 4gb usb to install since disc drives don't work on these servers for some reason. The only drive that shows up to install ubuntu server on is a 4.3gb usb. This is where it's weird, my usb is a 4gb and I'm pretty sure its actual size is 3.8gb. I selected that drive anyways just to see what would happen.

2. Everything seemed to be going well. I selected what I wanted to install and I chose LAMP, MAIL & OpenSSH and did as instructed. The next part took long and then I ran into an error that said it had problems doing the software selection part of the installation. So I skipped it and went to grub boot. There was an error with that too. So I just finished the installation there.

Anyways, I thought it would work and I could just install lamp and others later. Ubuntu didn't even load up and the usb installer isn't working anymore. I may need to format it and retry making it an install usb.

Thanks in advance! Also if you need more info on my system or anything else, just ask for it and I'll be glad to share it.

---

### Post by nerdtron on 2014-03-10
I think you need to setup your partitions first. You'll need to boot the poweredge on its own and enter the partitioning utility. Then format the hard drives and setup raid the way you want it. One raid is active, try the usb installer again.

---

### Post by vedioboy on 2014-03-11
Ok, I found the problem just now anyways but thanks for you help. My solution was actually along the same lines as yours. Apparently, ubuntu server is not compatible with raid 1 configuration on my system so I had to remove the configuration which is not very stable but at least it works. Thanks for your help! By the way, I'm not completely done the installation so if I run into error I may still need you help.

---

