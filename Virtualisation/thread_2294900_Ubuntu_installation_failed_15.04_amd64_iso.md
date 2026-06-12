---
title: "Ubuntu installation failed 15.04 amd64 iso"
date: 2015-09-14
forum: Virtualisation
---

### Post by GirishSharma on 2015-09-14
Host OS : Windows 7 Home Premium 64 bit
Downloaded ubuntu-15.04-desktop-amd64.iso.  MD5Sum (53c869eba8686007239a650d903847fd) matched.
Oracle VM Virtual Box Version 4.2.4 r81684
Enabled 3D Acceleration.

After few minutes of installation, I gets 
Oracle VM VirtualBox Manager has stopped. Windows is checking for a solution to the problem.
Then a message box saying something Windows will inform you if a solution is available and a close program button.

I don't know which log part (right click the machine icon in VM software and show log option) should I post, but last few lines are :

00:01:20.257552 NAT: IPv6 not supported 00:01:20.582857 NAT: DHCP offered IP address 10.0.2.15
 00:01:20.583963 NAT: DHCP offered IP address 10.0.2.15
 00:01:24.890909 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=000000000a1e0000 w=1024 h=768 bpp=32 cbLine=0x1000, flags=0x1
 00:09:22.101045 
 00:09:22.101048 !!Assertion Failed!!
 00:09:22.101049 Expression: pSgBuf->cbSegLeft <= 5 * _1M && (uintptr_t)pSgBuf->pvSegCur >= (uintptr_t)pSgBuf->paSegs[pSgBuf->idxSeg].pvSeg && (uintptr_t)pSgBuf->pvSegCur + pSgBuf->cbSegLeft <= (uintptr_t)pSgBuf->paSegs[pSgBuf->idxSeg].pvSeg + pSgBuf->paSegs[pSgBuf->idxSeg].cbSeg
 00:09:22.101051 Location  : D:\tinderbox\win-4.2\src\VBox\Runtime\common\misc\sg.cpp(54) void *__cdecl sgBufGet(struct RTSGBUF *,unsigned __int64 *)
 00:09:22.109756 pSgBuf->idxSeg=0 pSgBuf->cSegs=1 pSgBuf->pvSegCur=00000000827c1000 pSgBuf->cbSegLeft=7012352 pSgBuf->paSegs[0].pvSeg=00000000827c1000 pSgBuf->paSegs[0].cbSeg=7012352
 
In this VM software, other machines like Ubuntu 13.04 64 bit and other windows flavour are working fine, but this installation is not going to complete.
Kindly help me to complete above 10 time failed installation efforts.

Thanks and Regards
Girish Sharma

---

### Post by howefield on 2015-09-14
Thread moved to the "*Virtualisation*" forum.

---

