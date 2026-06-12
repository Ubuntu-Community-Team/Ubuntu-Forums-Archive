---
title: "Ubuntu CD: &quot;Cannot find autorun program&quot;"
date: 2009-01-24
forum: System76 Support
---

### Post by Crispus K on 2009-01-24
I have a pav4 running ubuntu 8.10.  I am attempting to reinstall ubuntu to fix a few minor bugs that have popped up using the install CD that i ordered off the main ubuntu website. I pop it in. It asks if I'd like to autorun the software. I click the Run button and then an error message pops up that says "Error autorunning software.  Cannot find the autorun program"

Does anyone know what the issue might be here or have a work around that will allow me to reinstall the OS?

Thanks

---

### Post by jdb on 2009-01-24
> **Crispus K said:**
> I have a pav4 running ubuntu 8.10.  I am attempting to reinstall ubuntu to fix a few minor bugs that have popped up using the install CD that i ordered off the main ubuntu website. I pop it in. It asks if I'd like to autorun the software. I click the Run button and then an error message pops up that says "Error autorunning software.  Cannot find the autorun program"

Does anyone know what the issue might be here or have a work around that will allow me to reinstall the OS?

Thanks

That sounds like a windows error.

You need to power up with the CD in the drive.
If it does not boot to the CD, you may need to change a bios option to allow it.

Be aware that the partition to which you load Ubuntu will be completely erased, you will lose everything that is on it.

jdb

---

### Post by Murrquan on 2009-01-24
> **Crispus K said:**
> I have a pav4 running ubuntu 8.10.  I am attempting to reinstall ubuntu to fix a few minor bugs that have popped up using the install CD that i ordered off the main ubuntu website. I pop it in. It asks if I'd like to autorun the software. I click the Run button and then an error message pops up that says "Error autorunning software.  Cannot find the autorun program"

Does anyone know what the issue might be here or have a work around that will allow me to reinstall the OS?

Yes!

When it talks about autorun, what it's doing is trying to use Wine to autorun the Windows software on the CD. You know how your CD has an autorun menu, that comes up when you put it in in Windows? That's what it's talking about, and that's what it's trying to run. If you don't have Wine installed, though, you won't be able to run Windows programs -- including the Ubuntu CD's autorun!

Fortunately, you don't need to. Just put the CD in your drive and restart your computer. Then you can reinstall it like normal.

[COLOR="Blue"]What are these problems you're having?[/COLOR] Ubuntu's not like Windows, where you can only solve some things by reinstalling it; you *should* be able to fix things without having to do that.

If you do decide to reinstall Ubuntu, make sure to back up all your personal data first!

---

### Post by Crispus K on 2009-01-26
Thank you for these responses.  I was able to boot to the CD by following these directions and successfully reinstalled ubuntu and the system76 drivers.  Consider this thread closed.

---

