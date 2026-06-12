---
title: "Help"
date: 2018-01-20
forum: Server Platforms
---

### Post by sam13764 on 2018-01-20
I am a new ubuntu user who is trying to build a Plex Media server. I formated my hard drive as ntfs and for some reason it unmounted randomly and now it wont re-mount and it keeps giving me this error message: ```
Error mounting system-managed device /dev/sdb1: Command-line `mount "/home/sam/films"' exited with non-zero exit status 13: ntfs_mst_post_read_fixup_warn: magic: 0x52d97f6e  size: 1024   usa_ofs: 39977  usa_count: 57879: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xb807ad31  size: 1024   usa_ofs: 52905  usa_count: 25503: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x5ae72630  size: 1024   usa_ofs: 7105  usa_count: 62162: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x8c1df931  size: 1024   usa_ofs: 49289  usa_count: 13469: Invalid argument
$MFTMirr error: Invalid mft record for '$MFT'.
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
 (udisks-error-quark, 0)
```

---

### Post by slickymaster on 2018-01-20
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2018-01-20
If you are trying to build a linux server why do you format the disk as ntfs?

---

### Post by mastablasta on 2018-01-22
this first:
> In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very important 

also, really why NTFS? are you moving films form windows to Ubuntu server?

NTFS will work OK as storage partition (i use it on Openelec/Kodi), just know that you need windows OS and windows tools (such as chkdsk) to maintain it.

---

### Post by LHammonds on 2018-01-22
FYI - You can use ext4 for all your Linux partitions and if you share a folder using Samba to Windows PCs, they can connect just fine.

NTFS shouldn't be needed for anything on a Linux server.

With that said, I have no experience troubleshooting NTFS partition issues since I've never used them on Linux (even though most of my other servers are Windows and ALL of my PCs are Windows 10/7)...but it does seem like there might be an issue with the physical drive itself.

LHammonds

---

