---
title: "At long last, a working extent-friendly ext4 driver for Windows."
date: 2010-10-18
forum: The Cafe
---

### Post by Starks on 2010-10-18
[Ext2fsd-0.48-bb8]("http://www.acc.umu.se/%7Ebosse/ext2fsd-0.48-bb8.zip") (Support for ext4 extents and fix for BSOD on Windows 7.)

My Windows 7 partition suddenly became more valuable.

Be sure to follow the readme.

---

### Post by Starks on 2010-10-19
Really? Nobody cares?

---

### Post by blueturtl on 2010-10-19
I actually consider it safer for Windows to remain oblivious to any other operating systems on the same hard-drive or machine. That way you can be sure nothing bad that happens in Windows can ever touch your Linux install.

---

### Post by miggols99 on 2010-10-19
> **blueturtl said:**
> I actually consider it safer for Windows to remain oblivious to any other operating systems on the same hard-drive or machine. That way you can be sure nothing bad that happens in Windows can ever touch your Linux install.
+1

I really hate it when Windows creates those thumb.db files everywhere! That's why I don't like Windows getting access to Linux...

---

### Post by MooseDog on 2010-10-19
thx for sharing link, i'll look into it!

i have to agree, certainky makes windows more useful, a little bit at least.  

agree also that giving windows knowledge about anything else but itself is a threat to others (lord knows win has a hard enough time dealing with its own problems), but i've solved that by always putting the two installs on two different drives, never! on one single one.

---

### Post by Lucradia on 2010-10-19
> **miggols99 said:**
> +1

i really hate it when windows creates those thumb.db files everywhere! That's why i don't like windows getting access to linux...

qft

---

### Post by zekopeko on 2010-10-19
> **miggols99 said:**
> +1

I really hate it when Windows creates those thumb.db files everywhere! That's why I don't like Windows getting access to Linux...

