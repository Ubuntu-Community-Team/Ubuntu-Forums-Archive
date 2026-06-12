---
title: "I/O error (basic_ios::clear)"
date: 2013-06-15
forum: Virtualisation
---

### Post by rollaster on 2013-06-15
Trying to run some programs like wget, pdf2djvu, etc.

Need it to output to my ntfs drive because I'm running virtual box of xubuntu x64 to handle the main system and installation files. Don't want a multi 100gb virtual disk for my work. Also have win 8 x64 if that helps.

Anyhow I installed dkms (Virtualbox Guest Additions). Changed the account settings as I ran into problems whenever I tried to use the terminal or dolphin to access /media/sf_C_DRIVE whenever I wasn't root. So that part was fixed by added vboxsf to my usergroup.

But whenever I try to run any programs which require read/write I get this:

[FONT=Ubuntu Mono]I/O error (basic_ios::clear)
[/FONT]
That was after running pdf2djvu. Another program for example wget -mk url -E 
gave me this after grabbing all the files and placing it into the directory. I added -E so I can view them properly however that requires renaming files, downloading the files works ok, but it is unbrowsable as the html files have to be opened by individually, won't work proper linking in a web browser.

Converting avalon.law.yale.edu/sept11/epa_030.asp... Unable to delete &#8216;avalon.law.yale.edu/sept11/epa_030.asp&#8217;: Text file busy
Converting avalon.law.yale.edu/css/site.css... nothing to do.
Converted 5540 files in 23 seconds.

I ran all programs like this

cd /media/sf_C_DRIVE/website
sudo pdf2djvu or wget

---

