---
title: "TFTP error with PXE"
date: 2015-03-30
forum: Server Platforms
---

### Post by tmontney on 2015-03-30
I followed this tutorial: [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

I believe I followed everything right, but I'm getting "File Not Found" error when PXE booting. It gets the IP configuration, so I know DHCP is working. But it can't seem to find the configuration file. I'm running Ubuntu Server 14.04. Let me know what settings you want me to post, as I'm not too knowledgeable with Ubuntu.

---

### Post by Lars Noodén on 2015-03-30
The configuration file for tftpd-hpa is in /etc/default/tftpd-hpa.  There you can set the TFTP ditrectory to be /tftpboot like in the tutorial or put the PXE file in /var/lib/tftpboot/

---

### Post by tmontney on 2015-03-30
See, I thought I had that right. Here's my file.

# /etc/default/tftpd-hpa

#TFTP_USERNAME="tftp"
#TFTP_DIRECTORY="/var/lib/tftpboot"
#TFTP_ADDRESS="[::]:69"
#TFTP_OPTIONS="--secure"

RUN_DAEMON="yes"
OPTIONS="-l -s /tftpboot"

I was confused which directory it was looking at (the /tftpboot directory or the directory we copied files from /var/lib/tftpboot).

---

### Post by Lars Noodén on 2015-03-30
The line is commented out.  Remove the pound sign at the beginning of the line to enable that setting:

> **tmontney said:**
> TFTP_DIRECTORY="/var/lib/tftpboot"


Then you can choose the directory, save the configuration, and restart tftpd.

Edit: never mind.  The /tftpboot in the options points it to the directory /tftpboot.

---

### Post by tmontney on 2015-03-30
Here's the directory listing of /tftpboot.

---

### Post by Lars Noodén on 2015-03-30
What is in.tftpd looking for?

```

sudo lsof | grep in.tftpd

```

That will say which directory it is using, probably at the top.

---

### Post by tmontney on 2015-03-30
That command didn't do anything.

---

### Post by Lars Noodén on 2015-03-30
Hmm.  Is tftpd running?

```

service tftpd-hpa status

```

---

### Post by tmontney on 2015-03-30
It says start/running. Seems good.

If it helps, there's nothing in [COLOR=#333333][FONT=UbuntuMono]/var/lib/tftpboot.

I was able to copy and paste the fstab configuration, rather than type it out this time. I tried it again, and now I get "TFTP open timeout". Perhaps I'm making progress?[/FONT][/COLOR]

---

### Post by tmontney on 2015-03-30
This is my /etc/exports file.

/nfsroot             192.168.0.*(rw,no_root_squash,async,insecure)

I tried using my Sony and my HP laptop. Neither worked (both used Realtek NICs).

Could my NIC be problematic? I have a BCM57XX, and could not get it working with 14.04. The Realtek I put in worked immediately.

I noticed my syslog was saying "dhcpd can't create new lease file permission denied". I disabled the apparmor profile on it. I'm not getting the error anymore, but it didn't resolve my TFTP timeout error.

---

### Post by Lars Noodén on 2015-03-31
Exports would be for NFS rather than TFTP.

I'm curious that 'lsof' did not show anything.  What do the logs say about TFTP activity?

```

grep tftp /var/log/syslog

```

---

### Post by tmontney on 2015-03-31
I was wondering why I didn't see a reply. I was sure I checked if the thread moved to another page.

Yesterday I did make some "progress".

     ```
 Mar 30 21:02:15 deployment in.tftpd[918]: no user --address: Success
      Mar 30 21:02:15 deployment kernel: [   19.104284] init: tftpd-hpa main process (918) terminated with status 67
      Mar 30 21:02:15 deployment kernel: [   19.104320] init: tftpd-hpa main process ended, respawning
```

This from syslog after I enabled verbose. Then my error message switched to this: PXE-T02: Only absolute filenames allowed, PXE-E3C: TFTP Error - Access Violation. I believe uncommenting out the username, from /etc/default/tftpd-hpa, gave me the PXE-T02 error. My next logs looked like this...

```
Mar 30 20:59:58 deployment kernel: [22412.511831] init: tftpd-hpa main process (2604) terminated with status 67
Mar 30 20:59:58 deployment kernel: [22412.511868] init: tftpd-hpa main process ended, respawning
Mar 30 21:02:15 deployment in.tftpd[918]: no user --address: Success
Mar 30 21:02:15 deployment kernel: [   19.104284] init: tftpd-hpa main process (918) terminated with status 67
Mar 30 21:02:15 deployment kernel: [   19.104320] init: tftpd-hpa main process ended, respawning
Mar 30 21:26:06 deployment in.tftpd[1208]: RRQ from 192.168.0.12 filename pxelinux.0
Mar 30 21:26:33 deployment in.tftpd[1209]: RRQ from 192.168.0.12 filename pxelinux.0
Mar 30 21:26:33 deployment in.tftpd[1210]: RRQ from 192.168.0.12 filename pxelinux.0
Mar 30 21:30:00 deployment in.tftpd[1217]: RRQ from 192.168.0.12 filename pxelinux.0
Mar 30 21:30:00 deployment in.tftpd[1218]: RRQ from 192.168.0.12 filename pxelinux.0
```


This is when I tried it again just now, but with a tcpdump.

```
tmontney@deployment:/tmp$ sudo tcpdump -r tcpdump
reading from file tcpdump, link-type EN10MB (Ethernet)
19:32:16.963597 IP 192.168.0.12.2070 > 192.168.0.2.tftp:  27 RRQ "pxelinux.0" octet tsize 0
19:32:16.965471 IP 192.168.0.12.2071 > 192.168.0.2.tftp:  32 RRQ "pxelinux.0" octet blksize 1456
```

---

### Post by tmontney on 2015-03-31
I just figured out how to multiply verbosity. Here's another log.

```
Mar 31 19:44:21 deployment dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0
Mar 31 19:44:22 deployment dhcpd: DHCPOFFER on 192.168.0.12 to 00:00:00:00:00:00 via eth0
Mar 31 19:44:26 deployment dhcpd: DHCPREQUEST for 192.168.0.12 (192.168.0.2) from 00:00:00:00:00:00 via eth0
Mar 31 19:44:26 deployment dhcpd: DHCPACK on 192.168.0.12 to 00:00:00:00:00:00 via eth0
Mar 31 19:44:26 deployment in.tftpd[1656]: RRQ from 192.168.0.12 filename pxelinux.0
Mar 31 19:44:26 deployment in.tftpd[1656]: sending NAK (2, Only absolute filenames allowed) to 192.168.0.12
Mar 31 19:44:26 deployment in.tftpd[1657]: RRQ from 192.168.0.12 filename pxelinux.0
Mar 31 19:44:26 deployment in.tftpd[1657]: sending NAK (2, Only absolute filenames allowed) to 192.168.0.12
```

After finding this, I discovered I need to add the secure flag. Source: [https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/544377](https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/544377)

Now I'm back to the TFTP open timeout.

Edit: Well, I'll be. I made it past ("PXE entry point found"). I'm not too familiar with the syntax for these configuration files. I figured there was a difference between 'TFTP_OPTIONS' (original) and 'OPTIONS' (from the tutorial). I feel like the TIMEOUT error can be triggered from bad syntax in the config file. Once I commented out OPTIONS, from the tutorial, and set the directory after -s, I moved past my problems.

---

### Post by tmontney on 2015-03-31
It loaded farther but got stuck again: Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)

