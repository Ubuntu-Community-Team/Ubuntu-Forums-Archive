---
title: "virt-manager doesn't connect to KVM server"
date: 2022-07-22
forum: Virtualisation
---

### Post by Heeter on 2022-07-22
Hi all,

I am transitioning from an old laptop to a newer one.

I installed virt-manager on the new laptop, but it is refusing to connect to the local KVM server:
```

Unable to connect to libvirt qemu+ssh://root@192.168.1.148/system.

Configure SSH key access for the remote host, or install an SSH askpass package locally.

Libvirt URI is: qemu+ssh://root@192.168.1.148/system

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 956, in _do_open
    self._backend.open(connectauth.creds_dialog, self)
  File "/usr/share/virt-manager/virtinst/connection.py", line 172, in open
    conn = libvirt.openAuth(self._open_uri,
  File "/usr/lib/python3/dist-packages/libvirt.py", line 104, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirt.libvirtError: Cannot recv data: ssh_askpass: exec(/usr/bin/ssh-askpass): No such file or directory

```

I have tried installing askpass, try continuously entering my password, not working
I have tried moving the .ssh folder from the old laptop, doesn't work either
libvirtd service is working on server

virt-manager on the old laptop is connecting without issues

Any assistance would be great

---

### Post by TheFu on 2022-07-23
Some ssh defaults have changed over time with the different releases.  This is a client -to- KVM-server thing, not necessarily to each VM-guest machine.

So, does ssh work from the client to the KVM server?  If not, fix that.  I have an ssh troubleshooting blog entry: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) which might be helpful.  It was created pre-systemd, so any of those commands need to be switched out to the systemctl version. 

I am still using the ssh-keygen command shown there. I stopped using RSA keys a long time ago.  22.04 has something about ssh in the release notes. They changed some of the supported ciphers and the order each is attempted.  Best to just wipe them all and create new keys if there is any chance of a problem, IMHO.

---

### Post by Heeter on 2022-07-28
Hi TheFU

My apologies for the late reply

Yes I can ssh into both the KVM server and into all guests from the remote laptop

I wiped the the known hosts file inside the remote laptop .ssh folder, but still getting the same virt-manager error

Any other suggestions?

Thank you

---

### Post by TheFu on 2022-07-29
ssh into any VM clients isn't needed, just into the KVM/libvirt server.  Just ensure that your userid on the server system is a member of the libvirtd group.  The  libvirt URI is something like:  qemu+ssh://thefu@romulus/system  That connection is shared for management and all double-click "open" to running guest VMs.  Obviously, "romulus" has to be known by the IP stack on the client - that can be through DNS or mDNS or /etc/hosts settings.

---

### Post by MAFoElffen on 2022-07-29
> **TheFu said:**
> ... [COLOR=#ff0000] Just ensure that your userid on the server system is a member of the **libvirtd** group.[/COLOR]  ...
@TheFu -

Remember? You and I have been around KVM many years. The group membership for KVM used to be libvirtd [COLOR=#ff0000]prior[/COLOR] to Ubuntu 18.04...

At 18.04 and newer, the required Group membership changed to both kvm and libvirt...

---

### Post by TheFu on 2022-07-29
> **MAFoElffen said:**
> @TheFu -

Remember? You and I have been around KVM many years. The group membership for KVM used to be libvirtd [COLOR=#ff0000]prior[/COLOR] to Ubuntu 18.04...

At 18.04 and newer, the required Group membership changed to both kvm and libvirt...

My KVM hosts are still on 18.04.  BTW, I check the group membership here. Select/pasted the exact groupname from my membership to be certain.  
```
...,110(lxd),116(libvirtd),117(lpadmin),...
```
If the groupname has changed in 20.04 or later, IDK.  I also checked that membership in the workstation with virt-manager installed doesn't matter. The workstation I checked from was running 20.04.

So, if things have changed, which is definitely possible, use the right groupname.  The libvirt-whatever group would be added by the libvirt installer - just need to ensure your username is a member.

Because I've slept since this was pointed out last time, I don't clearly recall the change. Sorry.  Certain things aren't at the top of any list to remember and this idea is just a guess - maybe 30% likely to be the cause, but it is all I got.

Oh ... and don't use root!   Never use root!   Login with your real username, never root!  I suspect you didn't enable the root account and didn't put the ssh keys into the ~root/.ssh/ location.  Don't use root for virt-manager stuff. It isn't needed.

---

### Post by Heeter on 2022-07-30
Hey all,

Thank you for your responses.

But if my old laptop is connecting through virt-manager with no issues, wouldn't it be that my new installed laptop virt-manager is the problem?

How do I check the server if user is part of group?

Thank you

---

### Post by TheFu on 2022-07-30
Depends.  Which libvirt version does the VM server run?  Is it older than the new workstation?  Software may be backwards compatible, but is seldom "forwards compatible" since nobody can see the future.

Maybe tomorrow, I'll build a 22.04 desktop in a VM and see if the virt-manager can connect and control any of my KVM servers.  I have a 22.04 server for testing, but no desktops.

---

### Post by The Cog on 2022-07-31
According to post #1, virt-manager is trying to connect to root@192.168.1.148. Is it possible to ssh to root@192.168.1.148? Probably not. Could the old laptop? I think probably yes.

One way to fix this is to copy the caller's public key to /root/.ssh/authorized_keys on the kvm host. If you look at /root/.ssh/authorized_keys on the kvm host, is the old laptop's public key already there?

A better way might be to get virt-manager to connect as a normal user, and arrange permissions (membership of kvm group perhaps? I don't know).

---

### Post by TheFu on 2022-07-31
So, I setup Xubuntu 22.04 today in a minimal way. Then setup ssh keys from the workstation to the KVM server.

This is what I installed:
```
sudo apt install virt-manager ssh fail2ban 
```

Then I generated keys for my userid.
```
$ ssh-keygen -t ed25519
```
Then I pushed the public key to two KVM hosts.
```

$ ssh-copy-id -i ~/.ssh/id_ed25519.pub hadar
$ ssh-copy-id -i ~/.ssh/id_ed25519.pub istar
```

Then I started virt-manager, did an "Add Connection" ... entered thefu into the username (not root) and that was it.  It worked.  I didn't have to manually add my userid to any groups at all, but my username is part of the "libvirt" group on the workstation.

So, 22.04 Xubuntu can connect to a KVM host running 18.04.
Both systems were patched this weekend. Nothing special.

---

### Post by Heeter on 2022-07-31
Hey thanks guys, TheCog

I finally got working on my new laptop, cleared the keys in that folder and it works now.

---