[http://www.tweakxp.com/article36702.aspx](http://www.tweakxp.com/article36702.aspx)

Easy fix.

---

### Post by CarpKing on 2010-10-19
Interesting.  I was wondering when something like this would come about.  Last I heard, the ext3 driver worked by pretending the partition was ext2, which never seemed like the safest proposition.  

On my desktop I have my shared partition as ext3 because when I set it up ntfs write support was shaky, but I was thinking about moving it to ntfs sometime just so I wasn't depending on ext2fs.  That's how I have my laptop set up.  

Is there a btrfs driver for windows in the works? :3

---

### Post by CharlesA on 2010-10-19
Got a homepage instead of just a download link?

---

### Post by Lucradia on 2010-10-19
> **zekopeko said:**
> [http://www.tweakxp.com/article36702.aspx](http://www.tweakxp.com/article36702.aspx)

Easy fix.

Windows 7: gpedit.msc doesn't exist; nor does Control Panel > Folder Options > View > "Do not cache thumbnails"

As Windows Vista and higher force you to turn off thumbnails in order not to cache them.

---

### Post by CharlesA on 2010-10-19
> **Lucradia said:**
> Windows 7: gpedit.msc doesn't exist; nor does Control Panel > Folder Options > View > "Do not cache thumbnails"

As Windows Vista and higher force you to turn off thumbnails in order not to cache them.

Are you using Home Premium? I've got gpedit.msc on my Win7 Pro and Ultimate installs.

However, I don't see anything under folder options.

---

### Post by Lucradia on 2010-10-19
> **CharlesA said:**
> Are you using Home Premium?

Which is what most pre-built computers, like mine, come with; yes, I am.

---

### Post by Ctrl-Alt-F1 on 2010-10-20
As a few others have stated, I prefer that Windows can't read my Linux file system.  I don't mind Linux reading my Windows file systems because I trust Linux not to do anything stupid inadvertently.

---

### Post by the8thstar on 2010-10-20
It's good news for people who switch often from one OS to the other on the same computer.

Personally I share the general feeling of *not* wanting to use the ext4 reader because I don't want to risk harming my main system (Ubuntu) while working in a more exposed environment that is more susceptible to attacks because of the sheer number of people using it (Windows).

---

### Post by Starks on 2010-10-20
> **CharlesA said:**
> Got a homepage instead of just a download link?
[http://www.acc.umu.se/~bosse/]("http://www.acc.umu.se/%7Ebosse/")

---

### Post by julio_cortez on 2010-10-20
> **miggols99 said:**
> I really hate it when Windows creates those thumb.db files everywhere! That's why I don't like Windows getting access to Linux...You're talking about XP, aren't you? I think it doesn't happen anymore with Windows 7.

By the way, I have the exactly opposite problem: Ubuntu leaves behind those .trash folders in my shared NTFS volume (Data) each time I delete a file, and I have to manually remove them when I boot into Windows.
*Not only I wouldn't ever let Windows access an ext4 partition, but I would only let Ubuntu access a NTFS partition which is not a system one. I won't mount my XP or my 7 partition in Ubuntu..*

---

### Post by CharlesA on 2010-10-20
> **Starks said:**
> [http://www.acc.umu.se/~bosse/]("http://www.acc.umu.se/%7Ebosse/")

Thanks. :)

> **julio_cortez said:**
> You're talking about XP, aren't you? I think it doesn't happen anymore with Windows 7.

I think Win7 still does it, but the only option you have is to "turn off thumbnails completely" if you have the Home Premium version, since that version doesn't have access to gpedit.msc.

EDIT: You can add a registry entry to prevent the creation of the thumbs.db files:

```
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]
"DisableThumbnailCache"=dword:00000001
```

Tested it and it works. [Source]("http://superuser.com/questions/2345/how-can-i-suppress-those-annoying-thumbs-db-files-in-windows-vista-and-windows-7").

---

### Post by swoll1980 on 2010-10-20
I can never get the ext2 driver to work. Explorer always wants me to format my Linux drives when I try to access them. I could never figure out why. It obviously thinks they are empty, and unformatted. Thanks for the link though it was worth another try.

---

### Post by Jose Catre-Vandis on 2010-10-20
I use a shared partition formatted to ntfs. Works well and has been so for the last 12 months. This doesn't give W7 access to my linux filesystem (whereas as linux can see the W7 partition natively), but means I can access "working" files when in either OS seamlessly. Not noticed too much of a problem with thumb files though?

---

### Post by CharlesA on 2010-10-20
> **Jose Catre-Vandis said:**
> I use a shared partition formatted to ntfs. Works well and has been so for the last 12 months. This doesn't give W7 access to my linux filesystem (whereas as linux can see the W7 partition natively), but means I can access "working" files when in either OS seamlessly. Not noticed too much of a problem with thumb files though?

If I am dualbooting, that's what I do as well. Either that or just sftp stuff to/from my server, since I store most of my stuff there.

I haven't noticed a huge "problem" with Thumbs.db files either, I even did a search on my file server for them and it only found a handful of them. The files themselves are tiny, so it's not a huge deal for me.

---

### Post by varmeh on 2010-11-07
> **Starks said:**
> [Ext2fsd-0.48-bb8]("http://www.acc.umu.se/%7Ebosse/ext2fsd-0.48-bb8.zip") (Support for ext4 extents and fix for BSOD on Windows 7.)

My Windows 7 partition suddenly became more valuable.

Be sure to follow the readme.

would this work for win server 2008 r2?  or WHSv2 "vail"?

and how does it compare to:

[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

thanks for the input.  my situation is that i have a huge amount of data (for me anyway, about 1.2 TB) on an ext4 partition that i'd like to slide over to NTFS.

---

### Post by babygenius55 on 2012-07-17
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

do it. do it now.

---

### Post by sffvba[e0rt on 2012-07-17
*Back to sleep **old **thread.*


404

---

