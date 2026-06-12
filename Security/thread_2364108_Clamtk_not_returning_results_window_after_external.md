---
title: "Clamtk not returning results window after external hdd scan"
date: 2017-06-19
forum: Security
---

### Post by vstamatakos on 2017-06-19
Dear all,
Good day.

I just installed ubuntu 16.04.02 LTS and after that I installed clamav, updated it, installed clamtk and then connected an external hdd and scanned it. The scan found a lot of possible virus, but after closing the scan window, no results window popped up. Therefore i cannot see which are these files, nor quarantine or delete them.

Please assist.
Thank you

Vasilis

---

### Post by howefield on 2017-06-19
Have a look in the clamav History option..

Or run the scan specifying a log be created with the -l option eg.

```
clamscan -l ~/Documents/clamav.log ~/
```

---

### Post by vstamatakos on 2017-06-19
Clamav history is empty...

---

### Post by howefield on 2017-06-19
> **vstamatakos said:**
> Clamav history is empty...

Then run again using the option to produce a log file.

---

### Post by deadflowr on 2017-06-19
clamtk keeps a history log among other settings in the folder ~/.clamtk.
.clamtk is a hidden folder so you need to press ctrl + H to set it to view hidden files and folders in Ubuntu's File Manager.

---

### Post by vstamatakos on 2017-06-20
> **deadflowr said:**
> clamtk keeps a history log among other settings in the folder ~/.clamtk.
.clamtk is a hidden folder so you need to press ctrl + H to set it to view hidden files and folders in Ubuntu's File Manager.

History folder inside .clamtk is empty.

---

### Post by vstamatakos on 2017-07-10
Any follow-up on the above?

Thank you.

---

### Post by vstamatakos on 2017-07-17
Dear all fyi,

After thorough investigation and some out of the box thinking, I found out that the problem was a different system language in Ubuntu OS, which means I opened language support, installed English U.S. language and applied it in all system and BOOM. After that Clamtk properly shows results after scan.

Although now, I have a different query. When I delete or quarantine a threat with clamtk, it is not actually deleted or quarantined and when i manually delete it it goes into an invisible Trash folder.

Can you help on this??

Thank you in advance.

Best regards,

V. Stamatakos

---

