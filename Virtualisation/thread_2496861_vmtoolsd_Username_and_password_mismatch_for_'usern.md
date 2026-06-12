---
title: "vmtoolsd: Username and password mismatch for 'username'."
date: 2024-04-15
forum: Virtualisation
---

### Post by sarfarazzombarkar on 2024-04-15
getting below alert on ubuntu servers 

**vmtoolsd: Username and password mismatch for 'username'.**

Why vmtoolsd / open-vm-tools using the user account? how to change this?

How to get rid of this error?

---

### Post by MAFoElffen on 2024-04-15
Can you please post the full error posted within Code tags?

Can you tell us what the Virtual host is running, the remote that you are using and the VM OS?

When I look up this error, to get that error: I see vSphere VM Host, from a Windows remote client, and a problem with a tool from vCenter trying to connect to a vShere VM with the wrong administrative password while it is trying to connect to a VM... That is why I asked the above questions.

---

### Post by sarfarazzombarkar on 2024-04-16
1. Please find the below error.

This is error is showing in **auth.log** as well as when we put **systemctl status open-vm-tools.service** or **systemctl status vmtoolsd.service **commands
VGAuth[1751869]: pam_unix(vmtoolsd:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user='username'
VGAuth[1751869]: vmtoolsd: Username and password mismatch for 'username'.

2. The Vm is running on ESXi host and VM OS is ubuntu 22.04

3. The above error is getting logged whether we are trying to log in to the VM or not

---

### Post by MAFoElffen on 2024-04-16
<<Note to Moderators-- This should probably be moved to the "Virtualization" Section. It has to do with an on & off upstream issue with package 'open-vm-tools', not with Server Edition itself.>>

From inside your Ubuntu VM, do these commands. Please post the output "within CODE Tags". Since you didn't do that in your last post for the error, refer to the "Code Tags" link in my Signature Line if you need help on how to do that...
```

lsb_release -d
uname -r
apt list open-vm-tools --installed
which vmtoolsd
which vmware-rpctool
which vmware-toolbox-cmd
which vmware-vgauth-cmd
ls /usr/bin/vm*
sudo systemctl systemctl status vmtoolsd vgauthd --no-pager
journalctl -u vmtoolsd --no-pager
journalctl -u vgauthd --no-pager
/usr/bin/vmware-rpctool 'info-get guestinfo.metadata'
/usr/bin/vmware-rpctool 'info-get guestinfo.userdata'
/usr/bin/vmware-rpctool 'info-get guestinfo.vendordata'
grep . /etc/pam.d/vmtoolsd

```
If any of those return NULL, please note that... Especially on the rpctool info-get commands.

The contents of /etc/pam.d/vmtoolsd (the last command) on Debian and rhel should be similar to this:
```

#%PAM-1.0#%PAM-1.0
auth       sufficient       pam_unix2.so nullok
auth       sufficient       pam_unix.so shadow nullok
auth       required         pam_unix_auth.so shadow nullok
account    sufficient       pam_unix2.so
account    sufficient       pam_unix.so
account    required         pam_unix_acct.so
auth sufficient pam_unix2.so nullok
auth sufficient pam_unix.so shadow nullok
auth required pam_unix_auth.so shadow nullok
account sufficient pam_unix2.so
account sufficient pam_unix.so
account required pam_unix_acct.so

```
But that is just an example with "them"... Current Ubuntu is a little different, where it has /usr/lib/x86_64-linux-gnu/security/pam_unix.so, but unix2.so is not there, so is all on pam_unix.so, like below...

The bare minimum, like one of my servers, is this
```

#PAM configuration for vmtoolsd

@include common-auth

account    required    pamshells.so
@include common-account

## with common-auth included, that adds
auth    [success=1 default=ignore] pam_unix.so nullok
auth    requisite                  pam_deny.so
auth    required                   pam_permit.so
auth optional                      pam_cap.so

##With common-account included, that adds
account [success=1 new_authtok_reqd=done default=ignore]    pam_unix.so
account requisite                       pam_deny.so
account requires                        pam_permit.so

```
And tell us the release/version of the ESXi Virtualization Host. Also note the OS, version, and method of "VM connection" of the remote machine you are connecting to the VM.

Make a folder and keep all that output in a log file. Include the link to this thread. It will most likely need to be reported to LaunchPad in a Bug Report so they can report the problem to the upstream maintainer ([https://github.com/vmware/open-vm-tools](https://github.com/vmware/open-vm-tools))

---

### Post by QIII on 2024-04-16
Moved to Virtualisation

---

