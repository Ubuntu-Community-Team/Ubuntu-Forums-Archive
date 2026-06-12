---
title: "share fresh VirtualBox with Ubuntu12 hostname to windows10 host"
date: 2017-07-20
forum: Virtualisation
---

### Post by omargaliot on 2017-07-20
My Ubuntu12 has its own hostname, I can ping frm itself to itself by ping user@user-VirtualBox (user-VirtualBox is the computer name).
But from the windows 10 I can't! It don't know that hostname!

---

### Post by &amp;KyT$0P# on 2017-07-20
Is your VM connected to a host-only network?
Can you ping it by IP address?

---

### Post by QIII on 2017-07-20
Hello!

Both Ubuntu 12.04 and Ubuntu 12.10 are beyond End Of Life and neither is supported any longer.

Before you consume the valuable time of our volunteers by asking them to help you with an unsupported release, please upgrade your installation to a supported release.

Thank you.

---

### Post by SeijiSensei on 2017-07-21
> **omargaliot said:**
> But from the windows 10 I can't! It don't know that hostname!
Not a Linux issue.  You must add the machine's name and IP address to the [Windows hosts file]("https://en.wikipedia.org/wiki/Hosts_(file)").

---

### Post by efflandt on 2017-07-22
When you configure virtualbox on the host for a guest, the default is a NAT network, where guest could contact the host, but host or LAN cannot contact the guest. Under the Network tab for configuring virtualbox on the host you would need to set "Bridged Adapter" if you want to contact the guest from host or connected LAN. If your network has DHCP that should automatically assign the guest a LAN IP (different from host IP). The guest IP will likely NOT show up on the host networking (at least it does not on Linux host), you should be able to contact the guest IP from host or LAN. But unless you have DNS or mdns (like samba server on the guest) to resolve the guest's IP, you might not be able to access the guest by hostname.

---

### Post by omargaliot on 2017-07-23
Hi all and thank you!

1. halogen2 - the VM is connected using the "Bridged Adapter" to the ethernet network cable. And yes, I can ping from windows to vm and from vm to windows. both OS can ping to Internet (google...).
2. Qlll - I can't, I'm using that VM for specific sources that cannot be handled on ubuntu14 or 16.
3. SeijiSensei - It looks like linux issue, since when I've installed on the same way ubuntu16 on the vm, the default hostname was pingable from the windows.
4. efflandt - as I've described, I'm using bridged adapter. I can ping the vm using the vm ip frm the windows. I've also installed samba on the vm, and succeeded to access shared folder at the linux using samba, from the windows.

---

### Post by omargaliot on 2017-07-25
anybody?

---

### Post by SeijiSensei on 2017-07-25
Until you upgrade to a currently supported version of Ubuntu, there's little we can do.

---

### Post by omargaliot on 2017-07-25
[COLOR=#000000]2. Qlll - I can't, I'm using that VM for specific sources that cannot be handled on ubuntu14 or 16.[/COLOR]

---

### Post by efflandt on 2017-07-25
You said "I can ping the vm using the vm ip frm the windows. I've also installed  samba on the vm, and succeeded to access shared folder at the linux  using samba, from the windows.", what more do you need?

From **ifconfig** and **route -n** commands find out netmask, and default gateway (UG) on guest, then set the guest to a static IP on the LAN and also set netmask, gateway (LAN IP of router), nameserver(s) typically also LAN IP of router. Then add name and static IP of guest to **hosts** and/or **lmhosts** file of Windows host or any other LAN computer. However, Windows will usually not allow you to edit and save those files directly, you may need to temporarily save to your Windows home directory, then copy over the original files as administrator (then reboot Windows). Those hosts files in Windows are typically in Windows\System32\drivers\etc, but lmhosts.sam is just an example, which should be named just lmhosts to be active. Make sure that you have Windows set to NOT hide known filename extensions, because hosts.txt (where you do not see the hidden .txt) will not work.

---

### Post by omargaliot on 2017-07-26
Hi efflandt,

I want the automatically generated hostname by ubuntu (username-pcname),
to be automatically shared to the windows pc.
on Ubuntu16 it being shared automatically, probably via the DNS or something like that.
I want to get this happen automatically on ubuntu12, and search for the lack that I need to add...

Thank you!

---

