---
title: "Installing windows server as a kvm guest on ubuntu 8.10 (interpid)"
date: 2009-10-17
forum: Virtualisation
---

### Post by vganesh on 2009-10-17
Hello, 

Issues with virtualization using kvm on ubuntu 8.1 (interpid) with Windows Server as client.  

I followed the instructions from [http://www.howtoforge.com/installing-windows-xp-as-a-kvm-guest-on-ubuntu-8.10-desktop-p3](http://www.howtoforge.com/installing-windows-xp-as-a-kvm-guest-on-ubuntu-8.10-desktop-p3) and successfully installed and login to a Windows Server 2003 client. Thanks a lot for this wonderful instructions. 

Now I am running into two issues, **[COLOR="Red"]not able to read the CD and no network connections from Windows client[/COLOR]**. Please see the attached screenshot.png file.    

1. From Windows Server 2003 client, I am not able to read the CD (D: drive). What steps do I need to follow so that from Windows client the CD information can be accessed? Are there instructions available somewhere I can follow? 

2. What steps do I need to follow to enable networks from Windows client? Output from ipconfig and netstat commands,from a command prompt, on Windows, are empty. 

I tried to follow the steps listed at [http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers](http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers). The author of this article has mentioned these instructions were tested on Fedora not ubuntu. I have burned the ISO format drivers to a CD successfully. The files in this CD are listed below. However, I can't access these files from Windows client though. [COLOR="Red"]I can't read any USB ports either from Windows client.[/COLOR]  

<user-name>@ubuntu:~$ ls /media/CDROM/
kvm-guest-drivers-linux-1.tar.gz  Windows 2000  Windows XP
<user-name>@ubuntu:~$ 

I am not able to complete the step "Reboot Windows Guest using Virtio Option" successfully. The qemu-system-x86_64 command fails as shown below. I guess the parameters for this command are not quite right for ubuntu and maybe they will work on fedora or maybe nic model is not correct.  

<user-name>@ubuntu:~$ qemu-system-x86_64 -hda /host/ubuntu/win2000server.img -net nic,model=virtio -net user ...
[COLOR="DarkRed"]qemu: Unsupported NIC: virtio[/COLOR]
<user-name>@ubuntu:~$ qemu-system-x86_64 -hda /host/ubuntu/win2000server.img -net nic,model=virtio -net user 
qemu: Unsupported NIC: virtio
<user-name>@ubuntu:~$ qemu-system-x86_64 -hda /host/ubuntu/win2000server.img -net nic,model=virtio -net tap
warning: could not open /dev/net/tun: no virtual network emulation
Could not initialize device 'tap'
<user-name>@ubuntu:~$ 


I thought model virtio is not the correct nic on my computer. From the output of the command 'lspci -tv' I could see that I have Intel's interface controller but I do not know what must be the model name for it that must be passed as a parameter to the above command. 


<user-name>@ubuntu:~$ lspci -tv
...
    +-1f.0  Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller
...

Thanks and regards, 
Ganesh

---

