---
title: "Can't Change Hostname in 18.04 Server"
date: 2018-04-11
forum: Ubuntu Development Version
---

### Post by chuckhenry.nnyln on 2018-04-11
I'm missing something. Thanks in advance for your suggestions. I've been trying to change the hostname of a 18.04 server. No matter what I've tried, after a reboot it returns to the original host name.

There's a few blogs out there with instructions but I haven't been able to get any of them to work.

So here's the output from hostnamectl:
```
   Static hostname: ubuntuserver1804         Icon name: computer-vm
           Chassis: vm
        Machine ID: 3b79eae1ec8942ef9b20e15fff3c301e
           Boot ID: 7248a39eedd4466a8869c586900153a0
    Virtualization: oracle
  Operating System: Ubuntu Bionic Beaver (development branch)
            Kernel: Linux 4.15.0-13-generic
      Architecture: x86-64
```

First I tried: sudo hostnamectl set-hostname nyshn2
No additional output.

```
chief@ubuntuserver1804:~$ hostnamectl   
Static hostname: nyshn2
         Icon name: computer-vm
           Chassis: vm
        Machine ID: 3b79eae1ec8942ef9b20e15fff3c301e
           Boot ID: 27eabc4caabf4dff958401a1a54d6bff
    Virtualization: oracle
  Operating System: Ubuntu Bionic Beaver (development branch)
            Kernel: Linux 4.15.0-13-generic
      Architecture: x86-64
```

After logging out and back in again my prompt says: chief@nyshn2
```
cat /etc/hostname
nyshn2
```
OK, right? However, after a reboot we're back to: 
```
chief@ubuntuserver1804:~$ hostnamectl   
Static hostname: ubuntuserver1804
         Icon name: computer-vm
           Chassis: vm
        Machine ID: 3b79eae1ec8942ef9b20e15fff3c301e
           Boot ID: 27eabc4caabf4dff958401a1a54d6bff
    Virtualization: oracle
  Operating System: Ubuntu Bionic Beaver (development branch)
            Kernel: Linux 4.15.0-13-generic
      Architecture: x86-64
```

Some of the instructions I found suggested directly editing /etc/hostname and replacing the name there. I've done that. Also some suggest editing /etc/hosts like this:
```
127.0.0.1    localhost.localdomain    localhost    nyshn2
::1        localhost6.localdomain6    localhost6


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

However, after any reboot the /etc/hostname returns to the original name.  What am I missing? Is there someplace else the hostname needs to be set?

---

### Post by SeijiSensei on 2018-04-11
How about just

```
sudo hostname name
```

That's been the standard method for decades.

---

### Post by chuckhenry.nnyln on 2018-04-11
No love. I tried: sudo hostname nyshn2
Then I rebooted the server. Came back up as ubuntuserver1804.

---

### Post by logix2 on 2018-04-11
First step: edit [COLOR=#000000] /etc/hostname[/COLOR] and [COLOR=#000000][FONT=&quot]/etc/hosts [/FONT][/COLOR]manually and change the host to the new one. Next, run:
sudo hostnamectl set-hostname <new-hostname>
[FONT=Consolas]This is what worked for me.[/FONT]

---

### Post by chuckhenry.nnyln on 2018-04-11
Also no love. After a reboot it returns to the original value. Thanks for the suggestion!

---

### Post by logix2 on 2018-04-11
I edited my post. I forgot to mention it requires editing both /etc/hostname and /etc/hosts. Sorry about that.

---

### Post by chuckhenry.nnyln on 2018-04-11
logix2, I already have the /etc/hosts file modified. Perhaps what I have isn't right? Here's what I have at the moment:
```
chief@ubuntuserver1804:~$ cat /etc/hosts
127.0.0.1    localhost.localdomain    localhost    nyshn2
::1        localhost6.localdomain6    localhost6


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by logix2 on 2018-04-11
Here's mine:
```
logix@logix-laptop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	logix-laptop


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by chuckhenry.nnyln on 2018-04-11
logix2, I did the following:

Changed the hostname in /etc/hostname to nyshn2.
Modified /etc/hosts to read:
```

