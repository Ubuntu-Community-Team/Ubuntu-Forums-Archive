---
title: "Importing mail files to Seamonkey from Eudora"
date: 2010-01-21
forum: Ubuntuzilla
---

### Post by Sleepy-zz-John on 2010-01-21
Hi,  I'm trying to get my Karmic SeaMonkey 2.0.2 to import mail mbx and toc files from Eudora on another (mounted) partition.  
In Mail & Newsgroups - Tools -Import, I've tried **"Import Everything"** in which case the only available option displayed is to import from SeaMonkey 1.X, Netscape 6/7 or Mozilla 1.X
And I've also tried **"Mail"** in which case the only available option displayed is Communicator 4.X

Clearly SeaMonkey's import wizard isn't seeing my Eudora at all.  What exactly is the import wizard looking for, and where is it looking?   The only files I really need have .mbx and .toc extensions and are in Eudora mail folders with .fol extensions.  I don't need settings or address book stuff.   If I knew what and where SeaMonkey import wizard is actually looking, I could easily copy my relevant Eudora files there.

As an alternative approach I've tried creating a SeaMonkey Local Folder called **"Test"** and then pasting one of my Eudora .mbx files into ```
/home/john/.mozilla/seamonkey/jypxx42c.default/Mail/Local Folders/Test
``` After modifying the original Eudora header to make it look more like a Mozilla mail header,  I did manage to get my original Eudora header details to display OK in SeaMonkey's local 'Test' mailbox, but I failed to get its body to display because I didn't know how to set the correct eom info in the matching .msf file.  Hopefully the import wizard knows how to derive that by measuring the body length itself or from Eudora's .toc file.

I think it would be a lot easier if I could get the Import Wizard to do the job for me,  but if that's not possible for any reason,  perhaps if I knew how,  I could modify a dummy .msf file to match the actual body length.

---

### Post by nanotube on 2010-01-21
Hi
it appears that there are some pieces missing from the seamonkey mail importer...

so my recommendation would be to install thunderbird, use thunderbird to import email, and then use seamonkey to import from thunderbird.

for importing to thunderbird, see this page:
[http://kb.mozillazine.org/Importing_from_Eudora_%28Thunderbird%29](http://kb.mozillazine.org/Importing_from_Eudora_%28Thunderbird%29)

after you're done, you can uninstall thunderbird and delete the extra copy of your email from the .thunderbird directory.

or, you could consider just using thunderbird for your email :)

---

### Post by Sleepy-zz-John on 2010-01-21
Thanks for the suggestions.  In view of this complication,  I'm wondering now whether it might be a better idea to go in for a Linux version of Eudora (8.0.0b7 -including Penelope),  instead of Thunderbird.  

I'm actually missing several features from my old Windows Eudora 6 that don't appear in either SeaMonkey or Thunderbird at all (e.g. managing individual mails previously left on the mailserver,  displaying individual message size against each message in mailbox list, editting received mails, date time & timezone quoted in replies, etc.) so maybe I should investigate this as another alternative, first. 

 I notice in eudora/8.0b7/README.txt that bugzilla is involved in the development, so maybe this is where should look for a good overview?

---

### Post by nanotube on 2010-01-21
don't really know anything about eudora specifically... 

btw, most of the features you list indeed don't seem to be available is sm or tb, but displaying message size in the mailbox list is not one of them (i have my tbird displaying it for me as we speak). 

at any rate, i'm not really qualified to say anything about how to best install linux eudora or anything like that.

---

