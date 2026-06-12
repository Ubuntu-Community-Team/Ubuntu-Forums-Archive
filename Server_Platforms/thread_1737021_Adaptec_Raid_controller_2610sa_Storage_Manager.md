---
title: "Adaptec Raid controller 2610sa Storage Manager"
date: 2011-04-22
forum: Server Platforms
---

### Post by Teh_Messiah on 2011-04-22
Hi all,

I bought an Adaptec aar 2610sa 6 port sata raid controller from Ebay for my home file server / media center.

I have 6 seagate 1tb drives in 2x 2TB raid5 arrays.
which recently on reboot told me that 1 of the drives wasn't working due to a S.M.A.R.T status error.

I have bought a new drive to replace the broken one but since the Adaptec Storage manager doesn't work I can't rebuild/repair the array.

I found several places online that explain how to use alien to convert the storage manager .rpm to a .deb

[http://lists.us.dell.com/pipermail/linux-poweredge/2006-October/028050.html]("http://lists.us.dell.com/pipermail/linux-poweredge/2006-October/028050.html")
[http://ubuntuforums.org/showthread.php?t=491049]("http://ubuntuforums.org/showthread.php?t=491049")
[http://benheininger.homelinux.net/raidmngr.htm]("http://benheininger.homelinux.net/raidmngr.htm")

Which I did and then installed, which seemed to work?!?!
Until I go to login.
when I login it just says > user root could not be logged in to ben-MS-7260

The command line utilities don't work either.
```
sudo /usr/StorMan/arcconf getconfig 1
/usr/StorMan/arcconf: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

[LIST=1]
[*]Does anyone know if I can just rebuild the array from the dos command at startup?
[*]If not, can anyone tell me how to get this Adaptec Storage Manager to work Xubuntu 10.10 64bit
[*]Can ubuntu team build a working version of the Storage Manager for these cards Please?
[/LIST]

---

### Post by Teh_Messiah on 2011-04-27
Bump!!

Anyone know any answers to the above please?
I don't want to mess this up and lose data.

Another thought, since it is difficult to set up should I just use the discs as JBOD setup and use software raid mdadm.
I know this defeats the purpose of having hardware RAID but I cant monitor or manage it without the software for the card!

Help ASAP Please.

---

### Post by dtfinch on 2011-04-27
That library file can be found in this package:
[http://packages.ubuntu.com/dapper/libs/libstdc++2.10-glibc2.2](http://packages.ubuntu.com/dapper/libs/libstdc++2.10-glibc2.2)

Be aware that the package is over 5 years old (10 releases) and 32-bit, and that version of the library is 10 years old, and might not work at all. I have almost no experience with 32 bit libraries on 64 bit Linux, but I suspect you'll have to do some extra work like moving it from /usr/lib to /usr/lib32, though I'm not positive. And if, while installing, it prompts you to remove something, or if it claims to be upgrading rather than installing, I'd abort it, and try extracting the file manually, and creating a symlink to it with the name "libstdc++-libc6.2-2.so.3".

And if it does work, there's a good chance it'll complain about another library missing, and so on. You might be able to get a full list of what libraries it needs by running "ldd" on it.

You might also want to search for a newer version of their storage manager if you haven't already.

---

### Post by Teh_Messiah on 2011-04-28
Thank you :)

My backup finally finished after 3 days of compression to multiple rar.

Had to go away for a funeral and when I returned yesterday, shutdown + replaced the faulty drive then rebooted into the boot up adaptec bios manager it just automatically discovered the new drive and started rebuilding it immediately.

Rebuild time was approximately 18 to 20 hours for a RAID5 2TB array :/
3x 1TB Seagates.

---

### Post by Teh_Messiah on 2011-04-28
This is the latest version which is what I downloaded and installed.
[http://www.adaptec.com/en-us/speed/raid/aac/sm/asm_linux_x64_v4_30-16038_rpm.htm]("http://www.adaptec.com/en-us/speed/raid/aac/sm/asm_linux_x64_v4_30-16038_rpm.htm")
[LIST=1]
[*]Do you think I need one of these drivers as well as the storage manager?
[http://www.adaptec.com/en-us/support/raid/sata/aar-2410sa/]("http://www.adaptec.com/en-us/support/raid/sata/aar-2410sa/")
[*]If so which one do I download?
[*]Or do you think it is a waste of time and system resources to even bother with it?
[/LIST]

---

### Post by Teh_Messiah on 2011-04-29
I found more problems with this raid card here on our forums
[http://ubuntuforums.org/showthread.php?t=583820]("http://ubuntuforums.org/showthread.php?t=583820")

I "sudo apt-get purge storeman".
That fixes everything!
Now I just check it everytime I reboot the system after installing updates that require restarts!

Only other method would be to use one of the supported OSes like redhat/CentOS, or SUSE. 
Or even run them in a virtual machine inside xubuntu to monitor it!
I don't think so!

---

### Post by oke on 2011-09-10
I've also ditched StorMan for controlling the 2610sa in an Ubuntu 32-bit desktop release after many attempts. I never succeeded in getting the client and server connected and finally gave up. However, I found following website /[http://hwraid.le-vert.net/]("http://hwraid.le-vert.net/"), which was really helpful for me in getting arcconf working in Ubuntu :).

Currently, I have arcconf with the 2610sa working fine in Ubuntu 10.04 LTS desktop 32-bit. Since the 2610sa is already rather old not all commands available in this arcconf version are working. E.g., power management features are not available in the 2610sa so for instance drive spin up staggering is not possible.

Note that the website ([http://hwraid.le-vert.net/wiki/DebianPackages]("http://hwraid.le-vert.net/wiki/DebianPackages")) also has an amd64 version of arcconf available. Hence, it might work on your system too.

---

