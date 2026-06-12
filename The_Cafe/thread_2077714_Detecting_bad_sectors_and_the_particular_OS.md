---
title: "Detecting bad sectors and the particular OS"
date: 2012-10-29
forum: The Cafe
---

### Post by allen76693 on 2012-10-29
To begin with I post this as FYI I need no help except wish I was younger at 80. I am one those folks who have tried bunch Linux OS and I always come back to 10.04 hey its my comfort zone.
But last week I thought I would re-size my partition and try openSUSE 12.1 in gnome.
First disappointing aspect told me I did not have gnome3 capability and that is not focus of this FYI. So installation complete and bottom center flashing alert hard-drive problem bad sectors.
Yea initially kind of put me in a panic, my Toshiba is 4 years old and cannot afford a new one, but the sector thing really got my attention.
So put in live gparted deleted SUSE now have 10.04 single partition 250GB (I have no windows thank God.)
I then did a sudo badblocks -sv /dev/sda in my terminal
after hour and half I get test: done                                
Pass completed, 0 bad blocks found.
For you tech smart members is Suse just more sensitive and I actually have bad blocks or is it just a glitch or is Ubuntu check challenged. Finally is it my computer. As I said not looking for help just conveying experience

---

### Post by Paqman on 2012-10-29
Bad blocks aren't in themselves anything to freak out about, they do just pop up as normal wear and tear. A drive that's been in use for years with a bad block or two is fine.

What is an issue is if you have lots of bad blocks, or the number is increasing. The SMART data stored in the drive logs these things, you can check that in Ubuntu using the Disk Utility tool (aka Disks in recent version). Look under the headings "Reallocated sector count", "Current Pending sectors" and "Offline Uncorrectable".

No idea why badblocks is reporting differently from Disk Utility. SMART data is not infallible, but does come from a different source (the drive's firmware rather than the OSes software) so a discrepancy is not out of the question.

---

### Post by allen76693 on 2012-10-29
> **Paqman said:**
> Bad blocks aren't in themselves anything to freak out about, they do just pop up as normal wear and tear. A drive that's been in use for years with a bad block or two is fine.

What is an issue is if you have lots of bad blocks, or the number is increasing. The SMART data stored in the drive logs these things, you can check that in Ubuntu using the Disk Utility tool (aka Disks in recent version). Look under the headings "Reallocated sector count", "Current Pending sectors" and "Offline Uncorrectable".

No idea why badblocks is reporting differently from Disk Utility. SMART data is not infallible, but does come from a different source (the drive's firmware rather than the OSes software) so a discrepancy is not out of the question.

Thank you so mush for the specifics as well as your being early riser and willing to share your expertise.

---

### Post by allen76693 on 2012-10-29
Disk utility has indeed opened a new vista for these old eyes and obviously learning curve. See attachments and I did run self test and not sure were report is or if that reallocated is the report. Please comment at your leisure
Allen

---

### Post by Paqman on 2012-10-29
> **allen76693 said:**
> as well as your being early riser

Hey it's lunch time here, but you're welcome!

208 bad sectors is not good. Back up your data right away, your disk is likely to completely fail at any time.

---

### Post by allen76693 on 2012-10-29
> **Paqman said:**
> Hey it's lunch time here, but you're welcome!

208 bad sectors is not good. Back up your data right away, your disk is likely to completely fail at any time.
Very fortunate you were kind enough to answer. Shipping included $70 for
exact replacement. I have put in memory so this is just 4 screws. Again thanks

---

