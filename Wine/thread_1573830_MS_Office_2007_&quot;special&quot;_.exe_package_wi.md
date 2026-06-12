---
title: "MS Office 2007 &quot;special&quot; .exe package wine will not read"
date: 2010-09-13
forum: Wine
---

### Post by agm. on 2010-09-13
Hi,

My university offers a free download of MS Office 2007 for all students and faculty, but the file that is downloaded is not a "traditional" installation package for MS Office.  Instead, it is a special .exe file that unpacks everything and when I have tried to "install" it via Wine, it will not run.

Wine goes through the extraction process, but then after it has unpacked everything out of the .exe I get an error.  As an example, it extracts the following lines (not all inclusive):  

```
Extracting Office 2007 Enterprise SP2\InfoPath.en-us
Extracting Office 2007 Enterprise SP2\Office.en-us
Extracting Office 2007 Enterprise SP2\Office64.en-us
Extracting Office 2007 Enterprise SP2\OneNote.en-us
Extracting Office 2007 Enterprise SP2\Outlook.en-us
Extracting Office 2007 Enterprise SP2\plug-ins
Extracting Office 2007 Enterprise SP2\PowerPoint.en-us
Extracting Office 2007 Enterprise SP2\Proofing.en-us
```

After everything is unpacked, and the installation bar reports 100%, Wine gives the following error:

"There is no Windows program configured to open this type of file."

If it matters, it goes to the Wine folder: C:\Windows\cuinst.

Thanks for any help!

---

### Post by beew on 2010-09-13
[http://appdb.winehq.org/appview.php?iVersionId=4992](http://appdb.winehq.org/appview.php?iVersionId=4992)

BTW, this is just for installation, not functionalities.

**Edited: **You may want to make sure you have the same version of WINE, what works for one version may not work for another.

---

### Post by Elfy on 2010-09-13
moved to wine

---

### Post by agm. on 2010-09-13
> **beew said:**
> [http://appdb.winehq.org/appview.php?iVersionId=4992](http://appdb.winehq.org/appview.php?iVersionId=4992)

BTW, this is just for installation, not functionalities.

Yeah, I've seen that page and looked at it, but I am not sure how it applies when I don't have a "setup.exe" file.  Wine tries to do all of the stuff that this page shows, but I get the error described in my first post.

Could you clarify how I am supposed to fix this or what exactly you meant for me to see on that page that would fix my problem?

Thanks.

PS Have the version of Wine in from the 10.04 repos... 1.1.42

---

### Post by beew on 2010-09-13
It appears that you need wine 1.30 from the link. You can get it by setting up a wine ppa, go to their home page > downloads and they have the instructions for Ubuntu.

**Edited:** If you don't have a .exe file how are you supposed to set up office in windows? I am afraid I don't get it.

---

