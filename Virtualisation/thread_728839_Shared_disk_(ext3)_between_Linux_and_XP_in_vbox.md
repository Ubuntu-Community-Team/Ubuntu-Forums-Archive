---
title: "Shared disk (ext3) between Linux and XP in vbox"
date: 2008-03-19
forum: Virtualisation
---

### Post by Kiri on 2008-03-19
Has anyone had experience to use a shared partition formatted to ext3 between Linux (host) and XP (guest) in virtualbox or other virtualization software?

Are there any problems or issues with having applications in the guest OS (XP) write to or read from the ext3 partition ?

---

### Post by gdrumm on 2008-03-19
Are you talking about a physical hard disk with dual partitions, or a virtual machine running on top of a Linux OS with an EXT3?

If you're talkign about the latter, I have several VMWare Servers and ESX Servers, and a VirtualBox server, all with "Linux" at the core and I've never had any issues with formatting a virtual hard disk in FAT, FAT32, or even NTFS.  I have several production servers running under this config.

Unless I'm totally missing the question.

---

### Post by fjgaude on 2008-03-19
There are no issues with what you describe, using Samba, and a drive that is ext3. That's what I use daily, see my signature.

---

### Post by Kiri on 2008-03-20
I mean a physical hard disk with a partition fomatted to ext3 to be shared (for data, video files etc)  between the linux host and xp guest (running in a vm). So I would be accesssing the disk at the same time through linux and xp. I assume I will need to install fs driver in the xp vm, but beyond that I was wondering if there would be any problems

---

### Post by dark_harmonics on 2008-03-20
Did you check out the shared folders options in virtual box? You point it at a folder in ubuntu (like a seperate mounted HD or even just a blank folder) and it shares it out to your virtual machine. You can then map it in XP. I think its to \\vboxserver or something like that (it says the name in the same sharing window)

---

### Post by fjgaude on 2008-03-20
> **Kiri said:**
> I mean a physical hard disk with a partition fomatted to ext3 to be shared (for data, video files etc)  between the linux host and xp guest (running in a vm). So I would be accesssing the disk at the same time through linux and xp. I assume I will need to install fs driver in the xp vm, but beyond that I was wondering if there would be any problems

Yes, yes... you can do that either in VBox or VMware... it's easy and fast. My raid5 is an ext3 filesystem and through Samba the Windows guest has full access to all the files there. And all the Windows programs do too.

It's all done through Shares, in both Windows and in Ubuntu. The whole disk or disks can be a Share or Shares.

---

### Post by Kiri on 2008-03-20
Ok then I will go ahead and format to ext3. Thanks for the info :)
Did you need to install the fsdriver to get the ext3 filesystem recognized by windows by the way?

---

### Post by fjgaude on 2008-03-20
Well, I normally have my host as Ubuntu. All the files on the Windows side are NTFS. Setting up Samba (System/Administration/Shared Folders) in Ubuntu and sharing the drives you wish to share in Windows should do it. Make sure you set the workgroup to the name you wish to use in Windows.

Then in Windows share the drive or folders you wish using Explorer, the file browser. You will see your workgroup in My Networks, or just Networks. Click until you see your Ubuntu shares.

Samba is the program that does the trick between Windows type files and Linux types.

Let us know how you are doing... lots of work to go through to get everything working with USBs and the like. But it does work and is dead reliable, no bugs.

---

### Post by Kiri on 2008-03-21
oh I see. Actually I have never used samba and am not really sure how it works, so I was a bit confused... (and still actually, lol)
But it sounds like it will work, so I will try it out. 
Thanks :)

ps: One thing I'm confused by though, wouldn't it be easier just to use the fs driver in the XP guest to provide support for the ext3 disks?

---

### Post by fjgaude on 2008-03-21
> **Kiri said:**
> oh I see. Actually I have never used samba and am not really sure how it works, so I was a bit confused... (and still actually, lol)
But it sounds like it will work, so I will try it out. 
Thanks :)

ps: One thing I'm confused by though, wouldn't it be easier just to use the fs driver in the XP guest to provide support for the ext3 disks?

Maybe, but there are so many ways to go about doing intergration of the vm guest with the host. It's up to you. I use Samba, which let me go from ext3 to NTFS and back. It's the Linux way.

---

### Post by Kiri on 2008-03-21
ok. Anyway, thanks for the advice :)

---

### Post by prshah on 2008-03-21
> **Kiri said:**
> I mean a physical hard disk with a partition fomatted to ext3 to be shared (for data, video files etc)  between the linux host and xp guest (running in a vm). So I would be accesssing the disk at the same time through linux and xp. I assume I will need to install fs driver in the xp vm, but beyond that I was wondering if there would be any problems

Virtual Box doesn't support physical partitions, it works only on virtual drives.

VMWare does support usage of physical partitions in virtual "guest" OSs.

Someone please kick me if I'm wrong.

---

### Post by Kiri on 2008-03-22
I actually meant a physical partition for the shared disk. I know that I will have to install XP to a virtual disk. But for data sharing I want to access a physical partition. I'm pretty sure this is possible.

---

### Post by fjgaude on 2008-03-22
> **Kiri said:**
> I actually meant a physical partition for the shared disk. I know that I will have to install XP to a virtual disk. But for data sharing I want to access a physical partition. I'm pretty sure this is possible.

You do this through Shares on Ubuntu side, and setting shares on the Windows side.

Then you use apps and the file browsers to copy, move, view files.

Notice in Ubuntu in System / Administratiin / Shared Folders menu, setup the Samba share for the whole partition, like /home/<user>. And in Windows Ecplorer set a drive or folder to share.

Once we understand what to do it is easy to do it. In VBox you simply set the shared folders in menu. I don't any longer use VBox but it is also easy.

Let us know how you are doing.

---

### Post by Kiri on 2008-03-22
thanks fjgaude. Once I actually install ubuntu I will try it. (at the moment I am just running ubuntu in vbox)

---

