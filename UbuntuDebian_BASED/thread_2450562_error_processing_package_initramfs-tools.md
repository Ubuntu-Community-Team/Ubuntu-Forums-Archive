---
title: "error processing package initramfs-tools"
date: 2020-09-16
forum: Ubuntu/Debian BASED
---

### Post by phoenixintraining on 2020-09-16
Hey Guys
Hope that I can efficiently relay and provide an accurate description of the problem that I am having because I have been beating my head against the wall for a little time now before posting this. Please keep in mind I have not posted inside of community support forums in a while so I do apologize if I have entered this in the wrong location. 
@Admins(Please feel free to move if I have)    
  
I am currently experiencing an error that I cant seem to be able to resolve and it is preventing me from effectively maintaining and updating my Current OS which as we all know is a huge problem cant even install OpenVPN at this time:(.  

OS build was created by following 
[https://mutschler.eu/linux/install-guides/pop-os-btrfs/](https://mutschler.eu/linux/install-guides/pop-os-btrfs/)

[COLOR=#0000ff]**OS Information**[/COLOR]- 
```
duplicity@annalee-call:~$ cat /etc/os-release
NAME="Pop!_OS"
VERSION="20.04 LTS"
ID=pop
ID_LIKE="ubuntu debian"
PRETTY_NAME="Pop!_OS 20.04 LTS"
VERSION_ID="20.04"
HOME_URL="https://pop.system76.com"
SUPPORT_URL="https://support.system76.com"
BUG_REPORT_URL="https://github.com/pop-os/pop/issues"
PRIVACY_POLICY_URL="https://system76.com/privacy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
LOGO=distributor-logo-pop-os
```

[COLOR=#0000ff]Kernel [/COLOR]
```
duplicity@annalee-call:~$ uname -r
5.4.0-7642-generic
```

[COLOR=#0000ff]df info[/COLOR]
```
duplicity@annalee-call:~$ df -h
Filesystem             Size  Used Avail Use% Mounted on
udev                   5.8G     0  5.8G   0% /dev
tmpfs                  1.2G  2.3M  1.2G   1% /run
/dev/mapper/data-root  927G   36G  890G   4% /
tmpfs                  5.8G  435M  5.4G   8% /dev/shm
tmpfs                  5.0M     0  5.0M   0% /run/lock
tmpfs                  5.8G     0  5.8G   0% /sys/fs/cgroup
/dev/sdb1              511M  186M  326M  37% /boot/efi
/dev/sdb2              4.0G  2.4G  1.7G  60% /recovery
/dev/mapper/data-root  927G   36G  890G   4% /swap
/dev/mapper/data-root  927G   36G  890G   4% /home
tmpfs                  1.2G   20K  1.2G   1% /run/user/110
tmpfs                  1.2G  156K  1.2G   1% /run/user/1000
/dev/sda1              1.9T   38G  1.8T   3% /media/duplicity/Seagate
/dev/mapper/data-root  927G   36G  890G   4% /run/timeshift/backup
```

[COLOR=#ff0000]Error[/COLOR] 
```
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned 
error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



Any and all help is really appreciated as I have reached wits end on what I know to do.

---

### Post by howefield on 2020-09-16
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Bashing-om on 2020-09-16
phoenixintraining; Hello -

Let's have a peek at what the package manager thinks -
Post back the full results of terminal commands:
```

sudo apt update
sudo apt upgrade

```

See where then we go to from here.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by phoenixintraining on 2020-09-16
Hey Guys, 

Thanks for the reply I was able to resolve this issue it looks like there was a problem with my init config of the os I forgot a comma at the after the splash... 
Thanks @howefield & Bashing-om 
I am posting below the output that caused the problem but the solution was a comma, funny how that works one small thing can cause so much damage. Thanks again guys! 

```

cat /etc/kernelstub/configuration
{
  "default": {
    "kernel_options": [
      "quiet",
      "splash"
    ],
    "esp_path": "/boot/efi",
    "setup_loader": false,
    "manage_mode": false,
    "force_update": false,
    "live_mode": false,
    "config_rev": 3
  },
  "user": {
    "kernel_options": [
      "quiet",
      "loglevel=0",
      "systemd.show_status=false",
      "splash"
      "rootflags=subvol=@"
    ],
    "esp_path": "/boot/efi",
    "setup_loader": true,
    "manage_mode": true,
    "force_update": false,
    "live_mode": false,
    "config_rev": 3
  }
}



```

---

### Post by Bashing-om on 2020-09-16
phoenixintraining; Good sleuthing :D

Thanks for providing the solution - 
as the issue is now resolved:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

