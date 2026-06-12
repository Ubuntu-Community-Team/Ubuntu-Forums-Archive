---
title: "How to remove an installed program in Wine (or make it work)"
date: 2009-12-04
forum: Wine
---

### Post by Radissthor on 2009-12-04
I know this is a know issue. I read some things but they implied removing all wine applications and I just want to delete one. 

Of course, the uninstaller of the program installed doesn't work. Actually, the program doesn't run. It is a software to capture video from a Sony Digital Recorder camera. The program's called "USB TV Super Mini", the installation CD installed a driver and a software. I installed everything with wine. The player that comes with the software works, but the video capturing software doesn't even open.

I tried running 'wine uninstaller' on the terminal and I selected the program I wanted to remove (both the software and the driver) but nothing was uninstalled. This is the output I got:

```

hernan@Inspiron1525:~$ wine uninstaller
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 15/03/2009, dlt (d/m/y): 11/10/2009
fixme:reg:GetNativeSystemInfo (0x331510) using GetSystemInfo()
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x20040
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2500-000022000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2500-000022000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2500-000022000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 15/03/2009, dlt (d/m/y): 11/10/2009
fixme:reg:GetNativeSystemInfo (0x331510) using GetSystemInfo()
devcon.exe failed.
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 15/03/2009, dlt (d/m/y): 11/10/2009
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3f00-00003c000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3f00-00003c000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3f00-00003c000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
hernan@Inspiron1525:~$ 
```

Any hints on how could I solve this problem. Either making the program work or safely removing it...

---

### Post by rocky5051 on 2009-12-04
Remove it's program folder manually, then use 'wine regedit' to remove it's registry entries manually.

There really isn't any clean way to do it if the uninstaller won't work.

---

### Post by Radissthor on 2009-12-04
Thanks. Ok, I browsed and found  no folders. Apparently, the uninstaller did erase the folders, but the desktop icon and the entries on the programs menu are still there. I run wine regedit and browsed every folder, but found nothing with the name of the program...Is there something I'm missing?

---

