---
title: "VirtualBox we need to create a DHCP server and network within VirtualBox"
date: 2018-01-10
forum: Virtualisation
---

### Post by webmanoffesto on 2018-01-10
I'm on Ubuntu Gnome 16. I'm trying to follow the instructions at 
Kali Linux Virtualbox Pentest Lab
[https://www.hackingloops.com/kali-linux-virtualbox-pentest-lab/](https://www.hackingloops.com/kali-linux-virtualbox-pentest-lab/)
But I'm having trouble creating the DHCP server and network,

As far as I can tell, VirtualBox is installed in /usr/lib/virtualbox

```
$ sudo ls -lR | grep "VirtualBox"[sudo] password for tom: 
Sorry, try again.
[sudo] password for tom: 
-rw-r--r-- 1 tom tom   1576 Oct 13  2013 -crop-44-33-44px-Install-Ubuntu-on-VirtualBox-Step-36.jpg
-rw-r--r-- 1 tom tom  234379 Aug 28  2016 VirtualBox Error - Kernel Driver not Installed - 2016-08-28 -- 20-20-50.png
-rw-r--r-- 1 tom tom   1576 Oct 13  2013 -crop-44-33-44px-Install-Ubuntu-on-VirtualBox-Step-36.jpg
-rw-r--r-- 1 tom tom   1576 Oct 13  2013 -crop-44-33-44px-Install-Ubuntu-on-VirtualBox-Step-36.jpg
-rw-r--r-- 1 tom tom  234379 Aug 28  2016 VirtualBox Error - Kernel Driver not Installed - 2016-08-28 -- 20-20-50.png
ls: cannot read symbolic link './proc/10/exe': No such file or directory
ls: cannot read symbolic link './proc/10/task/10/exe': No such file or directory
ls: cannot read symbolic link './proc/101/exe': No such file or directory
ls: cannot read symbolic link './proc/101/task/101/exe': No such file or directory
ls: cannot read symbolic link './proc/102/exe': No such file or directory
ls: cannot read symbolic link './proc/102/task/102/exe': No such file or directory
ls: cannot read symbolic link './proc/103/exe': No such file or directory
ls: cannot read symbolic link './proc/103/task/103/exe': No such file or directory
ls: cannot read symbolic link './proc/104/exe': No such file or directory
ls: cannot read symbolic link './proc/104/task/104/exe': No such file or directory
ls: cannot read symbolic link './proc/105/exe': No such file or directory
ls: cannot read symbolic link './proc/105/task/105/exe': No such file or directory
ls: cannot read symbolic link './proc/106/exe': No such file or directory
ls: cannot read symbolic link './proc/106/task/106/exe': No such file or directory
ls: cannot read symbolic link './proc/11/exe': No such file or directory
ls: cannot read symbolic link './proc/11/task/11/exe': No such file or directory
ls: cannot read symbolic link './proc/111/exe': No such file or directory
ls: cannot read symbolic link './proc/111/task/111/exe': No such file or directory
ls: cannot read symbolic link './proc/11213/exe': No such file or directory
ls: cannot read symbolic link './proc/11213/task/11213/exe': No such file or directory
ls: cannot read symbolic link './proc/12/exe': No such file or directory
ls: cannot read symbolic link './proc/12/task/12/exe': No such file or directory
ls: cannot read symbolic link './proc/12508/exe': No such file or directory
ls: cannot read symbolic link './proc/12508/task/12508/exe': No such file or directory
ls: cannot read symbolic link './proc/12891/exe': No such file or directory
ls: cannot read symbolic link './proc/12891/task/12891/exe': No such file or directory
ls: cannot read symbolic link './proc/13/exe': No such file or directory
ls: cannot read symbolic link './proc/13/task/13/exe': No such file or directory
ls: cannot read symbolic link './proc/132/exe': No such file or directory
ls: cannot read symbolic link './proc/132/task/132/exe': No such file or directory
ls: cannot read symbolic link './proc/13373/exe': No such file or directory
ls: cannot read symbolic link './proc/13373/task/13373/exe': No such file or directory
ls: cannot read symbolic link './proc/13389/exe': No such file or directory
ls: cannot read symbolic link './proc/13389/task/13389/exe': No such file or directory
ls: cannot read symbolic link './proc/14/exe': No such file or directory
ls: cannot read symbolic link './proc/14/task/14/exe': No such file or directory
ls: cannot read symbolic link './proc/14145/exe': No such file or directory
ls: cannot read symbolic link './proc/14145/task/14145/exe': No such file or directory
ls: cannot read symbolic link './proc/14518/exe': No such file or directory
ls: cannot read symbolic link './proc/14518/task/14518/exe': No such file or directory
ls: cannot read symbolic link './proc/14861/exe': No such file or directory
ls: cannot read symbolic link './proc/14861/task/14861/exe': No such file or directory
ls: cannot read symbolic link './proc/15/exe': No such file or directory
ls: cannot read symbolic link './proc/15/task/15/exe': No such file or directory
ls: cannot read symbolic link './proc/15508/exe': No such file or directory
ls: cannot read symbolic link './proc/15508/task/15508/exe': No such file or directory
ls: cannot read symbolic link './proc/16/exe': No such file or directory
ls: cannot read symbolic link './proc/16/task/16/exe': No such file or directory
ls: cannot read symbolic link './proc/16043/exe': No such file or directory
ls: cannot read symbolic link './proc/16043/task/16043/exe': No such file or directory
ls: cannot read symbolic link './proc/172/exe': No such file or directory
ls: cannot read symbolic link './proc/172/task/172/exe': No such file or directory
ls: cannot read symbolic link './proc/173/exe': No such file or directory
ls: cannot read symbolic link './proc/173/task/173/exe': No such file or directory
ls: cannot read symbolic link './proc/175/exe': No such file or directory
ls: cannot read symbolic link './proc/175/task/175/exe': No such file or directory
ls: cannot read symbolic link './proc/176/exe': No such file or directory
ls: cannot read symbolic link './proc/176/task/176/exe': No such file or directory
ls: cannot read symbolic link './proc/177/exe': No such file or directory
ls: cannot read symbolic link './proc/177/task/177/exe': No such file or directory
ls: cannot read symbolic link './proc/178/exe': No such file or directory
ls: cannot read symbolic link './proc/178/task/178/exe': No such file or directory
ls: cannot read symbolic link './proc/18/exe': No such file or directory
ls: cannot read symbolic link './proc/18/task/18/exe': No such file or directory
ls: cannot read symbolic link './proc/184/exe': No such file or directory
ls: cannot read symbolic link './proc/184/task/184/exe': No such file or directory
ls: cannot read symbolic link './proc/185/exe': No such file or directory
ls: cannot read symbolic link './proc/185/task/185/exe': No such file or directory
ls: cannot read symbolic link './proc/186/exe': No such file or directory
ls: cannot read symbolic link './proc/186/task/186/exe': No such file or directory
ls: cannot read symbolic link './proc/187/exe': No such file or directory
ls: cannot read symbolic link './proc/187/task/187/exe': No such file or directory
ls: cannot read symbolic link './proc/18768/exe': No such file or directory
ls: cannot read symbolic link './proc/18768/task/18768/exe': No such file or directory
ls: cannot read symbolic link './proc/18769/exe': No such file or directory
ls: cannot read symbolic link './proc/18769/task/18769/exe': No such file or directory
ls: cannot read symbolic link './proc/188/exe': No such file or directory
ls: cannot read symbolic link './proc/188/task/188/exe': No such file or directory
ls: cannot read symbolic link './proc/18866/exe': No such file or directory
ls: cannot read symbolic link './proc/18866/task/18866/exe': No such file or directory
ls: cannot read symbolic link './proc/189/exe': No such file or directory
ls: cannot read symbolic link './proc/189/task/189/exe': No such file or directory
ls: cannot read symbolic link './proc/19/exe': No such file or directory
ls: cannot read symbolic link './proc/19/task/19/exe': No such file or directory
ls: cannot read symbolic link './proc/190/exe': No such file or directory
ls: cannot read symbolic link './proc/190/task/190/exe': No such file or directory
ls: cannot read symbolic link './proc/191/exe': No such file or directory
ls: cannot read symbolic link './proc/191/task/191/exe': No such file or directory
ls: cannot read symbolic link './proc/192/exe': No such file or directory
ls: cannot read symbolic link './proc/192/task/192/exe': No such file or directory
ls: cannot read symbolic link './proc/193/exe': No such file or directory
ls: cannot read symbolic link './proc/193/task/193/exe': No such file or directory
ls: cannot read symbolic link './proc/194/exe': No such file or directory
ls: cannot read symbolic link './proc/194/task/194/exe': No such file or directory
ls: cannot read symbolic link './proc/195/exe': No such file or directory
ls: cannot read symbolic link './proc/195/task/195/exe': No such file or directory
ls: cannot read symbolic link './proc/196/exe': No such file or directory
ls: cannot read symbolic link './proc/196/task/196/exe': No such file or directory
ls: cannot read symbolic link './proc/19628/exe': No such file or directory
ls: cannot read symbolic link './proc/19628/task/19628/exe': No such file or directory
ls: cannot read symbolic link './proc/197/exe': No such file or directory
ls: cannot read symbolic link './proc/197/task/197/exe': No such file or directory
ls: cannot read symbolic link './proc/198/exe': No such file or directory
ls: cannot read symbolic link './proc/198/task/198/exe': No such file or directory
ls: cannot read symbolic link './proc/199/exe': No such file or directory
ls: cannot read symbolic link './proc/199/task/199/exe': No such file or directory
ls: cannot read symbolic link './proc/2/exe': No such file or directory
ls: cannot read symbolic link './proc/2/task/2/exe': No such file or directory
ls: cannot read symbolic link './proc/20/exe': No such file or directory
ls: cannot read symbolic link './proc/20/task/20/exe': No such file or directory
ls: cannot read symbolic link './proc/201/exe': No such file or directory
ls: cannot read symbolic link './proc/201/task/201/exe': No such file or directory
ls: cannot read symbolic link './proc/203/exe': No such file or directory
ls: cannot read symbolic link './proc/203/task/203/exe': No such file or directory
ls: cannot read symbolic link './proc/20341/exe': No such file or directory
ls: cannot read symbolic link './proc/20341/task/20341/exe': No such file or directory
ls: cannot read symbolic link './proc/205/exe': No such file or directory
ls: cannot read symbolic link './proc/205/task/205/exe': No such file or directory
ls: cannot read symbolic link './proc/206/exe': No such file or directory
ls: cannot read symbolic link './proc/206/task/206/exe': No such file or directory
ls: cannot read symbolic link './proc/207/exe': No such file or directory
ls: cannot read symbolic link './proc/207/task/207/exe': No such file or directory
ls: cannot read symbolic link './proc/21/exe': No such file or directory
ls: cannot read symbolic link './proc/21/task/21/exe': No such file or directory
ls: cannot read symbolic link './proc/21304/cwd': No such file or directory
ls: cannot read symbolic link './proc/21304/root': No such file or directory
ls: cannot read symbolic link './proc/21304/exe': No such file or directory
ls: reading directory './proc/21304/net': Invalid argument
ls: cannot read symbolic link './proc/21304/ns/net': No such file or directory
ls: cannot read symbolic link './proc/21304/ns/uts': No such file or directory
ls: cannot read symbolic link './proc/21304/ns/ipc': No such file or directory
ls: cannot read symbolic link './proc/21304/ns/mnt': No such file or directory
ls: cannot read symbolic link './proc/21304/ns/cgroup': No such file or directory
ls: cannot read symbolic link './proc/21304/task/21304/cwd': No such file or directory
ls: cannot read symbolic link './proc/21304/task/21304/root': No such file or directory
ls: cannot read symbolic link './proc/21304/task/21304/exe': No such file or directory
ls: reading directory './proc/21304/task/21304/net': Invalid argument
ls: cannot read symbolic link './proc/21304/task/21304/ns/net': No such file or directory
ls: cannot read symbolic link './proc/21304/task/21304/ns/uts': No such file or directory
ls: cannot read symbolic link './proc/21304/task/21304/ns/ipc': No such file or directory
ls: cannot read symbolic link './proc/21304/task/21304/ns/mnt': No such file or directory
ls: cannot read symbolic link './proc/21304/task/21304/ns/cgroup': No such file or directory
ls: cannot read symbolic link './proc/22/exe': No such file or directory
ls: cannot read symbolic link './proc/22/task/22/exe': No such file or directory
ls: cannot read symbolic link './proc/231/exe': No such file or directory
ls: cannot read symbolic link './proc/231/task/231/exe': No such file or directory
ls: cannot read symbolic link './proc/232/exe': No such file or directory
ls: cannot read symbolic link './proc/232/task/232/exe': No such file or directory
ls: cannot read symbolic link './proc/24/exe': No such file or directory
ls: cannot read symbolic link './proc/24/task/24/exe': No such file or directory
ls: cannot read symbolic link './proc/25/exe': No such file or directory
ls: cannot read symbolic link './proc/25/task/25/exe': No such file or directory
ls: cannot read symbolic link './proc/257/exe': No such file or directory
ls: cannot read symbolic link './proc/257/task/257/exe': No such file or directory
ls: cannot read symbolic link './proc/26/exe': No such file or directory
ls: cannot read symbolic link './proc/26/task/26/exe': No such file or directory
ls: cannot read symbolic link './proc/27/exe': No such file or directory
ls: cannot read symbolic link './proc/27/task/27/exe': No such file or directory
ls: cannot read symbolic link './proc/2730/cwd': No such file or directory
ls: cannot read symbolic link './proc/2730/root': No such file or directory
ls: cannot read symbolic link './proc/2730/exe': No such file or directory
ls: reading directory './proc/2730/net': Invalid argument
ls: cannot read symbolic link './proc/2730/ns/net': No such file or directory
ls: cannot read symbolic link './proc/2730/ns/uts': No such file or directory
ls: cannot read symbolic link './proc/2730/ns/ipc': No such file or directory
ls: cannot read symbolic link './proc/2730/ns/mnt': No such file or directory
ls: cannot read symbolic link './proc/2730/ns/cgroup': No such file or directory
ls: cannot read symbolic link './proc/2730/task/2730/cwd': No such file or directory
ls: cannot read symbolic link './proc/2730/task/2730/root': No such file or directory
ls: cannot read symbolic link './proc/2730/task/2730/exe': No such file or directory
ls: reading directory './proc/2730/task/2730/net': Invalid argument
ls: cannot read symbolic link './proc/2730/task/2730/ns/net': No such file or directory
ls: cannot read symbolic link './proc/2730/task/2730/ns/uts': No such file or directory
ls: cannot read symbolic link './proc/2730/task/2730/ns/ipc': No such file or directory
ls: cannot read symbolic link './proc/2730/task/2730/ns/mnt': No such file or directory
ls: cannot read symbolic link './proc/2730/task/2730/ns/cgroup': No such file or directory
ls: cannot read symbolic link './proc/28/exe': No such file or directory
ls: cannot read symbolic link './proc/28/task/28/exe': No such file or directory
ls: cannot read symbolic link './proc/30/exe': No such file or directory
ls: cannot read symbolic link './proc/30/task/30/exe': No such file or directory
ls: cannot read symbolic link './proc/31/exe': No such file or directory
ls: cannot read symbolic link './proc/31/task/31/exe': No such file or directory
ls: cannot read symbolic link './proc/31371/exe': No such file or directory
ls: cannot read symbolic link './proc/31371/task/31371/exe': No such file or directory
ls: cannot read symbolic link './proc/31376/exe': No such file or directory
ls: cannot read symbolic link './proc/31376/task/31376/exe': No such file or directory
ls: cannot read symbolic link './proc/31377/exe': No such file or directory
ls: cannot read symbolic link './proc/31377/task/31377/exe': No such file or directory
ls: cannot read symbolic link './proc/31382/exe': No such file or directory
ls: cannot read symbolic link './proc/31382/task/31382/exe': No such file or directory
ls: cannot read symbolic link './proc/31383/exe': No such file or directory
ls: cannot read symbolic link './proc/31383/task/31383/exe': No such file or directory
ls: cannot read symbolic link './proc/31384/exe': No such file or directory
ls: cannot read symbolic link './proc/31384/task/31384/exe': No such file or directory
ls: cannot read symbolic link './proc/31385/exe': No such file or directory
ls: cannot read symbolic link './proc/31385/task/31385/exe': No such file or directory
ls: cannot read symbolic link './proc/31386/exe': No such file or directory
ls: cannot read symbolic link './proc/31386/task/31386/exe': No such file or directory
ls: cannot read symbolic link './proc/31387/exe': No such file or directory
ls: cannot read symbolic link './proc/31387/task/31387/exe': No such file or directory
ls: cannot read symbolic link './proc/31434/exe': No such file or directory
ls: cannot read symbolic link './proc/31434/task/31434/exe': No such file or directory
ls: cannot read symbolic link './proc/32/exe': No such file or directory
ls: cannot read symbolic link './proc/32/task/32/exe': No such file or directory
ls: cannot read symbolic link './proc/34/exe': No such file or directory
ls: cannot read symbolic link './proc/34/task/34/exe': No such file or directory
ls: cannot read symbolic link './proc/35/exe': No such file or directory
ls: cannot read symbolic link './proc/35/task/35/exe': No such file or directory
ls: cannot read symbolic link './proc/36/exe': No such file or directory
ls: cannot read symbolic link './proc/36/task/36/exe': No such file or directory
ls: cannot read symbolic link './proc/37/exe': No such file or directory
ls: cannot read symbolic link './proc/37/task/37/exe': No such file or directory
ls: cannot read symbolic link './proc/38/exe': No such file or directory
ls: cannot read symbolic link './proc/38/task/38/exe': No such file or directory
ls: cannot read symbolic link './proc/382/exe': No such file or directory
ls: cannot read symbolic link './proc/382/task/382/exe': No such file or directory
ls: cannot read symbolic link './proc/39/exe': No such file or directory
ls: cannot read symbolic link './proc/39/task/39/exe': No such file or directory
ls: cannot read symbolic link './proc/392/exe': No such file or directory
ls: cannot read symbolic link './proc/392/task/392/exe': No such file or directory
ls: cannot read symbolic link './proc/399/exe': No such file or directory
ls: cannot read symbolic link './proc/399/task/399/exe': No such file or directory
ls: cannot read symbolic link './proc/4/exe': No such file or directory
ls: cannot read symbolic link './proc/4/task/4/exe': No such file or directory
ls: cannot read symbolic link './proc/40/exe': No such file or directory
ls: cannot read symbolic link './proc/40/task/40/exe': No such file or directory
ls: cannot read symbolic link './proc/41/exe': No such file or directory
ls: cannot read symbolic link './proc/41/task/41/exe': No such file or directory
ls: cannot read symbolic link './proc/42/exe': No such file or directory
ls: cannot read symbolic link './proc/42/task/42/exe': No such file or directory
ls: cannot read symbolic link './proc/43/exe': No such file or directory
ls: cannot read symbolic link './proc/43/task/43/exe': No such file or directory
ls: cannot read symbolic link './proc/4359/exe': No such file or directory
ls: cannot read symbolic link './proc/4359/task/4359/exe': No such file or directory
ls: cannot read symbolic link './proc/4360/exe': No such file or directory
ls: cannot read symbolic link './proc/4360/task/4360/exe': No such file or directory
ls: cannot read symbolic link './proc/4361/exe': No such file or directory
ls: cannot read symbolic link './proc/4361/task/4361/exe': No such file or directory
ls: cannot read symbolic link './proc/4369/exe': No such file or directory
ls: cannot read symbolic link './proc/4369/task/4369/exe': No such file or directory
ls: cannot read symbolic link './proc/44/exe': No such file or directory
ls: cannot read symbolic link './proc/44/task/44/exe': No such file or directory
ls: cannot read symbolic link './proc/45/exe': No such file or directory
ls: cannot read symbolic link './proc/45/task/45/exe': No such file or directory
ls: cannot read symbolic link './proc/4512/exe': No such file or directory
ls: cannot read symbolic link './proc/4512/task/4512/exe': No such file or directory
ls: cannot read symbolic link './proc/46/exe': No such file or directory
ls: cannot read symbolic link './proc/46/task/46/exe': No such file or directory
ls: cannot read symbolic link './proc/47/exe': No such file or directory
ls: cannot read symbolic link './proc/47/task/47/exe': No such file or directory
ls: cannot read symbolic link './proc/51/exe': No such file or directory
ls: cannot read symbolic link './proc/51/task/51/exe': No such file or directory
ls: cannot read symbolic link './proc/52/exe': No such file or directory
ls: cannot read symbolic link './proc/52/task/52/exe': No such file or directory
ls: cannot read symbolic link './proc/53/exe': No such file or directory
ls: cannot read symbolic link './proc/53/task/53/exe': No such file or directory
ls: cannot read symbolic link './proc/54/exe': No such file or directory
ls: cannot read symbolic link './proc/54/task/54/exe': No such file or directory
ls: cannot read symbolic link './proc/55/exe': No such file or directory
ls: cannot read symbolic link './proc/55/task/55/exe': No such file or directory
ls: cannot read symbolic link './proc/6/exe': No such file or directory
ls: cannot read symbolic link './proc/6/task/6/exe': No such file or directory
ls: cannot read symbolic link './proc/611/exe': No such file or directory
ls: cannot read symbolic link './proc/611/task/611/exe': No such file or directory
ls: cannot read symbolic link './proc/612/exe': No such file or directory
ls: cannot read symbolic link './proc/612/task/612/exe': No such file or directory
ls: cannot read symbolic link './proc/6957/exe': No such file or directory
ls: cannot read symbolic link './proc/6957/task/6957/exe': No such file or directory
ls: cannot read symbolic link './proc/6962/exe': No such file or directory
ls: cannot read symbolic link './proc/6962/task/6962/exe': No such file or directory
ls: cannot read symbolic link './proc/7/exe': No such file or directory
ls: cannot read symbolic link './proc/7/task/7/exe': No such file or directory
lrwxrwxrwx 1 root root 0 Jan 10 06:14 exe -> /usr/lib/virtualbox/VirtualBox
l-wx------ 1 root root 64 Jan 10 06:14 29 -> /home/tom/.config/VirtualBox/selectorwindow.log
lr-------- 1 root root 64 Jan 10 08:46 400000-425000 -> /usr/lib/virtualbox/VirtualBox
lr-------- 1 root root 64 Jan 10 08:46 624000-625000 -> /usr/lib/virtualbox/VirtualBox
lr-------- 1 root root 64 Jan 10 08:46 625000-626000 -> /usr/lib/virtualbox/VirtualBox
lr-------- 1 root root 64 Jan 10 08:46 7f06ad757000-7f06ae086000 -> /usr/lib/virtualbox/VirtualBox.so
lr-------- 1 root root 64 Jan 10 08:46 7f06ae086000-7f06ae285000 -> /usr/lib/virtualbox/VirtualBox.so
lr-------- 1 root root 64 Jan 10 08:46 7f06ae285000-7f06ae2c8000 -> /usr/lib/virtualbox/VirtualBox.so
lr-------- 1 root root 64 Jan 10 08:46 7f06ae2c8000-7f06ae2cd000 -> /usr/lib/virtualbox/VirtualBox.so
lrwxrwxrwx 1 root root 0 Jan 10 08:41 exe -> /usr/lib/virtualbox/VirtualBox
l-wx------ 1 root root 64 Jan 10 08:46 29 -> /home/tom/.config/VirtualBox/selectorwindow.log
lrwxrwxrwx 1 root root 0 Jan 10 08:41 exe -> /usr/lib/virtualbox/VirtualBox
l-wx------ 1 root root 64 Jan 10 08:46 29 -> /home/tom/.config/VirtualBox/selectorwindow.log
lrwxrwxrwx 1 root root 0 Jan 10 08:41 exe -> /usr/lib/virtualbox/VirtualBox
l-wx------ 1 root root 64 Jan 10 08:46 29 -> /home/tom/.config/VirtualBox/selectorwindow.log
lrwxrwxrwx 1 root root 0 Jan 10 08:41 exe -> /usr/lib/virtualbox/VirtualBox
l-wx------ 1 root root 64 Jan 10 08:46 29 -> /home/tom/.config/VirtualBox/selectorwindow.log
lrwxrwxrwx 1 root root 0 Jan 10 08:41 exe -> /usr/lib/virtualbox/VirtualBox
l-wx------ 1 root root 64 Jan 10 08:46 29 -> /home/tom/.config/VirtualBox/selectorwindow.log
lrwxrwxrwx 1 root root 0 Jan 10 08:41 exe -> /usr/lib/virtualbox/VirtualBox
l-wx------ 1 root root 64 Jan 10 08:46 29 -> /home/tom/.config/VirtualBox/selectorwindow.log
l-wx------ 1 tom tom 64 Jan 10 06:14 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
l-wx------ 1 tom tom 64 Jan 10 08:41 8 -> /home/tom/.config/VirtualBox/VBoxSVC.log
ls: cannot read symbolic link './proc/8/exe': No such file or directory
ls: cannot read symbolic link './proc/8/task/8/exe': No such file or directory
ls: cannot read symbolic link './proc/9/exe': No such file or directory
ls: cannot read symbolic link './proc/9/task/9/exe': No such file or directory
ls: cannot read symbolic link './proc/9328/exe': No such file or directory
ls: cannot read symbolic link './proc/9328/task/9328/exe': No such file or directory
ls: cannot read symbolic link './proc/95/exe': No such file or directory
ls: cannot read symbolic link './proc/95/task/95/exe': No such file or directory
ls: cannot read symbolic link './proc/96/exe': No such file or directory
ls: cannot read symbolic link './proc/96/task/96/exe': No such file or directory
ls: cannot read symbolic link './proc/98/exe': No such file or directory
ls: cannot read symbolic link './proc/98/task/98/exe': No such file or directory
ls: cannot read symbolic link './proc/99/exe': No such file or directory
ls: cannot read symbolic link './proc/99/task/99/exe': No such file or directory
ls: cannot access './run/user/1000/gvfs': Permission denied
ls: cannot open directory './run/user/1000/gvfs': Permission denied
lrwxrwxrwx 1 root root          27 Nov  9 19:18 VirtualBox -> ../share/virtualbox/VBox.sh
-rw-r--r-- 1 root root 122343 Nov  9 18:27 VirtualBox_constants.py
-rw-r--r-- 1 root root  62006 Jan  9 23:56 VirtualBox_constants.pyc
-rwsr-sr-x 1 root root   154184 Nov  9 19:19 VirtualBox
-rw-r--r-- 1 root root  9921448 Nov  9 19:19 VirtualBox.so
-rw-r--r-- 1 root root   90268 Nov  9 18:31 VirtualBox_XPCOM.xpt
lrwxrwxrwx 1 root root     15 Nov  9 19:18 virtualbox.1.gz -> VirtualBox.1.gz
-rw-r--r-- 1 root root    898 Nov  9 19:18 VirtualBox.1.gz
-rw-r--r-- 1 root root 389980 Nov  9 18:27 VirtualBox_bg.qm
-rw-r--r-- 1 root root 394441 Nov  9 18:27 VirtualBox_ca.qm
-rw-r--r-- 1 root root 283103 Nov  9 18:27 VirtualBox_ca_VA.qm
-rw-r--r-- 1 root root 363335 Nov  9 18:27 VirtualBox_cs.qm
-rw-r--r-- 1 root root 366906 Nov  9 18:27 VirtualBox_da.qm
-rw-r--r-- 1 root root 388326 Nov  9 18:27 VirtualBox_de.qm
-rw-r--r-- 1 root root 400921 Nov  9 18:27 VirtualBox_el.qm
-rw-r--r-- 1 root root   3747 Nov  9 18:27 VirtualBox_en.qm
-rw-r--r-- 1 root root 397363 Nov  9 18:27 VirtualBox_es.qm
-rw-r--r-- 1 root root 384957 Nov  9 18:27 VirtualBox_eu.qm
-rw-r--r-- 1 root root 353695 Nov  9 18:27 VirtualBox_fa_IR.qm
-rw-r--r-- 1 root root 114853 Nov  9 18:27 VirtualBox_fi.qm
-rw-r--r-- 1 root root 395509 Nov  9 18:27 VirtualBox_fr.qm
-rw-r--r-- 1 root root 133179 Nov  9 18:27 VirtualBox_gl_ES.qm
-rw-r--r-- 1 root root  78338 Nov  9 18:27 VirtualBox_he.qm
-rw-r--r-- 1 root root 365660 Nov  9 18:27 VirtualBox_hu.qm
-rw-r--r-- 1 root root 379629 Nov  9 18:27 VirtualBox_id.qm
-rw-r--r-- 1 root root 398279 Nov  9 18:27 VirtualBox_it.qm
-rw-r--r-- 1 root root 288062 Nov  9 18:27 VirtualBox_ja.qm
-rw-r--r-- 1 root root 147472 Nov  9 18:27 VirtualBox_km_KH.qm
-rw-r--r-- 1 root root 288638 Nov  9 18:27 VirtualBox_ko.qm
-rw-r--r-- 1 root root 189805 Nov  9 18:27 VirtualBox_lt.qm
-rw-r--r-- 1 root root 393711 Nov  9 18:27 VirtualBox_nl.qm
-rw-r--r-- 1 root root 157424 Nov  9 18:27 VirtualBox_pl.qm
-rw-r--r-- 1 root root 398611 Nov  9 18:27 VirtualBox_pt_BR.qm
-rw-r--r-- 1 root root 141934 Nov  9 18:27 VirtualBox_pt.qm
-rw-r--r-- 1 root root 119899 Nov  9 18:27 VirtualBox_ro.qm
-rw-r--r-- 1 root root 391183 Nov  9 18:27 VirtualBox_ru.qm
-rw-r--r-- 1 root root 115499 Nov  9 18:27 VirtualBox_sk.qm
-rw-r--r-- 1 root root 380013 Nov  9 18:27 VirtualBox_sl.qm
-rw-r--r-- 1 root root 176240 Nov  9 18:27 VirtualBox_sr.qm
-rw-r--r-- 1 root root 276902 Nov  9 18:27 VirtualBox_sv.qm
-rw-r--r-- 1 root root 382625 Nov  9 18:27 VirtualBox_tr.qm
-rw-r--r-- 1 root root 382015 Nov  9 18:27 VirtualBox_uk.qm
-rw-r--r-- 1 root root 259284 Nov  9 18:27 VirtualBox_zh_CN.qm
-rw-r--r-- 1 root root 263997 Nov  9 18:27 VirtualBox_zh_TW.qm



```

But the below command seems to fail.

```
/usr/lib/virtualbox$ vboxmanage dhcpserver add &#8211;netname mydhcpnetwork &#8211;ip 10.10.10.1 &#8211;netmask 255.255.255.0 &#8211;lowerip 10.10.10.2 &#8211;upperip 10.10.10.10 &#8211;enable


Oracle VM VirtualBox Command Line Management Interface Version 5.0.40_Ubuntu
(C) 2005-2017 Oracle Corporation
All rights reserved.


Usage:


VBoxManage dhcpserver       add|modify --netname <network_name> |
                                       --ifname <hostonly_if_name>
                            [--ip <ip_address>
                            --netmask <network_mask>
                            --lowerip <lower_ip>
                            --upperip <upper_ip>]
                            [--enable | --disable]


VBoxManage dhcpserver       remove --netname <network_name> |
                                   --ifname <hostonly_if_name>



```

How do I fix this problem?

---

