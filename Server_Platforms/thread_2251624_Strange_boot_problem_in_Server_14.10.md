---
title: "Strange boot problem in Server 14.10"
date: 2014-11-05
forum: Server Platforms
---

### Post by Vaindil on 2014-11-05
*This was originally posted [here]("http://askubuntu.com/questions/545774/strange-boot-problem-in-server-14-10"), but I'm posting here for additional help. Thank you!*

This is on Ubuntu Server 14.10. I am setting up a user that is chrooted to its own home directory through SFTP, but I need the user to be able to access/edit a subdomain of my website at /var/www/subdomain. I had this previously set up perfectly, but I had to reimage my VPS. I have the user set up and working properly, so everything is good there. Now, however, when the OS is rebooting (the OS, not the VPS), I get a message stating "Waiting for network configuration..." for about 30 seconds, then "Waiting up to 60 more seconds for network configuration...". I didn't change anything with my network config, and it's really annoying to wait 90 seconds each time I need to reboot the system.

Additionally, I need this user to be able to edit a subdomain of my website that's located at /var/www/subdomain. To get around the chroot in the past, I added the following line to /etc/fstab:

```
/var/www/subdomain    /home/username/index    none    none    0 0
```

When that is in place now, however, the OS sits at a blank screen and waits for me to press "s" (discovered via trial-and-error). Once that's pressed, the screen displays "keys:", then waits about 20 seconds, then the above network problem occurs.

I have no idea what the heck is going on here. Any thoughts would be greatly appreciated.

---

### Post by howefield on 2014-11-05
Thread moved to the "*Server Platforms*" forum.

---

### Post by lukeiamyourfather on 2014-11-05
Check /etc/network/interfaces file because there's probably an adapter set for DHCP that isn't actually plugged into anything.

[https://help.ubuntu.com/14.04/serverguide/network-configuration.html](https://help.ubuntu.com/14.04/serverguide/network-configuration.html)

---

### Post by Vaindil on 2014-11-06
This is a VPS, I'm sorry, I should have clarified that. /etc/network/interfaces is below. Everything looks correct to me (the hostnames and IP address are correct, just removed for security).

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address <address>
gateway <gateway>
netmask 255.255.255.0
sysctl kernel.hostname=<hostname>
hostname <hostname>
dns-nameservers 8.8.8.8
```

---

### Post by Vaindil on 2014-11-10
I don't know if bumping is allowed, so I apologize if it's not, but I'm bumping this in case anyone else has an idea.

---

### Post by sudodus on 2014-11-10
Bumping once a day (each 24 hours approx) is allowed and recommended. You may vary the bump time to alert people in different time zones around the earth.

-o-

I cannot help you with the problem, but I can wish you good luck :-)

---

### Post by Jonathan L on 2014-11-13
Hi Vaindil

Just some guesses, but if you're stumped other people's guesses can be helpful!

The pressing 's' sounds like you're getting one of the messages from mountall, which is the program responsible for mounting during boot.
```
An error occurred while mounting /dev/thing
Press S to skip mounting or M for manual recovery
```

With some luck there will be additional things in the logs.

I'd check the order of the entries in fstab, and note that perhaps you need one of the magic fstab flags (hard to tell without seeing the rest of fstab).

fstab(5) says:```

       The  mountall(8) program that mounts filesystem during boot also recog&#8208;
       nises additional options that the  ordinary  mount(8)  tool  does  not.
       These  are:  ``bootwait''  which  can  be applied to remote filesystems
       mounted outside of /usr or /var, without which  mountall(8)  would  not
       hold up the boot for these; ``nobootwait'' which can be applied to non-
       remote filesystems to explicitly instruct mountall(8) not  to  hold  up
       the boot for them; ``optional'' which causes the entry to be ignored if
       the filesystem type is not known  at  boot  time;  and  ``showthrough''
       which  permits  a mountpoint to be mounted before its parent mountpoint
       (this latter should be used carefully, as it can cause boot hangs).
```

A trawl (frankly nothing more sophisticated!) through the source of mountall suggests there are a number of cases which can trigger this message.  One is a timeout, two are fsck failures (not common in virtual servers), lastly some generic mount error.

```
case ERROR_BORED: 
The disk drive for %s is not ready yet or not present.
Continue to wait, or Press S to skip mounting or M for manual recovery

case ERROR_FSCK_FAILED:
Errors were found while checking the disk drive for %s.
Press F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery"

case ERROR_FSCK_FAILED_HARD:
Serious errors were found while checking the disk drive for %s.
Press I to ignore, S to skip mounting, or M for manual recovery

case ERROR_MOUNT_FAILED:
An error occurred while mounting %s.
Press S to skip mounting or M for manual recovery
```


Let us know if that helps at all.

Kind regards,
Jonathan.

PS.  I won't claim anything more sophisticated than find/grep for "keys:", then online to find source, which is at [https://launchpad.net/ubuntu/+source/mountall/2.53](https://launchpad.net/ubuntu/+source/mountall/2.53)

---

