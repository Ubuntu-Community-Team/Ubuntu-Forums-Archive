---
title: "Executable On Windows Partition Will Not Execute"
date: 2011-06-14
forum: Wine
---

### Post by amtur_poet on 2011-06-14
I have been trying to get an program that is installed on my Windows partition to run in Wine, but I am having trouble with the permissions on the .exe file. When I go into the file's properties under the Permissions tab and select "Allow executing file as program", the check box immediately deselects itself. I cannot get it to become executable. I tried running ```
sudo chmod a+x
``` on the file in its directory, but that didn't work, either. What can I do to get this to work in Wine?

---

### Post by sanderj on 2011-06-15
I don't think you need to have the x-bit on on the file you want to 'wine'. Just run 'wine <...>'

I don't know whether you can set the rwx-bits on a mounted NTFS drive.

---

### Post by vincentertainment on 2011-07-19
I'd been having same problem. Most of my Windows exe files are on my windows hard drive (naturally). Couldn't understand why I couldn't change permission to executable.
After copying exe files to my Linux drive, it lets me change permission to executable and run in Wine.
Hope this helps others too.

---

### Post by Morbius1 on 2011-07-19
Cautious-launcher. It's a little script that insists on checking if a *.exe file has a linux executable bit set. Does Wine require an exe to have a linux executable bit set - No. Wine doesn't care. Wine doesn't even know what a linux executable bit is.

Here's three ways to fix this problem: [http://ubuntuforums.org/showthread.php?t=1747138](http://ubuntuforums.org/showthread.php?t=1747138)

---

### Post by Soulcage on 2011-07-20
Give this a read [http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2]("http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2")

---

