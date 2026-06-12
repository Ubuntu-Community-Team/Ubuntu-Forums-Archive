---
title: "Using Linux filesystems on NAS boxes to prevent viral spread"
date: 2010-07-01
forum: Server Platforms
---

### Post by Ted_Smith on 2010-07-01
Hi

At work, we have a series of Blade servers and NAS storage boxes. The servers all run Windows Server 2003. 

All the storage is formatted as NTFS filesystems, and managed by the Windows operating system. 

All the workstations connect to these storage areas, and run a variety of Windows based software. 

However, despite having anti-virus software installed, the odd virus has broken out in the past, and my colleagues are trying to work out a better way to avoid this. 

Being the office "Linux guy" I have informally proposed that all the storage servers are reformatted to Linux using ext3 or ext4 filesystems, my thinking being that this would prevent many viruses being able to spread. 

I was not taken very seriously. 

It was only a casual suggestion, so I'm not sure if it actually has any credability, as I'm not a server person by trade. Does it though? Would changing our storage areas to ext3\4 and then installing Samba to allow the Windows based workstations to utilise such storage help reduce viral spread? 

Ted

---

### Post by wirelessmonkey on 2010-07-01
Virus propogation will have very little to do with filesystem, and very much to do with how they are shared.

---

### Post by atomizer on 2010-07-01
It's not about the FileSystem, it's about the OS.

There are a few Viri that affect Linux and a lot that affect Windows

---

### Post by Vegan on 2010-07-01
Malware is OS spread, not based on storage. Moving from Windows Server to Linux for a file server is easy enough.

SAMBA is well developed to make it happen. I use it, so my Linux box also is the web server too.

---