---

### Post by Lars Noodén on 2015-03-31
> **tmontney said:**
>  Once I commented out OPTIONS, from the tutorial, and set the directory after -s, I moved past my problems.

Ok.  So you are now able to download via TFTP?   In experimenting I found that the tftpd needed to be restarted if I made changes to the permissions of the files in the directory it reads from.  

> **tmontney said:**
> It loaded farther but got stuck again: Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)

Is this on the client or the server?  Are you sure the disk is ok?

---

### Post by tmontney on 2015-04-01
> **Lars Noodén said:**
> Ok.  So you are now able to download via TFTP?   In experimenting I found that the tftpd needed to be restarted if I made changes to the permissions of the files in the directory it reads from.  

Usually when I make changes, I restart related services (just in case).

Is this on the client or the server?  Are you sure the disk is ok?

All the problems so far have been the client. The client booted the the kernel, then had a panic. Complained about not being able to mount root fs. Before this, it wouldn't boot the kernel because it couldn't transfer it (e.g. TFTP timeout).

Edit:

Changed my pxelinux.cfg/default to this...

PROMPT 0
DEFAULT linux root=/dev/nfs nfsroot=192.168.2.10:/nfsroot
APPEND root=/dev/nfs nfsroot=192.168.2.10:/nfsroot
LABEL linux
  KERNEL vmlinuz-2.6.38-8-generic
  APPEND root=/dev/nfs initrd=initrd.img-2.6.38-8-generic nfsroot=192.168.2.10:/nfsroot ip=dhcp rw

