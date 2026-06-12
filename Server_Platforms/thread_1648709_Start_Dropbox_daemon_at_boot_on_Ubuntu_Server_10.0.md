---
title: "Start Dropbox daemon at boot on Ubuntu Server 10.04"
date: 2010-12-19
forum: Server Platforms
---

### Post by Blackrider69 on 2010-12-19
Hello!

I am having some trouble making the dropbox daemon start at boot. I followed these instructions -> [http://1000umbrellas.com/2010/04/30/how-to-install-dropbox-on-a-headless-ubuntu-10-04-server](http://1000umbrellas.com/2010/04/30/how-to-install-dropbox-on-a-headless-ubuntu-10-04-server), which are basically a replica of the original instructions from the Dropbox Wiki ([http://wiki.dropbox.com/TipsAndTricks/TextBasedLinuxInstall](http://wiki.dropbox.com/TipsAndTricks/TextBasedLinuxInstall)).

The installation went fine, except that the machine still cannot start the daemon at boot. I tried to modify the init.d script a bit (see the attachment), but it still wont work (I am not sure if my changes made any significant difference, though). The daemon will only start if I invoke it manually after login with the command:

```
[user@machine:~]$ service dropbox start
```Which executes the daemon just fine. 

I also tried adding this line of code to crontab:

```
@reboot /etc/init.d/dropbox start
```This command starts the daemon if I check with the command "service dropbox status", but if I execute the official dropbox CLI command:

```
~/bin/dropbox.py status
```it says that Dropbox isn't running and I still have to execute it manually.

Any help is greatly appreciated. :)

BR, Jan

P.s.: The machine runs Ubuntu Server 10.04, with all the latest system patches and updates.

---

### Post by Calimo on 2010-12-19
In the 1000umbrellas.com post, the following line may be the source of your problem:
```
sudo update-rc.d dropbox defaults
```It will setup dropbox to start early in the boot process. Maybe it requires some other daemon that is not started at that time?
Have a look in the syslog or in dmesg to see what's wrong.

```
sudo update-rc.d -f dropbox remove
sudo update-rc.d dropbox defaults 98 02
```should give it a much lower priority, that is it will start later in the boot process: that may be enough to solve the issue.

---

### Post by Blackrider69 on 2010-12-22
Hi Calimo!

First of all, thank you for your hint. I tried it, but Dropbox still won't launch at boot. :confused:

Do you (or anybody else, for the matter) have any other idea? Could it perhaps be a permission issue?

Any other hints are welcome!

---

### Post by Blackrider69 on 2010-12-29
Hi!

Just wanted to say that I solved my problem. I created a new user  "dropbox" and installed the daemon there. It worked just fine! The  daemon starts at boot and syncs just well! Maybe the daemon isn't meant  to be run under an administrative account. Anyway, it works fine. I  added some symlinks, and now I have the same functionality as I would have if I installed Dropbox under my main account.

Thanks anyway Calimo for your help!

BR, Jan

---

