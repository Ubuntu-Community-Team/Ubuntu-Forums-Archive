---
title: "losing quality OGV after editing (PiTiVi)"
date: 2010-03-12
forum: Ubuntu Studio
---

### Post by mbz99 on 2010-03-12
[B]I was trying to edit ogv video recorded by 			[B]gtk-recordMyDesktop , I used PiTiVi, There are losing in the quality,and texts in screen didn't appear clearly, any suggestions to avoid the problem.

thanks :)
[/B][/B]

---

### Post by ragtag on 2010-03-12
OGV is a lossy compressed format. So it's getting compressed twice, first by recordMyDesktop, and then again by PiTiVi.

Enable Zero Compression in the Performance tab in recordMyDesktop. It will take a lot more disk space, but at least you'll only be compressing it once when outputting the final video. :)

---

### Post by mbz99 on 2010-03-13
> **ragtag said:**
> OGV is a lossy compressed format. So it's getting compressed twice, first by recordMyDesktop, and then again by PiTiVi.

Enable Zero Compression in the Performance tab in recordMyDesktop. It will take a lot more disk space, but at least you'll only be compressing it once when outputting the final video. :)

It is hard to record video again, Can I covert it to enable zero compression on the exist video?

Thanks anyway.

---

### Post by mcduck on 2010-03-13
> **mbz99 said:**
> It is hard to record video again, Can I covert it to enable zero compression on the exist video?

Thanks anyway.

It's too late, the details were lost at the point when the video was compressed the first time (that's why it's called a *lossy* compression.)

There's no way to get back the information that was removed from the video during the compression. If that was possible there wouldn't really be any use for lossless compressions, would there..

---

### Post by mbz99 on 2010-03-14
> **mcduck said:**
> It's too late, the details were lost at the point when the video was compressed the first time (that's why it's called a *lossy* compression.)

There's no way to get back the information that was removed from the video during the compression. If that was possible there wouldn't really be any use for lossless compressions, would there..

Thanks of sharing information

 [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

