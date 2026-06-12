---
title: "Trouble during creation of local usb drive repository for Kubuntu 20.04."
date: 2024-01-23
forum: Repositories &amp; Backports
---

### Post by MLawrence on 2024-01-23
Hello everyone, I'm Mario.

I'm trying to create offline usb repositories for Kubuntu 20.04. I will require them because there is no internet access where me and mine will be going. 

Here's what I have done...

I attempted to use apt-mirror, following the steps found here: [https://www.linuxtechi.com/setup-local-apt-repository-server-ubuntu/](https://www.linuxtechi.com/setup-local-apt-repository-server-ubuntu/) 
I modified these steps to work with focal (20.04) instead. 
After waiting for a multi-hundred GB download (understood and expected), I modified my /etc/apt/sources.list to aim ONLY at the local repo I created on the drive with apt-mirror. 

I encountered the following errors: 

```
[FONT=monospace][COLOR=#000000]  File not found - /[/COLOR][/FONT][FONT=monospace]var/www/html/localrepo[/FONT][FONT=monospace][COLOR=#000000]/dists/focal/main/dep11/icons-48x48.tar (2: No such file or directory) [/COLOR]
Get:7 file:/var/www/html/localrepo/focal/main DEP-11 64x64 Icons [221 kB] 
Ign:7 file:/[/FONT][FONT=monospace]var/www/html/localrepo/[/FONT][FONT=monospace]focal/main DEP-11 64x64 Icons 
Reading package lists... Done 
[COLOR=#b26818]N: [/COLOR][COLOR=#000000]Download is performed unsandboxed as root as file '/[/COLOR][/FONT][FONT=monospace]var/www/html/localrepo[/FONT][FONT=monospace][COLOR=#000000]dists/focal/InRelease' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied) [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Failed to fetch file:/[/COLOR][/FONT][FONT=monospace]var/www/html/localrepo[/FONT][FONT=monospace][COLOR=#000000]/dists/focal/main/dep11/icons-48x48.tar  File not found - /[/COLOR][/FONT][FONT=monospace]var/www/html/localrepo[/FONT][FONT=monospace][COLOR=#000000]/dists/focal/main/dep11/icons-48x48.tar (2: No such file or directory) [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]


[/FONT]
```

As confirmed on the linuxtechi website, apt-mirror was failing to mirror necessary metadata. I ran the provided workaround configuration script after modifying it for focal (20.04), and my needs.

```
$ vi fix-errors.sh
#!/bin/bash

cd /var/www/html/ubuntu/archive.ubuntu.com/ubuntu/dists

for dist in jammy jammy-updates jammy-security jammy-backports; do
  for comp in main multiverse universe; do
    for size in 48 64 128; do
    wget http://archive.ubuntu.com/ubuntu/dists/$dist/$comp/dep11/icons-${size}x${size}@2.tar.gz -O $dist/$comp/dep11/icons-${size}x${size}@2.tar.gz;
   done
 done
done

cd /var/tmp
for p in "${1:-jammy}"{,-{security,updates,backports}}\
/{main,restricted,universe,multiverse};do >&2 echo "${p}"
wget -q -c -r -np -R "index.html*"\
"http://archive.ubuntu.com/ubuntu/dists/${p}/cnf/Commands-amd64.xz"
wget -q -c -r -np -R "index.html*"\
"http://archive.ubuntu.com/ubuntu/dists/${p}/cnf/Commands-i386.xz"
wget -q -c -r -np -R "index.html*" \
"http://archive.ubuntu.com/ubuntu/dists/${p}/binary-i386/"
done

sudo cp -av archive.ubuntu.com/ubuntu/ /var/www/html/ubuntu/archive.ubuntu.com
``` 
Please note, this is the original script, not the one I modified. 

After I modified the script and ran it, the same errors persisted. 
I then went to [http://archive.ubuntu.com](http://archive.ubuntu.com) and downloaded the specific files manually to my repo. It still gave the error that the files could not be found.
I verified my path, and the problems persisted.

I completely deleted the repository and decided to build the repo manually; following instructions from here: [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository) 
This proved successful, because even though it gave errors, when I ran "sudo apt update", it would tell me which files were missing,like before, and I simply added the needed metadata file from the official ubuntu repo. 
So I had a working repository, but no debian packages in it. This was expected and intended at that point. I wanted to ensure that apt could properly read metadata and update itself BEFORE committing to another multi-hundred GB download wait. 

I successfully used apt-mirror THIS time, purely to download pool folder data, mainly the deb files. I trashed the metadata that apt-mirror pulled (knowing it was incomplete), and provided the metadata that I pulled manually from the repo. 
Voila! It worked perfectly. I did a quick test installing and autoremoving the package gufw. All is well. 

I then copied my repo metadata to a usb drive. 
[[IMG]https://i.ibb.co/gzGYS93/usb.jpg[/IMG]]("https://ibb.co/PwRkcjN")

And adjusted the contents of /etc/apt/sources.list to aim solely at the usb drive.
```
[FONT=monospace][COLOR=#ffffff]  GNU nano 4.8                                                                                                                 /etc/apt/sources.list                                                                                                                           [/COLOR]
[COLOR=#5454ff]**#deb cdrom:[Kubuntu 20.04.4 LTS _Focal Fossa_ - Release amd64 (20220223)]/ focal main multiverse restricted universe**[/COLOR]

[COLOR=#5454ff]**# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to**[/COLOR]
[COLOR=#5454ff]**# newer versions of the distribution.**[/COLOR]
[COLOR=#5454ff]**#deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted**[/COLOR]
[COLOR=#5454ff]**# deb-src http://us.archive.ubuntu.com/ubuntu/ focal main restricted**[/COLOR]

[COLOR=#5454ff]**## Major bug fix updates produced after the final release of the**[/COLOR]
[COLOR=#5454ff]**## distribution.**[/COLOR]
[COLOR=#5454ff]**#deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted**[/COLOR]
[COLOR=#5454ff]**# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted**[/COLOR]

[COLOR=#5454ff]**## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu**[/COLOR]
[COLOR=#5454ff]**## team. Also, please note that software in universe WILL NOT receive any**[/COLOR]
[COLOR=#5454ff]**## review or updates from the Ubuntu security team.**[/COLOR]
[COLOR=#5454ff]**#deb http://us.archive.ubuntu.com/ubuntu/ focal universe**[/COLOR]
[COLOR=#5454ff]**# deb-src http://us.archive.ubuntu.com/ubuntu/ focal universe**[/COLOR]
[COLOR=#5454ff]**#deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe**[/COLOR]
[COLOR=#5454ff]**# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates universe**[/COLOR]

[COLOR=#5454ff]**## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu**[/COLOR]
[COLOR=#5454ff]**## team, and may not be under a free licence. Please satisfy yourself as to**[/COLOR]
[COLOR=#5454ff]**## your rights to use the software. Also, please note that software in**[/COLOR]
[COLOR=#5454ff]**## multiverse WILL NOT receive any review or updates from the Ubuntu**[/COLOR]
[COLOR=#5454ff]**## security team.**[/COLOR]
[COLOR=#5454ff]**#deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse**[/COLOR]
[COLOR=#5454ff]**# deb-src http://us.archive.ubuntu.com/ubuntu/ focal multiverse**[/COLOR]
[COLOR=#5454ff]**#deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse**[/COLOR]
[COLOR=#5454ff]**# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse**[/COLOR]

[COLOR=#5454ff]**## N.B. software from this repository may not have been tested as**[/COLOR]
[COLOR=#5454ff]**## extensively as that contained in the main release, although it includes**[/COLOR]
[COLOR=#5454ff]**## newer versions of some applications which may provide useful features.**[/COLOR]
[COLOR=#5454ff]**## Also, please note that software in backports WILL NOT receive any review**[/COLOR]
[COLOR=#5454ff]**## or updates from the Ubuntu security team.**[/COLOR]
[COLOR=#5454ff]**#deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse**[/COLOR]
[COLOR=#5454ff]**# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse**[/COLOR]

[COLOR=#5454ff]**## Uncomment the following two lines to add software from Canonical's**[/COLOR]
[COLOR=#5454ff]**## 'partner' repository.**[/COLOR]
[COLOR=#5454ff]**## This software is not part of Ubuntu, but is offered by Canonical and the**[/COLOR]
[COLOR=#5454ff]**## respective vendors as a service to Ubuntu users.**[/COLOR]
[COLOR=#5454ff]**# deb http://archive.canonical.com/ubuntu focal partner**[/COLOR]
[COLOR=#5454ff]**# deb-src http://archive.canonical.com/ubuntu focal partner**[/COLOR]

[COLOR=#5454ff]**#deb http://security.ubuntu.com/ubuntu focal-security main restricted**[/COLOR]
[COLOR=#5454ff]**# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted**[/COLOR]
[COLOR=#5454ff]**#deb http://security.ubuntu.com/ubuntu focal-security universe**[/COLOR]
[COLOR=#5454ff]**# deb-src http://security.ubuntu.com/ubuntu focal-security universe**[/COLOR]
[COLOR=#5454ff]**#deb http://security.ubuntu.com/ubuntu focal-security multiverse**[/COLOR]
[COLOR=#5454ff]**# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse**[/COLOR]

[COLOR=#5454ff]**# This system was installed using small removable media**[/COLOR]
[COLOR=#5454ff]**# (e.g. netinst, live or single CD). The matching "deb cdrom"**[/COLOR]
[COLOR=#5454ff]**# entries were disabled at the end of the installation process.**[/COLOR]
[COLOR=#5454ff]**# For information about how to configure apt package sources,**[/COLOR]
[COLOR=#5454ff]**# see the sources.list(5) manual.**[/COLOR]

[COLOR=#5454ff]**#deb [arch=amd64 signed-by=/usr/share/keyrings/oracle-virtualbox-2016.gpg] https://download.virtualbox.org/virtualbox/debian focal contrib**[/COLOR]

[COLOR=#5454ff]**#deb [trusted=yes] file:///var/www/html/localrepo focal main restricted universe multiverse**[/COLOR]
[COLOR=#b26818]deb[/COLOR][COLOR=#54ffff]** [trusted=yes] **[/COLOR][COLOR=#54ff54]**file:///media/mario/usbrepo**[/COLOR][COLOR=#ff5454]** focal**[/COLOR][COLOR=#ff54ff]** main restricted universe multiverse**[/COLOR] [/FONT]
```[FONT=monospace] 

But now the problem has returned.

It's like it sees everything else except the icons-48x48 tarball. 
I can verify that file IS infact there. 
[[IMG]https://i.ibb.co/4Px9r14/48x48-there.jpg[/IMG]]("https://ibb.co/gzCHK4t")

[FONT=arial][SIZE=2]And I attempted to chmod the InRelease file to 755... and then just for s&g's I chmod'd it to 777. 
I still get this output when I try to run "sudo apt update".
[/SIZE][/FONT][/FONT]```
[FONT=monospace][COLOR=#000000]Get:1 file:/media/mario/usbrepo focal InRelease [265 kB] [/COLOR]
Get:1 file:/media/mario/usbrepo focal InRelease [265 kB] 
Get:2 file:/media/mario/usbrepo focal/main i386 Packages [718 kB] 
Ign:2 file:/media/mario/usbrepo focal/main i386 Packages 
Get:3 file:/media/mario/usbrepo focal/main amd64 Packages [970 kB] 
Ign:3 file:/media/mario/usbrepo focal/main amd64 Packages 
Get:4 file:/media/mario/usbrepo focal/main Translation-en [506 kB] 
Ign:4 file:/media/mario/usbrepo focal/main Translation-en 
Get:5 file:/media/mario/usbrepo focal/main amd64 DEP-11 Metadata [494 kB] 
Ign:5 file:/media/mario/usbrepo focal/main amd64 DEP-11 Metadata 
Get:6 file:/media/mario/usbrepo focal/main DEP-11 48x48 Icons [98.4 kB] 
Ign:6 file:/media/mario/usbrepo focal/main DEP-11 48x48 Icons 
Get:7 file:/media/mario/usbrepo focal/main DEP-11 64x64 Icons [163 kB] 
Ign:7 file:/media/mario/usbrepo focal/main DEP-11 64x64 Icons 
Get:8 file:/media/mario/usbrepo focal/main DEP-11 64x64@2 Icons [15.8 kB] 
Ign:8 file:/media/mario/usbrepo focal/main DEP-11 64x64@2 Icons 
Get:9 file:/media/mario/usbrepo focal/main DEP-11 128x128 Icons [367 kB] 
Ign:9 file:/media/mario/usbrepo focal/main DEP-11 128x128 Icons 
Get:10 file:/media/mario/usbrepo focal/main amd64 c-n-f Metadata [29.5 kB] 
Ign:10 file:/media/mario/usbrepo focal/main amd64 c-n-f Metadata 
Get:11 file:/media/mario/usbrepo focal/restricted amd64 Packages [22.0 kB] 
Ign:11 file:/media/mario/usbrepo focal/restricted amd64 Packages 
Get:12 file:/media/mario/usbrepo focal/restricted i386 Packages [8,112 B] 
Ign:12 file:/media/mario/usbrepo focal/restricted i386 Packages 
Get:13 file:/media/mario/usbrepo focal/restricted Translation-en [6,212 B] 
Ign:13 file:/media/mario/usbrepo focal/restricted Translation-en 
Get:14 file:/media/mario/usbrepo focal/restricted amd64 c-n-f Metadata [392 B] 
Ign:14 file:/media/mario/usbrepo focal/restricted amd64 c-n-f Metadata 
Get:15 file:/media/mario/usbrepo focal/universe amd64 Packages [8,628 kB] 
Ign:15 file:/media/mario/usbrepo focal/universe amd64 Packages 
Get:16 file:/media/mario/usbrepo focal/universe i386 Packages [4,642 kB] 
Ign:16 file:/media/mario/usbrepo focal/universe i386 Packages 
Get:17 file:/media/mario/usbrepo focal/universe Translation-en [5,124 kB] 
Ign:17 file:/media/mario/usbrepo focal/universe Translation-en 
Get:18 file:/media/mario/usbrepo focal/universe amd64 DEP-11 Metadata [3,603 kB] 
Ign:18 file:/media/mario/usbrepo focal/universe amd64 DEP-11 Metadata 
Get:19 file:/media/mario/usbrepo focal/universe DEP-11 48x48 Icons [3,016 kB] 
Ign:19 file:/media/mario/usbrepo focal/universe DEP-11 48x48 Icons 
Get:20 file:/media/mario/usbrepo focal/universe DEP-11 64x64 Icons [7,794 kB] 
Ign:20 file:/media/mario/usbrepo focal/universe DEP-11 64x64 Icons 
Get:21 file:/media/mario/usbrepo focal/universe DEP-11 64x64@2 Icons [44.3 kB] 
Ign:21 file:/media/mario/usbrepo focal/universe DEP-11 64x64@2 Icons 
Get:22 file:/media/mario/usbrepo focal/universe DEP-11 128x128 Icons [14.3 MB] 
Ign:22 file:/media/mario/usbrepo focal/universe DEP-11 128x128 Icons 
Get:23 file:/media/mario/usbrepo focal/universe amd64 c-n-f Metadata [265 kB] 
Ign:23 file:/media/mario/usbrepo focal/universe amd64 c-n-f Metadata 
Get:24 file:/media/mario/usbrepo focal/multiverse amd64 Packages [144 kB] 
Ign:24 file:/media/mario/usbrepo focal/multiverse amd64 Packages 
Get:25 file:/media/mario/usbrepo focal/multiverse i386 Packages [74.7 kB] 
Ign:25 file:/media/mario/usbrepo focal/multiverse i386 Packages 
Get:26 file:/media/mario/usbrepo focal/multiverse Translation-en [104 kB] 
Ign:26 file:/media/mario/usbrepo focal/multiverse Translation-en 
Get:27 file:/media/mario/usbrepo focal/multiverse amd64 DEP-11 Metadata [48.4 kB] 
Ign:27 file:/media/mario/usbrepo focal/multiverse amd64 DEP-11 Metadata 
Get:28 file:/media/mario/usbrepo focal/multiverse DEP-11 48x48 Icons [23.1 kB] 
Ign:28 file:/media/mario/usbrepo focal/multiverse DEP-11 48x48 Icons 
Get:29 file:/media/mario/usbrepo focal/multiverse DEP-11 64x64 Icons [192 kB] 
Ign:29 file:/media/mario/usbrepo focal/multiverse DEP-11 64x64 Icons 
Get:30 file:/media/mario/usbrepo focal/multiverse DEP-11 64x64@2 Icons [214 B] 
Ign:30 file:/media/mario/usbrepo focal/multiverse DEP-11 64x64@2 Icons 
Get:31 file:/media/mario/usbrepo focal/multiverse DEP-11 128x128 Icons [326 kB] 
Ign:31 file:/media/mario/usbrepo focal/multiverse DEP-11 128x128 Icons 
Get:32 file:/media/mario/usbrepo focal/multiverse amd64 c-n-f Metadata [9,136 B] 
Ign:32 file:/media/mario/usbrepo focal/multiverse amd64 c-n-f Metadata 
Get:2 file:/media/mario/usbrepo focal/main i386 Packages [930 kB] 
Ign:2 file:/media/mario/usbrepo focal/main i386 Packages 
Get:3 file:/media/mario/usbrepo focal/main amd64 Packages [1,275 kB] 
Ign:3 file:/media/mario/usbrepo focal/main amd64 Packages 
Get:4 file:/media/mario/usbrepo focal/main Translation-en [506 kB] 
Ign:4 file:/media/mario/usbrepo focal/main Translation-en 
Get:5 file:/media/mario/usbrepo focal/main amd64 DEP-11 Metadata [705 kB] 
Ign:5 file:/media/mario/usbrepo focal/main amd64 DEP-11 Metadata 
Get:6 file:/media/mario/usbrepo focal/main DEP-11 48x48 Icons [154 kB] 
Ign:6 file:/media/mario/usbrepo focal/main DEP-11 48x48 Icons 
Get:7 file:/media/mario/usbrepo focal/main DEP-11 64x64 Icons [221 kB] 
Ign:7 file:/media/mario/usbrepo focal/main DEP-11 64x64 Icons 
Get:8 file:/media/mario/usbrepo focal/main DEP-11 64x64@2 Icons [32.3 kB] 
Ign:8 file:/media/mario/usbrepo focal/main DEP-11 64x64@2 Icons 
Get:9 file:/media/mario/usbrepo focal/main DEP-11 128x128 Icons [435 kB] 
Ign:9 file:/media/mario/usbrepo focal/main DEP-11 128x128 Icons 
Get:10 file:/media/mario/usbrepo focal/main amd64 c-n-f Metadata [111 kB] 
Ign:10 file:/media/mario/usbrepo focal/main amd64 c-n-f Metadata 
Get:11 file:/media/mario/usbrepo focal/restricted amd64 Packages [22.0 kB] 
Ign:11 file:/media/mario/usbrepo focal/restricted amd64 Packages 
Get:12 file:/media/mario/usbrepo focal/restricted i386 Packages [8,112 B] 
Ign:12 file:/media/mario/usbrepo focal/restricted i386 Packages 
Get:13 file:/media/mario/usbrepo focal/restricted Translation-en [6,212 B] 
Get:14 file:/media/mario/usbrepo focal/restricted amd64 c-n-f Metadata [392 B] 
Ign:13 file:/media/mario/usbrepo focal/restricted Translation-en 
Ign:14 file:/media/mario/usbrepo focal/restricted amd64 c-n-f Metadata 
Get:15 file:/media/mario/usbrepo focal/universe amd64 Packages [8,628 kB] 
Ign:15 file:/media/mario/usbrepo focal/universe amd64 Packages 
Get:16 file:/media/mario/usbrepo focal/universe i386 Packages [4,642 kB] 
Ign:16 file:/media/mario/usbrepo focal/universe i386 Packages 
Get:17 file:/media/mario/usbrepo focal/universe Translation-en [5,124 kB] 
Ign:17 file:/media/mario/usbrepo focal/universe Translation-en 
Get:18 file:/media/mario/usbrepo focal/universe amd64 DEP-11 Metadata [3,603 kB] 
Ign:18 file:/media/mario/usbrepo focal/universe amd64 DEP-11 Metadata 
Get:19 file:/media/mario/usbrepo focal/universe DEP-11 48x48 Icons [3,016 kB] 
Ign:19 file:/media/mario/usbrepo focal/universe DEP-11 48x48 Icons 
Get:20 file:/media/mario/usbrepo focal/universe DEP-11 64x64 Icons [7,794 kB] 
Ign:20 file:/media/mario/usbrepo focal/universe DEP-11 64x64 Icons 
Get:21 file:/media/mario/usbrepo focal/universe DEP-11 64x64@2 Icons [44.3 kB] 
Ign:21 file:/media/mario/usbrepo focal/universe DEP-11 64x64@2 Icons 
Get:22 file:/media/mario/usbrepo focal/universe DEP-11 128x128 Icons [14.3 MB] 
Ign:22 file:/media/mario/usbrepo focal/universe DEP-11 128x128 Icons 
Get:23 file:/media/mario/usbrepo focal/universe amd64 c-n-f Metadata [265 kB] 
Ign:23 file:/media/mario/usbrepo focal/universe amd64 c-n-f Metadata 
Get:24 file:/media/mario/usbrepo focal/multiverse amd64 Packages [144 kB] 
Ign:24 file:/media/mario/usbrepo focal/multiverse amd64 Packages 
Get:25 file:/media/mario/usbrepo focal/multiverse i386 Packages [74.7 kB] 
Ign:25 file:/media/mario/usbrepo focal/multiverse i386 Packages 
Get:26 file:/media/mario/usbrepo focal/multiverse Translation-en [104 kB] 
Ign:26 file:/media/mario/usbrepo focal/multiverse Translation-en 
Get:27 file:/media/mario/usbrepo focal/multiverse amd64 DEP-11 Metadata [48.4 kB] 
Ign:27 file:/media/mario/usbrepo focal/multiverse amd64 DEP-11 Metadata 
Get:28 file:/media/mario/usbrepo focal/multiverse DEP-11 48x48 Icons [23.1 kB] 
Ign:28 file:/media/mario/usbrepo focal/multiverse DEP-11 48x48 Icons 
Get:29 file:/media/mario/usbrepo focal/multiverse DEP-11 64x64 Icons [192 kB] 
Ign:29 file:/media/mario/usbrepo focal/multiverse DEP-11 64x64 Icons 
Get:30 file:/media/mario/usbrepo focal/multiverse DEP-11 64x64@2 Icons [214 B] 
Ign:30 file:/media/mario/usbrepo focal/multiverse DEP-11 64x64@2 Icons 
Get:31 file:/media/mario/usbrepo focal/multiverse DEP-11 128x128 Icons [326 kB] 
Ign:31 file:/media/mario/usbrepo focal/multiverse DEP-11 128x128 Icons 
Get:32 file:/media/mario/usbrepo focal/multiverse amd64 c-n-f Metadata [9,136 B] 
Ign:32 file:/media/mario/usbrepo focal/multiverse amd64 c-n-f Metadata 
Get:2 file:/media/mario/usbrepo focal/main i386 Packages [4,216 kB] 
Ign:2 file:/media/mario/usbrepo focal/main i386 Packages 
Get:3 file:/media/mario/usbrepo focal/main amd64 Packages [5,827 kB] 
Ign:3 file:/media/mario/usbrepo focal/main amd64 Packages 
Get:4 file:/media/mario/usbrepo focal/main Translation-en [709 kB] 
Ign:4 file:/media/mario/usbrepo focal/main Translation-en 
Get:5 file:/media/mario/usbrepo focal/main amd64 DEP-11 Metadata [2,125 kB] 
Ign:5 file:/media/mario/usbrepo focal/main amd64 DEP-11 Metadata 
Get:6 file:/media/mario/usbrepo focal/main DEP-11 48x48 Icons [154 kB] 
Err:6 file:/media/mario/usbrepo focal/main DEP-11 48x48 Icons 
  File not found - /media/mario/usbrepo/dists/focal/main/dep11/icons-48x48.tar (2: No such file or directory) 
Get:7 file:/media/mario/usbrepo focal/main DEP-11 64x64 Icons [221 kB] 
Ign:7 file:/media/mario/usbrepo focal/main DEP-11 64x64 Icons 
Reading package lists... Done 
[COLOR=#b26818]N: [/COLOR][COLOR=#000000]Download is performed unsandboxed as root as file '/media/mario/usbrepo/dists/focal/InRelease' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied) [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Failed to fetch file:/media/mario/usbrepo/dists/focal/main/dep11/icons-48x48.tar  File not found - /media/mario/usbrepo/dists/focal/main/dep11/icons-48x48.tar (2: No such file or directory) [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]
[/FONT]
``` 

I admit I am out of ideas. 
I reformatted the USB drive to exfat to get around potential permissions issues and the problem remains. 

And as of the time of this post, I have completely reformatted the usb drive and there is NO DATA on the drive and I STILL get the above output! Even with the drive PHYSICALLY DISCONNECTED it still gives me the above output!
I'm thinking apt has somehow choked-up. 

The moment I adjust /etc/apt/sources.list to aim at the local repo or the official online repos... apt is back to normal. But when I switch back the usb drive, whether its disconnected or not, I get the exact above error.

I went so far as to reboot my PC just to see if that has something to do with it.

I hate to admit it, but I need help. :(

My end goal is to have a viable offline local usb repo, that I can simply plug into a couple of different permanently-offline computers in order to update them. 
I'd like to be able to simply log into them, and add the usb repo to their sources list. and they use that when they detect it. 

But so far, I'm clueless.

---

