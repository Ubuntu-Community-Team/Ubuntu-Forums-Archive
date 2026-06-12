---
title: "Boot info script not working so well ?"
date: 2011-12-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2011-12-19
I happened to notice this today:

[http://ubuntuforums.org/showpost.php?p=11548455&postcount=4](http://ubuntuforums.org/showpost.php?p=11548455&postcount=4)

Following that I tried the BIS in Precise, Oneiric, and Natty with similar results so I opened a thread at SourceForge:

[https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4890364](https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4890364)

Any thoughts?

---

### Post by coffeecat on 2011-12-19
I've been noticing that "looks for <blank> on this drive" for some while in threads now. Somewhat frustrating when you are wanting to see if grub is installed properly. Anyway, I've noticed something else odd. From my main machine and running Oneiric and bis 0.60:

```
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
```

Drive sdb is my Data drive, one single big ext4 partition. I don't remember using it as a boot drive, but I must have done (briefly) at one point. I've been doing a lot of drive swapping around over the past few months and I guess that must be the residuum from Natty's grub sitting in the mbr of sdb. So why is that giving a sensible output, and my Oneiric grub in sda not? :?

Thanks for bringing this up on Sourceforge.

---

### Post by oldfred on 2011-12-19
I have also notice the issue(s).

I think it is one of the changes in 1.99. Older versions of grub 1.99 when the script was last updated worked, but the newer versions of 1.99 do not correctly parse core.img for the partition it looks at.

I would also like to see it include the efi partitions in its parsing which I think is just adding a list of paths to seach & file names to look for.

Math errors seem to cause it to crash or stop outputing data. Not sure if it is just not having gawk installed (defaults to awk) or not.

---

### Post by kansasnoob on 2011-12-19
I'd appreciate some comments here:

[https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4890364](https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4890364)

That way Gert won't think it's just a fluke. I'm not sure what got changed but I even tried a Natty live CD and it fails so I think it had to be a change in the BIS itself.

I haven't had hardly any time to play lately so I didn't notice it until now.

Color me dazed and confused ............ but happy ;)

---

### Post by oldfred on 2011-12-19
kansasnoob,
are you able to login with a Ubuntu openID or do you have a separate id for sourceforge. I am confused since I thought I had a openID when I set up my wiki, but Ubuntu does not seem to be one of the openID options.


My system:
sda - msdos - Early Oneric on sdc16
sdb - gpt - my main install Maverick 11.10
sdc - msdos - 11.04 Kubuntu
sdd - gpt - 12.04 precise

script run from Maverick with gawk, awk, & mawk all installed.  Note the issue is only with the newest grub 1.99 in sdd.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 16 for .
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    34 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,gpt2)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos14)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 
    616448 of the same hard drive for core.img. core.img is at this location 
    and looks for  on this drive.

```

---

### Post by kansasnoob on 2011-12-20
> **oldfred said:**
> kansasnoob,
are you able to login with a Ubuntu openID or do you have a separate id for sourceforge. I am confused since I thought I had a openID when I set up my wiki, but Ubuntu does not seem to be one of the openID options.


My system:
sda - msdos - Early Oneric on sdc16
sdb - gpt - my main install Maverick 11.10
sdc - msdos - 11.04 Kubuntu
sdd - gpt - 12.04 precise

script run from Maverick with gawk, awk, & mawk all installed.  Note the issue is only with the newest grub 1.99 in sdd.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 16 for .
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    34 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,gpt2)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos14)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 
    616448 of the same hard drive for core.img. core.img is at this location 
    and looks for  on this drive.

```

I had to create an actual sourceforge account. But I see from your reporting I was sort of on the wrong track. I was thinking it was a matter of what media I was using to run the BIS rather than what version of grub is installed where. I'll do some more testing and see what I come up with.

---

### Post by Gert Hulselmans on 2011-12-20
Did any of you try the last git version?


```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'

chmod a+x bootinfoscript
```

---

### Post by oldfred on 2011-12-20
This was from the latest download. But I cannot see it or the result8.txt that it created. It works from terminal, but I cannot see either file in Nautilus. When I open it from the terminal it says it is in /home/fred and it is not a hidden file?? gksu gedit RESULTS8.txt works from terminal but it still is not in my home?

This version does show sdd correctly.:)

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 63d146fd-1c63-4b31-95c5-ab52e2892283 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    34 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,gpt2)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos14)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 
    616448 of the same hard drive for core.img. core.img is at this location 
    and looks for (,gpt3)/boot/grub on this drive.

```

---

### Post by kansasnoob on 2011-12-20
> **Gert Hulselmans said:**
> Did any of you try the last git version?


```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'

chmod a+x bootinfoscript
```

Haven't tried Precise yet, but I tried it with both a freshly installed Oneiric and a fully updated Oneiric. Both look OK to me:

[ATTACH]209442[/ATTACH]

I'll try Precise ASAP, but have some errands to run.

---

### Post by kansasnoob on 2011-12-20
> **oldfred said:**
> This was from the latest download. But I cannot see it or the result8.txt that it created. It works from terminal, but I cannot see either file in Nautilus. When I open it from the terminal it says it is in /home/fred and it is not a hidden file?? gksu gedit RESULTS8.txt works from terminal but it still is not in my home?

This version does show sdd correctly.:)

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 63d146fd-1c63-4b31-95c5-ab52e2892283 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    34 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,gpt2)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos14)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 
    616448 of the same hard drive for core.img. core.img is at this location 
    and looks for (,gpt3)/boot/grub on this drive.

```

> **I cannot see it or the result8.txt that it created. It works from terminal**

Same thing here, but running ls shows it so I just run "sudo bash bootinfoscript", wondered what I might be doing wrong :)

---

### Post by Gert Hulselmans on 2011-12-20
Good that it works now :).

The grub v1.99 bugs were fixed almost a half year ago. I want to finish some features before releasing the next version. I hope to find some time next week.

Is the RESULTS.txt file only hidden on the last version of Ubuntu or does it always happen with the new script?
Maybe it is a bug in nautilus. Can you try to refresh the nautilus view? Or logout and login again?

Does the following work to view the file as regular user?
```
less RESULTS.txt
```

@ kansasnoob
Did you install gawk when you ran your last tests?

---

### Post by oldfred on 2011-12-20
I close Nautilus, open Nautilus, turned on & off hidden files, did a search of entire system and found a bunch of RESULTS8.txt that I had tucked away for backups, but have not been able to find either file in my /home/fred folder except from terminal. less also works as did the gksu gedit command, and it ran, so files are really there.

