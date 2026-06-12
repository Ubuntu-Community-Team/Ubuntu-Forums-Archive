---
title: "MS-DOS copy command question"
date: 2006-11-10
forum: Windows
---

### Post by K.Mandla on 2006-11-10
I could've sworn there was an MS-DOS command that copies from a directory *and* its subdirectories, but all the help pages I find for copy and xcopy say nothing about that.

Basically I want to run a batch file that screens through a directory and its subdirectories for a certain pattern match, and copies them to another directory elsewhere on the network. I don't want the actual tree, just the files that were in those subdirectories, lumped into a new location.

Something like ...

```
xcopy /S *1026*.tif Z:\Daily
```
except that doesn't work. The /S switch doesn't seem to be what I thought it was; it creates subdirectories when I try it.

Anybody remember this? Or did I dream it? :confused:

---

### Post by evilghost on 2006-11-10
XCopy is going to preserve the directory structure.  Try the below code.

```

DIR /S /B *1026* > TMP.DIR
FOR /F %F IN (TMP.DIR) DO COPY %F Z:\DAILY

```

> 
Copies files and directory trees.

XCOPY source [destination] [/A | /M] [/D[:date]] [/P] [/S [/E]] [/V] [/W]
                           [/C] [/I] [/Q] [/F] [/L] [/G] [/H] [/R] [/T] [/U]
                           [/K] [/N] [/O] [/X] [/Y] [/-Y] [/Z]
                           [/EXCLUDE:file1[+file2][+file3]...]

  source       Specifies the file(s) to copy.
  destination  Specifies the location and/or name of new files.
  /A           Copies only files with the archive attribute set,
               doesn't change the attribute.
  /M           Copies only files with the archive attribute set,
               turns off the archive attribute.
  /D:m-d-y     Copies files changed on or after the specified date.
               If no date is given, copies only those files whose
               source time is newer than the destination time.
  /EXCLUDE:file1[+file2][+file3]...
               Specifies a list of files containing strings.  Each string
               should be in a separate line in the files.  When any of the
               strings match any part of the absolute path of the file to be
               copied, that file will be excluded from being copied.  For
               example, specifying a string like \obj\ or .obj will exclude
               all files underneath the directory obj or all files with the
               .obj extension respectively.
  /P           Prompts you before creating each destination file.
  /S           Copies directories and subdirectories except empty ones.
  /E           Copies directories and subdirectories, including empty ones.
               Same as /S /E. May be used to modify /T.
  /V           Verifies each new file.
  /W           Prompts you to press a key before copying.
  /C           Continues copying even if errors occur.
  /I           If destination does not exist and copying more than one file,
               assumes that destination must be a directory.
  /Q           Does not display file names while copying.
  /F           Displays full source and destination file names while copying.
  /L           Displays files that would be copied.
  /G           Allows the copying of encrypted files to destination that does
               not support encryption.
  /H           Copies hidden and system files also.
  /R           Overwrites read-only files.
  /T           Creates directory structure, but does not copy files. Does not
               include empty directories or subdirectories. /T /E includes
               empty directories and subdirectories.
  /U           Copies only files that already exist in destination.
  /K           Copies attributes. Normal Xcopy will reset read-only attributes.
  /N           Copies using the generated short names.
  /O           Copies file ownership and ACL information.
  /X           Copies file audit settings (implies /O).
  /Y           Suppresses prompting to confirm you want to overwrite an
               existing destination file.
  /-Y          Causes prompting to confirm you want to overwrite an
               existing destination file.
  /Z           Copies networked files in restartable mode.

The switch /Y may be preset in the COPYCMD environment variable.
This may be overridden with /-Y on the command line.


---

### Post by K.Mandla on 2006-11-11
> **evilghost said:**
> ```

DIR /S /B *1026* > TMP.DIR
FOR /F %F IN (TMP.DIR) DO COPY %F Z:\DAILY

```
Perfect! :mrgreen: Thanks.

I must have been working with some sort of extended DOS shell or something, because I'm 99 44/100 percent sure we used some sort of copy command that worked through subdirectories too.

Cheers! :biggrin:

---

### Post by evilghost on 2006-11-11
Glad to have helped :)

---

### Post by jimartin8219 on 2008-12-09
> **K.Mandla said:**
> I could've sworn there was an MS-DOS command that copies from a directory *and* its subdirectories, but all the help pages I find for copy and xcopy say nothing about that.

Basically I want to run a batch file that screens through a directory and its subdirectories for a certain pattern match, and copies them to another directory elsewhere on the network. I don't want the actual tree, just the files that were in those subdirectories, lumped into a new location.

Something like ...

```
xcopy /S *1026*.tif Z:\Daily
```
except that doesn't work. The /S switch doesn't seem to be what I thought it was; it creates subdirectories when I try it.

Anybody remember this? Or did I dream it? :confused:


Put the /S at the end of the command:
Xcopy "*1026*.tif" "Z:\Daily" /S

---

### Post by fubbleskag on 2008-12-09
> **K.Mandla said:**
> Perfect! :mrgreen: Thanks.

I must have been working with some sort of extended DOS shell or something, because I'm 99 44/100 percent **pure** we used some sort of copy command that worked through subdirectories too.

Cheers! :biggrin:
fixed :P

---

