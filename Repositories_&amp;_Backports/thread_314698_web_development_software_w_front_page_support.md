---
title: "web development software w/ front page support?"
date: 2006-12-07
forum: Repositories &amp; Backports
---

### Post by bsc on 2006-12-07
Hi, first post here.. been using Ubuntu for about a month now in various places.. switched my laptop over 100% 2 weeks ago and last night my desktop with dual boot.  Installed 6.06 LTS on a server at work for testing too.

I have to say as a long time Slackware user (since 7.0) I love Ubuntu.. It Just Works.

Anyway my question is this: I run a student organization web page at my University and the only remote support they have for updating our sites is using Front Page or the new Microsoft Expression Web (which I must say I love.. it's nothing like FP in that it develops pretty much standards based code and doesn't make a mess out of things).

Is there a development software for Linux that I can use to upload my sites to this Front Page only server?  I have looked all around and can't seem to come up with anything solid, and I like to think of myself as no slouch with the Google.  8) 

Thanks for the help

---

### Post by david.rahrer on 2006-12-10
I'm pretty sure there is nothing that uses FP extensions except FP (I think even Expressions is abandoning them).  The only WYSIWYG web design tool I have found for Linux that comes even close to FP is Nvu (nvu.com) and it's still a long ways off.  If the web you are working with is full of FP specific code (navigation, embedded tools, etc) then using anything else to edit could cause a lot of problems.  Even FP can upload using FTP but other software isn't aware of all the hidden files and code it uses.  

I know nothing about it but I understand you can run MS Office on Ubuntu using Crossover Office.  Using that or a small partition with XP and FP might be the best thing.

---

### Post by bsc on 2006-12-10
> **david.rahrer said:**
> I'm pretty sure there is nothing that uses FP extensions except FP (I think even Expressions is abandoning them).  The only WYSIWYG web design tool I have found for Linux that comes even close to FP is Nvu (nvu.com) and it's still a long ways off.  If the web you are working with is full of FP specific code (navigation, embedded tools, etc) then using anything else to edit could cause a lot of problems.  Even FP can upload using FTP but other software isn't aware of all the hidden files and code it uses.  

I know nothing about it but I understand you can run MS Office on Ubuntu using Crossover Office.  Using that or a small partition with XP and FP might be the best thing.

Thanks for your insight. Actually Expression Web uploads to FP servers just fine.. and I am using no FP code or navigation whatsoever in my sites themselves, its pure XHTML 1.0 Strict and CSS. I pretty much just use Expression to make edits and then sync the files to the server. FTP doesn't work. I was thinking that Dreamweaver works when uploading to Front Page servers, but maybe I was wrong.

Maybe the best thing is to bust out some virtualization so I can run a Windows instance for Expression Web.... it is critically important that I am able to edit this site quickly and easily.

Thanks again.

---

### Post by bsc on 2006-12-11
Problem solved.

1. Download FREE
[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

2. Create new 4GB virtual machine and install WinXP Pro with existing license.

3. Install and run any needed Windows apps at will.

4. ??????

5. Profit!

---

### Post by hikaricore on 2006-12-13
> **bsc said:**
> Problem solved.
4. ??????

5. Profit!

Isn't it sad that people still quote that south park episode over 6 years after it came out?  I know I do it on a weekly basis.

---

