---
title: "Remove SNAP easily"
date: 2023-07-23
forum: Ubuntu, Linux and OS Chat
---

### Post by VMC on 2023-07-23
Very easily. Just did it on neon. Flawless!
```
bash -c "$(curl -fsSL https://raw.githubusercontent.com/BryanDollery/remove-snap/main/remove-snap.sh)"
```

Also [here]("https://github.com/popey/unsnap/blob/main/unsnap") is another script.

---

### Post by Rubi1200 on 2023-07-24
Hi,

the first script removes snaps and the snap daemon?

The second script removes snaps and tries to replace with flatpaks to the extent possible; have I understood this correctly?

Or both do essentially the same thing?

Either way, thanks for taking the time to put this together.

---

### Post by VMC on 2023-07-24
> **Rubi1200 said:**
> Hi,

the first script removes snaps and the snap daemon?
 Author Bryan Dollery's readme file:
> This simple bash script removes snap from Ubuntu. Why? Because snap is  severely broken and it completely messes up my servers. The content for  this script came from an [Ask Ubuntu answer from Lorenz Keel]("https://askubuntu.com/a/1285102/392607").  I've put it in github so that I can invoke it on my aws ec2 ubuntu  instances as part of my packer builds without having to copy the  contents of the script everywhere and eventually lose it.

Info found [here]("https://github.com/BryanDollery/remove-snap/tree/main").

> **Rubi1200 said:**
> The second script removes snaps and tries to replace with flatpaks to the extent possible; have I understood this correctly?
Author Popey's readme file.
> Quickly and easily migrate from using snap for applications to flatpak.  unsnap runs as a two-stage process. unsnap itself generates the scripts  to do the actual migration. This enables users to view and/or edit the  scripts prior to execution to validate or tweak them.

info found [here]("https://github.com/popey/unsnap/tree/main").

> **Rubi1200 said:**
> Or both do essentially the same thing?
There separate *gethub* scripts.

> **Rubi1200 said:**
> Either way, thanks for taking the time to put this together.
I use to use the command line inputs to remove Snap. I just recently found the two scripts above, and tried them out on neon.
Odd , neon says they don't have Snap installed, yet Firefox needed Snap to install on one of their unstable iso's.

---

### Post by #&amp;thj^% on 2023-07-24
+1 for both of those scripts, nice and easy for Ubuntu
Others Ubuntu/based might have some hand clean up after.
Truly adds to my  unsnappyness....lol

---

### Post by Robbyx on 2023-12-03
I just run the first script and a very lange number of cannot remove errors arose

eg
rm: cannot remove '/snap/gnome-boxes/9/usr/share/osinfo/os/microsoft.com/win-7.d/post-installable-drivers.xml': Read-only file system


All the errors are read only file system

Have I caused myself a load more problems?

---

### Post by #&amp;thj^% on 2023-12-03
Are you now booted and running a healthy system yet?
I've seen your other ZFS thread....so if your still trying to make your system right again, then just wait on this until you have a stable system. 
You could be adding more infliction to your system, and confusing anyone trying to help you in your other Thread. ;)
Regards

---

### Post by Robbyx on 2023-12-04
I agree with the tenor of your comment. Fortunately I ran the script after my other zfs thread had been resolved.

---

### Post by #&amp;thj^% on 2023-12-04
Ok if your solved from your other thread, I'll see if I can assist you now.

1st. You have unsnap somewhere, mine is in /home/me
```
cd unsnap
###Now I ran it as
./unsnap auto
```
Please Note if firefox is open it won't work correctly(you need to close firefox before running the code)
Let it finish it's first run.
2nd. I did a little extra steps at this point, I'll post them all:
```
sudo systemctl disable snapd.service
sudo systemctl disable snapd.socket
sudo systemctl disable snapd.seeded.service
sudo systemctl mask snapd.service
```
Now I go for my snaps:
```
snap remove gtk-common-themes
snap remove bare
snap remove gnome-42-2204
snap remove core22 
snap list
snap remove snapd
```
My system now:
```
systemctl status snapd
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)
TriggeredBy: &#9675; snapd.socket

```
I'm a bit under the weather today and might not reply back quickly, but I'll check in on you later.

---

### Post by Robbyx on 2023-12-04
So far I have not found   ~/unsnap.

As I have run the script I ran ssystemctl status (firefox was not loaded at the time of running the command line):

