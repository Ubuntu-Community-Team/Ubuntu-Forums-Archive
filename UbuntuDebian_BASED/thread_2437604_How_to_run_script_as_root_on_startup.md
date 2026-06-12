---
title: "How to run script as root on startup"
date: 2020-02-26
forum: Ubuntu/Debian BASED
---

### Post by roland-wh on 2020-02-26
Hi, I have a secondary drive in my PC. It's an LDM drive and Linux will not mount it until I run
```
sudo ldmtool create all
``` Once I run this command it works fine, the problem is when I reboot my computer I have to run the command again which gets very annoying especially as root is required for the command to work properly. I have already tried using systemd and systemctl to run the script on startup but this did not work. I also tried creating a symbolic link in /etc/rc5.d using ```
ln -s /etc/init.d/finddata.sh /etc/rc5.d/S99finddata.sh
``` but neither worked. Any suggestions would be very appreciated, thanks in advance :)

P.S I am running Feren OS KDE but it does not have it's own forum and I would assume that what I am looking to do would be the same across all Debian based distros.

Edit: I now realize that all scripts running at startup are root so I removed the sudo from the beginning of my script but it still doesn't work :(

---

### Post by wildmanne39 on 2020-02-26
*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

---

### Post by DuckHook on 2020-02-26
Welcome to the forums, roland-wh.

LDM is not native to Linux, so that's part of the problem. I don't know if ldmtool is FUSE, but it doesn't appear to be (which helps).

I'm surprised that you couldn't create a systemd mount script for it. Please post your script. It should still be the best way to get this running. A wild guess on my part, but I suspect that the script failed because it didn't wait for a dependent service to be loaded before executing.

I haven't used Windows for years and have no familiarity with LDM at all, so my knowledge is almost nonexistent, but post your systemd script and others may be able to help.

---

### Post by TheFu on 2020-02-26
Probably not what you want to read, but have you considered reformatting from LDM to something more standard?  About once a year, we see someone with LDM here, so it doesn't seem popular.  If this disk is for Linux only use, ext4 is probably the best choice for performance and data safety.

---

### Post by roland-wh on 2020-02-27
Thanks for the quick responses :) 
> **DuckHook said:**
> Please post your script.
 Here you go:
```
[Unit]
Description=Mount my external data drive

[Service]
ExecStart=/usr/local/sbin/find-data.sh

[Install]
WantedBy=multi-user.target
```
 
> **DuckHook said:**
> A wild guess on my part, but I suspect that the  script failed because it didn't wait for a dependent service to be  loaded before executing.
Yeah that was my guess too that's why I tried the second method of  creating a symbolic link in /etc/rc5.d seeing as that's the last  runlevel I assumed all the services would be loaded by then.
[QUOTE=TheFu]have you considered reformatting from LDM to something more standard?[/QUOTE]
I'm afraid that's not an option for me as I need that data and I don't  have another drive big enough to back it up onto. If worst comes to  worst I could just manually run the command every time the computer  starts up but I'm hoping I can find a way to automate it as that would  be a pain. Sorry if I'm missing something obvious here, I'm quite good with  computers but I've only recently switched to Linux.

Edit: I should clarify the code I posted was the find-data.service file I placed in /etc/systemd/system/  the find-data.sh file in  /usr/local/sbin   just said: ldmtool create all

---

### Post by roland-wh on 2020-02-27
Update: I just run systemctl status find-data.service and this was the result
```
&#9679; find-data.service - Mount my external data drive
   Loaded: loaded (/etc/systemd/system/find-data.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2020-02-27 09:37:41 GMT; 1min 13s ago
  Process: 894 ExecStart=/usr/local/sbin/find-data.sh (code=exited, status=203/EXEC)
 Main PID: 894 (code=exited, status=203/EXEC)

Feb 27 09:37:41 Red-Phoenix systemd[1]: Started Mount my external data drive.
Feb 27 09:37:41 Red-Phoenix systemd[894]: find-data.service: Failed to execute command: Exec format error
Feb 27 09:37:41 Red-Phoenix systemd[894]: find-data.service: Failed at step EXEC spawning /usr/local/sbin/find-data.sh: Exec format error
Feb 27 09:37:41 Red-Phoenix systemd[1]: find-data.service: Main process exited, code=exited, status=203/EXEC
Feb 27 09:37:41 Red-Phoenix systemd[1]: find-data.service: Failed with result 'exit-code'.
```

---

### Post by TheFu on 2020-02-27
What are the permissions for the script? it must have execute permissions.

Insde the script, the ldmtool needs to have the full path.  I doubt there is a PATH set early in boot.  When scripting, always use full paths to all programs, every time.

Probably needs a 
```
#!/bin/bash 
```
as the first line to tell it which interpreter to use.

BTW, there are no runlevels anymore. Just targets.

---

### Post by roland-wh on 2020-02-27
Thank you so much, I had already set execute permissions but I forgot that everything in Linux is a file of some kind, I was still thinking in the Windows peasant mindset :D
I didn't know about the #!/bin/bash thing though 

Thanks a lot for the help :)

---

