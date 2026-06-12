---
title: "COD4 1603 error"
date: 2010-10-29
forum: Wine
---

### Post by pieman711 on 2010-10-29
When trying to install COD4 (call of duty modern warfare) I get an MSI error saying "1603". This happens write at the end of the data transfer part. I've tried googling and although I've found some people with a similar problem I haven't found any way of fixing it.
I've tried with wine 1.2, 1.3.5 and play on linux at the most current stable release. I'm using Ubuntu 10.04 and have 11gb of hard-drive space free in my home folder. Can anyone offer any suggestions? I'm about to go out but when I get back I'll have another installing in a terminal and post the command line output.
Any help would be great, it says it's a platium game in the wine appdb and it was one of my favourite games back when I was a slave to the windows installation on my computer :P!

-edit
I've just found this in my google history not the full output but hopefully the relevant part 

```
err:msi:ACTION_InstallFiles Failed to copy L"D:\\Setup\\Data\\main\\video\\coup_load.bik" to L"C:\\Program Files\\Activision\\Call of Duty 4 - Modern Warfare\\main\\video\\coup_load.bik" (5) err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
```

---

### Post by dino99 on 2010-10-29
you might use winetricks to override msi

[http://wiki.jswindle.com/index.php/Wine_MSI](http://wiki.jswindle.com/index.php/Wine_MSI)

---

### Post by pieman711 on 2010-10-29
Still no joy. I've been playing around with the library over rides but haven't got any further (I've typed my CD key in so many times I know it by heart!) I noticed there is a bug report for this problem on the wine website. Also googling it shows that people are having a problem with this in windows (I didn't when I installed it originally in XP)
any other ideas?

---

### Post by GWBouge on 2010-10-29
I just tried installing this game as well (man I'm bored  XoD ) and getting the same error, except I'm getting it just as the installer starts copying files.  I also found a lot of Windows users getting this error thanks to Google, but there seemed to be a plethora of causes, from permissions issues to corrupt/scratched discs.

Here's the end of my output:
```
err:msi:ITERATE_Actions Execution halted, action L"InstallFiles" returned 1603
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x80000001f
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1e00-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1e00-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1e00-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1e00-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1e00-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
```

It's really strange, since I've installed it on Ubuntu before around 9.04ish (I think it was WINE 0.96 or so at the time?  ... could be wrong).  Worked fairly well back then, but the frame rate was about half (or less) of what the game ran on Windows.  Was hoping to see how much progress had been made in that department.

---

### Post by Geremia on 2012-04-20
> **pieman711 said:**
> ```
err:msi:ACTION_InstallFiles Failed to copy L"D:\\Setup\\Data\\main\\video\\coup_load.bik" to L"C:\\Program Files\\Activision\\Call of Duty 4 - Modern Warfare\\main\\video\\coup_load.bik" (5) err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
```I never used to have this problem and now I do. I think some temp or .cache files need deleting.

---

