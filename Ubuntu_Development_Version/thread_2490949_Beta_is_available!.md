---
title: "Beta is available!"
date: 2023-09-21
forum: Ubuntu Development Version
---

### Post by corradoventu on 2023-09-21
Iso in daily is BETA! Ubuntu 23.10 "Mantic Minotaur" - Beta amd64 (20230919.1)
I installed in 2 partition with minimal and full install and both works fine.

---

### Post by Dennis N on 2023-09-21
Nice. Did you notice if the old installer (Ubiquity) is available as a alternate, perhaps by download? Otherwise, certain types of installation can't be done.

---

### Post by Rubi1200 on 2023-09-21
> **corradoventu said:**
> Iso in daily is BETA! Ubuntu 23.10 "Mantic Minotaur" - Beta amd64 (20230919.1)
I installed in 2 partition with minimal and full install and both works fine.

Thanks for the update.

Perhaps this might interest you?
[https://bugs.launchpad.net/ubuntu/+bug/2036987](https://bugs.launchpad.net/ubuntu/+bug/2036987)

---

### Post by corradoventu on 2023-09-21
The ISO with old installer ubuquity is available in [https://cdimages.ubuntu.com/daily-legacy/](https://cdimages.ubuntu.com/daily-legacy/)
Bug 2036987 refers to a laptop with legacy BIOS, i'm using a desktop.

---

### Post by Claus7 on 2023-09-21
Hello,

I suppose that from here: [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/)
the iso mantic-desktop-amd64.iso 2023-09-20 00:42 4.8G is even newer?

I 'm downloading it right now and check.

Regards!

---

### Post by Dennis N on 2023-09-21
> **corradoventu said:**
> The ISO with old installer ubuquity is available in [https://cdimages.ubuntu.com/daily-legacy/](https://cdimages.ubuntu.com/daily-legacy/)

Thanks. I now have it downloaded.

---

### Post by Claus7 on 2023-09-21
Hello,

I can see two options available for installation. Still, hellenic keyboard doesn't allow you to proceed with the installation. I cannot go back from timezone step in order to change that. An error showed up from systemd-localed and a bug was filled, which I cannot copy paste right now. I went and added manually the english keyboard under options and installation is taking place right now.

edit: [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/2037001](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/2037001)
installation of the non minimal option went fine

Regards!

---

### Post by #&amp;thj^% on 2023-09-21
> **Claus7 said:**
> Hello,
. I cannot go back from timezone step in order to change that
Regards!
Remember this one:
```
sudo timedatectl set-timezone your_time_zone
```
Also if needed:
```
timedatectl list-timezones
```

---

### Post by Claus7 on 2023-09-21
Hello,

> **1fallen said:**
> Remember this one:
```
sudo timedatectl set-timezone your_time_zone
```
Also if needed:
```
timedatectl list-timezones
```

didn't see your post earlier. I was occupied with the installation and filling the bug report. Timezone was selected out of the box. I couldn't go backwards in order to select just english keyboard so as to proceed with the installation, yet I managed to do it via options.
I suppose that your commands are the ones required in order to set the timezone. I wanted to return to a previous installation step. 
I do not know if actually the error reported is about the locale or the installation in general. Either way it got medium importance right away.

Regards!

---

### Post by #&amp;thj^% on 2023-09-21
> **Claus7 said:**
> 
 Either way it got medium importance right away.

Regards!
Nice, it's nice to see active bugs being sent..Thank You

---

### Post by MAFoElffen on 2023-09-22
New installer, Erase Disk and Install ZFS = Success today:
```

mafoelffen@minatuar-02:~$ uname -r
6.5.0-5-generic
mafoelffen@minatuar-02:~$ lsb_release -d
No LSB modules are available.
Description:    Ubuntu Mantic Minotaur (development branch)
mafoelffen@minatuar-02:~$ sudo zfs list
[sudo] password for mafoelffen: 
NAME                                               USED  AVAIL  REFER  MOUNTPOINT
bpool                                              127M  1.63G    96K  /boot
bpool/BOOT                                         126M  1.63G    96K  none
bpool/BOOT/ubuntu_1xhsg8                           126M  1.63G   126M  /boot
rpool                                             3.96G  13.5G    96K  /
rpool/ROOT                                        3.96G  13.5G    96K  none
rpool/ROOT/ubuntu_1xhsg8                          3.96G  13.5G  2.94G  /
rpool/ROOT/ubuntu_1xhsg8/srv                        96K  13.5G    96K  /srv
rpool/ROOT/ubuntu_1xhsg8/usr                       224K  13.5G    96K  /usr
rpool/ROOT/ubuntu_1xhsg8/usr/local                 128K  13.5G   128K  /usr/local
rpool/ROOT/ubuntu_1xhsg8/var                      1.02G  13.5G    96K  /var
rpool/ROOT/ubuntu_1xhsg8/var/games                  96K  13.5G    96K  /var/games
rpool/ROOT/ubuntu_1xhsg8/var/lib                  1.00G  13.5G   906M  /var/lib
rpool/ROOT/ubuntu_1xhsg8/var/lib/AccountsService    96K  13.5G    96K  /var/lib/AccountsService
rpool/ROOT/ubuntu_1xhsg8/var/lib/NetworkManager    136K  13.5G   136K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_1xhsg8/var/lib/apt              85.8M  13.5G  85.8M  /var/lib/apt
rpool/ROOT/ubuntu_1xhsg8/var/lib/dpkg             35.0M  13.5G  35.0M  /var/lib/dpkg
rpool/ROOT/ubuntu_1xhsg8/var/log                  11.5M  13.5G  11.5M  /var/log
rpool/ROOT/ubuntu_1xhsg8/var/mail                   96K  13.5G    96K  /var/mail
rpool/ROOT/ubuntu_1xhsg8/var/snap                 1.30M  13.5G  1.30M  /var/snap
rpool/ROOT/ubuntu_1xhsg8/var/spool                 112K  13.5G   112K  /var/spool
rpool/ROOT/ubuntu_1xhsg8/var/www                    96K  13.5G    96K  /var/www

```
Only one hiccup, with a quick work-around. On fist boot, it paused for a long time at the splash, then it went to a black screen and never recovered.

Shutdown with SIG_TERM.

On next boot, at Grub2 Boot menu: Deleted splash and added "---" in it's place. After "quiet" added "debug verbose"... Continued boot. Came right up into the Graphical Login Panel in less than a second. From then on, it worked as expected.

Good job.

---

### Post by Rubi1200 on 2023-09-25
> **corradoventu said:**
> Iso in daily is BETA! Ubuntu 23.10 "Mantic Minotaur" - Beta amd64 (20230919.1)
I installed in 2 partition with minimal and full install and both works fine.

Beta installer now shows the options as follows:

Default installation = Minimal

Expanded installation = Full

Isn't this a tad confusing?

Previous daily build had Normal and Minimal and Normal was the default now minimal is default?

At the partition screen the Beta does not offer the option to erase and reinstall Mantic; is this by design?

EDIT: installer crashed, bug report filed, feeling disappointed.

For anyone interested, this is the bug report:
[https://bugs.launchpad.net/subiquity/+bug/2037299](https://bugs.launchpad.net/subiquity/+bug/2037299)

---

### Post by corradoventu on 2023-09-26
Can't see the bug You report is PRIVATE?

---

### Post by Rubi1200 on 2023-09-26
I did not set the privacy, it was automatically set by Launchpad because apparently it contains a vulnerability.

I can set it to Public if you want?

But...do you know the answer to my questions in the previous post?

Grazie!

---

### Post by corradoventu on 2023-09-26
At the partition screen the Beta does not offer the option to erase and reinstall Mantic; is this by design?
but if You select 'Manual partitioning' you can install on an existing partition formatting it during installation.

---