127.0.0.1	localhost.localdomain	localhost
127.0.0.1	nyshn2
::1		localhost6.localdomain6	localhost6


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Then ran: sudo hostnamectl set-hostname nyshn2
Afterwards, I rebooted the server. And it's back the original again.

```

chief@ubuntuserver1804:~$ hostnamectl
   Static hostname: ubuntuserver1804
         Icon name: computer-vm
           Chassis: vm
        Machine ID: 3b79eae1ec8942ef9b20e15fff3c301e
           Boot ID: c572c52e10ac40ffac57f2afaa1b9afb
    Virtualization: oracle
  Operating System: Ubuntu Bionic Beaver (development branch)
            Kernel: Linux 4.15.0-13-generic
      Architecture: x86-64
```

---

### Post by zika on 2018-04-11
You're trying all this from a VM?
[SIZE=1]Do use code tags for commands so we can see them right...[/SIZE]

---

### Post by chuckhenry.nnyln on 2018-04-11
Yes. It's a VM.

---

### Post by The Cog on 2018-04-11
Re post #9:
I think the second line is supposed to be 127.0.1.1 not 127.0.0.1. Here is my hosts file, as created by the installer.
```
steve@Steves-PC:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	Steves-PC

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

I wonder if your machine is picking up an old hostname from a DHCP server that has learned it from you. I have seen that before,  and even reinstalling didn't help because the DHCP server still remembered and told me my hostname again.

---

### Post by chuckhenry.nnyln on 2018-04-11
I gave it a try with 127.0.1.1 and it didn't work either. The server has a static IP address so I doubt the DHCP has much to do with it.

---

### Post by faromano on 2018-04-12
> **chuckhenry.nnyln said:**
> I gave it a try with 127.0.1.1 and it didn't work either. The server has a static IP address so I doubt the DHCP has much to do with it.

Hi,

I had the same problem. You can try to remove ubuntu cloud packages:
apt remove cloud-init    cloud-initramfs-copymods      cloud-initramfs-dyn-netconf

Then you can try to change hostname with hostnamectl.

---

### Post by chuckhenry.nnyln on 2018-04-12
Winner winner chicken dinner!

Yes! Removing cloud-init cloud-initramfs-copymods cloud-initramfs-dyn-netconf and then running sudo hostnamectl set-hostname nyshn2 worked!

Thanks everyone for your help!

---

### Post by modiford2 on 2018-04-25
> **faromano said:**
> Hi,

I had the same problem. You can try to remove ubuntu cloud packages:
apt remove cloud-init    cloud-initramfs-copymods      cloud-initramfs-dyn-netconf

Then you can try to change hostname with hostnamectl.

As the only post in existence that explained the remedy to this issue, I thank you very much.

Guess that's yet ANOTHER annoyance from the Canonical Factory alongside NetPlan / YAML nonsense and MySQL not asking for a password during installation with this Bionic release...

---

### Post by jbicha on 2018-04-26
Specifically, it's cloud-init. Try changing /etc/cloud/cloud.cfg's preserve_hostname line to true

---

### Post by dankegel on 2018-04-26
On 18.04 I just edited /etc/hosts and /etc/hostname, then rebooted.  I didn't bother with hostnamectl.  Seemed to work.

---

### Post by LHammonds on 2018-05-03
> **dankegel said:**
> On 18.04 I just edited /etc/hosts and /etc/hostname, then rebooted.  I didn't bother with hostnamectl.  Seemed to work.
In the finial release, this is the difference between the "live" ISO and the "alternative"

The "live" ISO image has the cloud-init package and thus you need to edit **preserve_hostname** in /etc/cloud/cloud.cfg

We are trying to document such differences in the final product between the "live" and "alternative" ISO images here: [https://ubuntuforums.org/showthread.php?t=2390785](https://ubuntuforums.org/showthread.php?t=2390785)

LHammonds

---

### Post by cariboo on 2018-05-03
Thread Closed, as Bionic has been released.

---