We have seen this bug also and it seems script crashes when this happens and we get little data. I saved this from some post where I was trying to help.

```
unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")
```Also we are seeing more UEFI systems.

[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
find /boot/efi -name "*efi"
```
/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/BOOT/refit.efi
/boot/efi/EFI/BOOT/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi
/boot/efi/EFI/grub/grub.efi
/boot/efi/EFI/BOOT-backup/bootx64.efi
/boot/efi/EFI/BOOT-backup/BOOT/refit/refit.efi
/boot/efi/EFI/BOOT-backup/BOOT/bootx64.efi
```A couple more with some UEFI info:
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg outputs
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570) - see post #36 for listing of efi files
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.


Did you want me to post full script?

---

### Post by Gert Hulselmans on 2011-12-20
> **oldfred said:**
> I close Nautilus, open Nautilus, turned on & off hidden files, did a search of entire system and found a bunch of RESULTS8.txt that I had tucked away for backups, but have not been able to find either file in my /home/fred folder except from terminal. less also works as did the gksu gedit command, and it ran, so files are really there.
Is the file visible in nautilus after a reboot?
> **oldfred said:**
> 
We have seen this bug also and it seems script crashes when this happens and we get little data. I saved this from some post where I was trying to help.
```
unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")
```

This error happens when the user doesn't have gawk installed and when grub4dos is found.
> **oldfred said:**
> 
Also we are seeing more UEFI systems.

