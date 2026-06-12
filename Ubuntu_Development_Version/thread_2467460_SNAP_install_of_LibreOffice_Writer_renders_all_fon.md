---
title: "SNAP install of LibreOffice Writer renders all fonts poorly in Wayland session"
date: 2021-09-27
forum: Ubuntu Development Version
---

### Post by rbmorse on 2021-09-27
Honestly, they look like something from Windows 3.0 with a mis-matched display configuration. Blotchy and pixelated. Only fonts within the LibreOffice window are affected, but the issue manifests with titlebars, menu items, and of course, the composition window.  Font rendering outside of the LibreOffice window appears normal. 

If I log out of the Wayland session and log back in to a Ubuntu on Xorg session, LibreOffice renders all fonts normally.  

If I remove the SNAP installation of Libreoffice and reinstall from repository with Apt, LibreOffice Writer renders fonts normally in both Wayland and Xorg sessions. 

Should I file a bug report under SNAP or Wayland?

---

### Post by VMC on 2021-09-27
Good question. I would file under snap with Wayland mentioned.

Snap is the first item I remove. Regarding LibreOffice, I'm installing minimal Ubuntu which doesn't have Office. I've recently tried Gnumeric and love it. I don't have the need for all that LibreOffice offers.

---