```
Dec 03 20:32:04 robins-MS-7C96 systemd[1]: Started Snap Daemon.
Dec 03 20:37:06 robins-MS-7C96 snapd[3478]: storehelpers.go:773: cannot refresh: snap has no updates available: "aphototoollibre", "bare", "core", "core18", "core20", "core>
Dec 03 20:54:08 robins-MS-7C96 snapd[3478]: api_snaps.go:412: Installing snap "firefox" revision unset
Dec 03 20:55:05 robins-MS-7C96 snapd[3478]: api_snaps.go:412: Installing snap "firefox" revision unset
Dec 03 21:36:41 robins-MS-7C96 systemd[1]: Stopping Snap Daemon...
Dec 03 21:36:41 robins-MS-7C96 snapd[3478]: main.go:155: Exiting on terminated signal.
Dec 03 21:36:41 robins-MS-7C96 snapd[3478]: overlord.go:516: Released state lock file
Dec 03 21:36:41 robins-MS-7C96 systemd[1]: snapd.service: Deactivated successfully.
Dec 03 21:36:41 robins-MS-7C96 systemd[1]: Stopped Snap Daemon.
Dec 03 21:36:41 robins-MS-7C96 systemd[1]: snapd.service: Consumed 1.751s CPU time.

```

What does the output above tell you about the status of my snaps and where I should run your solution in your last post above.

I wish you a speedy recovery

Robin

---

### Post by #&amp;thj^% on 2023-12-04
Hi Robin
open your terminal a new one please:
run:
```
ls | grep unsnap
```
it should show you "unsnap" if not tell me now.

---

### Post by Robbyx on 2023-12-04
robins@robins-MS-7C96:~$ ls | grep unsnap
robins@robins-MS-7C96:~$

---

### Post by #&amp;thj^% on 2023-12-04
> **Robbyx said:**
> So far I have not found   ~/unsnap.

I wish you a speedy recovery

Robin

Just noticed your typeO you forgot the leading [[COLOR="#FF0000"]**.**[/COLOR]]
copy this when your in "unsnap"
```
[COLOR="#FF0000"]./unsnap auto[/COLOR]
```

---

### Post by #&amp;thj^% on 2023-12-04
Robin I'm always in the dark when helping you, I have no idea where or what script your running but please so we are both on the same page.
```
git clone https://github.com/popey/unsnap
```

Change directory to the cloned repository:

```
 cd unsnap
```

Run the unsnap command:

```
sudo ./unsnap auto
```
And now back in post#8
start with the first line "sudo systemctl disable snapd.service" and run them all through "snap remove"

---

### Post by SeijiSensei on 2023-12-05
I switched to Debian 12 where there are no such things as snaps.

---

### Post by #&amp;thj^% on 2023-12-05
> **SeijiSensei said:**
> I switched to Debian 12 where there are no such things as snaps.

Well they are there, but just not inflicted on us at install time.
The user would have to manually install "snapd".

---