[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
find /boot/efi -name "*efi"
```
/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/BOOT/refit.efi
/boot/efi/EFI/BOOT/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi
/boot/efi/EFI/grub/grub.efi
/boot/efi/EFI/BOOT-backup/bootx64.efi
/boot/efi/EFI/BOOT-backup/BOOT/refit/refit.efi
/boot/efi/EFI/BOOT-backup/BOOT/bootx64.efi
```A couple more with some UEFI info:
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg outputs
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570) - see post #36 for listing of efi files
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.
The git version will list most EFI modules: At least for now all /efi/*/*.efi files should be detected. Can you ask them to run the last git version to see if it finds the files?

> **oldfred said:**
> 
Did you want me to post full script?
If there are no strange errors, malformed text, new boot sectors, ... then I don't really need it.

---

### Post by VMC on 2011-12-20
Gert,

Per your instructions, I attached my MBR.

I have Windows7, Ubuntu Lucid, Mint 12, Fedora 16. The mbr should point to Fedora 16, but I get the "??" instead from RESULTS.txt.

No matter who I put in charge, I always get "??".

Vern

---

### Post by Gert Hulselmans on 2011-12-20
@ VMC
Did you install **unlzma**?
You normally should see a message about it, in the error part of the RESULTS.txt file.

---

### Post by VMC on 2011-12-20
> **Gert Hulselmans said:**
> @ VMC
Did you install **unlzma**?
You normally should see a message about it, in the error part of the RESULTS.txt file.

This is the err message:

```
=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically
```

I don't see any reference to unlzma. But it use to work using Lucid and when I make it my boot partition I get the same "??" message.

edit: I do have the c-header for lzma in Fedora:
/lib/modules/3.1.5-6.fc16.x86_64/build/include/linux/decompress/unlzma.h

---

### Post by oldfred on 2011-12-20
For whatever reason I let computer sleep for an hour or two and now I can see both files bootinfoscript & results8.txt with Nautilus??



unizma seems to be part of xz-utils

sudo apt-get install xz-utils

man xz
> unlzma is equivalent to xz --format=lzma --decompress.

---

### Post by Gert Hulselmans on 2011-12-21
@VMC
What is the output of:
```
type unlzma > /dev/null 2>&1 ; echo $?
``````
which unlzma
which lzma
which 7z
which xz
```Also change:
```
printf '\x5d\x00\x00\x01\x00'$( printf '%08x' $((${total_uncompressed_size} - ${offset_lzma} + 512 ))  | awk '{printf "\\x%s\\x%s\\x%s\\x%s", substr($0,7,2), substr($0,5,2), substr($0,3,2), substr($0,1,2)}' )'\x00\x00\x00\x00' > ${Tmp_Log};
```To:
```
printf '\x5d\x00\x00\x01\x00'$( printf '%08x' $((${total_uncompressed_size} - ${offset_lzma} + 512 ))  | ${AWK} '{printf "\\x%s\\x%s\\x%s\\x%s", substr($0,7,2), substr($0,5,2), substr($0,3,2), substr($0,1,2)}' )'\x00\x00\x00\x00' > ${Tmp_Log};
```

When running the commands manually, without changing the script, on the file you send, I get: **(,msdos6)/boot/grub2** and not ??

---

### Post by kansasnoob on 2011-12-21
> **Gert Hulselmans said:**
> Good that it works now :).

The grub v1.99 bugs were fixed almost a half year ago. I want to finish some features before releasing the next version. I hope to find some time next week.

Is the RESULTS.txt file only hidden on the last version of Ubuntu or does it always happen with the new script?
Maybe it is a bug in nautilus. Can you try to refresh the nautilus view? Or logout and login again?

Does the following work to view the file as regular user?
```
less RESULTS.txt
```

@ kansasnoob
Did you install gawk when you ran your last tests?

Sorry for the long delay, I was too tired when I got back to the house to make sense of anything so I just went to bed.

Regarding, "Did you install gawk when you ran your last tests?", I think the answer is no. The output named "fresh_oneiric" is a freshly installed Oneiric with no updates applied, no packages added, and no modifications made at all.

The output named "updated_oneiric" is my stable daily-work OS and I can't think of any reason I would have installed gawk, but I'll double check the package status on both of those OS's after this post.

Regarding the "hidden file" issue I think it must be a Nautilus and/or Unity thing because the Precise I'm running now is [converted to a classic DE]("http://ubuntuforums.org/showthread.php?t=1886799") and I don't have that issue with it.

Regarding 'unlzma', 'lzma', 'xz', etc. you might find my Precise updates interesting (hadn't had time to update my "stable" Precise in several days):

```
Reading state information... Done
Calculating upgrade... Done
The following packages will be **[COLOR="Red"]REMOVED[/COLOR]**:
  **[COLOR="Red"]lzma[/COLOR]** python-gobject-cairo
The following NEW packages will be **[COLOR="Red"]installed[/COLOR]**:
  folks-common fonts-khmeros-core fonts-takao-pgothic krb5-locales
  libabiword-2.9 libatk-adaptor-schemas libcurl3-nss libgdk-pixbuf2.0-common
  libminiupnpc8 libnautilus-extension1a libnl-3-200 libnl-genl-3-200
  libnl-route-3-200 libvte-2.90-common linux-headers-3.2.0-6
  linux-headers-3.2.0-6-generic linux-image-3.2.0-6-generic python-gi-cairo
  **[COLOR="Red"]xz-lzma[/COLOR]**
The following packages will be upgraded:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview
  accountsservice acl acpid app-install-data-partner aptdaemon aptdaemon-data
  avahi-autoipd avahi-daemon avahi-utils bamfdaemon banshee
  banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore
  base-passwd binutils brasero brasero-cdrkit brasero-common bsdutils
  busybox-initramfs busybox-static bzip2 c2esp colord cpp cpp-4.6 cups
  cups-bsd cups-client cups-common cups-ppdc dconf-gsettings-backend
  dconf-service debianutils deja-dup desktop-file-utils dictionaries-common
  dnsmasq-base dosfstools dpkg duplicity eject empathy empathy-common eog
  evince evince-common file-roller firefox firefox-globalmenu
  firefox-gnome-support firefox-locale-en gcc gcc-4.6 gcc-4.6-base gconf2
  gconf2-common gdb gedit gedit-common ghostscript ghostscript-cups
  ghostscript-x gir1.2-freedesktop gir1.2-gconf-2.0 gir1.2-gdkpixbuf-2.0
  gir1.2-glib-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gst-plugins-base-0.10
  gir1.2-gstreamer-0.10 gir1.2-gtk-2.0 gir1.2-gtk-3.0 gir1.2-polkit-1.0
  gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-vte-2.90
  gnome-accessibility-themes gnome-bluetooth gnome-control-center
  gnome-control-center-data gnome-desktop-data gnome-disk-utility
  gnome-online-accounts gnome-screensaver gnome-session gnome-session-bin
  gnome-session-canberra gnome-session-common gnome-session-fallback
  gnome-settings-daemon gnome-terminal gnome-terminal-data
  gnome-themes-standard grep gsettings-desktop-schemas gstreamer0.10-alsa
  gstreamer0.10-fluendo-mp3 gstreamer0.10-gconf gstreamer0.10-gnomevfs
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines-murrine gtk2-engines-pixbuf gucharmap gwibber
  gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter hunspell-en-us hyphen-en-us ibus ibus-gtk ibus-gtk3
  ifupdown indicator-appmenu initscripts iptables isc-dhcp-client
  isc-dhcp-common iso-codes jockey-common jockey-gtk language-selector-common
  language-selector-gnome libaccountsservice0 libacl1 libarchive1
  libatkmm-1.6-1 libattr1 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0
  libavahi-ui-gtk3-0 libavc1394-0 libbamf0 libbamf3-0 libblkid1
  libbrasero-media3-1 libbz2-1.0 libc-bin libc-dev-bin libc6 libc6-dev
  libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcap-ng0 libcolord1
  libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
  libdb4.8 libdconf-dbus-1-0 libdconf0 libdmapsharing-3.0-2 libdvbpsi7
  libdvdnav4 libdvdread4 libevent-2.0-5 libevince3-3 libexif12 libfftw3-3
  libflite1 libfolks-eds25 libfolks-telepathy25 libfolks25 libgail-3-0
  libgail-common libgail18 libgcc1 libgconf2-4 libgdk-pixbuf2.0-0 libgdu-gtk0
  libgdu0 libgirepository-1.0-1 libgksu2-0 libglib2.0-0 libglib2.0-bin
  libglib2.0-data libglibmm-2.4-1c2a libgmp10 libgnome-bluetooth8
  libgnome-control-center1 libgnome2-0 libgnome2-common libgnutls26
  libgoa-1.0-0 libgomp1 libgs9 libgs9-common libgssapi-krb5-2
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkmm-2.4-1c2a
  libgucharmap-2-90-7 libgudev-1.0-0 libgwibber-gtk2 libgwibber2 libhyphen0
  libibus-1.0-0 libidn11 libido3-0.1-0 libjack-jackd2-0 libjasper1
  libk5crypto3 libkpathsea5 libkrb5-3 libkrb5support0
  libmission-control-plugins0 libmount1 libmusicbrainz4c2a libnl3
  libnm-glib-vpn1 libnm-glib4 libnm-util2 libnspr4 libnspr4-0d libnss3
  libnss3-1d liboauth0 libp11-kit0 libpangomm-1.4-1 libpci3 libperl5.14
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0
  libpoppler-glib8 libpoppler19 libportaudio2 libproxy0
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpython2.7 libquadmath0
  libraptor2-0 libraw1394-11 libraw5 librhythmbox-core4 librsvg2-2
  librsvg2-common libshout3 libsigc++-2.0-0c2a libsmbclient libsnmp-base
  libsnmp15 libstdc++6 libsyncdaemon-1.0-1 libtag1-vanilla libtag1c2a
  libtext-iconv-perl libtotem-plparser17 libtotem0 libubuntuone-1.0-1
  libubuntuone1.0-cil libudev0 libunity-core-4.0-4 libutouch-frame1
  libutouch-geis1 libuuid-perl libuuid1 libvte-2.90-9 libvte-common libvte9
  libwbclient0 libwpd-0.9-9 libwps-0.2-2 libwv-1.2-3 libyelp0
  libzeitgeist-1.0-1 linux-firmware linux-generic linux-headers-generic
  linux-image-generic linux-libc-dev mobile-broadband-provider-info mount
  mousetweaks multiarch-support myspell-en-au mythes-en-au nautilus
  nautilus-data nautilus-sendto-empathy nautilus-share network-manager
  notify-osd onboard openoffice.org-common pciutils perl perl-base
  perl-modules policykit-1 policykit-1-gnome poppler-utils pppconfig
  printer-driver-c2esp procps pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-apt python-apt-common python-aptdaemon
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-gi
  python-gobject python-gobject-2 python-httplib2 python-ibus
  python-launchpadlib python-libproxy python-papyon python-pyasn1
  python-pyorbit python-simplejson python-ubuntuone-client python-vte
  python2.7 python2.7-minimal python3.2 python3.2-minimal rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins rsyslog samba-common
  samba-common-bin smbclient software-center splix sysv-rc sysvinit-utils
  telepathy-gabble telepathy-mission-control-5 thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-gb thunderbird-locale-en-us totem totem-common
  totem-mozilla totem-plugins totem-plugins-extra transmission-common
  transmission-gtk ttf-khmeros-core ttf-takao-pgothic ubuntu-desktop
  ubuntu-minimal ubuntu-restricted-addons ubuntu-standard ubuntu-tweak
  ubuntuone-client ubuntuone-client-gnome ubuntuone-installer udev unity
  unity-common unity-lens-applications unity-services update-manager
  update-manager-core util-linux uuid-runtime vinagre vino xdiagnose
  xserver-common xserver-xorg-core xserver-xorg-video-intel
  xserver-xorg-video-nouveau yelp zukitwo-dark-gtk-theme
408 upgraded, 19 newly installed, 2 to remove and 0 not upgraded.
```

Regardless here is the output of BIS in my freshly updated Precise:

[ATTACH]209498[/ATTACH]

Looks OK to me :)

BTW, many thanks to Gert for supporting the BIS. We'd be up a creek w/o a paddle if it didn't exist, so many thanks again. We owe you big time.

---

### Post by kansasnoob on 2011-12-21
Regarding 'gawk', I happen to prefer 'aptitude' for displaying package status so I installed 'aptitude' in Precise and then:

```
lance@lance-desktop:~$ aptitude show gawk
Package: gawk                     
State: not installed
Version: 1:3.1.8+dfsg-0.1build1
Priority: optional
Section: interpreters
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,282 k
PreDepends: libc6 (>= 2.11), libsigsegv2 (>= 2.9)
Provides: awk

```

I'll now check both of those Oneiric installs.

---

### Post by kansasnoob on 2011-12-21
In the freshly installed Oneiric I get:

```
lance@lance-desktop:~$ aptitude show gawk
Package: gawk                     
State: not installed
Version: 1:3.1.8+dfsg-0.1build1
Priority: optional
Section: interpreters
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,282 k
PreDepends: libc6 (>= 2.11), libsigsegv2 (>= 2.9)
Provides: awk

```

---

### Post by Gert Hulselmans on 2011-12-21
@ kansasnoob
Can you run the **which** commands too, to see if unlzma still exists or that only xz is installed:
```
which unlzma
which lzma
which 7z
which xz
```
busybox awk on Ubuntu 12.04 doesn't seem to support math operations. So it won't show any filesizes:
```
=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-4-generic-pae            3
               =                boot/vmlinuz-3.2.0-4-generic-pae               1
               =                initrd.img                                     3
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: (stdin): Compressed data is corrupt
unlzma: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```Is mawk in Ubuntu 12.04 still at 1.3.3 (and thus broken)?
```
mawk -W version
```If you downloaded the git version of bootinfoscript it is advisable to run --update, so it easier for me to keep track of which exact version of BIS you ran (in case I just changed some stuff).
```

  The last development version of Boot Info Script can be downloaded, with:
    (no root rights needed)

    ./bootinfoscript --update <filename>

  If no filename is specified, the file will be saved in the home dir as
  "bootinfoscript_YYYY-MM-DD_hh:mm:ss".

``````
$ ./bootinfoscript --update

Downloading last development version of Boot Info Script from git:

--2011-12-21 15:49:26--  http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD
Resolving bootinfoscript.git.sourceforge.net... 216.34.181.91
Connecting to bootinfoscript.git.sourceforge.net|216.34.181.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `/home/user/bootinfoscript_2011-12-21_14:49:26'

    [   <=>                                 ] 113,072      201K/s   in 0.6s    

2011-12-21 15:49:27 (201 KB/s) - `/home/user/bootinfoscript_2011-12-21_14:49:26' saved [113072]


The development version of Boot Info Script is saved as:
"/home/user/bootinfoscript_2011-12-21_14:49:26"
``````
# Make it executable
chmod a+x ./bootinfoscript_2011-12-21_14\:49\:26

# Display version info (also displayed in the RESULTS.txt file)
$ ./bootinfoscript_2011-12-21_14\:49\:26 --version

Boot Info Script version: 0.60
Release date:             17 May 2011
Last git commit:          a63e662 README: Update "Usage" section.
Retrieved from git on:    2011-12-21 14:49:26
```

---

### Post by kansasnoob on 2011-12-21
In my "every-day" Oneiric I also get:

```
lance@lance-desktop:~$ aptitude show gawk
Package: gawk                     
State: not installed
Version: 1:3.1.8+dfsg-0.1build1
Priority: optional
Section: interpreters
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,282 k
PreDepends: libc6 (>= 2.11), libsigsegv2 (>= 2.9)
Provides: awk

```

---

### Post by kansasnoob on 2011-12-21
> **Gert Hulselmans said:**
> @ kansasnoob
Can you run the **which** commands too, to see if unlzma still exists or that only xz is installed:
```
which unlzma
which lzma
which 7z
which xz
```
busybox awk on Ubuntu 12.04 doesn't seem to support math operations. So it won't show any filesizes:
```
=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-4-generic-pae            3
               =                boot/vmlinuz-3.2.0-4-generic-pae               1
               =                initrd.img                                     3
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: (stdin): Compressed data is corrupt
unlzma: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```Is mawk in Ubuntu 12.04 still at 1.3.3 (and thus broken)?
```
mawk -W version
```If you downloaded the git version of bootinfoscript it is advisable to run --update, so it easier for me to keep track of which exact version of BIS you ran (in case I just changed some stuff).
```

  The last development version of Boot Info Script can be downloaded, with:
    (no root rights needed)

    ./bootinfoscript --update <filename>

  If no filename is specified, the file will be saved in the home dir as
  "bootinfoscript_YYYY-MM-DD_hh:mm:ss".

``````
$ ./bootinfoscript --update

Downloading last development version of Boot Info Script from git:

--2011-12-21 15:49:26--  http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD
Resolving bootinfoscript.git.sourceforge.net... 216.34.181.91
Connecting to bootinfoscript.git.sourceforge.net|216.34.181.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `/home/user/bootinfoscript_2011-12-21_14:49:26'

    [   <=>                                 ] 113,072      201K/s   in 0.6s    

2011-12-21 15:49:27 (201 KB/s) - `/home/user/bootinfoscript_2011-12-21_14:49:26' saved [113072]


The development version of Boot Info Script is saved as:
"/home/user/bootinfoscript_2011-12-21_14:49:26"
``````
# Make it executable
chmod a+x ./bootinfoscript_2011-12-21_14\:49\:26

# Display version info (also displayed in the RESULTS.txt file)
$ ./bootinfoscript_2011-12-21_14\:49\:26 --version

Boot Info Script version: 0.60
Release date:             17 May 2011
Last git commit:          a63e662 README: Update "Usage" section.
Retrieved from git on:    2011-12-21 14:49:26
```

Give me a little bit to digest that :)

---

### Post by VMC on 2011-12-21
@Gert,

> **Gert Hulselmans said:**
> @VMC
What is the output of:
```
type unlzma > /dev/null 2>&1 ; echo $?
``````
which unlzma
which lzma
which 7z
which xz
```Also change:
```
printf '\x5d\x00\x00\x01\x00'$( printf '%08x' $((${total_uncompressed_size} - ${offset_lzma} + 512 ))  | awk '{printf "\\x%s\\x%s\\x%s\\x%s", substr($0,7,2), substr($0,5,2), substr($0,3,2), substr($0,1,2)}' )'\x00\x00\x00\x00' > ${Tmp_Log};
```To:
```
printf '\x5d\x00\x00\x01\x00'$( printf '%08x' $((${total_uncompressed_size} - ${offset_lzma} + 512 ))  | ${AWK} '{printf "\\x%s\\x%s\\x%s\\x%s", substr($0,7,2), substr($0,5,2), substr($0,3,2), substr($0,1,2)}' )'\x00\x00\x00\x00' > ${Tmp_Log};
```

When running the commands manually, without changing the script, on the file you send, I get: **(,msdos6)/boot/grub2** and not ??

```
$ type unlzma > /dev/null 2>&1 ; echo $?
**1**

$ which unlzma
/usr/bin/which:** no unlzma** in (/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/vmc/.local/bin:/home/vmc/bin)
$ which lzma
/usr/bin/which: **no lzma** in (/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/vmc/.local/bin:/home/vmc/bin)
$ which 7z
/usr/bin/which:** no 7z** in (/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/vmc/.local/bin:/home/vmc/bin)
$ which xz
**[B]/usr/bin/xz**[/B]
```

> When running the commands manually, without changing the script, on the file you send, I get: **(,msdos6)/boot/grub2** and not ??Good to know!
I'll try running with new script.

---

### Post by Gert Hulselmans on 2011-12-21
@ VMC
A quick test version attached.

Can you attach the RESULTS.txt file from the previous version and from the test version in your next post? I don't get it why you don't see the message that you need unlzma.

From which distro are you running BIS?

---

### Post by kansasnoob on 2011-12-21
Since I don't know what I'm doing I decided to go at this one chunk at a time. In my every-day Oneiric:

```
lance@lance-desktop:~$ which unlzma
/usr/bin/unlzma
lance@lance-desktop:~$ which lzma
/usr/bin/lzma
lance@lance-desktop:~$ which 7z
lance@lance-desktop:~$ which xz
/usr/bin/xz

```

Then:

```
lance@lance-desktop:~$ sudo bash bootinfoscript --update
[sudo] password for lance: 

Downloading last development version of Boot Info Script from git:

--2011-12-21 09:55:36--  http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD
Resolving bootinfoscript.git.sourceforge.net... 216.34.181.91
Connecting to bootinfoscript.git.sourceforge.net|216.34.181.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `/home/lance/bootinfoscript_2011-12-21_15:55:36'

    [  <=>                                  ] 113,072      302K/s   in 0.4s    

2011-12-21 09:55:39 (302 KB/s) - `/home/lance/bootinfoscript_2011-12-21_15:55:36' saved [113072]


The development version of Boot Info Script is saved as:
"/home/lance/bootinfoscript_2011-12-21_15:55:36"

```

Then:

```
lance@lance-desktop:~$ sudo bash bootinfoscript_2011-12-21_15:55:36
[sudo] password for lance: 

Boot Info Script 0.60      [17 May 2011]
  Last git commit:         a63e662 README: Update "Usage" section.
  Retrieved from git on:   2011-12-21 15:55:36


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Searching sda13 for information... 
Searching sda14 for information... 
Searching sda15 for information... 
Searching sda16 for information... 
Searching sda17 for information... 
Searching sda18 for information... 
Searching sda19 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 

Finished. The results are in the file "RESULTS2.txt"
located in "/home/lance/".

```

Which results in:

[ATTACH]209503[/ATTACH]

I'll check Precise ASAP but I must first check some stock tank heaters (animals need water) and I'll check back here first to see if I'm even thinking along the right lines :)

---

### Post by VMC on 2011-12-21
> **Gert Hulselmans said:**
> @ VMC
A quick test version attached.

Can you attach the RESULTS.txt file from the previous version and from the test version in your next post? I don't get it why you don't see the message that you need unlzma.

From which distro are you running BIS?

@Gert,

Just installing lzma fixed my issue, thanks.

I'm unsure if Lucid and Mint12 have lzma installed. I'll check.

edit: now that I think about it, I ran bis on all three OS's, Fedora, Lucid, Mint12. All had the same "??" issue. What changed, and when was lzma added?

---

### Post by kansasnoob on 2011-12-21
> **kansasnoob said:**
> Since I don't know what I'm doing I decided to go at this one chunk at a time. In my every-day Oneiric:

```
lance@lance-desktop:~$ which unlzma
/usr/bin/unlzma
lance@lance-desktop:~$ which lzma
/usr/bin/lzma
lance@lance-desktop:~$ which 7z
lance@lance-desktop:~$ which xz
/usr/bin/xz

```

Then:

```
lance@lance-desktop:~$ sudo bash bootinfoscript --update
[sudo] password for lance: 

Downloading last development version of Boot Info Script from git:

--2011-12-21 09:55:36--  http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD
Resolving bootinfoscript.git.sourceforge.net... 216.34.181.91
Connecting to bootinfoscript.git.sourceforge.net|216.34.181.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `/home/lance/bootinfoscript_2011-12-21_15:55:36'

    [  <=>                                  ] 113,072      302K/s   in 0.4s    

2011-12-21 09:55:39 (302 KB/s) - `/home/lance/bootinfoscript_2011-12-21_15:55:36' saved [113072]


The development version of Boot Info Script is saved as:
"/home/lance/bootinfoscript_2011-12-21_15:55:36"

```

Then:

```
lance@lance-desktop:~$ sudo bash bootinfoscript_2011-12-21_15:55:36
[sudo] password for lance: 

Boot Info Script 0.60      [17 May 2011]
  Last git commit:         a63e662 README: Update "Usage" section.
  Retrieved from git on:   2011-12-21 15:55:36


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Searching sda13 for information... 
Searching sda14 for information... 
Searching sda15 for information... 
Searching sda16 for information... 
Searching sda17 for information... 
Searching sda18 for information... 
Searching sda19 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 

Finished. The results are in the file "RESULTS2.txt"
located in "/home/lance/".

```

Which results in:

[ATTACH]209503[/ATTACH]

I'll check Precise ASAP but I must first check some stock tank heaters (animals need water) and I'll check back here first to see if I'm even thinking along the right lines :)

Oops :rolleyes:

Those results showed Precise on sda15 still in charge, which it was, so here's my stable Oneiric on sda1 in charge:

[ATTACH]209507[/ATTACH]

---

### Post by Gert Hulselmans on 2011-12-21
> **VMC said:**
> @Gert,

Just installing lzma fixed my issue, thanks.

I'm unsure if Lucid and Mint12 have lzma installed. I'll check.

edit: now that I think about it, I ran bis on all three OS's, Fedora, Lucid, Mint12. All had the same "??" issue. What changed, and when was lzma added?
unlzma was added to support grub v1.99.

The test version I attached uses xz now.
Can you uninstall unlzma again to test (or try on another distro that failed for you)?

If anybody else can test it is fine too.
I don't have grub v1.99 installed here.

---

### Post by kansasnoob on 2011-12-21
Precise mawk:

```
lance@lance-desktop:~$ mawk -W version
mawk 1.3.3 Nov 1996, Copyright (C) Michael D. Brennan

compiled limits:
max NF             32767
sprintf buffer      1020

```

So I guess still borked.

---

### Post by kansasnoob on 2011-12-21
Still in Precise:

```
lance@lance-desktop:~$ which unlzma
/usr/bin/unlzma
lance@lance-desktop:~$ which lzma
/usr/bin/lzma
lance@lance-desktop:~$ which 7z
lance@lance-desktop:~$ which xz
/usr/bin/xz

```

And now I'm kind of lost :confused:

---

### Post by Gert Hulselmans on 2011-12-21
> **kansasnoob said:**
> And now I'm kind of lost :confused:
So for Precise, it doesn't matter what BIS uses (unlzma or xz).

Did you try the attached test version (uses xz instead of unlzma) already?
It should give exactly the same output than the git version (uses unlzma).

Yes, mawk will be very likely to be still borked. I don't get it why they don't update it.

---

### Post by VMC on 2011-12-21
> **Gert Hulselmans said:**
> unlzma was added to support grub v1.99.

The test version I attached uses xz now.
Can you uninstall unlzma again to test (or try on another distro that failed for you)?

If anybody else can test it is fine too.
I don't have grub v1.99 installed here.

I uninstalled lzma, and used the test version and it works. Great!

>                    Boot Info Script 0.60      [17 May 2011]

Last git commit:       a63e662 README: Update "Usage" section. (use xz instead of lzma)
Retrieved from git on: 2011-12-21 14:53:34


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub2 on this drive.


---

### Post by Gert Hulselmans on 2011-12-21
> **VMC said:**
> I uninstalled lzma, and used the test version and it works. Great!
:D A cleaner patch will be applied to the git version (can use xz or unlzma).

---

### Post by kansasnoob on 2011-12-22
> **Gert Hulselmans said:**
> So for Precise, it doesn't matter what BIS uses (unlzma or xz).

Did you try the attached test version (uses xz instead of unlzma) already?
It should give exactly the same output than the git version (uses unlzma).

Yes, mawk will be very likely to be still borked. I don't get it why they don't update it.

I reran the git version and the test version from post #26 in Precise again and the diff -u is unremarkable:

```
--- git_RESULTS.txt	2011-12-22 01:12:14.628489176 -0600
+++ bis_test_26_RESULTS.txt	2011-12-22 01:04:53.848492271 -0600
@@ -1,5 +1,8 @@
                    Boot Info Script 0.60      [17 May 2011]
 
+Last git commit:       a63e662 README: Update "Usage" section. (use xz instead of lzma)
+Retrieved from git on: 2011-12-21 14:53:34
+
 
 ============================= Boot Info Summary: ===============================
 
@@ -5715,8 +5718,8 @@
 
 =============================== StdErr Messages: ===============================
 
-unlzma: (stdin): Compressed data is corrupt
-unlzma: (stdin): Compressed data is corrupt
+xz: (stdin): Compressed data is corrupt
+xz: (stdin): Compressed data is corrupt
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
@@ -5765,7 +5768,7 @@
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
-unlzma: (stdin): Compressed data is corrupt
+xz: (stdin): Compressed data is corrupt
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
@@ -5781,7 +5784,7 @@
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
-unlzma: (stdin): Compressed data is corrupt
+xz: (stdin): Compressed data is corrupt
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
@@ -5810,7 +5813,7 @@
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
-unlzma: (stdin): Compressed data is corrupt
+xz: (stdin): Compressed data is corrupt
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
 awk: cmd. line:36: Math support is not compiled in
```

I'm attaching the full results in case they're helpful:

[ATTACH]209536[/ATTACH]

---

### Post by Gert Hulselmans on 2011-12-22
@ kansasnoob
Can you check if, when you uninstall unlzma and run the git version, if you see this line in your RESULTS.txt?
```
=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".

```

---

### Post by kansasnoob on 2011-12-22
> **Gert Hulselmans said:**
> @ kansasnoob
Can you check if, when you uninstall unlzma and run the git version, if you see this line in your RESULTS.txt?
```
=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".

```

In both Precise and Oneiric I can't find the package 'unlzma', but in Oneiric I see this:

```
lance@lance-desktop:~$ which unlzma
/usr/bin/unlzma

```

What am I doing wrong?

Sorry to be inept :confused:

---

### Post by Gert Hulselmans on 2011-12-22
The package name is probably **lzma**.

---

### Post by kansasnoob on 2011-12-22
> **Gert Hulselmans said:**
> The package name is probably **lzma**.

In my stable Oneiric it's not installed anyway:

[ATTACH]209542[/ATTACH]

But I wonder if I need to purge any config files?

---

### Post by Gert Hulselmans on 2011-12-22
> **kansasnoob said:**
> In my stable Oneiric it's not installed anyway:

[ATTACH]209542[/ATTACH]

But I wonder if I need to purge any config files?
The xz-lzma package will probably contain unlzma.

---

### Post by kansasnoob on 2011-12-22
> **Gert Hulselmans said:**
> The xz-lzma package will probably contain unlzma.

Even that is not installed by default in Oneiric but I was surprised that 'file-roller' seems to support xz and lzma:

[ATTACH]209550[/ATTACH]

BTW all three of those packages are installed in Oneiric by default.

---

### Post by Gert Hulselmans on 2011-12-26
@ VMC
Can you try the attached version?
I think this should display the unlzma error in the RESULTS.txt file.

---

### Post by VMC on 2011-12-26
> **Gert Hulselmans said:**
> @ VMC
Can you try the attached version?
I think this should display the unlzma error in the RESULTS.txt file.

This is my results using Fedora without unlzma:
> $ sudo ./bootinfoscript_stderr
Boot Info Script 0.60      [17 May 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/vmc/".


> ============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
.
.
.
=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".
  No volume groups found
mdadm: No arrays found in config file or automatically


---

### Post by Gert Hulselmans on 2011-12-26
@ VMC
The attached version should display the error now, when xz and lzma are not available.

@ all
Please test the attached version.

It will try to use xz first and if not found lzma (not unlzma anymore) so I hope it still works.
Test with:

[LIST]
[*] xz and lzma not installed
[*] lzma installed
[*] xz installed
[/LIST]

---

### Post by kansasnoob on 2011-12-27
> **Gert Hulselmans said:**
> @ VMC
The attached version should display the error now, when xz and lzma are not available.

@ all
Please test the attached version.

It will try to use xz first and if not found lzma (not unlzma anymore) so I hope it still works.
Test with:

[LIST]
[*] xz and lzma not installed
[*] lzma installed
[*] xz installed
[/LIST]

I'm beginning in Oneiric, remember what I noted previously about 'file-roller', but assuming you mean those instructions by file name:

```
lance@lance-desktop:~$ sudo apt-get purge xz lzma
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xz
lance@lance-desktop:~$ sudo apt-get purge lzma
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lzma*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 172 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 191060 files and directories currently installed.)
Removing lzma ...
Processing triggers for man-db ...

```

I'll now start some BIS testing, but please clarify if I'm doing something wrong.

---

### Post by Gert Hulselmans on 2011-12-27
> **kansasnoob said:**
> I'll now start some BIS testing, but please clarify if I'm doing something wrong.
I think not, but to be sure check if:
[HTML]which xz
which lzma[/HTML]
give some output. If nothing is shown, both tools are uninstalled.

---

### Post by kansasnoob on 2011-12-27
It appears to me that some 'xz' exists:

```
lance@lance-desktop:~$ which xz
/usr/bin/xz
lance@lance-desktop:~$ which lzma

```

Regardless I ran the new test BIS, first the terrminal output:

```
lance@lance-desktop:~/Desktop$ sudo bash bootinfoscript_xz_lzma

Boot Info Script 0.60      [17 May 2011]
  Last git commit:         Use lzma or xz for decompression of lzma streams.
  Retrieved from git on:   


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Searching sda13 for information... 
Searching sda14 for information... 
Searching sda15 for information... 
Searching sda16 for information... 
Searching sda17 for information... 
Searching sda18 for information... 
Searching sda19 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/lance/Desktop/".

```

And of course the results:

[ATTACH]209764[/ATTACH]

I'm thinking out-loud here but what if we began testing by installing both xz and lzma, then purging both, eg:

```
sudo apt-get install xz lzma
```

```
sudo apt-get purge xz lzma
```

Like I said, just thinking out-loud :)

Give me just a bit of time to try some stuff.

---

### Post by Gert Hulselmans on 2011-12-27
OK, that output looks OK.

Try to uninstall xz. The following command should list all packages related to **xz**:
```
apt-cache search xz
```

---

### Post by kansasnoob on 2011-12-27
Just getting up to speed here :oops:

It appears that we need to begin with:

```
sudo apt-get purge xz-utils lzma
```

Give me just a bit more time :)

---

### Post by kansasnoob on 2011-12-27
Actually it appears that removing xz is not an option:

[ATTACH]209766[/ATTACH]

```
lance@lance-desktop:~$ sudo apt-get purge xz-utils
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 base-files : PreDepends: awk
 libasound2 : PreDepends: multiarch-support but it is not going to be installed
              PreDepends: dpkg (>= 1.15.7.2) but it is not going to be installed
 libc6 : Depends: libgcc1 but it is not going to be installed
         Depends: tzdata but it is not going to be installed
 openjdk-6-jre : Depends: libjpeg62 (>= 6b1)
                 Depends: libpng12-0 (>= 1.2.13-4) but it is not going to be installed
                 Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
                 Depends: libx11-6 but it is not going to be installed
                 Depends: libxext6 but it is not going to be installed
                 Depends: libxi6 but it is not going to be installed
                 Depends: libxrender1 but it is not going to be installed
                 Depends: libxtst6 but it is not going to be installed
                 Depends: libaccess-bridge-java-jni but it is not going to be installed
                 Recommends: icedtea-netx but it is not going to be installed
 openjdk-6-jre-headless : Depends: openjdk-6-jre-lib (>= 6b23~pre11-0ubuntu1.11.10) but it is not going to be installed
                          Depends: ca-certificates-java but it is not going to be installed
                          Depends: tzdata-java but it is not going to be installed
                          Depends: libcups2 but it is not going to be installed
                          Depends: liblcms1 but it is not going to be installed
                          Depends: libjpeg62
                          Depends: libnss3-1d (>= 3.12.9+ckbi-1.82-0ubuntu4) but it is not going to be installed
                          Depends: libfreetype6 (>= 2.2.1) but it is not going to be installed
                          Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
                          Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
                          Depends: zlib1g (>= 1:1.1.4) but it is not going to be installed
                          Recommends: icedtea-6-jre-cacao (= 6b23~pre11-0ubuntu1.11.10) but it is not going to be installed
                          Recommends: icedtea-6-jre-jamvm (= 6b23~pre11-0ubuntu1.11.10) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

Give me more time :D

---

### Post by kansasnoob on 2011-12-27
Oops, left out the most important part:

```
lance@lance-desktop:~$ apt-cache search xz
devscripts - scripts to make the life of a Debian Package maintainer easier
liblzma-dev - XZ-format compression library - development files
liblzma-doc - XZ-format compression library - API documentation
liblzma2 - XZ-format compression library
xz-utils - XZ-format compression utilities
makexvpics - updates .xvpics thumbnails from the command line
p7zip-full - 7z and 7za file archivers with high compression ratio
python-lzma - Python bindings for liblzma
python-lzma-dbg - python-lzma debug symbols
python-txzookeeper - Twisted-based Asynchronous Libraries for Apache Zookeeper.
xz-lzma - XZ-format compression utilities - compatibility commands
xzdec - XZ-format compression utilities - tiny decompressors
xzgv - Picture viewer for X with a thumbnail-based selector
xzip - Interpreter of Infocom-format story-files
xzoom - magnify part of X display, with real-time updates
zutils - utilities for dealing with compressed files transparently
zutils-dbg - utilities for dealing with compressed files transparently (debug)
**[COLOR="Red"]file-roller[/COLOR]** - an archive manager for GNOME

```

I'd think that would result in major borkage.

---

### Post by Gert Hulselmans on 2011-12-27
If you feel comfortable with it, you can temporarily move the xz binary before executing BIS:
```
sudo mv -v /usr/bin/xz /usr/bin/xz-old
```After running the script, move the binary back:
```
sudo mv -v /usr/bin/xz-old /usr/bin/xz
```

---

### Post by kansasnoob on 2011-12-28
Sorry for the long delay, I got called away unexpectedly. When I started the computer up again I decided to begin with Lucid which is just the opposite:

```
lance@lance-desktop:~$ which xz
lance@lance-desktop:~$ which lzma
/usr/bin/lzma

```

Terminal output running the BIS:

```
lance@lance-desktop:~$ sudo bash bootinfoscript_xz_lzma
[sudo] password for lance: 

Boot Info Script 0.60      [17 May 2011]
  Last git commit:         Use lzma or xz for decompression of lzma streams.
  Retrieved from git on:   

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Searching sda13 for information... 
Searching sda14 for information... 
Searching sda15 for information... 
Searching sda16 for information... 
Searching sda17 for information... 
Searching sda18 for information... 
Searching sda19 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 

Finished. The results are in the file "RESULTS2.txt"
located in "/home/lance/".

```

And the results themselves:

[ATTACH]209809[/ATTACH]

I have some other test installs on this machine so I'll pick one for further testing :)

---

### Post by Gert Hulselmans on 2011-12-28
This output looks OK too.
I now just need one sample without lzma and xz.

---

### Post by kansasnoob on 2011-12-28
Not surprisingly Precise has both:

```
lance@lance-desktop:~$ which xz
/usr/bin/xz
lance@lance-desktop:~$ which lzma
/usr/bin/lzma

```

Just give me a bit to figure out what I want to do there. Not that I don't trust you, but I just do things a bit differently :)

Just for fun, although not asked for, here's the results in Precise with both xz and lzma:

[ATTACH]209811[/ATTACH]

---

### Post by kansasnoob on 2011-12-28
What I did:

```
lance@lance-desktop:~$ sudo mv -v /usr/bin/xz /usr/bin/xz_OLD
[sudo] password for lance: 
`/usr/bin/xz' -> `/usr/bin/xz_OLD'
lance@lance-desktop:~$ sudo chmod -x /usr/bin/xz_OLD
lance@lance-desktop:~$ sudo mv -v /usr/bin/lzma /usr/bin/lzma_OLD
`/usr/bin/lzma' -> `/usr/bin/lzma_OLD'
lance@lance-desktop:~$ sudo chmod -x /usr/bin/lzma_OLD
chmod: cannot operate on dangling symlink `/usr/bin/lzma_OLD'
lance@lance-desktop:~$ which xz
lance@lance-desktop:~$ which lxma
```

Not sure what to think about the "dangling symlink" warning but you can see that both "which" commands show nothing so:

```
lance@lance-desktop:~$ sudo bash bootinfoscript_xz_lzma

Boot Info Script 0.60      [17 May 2011]
  Last git commit:         Use lzma or xz for decompression of lzma streams.
  Retrieved from git on:   


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Searching sda13 for information... 
Searching sda14 for information... 
Searching sda15 for information... 
Searching sda16 for information... 
Searching sda17 for information... 
Searching sda18 for information... 
Searching sda19 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 

Finished. The results are in the file "RESULTS1.txt"
located in "/home/lance/".

```

The results show an obvious problem:

[ATTACH]209813[/ATTACH]

The obvious problem is:

>  => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for **[COLOR="Red"]??[/COLOR]** on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 18 for [COLOR="Red"]**??**[/COLOR].


This is just a testing OS so breakage is not a problem :)

---

### Post by kansasnoob on 2011-12-28
Still not sure about that symlink error but I seem to have things back:

```
lance@lance-desktop:~$ sudo mv -v /usr/bin/xz_OLD /usr/bin/xz
[sudo] password for lance: 
`/usr/bin/xz_OLD' -> `/usr/bin/xz'
lance@lance-desktop:~$ sudo chmod +x /usr/bin/xz
lance@lance-desktop:~$ sudo mv -v /usr/bin/lzma_OLD /usr/bin/lzma
`/usr/bin/lzma_OLD' -> `/usr/bin/lzma'
lance@lance-desktop:~$ sudo chmod +x /usr/bin/lzma
```

```
lance@lance-desktop:~$ which xz
/usr/bin/xz
lance@lance-desktop:~$ which lzma
/usr/bin/lzma

```

Just thinking we need a consistent testing plan :)

---

### Post by Gert Hulselmans on 2011-12-28
> **kansasnoob said:**
> 
The obvious problem is:
> => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for **[COLOR=Red]??[/COLOR]** on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 18 for [COLOR=Red]**??**[/COLOR]. 			 		


That is normal. I was only interested to see the following line in the StdErr Message part:
```

=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "xz" or "lzma".
```
Thanks for testing. For now I don't need further tests.

---

### Post by oldfred on 2011-12-29
Jake42 posted results from an efi boot. I reposted it in post #9. It looks like it finds the efi files fine.

[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

---

