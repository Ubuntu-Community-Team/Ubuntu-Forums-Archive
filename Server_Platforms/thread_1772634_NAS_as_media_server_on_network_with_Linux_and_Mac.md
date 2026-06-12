---
title: "NAS as media server on network with Linux and Mac"
date: 2011-05-31
forum: Server Platforms
---

### Post by GROwen on 2011-05-31
Hi all, 

I've got a D-Link DNS-313 NAS that I'm trying to figure out how I can incorporate it into a home network as a media server.

The DNS 313 has a few quirks to it's file systems that are  making me consider replacing it with something else. It has a small ext2  file partition for running firmware but the actual partition that's  accessed can only be NTFS - without a bit of hacking. 
 
 Hacked I can swap partitions so that the main storage partition is ext2  but I don't know if it's worth it considering a Mac will be saving  photos/videos etc to it.

If I'm using Linux and Mac software to manage the media on the NAS what  file system would suit best? Or am I'm trying creating a headache for  myself.

My current setup (which came together over a long period of time and  therefore I don't feel is best utilising equipment) includes;

**DNS 313 500GB**

[LIST]
[*]backup device for laptop
[/LIST]
 **Old PC running Ubuntu 11.04 250GB and 1TB;**

[LIST]
[*]HTPC
[*]music server (only via SMB share)
[/LIST]
 **Mac running OS X 10.4**

[LIST]
[*]basically using as a netbook with media management (ie iPhoto)
[/LIST]
 
**My current concept is to use them in the following ways;**

**DNS 313 with 1TB drive**

[LIST]
[*]MediaTomb for serving media
[*]mythTV storage directores (saving recorded programs etc.)
[/LIST]
 **Ubuntu 11.04 setup with 250GB and 500GB drives;**

[LIST]
[*]HTPC, uPnP client
[*]mythTV backend with it's storage directories being on the NAS
[*]mythTV frontend
[*]XBMC and mythBox plugin
[*]media manager (importing photos/home video using either) for media server
[*]backup for important files from DNS 313
[/LIST]
 **Mac; **

[LIST]
[*]netbook
[*]uPnP client
[*]media manager (importing photos/video using either iPhoto or Picasa) for server
[/LIST]
 I've had troubles in the past where the Apple HFS wasn't able to be  backed up correctly because of the limitations in naming of NTFS. Will I  come across problems like this using programs from an ext3 FS (Ubuntu)  and the Mac when serving the media from the NAS?

Thanks in advance for any advice that can be offered.

---

### Post by doas777 on 2011-05-31
It depends on the protocols you will be using to access the data. I don't have any mac's but I use ext3 on my nas (a synology; linux 2.6.x based) and use Samba to access files. Samba acts as an intermediary, so that my windows boxes never notice that the filesystem is non-native. I also use the synology web manager for administration and organizing files (faster copy between drives if I don't have to do it over samba.) if you have hacked the kernel to run off ext2, it should hide the exact filesystem semantics from whatever application calls it, but it does depend on how you hacked it. if a given protocols application uses a filesystem access method not covered by your hack, it won't work.

I know macs have to have a solid smb client by now (the one I last used was a CIFS client for Mac OS 8.4, and was a little flaky), so samba ought to work fine.

---

### Post by GROwen on 2011-05-31
Thanks for the quick reply, helps me to make sense of what Samba actually is and gives me enough incentive to just go ahead and format to ext2/3 to see how it works.

Samba has been working great between the Ubuntu machine and the Mac for serving music to iTunes is that scenario very different from using something like MediaTomb to serve media to devices via uPnP?

---

### Post by doas777 on 2011-05-31
> **GROwen said:**
> Thanks for the quick reply, helps me to make sense of what Samba actually is and gives me enough incentive to just go ahead and format to ext2/3 to see how it works.

Samba has been working great between the Ubuntu machine and the Mac for serving music to iTunes is that scenario very different from using something like MediaTomb to serve media to devices via uPnP?

well, like I said, that depends on how you hack the device. if you hack it so that whatever filesystem drivers mediatomb uses to read disk data will read off ext2, it shouldn't notice what file system type is underneath. without knowing more about how you intend to modify it, I couldn't say (and it'd prolly come down to try it and see). 

your device does appear to run linux, so that should make it easier.
[http://www.shadowandy.net/2008/06/dns-313-specifications.htm](http://www.shadowandy.net/2008/06/dns-313-specifications.htm)

---

### Post by GROwen on 2011-05-31
> if you hack it so that whatever filesystem drivers mediatomb uses to read disk data will read off ext2

By this do you mean that if mediatomb reads/compatible with ext2? It appears to be, people have had issues with mediatomb on ntfs and were recommended to format to ext2/3.

Thanks for the link too, definitely going to give it a hack to see where it leads me.

---

### Post by doas777 on 2011-06-01
> **GROwen said:**
> By this do you mean that if mediatomb reads/compatible with ext2? It appears to be, people have had issues with mediatomb on ntfs and were recommended to format to ext2/3.

Thanks for the link too, definitely going to give it a hack to see where it leads me.


well, yes and no. most applications do not directly access the filesystem, but instead make system calls (to code in the kernel) to do that for them. programmers are still responsible for navigating the filesystem however. most modern langagues have mechanisms built in that allow them to determine the details of the host environment, so a well coded program will ask the system where it uses / or \ for path seperators, etc.

so, if the developers of mediatomb avoided directly specifying system-dependent paths and used system calls to access files, then it will work just fine no matter what filesystem it has underneath it. 

just a hint, remember, Samba acts as an intermediary, so if mediatomb doesn't work right accessing the ext2, then just try pointing it to a samba share of that location instead of accessing it directly. may cost you some performance, but its worth a shot.

---

### Post by tgalati4 on 2011-06-01
I've had good luck with [http://freenas.org](http://freenas.org).

---

