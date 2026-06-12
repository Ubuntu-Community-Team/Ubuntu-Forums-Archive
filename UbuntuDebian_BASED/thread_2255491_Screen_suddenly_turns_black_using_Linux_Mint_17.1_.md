---
title: "Screen suddenly turns black using Linux Mint 17.1 Rebecca"
date: 2014-12-05
forum: Ubuntu/Debian BASED
---

### Post by iokara08 on 2014-12-05
Good evening,

My laptop is an LG E500 running Linux Mint for the last 3 years. Last April, 2014, I upgraded to Linux mint 17. Everything was working fine. Since October my laptop's screen sometimes turned black and I couldn't do anything except entering in slleping mode and then coming back. Anyway, two weeks ago I upgraded to Linux Mint 17.1 Rebecca hopefully that this problem would be disappeared. Unfortunately, this issue is continue. Below are my laptop's characteristics (acquired using ''System Profiler and Benchmark''):
[TABLE]
[TR]
[TD="class: field"]**CPU**
Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz[/TD]
[TD="class: value"]
1733,00MHz[/TD]
[/TR]
[TR]
[TD="class: field"]Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz[/TD]
[TD="class: value"]1333,00MHz
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="class: sstitle, colspan: 2"]**OpenGL**[/TD]
[/TR]
[TR]
[TD="class: field"]Vendor[/TD]
[TD="class: value"]Intel Open Source Technology Center[/TD]
[/TR]
[TR]
[TD="class: field"]Renderer[/TD]
[TD="class: value"]Mesa DRI Intel(R) 965GM x86/MMX/SSE2[/TD]
[/TR]
[TR]
[TD="class: field"]Version[/TD]
[TD="class: value"]2.1 Mesa 10.1.3[/TD]
[/TR]
[TR]
[TD="class: field"]Direct Rendering[/TD]
[TD="class: value"]Yes[/TD]
[/TR]
[/TABLE]
**MEMORY**
2055MB

**SCSI DISKS**
[TABLE]
[TR]
[TD="class: field"]ATA FUJITSU MHY2160B[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]HL-DT-ST DVDRAM GSA-T20N[/TD]
[/TR]
[/TABLE]

My personal opinion is that something has to do with the drivers of my graphic card. I checked for any other driver using the ''additional drivers'' software but I get that this system doesn't use any proprietary driver. Any kind of help is more than welcome!

---

### Post by iokara08 on 2014-12-15
Hi again,

I figured out that my problem is a known bug described here:
[https://www.libreoffice.org/bugzilla/show_bug.cgi?id=80568](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=80568)

After reading the link above I understood that the problem is related with google chrome browser.
I used my system for the last 10 days without using chrome and everything works fine as it should.
Therefore I will mark this thread as solved and I am sure that in the short term this bug will be overcomed ):P.

---

