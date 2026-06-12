---
title: "HOW DO I Unlock an LVM encrupted Ubuntu server 10.04 via SSH"
date: 2011-04-18
forum: Server Platforms
---

### Post by tue.kyndal on 2011-04-18
Hi. (I know I'm not the first with this problem, but it dos not seem to have been solved as of yet)

I have installed the Ubuntu server 10.04 with an LVM LUKS encrypted system.

The idea is that it will serve as a headless sever, that I can reboot and unlock via ssh

Problems:

1:
I can not login via SSH using the rsa_id files I copied to my own ubuntu system, and I can not unlock the encrypted system via ssh.

2.
I can not assign a static IP for the preboot system, to avoid shifting ip's with my dhcp sever. Any edit of any files still gives me a reboot with an dhcp signed IP??????

I have read extensively on the web to find answers, but nothing works.

Its works out of the box on Debian, what is the problem with ubuntu servers?

Please guide me to the correct manual or fix, before I give up on ubuntu and reinstall all my systems with Debian once and for all.


A bit about what I have done so fare:

I have installed busybox and dropbear with
apt-get install dropbear busybox 
 
copyed the keys from the server to my laptop
 
scp /etc/initramfs-tools/root/.ssh/id_rsa [EMAIL="root@192.168.1.2:/root/.ssh"]root@192.168.1.2:/root/.ssh[/EMAIL]/id_rsa 

scp /etc/initramfs-tools/root/.ssh/id_rsa.pub [EMAIL="root@192.168.1.2:/root/.ssh/id_rsa.pub"]root@192.168.1.2:/root/.ssh/id_rsa.pub[/EMAIL] 

scp /etc/initramfs-tools/root/.ssh/authorized_keys [EMAIL="root@192.168.1.2:/root/.ssh"]root@192.168.1.2:/root/.ssh[/EMAIL]/known_hosts 

check the chmod 600 for each file

Fixed the quite splash issue in /etc/default/grub

- GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash” 

+ GRUB_CMDLINE_LINUX_DEFAULT=”"

and updated grub with sudo update-grub

(the server now boots with normal command line promt...but still shifts one line per passfrase digit in the unlock process...I don,t know if this is a problem,. In any case...I still cannot login via SSH, it just asks for a password that i can not provide...I need the key-files to work!)

I have tried to apply this fix..

--- /usr/share/initramfs-tools/scripts/local-top/cryptroot.orig    2010-03-30 00:28:49.000000000 +0300 
+++ /usr/share/initramfs-tools/scripts/local-top/cryptroot    2011-02-20 14:35:29.996636634 +0200 
@@ -288,7 +288,7 @@ 
  
         if [ -z "$cryptkeyscript" ]; then 
             cryptkey="Unlocking the disk $cryptsource ($crypttarget)\nEnter passphrase: " 
-            if [ -x /bin/plymouth ] && plymouth --ping; then 
+            if false; then 
                 cryptkeyscript="plymouth ask-for-password --prompt" 
                 cryptkey=$(echo -e "$cryptkey") 
             else 


But it brinks the system...and I can not unlock it anymore.

I  have tryed everyting descriped on the web for this issued, which appears to be annoying a lot of people. 

PLEASE PROVIDE SOME ANSWERS REGARDING THIS ISSUE!

To build an encrypted server, and access and unlock it with SSH should be easy, not buggy and apparently almost impossible!

I hope someone can help...Thank you in advance.

PS. If some knows, I would also like to know how to unlock an LMV LUKS encrypted RAID at at same time as the system disk is unlocked..but for now..I'm not that fare in the process ;O)

\TK

---

