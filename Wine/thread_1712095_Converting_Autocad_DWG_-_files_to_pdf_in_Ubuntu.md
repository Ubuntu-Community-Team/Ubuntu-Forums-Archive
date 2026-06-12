---
title: "Converting Autocad DWG - files to pdf in Ubuntu"
date: 2011-03-22
forum: Wine
---

### Post by Mikael Hartzell on 2011-03-22
I have some old Autocad drawings in .dwg - format and I struggled to get them converted to pdf.

Here is the solution I found :p

The last steps (8->) may be done alternatively in Ubuntu, OS X or windows.

Ubuntu
----------
1. Install **wine 1.2**
2. Download **lx-viewer for windows** (works with wine 1.2 on Ubuntu 10.10) from here: [http://sourceforge.net/projects/lx-viewer/files/LX-Viewer/Experimnt.%200.99e%20Windows/]("http://sourceforge.net/projects/lx-viewer/files/LX-Viewer/Experimnt.%200.99e%20Windows/")
3. RightClick lx-viewer.exe choose "**Properties**", from the "**Permissions Tab**", tick "**Allow executing file as program**", click "**Close**".
4. RightClick lw-viewer.exe, choose "**Open with wine windows program loader**" 
5. Click through the install process
5. Open dwg files one by one in lx-viewer and save to dxf
6. Import dxf - files to Google Docs (allow conversion to Google Docs format).
7. View file in Google Docs and select "**FILE / PRINT (PDF)**".

Ubuntu
----------
8. A Print - dialog opens, select "**PRINT TO FILE**". Select the file and folder to save to, check that the selected save format is PDF and click "**PRINT**". 

OS X 10.6
-------------
8. A Print dialog opens, klick "**PREVIEW**". The file open in OS X Preview - program.
9. If the image is not correctly aligned on the page, crop and rotate it. 
10. Select "**FILE / PRINT**" from the Preview - program.
11. Choose the correct paper size, zoom to fit and orientation.
12. From the Print - dialogs left bottom corner click "**PDF / SAVE AS PDF**".

windows
----------
8. If you have Adobe Reader installed, the file opens in it, save the file to pdf.

---

### Post by howefield on 2011-03-23
Moved to *Wine* forum.

---

