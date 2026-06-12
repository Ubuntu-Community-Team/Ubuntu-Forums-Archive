---
title: "Did someone log into my PC and edit auth.log entries to cover tracks?"
date: 2021-04-15
forum: Security
---

### Post by hairyjew117 on 2021-04-15
Title says it all. I was looking at my log files and noticed something unsual, a gap between when I last shut down my PC and when I started it, doesn't show session closed or anything for when I shut it off, just stops at this "Failed to activate service 'org.bluez': message and that's it. Is it possible that someone knowing the password to my machine, can log in and change the log file to remove all traces that they got in? Below I have highlighted the 2 entries that caught my eye. Let me know if this looks unusual to you.



```
Apr  8 03:17:28 s-p7-1449 su: (to s) root on none
Apr  8 03:17:28 s-p7-1449 su: pam_unix(su:session): session opened for user s by (uid=0)
Apr  8 03:17:28 s-p7-1449 su: pam_unix(su:session): session closed for user s
Apr  8 03:18:06 s-p7-1449 dbus-daemon[850]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Apr  8 03:29:13 s-p7-1449 gdm-password]: pam_unix(gdm-password:auth): Couldn't open /etc/securetty: No such file or directory
Apr  8 03:29:23 s-p7-1449 gdm-password]: pam_unix(gdm-password:auth): Couldn't open /etc/securetty: No such file or directory
Apr  8 03:29:23 s-p7-1449 gdm-password]: gkr-pam: unlocked login keyring
Apr  8 03:39:18 s-p7-1449 systemd-logind[876]: New seat seat0.
Apr  8 03:39:18 s-p7-1449 systemd-logind[876]: Watching system buttons on /dev/input/event1 (Power Button)
Apr  8 03:39:18 s-p7-1449 systemd-logind[876]: Watching system buttons on /dev/input/event0 (Power Button)
Apr  8 03:39:18 s-p7-1449 systemd-logind[876]: Watching system buttons on /dev/input/event3 (Logitech USB Keyboard)
Apr  8 03:39:18 s-p7-1449 systemd-logind[876]: Watching system buttons on /dev/input/event5 (Logitech USB Keyboard System Control)
Apr  8 03:39:26 s-p7-1449 gdm-launch-environment]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)
Apr  8 03:39:26 s-p7-1449 systemd-logind[876]: New session c1 of user gdm.
Apr  8 03:39:26 s-p7-1449 systemd: pam_unix(systemd-user:session): session opened for user gdm by (uid=0)
Apr  8 03:39:43 s-p7-1449 polkitd(authority=local): Registered Authentication Agent for unix-session:c1 (system bus name :1.41 [/usr/bin/gnome-shell], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8)
**Apr  8 03:39:57 s-p7-1449 dbus-daemon[853]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)**
[B]Apr  8 16:02:36 s-p7-1449 gdm-launch-environment]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)
[/B]Apr  8 16:02:36 s-p7-1449 systemd-logind[864]: New session c1 of user gdm.
Apr  8 16:02:36 s-p7-1449 systemd: pam_unix(systemd-user:session): session opened for user gdm by (uid=0)
Apr  8 16:03:01 s-p7-1449 polkitd(authority=local): Registered Authentication Agent for unix-session:c1 (system bus name :1.42 [/usr/bin/gnome-shell], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8)
Apr  8 16:03:05 s-p7-1449 dbus-daemon[845]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Apr  8 16:17:01 s-p7-1449 CRON[1774]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  8 16:17:01 s-p7-1449 CRON[1774]: pam_unix(cron:session): session closed for user root
Apr  8 16:26:09 s-p7-1449 gdm-password]: pam_unix(gdm-password:auth): Couldn't open /etc/securetty: No such file or directory
Apr  8 16:26:18 s-p7-1449 gdm-password]: pam_unix(gdm-password:auth): Couldn't open /etc/securetty: No such file or directory
Apr  8 16:26:18 s-p7-1449 gdm-password]: gkr-pam: unable to locate daemon control file
Apr  8 16:26:18 s-p7-1449 gdm-password]: gkr-pam: stashed password to try later in open session
Apr  8 16:26:18 s-p7-1449 gdm-password]: pam_unix(gdm-password:session): session opened for user s by (uid=0)
Apr  8 16:26:18 s-p7-1449 systemd-logind[864]: New session 3 of user s.

```

