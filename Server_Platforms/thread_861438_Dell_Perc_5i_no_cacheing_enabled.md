---
title: "Dell Perc 5/i no cacheing enabled"
date: 2008-07-16
forum: Server Platforms
---

### Post by getut on 2008-07-16
Can anyone walk me through the steps to enable the cache on my Dell 2900 Perc 5/i. I am running 64bit Hardy server.

I have been beating on a VMWare disk performance issue for a long time and think this might be the cause. The controller BIOS doesn't have any facility to let me change the setting. I found another thread on here discussing the 5/iR which is a different controller. I can find nothing on the 5/i.

My DMESG log pertinent lines:```

[  163.044342] sd 0:2:0:0: [sda] 1464074240 512-byte hardware sectors (749606 MB)
[  163.044388] sd 0:2:0:0: [sda] Write Protect is off
[  163.044390] sd 0:2:0:0: [sda] Mode Sense: 1f 00 10 08
[  163.044492] sd 0:2:0:0: [sda] Write cache: disabled, read cache: disabled, supports DPO and FUA
[  163.044617] sd 0:2:0:0: [sda] 1464074240 512-byte hardware sectors (749606 MB)
[  163.044662] sd 0:2:0:0: [sda] Write Protect is off
[  163.044665] sd 0:2:0:0: [sda] Mode Sense: 1f 00 10 08
[  163.044744] sd 0:2:0:0: [sda] Write cache: disabled, read cache: disabled, supports DPO and FUA
[  163.044749]  sda: sda1 sda2 <<6>ata1.00: ATAPI: TSSTcorp CD-RW/DVD-ROM TS-H492C, DE02, max UDMA/33
[  163.067845]  sda5 >
[  163.067958] sd 0:2:0:0: [sda] Attached SCSI disk
[  163.068118] sd 0:2:1:0: [sdb] 1464074240 512-byte hardware sectors (749606 MB)
[  163.068160] sd 0:2:1:0: [sdb] Write Protect is off
[  163.068163] sd 0:2:1:0: [sdb] Mode Sense: 1f 00 10 08
[  163.068240] sd 0:2:1:0: [sdb] Write cache: disabled, read cache: disabled, supports DPO and FUA
[  163.068377] sd 0:2:1:0: [sdb] 1464074240 512-byte hardware sectors (749606 MB)
[  163.068419] sd 0:2:1:0: [sdb] Write Protect is off
[  163.068422] sd 0:2:1:0: [sdb] Mode Sense: 1f 00 10 08
[  163.068518] sd 0:2:1:0: [sdb] Write cache: disabled, read cache: disabled, supports DPO and FUA
[  163.068523]  sdb: sdb1
[  163.068713] sd 0:2:1:0: [sdb] Attached SCSI disk
[  163.068804] sd 0:2:2:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[  163.068843] sd 0:2:2:0: [sdc] 4392222720 512-byte hardware sectors (2248818 MB)
[  163.068897] sd 0:2:2:0: [sdc] Write Protect is off
[  163.068900] sd 0:2:2:0: [sdc] Mode Sense: 1f 00 10 08
[  163.068991] sd 0:2:2:0: [sdc] Write cache: disabled, read cache: disabled, supports DPO and FUA
[  163.069095] sd 0:2:2:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[  163.069149] sd 0:2:2:0: [sdc] 4392222720 512-byte hardware sectors (2248818 MB)
[  163.069217] sd 0:2:2:0: [sdc] Write Protect is off
[  163.069220] sd 0:2:2:0: [sdc] Mode Sense: 1f 00 10 08
[  163.069306] sd 0:2:2:0: [sdc] Write cache: disabled, read cache: disabled, supports DPO and FUA
[  163.069311]  sdc: sdc1
```

---

### Post by unixbills on 2008-07-16
I have a PERC 6 in default setup and it seems to be the exact opposite

[CODE:]
[sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[/CODE:]

Maybe you can figure out how to turn off DPO or FUA support and that will enable the cache.

---

### Post by getut on 2008-07-17
I found mutliple threads mentioning that I need the megacli program. I think that program is the one that will allow me to change the cache settings as well as the DPO and FUA modes if those need to be changed also.

I think the reason mine is defaulting to no caching is because we opted to not purchase the battery backed version because we have our server rack hooked to a 2kva UPS as well as a backup generator.

The megacli has command options to force the usage of cache if the battery is failed or not present.

I have found it but alien won't convert it to deb because I can only find a 32 bit version of megacli.. then alien complains about AMD64 not being in packages architecture list.

```
xxx@yyy:~/Compiled_Software$ sudo alien MegaCli-1.01.39-0.i386.rpm
Warning: Skipping conversion of scripts in package MegaCli: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/megacli
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: MegaCli-1.01.39: No such file or directory

```

End result is I'm still stuck.

---

### Post by getut on 2008-07-22
One more bump before I give up on this.

Does anyone know of megacli in deb format for 64bit ubuntu?
or know how to run 32 megacli on 64bit machine?

Please help me.

---

### Post by robhouse on 2008-08-02
I believe you would have to download MegaCLI from LSI as a rpm and then use something like alien to convert it to a .deb or .tar.gz.

See: [URL="http://pookey.co.uk/blog/archives/45-Dell-PERC-6i-and-RAID-monitoring.html"]http://pookey.co.uk/blog/archives/45-Dell-PERC-6i-and-RAID-monitoring.html
[/URL]
Regards,

RH.

---

