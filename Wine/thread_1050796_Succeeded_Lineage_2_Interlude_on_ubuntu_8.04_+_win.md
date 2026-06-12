---
title: "Succeeded: Lineage 2 Interlude on ubuntu 8.04 + wine 1.1.13"
date: 2009-01-26
forum: Wine
---

### Post by smo0th on 2009-01-26
Well after a few hours I succeeded in playing Lineage 2 in a private server (l2chile) which runs interlude. My system runs wine 1.1.13 over hardy(8.04). I have a Phenom CPU with 4 GB RAM and a 512MB GeForce 5200GT.

Here are the steps I followed:

1. Install wine: ```
sudo apt-get install wine
```
2. Download and install Lineage client: [[COLOR="DarkOrange"]http://games.internode.on.net/filelist.php?filedetails=7053[/COLOR]]("http://games.internode.on.net/filelist.php?filedetails=7053") (interlude in this case)

3. Download and apply the private server's system folder: [[COLOR="DarkOrange"]http://rapidshare.com/files/72092818/SystemL2Chile.rar.html[/COLOR]]("http://rapidshare.com/files/72092818/SystemL2Chile.rar.html") (l2chile)

4. I had to modify the l2.ini configuration for it to work under ubuntu. For this we need [[COLOR="DarkOrange"]l2encdec.exe[/COLOR]]("http://dstuff.l2wh.com/public/common/l2encdec_292.zip") so we can edit l2.ini, decompress l2encdec.exe to your system folder and go there with the terminal, type ```
wine l2encdec.exe -d l2.ini l2dec.ini
``` This decodes l2.ini and saves it as l2dec.ini, now open the decoded one and search for the values "UseHardwareTL" and "UseHardwareVS" under "[D3DDrv.D3DRenderDevice]" and set both values to "False" (thanks razumok). Now save and close the file and type ```
wine l2encdec.exe -e 413 l2dec.ini l2.ini
``` This should do the trick.

5. You may include the server's ip into your l2.ini or modify your hosts file, either way it works fine, I prefer to include it into l2.ini

6. Copy the following dlls into your wine system32 directory (~/.wine/drive_c/windows/system32/). [[COLOR="DarkOrange"]dpmodemx.dll[/COLOR]]("http://http://www.dlldump.com/download-dll-files_new.php/dllfiles/D/dpmodemx.dll/5.03.2600.2180/download.html"), [[COLOR="DarkOrange"]dpnet.dll[/COLOR]]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/D/dpnet.dll/5.03.2600.2180/download.html"), [[COLOR="DarkOrange"]dpwsock.dll[/COLOR]]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/D/dpwsock.dll/5.00.2134.10/download.html"), [[COLOR="DarkOrange"]dpwsockx.dll[/COLOR]]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/D/dpwsockx.dll/5.03.2600.2180/download.html")

7. Edit your /etc/security/limits.conf so the end of the file looks like this:
```
* hard nofile 16383
# End of file 
```

8. Open terminal, type ```
winecfg
``` and set l2.exe and LineageII.exe to run as wind0ze xp.

9. Create an account in your private server ([[COLOR="DarkOrange"]http://l2chile.sytes.net[/COLOR]]("http://l2chile.sytes.net/") for l2chile)

10. Run l2.exe, if you have error messages close l2 and type ```
wineserver -k
``` then start again L2.

For your reference, here's my [[COLOR="DarkOrange"]l2.ini[/COLOR]]("http://rapidshare.com/files/189549070/l2.ini.html") plus [[COLOR="DarkOrange"]mirror[/COLOR]]("http://www.megaupload.com/?d=D2T5J35M")

It works similar for Gracia 2 and other L2 distros, check for yours at [[COLOR="DarkOrange"]wine headquarters[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2273").

Hope it works for you.

---

### Post by mrpopo666 on 2009-02-04
hi , i follow all steps and l2 dont run ,i dont have error messages
i execute by console and show me this 

[email]mrpopo@ubuntu:~/.wine[/email]/drive_c/Lineage2/system$ wine l2.exe
fixme:reg:GetNativeSystemInfo (0x1edb3bc) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1f26d5e): Stub!
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0034, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0035, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0036, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0037, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0038, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0039, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003a, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003b, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003c, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003d, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003e, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003f, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0040, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0041, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0042, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0043, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0044, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0045, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0046, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0047, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 000b, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0009, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0018, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0013, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0016, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0034, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0035, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0036, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0037, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0038, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0039, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003a, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003b, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003c, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003d, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003e, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 003f, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0040, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0041, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0042, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0043, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0044, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0045, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0046, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0047, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 000b, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0009, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0018, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0013, blocked by 0033, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d604 "loader.c: loader_section" wait timed out in thread 0016, blocked by 0033, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3be50


help 


pd sorry for my english :D

---

### Post by saixx on 2009-03-05
I have the same problem as mrpopo... any ideas?

---

### Post by BatPenguin on 2009-06-07
> **saixx said:**
> I have the same problem as mrpopo... any ideas?

Did you guys ever figure this out? I'm getting the same error message in Picasa (it always runs Wine).

---

### Post by AllRadioisDead on 2009-10-23
Sorry for necroposting, but I'm getting the same problem as mrpopo, can someone please help?

---

### Post by netCDwtF on 2010-01-22
[http://dstuff.l2wh.com/public/common/l2encdec_292.zip](http://dstuff.l2wh.com/public/common/l2encdec_292.zip)

is dead link >.<

---

### Post by Cordate on 2010-06-08
Necroposting, but 

[http://dstuff.luftbrandzlung.org/public/common/l2encdec_2.10.1.7z]("http://dstuff.luftbrandzlung.org/public/common/l2encdec_2.10.1.7z")

is the link to the current version of L2encdec as of the present :) 

My friend is giving this a go today, hopefully she'll be able to play later!

---

### Post by netCDwtF on 2010-06-09
i still have following error message while runing l2  ingame

> 
fixme:d3d_shader:shader_glsl_load_constantsI >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4ivARB @ glsl_shader.c / 300
fixme:d3d_shader:shader_glsl_load_constantsI >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4ivARB @ glsl_shader.c / 300
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315



also, most of the textures are missing :S 

any ideas?

---