---

### Post by DuckHook on 2021-04-15
Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. It is also unnecessary to post whole screenshots in most cases. Terminal output can be highlighted with the mouse, copied with a right click and pasted into the posting box between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the button in the *Adv Reply* toolbar.

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

---

### Post by hairyjew117 on 2021-04-15
> **DuckHook said:**
> Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. It is also unnecessary to post whole screenshots in most cases. Terminal output can be highlighted with the mouse, copied with a right click and pasted into the posting box between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the button in the *Adv Reply* toolbar.

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

My apologies, converted it to text instead. Would like someone's opinion on this. Is this normal?

---

### Post by CharlesA on 2021-04-15
Do you have VNC or Remote Desktop or SSH enabled?

Is the gap in the logs the only reason you suspect someone tried to access your machine?

---

### Post by hairyjew117 on 2021-04-16
> **CharlesA said:**
> Do you have VNC or Remote Desktop or SSH enabled?

Is the gap in the logs the only reason you suspect someone tried to access your machine?

It's someone I live with that managed to get my password and tries to break into it when I'm not around. I've had my google account compromised too and this isn't the first time. Is it possible as a root user to delete these entries and hide that you deleted them? When i powered the laptop down I powered it down holding the button but it should still log that I powered it down?? I don't see any record of it being powered down between 3am and 4pm

---

