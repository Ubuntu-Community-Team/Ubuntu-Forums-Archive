---
title: "Rosetta Stone using WINE, yet again"
date: 2011-01-09
forum: Wine
---

### Post by deussean on 2011-01-09
Hello, I have been trying to use Rosetta Stone 2.2.0.0A with WINE 1.2 (1.1.31, same thing) and it DO NOT work.  It installs seemingly ok but when i put my language cd in (chinese) it says :  'object expected.  script error.  continue?'   if i say yes, it just gives me the same crap, if i say no it exits the program.  
I tried making an ISO of the disk and just copying the files to a directory and adding the path of those into WINE but then Rosetta Stone won't recognize them and asks for the disk.  

If anyone has any ideas about how to get this working, I would love to hear it.  I've been all around the internet looking and I don't want to dualboot (yaaay freedom!).  

I can also give terminal's error output when i run RS if someone quickly tells me how to embed it in those nice little list boxes.  

thanks for anything

---

### Post by ronnielsen1 on 2011-01-09
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867)

That particular version is rated garbage in winehq. Sorry, you probably won't get it to work. Can you get your hands on a newer Rosetta Stone?

---

### Post by deussean on 2011-01-09
> **ronnielsen1 said:**
> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867)

That particular version is rated garbage in winehq. Sorry, you probably won't get it to work. Can you get your hands on a newer Rosetta Stone?
i saw that, but i was hoping that a newer version of wine (or ubuntu) would straighten it out.  since i paid for it, i would like to use my rosetta stone, but i could look around for torrents of others.  if you know of any resources for newer versions or tips for getting mine to work, lemme know.  

i've also heard someone else complain that the problem might be the ancient version of quicktime that automatically installs when you installl rosetta stone.  i'm going to try to install a newer version and see where that takes me.  

thanks

---

### Post by deussean on 2011-01-09
OK, updating the quicktime sure didn't work.  
anyway, if it helps at all the output of the error messages is as follows ( i would like to know how to put it in that hand list box everyone puts it in) :

fixme:mountmgr:harddisk_ioctl unsupported ioctl 70020
fixme:mountmgr:harddisk_ioctl unsupported ioctl 70020
fixme:mountmgr:harddisk_ioctl unsupported ioctl 70020
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a3ab8,0x1a5de8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a3ab8,0x1a7490): stub
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp9A630.FOT",L"C:\\windows\\temp\\AAX36a5.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp6C630.FOT",L"C:\\windows\\temp\\AAX36c4.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpFC630.FOT",L"C:\\windows\\temp\\AAX36c9.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpFD630.FOT",L"C:\\windows\\temp\\AAX36d9.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp6E630.FOT",L"C:\\windows\\temp\\AAX36e3.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpDE630.FOT",L"C:\\windows\\temp\\AAX36ea.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp7F630.FOT",L"C:\\windows\\temp\\AAX36f2.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpBF630.FOT",L"C:\\windows\\temp\\AAX36f9.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpFF630.FOT",L"C:\\windows\\temp\\AAX36fd.tmp",(null)): stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp40730.FOT",L"C:\\windows\\temp\\AAX3702.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpD0730.FOT",L"C:\\windows\\temp\\AAX3707.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpA1730.FOT",L"C:\\windows\\temp\\AAX370f.tmp",(null)): stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp52730.FOT",L"C:\\windows\\temp\\AAX3721.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpB6730.FOT",L"C:\\windows\\temp\\AAX3764.tmp",(null)): stub
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:shell:DllCanUnloadNow stub

---

