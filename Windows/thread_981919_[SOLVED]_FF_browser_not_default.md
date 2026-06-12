---
title: "[SOLVED] FF browser not default??"
date: 2008-11-14
forum: Windows
---

### Post by Yezinki on 2008-11-14
Hello every one,

Am using a dual boot of Vista & Ubuntu 8.10.

In Vista, despite that I have set FF as my default browser, each time I get a mail etc instead of FF IE starts up?

How can I set FF as permanent & not let IE to start?

Hoping to hear,

Regards,

Yezinki.

---

### Post by Majorix on 2008-11-14
Certain Windows apps (mainly those coming from MS) directly run IE instead of asking the OS for the default browser. Live Messenger is an example, also Outlook does it too I think. I don't know if a fix exists.

---

### Post by mjwhitfield on 2008-11-14
> **Yezinki said:**
> How can I set FF as permanent & not let IE to start?Format, install Ubuntu.

FIXED!

---

### Post by Majorix on 2008-11-14
There is no necessity to push Ubuntu up his throat at the moment, this is the **Other OS'es** section.

---

### Post by bapoumba on 2008-11-14
Moved to the Windows Discussions.

---

### Post by Giant Speck on 2008-11-14
From Mozilla's Firefox support page:

> *If after using Firefox to set the default browser you still experience one or more of the symptoms above, you can try to use your operating system to set the system default browser.*

[SIZE="5"]**[COLOR="DarkOrchid"]Windows Vista[/COLOR]**[/SIZE]

   1. Click the Start button, then click the **Default Programs** item.
   2. Click on the **Set Program Access** and **Computer Defaults** item.
   3. In the **Access and Defaults** window, click on the **Custom** radio button to expand the **Custom** category.
   4. Underneath **Choose a default Web browser** click the radio button next to **Mozilla Firefox**.
   5. Click **OK** at the bottom of the window. 

[COLOR="DarkOrchid"][SIZE="5"]**Windows XP**[/SIZE][/COLOR]

   1. Click the Start button, then click on the **Control Panel** icon to open the **Windows Control Panel**.
   2. Click the **Add or Remove Programs** icon to open the **Add or Remove Programs** applet.
   3. On the left side of the Window click the **Set Program Access and Defaults** icon.
   4. In the **Access and Defaults** window, click on the **Custom** radio button to expand the **Custom** category.
   5. Underneath **Choose a default Web browser** click the radio button next to **Mozilla Firefox.**
   6. Click OK at the bottom of the window. 
[COLOR="DarkOrchid"][B][SIZE="4"]
Manually set File Types (Windows XP)[/SIZE][/B][/COLOR]

If links from programs like Outlook fail to open in Firefox, you can try to set the file handling options manually.

   1. Open **Windows Explorer**
   2. In the menu bar, click **Tools** > **Folder Options**...
   3. Click the **File Types** tab
   4. Find **(NONE) URL:Hyper Text Transfer Protocol**, click it, and then click **Advanced**.
   5. Click the open action and click the **Edit**.
   6. Fill in the fields with this information:
         [INDENT] * Action: **open**
          * Application used to perform action: **"C:\Program Files\Mozilla Firefox\firefox.exe" -requestPending -osint -url "%1" **(Assumng you installed Firefox to the default location. If not, use your own path, surrounded by quotation marks)
          * Use DDE: **Checked**
          * DDE Message: **"%1",,0,0,,,,**
          * Application: **Firefox**
          * Topic: **WWW_OpenURL**[/INDENT]


Repeat steps 5 and 6 for the **(NONE) URL:Hyper Text Transfer Protocol with Privacy** option.

---

### Post by Yezinki on 2008-11-18
> **Giant Speck said:**
> From Mozilla's Firefox support page:


It becomes Yahoo's default browser but not MSN's, whether in XP or Vista!

Regards,

Yezinki.

---

### Post by donkyhotay on 2008-11-20
As mentioned previously this is because some programs are hardcoded to use IE rather then use the OS's default browser like most programs do. The only way to fix this is to modify the source code for those programs, unfortunately when dealing with non-OSS software...

---

