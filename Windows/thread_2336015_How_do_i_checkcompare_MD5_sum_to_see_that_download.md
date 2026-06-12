---
title: "How do i check/compare MD5 sum to see that download is correct?"
date: 2016-09-03
forum: Windows
---

### Post by patrikmellq on 2016-09-03
How do i check/compare MD5 sum to see that download is correct?

I understand that i can read from site what kind of MD5 sum the download has.
But when i have done the download, how do i check the MD5 sum is correct with my download, where to look and how do i know no one have tempered with my download, i reckon that is the reason you use MD5 sum to check that the download is Clean and valid.

Many Thanks

Cheers

---

### Post by &amp;KyT$0P# on 2016-09-03
```
openssl dgst -md5 <downloaded_file>
```

---

### Post by SeijiSensei on 2016-09-03
From the command prompt:

```
$ md5sum < /path/to/downloaded/file
4c978aa22f0bfd399686b166e1b13cce  -

```
Ignore the hyphen.  The MD5 hash of this file is "4c978aa22f0bfd399686b166e1b13cce".

---

### Post by TheFu on 2016-09-03
Open a terminal in the download directory.
Run the tool used by the guy publishing the download.... that could be md5sum, sha1sum, sha256sum ... with the download filename as the input.

For example, I grabbed a copy of RemixOS (android for x86)
```
$ md5sum ./Remix_OS_for_PC_Android_M_64bit_B2016083002.iso
1bee3eacbc569dcb6e62b1ff6a6c3ee4  Remix_OS_for_PC_Android_M_64bit_B2016083002.iso
```
The other tools work in a similar way.

Then look at the output AND what the download page claims as the correct output. Do they match?

---

### Post by howefield on 2016-09-03
Another method..

```
echo "md5sum path/to/file" | md5sum -c -
```


Example :
```
hugh@xenial-laptop:~$  echo "00c1b197578337456930269ed4d12297 /home/hugh/Downloads/opera-stable_39.0.2256.48_amd64.deb" | md5sum -c -
/home/hugh/Downloads/opera-stable_39.0.2256.48_amd64.deb: OK
hugh@xenial-laptop:~$ 
```

---

### Post by patrikmellq on 2016-09-04
Thanks for the help - but i am going to convert from windows 10 to Ubuntu LTS - so i need to check that the MD5 sum is correct with my windows 10 operativ.
How do i do that? can i download a software who check that or use a specific web browser that check that ...

Many Thanks

---

### Post by TheFu on 2016-09-04
Many Unix tools have been ported to Windows.  That is really a Windows question. Use google?

Or download the ISO, burn it to a CD/DVD, boot off that "live boot" media, then run md5sum against the ISO used to create the boot-able DVD.
Also, on the first page for the live-boot media, there is an option to verify the media - that will do the same check. It is after the fact, but does work.

And you don't have to use optical media. USB flash drives usually work too.  For that, use a tool like Yumi (on Windows [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/) ) to create a multi-boot Flash drive. It will wipe everything off the flash drive the first time, so be prepared for that.  It is easy to have 15+ distros on a single 16G flash drive this way.  It is good to try before you commit to a distro.  I think all of the major distros have the "verify" option on their first screen.

---

### Post by howefield on 2016-09-04
Thread moved to the "*Windows*" forum.

CertUtil seems to work quite well.

```
if ( $($(CertUtil -hashfile path\to\file MD5)[1] -replace " ","") -eq "place\hashsum\here" ) { echo "ok" }
```

Example : 
```
PS C:\Users\Hugh\Downloads> if ( $($(CertUtil -hashfile C:\Users\Hugh\Downloads\opera-stable_39.0.2256.48_amd64.deb MD5)
[1] -replace " ","") -eq "00c1b197578337456930269ed4d12297" ) { echo "ok" }
ok
```

No output if hashsum doesn't match.

---

### Post by &amp;KyT$0P# on 2016-09-04
There's [HashMyFiles]("http://www.nirsoft.net/utils/hash_my_files.html"), which is a GUI program, maybe useful if you rather not like command line on Windows.

---

### Post by SeijiSensei on 2016-09-04
If you're worried about the integrity of the installation image, use a [torrent]("http://releases.ubuntu.com/16.04/ubuntu-16.04-desktop-amd64.iso.torrent") client.  Every chunk of a torrent is hashed and checked for integrity during transmission. If a chunk fails the check, it is downloaded again.

---

