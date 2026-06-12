---
title: "VMWare Fusion Folder Sharing"
date: 2013-04-27
forum: Virtualisation
---

### Post by Macdude-StL on 2013-04-27
Host: MacOSX 10.8.3
Guest: Ubuntu 12.10 Quantal 64 bit
VM Engine: VMWare Fusion Pro 5.0.3


I've been struggling with getting folder sharing to work in VMWare 5 - thought I had already installed VMWare Tools, but nothing would show in /mnt/hgfs. I finally tried re-installing. When I got to the section of the install where kernel headers are to be rebuilt, the prompt indicated a valid kernel header path was not present. I tried installing the 3.5.0-25 kernel headers (in Ubuntu Software Center), and got the same error again. Then I realized that there is a selection to install 3.5.0-25 generic kernel headers. After selecting that, the installer indicated a valid file path. After completing the installation, I found the shares present in /mnt/hgfs! I restarted the VM anyway, since some things occasionally don't get refreshed without a hard restart, and things still looked right after the restart.

I believe this situation may have returned after a system update, since 3.5.0-17 header source seems to have been present, but the system is now at 3.5.0-25.

When doing this in VirtualBox, I had found that the shares do not show up until after the machine is restarted, which had led to much frustration.

Before:
> Searching for a valid kernel header path...
The path "" is not a valid path to the 3.5.0-25-generic kernel headers.
Would you like to change it? [yes] ^C
Execution aborted.

After:
> Searching for a valid kernel header path...
Detected the kernel headers at "/lib/modules/3.5.0-25-generic/build/include".
The path "/lib/modules/3.5.0-25-generic/build/include" appears to be a valid 
path to the 3.5.0-25-generic kernel headers.
Would you like to change it? [no] 

Similar issues were described in earlier posts:

[Two newbie issues in need of help]("http://ubuntuforums.org/showthread.php?t=958956")

[VMWare tools]("http://ubuntuforums.org/showthread.php?t=1493498")

---