### Post by The Cog on 2021-04-16
On my laptop, a brief press on the power button brings up a dialogue asking if I want to power 0ff, suspend or reboot (I'm on Xubuntu, but I guess Ubuntu behaves similarly). A long press (maybe 10 Sec) powers the laptop down without warning the OS, and should only be used when it has crashed and cannot power itself down properly. It can cause disk corruption. So if you used the long-press, there's no surprise that the OS didn't log the loss of power.

But yes, someone as root would be able to edit log files to hide evidence of their activity. In larger setups, computers are often configured to send all their log messages to a separate audit server that has the job of logging all events, and is suitably hardened and backed up. There are even append-only filesystems that do not allow deletion of logs once written.

---

### Post by TheFu on 2021-04-16
If you cannot restrict physical access to the system, then there isn't anything that can be done. With physical access, anything is possible.
There is 1 way to fight that.  **Whole disk encryption using 2FA where you keep the 2FA device with you at all times.**  ALL TIMES.  That includes in the toilet, shower.  Get a Yubikey and setup 2FA to decrypt the LUKS encryption pre-boot using a challenge-response mode.

_**But you still have to completely power down the system whenever you leave the room for this to be effective.**_  When the system is running, the normal password is the only thing preventing local access and with a carefully crafted USB drive, it is possible to force new drivers, which run as root and can do anything, to be loaded when the USB drive is connected.

On an unencrypted system, I could accomplish what you are seeing if I had 5 minutes ... perhaps 2 minutes. Less if I knew more about the system and had a custom built flash drive.

Check **dmesg** to see if the box was rebooted.  Can also use **journalctl** to look across all sorts of logs if your grep-fu is lacking.  Rebooting a system leaves all sorts of traces around the file systems. I doubt someone could clean up all of them. Traces are in /dev, /sys, /var, /proc.

---

### Post by QIII on 2021-04-16
2FA disk encryption as described is pretty much the key.

Physical access is the mother of all security issues.

---

### Post by T6&amp;sfpER35% on 2021-04-16
> [COLOR=#000000]It's someone I live with that managed to get my password and tries to break into it when I'm not around[/COLOR]
you need to check you're living arrangements lol

---

### Post by QIII on 2021-04-16
> **3nd said:**
> you need to check you're living arrangements lol

Dorms, apartment room mates ... sometimes hard to make sure everyone passes a security background check.  :)

---

### Post by T6&amp;sfpER35% on 2021-04-16
> [COLOR=#000000]Dorms, apartment room mates .[/COLOR]
yea ok my bad ,didn't think of that . I'm 50 so those living arrangements left me like 30yrs ago lol.

instead of shutting down all the time when you go have a dump or whatever , maybe look into [this](https://itsfoss.com/how-to-disable-usb-ports-in-ubuntu/) ?

just a thought that occurred to me , if someone cant access a USB port ...well...

---

### Post by TheFu on 2021-04-16
If the attacker isn't just a normal roommate, but some sort of highly motivated "state actor", then any bus connection can be used - PCI, PCIe, firewire, USB, Thunderbolt - any bus can be abused. I'd bet SATA, eSATA, IDE can be used too. There are published attack techniques for USB, firewire, and thunderbolt connections.
And if you use any wireless mouse, keyboard of any sort, game over.  Currently, none of the wireless protocols are known to be secure.  I've been hacked over bluetooth.

For example:
[LIST]
[*] [https://www.bleepingcomputer.com/news/security/linux-has-a-usb-driver-security-problem/](https://www.bleepingcomputer.com/news/security/linux-has-a-usb-driver-security-problem/)
[*] [https://www.kernel.org/doc/html/latest/core-api/debugging-via-ohci1394.html](https://www.kernel.org/doc/html/latest/core-api/debugging-via-ohci1394.html)  Completely access all RAM on a system.
[*] [https://www.schneier.com/blog/archives/2008/03/physically_hack.html](https://www.schneier.com/blog/archives/2008/03/physically_hack.html)
[*] [https://www.slashgear.com/thunderspy-thunderbolt-hack-exposes-your-files-windows-macos-linux-how-to-check-11619992/](https://www.slashgear.com/thunderspy-thunderbolt-hack-exposes-your-files-windows-macos-linux-how-to-check-11619992/)
[*] [https://thunderspy.io/](https://thunderspy.io/)
[/LIST]

I'm not making this stuff up.

---

### Post by T6&amp;sfpER35% on 2021-04-16
or ..
to block:
```
[FONT=monospace]sudo chmod 700 /media[/FONT]
```

[FONT=Verdana]This will allow the root user only to mount the removable disks not the normal users

to unblock:
```
[/FONT][FONT=monospace]sudo chmod 755 /media[/FONT][FONT=Verdana]
```

that's if your your 'attacker" is not a spy of some sorts like **the fu** said [/FONT]

---

### Post by CharlesA on 2021-04-17
> **TheFu said:**
> If you cannot restrict physical access to the system, then there isn't anything that can be done. With physical access, anything is possible.
There is 1 way to fight that.  **Whole disk encryption using 2FA where you keep the 2FA device with you at all times.**  ALL TIMES.  That includes in the toilet, shower.  Get a Yubikey and setup 2FA to decrypt the LUKS encryption pre-boot using a challenge-response mode.

Agreed on the encryption bit. It's a layer of extra security, but it does have it's down sides as well.

If you are in this sort of situation, enabling two-factor authentication can help immensely, but it won't stop everything if someone has physical access to your phone or email.

---

### Post by scorp123 on 2021-04-17
> **hairyjew117 said:**
>  When i powered the laptop down I powered it down holding the button but it should still log that I powered it down??

On the laptops I own (and I own several) pressing + holding the power button is **NOT** a graceful shutdown. It's a forced shutdown, the equivalent of suddenly pulling the power cord on a desktop PC. I would find it quite surprising if your Linux installation managed to log anything at all in that moment since you're basically violently pulling the rug from under its feet.

Please stop doing that. A short press of the power button so the laptop initiates a graceful shutdown by itself (takes about 2 to 10 seconds) is OK, but not pressing + holding.


As for the possibility of someone logging into your system:

Did you check these commands?
```
sudo last
sudo lastb
```

Sometimes people (intruders too) forget that these files exist, e.g. they remove entries from "auth.log" but forget to erase the traces they left in places like **/var/log/wtmp** ....  The other thing is that **/var/log/btmp** and **/var/log/wtmp** are in a binary format and thus harder to manipulate without completely messing them up. Most people trying to cover their tracks will simply resort to erasing those files right away or filling them with binary '0' so those files look empty.

So if you check the outputs of ```
sudo lastb
``` (the "bad" login attempts ... could well be empty if nobody ever tried anything) and ```
sudo last
``` (the successful logins ... NO WAY this could ever be empty!!) is there any oddity there? Or nothing at all? e.g. you only get empty outputs from both commands?

If the system was indeed tampered with then ```
sudo last
``` will produce no output at all (e.g. the log was erased) or there should be strange time gaps, e.g. complete days missing.

On a normal system where no tampering took place a "last" output should look something like this and you should be able to see both local and remote logins over a period of several months:

```

frodo      pts/1        192.168.1.6      Sat Apr 17 12:03   still logged in
frodo      tty7         :0               Sat Apr 17 04:04 - 04:10  (00:05)
frodo      tty7         :0               Sat Apr 17 03:56 - 04:04  (00:07)
frodo      pts/1        192.168.1.6      Fri Apr 16 16:54 - 17:08  (00:14)
frodo      pts/1        192.168.1.6      Fri Apr 16 15:41 - 15:41  (00:00)
frodo      pts/1        192.168.1.6      Fri Apr 16 15:40 - 15:40  (00:00)
frodo      pts/1        192.168.1.6      Fri Apr 16 15:19 - 15:19  (00:00)
gollum     pts/1        10.106.77.10     Fri Apr 16 15:17 - 16:17  (01:00)
frodo      pts/0        192.168.1.6      Fri Apr 16 14:15 - 14:15  (00:00)
frodo      tty7         :0               Fri Apr 16 14:11 - 14:13  (00:01)
frodo      tty7         :0               Fri Apr 16 13:58 - 14:11  (00:13)
frodo      tty7         :0               Fri Apr 16 13:57 - 13:58  (00:01)
frodo      pts/0        192.168.1.6      Fri Apr 16 13:17 - 13:56  (00:38)
frodo      pts/0        192.168.1.6      Fri Apr 16 13:13 - 13:13  (00:00)
frodo      pts/0        192.168.1.6      Fri Apr 16 13:06 - 13:06  (00:00)
frodo      pts/0        192.168.1.108    Fri Apr 16 01:43 - 01:46  (00:03)
reboot   system boot  5.4.0-72-generic   Fri Apr 16 01:09   still running
frodo      pts/0        192.168.1.7      Fri Apr 16 01:07 - 01:08  (00:00)
frodo      pts/0        192.168.1.7      Fri Apr 16 01:06 - 01:06  (00:00)
frodo      pts/0        192.168.1.7      Fri Apr 16 01:06 - 01:06  (00:00)
frodo      pts/0        192.168.1.7      Fri Apr 16 01:06 - 01:06  (00:00)
frodo      pts/0        192.168.1.7      Fri Apr 16 01:02 - 01:06  (00:03)
frodo      pts/0        192.168.1.7      Fri Apr 16 01:02 - 01:02  (00:00)
frodo      pts/1        192.168.1.2      Fri Apr 16 01:01 - 01:03  (00:01)
frodo      pts/0        192.168.1.7      Fri Apr 16 01:01 - 01:02  (00:00)
frodo      pts/0        192.168.1.7      Fri Apr 16 01:01 - 01:01  (00:00)
frodo      pts/0        192.168.1.2      Thu Apr 15 00:21 - 01:59  (01:38)
frodo      pts/0        192.168.1.2      Thu Apr 15 00:04 - 00:08  (00:03)
frodo      tty7         :0               Wed Apr 14 23:06 - 23:10  (00:03)
gollum     pts/0        10.106.77.10     Wed Apr 14 16:50 - 16:56  (00:06)
frodo      pts/0        192.168.1.43     Wed Apr 14 14:07 - 14:07  (00:00)
reboot   system boot  5.4.0-71-generic   Wed Apr 14 14:05 - 01:08 (1+11:02)
frodo      pts/0        192.168.1.6      Wed Apr 14 13:52 - 13:52  (00:00)
frodo      pts/0        10.135.75.30     Wed Apr 14 12:02 - 12:12  (00:09)
frodo      pts/0        10.135.75.30     Wed Apr 14 11:47 - 11:51  (00:04)
frodo      pts/0        10.135.75.30     Wed Apr 14 11:39 - 11:41  (00:01)
frodo      pts/0        10.135.75.30     Tue Apr 13 12:30 - 12:31  (00:00)
frodo      pts/0        10.135.75.30     Tue Apr 13 12:11 - 12:13  (00:02)
frodo      pts/0        10.135.75.30     Tue Apr 13 11:20 - 11:30  (00:09)
frodo      pts/0        10.135.75.30     Tue Apr 13 10:23 - 10:30  (00:06)
reboot   system boot  5.4.0-71-generic   Tue Apr 13 10:23 - 14:04 (1+03:41)
frodo      pts/1        10.135.75.30     Tue Apr 13 10:17 - 10:22  (00:04)
...

```

And here a small example output from "lastb"... in this case an Internet-facing SFTP server where only SSH key authentication is activated. But lots of people try anyway with all kinds of weird usernames (this is a manual selection; I removed all entries with identifiable IP addresses) :

```

randall  ssh:notty    vmi545853.contab Sat Apr 17 11:40 - 11:40  (00:00)
randall  ssh:notty    vmi545853.contab Sat Apr 17 11:40 - 11:40  (00:00)
pi       ssh:notty    mon75-h02-176-14 Sat Apr 17 10:54 - 10:54  (00:00)
pi       ssh:notty    mon75-h02-176-14 Sat Apr 17 10:54 - 10:54  (00:00)
pi       ssh:notty    mon75-h02-176-14 Sat Apr 17 10:54 - 10:54  (00:00)
pi       ssh:notty    mon75-h02-176-14 Sat Apr 17 10:54 - 10:54  (00:00)
admin    ssh:notty    this-is-a-tor-ex Sat Apr 17 07:18 - 07:18  (00:00)
admin    ssh:notty    this-is-a-tor-ex Sat Apr 17 07:18 - 07:18  (00:00)
sorin    ssh:notty    19010730120.ip71 Sat Apr 17 06:04 - 06:04  (00:00)
sorin    ssh:notty    19010730120.ip71 Sat Apr 17 06:04 - 06:04  (00:00)
...

```

Failed local logins would be visible too on this log if there had been any of those.

Can you check what output you get on your laptop?

---

### Post by hairyjew117 on 2021-04-18
> **scorp123 said:**
> 

Failed local logins would be visible too on this log if there had been any of those.

Can you check what output you get on your laptop?


I have checked last and was able to find several logs of logins from many months that looked normal. lastb didn't produce much just 1 entry that it begins on the 14th, I even tested putting the wrong password with sudo and on the lock login screen and didnt find any records anywhere of failed login attempts. Checking faillog only give me a long wall of text with "^@^@^@^@^@^@^@^@^@^@^@".


This is what I got running lastb command 

```
root     pts/0                         Wed Apr 14 18:54 - 18:54  (00:00)

btmp begins Wed Apr 14 18:54:11 2021


```


And this is what I get running faillog -a

```
Login       Failures Maximum Latest                   On

root            0        0   12/31/69 18:00:00 -0600  
daemon          0        0   12/31/69 18:00:00 -0600  
bin             0        0   12/31/69 18:00:00 -0600  
sys             0        0   12/31/69 18:00:00 -0600  
sync            0        0   12/31/69 18:00:00 -0600  
games           0        0   12/31/69 18:00:00 -0600  
man             0        0   12/31/69 18:00:00 -0600  
lp              0        0   12/31/69 18:00:00 -0600  
mail            0        0   12/31/69 18:00:00 -0600  
news            0        0   12/31/69 18:00:00 -0600  
uucp            0        0   12/31/69 18:00:00 -0600  
proxy           0        0   12/31/69 18:00:00 -0600  
www-data        0        0   12/31/69 18:00:00 -0600  
backup          0        0   12/31/69 18:00:00 -0600  
list            0        0   12/31/69 18:00:00 -0600  
irc             0        0   12/31/69 18:00:00 -0600  
gnats           0        0   12/31/69 18:00:00 -0600  
nobody          0        0   12/31/69 18:00:00 -0600  
systemd-network       0        0   12/31/69 18:00:00 -0600  
systemd-resolve       0        0   12/31/69 18:00:00 -0600  
systemd-timesync       0        0   12/31/69 18:00:00 -0600  
messagebus       0        0   12/31/69 18:00:00 -0600  
syslog          0        0   12/31/69 18:00:00 -0600  
_apt            0        0   12/31/69 18:00:00 -0600  
tss             0        0   12/31/69 18:00:00 -0600  
uuidd           0        0   12/31/69 18:00:00 -0600  
tcpdump         0        0   12/31/69 18:00:00 -0600  
avahi-autoipd       0        0   12/31/69 18:00:00 -0600  
usbmux          0        0   12/31/69 18:00:00 -0600  
rtkit           0        0   12/31/69 18:00:00 -0600  
dnsmasq         0        0   12/31/69 18:00:00 -0600  
cups-pk-helper       0        0   12/31/69 18:00:00 -0600  
speech-dispatcher       0        0   12/31/69 18:00:00 -0600  
avahi           0        0   12/31/69 18:00:00 -0600  
kernoops        0        0   12/31/69 18:00:00 -0600  
saned           0        0   12/31/69 18:00:00 -0600  
nm-openvpn       0        0   12/31/69 18:00:00 -0600  
hplip           0        0   12/31/69 18:00:00 -0600  
whoopsie        0        0   12/31/69 18:00:00 -0600  
colord          0        0   12/31/69 18:00:00 -0600  
geoclue         0        0   12/31/69 18:00:00 -0600  
pulse           0        0   12/31/69 18:00:00 -0600  
gnome-initial-setup       0        0   12/31/69 18:00:00 -0600  
gdm             0        0   12/31/69 18:00:00 -0600  
s               0        0   12/31/69 18:00:00 -0600  
systemd-coredump       0        0   12/31/69 18:00:00 -0600  
clamav          0        0   12/31/69 18:00:00 -0600  


```

This is what I get running faillog -u (username)

```
Login       Failures Maximum Latest                   On

Jeff               0        0   12/31/69 18:00:00 -0600  
```

---

### Post by TheFu on 2021-04-18
> **CharlesA said:**
> Agreed on the encryption bit. It's a layer of extra security, but it does have it's down sides as well.

If you are in this sort of situation, enabling two-factor authentication can help immensely, but it won't stop everything if someone has physical access to your phone or email.

Actually, using LUKS with 2FA **does** stop access to the computer data, unless the LUKS encryption is unlocked when the attacker arrives.  Since while disk encryption unlocks before booting/login, the protection is simple to understand.

If the computer is useful, powered on, and you can type anything except a challenge, then it is NOT protected.

But if the computer is either powered off or sitting at the LUKS 2FA challenge prompts, then it is protected and I double **any** nation actor could directly gain access without both beating the person who knows the correct response to the challenge AND has the 2FA device available. Also, I boot from a flash drive that is kept with me when traveling. I don't boot from the on-board storage ... look up "evil maid attack" for more information.

I couldn't break into any of my LUKS encrypted systems without the correct 2FA device, regardless of what I might know.  And someone with the 2FA device probably wouldn't know the correct challenge to enter to unlock the storage.

Basically, whole disk encryption, as performed by Ubuntu, is only good when the computer is powered off. That applies to all encrypted systems that I know.  The storage must be locked to be useful for securing data.

---

### Post by TheFu on 2021-04-18
faillog output above doesn't show any attempts that failed.

---

### Post by hairyjew117 on 2021-04-19
> **TheFu said:**
> faillog output above doesn't show any attempts that failed.

Is it supposed to log them? I have entered my password incorrectly many times and it should show it but it doesn't.

---

### Post by TheFu on 2021-04-19
> **hairyjew117 said:**
> Is it supposed to log them? I have entered my password incorrectly many times and it should show it but it doesn't.

I'd have to read the manpage for that command to know.  
```
NAME
       faillog - display faillog records or set login failure limits

SYNOPSIS
       faillog [options]

DESCRIPTION
       faillog displays the contents of the failure log database (/var/log/faillog). It can also
       set the failure counters and limits. When faillog is run without arguments, it only displays
       the faillog records of the users who had a login failure.
...

```

Looks like it would see only failures related to login on a tty/ptty, not ssh or a screen saver.

---

