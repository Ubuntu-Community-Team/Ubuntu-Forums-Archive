---
title: "sudo command lag after renaming an ubuntu VM (hostnamectl)"
date: 2021-11-22
forum: Virtualisation
---

### Post by bluefrog on 2021-11-22
UPDATE: this thread should be moved to the server section as I think it has nothing to do with virtualization in the end

Hi,

I have a strange thing happening with ubuntu and vmware fusion pro 12

I suspect it to be an ubuntu "bug" but I am not sure.

After renaming the server (hostnamectl), sudo takes up to 1 minute to ask for a password (or give the prompt) instead of a split second.

Steps to reproduce:
*** Create an ubuntu server 20.04 VM
ubuntu server hostname : whatever_name

log into the server
sudo -k
<Enter>
the prompt takes a split second to appear

*** Full clone / linked clone / or even copy/paste the VM.vmwarevm file
Run the "new" VM
sudo -k
the prompt takes a split second to appear

change the server hostname
hostnamectl set-hostname new_name

sudo -k
the prompt now takes up to 1 minute to reappear

UPDATE:
Reverting to the old name makes the problem disappear

SOLVED:
need to update the new name by hand in /etc/hosts

---

### Post by TheFu on 2021-11-22
The sudoers file needs to validate the hostname, since a single sudoers can be shared across thousands of hosts inside an enterprise, but only provide specific commands to specific users on specific hosts.

---

