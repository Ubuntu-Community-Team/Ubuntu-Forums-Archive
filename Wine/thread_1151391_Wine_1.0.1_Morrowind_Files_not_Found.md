---
title: "Wine 1.0.1: Morrowind Files not Found?"
date: 2009-05-06
forum: Wine
---

### Post by Mister LinOx on 2009-05-06
Okay. I have gotten myself a hold of a copy of Morrowind. I mounted the Morrowind.iso and placed the files in the Wine C: drive under Programs. When I go to run the setup.exe/exe;1 file, it says that iKernal.exe can not be found. It does not exist. Quite frankly, it is placed right above it. Then, I tried to do it through the autorunmorrowind.exe/exe;1, but it just prompts me by asking if I want to install The Elder Scrolls III: Morrowind. When selecting yes, the prompt exits, but returns nothing.

    I am running Wine 1.0.1 using Windows version XP on Jaunty. If you need to know anything else to help me, just say so.

                                Thank you in advanced.

EDIT AT LAST SECOND: I just remembered; the iKernel.exe file was name iKernel.ex_;1, but it didn't work then either and it was an unknown application, so i changed it to exe. Same thing. Also, all of the files have the ;1 after the file extension. I've tried removing it, but the problem still persists.

---

### Post by asdfoo on 2009-05-06
> **Mister LinOx said:**
> Okay. I have gotten myself a hold of a copy of Morrowind. I mounted the Morrowind.iso and placed the files in the Wine C: drive under Programs. When I go to run the setup.exe/exe;1 file, it says that iKernal.exe can not be found. It does not exist. Quite frankly, it is placed right above it. Then, I tried to do it through the autorunmorrowind.exe/exe;1, but it just prompts me by asking if I want to install The Elder Scrolls III: Morrowind. When selecting yes, the prompt exits, but returns nothing.

    I am running Wine 1.0.1 using Windows version XP on Jaunty. If you need to know anything else to help me, just say so.

                                Thank you in advanced.

EDIT AT LAST SECOND: I just remembered; the iKernel.exe file was name iKernel.ex_;1, but it didn't work then either and it was an unknown application, so i changed it to exe. Same thing. Also, all of the files have the ;1 after the file extension. I've tried removing it, but the problem still persists.

Upgrade to 1.1.20 [http://winehq.org/download](http://winehq.org/download) and try again

---

### Post by Mister LinOx on 2009-05-07
> **asdfoo said:**
> Upgrade to 1.1.20 [http://winehq.org/download](http://winehq.org/download) and try again

The problem still persists.

---

### Post by Mister LinOx on 2009-05-08
I can't really seem to find how other people have fixed this.

---

### Post by NightMKoder on 2009-05-08
Since you mounted the ISO make sure it shows up in the wine drives tab AS a cd-rom drive. It may be checking that.

---

### Post by Mister LinOx on 2009-05-08
> **NightMKoder said:**
> Since you mounted the ISO make sure it shows up in the wine drives tab AS a cd-rom drive. It may be checking that.

How can I check and see if it is? I mounted the iso to my desktop using archive mounter, but I also just extracted the files and folders into a folder name morrowind in the Programs folder. Both do the things mentioned above.

---

### Post by NightMKoder on 2009-05-08
When you mount the ISO, open winecfg and go to the drives tab.

---

### Post by Mister LinOx on 2009-05-08
> **NightMKoder said:**
> When you mount the ISO, open winecfg and go to the drives tab.

It must not be recognized then. Do I just select the "+ADD" button to search for the mounted iso?

---

### Post by Progressive on 2009-05-09
There is an auto-detect button in the drives tab of winecfg which usually works. Otherwise, you will need to manually add it by linking E: to /mnt/iso or wherever you mounted it to.

---

