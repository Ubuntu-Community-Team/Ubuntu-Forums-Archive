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
I can not login via SSH using the rsa_id files I copied to my own ubuntu  system, and I can not unlock the encrypted system via ssh.

2.
I can not assign a static IP for the preboot system, to avoid shifting  ip's with my dhcp sever. Any edit of any files still gives me a reboot  with an dhcp signed IP??????

I have read extensively on the web to find answers, but nothing works.

Its works out of the box on Debian, what is the problem with ubuntu servers?

Please guide me to the correct manual or fix, before I give up on ubuntu  and reinstall all my systems with Debian once and for all.


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

(the server now boots with normal command line promt...but still shifts  one line per passfrase digit in the unlock process...I don,t know if  this is a problem,. In any case...I still cannot login via SSH, it just  asks for a password that i can not provide...I need the key-files to  work!)

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

PS. If some knows, I would also like to know how to unlock an LMV LUKS  encrypted RAID at at same time as the system disk is unlocked..but for  now..I'm not that fare in the process ;O)

\TK

---

### Post by tue.kyndal on 2011-04-28
Can it really be correct that nobody knows how to unlock an encrypted ubuntu server via ssh????

---

### Post by tue.kyndal on 2011-04-29
I have followed all the guides from this post on a new Virtual Box ubuntu server 10.04.

I don't get a static ip--still stuck with DHCP, and I don't get ssh login, and no decryption over ssh what so ever!

[http://ubuntuforums.org/showthread.php?t=1648319&highlight=dropbear+ssh&page=2](http://ubuntuforums.org/showthread.php?t=1648319&highlight=dropbear+ssh&page=2) 

Where someone recently has ported some scripts for debian to ubuntu.

It appears that everything now works natively in Debian, but not in Ubuntu.

HOW CAN THIS BE?

There must be a guide that shows how this is done precisely!

And whats up with this forum anyway...not a single answer for a week?

Am I the only one in the world who would like an encrypted server?

---

### Post by hastala on 2011-08-29
i had been struggling with this entire setup as well, having upgraded from an 8.04 that worked like a charm with dropbear, to 10.4.03 LTS...

here's how i got it to work eventually (in a very short form, ask questions if you have any) with:
a) the plymouth boot loader to accept ssh as well as keyboard based unlocking
b) root user enabled, for password authentication
c) dedicated IP support for my stupid Atheros NIC that does not get DHCP address because it has it's MAC in a wrong flash (diffent story, very frustrating though)


1) install all packages you need

```
sudo apt-get install dropbear busybox-initramfs

```

2) create the unlock script (see bottom of the post) and make it executable
```
sudo vi /usr/share/initramfs-tools/hooks/unlock_ssh
```
```
sudo chmod 755 /usr/share/initramfs-tools/hooks/unlock_ssh
```

3) ensure your root user will be able to log in (only do this if you do need root user (or any other user, for that matter) password authentication, instead of public / private key authentication as provided by dropbear out of the box)

```
sudo vi /etc/initramfs-tools/initramfs.conf 
add SSHUSERPASS=root
```
sudo vi /usr/share/initramfs-tools/hooks/plymouth
```
replace "bash" by "sh" --> echo 'root:x:0:0:root:/root:/bin/sh' >${DESTDIR}/etc/passwd
```

4) enable dedicated IP address
```
sudo vi /etc/default/grub
add GRUB_CMDLINE_LINUX="ip=192.168.0.100::192.168.0.1:255.255.255.0:decrypt:eth0:off"
```

5) but get rid of it immediately after boot to get your DHCP setup properly
```
sudo vi /etc/rc.local
add the following before "exit  0":
ifconfig eth0 down
sleep 3
/etc/init.d/networking restart
```


6) get your initramfs

```
sudo update-grub2
sudo update-initramfs -u
```

check /boot/grub/grub.cfg and make sure the just compiled initramfs is the first one in the list

7) voila ;-)


unlock_ssh script:

```
#!/bin/sh

PREREQ="dropbear"

prereqs() {
	echo "$PREREQ"
}

case "$1" in
	prereqs)
		prereqs
		exit 0
	;;
esac

. "${CONFDIR}/initramfs.conf"
. /usr/share/initramfs-tools/hook-functions

if [ "${DROPBEAR}" != "n" ] && [ -r "/etc/crypttab" ] ; then
	cat > "${DESTDIR}/bin/unlock" <<-EOF
		#!/bin/sh
		if PATH=/lib/unlock:/bin:/sbin /scripts/local-top/cryptroot
		then
			/sbin/pkill cryptroot
			/sbin/pkill -f "plymouth ask-for-pass"
			/sbin/pkill cryptsetup
			exit 0
		fi
		exit 1
	EOF
	chmod 755 "${DESTDIR}/bin/unlock"

	mkdir -p "${DESTDIR}/lib/unlock"
	cat > "${DESTDIR}/lib/unlock/plymouth" <<-EOF
		#!/bin/sh
		[ "\$1" == "--ping" ] && exit 1
		/bin/plymouth "\$@"
	EOF
	chmod 755 "${DESTDIR}/lib/unlock/plymouth"

	# Enable password login
	if [ -n "$SSHUSERPASS" ]
	then
		sed -n "s/^${SSHUSERPASS}:/root:/p" /etc/shadow > "${DESTDIR}/etc/shadow"
		chmod 640 "${DESTDIR}/etc/shadow"
	fi

fi
```

---