### Post by Robbyx on 2023-12-06
robins@robins-MS-7C96:~/unsnap$ git clone [https://github.com/popey/unsnap](https://github.com/popey/unsnap)
fatal: destination path 'unsnap' already exists and is not an empty directory.
robins@robins-MS-7C96:~/unsnap$  cd unsnap
bash: cd: unsnap: Not a directory
robins@robins-MS-7C96:~/unsnap$ ls | grep unsnap
unsnap
robins@robins-MS-7C96:~/unsnap$ 

after the above I ran:

 ls | grep unsnap
[COLOR="#FF0000"]unsnap[/COLOR]  (no added comment from system)

---

### Post by #&amp;thj^% on 2023-12-06
Why are you looking here>>"robins@robins-MS-7C96:~/unsnap"
With that same termiinal, please enter "[COLOR="#0000FF"]cd[/COLOR]"
and then show me this please:
```
ls
```

---

### Post by deadflowr on 2023-12-06
If you are in the unsnap directory and ls shows unsnap that should be the script.
Just make it execautablelthe and run it.

Was gonna spell check that, but i found it funny enough to keep as is.

---

### Post by #&amp;thj^% on 2023-12-06
> **deadflowr said:**
>  execautablelthe 

Was gonna spell check that, but i found it funny enough to keep as is.

Can I use that one? :lolflag:
Nothing has to be done 
```
ls
data-sets  ExtremeCooling4Linux-v0.3-x86_64.AppImage  Public                Templates
Desktop    memory.txt                                 snap                  unsnap
Documents  Music                                      surfshark-install.sh  Videos
Downloads  Pictures                                   temp.file

```
and ```
cd unsanp
```
```
&#9474;unsnap 
&#9492;&#9472;> ls
applist.csv         LICENSE                  log-2023-12-02.18.32.44  unsnap
excluded_snaps.txt  log-2023-11-29.20.39.15  README.md

```
Now just run 
```
**_./unsnap auto_**
WARNING! Care has been taken to ensure this script is safe.
The generated scripts will remove applications and data.
Please ensure you have backups in case you need to recover data.
Also note significant disk space may be required to migrate,
while both snaps and equivalent flatpaks are installed.
Press enter now to continue or CTRL+C to abort.

```

---

### Post by deadflowr on 2023-12-06
> **1fallen said:**
> Can I use that one? :lolflag:

Sure, why not.
Does it even need to be made, whatever i said it needed to be?
The web page doesn't explicitly say to mark it as executlalbled,

Edit:

I see the edited post with the additional info.
Thanks.

---

### Post by Robbyx on 2023-12-06
Following the advice here I ran the following in terminal:

```
robins@robins-MS-7C96:~/mkdir$ cd
robins@robins-MS-7C96:~$ cd unsnap
robins@robins-MS-7C96:~/unsnap$ sudo ./unsnap auto
[sudo] password for robins: 
WARNING! Care has been taken to ensure this script is safe.
The generated scripts will remove applications and data.
Please ensure you have backups in case you need to recover data.
Also note significant disk space may be required to migrate,
while both snaps and equivalent flatpaks are installed.
Press enter now to continue or CTRL+C to abort.
INFO: Detected ubuntu
INFO: Checking for snap binary
ERROR: snapd doesn't appear to be installed, exiting.
robins@robins-MS-7C96:~/unsnap$ ls
applist.csv         LICENSE                  log-2023-12-06.18.09.45  log-2023-12-06.18.13.52  README.md
excluded_snaps.txt  log-2023-12-06.17.57.53  log-2023-12-06.18.12.04  log-2023-12-06.22.51.11  unsnap
robins@robins-MS-7C96:~/unsnap$ 

```


Then  I ran unsnap from nautilus and that did no seem to do much  except produce an usnap.log  which contained:


> INFO: Detected ubuntu
INFO: Checking for snap binary
ERROR: snapd doesn't appear to be installed, exiting.

Does this mean that snap has been removed? How do I check it?

---

### Post by #&amp;thj^% on 2023-12-06
> **Robbyx said:**
> 
Does this mean that snap has been removed? How do I check it?

```
systemctl status snapd

```
should look like
```
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)
TriggeredBy: &#9675; snapd.socket

```
And
```
apt policy snap
snap:
  Installed: (none)
  Candidate: 2013-11-29-11
  Version table:
     2013-11-29-11 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages


```
And :
```
snap install hello-world
error: cannot communicate with server: Post "http://localhost/v2/snaps/hello-world": dial unix /run/snapd.socket: connect: no such file or directory

snap install firefox
error: cannot communicate with server: Post "http://localhost/v2/snaps/firefox": dial unix /run/snapd.socket: connect: no such file or directory


```

---

### Post by VMC on 2023-12-07
I do this: '**snap list**' to make sure all its children are gone, then '**sudo find / -name snap**'  to see what's lurking in the bushes.

---

### Post by Robbyx on 2023-12-09
It seems like my snap is disabled:

```
robins@robins-MS-7C96:~$ systemctl status snapd
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)
robins@robins-MS-7C96:~$ &#9675; snapd.service
&#9675;: command not found
robins@robins-MS-7C96:~$ apt policy snap
snap:
  Installed: (none)
  Candidate: 2013-11-29-11
  Version table:
     2013-11-29-11 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
robins@robins-MS-7C96:~$  snapd.service
snapd.service: command not found
robins@robins-MS-7C96:~$ snap install hello-world
Command 'snap' not found, but can be installed with:
sudo apt install snapd
robins@robins-MS-7C96:~$ stap list
Command 'stap' not found, but can be installed with:
sudo apt install systemtap
robins@robins-MS-7C96:~$ sudo find /-name snap
[sudo] password for robins: 
find: ‘/-name’: No such file or directory
find: ‘snap’: No such file or directory
robins@robins-MS-7C96:~$ sudo find / -name snap
/snap
/var/lib/gdm3/snap
/var/snap
find: ‘/run/user/1000/doc’: Permission denied
find: ‘/run/user/1000/gvfs’: Permission denied
robins@robins-MS-7C96:~$ 

```

---

### Post by #&amp;thj^% on 2023-12-09
Nice and Done.
If you later want firefox as a .deb, just post in the normal forums. :)

---

