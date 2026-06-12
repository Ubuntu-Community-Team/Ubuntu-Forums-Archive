---
title: "suggestion on this blog post : Nessecary Tools for Booting Issues on ubuntu and windo"
date: 2010-01-22
forum: The Cafe
---

### Post by medya on 2010-01-22
hey guys I just finished writing this blog post , do you think I have included all the cool necessary applications ? help me adding more useful stuff (sorry for my bad english)

[Nessecary Tools for Booting Issues on ubuntu and windows , Bootloader, Grub , MBR]("http://blog.shevin.info/2010/01/nessecary-tools-for-booting-issues-on.html")

here is the full text , links wont be copied here .
> 
Sorry guys that I dont update that much, I am stuck with my university in Iran, it is funny I fail my courses with bad scores and those guys who dont know a thing about comptuer get best scores okay enough nagging let read my newest article !

Having Windows Xp, Windows Vista, Windows Seven , ubuntu 8.04 and ubuntu 9.10 on two hard disks , has made me an expertise in facing all kind of problem with Dual booting (I guess I should say Quad booting) .

I had written an article about grub three years ago and I still receive emails saying "Thank you that saved my ***".

here I want to introduce some links and applications to save more ***** ;)

Warning : these list items are not steps , don't do them blindly one after another, these are seprate solutions for seprate problems .

    * First of all Grub 2 Tutorial on the forum is a great reference for all !

    * if you deleted one of your partitions and the partition table became invalid then try
      TestDisk

    * it is always a good idea to see a list of your partitions in ubuntu (you can always boot from an Ubuntu live CD)

          sudo fdisk -l

      in the results you can see the bootable partition is marked with a * and you an see their official name (the name that computer knows them by)
      for i.e :

          /dev/sdb2 * 5043 9562 36306900 7 HPFS/NTFS

      that tells me sdb2 (the second partion of my B hard disk is bootable and its filesystem is NTFS) and its address is /dev/sdb2

    * if you deleted your Windows bootloader . (in my case I deleted the first partition of windows hard disk) and windows MBR was gone, you can restore it using an Ubuntu live CD

          sudo apt-get install lilo
          sudo lilo -M /dev/sda mbr


      Replace sda with your hard disk ,for i.e if want to restore the windows MBR of your second hard disk it would be :

          sudo lilo -M /dev/sdb mbr

    *

          Partition Magic 8.1 Bootable CD is available on torrents , you can search and download if it is legal in your country . (I can't give you a direct link but you can search in Torrentz )

    * Gparted Live CD is an open source clone of Partition magic .

    * SystemRescueCD is a great linux Live CD , that does tons of things , from partion-ing to cloning and repairing more !

    * there are Russian windows live CDs that are useful , find them on torrentz at your own legal risk (becareful they are fake virus ones too)

    * to make your grub menu beautiful , you can always try Start up Manager
      for ubuntu


---

### Post by medya on 2010-01-22
update : I added this to the gparted :

in gparted you can , right click on the partition you want  then click on "Manage Flags" then you can make a partition bootable by marking the boot flag.

---

