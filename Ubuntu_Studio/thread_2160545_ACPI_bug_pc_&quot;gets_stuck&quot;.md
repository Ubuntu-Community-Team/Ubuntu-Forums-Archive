---
title: "ACPI bug? pc &quot;gets stuck&quot;"
date: 2013-07-07
forum: Ubuntu Studio
---

### Post by spiridonios on 2013-07-07
Hallo there,
I' ve been dealing with a "stucking" problem after my new ubuntu studio installation on my new built pc, ([http://ubuntuforums.org/showthread.php?t=2158680](http://ubuntuforums.org/showthread.php?t=2158680))  and searching and asking around I ve been told that this is probably an ACPI error. I don't know how to deal with this by myself, and I love ubuntu studio, so I' m advised by [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI) here I send a bug report, hopping for some help :)

so here are the uname -a,sudo lspci -vvnn and sudo dmidecode attached in differnet files (because of the forums upload limit)

[ATTACH]244475[/ATTACH][ATTACH]244476[/ATTACH][ATTACH]244477[/ATTACH][ATTACH]244478[/ATTACH][ATTACH]244479[/ATTACH][ATTACH]244475[/ATTACH][ATTACH]244476[/ATTACH][ATTACH]244477[/ATTACH][ATTACH]244478[/ATTACH][ATTACH]244479[/ATTACH]

when i terminal the other three commands i get 

spiridonios@spiridonios-To-be-filled-by-O-E-M:~$ /var/log/kern.log.0
bash: /var/log/kern.log.0: No such file or directory
spiridonios@spiridonios-To-be-filled-by-O-E-M:~$ cp -r /proc/acpi /tmp
cp: cannot open `/proc/acpi/event' for reading: Permission denied
spiridonios@spiridonios-To-be-filled-by-O-E-M:~$ ar -cvjf ~/acpi.tar.bz /tmp/acpi
ar: invalid option -- 'j'
Usage: ar [emulation options] [-]{dmpqrstx}[abcDfilMNoPsSTuvV] [--plugin <name>] [member-name] [count] archive-file file...
       ar -M [<mri-script]
 commands:
  d            - delete file(s) from the archive
  m[ab]        - move file(s) in the archive
  p            - print file(s) found in the archive
  q[f]         - quick append file(s) to the archive
  r[ab][f][u]  - replace existing or insert new file(s) into the archive
  s            - act as ranlib
  t            - display contents of archive
  x[o]         - extract file(s) from the archive
 command specific modifiers:
  [a]          - put file(s) after [member-name]
  [b]          - put file(s) before [member-name] (same as [i])
  [D]          - use zero for timestamps and uids/gids
  [N]          - use instance [count] of name
  [f]          - truncate inserted file names
  [P]          - use full path names when matching
  [o]          - preserve original dates
  [u]          - only replace files that are newer than current archive contents
 generic modifiers:
  [c]          - do not warn if the library had to be created
  [s]          - create an archive index (cf. ranlib)
  [S]          - do not build a symbol table
  [T]          - make a thin archive
  [v]          - be verbose
  [V]          - display the version number
  @<file>      - read options from <file>
  --target=BFDNAME - specify the target object format as BFDNAME
 optional:
  --plugin <p> - load the specified plugin
 emulation options:
  No emulation specific options
ar: supported targets: elf64-x86-64 elf32-i386 elf32-x86-64 a.out-i386-linux pei-i386 pei-x86-64 elf64-l1om elf64-k1om elf64-little elf64-big elf32-little elf32-big plugin srec symbolsrec verilog tekhex binary ihex
spiridonios@spiridonios-To-be-filled-by-O-E-M:~$  /var/log/kern.log.0
bash: /var/log/kern.log.0: No such file or directory
spiridonios@spiridonios-To-be-filled-by-O-E-M:~$ cp -r /proc/acpi /tmp
cp: cannot open `/proc/acpi/event' for reading: Permission denied
spiridonios@spiridonios-To-be-filled-by-O-E-M:~$ tar -cvjf ~/acpi.tar.bz /tmp/acpi
tar: Removing leading `/' from member names
/tmp/acpi/
/tmp/acpi/battery/
/tmp/acpi/ac_adapter/
/tmp/acpi/wakeup

If you can see something through this I will be happy trying to fix the problem.
Otherwise I think I ll try to install ubuntu studio 13.04, although it is not a long term supported version and 12.04 are supposed to be more stable..

thanks for any advice in advance :)

---

### Post by spiridonios on 2013-07-09
eventually I downloaded and install ubuntu studio 13.04 and the problem seems to be solved. the machine is been working continiusly for almost 24 hours :)

---

### Post by Mr.Dunham on 2013-07-13
Thanks, good to know there's a way to solve it, I had the same problem sometime ago and gave up on it.

---

### Post by spiridonios on 2013-07-14
yeah. and to insist on hte confirmation, after 4 days everything works fine. just fine :)

---

