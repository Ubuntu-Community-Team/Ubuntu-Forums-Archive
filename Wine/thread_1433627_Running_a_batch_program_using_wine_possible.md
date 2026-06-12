---
title: "Running a batch program using wine possible?"
date: 2010-03-19
forum: Wine
---

### Post by thianpa on 2010-03-19
Hi,

 I have this batch program which i use to run using WIndows. Now as I have my VPS which is using Ubuntu. I want to know if this program .bat can run using Wine. The program also use winrar which runs fine with Wine. If its not possible I would really like to know how? I think shell programming cansolve it but i dont know how.. Here's the program code of the batch file.

```
c:
set SOURCEDIR="Documents and Settings\Administrator\My Documents\Downloads"
set DESTINATION=c:\info\
set INFO=info.txt
set html1="c:\Mizo i nih chuan mizoblog.com.url"
set html2="c:\Mizo te tan at mizowalla.org.url"
set WINRAR="c:\Program Files\WinRAR\WinRAR.exe"
set FILETYPE=wmv
set FILETYPE2=avi
set SIZE=209715200
set WINRARCODE=%WINRAR% a -u -r
cd %SOURCEDIR%
for %%i in (*.%FILETYPE% *.%FILETYPE2%) do %WINRARCODE% -zc:\info\info.txt -m0 -v%SIZE%b %DESTINATION%%%~ni.rar %html1% %html2% %%i


```

---

### Post by asdfoo on 2010-03-19
> **thianpa said:**
> Hi,

 I have this batch program which i use to run using WIndows. Now as I have my VPS which is using Ubuntu. I want to know if this program .bat can run using Wine. The program also use winrar which runs fine with Wine. If its not possible I would really like to know how? I think shell programming cansolve it but i dont know how.. Here's the program code of the batch file.

```
c:
set SOURCEDIR="Documents and Settings\Administrator\My Documents\Downloads"
set DESTINATION=c:\info\
set INFO=info.txt
set html1="c:\Mizo i nih chuan mizoblog.com.url"
set html2="c:\Mizo te tan at mizowalla.org.url"
set WINRAR="c:\Program Files\WinRAR\WinRAR.exe"
set FILETYPE=wmv
set FILETYPE2=avi
set SIZE=209715200
set WINRARCODE=%WINRAR% a -u -r
cd %SOURCEDIR%
for %%i in (*.%FILETYPE% *.%FILETYPE2%) do %WINRARCODE% -zc:\info\info.txt -m0 -v%SIZE%b %DESTINATION%%%~ni.rar %html1% %html2% %%i


```

it's possible, it works the same as in windows, bat files are run by cmd.exe

I suggest you test it on your local system before doing it on your vps.  Wine's cmd.exe is not bug free.

---

