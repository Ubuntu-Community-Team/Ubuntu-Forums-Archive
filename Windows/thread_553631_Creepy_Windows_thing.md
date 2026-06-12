---
title: "Creepy Windows thing"
date: 2007-09-18
forum: Windows
---

### Post by Scarlett on 2007-09-18
I noticed this just recently on my Windows box at work.  When I receive an attachment in my e-mail and I use save-as to put it on the server, the file path it's saving from leads to a directory that is completely hidden.  Not just hidden as in one of those sort-of hidden files that you can un-hide through the folder options dialogue box.  I mean, completely hidden in that you will never find it unless you know the exact path name and open up a DOS prompt and go directly to it.

So I did that and discovered that along with the "OLK9E" folder that's completely hidden in Temporary Internet Files, there's also 15 other folders.  I listed the contents of OLK9E and find that all the cookies, web addresses, e-mail attachments and favicons that I thought Firefox had been deleting upon exit, have actually been secretly stored in this mysterious, invisible file.  (Which I was really grateful for, because there's a bunch of stuff in there I had neglected to save prior to my e-mail getting wiped out due to an operator error.)

Why would Windows want to store this information in a place that is really hard to find despite my instructions to my browser to delete it?  How do I make the files visible so I can find out what's in the other 15 folders that don't appear in Explorer but still exist according to DOS?  (Incidentally, it felt really strange navigating through the computer this way... like I was at home on Ubuntu.  I never knew XP had a command line.)

---

### Post by jrusso2 on 2007-09-18
I don't know why that has always been part of windows.  I remember in Windows 95 having to delete temp files in dos to get rid of all those hidden ones

---

### Post by notwen on 2007-09-18
CLI > all.  More reason to see the strength of the CLI and its capabilities over GUI.

---

### Post by TheThinker on 2007-09-18
I may be able to help you out here. Being a former windows user, I've encountered similar problems in the past. Download a program called HijackThis. It will be able to generate a report of all the processes that your system boots up as well as any that are currently working in the background. You can login at Bleepingcomputers.com, post it in one of their help forums, and you should be getting some handy support. Plus, the program also allows you to delete and kill any processes that you feel are nefarious.

You can find HijackThis at [http://www.merijn.org/index.php](http://www.merijn.org/index.php)


There are other things about windows that I hate too, such as the fact that malware can be re-introduced to the computer if you use the restore tool. That is why it's expected that you delete the restore file after you clean the system, then recreate it. And that's while you boot in safe mode. In the end you realize that Windows is  really a soup of peripherals; they keep intermingling with eachother so much that it's often difficult to sort out the good ones from the bad ones.

The reason why I'm telling you this is because invisible folders are typically created by malware, which also takes advantage of invisible folders already found in XP. Don't ask me why they included invisible directories; I just want my computer to be transparent. HijackThis, and others like it, are great and necessary tools these days for windows users for this reason, among others.

---

### Post by dca on 2007-09-18
> **Scarlett said:**
> I noticed this just recently on my Windows box at work.  When I receive an attachment in my e-mail and I use save-as to put it on the server, the file path it's saving from leads to a directory that is completely hidden.  Not just hidden as in one of those sort-of hidden files that you can un-hide through the folder options dialogue box.  I mean, completely hidden in that you will never find it unless you know the exact path name and open up a DOS prompt and go directly to it.

So I did that and discovered that along with the "OLK9E" folder that's completely hidden in Temporary Internet Files, there's also 15 other folders.  I listed the contents of OLK9E and find that all the cookies, web addresses, e-mail attachments and favicons that I thought Firefox had been deleting upon exit, have actually been secretly stored in this mysterious, invisible file.  (Which I was really grateful for, because there's a bunch of stuff in there I had neglected to save prior to my e-mail getting wiped out due to an operator error.)

Why would Windows want to store this information in a place that is really hard to find despite my instructions to my browser to delete it?  How do I make the files visible so I can find out what's in the other 15 folders that don't appear in Explorer but still exist according to DOS?  (Incidentally, it felt really strange navigating through the computer this way... like I was at home on Ubuntu.  I never knew XP had a command line.)

Don't quote me, if I remember correctly the purpose of the OKL**** hidden directories was to stop people from editing email attachments within Outlook.  That's what keeps the integrity of email attachments when moving them from the .pst database file to that hidden directory for viewing.  This way every time you open the email attachment you rec'd it will be the same as what the user sent you.  It's a bad habit editing word docs & spreadsheets, etc within Outlook.  You should save to your desktop or My docs directory, then edit.  When done, you can save, then attach it to new email...

---

### Post by Scarlett on 2007-09-19
> **TheThinker said:**
> You can find HijackThis at [http://www.merijn.org/index.php](http://www.merijn.org/index.php)

There are other things about windows that I hate too, such as the fact that malware can be re-introduced to the computer if you use the restore tool. That is why it's expected that you delete the restore file after you clean the system, then recreate it. And that's while you boot in safe mode. In the end you realize that Windows is  really a soup of peripherals; they keep intermingling with eachother so much that it's often difficult to sort out the good ones from the bad ones.

The reason why I'm telling you this is because invisible folders are typically created by malware, which also takes advantage of invisible folders already found in XP. Don't ask me why they included invisible directories; I just want my computer to be transparent. HijackThis, and others like it, are great and necessary tools these days for windows users for this reason, among others.

Well, f&$@*$# crap.  The only reason I ever noticed those additional folders was because I suspected my computer was compromised so I went digging.  I did a completely stupid thing at the request of the boss, so at least I'm covered there - but I should have known better.  

The obvious thing I noticed was that it renamed my Recycle folder to "Recyclers" and I couldn't view any of the contents.  ClamAV confirmed that there was a trojan running in that file and I restored the system to a couple of days prior to the date the file said it was installed.  That restored my Recycle folder and made the bogus Recyclers folder visible and I was able to delete it.  I thought everything was all good, but maybe not?  I'll definitely check out hijackthis when I get a free moment.  I had considered it before but their description didn't make it sound like it does as much as you say it does so I didn't bother.

> **dca said:**
> Don't quote me, if I remember correctly the purpose of the OKL**** hidden directories was to stop people from editing email attachments within Outlook.  That's what keeps the integrity of email attachments when moving them from the .pst database file to that hidden directory for viewing.  This way every time you open the email attachment you rec'd it will be the same as what the user sent you.  It's a bad habit editing word docs & spreadsheets, etc within Outlook.  You should save to your desktop or My docs directory, then edit.  When done, you can save, then attach it to new email...

Heh.. Yeah, OKL... I got the letters mixed up.  But if that's a valid directory, why is it so hidden?  Maybe some people want to restore stuff from there.  Or erase things.  Or just want to know what's going on in their own computer. 

Like the poster above illustrates, if I don't know what's supposed to be there, how am I supposed to figure out what's just a super-sneaky file and what's genuinely malicious.  Why must they make this more difficult than it really is?  Gah!  Now I'm going to be completely paranoid and nothing short of a fresh install is going to make me happy and I can't do that.... Stupid Microsoft!

---

### Post by wolfen69 on 2007-09-19
huh?

---

### Post by wolfen69 on 2007-09-19
it's hard to keep up with the jones

---

### Post by K.Mandla on 2007-09-20
Moved to Windows Discussions.

---

### Post by Joeb454 on 2007-09-20
If the folder's hidden even when you select "Show Hidden Files & Folders" then it could be an OS file/folder.

I'm sure there's an option underneath that called "Show Hidden Operating System Files" or something similar, maybe that's why.

---

### Post by Mr.Auer on 2007-09-22
This is a previously discovered FEATURE. MS operating systems also have this same feature of saving info in hidden folders about what web pages you have visited with Internet Explorer etc. Its said this is to help law enforcement to discover what pages you have visited if your computer is confiscated by the police. This hidden directory would still contain data about what pages were visited, even if you had deleted all browser caches etc.

In other words, the OS is spying on you and keeping logs of what you do in the web. Why would they let you see that, or the collected files? :)

Here are some links about this, bear in mind I HAVE NOT checked this out myself since I havent been using MS products in years now...But this can well be true, I see no reason why they would not do this...After all, Vista too is advertised as "We co-operated with NSA in making this." Should worry you a lot.

[http://membrane.com/security/secure/Microsoft_Is_Unscrupulous.html](http://membrane.com/security/secure/Microsoft_Is_Unscrupulous.html) or
[http://www.microsuck.com/content/ms-hidden-files.shtml](http://www.microsuck.com/content/ms-hidden-files.shtml)

"There are folders on your computer that Microsoft has tried hard to keep secret. Within these folders you will find two major things: Microsoft Internet Explorer has been logging all of the sites you have ever visited -- even after you've cleared your history, and Microsoft's Outlook Express has been logging all of your e-mail correspondence -- even after you've erased them from your Deleted Items bin. (This also includes all incoming and outgoing file attachments.) And believe me, that's not even the half of it. 

When I say these files are hidden well, I really mean it. If you don't have any knowledge of DOS then don't plan on finding these files on your own. I say this because these files/folders won't be displayed in Windows Explorer at all -- only DOS. (Even after you have enabled Windows Explorer to "view all files.") And to top it off, the only way to find them in DOS is if you knew the exact location of them. Basically, what I'm saying is if you didn't know the files existed then the chances of you running across them is slim to slimmer."

"2. SEEING IS BELIEVING 

No. Enabling Windows Explorer to "show all files" does not show the files in mention. No. DOS does not list the files after receiving a proper directory listing from root. And yes. Microsoft intentionally disabled the "Find" utility from searching through one of the folders. 

Oh, but that's not all. 

Just from one of these files I would be able to tell you which web sites you previously visited, what types of things you search for in search engines, and probably gather your ethnicity, religion, and sexual preference. Needless to say one can build quite a profile on you from these files. It has the potential to expose and humiliate -- putting your marriage, friendship, and corporation at risk. Here's one good example of the forensic capabilities."

So if youre worried, check out either one of those sites and see for yourself if what they say is true.
I just happened to stumble on this thread and rememberd id seen something written about this, and Googled for those pages.

Edit: This may also be of interest: [http://www.jsware.net/jsware/sviewer.php3](http://www.jsware.net/jsware/sviewer.php3)
" Did you know that: You could have an unlimited number of invisible files on your computer?...That such files could be secretly used by spyware companies or virus authors?...That they are currently used by Microsoft to store hidden data?... And that Microsoft has provided no standard means to view or remove these hidden files?

   Windows NT (NT4/2000/XP/2003) has the ability to attach multiple hidden files, known as "alternate data streams", to any given file (or folder). These are not the usual "hidden" files that you can choose to make visible. These are invisible files. In other words, this is an entire, secondary file system for which there is no equivalent to "Windows Explorer". This is an entire, secondary file system which you are not intended to access.
   Or to put it another way, Microsoft has deliberately created a file system that is incompatible with their own file browser (Windows Explorer), creating types of files that Windows itself cannot see!"

---

### Post by Mr.Auer on 2007-09-22
Needless to say, its stuff like this that made me change to Linux - for ever. I dont want a whole Spyware Operating System on my computer - especially when Id have to pay myself sick for the privilege. I believe Vista will multiply these kinds of things tenfold at least over previous Windows versions. Also theres a very good reason most armies use Linux systems for their own networks. Like the Finnish Defense Forces recently switched to Linux - for security reasons.

Windows is closed source, closed binaries and no one except high level leadership in Microsoft knows what the OS may contain beyond that told to consumers.

---

