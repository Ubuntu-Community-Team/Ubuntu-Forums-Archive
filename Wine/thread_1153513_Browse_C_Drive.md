---
title: "Browse C:\ Drive"
date: 2009-05-08
forum: Wine
---

### Post by connorh123 on 2009-05-08
Hey guys, I'm using Jaunty and I recently tried to download Americas Army. Well it saved into my Program files into the C Drive. When I try to browse the drive, it won't let me. I click it, and nothing happens! Does anyone else have any idea what to do?

---

### Post by Kareeser on 2009-05-08
Browse to ~/.wine/drive_c using the terminal. Type "ls" to bring up a directory listing. What do you see?

It sounds like the menu command has broken somehow. Have you tried rebooting?

---

### Post by connorh123 on 2009-05-08
connor@connor-laptop:~$ ls
Chapter 17 Work for Science.odt               msipatch.txt
Chapter 28 Vocabulary for Social Studies.odt  Music
Chapter 9 Work for Science.odt                %MYDOCS%
clip0001.avi                                  Pictures
clip0001.avi.bak                              player
clip0002.avi                                  plugin_stack.trace
clip0002.avi.bak                              Poem for Thomas.odt
clip0003.avi                                  Public
clip0003.avi.bak                              pulseaudio
clip0004.avi                                  TeamSpeak2RC2
clip0004.avi.bak                              tempdecal.wad
clip0005.avi                                  Templates
clip0005.avi.bak                              ubuntu-8.04.2-desktop-i386.iso
CS                                            vcsbasic60.exe
Desktop                                       ventrilo
D:\\Games\\Urban Terror\\.                    Videos
Documents                                     wine
DVDVideoSoft                                  winetricks
Examples                                      winetricks.1

---

### Post by cogadh on 2009-05-08
Open the file browser and press CTRL+H to unhide directories and files. Look for a directory labeled ".wine". Within that directory you will find a directory labeled "drive_c". That is your Wine "C:" drive.

---

### Post by connorh123 on 2009-05-09
> **cogadh said:**
> Open the file browser and press CTRL+H to unhide directories and files. Look for a directory labeled ".wine". Within that directory you will find a directory labeled "drive_c". That is your Wine "C:" drive.

Thank you very much :)

---

