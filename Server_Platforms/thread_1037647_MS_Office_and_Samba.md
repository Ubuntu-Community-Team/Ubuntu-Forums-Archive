---
title: "MS Office and Samba"
date: 2009-01-12
forum: Server Platforms
---

### Post by ramandhingra on 2009-01-12
Hi

I am using Ubuntu Server with Windows XP Clients.
Everything was working fine.. and then suddenly this error started happening where in Microsoft Office was not able to save files on samba shares. I have verified the file permissions and all.

I am using Microsoft Office 2007. Man!! Whats d issue?
Thanks a ton for your help.

---

### Post by HermanAB on 2009-01-12
Here you go:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by ramandhingra on 2009-01-12
Thanks for the reply, Herman.
But, can you please tell me what exactly what are you pointing out to in the mentioned link? And, I am to able to access the folder and copy files to it and even edit the files from other applications such as notepad, wordpad, etc..

Say, I create a text file on the samba share and open it using notepad, I am able to edit it. But, when I open the same file using MS Word, it behaves as if the file is read only.

I am sure it got nothing to do with file permissions, its something about MS Office and Samba incompatibility which I have seen people mentioned quite a lot in the google search results, but the solutions are not so available! HEPL (HELP!)

---

### Post by ramandhingra on 2009-01-14
Anyone? Experts?

---

### Post by dorowa on 2009-01-16
This might be because of the type of file lock, but you have to look through the log to see what happens with smb while someone access files...
If it concerns with locks, following options for shared directories might help (this might differ from version to version):

oplocks = False
level2 oplocks = False

Any way, I'd read the section about locks in samba manual...
Stay in touch with the problem!

---

### Post by Brian96 on 2009-01-17
For what it's worth, I am having the same problem in a simpler environment.

I installed Office 2007 in Hardy using Wine based on a how-to I found on here somewhere. The application works great, but when I save a file it treats it as read only.

I'm not sure Samba is part of the equation for my problem, though I could be wrong; I'm still quite new at this. I don't think it's a permission thing, as it happens everywhere, even in my home folder.

---

### Post by Brian96 on 2009-01-17
Does this give anybody insight?

[http://www.codeweavers.com/support/tickets/browse/?ticket_id=123175;s_subject=office;tscurPos=100](http://www.codeweavers.com/support/tickets/browse/?ticket_id=123175;s_subject=office;tscurPos=100)

Apparently not a new problem.

---

### Post by JeppeM on 2009-01-17
What version of samba are you using? We had this problem at work, using samba 3.0, but when upgrading it seemed to be fixed...

---

### Post by KingZZR on 2009-11-18
Hi i have a simliar problem with some MS programs on the samba server.
 
I am using MS PUBLICATIONS 2002
 
i can save to the samba server
when i reopen the file and alter it 
resave the file
i cannot open it at all.
 
It says 'publisher cannot open the file'
 
I have read the Knowledge base at MS, and found that a security update can effect opening files, it thinks it has a bad file & will not open it. I have added a PromptForBadFiles and entered the value as 1.
 
This still fails to work.
see this link
[http://www.computing.net/answers/networking/ms-publisher-2002-cant-open-file-saved-on-nas/38654.html](http://www.computing.net/answers/networking/ms-publisher-2002-cant-open-file-saved-on-nas/38654.html)
 
I am going to try and set it up on the FTP server see how i get on.
 
I will let you know if its a fix,

---

### Post by capscrew on 2009-11-18
> **ramandhingra said:**
> Hi

I am using Ubuntu Server with Windows XP Clients.
Everything was working fine.. and then suddenly this error started happening where in Microsoft Office was not able to save files on samba shares. I have verified the file permissions and all.

I am using Microsoft Office 2007. Man!! Whats d issue?
Thanks a ton for your help.

I have my doubts that this is a Samba problem.  I have XP and Vista clients that are capable of creating, modifying and saving both doc and docx files to a samba share.

How did you create and configure your samba share.  With the GUI (e.g Gnome, etc.) or via the /etc/samba/smb.conf file.

I have 2 servers in my network running samba and all works fine with both MS and Ubuntu for years now.

---

### Post by Vegan on 2009-11-18
I use Microsoft Office 2007 and I have SAMBA on the Linux box, no problems. Sounds like you have Windows problems.

My Linux machine works fine, and my Windows machine works fine too.

---

### Post by capscrew on 2009-11-18
> **Vegan said:**
> I use Microsoft Office 2007 and I have SAMBA on the Linux box, no problems. Sounds like you have Windows problems...


This does not appear to be a Windows problem.  I think you will find the OP has configured Samba shares with the GUI (right click >> etc.)  This causes no end of problems for non-gnome aware applications such as Open office and Gedit.

Sometimes user can overcome the problem by mounting the share to the *local *file system.  This is NOT needed with windows clients as long as the Samba daemon is configured correctly via the /etc/samb/smb.conf file.

---

### Post by dorowa on 2009-11-19
Hi 2 all!
I had linux-based samba server and didn't have any problems with files of any type, now i'm using linux-based nas with only samba, no ftp, and no problems at all, different windows on the network starting from win200 till win vista... The only problem I had was concerned with oplocks, I guess it was rather similar to that you guys have: the performance of samba server was low and some files were locked even for read...
First you must start from is to look through the samba log, put it here if you need help in understanding what's wrong. Perhaps you might need to increase the debug level, look through the samba manual to see how to do that...
Best wishes!

---

