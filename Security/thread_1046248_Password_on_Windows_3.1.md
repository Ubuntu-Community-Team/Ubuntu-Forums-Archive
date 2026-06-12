---
title: "Password on Windows 3.1"
date: 2009-01-21
forum: Security
---

### Post by txwooley on 2009-01-21
I have an old Windows 3.1 comp in my closet that I haven't thrown out because my wife used to write short stories on it and can't remember the password she used to save the stories.  The system itself is not locked, but the files with the stories is.  I have been looking for a password crack program, but everything is too fancy.  I don't need something sophisticated like Ophcrack or rainbow crack.  I'm not interested in breaking into new more secure machines.  Can anyone tell me how to go about recovering this password?  My wife says it's a simple one word no numbers or characters that PROBABLY doesn't have any capital letters.  Also, I don't think I can run a program on that machine as it only has a 3.5 floppy drive (pre-USB and CD-ROM), and a tiny hard drive.

---

### Post by Tomatz on 2009-01-21
> **txwooley said:**
> I have an old Windows 3.1 comp in my closet that I haven't thrown out because my wife used to write short stories on it and can't remember the password she used to save the stories.  The system itself is not locked, but the files with the stories is.  I have been looking for a password crack program, but everything is too fancy.  I don't need something sophisticated like Ophcrack or rainbow crack.  I'm not interested in breaking into new more secure machines.  Can anyone tell me how to go about recovering this password?  My wife says it's a simple one word no numbers or characters that PROBABLY doesn't have any capital letters.  Also, I don't think I can run a program on that machine as it only has a 3.5 floppy drive (pre-USB and CD-ROM), and a tiny hard drive.

You could remove the HDD and mount it in your main pc and get the files off that way.

If its an old pre ata hdd (assuming your main pc is ata/sata) you could try tomsrtbt. Its linux on a floppy disk (command line only) but you may need a second floppy drive to copy the files to another FD.

