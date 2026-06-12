---
title: "strange issues when entering psw for sudo"
date: 2024-08-22
forum: Ubuntu/Debian BASED
---

### Post by bayou-critter on 2024-08-22
im running a dual booted pop os 22.04, which, as i understand, is  essentially ubuntu. kernel is 6.9. For a period of time after booting, the kernel acts strange when using sudo. it does two things that are odd, so i will list and describe seperatelyl:
1) theres a long delay after (edit: BEFORE, NOT AFTER) entering psw. usually something like 15 seconds, where it just sits there. this is independent of whether or not the psw is corrent. generally, this only occurs for tthe first several minutes or so usually. after 5 to 10 minutes of being booted, the problem seems to go away, and it acts normally. 
2) i get the following error message, again, when using sudo. as above, it only occurs if triggered in the first few minutes after booting, although this period of time seems to be shorter; perhaps only occuring in the first 2 to 3 minutes after booting.
 The error message after running sudo apt update reads:
E: Could not get lock /var/lib/apt/lists/lock, It is held by process 1208 (packegekitd)
N: Be aware that removing the lock file is not a solution and my break your system.
E: Unable to lock directory /var/lib/apt/lists

This problem will occur repeatedly, but if i try a few minutes later, it works fine. Any thoughts on the source of these issues?
Sincerest thanks for your time

---

### Post by deadflowr on 2024-08-22
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by ajgreeny on 2024-08-23
I suspect this is because if you run Ubuntu as default (no idea about PopOS), after booting the system runs apt update to check for any updates available.
Turning off unattended updates, if you allow them, does not stop this as update-notifier will also check for updates.

All completely normal so just wait a minute or two and try again as you do at the moment.

---

### Post by &amp;KyT$0P# on 2024-08-23
Wait, are these issues occurring **no matter what command you run using [FONT=monospace]sudo[/FONT]**? :shock: Or is some important information missing here?

Please post all full [FONT=monospace]sudo[/FONT] commands you've tried and had this issue.

Does it occur even with
```
sudo echo test
```

> **ajgreeny said:**
> I suspect this is because if you run Ubuntu as default (no idea about PopOS), after booting the system runs apt update to check for any updates available.
Turning off unattended updates, if you allow them, does not stop this as update-notifier will also check for updates.

Pop!_OS has a Pop!_OS-specific update daemon which can be controlled in a screen in GNOME settings.  If I recall correctly, Pop!_OS doesn't use unattended-upgrades by default and doesn't have update-notifier at all.

---

### Post by bayou-critter on 2024-08-23
First, i misstated on the original post, the delay after running a command using sudo comes BEFORE entering the password, not after. I edited the original post. The sequence of events is 1. i enter the command 2. the cursor visably moves to the next line, but no text appears 3. 10 to 15 seconds pass 4. the text "[sudo] password for username" is shown

I just tried the command you suggested, sudo echo test, and it did the same thing, a delay of about 12 to 15 seconds. the only other command ive used and noticed the issue is, i think, sudo cat <some-file> to try and see if it happens elsewhere as well. Ive only recently added linux to this laptop, and its not my everyday machine, so i havent done much else with it.

---

### Post by bayou-critter on 2024-08-23
ok, so now im noticing that the delay continues every time i open a new terminal, regardless of how long ive been booted up. I dont think this has always been the case though. I feel like i remember trying this before and it eventually stops happening, even in a new terminal.

---

### Post by &amp;KyT$0P# on 2024-08-23
Is sudo aliased in your [FONT=monospace]~/.bashrc[/FONT] or similar?

Could you please post the contents of the [FONT=monospace]/etc/hosts[/FONT] file from this system?

---

### Post by bayou-critter on 2024-08-23
the word "sudo" never appears in ~/.bashrc. the contents of /etc/hosts is as follows:
# See `man hosts` for details.
#
# By default, systemd-resolved or libnss-myhostname will resolve
# localhost and the system hostname if they're not specified here.
127.0.0.1	localhost
::1		localhost


but i found something more concerning. when i turn off my wifi, the problem goes away. running "sudo echo test" in the terminal causes no delay. when i turn wifi back on, the delay returns. 
so i tried to see if a signal was being sent by running wireshark and then trying sudo echo test with internet on. I'm not experienced with wireshark, and it returned like a thousand packets in a few seconds, and i dont really know how to sift through them. so i disconnected form the wifi and tried again, and running sudo echo test does cause a signal to be sent, but its to a local port at 127.0.0.53. also, it mentions expressvpn, even though i didnt have the vpn activated. i dont know if any of that is relavent, but the fact that using sudo causes a delay only if im connected to the internet is kinda suspicious, right?

---

### Post by &amp;KyT$0P# on 2024-08-23
Your /etc/hosts is missing a line like this -
```
127.0.1.1	[COLOR="#FF0000"]your-computers-hostname[/COLOR]
```
replace [COLOR="#FF0000"]your-computers-hostname[/COLOR] with the output from running this command in Terminal -
```
hostname
```

Does adding this help?

---

### Post by bayou-critter on 2024-08-23
wow, that actually seems to have fixed the problem!! Thanks so much, helpful stranger! 
can you give me the 30 second explanation of what was happening here? also, do you have any thoughts on why that line wouldnt be there? i looked on my eeryday machine, which also uses pop-os, and that line is present in that file.
Again, sincerest thanks for your time.

---

### Post by &amp;KyT$0P# on 2024-08-23
> **bayou-critter said:**
> wow, that actually seems to have fixed the problem!! Thanks so much, helpful stranger! 

You're welcome! :KS

> can you give me the 30 second explanation of what was happening here?

Sorry, I don't understand it myself.  I just know weird issues with sudo can happen when the computer's hostname is not in /etc/hosts (from experience with using chroot as part of customizing old Xubuntu live CDs), and that Pop!_OS doesn't update the /etc/hosts entry for the system hostname (the Pop!_OS versions I have experience with did have such entry, but it was hard-coded to "pop-os" and I had to fix it manually).

---

