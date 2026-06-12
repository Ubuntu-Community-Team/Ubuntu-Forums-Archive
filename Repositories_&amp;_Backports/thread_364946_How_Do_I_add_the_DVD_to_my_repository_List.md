---
title: "How Do I add the DVD to my repository List?"
date: 2007-02-18
forum: Repositories &amp; Backports
---

### Post by TwistesdTexan on 2007-02-18
I don't know how but the DVD selection on the first page of Software Sources Dialog box nmo longer has the DVD option. When I try to add a Cdrom to the repositories I get an error that it could not find the disk. I am most likely wrong in assuming that I can use a dvd install - live disk as a repository though. Thnks

---

### Post by erkki70 on 2007-02-19
Hi,
This is from :
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> **Managing Local Repositories**

   **Disable the CD-ROM Repository**

  If you have installed Ubuntu from one of Ubuntu's CD-ROMs, the CD will be included in the list of repositories used by the package managment tools. When you install a new package, **Synaptic** will check whether the package is available locally (i.e. on the CD-ROM). **Synaptic** may then ask for the CD-ROM. This can help reduce the size of downloads and speed up the installation process. If you would like **Synaptic** to rely solely on the internet repositories for package management, you can disable the CD-ROM entry with a few steps: 
 [LIST]
[*] Launch Synaptic and navigate to "Settings" > "Repositories". 
 A list of software repositories or "Channels" will be shown. 
[*] Locate the entry for the CD-ROM (it may say something like **CD disk with Ubuntu 6.06 LTS**). Click on the checkbox next to it to disable the CD-ROM as a software source. 
[*] Click the **Close** button to save the changes you have made. 
[*] You can re-enable the CD-ROM at any time using the checkbox next to its entry.
[/LIST]So, if your DVD is in the drive this should work I guess...
Good luck :-)

Cheers,

---

### Post by TwistesdTexan on 2007-02-19
I looked in Synaptic under the repository list. This is a mirror of the source list (CD is not there). When I go to the third party tab and click the add CDrom it looks for a third party and can't find it ( E: fialed to locate cd...).

---

### Post by erkki70 on 2007-02-19
This time from:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
> 
** How to add extra repositories on DVDs **

 For users without broadband connection downloading packages from the net is a really big problem. You can download packages in DVDs and use them on every ubuntu installation without the need of downloading. [LIST]
[*] Download DVDs[/LIST]for i386  [Main Repository]("http://torrents.thepiratebay.org/hashtorrent/3552440.torrent/Ubuntu_6.10_-_Edgy_Eft_-_Main_Repository_-_i386.3552440.TPB.torrent")
[Universe - Multiverse - Restricted DVD1]("http://torrents.thepiratebay.org/hashtorrent/3552441.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_i386_-_1_of_3.3552441.TPB.torrent")
[Universe - Multiverse - Restricted DVD2]("http://torrents.thepiratebay.org/hashtorrent/3552442.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_i386_-_2_of_3.3552442.TPB.torrent")
[Universe - Multiverse - Restricted DVD3]("http://torrents.thepiratebay.org/hashtorrent/3552444.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_i386_-_3_of_3.3552444.TPB.torrent")  or for amd64  [Main Repository]("http://torrents.thepiratebay.org/hashtorrent/3570366.torrent/Ubuntu_6.10_-_Edgy_Eft_-_Main_Repository_-_amd64.3570366.TPB.torrent")
[Universe - Multiverse - Restricted DVD1]("http://torrents.thepiratebay.org/hashtorrent/3570368.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_amd64_-_1_of_3.3570368.TPB.torrent")
[Universe - Multiverse - Restricted DVD2]("http://torrents.thepiratebay.org/hashtorrent/3570369.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_amd64_-_2_of_3.3570369.TPB.torrent")
[Universe - Multiverse - Restricted DVD3]("http://torrents.thepiratebay.org/hashtorrent/3570371.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_amd64_-_3_of_3.3570371.TPB.torrent")  
  [LIST]
[*] Burn ISOs to DVDs (Read [  #How to burn Image (ISO) files into CD/DVD]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_burn_Image_.28ISO.29_files_into_CD.2FDVD"))[/LIST][LIST]
[*] System -> Administration -> Synaptic Package Manager[/LIST][LIST]
[*] To add DVDs in Repository lists[LIST=1]
[*] Settings -> Repositories -> Third Party
[*] Insert first DVD in drive and click Add Cdrom
[*] Name the added DVD
[*] repeat for other DVDs also[/LIST] [/LIST]Otherwise is your DVD player accessible, and mounted? can you read data from it? Do you have the DVD loaded into the drive?

---

