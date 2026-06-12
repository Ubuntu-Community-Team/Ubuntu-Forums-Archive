---
title: "wine and exam view"
date: 2009-03-06
forum: Wine
---

### Post by rick71 on 2009-03-06
Has anyone had success using Exam View Pro under Wine?

I have used it successfully under PCLinuxOS and Opensuse, but under Intrepid menus (File, Edit, etc) do not appear, and some text is missing from dialog boxes.

Any info appreciated.

---

### Post by rick71 on 2009-03-18
I reloaded Ubuntu a few times, and IIRC, the problem I had was on 8.10, though I am not sure it was an 8.10 dependent problem. I am now using 8.04, and I have loaded the MS core TT fonts. Exam view is again running well under Wine.

---

### Post by wangsuda on 2009-03-18
> **rick71 said:**
> Has anyone had success using Exam View Pro under Wine?

I have used it successfully under PCLinuxOS and Opensuse, but under Intrepid menus (File, Edit, etc) do not appear, and some text is missing from dialog boxes.

Any info appreciated.
Here's the info you requested. I use ExamView Pro to make math tests, so I understand what you are going through.
 
If you run a dual boot system, copy the fonts folder from the Windows file on your C drive. Put it somewhere where Ubuntu can find it. If you don't have a dual boot system, then download the Microsoft fonts [here]("http://www.mediafire.com/?dgnyqd4ctvh"). Once you have the fonts folder, go to applications>wine>Browse C:\ Drive. Open the folder marked "windows" and then open the folder called "Fonts." Paste the fonts from the downloaded fonts file (or the one you got from your copy of Windows) into the "Fonts" folder. Close everything up and reboot. Should work like a charm after that.

---

### Post by wangsuda on 2009-03-18
Forgot to add:

If you create a folder in your Home Folder called ".fonts" (without the quotation marks) and paste all the Microsoft fonts in there, then OpenOffice can use them too!

---

### Post by rick71 on 2009-03-19
Thanks, but as I posted.. I've got Exam View running OK after installing the fonts.

---

### Post by nlmaster on 2009-11-08
Thanks, I've been thinking about making a complete switch from MS to Ubuntu but was a bit reluctant because of how much I use examview. This makes my decision easier for sure.

---

### Post by rick71 on 2009-11-09
> **nlmaster said:**
> Thanks, I've been thinking about making a complete switch from MS to Ubuntu but was a bit reluctant because of how much I use examview. This makes my decision easier for sure.

I use Exam View for all of my tests. I give the kids hard copy, but they take the test online. My only problem is that I can't yet figure out how to get the test collated when printing multiple copies. They collate when running under Windows. Ah, well.

---

### Post by wangsuda on 2009-11-09
> **rick71 said:**
> I use Exam View for all of my tests. I give the kids hard copy, but they take the test online. My only problem is that I can't yet figure out how to get the test collated when printing multiple copies. They collate when running under Windows. Ah, well.
I understand your frustration. As you can see by the attached screenshot, the collate function is there, I am just not allowed to use it. I haven't figured out a way around this - unless you print to PDF and then hardcopy the PDF.

---

### Post by rick71 on 2009-11-11
> **wangsuda said:**
> I understand your frustration. As you can see by the attached screenshot, the collate function is there, I am just not allowed to use it. I haven't figured out a way around this - unless you print to PDF and then hardcopy the PDF.

I think the reason the collate function isn't available in your screenshot is that you only have one copy selected for printing.

I'll have to take a look at some other apps run under Wine and see if they can collate. It might be a Wine bug, or an ExamView bug.

---

