---
title: "Thunderbird inconsistent in opening attachments (.pdf .doc etc)"
date: 2010-03-30
forum: Ubuntuzilla
---

### Post by weiersc on 2010-03-30
Hi

This has been bothering me since I installed the first mozilla build of Thunderbird 3.

I frequently receive e-mails with a .pdf attachment.

Sometimes I can right-click on the attachment and ask Thunderbird to open it. It then identifies Adobe Acrobat as the associated programme and asks me if it can open it with the reader.

Other times it does not do that. It does not identify the reader and only gives me the option to save the file. Once I've saved the file I need to navigate to the file and open it independently.

I cannot work out why it will do this with some .pdf files and not with others.

This sometimes happens with .doc files that would usually automatically open in OpenOffice.org.

I don't know how to fix this. Am I just going mad? Or are others experiencing the same issues?

---

### Post by mankygitt on 2010-04-02
I have the same issue, and also have not yet found an explanation that works.

I have a Dell Inspiron running 9.10 with Thunderbird 2.0.0.24 with Adobe Acrobat Reader installed. I also have Clamav installed.
Some emails with a PDF attachment have an icon that associates them with Adobe Reader, and others do not. There is no consistent difference in the file name convention. Some files have spaces, some are long file names (20 characters), but consistently they all have a lowercase .pdf extension.
It seems quite random that some are correctly identified. Others provide only the option to open with Virus Scanner, or save to file system.

If I save them to the file system and then double-click them they open fine.

Does anyone have a good explanation as to why some files work and others do not.

Thanks

---

### Post by roberthr on 2010-05-03
Same here. And it's the same with Lucid!!! It's driving me crazy.

---

### Post by nanotube on 2010-05-03
Seems like a problem with thunderbird itself. You'll probably have better luck asking on the mozilla forums directly.

---

### Post by boyevil on 2010-05-06
[SOLVED] (for Thunderbird 3.0)

Download Gnome open here: [https://addons.mozilla.org/en-US/thunderbird/addon/12523](https://addons.mozilla.org/en-US/thunderbird/addon/12523)

Restart Thunderbird and install that add on from Tools>Add-ons

Bigity, Boom

---

### Post by darwinev0lved on 2010-05-10
Just wanted to say Gnome Open - what a time and hair saver! Brilliant stuff.

---

### Post by zasq on 2010-05-10
Thanks for the hint with the gnome-open-addon. But it's still unbelievable that such a basic function won't work in TB 3 (it seems to be a problem in all platforms, not only linux). Of course.

---

### Post by scottvance on 2010-06-27
I found [this thread]("http://ubuntuforums.org/showthread.php?t=329767") from 2007 that talks about the same problem.  It says that Thunderbird will only open attachments with the default application if  the file extension is in upper case.  I tried it out by sending myself two .pdf files, one with an upper case extension and one with a lower case extension.  Sure enough, the upper case one opens with the default viewer while the only choice for the lower case one is to save it.

Seems to be a very old problem that still doesn't have a solution.

---

### Post by virtual_najac on 2010-07-07
I hope it's not to late, here is how it worked for me.

The trouble is that some mail programs send attachments with a nonspecific content type: "application/octet-stream  or application/x-msdownload" instead of "Content-Type: application/pdf" (see message source with Crtl-U without opening the email).

To work around this, send yourself an e-mail to which you manually attached the pdf file (do not just forward the email whose attachment caused  the box to be disabled.) Then open the attachment and choose how you  want Thunderbird to open it. Check the box "Do this automatically for  files like this from now on".

After that go to menu /Edit/Preferences/attachments and you'll find an attachment-handling action for PDF documents associated to "Documents Viewer (Default). Just change this association (choose "Use other...") and choose /usr/bin/evince.

That's all

---

### Post by luvallcomputers on 2011-09-20
I fixed TB by making a pdf document out of office and then renaming it to have PDF as the extension.

I sent the file to myself.  I clicked to open it and it ask what to open with so went to /usr/bin/okular (I had to click on the name column to sort by name.)  I found the okular and clicked on it to open the file.  I then looked at TB edit preferences and attachments and the pdf was back and using okular to open.  I had deleted the pdf file that was in the preference box to begin with it was set to open pdf with gimp.

---

### Post by bobjohnbowles on 2012-04-23
This problem is caused by issues with TB's default settings. Please see this thread for more details: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/220991](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/220991)

---

