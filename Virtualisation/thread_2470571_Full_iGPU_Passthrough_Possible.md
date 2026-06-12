---
title: "Full iGPU Passthrough Possible?"
date: 2022-01-04
forum: Virtualisation
---

### Post by jvuabamlre on 2022-01-04
I have this NUC and want to do full igpu passthrough (intel 620) to windows guest.

Guides I looked at suggests I need to lose monitor output and use ssh to then configure the VM. I can't use SSH though.

How can I do this passthrough?

---

### Post by TheFu on 2022-01-04
99% of the time, full GPU passthru required 2 GPUs to work.  One is assigned to the hostOS and the other is assigned using vt-d and IOMMU to the specific VM guest for exclusive use.  On a system with just 1 GPU, I don't see how that is possible.

Why can't you use ssh?  ssh is completely separate from any GPU or GUI issue.  Even after a GPU driver is crashed, ssh into the system should still be possible.  I've done it more than a few times over the decades.  Of course, ssh has to be setup BEFORE it can be used.

---

### Post by MAFoElffen on 2022-01-06
To a Windows Guest of which Virtual Host system? And which version/build of Windows in your Windows Guest?

Builds of Windows 10 (after build 1809) and Windows 11 include a built-in SSH server and client that are based on OpenSSH. You just go to the Settings > Apps > Apps and features > Optional features (or run the command ms-settings:appsfeatures); then add OpenSSH Server. Or you can add it via powershell...

---

### Post by TheFu on 2022-01-06
> **MAFoElffen said:**
> To a Windows Guest of which Virtual Host system? And which version/build of Windows in your Windows Guest?

Builds of Windows 10 (after build 1809) and Windows 11 include a built-in SSH server and client that are based on OpenSSH. You just go to the Settings > Apps > Apps and features > Optional features (or run the command ms-settings:appsfeatures); then add OpenSSH Server. Or you can add it via powershell...

If you have any pull with MSFT, please get them to add ssh-copy-id to their ssh tools.  Just trying to talk someone through copying their keys to a remote system has proven to be beyond me and them to understand.  But with ssh-copy-id, it becomes a trivial command.

Just 2 commands needed on Unix systems to create, then push the public key.  It has been this way for 15-20 yrs:
```
Step 1:  Run on the client as the normal user:
   $ ssh-keygen -t ed25519

Step 2:  Run from the client to the server:
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
 The "username" is optional and not needed if the same between the client machine and remote server.
```
Easy Peasy and secure.  Next just disable password-based logins for any non-LAN location in the sshd_config.

---

