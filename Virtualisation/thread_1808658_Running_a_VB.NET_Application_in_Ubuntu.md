---
title: "Running a VB.NET Application in Ubuntu"
date: 2011-07-20
forum: Virtualisation
---

### Post by styounes on 2011-07-20
Please forgive my ignorance if I am going about this wrong way.  I have written and published an application using Visual Basic Express 2010 in Windows.  Therefore, I now have a folder which contains all of the configuration files, user settings, etc. and a single executable: setup.exe.  In order to install this application on a Windows computer you simply run setup.exe which sets up all of the .NET APIs that my application needs.  Is there a way to install this application in Ubuntu using some sort of emulation software?  I do not want to re-code the entire application under Mono-Development.  Thank you!

---

### Post by An Sanct on 2011-07-21
If the install checks for .net compatibility and then installs the missing parts, then just run it with wine and follow the installation procedure.

---

### Post by directhex on 2011-07-21
> **styounes said:**
> Please forgive my ignorance if I am going about this wrong way.  I have written and published an application using Visual Basic Express 2010 in Windows.  Therefore, I now have a folder which contains all of the configuration files, user settings, etc. and a single executable: setup.exe.  In order to install this application on a Windows computer you simply run setup.exe which sets up all of the .NET APIs that my application needs.  Is there a way to install this application in Ubuntu using some sort of emulation software?  I do not want to re-code the entire application under Mono-Development.  Thank you!

Don't use an installer. That ties you into using Wine for installation, if it even agrees to install via Wine.

Just ship your assemblies etc in a zip file, and run with "mono foo.exe" - if you're missing things like Microsoft.VisualBasic.dll, install from apt.

---

