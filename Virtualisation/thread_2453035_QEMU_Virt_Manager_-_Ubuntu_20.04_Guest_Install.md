---
title: "QEMU Virt Manager - Ubuntu 20.04 Guest Install"
date: 2020-11-02
forum: Virtualisation
---

### Post by Quarkrad on 2020-11-02
I have managed to install a ubuntu mate 20.04 guest following a win10 guest install.   During the win10 install I had to install Spice-Tools which all went OK.  I have downloaded spice-vdagent-0.19.0.tar.bz2 and unpacked it into my 20.04 environment but at my level of understanding the Readme is not clear how to install these spice tools for 20.04.  Any help/advice appreciated.

---

### Post by Quarkrad on 2020-11-02
I have just read I need to install spice-vdagent spice-webdavd and did that via Synaptic - it looks like this has solved the problem.  The screen resolution is not right but it looks good when viewing 'full screen' rather than in the virt manager window.

---

### Post by TheFu on 2020-11-02
Spice is the protocol used from the client machine to the VM running either local or remote. Inside the VM settings, just enable the spice protocol and choose the QXL video driver.

From your desktop, you'll use a normal connection with virt-viewer to access the guest desktop.  A concrete example.  I use this script:
$ more ~/bin/regulus 
```
#!/bin/bash
GO=regulus
if [[ $HOSTNAME == "hadar" ]] ; then
    # For local connection on hadar
    /usr/bin/virt-viewer -a -d  $GO &
else
    # For remote connections on the LAN
    /usr/bin/virt-viewer --connect qemu+ssh://hadar/system $GO &
fi
```

Hadar is my VM host machine, but I often connect from laptops and need the ssh-tunnel for security.  My normal userid has ssh-keys setup between the laptop and hadar. Also, hadar is in the local DNS, so the --connect stuff works.  virt-viewer has spice built-in. That works if the "laptop" machine is running windows too, but I don't know how to have ssh-keys setup to "just work" myself.  I have helped others running the WSL2 on Win10 setup keys and from the bash/powershell prompt, it did work, but they weren't interested in spice. They just wanted scp, sftp and ssh to work, which it did.

That same script works on any desktop here.  When remote, I'd need for ssh to work through firewalls and port forwards into hadar. In general, I don't allow VM hosts to be directly accessed over the internet, but through an openvpn or wireguard VPN, to provide LAN access, it should be fine. Those VPNs wouldn't run on hadar. They'd run in a VM.

---