[http://www.toms.net/rb/](http://www.toms.net/rb/)

---

### Post by txwooley on 2009-01-21
> **Tomatz said:**
> You could remove the HDD and mount it in your main pc and get the files off that way.

If its an old pre ata hdd (assuming your main pc is ata/sata) you could try tomsrtbt. Its linux on a floppy disk (command line only) but you may need a second floppy drive to copy the files to another FD.

[http://www.toms.net/rb/](http://www.toms.net/rb/)

Cool! I never thought of pulling the whole HDD.  Would John the Ripper work on that?  I need something simple to use this one time and then uninstall.

---

### Post by Tomatz on 2009-01-21
> **txwooley said:**
> Cool! I never thought of pulling the whole HDD.  Would John the Ripper work on that?  I need something simple to use this one time and then uninstall.

Just disconnect the HDD from the win 3 box then wire it up to your main PC (if compatible). Then boot your main PC (9x, NT or Linux) and mount the disk (or if using windows just go to my computer). 

Then just copy the files you need to your main HDD ;)

---

### Post by txwooley on 2009-01-21
Thanks for all the help so far!  I installed the HDD on an XP comp and copied the entire thing (<360MB) to a flash drive to view on my Ubuntu laptop.  So what now?  Just playing with it I tried to open the Word (3.1) docs in XP.  It gave an error about a dialog tab being open (even though there wasn't one) but never prompted for a password.  Which file from the 3.1 HDD contains the password?  OK so it's contained in "X", now what?  I am really a noob at this.  I thought I was pretty good since I could troubleshoot my wife's simple Windows probs on the phone with her, but I know nothing about Ubuntu (have been using it on my laptop for about 6 mos now) and even less about programming (I can spell C++).  How do I open these ancient Word docs if newer versions of Windows won't even recognize them?  I don't really want to use my kids XP or my wife's Vista as I consider this part of the learning process for my Ubuntu laptop, however my wife wants her old stories back, so anything that works is better than what I've got right now.

Again, thanks for the help so far!

---

### Post by txwooley on 2009-01-21
Correction:  Plugging the flash drive into my Vista desktop and trying to open said files with Open Office, it does prompt for a p-word.  Perhaps a bruteforce cracker is in order.  Any suggestions?  Please don't say, "Google it",  Google doesn't tell you who is better only who payed the most to be listed first.

---

### Post by tommynz1975 on 2009-01-21
Have you tried to open MS word files in Abiword?
This should be found under Applications ==> Office ==> Abiword

If all else fails you could install wine and install word.

now to be sure is it word files or *.wri files

From memory when windows 3.1 came out Ms word 5 and 6 where out and the cost was about nz$700

---

### Post by txwooley on 2009-01-21
> **tommynz1975 said:**
> Have you tried to open MS word files in Abiword?
This should be found under Applications ==> Office ==> Abiword

If all else fails you could install wine and install word.

now to be sure is it word files or *.wri files

From memory when windows 3.1 came out Ms word 5 and 6 where out and the cost was about nz$700

My mistake.  I was referencing the Windows vewrsion not the Word version.  When I right click the file, it gives me the first sentence and a half of the story.  The file type is Open Document (.DOC) and opens with WinWord and made by Word 6.0

---

### Post by Tomatz on 2009-01-22
Check here:

[http://windowsitpro.com/article/articleid/22478/accessing-data-in-a-password-protected-document.html](http://windowsitpro.com/article/articleid/22478/accessing-data-in-a-password-protected-document.html)

Its a .doc so the information in the link should still be relevant ;)

---

### Post by txwooley on 2009-01-22
> **Tomatz said:**
> Check here:

[http://windowsitpro.com/article/articleid/22478/accessing-data-in-a-password-protected-document.html](http://windowsitpro.com/article/articleid/22478/accessing-data-in-a-password-protected-document.html)

Its a .doc so the information in the link should still be relevant ;)

Thanks.  When I read the article, I really got my hopes up.  I should have known better.  When I change the .doc to .txt or even .rtf as suggested and open with a notepad in Ubuntu, it won't open and is an unreadable format.  When doing so in Vista, I discovered that just changing the name to document.txt creates document.txt.DOC and is still password protected.

I managed to find 1 file on the HDD called SHARES.PWL  I tried running that through Cain and Abel on Vista and it says it is an unsupported .PWL file.  I ran it through John the Ripper on Ubuntu and it comes up with 0 passwords detected.  I put the entire folder that contains the HDD contents into John, and it still says 0 passwords.  From what I can gather, the password hash must be in a format compatible with that of pwdump.  I think it's just too old for John.

How do I extract the hash from the .pwl file?  I've spent the entire day on google looking how to make win 9.x .pwl files readable by John, bu nobody talks about anything before NT.

---

### Post by Tomatz on 2009-01-23
> **txwooley said:**
> Thanks.  When I read the article, I really got my hopes up.  I should have known better.  When I change the .doc to .txt or even .rtf as suggested and open with a notepad in Ubuntu, it won't open and is an unreadable format.  When doing so in Vista, I discovered that just changing the name to document.txt creates document.txt.DOC and is still password protected.

I managed to find 1 file on the HDD called SHARES.PWL  I tried running that through Cain and Abel on Vista and it says it is an unsupported .PWL file.  I ran it through John the Ripper on Ubuntu and it comes up with 0 passwords detected.  I put the entire folder that contains the HDD contents into John, and it still says 0 passwords.  From what I can gather, the password hash must be in a format compatible with that of pwdump.  I think it's just too old for John.

How do I extract the hash from the .pwl file?  I've spent the entire day on google looking how to make win 9.x .pwl files readable by John, bu nobody talks about anything before NT.

This app should help with the .pwl file ;)

[http://lastbit.com/vitas/pwltool.asp](http://lastbit.com/vitas/pwltool.asp)

---

### Post by cariboo on 2009-01-23
the .pwl just stores a password. Back in the day if any one put a login password in windows 95 or 3.0+ the way to bypass it was to delete the .pwl file

Jim

---

