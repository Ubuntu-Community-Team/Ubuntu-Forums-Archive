---
title: "Server Side software"
date: 2015-07-28
forum: Server Platforms
---

### Post by Carl_Leatherbarrow on 2015-07-28
hi all, 
I am new to unbuntu server. i have a headless ubuntu 14.04 server running. is there any way of running native linux software on the server server-side (eg libre office) and using it on a windows client. I didn't want to install a windows equivalent on the windows machine, just use windows like a monitor. 

thanks carl

---

### Post by PaulW2U on 2015-07-28
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2015-07-28
That's pretty complicated.  How about using Samba to export some directories on the server that you can open in Windows?
[https://help.ubuntu.com/14.04/serverguide/samba.html](https://help.ubuntu.com/14.04/serverguide/samba.html)

---

### Post by LHammonds on 2015-07-28
> **Carl_Leatherbarrow said:**
> is there any way of running native linux software on the server server-side (eg libre office) and using it on a windows client.
I believe so.  I'm not familiar with that option though because I use Citrix/XenApp.  A quick searched turned up these options:

[http://wiki.x2go.org/doku.php](http://wiki.x2go.org/doku.php)
[http://www.ltsp.org/](http://www.ltsp.org/)
[http://sourceforge.net/projects/freenx.berlios/](http://sourceforge.net/projects/freenx.berlios/)
[http://www.2x.com/](http://www.2x.com/)
[https://www.nomachine.com/](https://www.nomachine.com/)
[https://www.cendio.com/thinlinc/what-is-thinlinc](https://www.cendio.com/thinlinc/what-is-thinlinc)
[https://www.teamviewer.com/en/index.aspx](https://www.teamviewer.com/en/index.aspx)
[http://tigervnc.org/](http://tigervnc.org/)
[https://wiki.gnome.org/Apps/Vinagre](https://wiki.gnome.org/Apps/Vinagre)

> **Carl_Leatherbarrow said:**
> I didn't want to install a windows equivalent on the windows machine, just use windows like a monitor.Technically speaking, you don't have to "install" LibreOffice if you use the [Portable Edition]("http://portableapps.com/apps/office/libreoffice_portable").  However, it would run on the Windows machine (compiled for Windows) and you'd have to expose your Ubuntu Server using Samba if you wanted to keep the files stored on Ubuntu.

LHammonds

---

### Post by mastablasta on 2015-07-30
install owncloud
therein you can edit documents in libre office (like your personal google docs). for this kind of thing owncloud is actually a great tool.

I think it's Explained on this site: [https://doc.owncloud.org/server/7.0/admin_manual/configuration/collaborative_documents_configuration.html](https://doc.owncloud.org/server/7.0/admin_manual/configuration/collaborative_documents_configuration.html)

sorry as I can't be sure. I am at work and owncloud is blocked here (file storage access denied).

---

### Post by LHammonds on 2015-07-30
> **mastablasta said:**
> therein you can edit documents in libre officeCorrection, you can only edit .odt (Writer/OpenDocumentText) documents in ownCloud with the built-in editor.  Not the spreadsheets or other applications.

---

### Post by lukeiamyourfather on 2015-08-01
Use SSH to connect to the Linux server and use X tunneling to render the GUI on the client. Cygwin has an X server that can handle this. Though some GUI elements might be rendered funky. VNC or some other full screen remote desktop utility might be better. X2Go isn't bad if you don't want to do X tunneling via SSH.

[http://wiki.x2go.org/doku.php](http://wiki.x2go.org/doku.php)

---

