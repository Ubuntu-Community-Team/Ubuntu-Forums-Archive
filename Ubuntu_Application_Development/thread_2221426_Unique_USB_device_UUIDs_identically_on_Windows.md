---
title: "Unique USB device UUIDs identically on Windows"
date: 2014-05-02
forum: Ubuntu Application Development
---

### Post by Cosmin_Popescu on 2014-05-02
Hi there guys,

I'm a newbie, so pls be patient with me.

I have a big problem on developing an app on Ubuntu. This app has to be able to control plugged-in usb devices, and do more stuff with them. 
For now I'm stuck with a problem. I have to be able to sort a way to obtain an usb-device unique id (no matter if upon a formatting step this id changes, but it has to be really unique on a certain let's say, usb flash device) on Ubuntu AND (THIS IS THE INTERESTING PART) to be able to obtain (somehow, don't know how yet) the same id number on Windows. 

I have already made it obtaining unique IDs on Ubuntu and Windows but separately (on Ubuntu using blkid command and parsing it's results) and on Windows using some API call that is able to deliver me an unique (until-next-format) id BUT THOSE TOO ids ARE DIFFERENT.

I'm not confined to using API calls of something like that. If you guys are proposing a low-level logic solution I'm very ok with that.

Thanks in advance !

---

### Post by sudodus on 2014-05-03
Welcome to the Ubuntu Forums :-)

I think the best identifier of a partition is the UUID, as seen with the linux command

```
sudo blkid
```

I'm not sure how it is seen by Windows, or if it works the same way with FAT32 and NTFS.

-o-

If you want an identifier of the whole USB device, (not only partitions) you need something else. You can see USB devices with the linux command

```
lsusb
```

---

### Post by sudodus on 2014-05-03
I checked in an old Windows XP (off-line of course, since it has passed end of life)


Linux:
```
[COLOR=#0000ff]sudo blkid[/COLOR]
[sudo] password for sudodus: 
/dev/sda1: LABEL="windows" UUID="D40C9321[COLOR=#ff0000]0C92FDA4[/COLOR]" TYPE="ntfs" 
/dev/sda5: UUID="e0900111-8221-4f7c-b337-f227d0a90ff5" TYPE="swap" 
/dev/sda6: LABEL="lubuntu" UUID="33e5d353-af97-488d-86f0-4d9c54b7542a" TYPE="ext4" 
/dev/sda7: LABEL="data" UUID="4D2303A0[COLOR=#006400]08731FD1[/COLOR]" TYPE="ntfs" 

```[COLOR=#0000ff]
[/COLOR]
Windows:
```

vol c: > vol_c
vol d: > vol_d

```[COLOR=#0000ff]

[/COLOR]and checking (in Linux)

```
[COLOR=#0000ff]
cat /media/data/vol*[/COLOR]
 Volymen i enhet C har etiketten windows
 Volymens serienummer är [COLOR=#ff0000]0C92-FDA4[/COLOR]
 Volymen i enhet D har etiketten data
 Volymens serienummer är [COLOR=#006400]0873-1FD1[/COLOR]
```

You can identify the last eight hexadecimal digits of the UUID of the NTFS partition with the output of the MSDOS command ***vol***, as is indicated by the [COLOR=#ff0000]red[/COLOR] and [COLOR=#006400]green[/COLOR] high-lights.

See also this link (particularly post #11)
[URL="http://ubuntuforums.org/showthread.php?t=869801"]
Changing the UUID to ntfs partition[/URL]

---

