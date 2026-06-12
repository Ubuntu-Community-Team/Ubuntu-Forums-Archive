---
title: "XLS to PDF in command line (or PHP) ?"
date: 2010-07-08
forum: Server Platforms
---

### Post by Saorex on 2010-07-08
Hello.

I'm looking for a way to automatically convert XLS and XLSX files to PDF when uploaded through a Web interface by users. I will probably use phplivedocx for DOC and DOCX files, but I haven't found any library for Excel files.

I may use PHP to call a some printing command to make the conversion, but I've never tried that on a server (which obviously) doesn't have Open Office installed (meaning no PDF printer driver I guess).

Any ideas anyone? Thanks a lot for your time and help.

---

### Post by zabuch on 2010-07-10
You can use Open Office for it - even if the server has no xserver running. You can run OO as a (service) daemon and use it for conversion - for both DOC/DOCX and XLS files. See [http://www.linux.com/archive/feed/61713](http://www.linux.com/archive/feed/61713) for details.
You don't even need to install OO from the package - I have downloaded newest OO and simply unpacked it in a directory to get it up & running.

cheers,
Tomek [http://techblog.zabuchy.net](http://techblog.zabuchy.net)

---

### Post by redfox1160 on 2010-07-10
if you can convert it to a post script file, you could use ps2pdf (im not sure if you can convert xls to ps, I just remember reading about ps2pdf before).

---

### Post by Saorex on 2010-07-12
Thank you guys. I'll look at both solutions during the week. I fear some MS Office 2007 documents may not print perfectly using OO. I'll see... Nobody works with OO here, and all users are slowly upgraded to Office 2007. But I'd really like to automate the process explained in my first post. Otherwise some users will have to create PDF versions of all files... #-o

---