Source: [http://ubuntuforums.org/showthread.php?t=1838201](http://ubuntuforums.org/showthread.php?t=1838201)

Thanks to the change, I noticed "initramfs loading..." which wasn't present before. Then I noticed "Alert! [FONT=Ubuntu Mono]/dev/nfs does not exist. Dropping to a shell!". [FONT=arial][SIZE=2]A thread pointed out to add "boot=nfs".[/SIZE][/FONT]

Source: [/FONT][http://askubuntu.com/questions/241998/pxe-boot-broken-after-12-04-upgrade](http://askubuntu.com/questions/241998/pxe-boot-broken-after-12-04-upgrade)

I swear, almost every single thread I've researched so far for each of these problems the person followed the HOWTO. Someone **seriously** needs to either rewrite it, or remove it.

I now saw an issue with my built-in NIC (BCM 57xx). It said my NIC wasn't ready, which is impossible. I assume it relates to the fact I couldn't find working drivers while configuring Ubuntu. My Realtek NIC (PCI) worked out of the box. As soon as I switched my cable, it found a link and an IP immediately. However, it got stuck again.

Begin: Running /scripts/nfs-premount ... done.
random: nonblocking pool is initalized
connect: Connection timed out

Took a considerably long time to tell me this.

NFS over TCP not available from 192.168.0.2.
Begin: Retrying nfs mount ... Begin: Running /scripts/nfs-premount ... done.

At least it's more specific. Will look into it in a little while.

---

### Post by tmontney on 2015-04-01
After disabling the firewall, I got past the error. I'm pretty sure this is what was causing the issue (many say the firewall is disabled by default at install). Obviously I'd rather have a firewall as my server does have an Internet connection; however, I trust all my internal systems (home network). I also enabled logging for NFS, and then noticed a client mismatch (pertaining to the exports file not allowing certain IP addresses). Once I fixed that, I booted without issue. Now my issue is performance. I assume my pentium 4/512 MB server is the issue. I only was building this system to see if I could pull it off. Once I deploy this for my actual purpose, I'll probably give it better hardware.

---

### Post by Lars Noodén on 2015-04-02
> **tmontney said:**
> 
I swear, almost every single thread I've researched so far for each of these problems the person followed the HOWTO. Someone **seriously** needs to either rewrite it, or remove it.


I was thinking the same the other day after reading it but refrained from saying anything.  I can see some changes needed to the DHCP and TFP sections, espcially in light of the fact that Ubuntu now has dnsmasq pre-installed.  However, about NFS, I have not used it for many years and am not up on best practices.  Maybe you could log into the wiki and correct that section or mention the corrections neede to the [documentation mailing list](https://lists.ubuntu.com/mailman/listinfo/ubuntu-doc)?

---

### Post by tmontney on 2015-04-03
I'd be more than happy to do that; however, I'm pretty weak with Linux. I'm more of a Windows guy because of the training I was told to take, when I was younger (MCSA, MCTS, MCP, A+, and so forth). I remember starting a Linux+ course, but dropping it because "it was so much different than Windows". Now I really wish I had taken it. I see how useful it can be to mix Windows and Linux systems together (especially when you have no money and you have server needs).

I'll probably have to redo this whole setup on a more powerful machine, so I can retrace my steps but write everything down. I can promise the exact steps to accomplishing the goal, but not much else (at this point I know more about how to accomplish this task rather than why it works). Someone else will need to fill in the rest.

If anything, I'd rather write an application to automate the process. Problem is, I only know Visual Basic. Perhaps WINE would solve that issue. I'd still be happy to write the manual way to do it, even if I write an application to automate and guide the process.

---

