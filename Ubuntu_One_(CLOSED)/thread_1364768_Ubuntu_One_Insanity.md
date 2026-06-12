---
title: "Ubuntu One Insanity"
date: 2009-12-26
forum: Ubuntu One (CLOSED)
---

### Post by Digital Hick on 2009-12-26
What is the deal with this thing?  I have erased config files.  I have updated to the PPA beta.  All it keeps doing in adding more entries of my computer to the account.  Does this thing actually work? :roll:
The latest thing is authentication failure when I try to run it.  It does not even have the browser open before it drops the connection.  The two test things I have in the folder are correctly marked **unsyncronized**.

Ubuntu 9.10 32-bit, updated client to PPA beta.

---

### Post by Digital Hick on 2009-12-26
No error logs appear to getting generated.

It appears from the bug reports I have found that this is a known authentication issue.

It finally asked for access to the key ring for the first time.* See attached picture.*

Installed ubuntuone-client-tools and tried the command line.
All I get after adding my computer on the webpage is AUTHENTICATION FAILED on the command line.

This thing is in really bad shape.
:confused::confused::confused:

---

### Post by andrea000 on 2009-12-26
I have only had 1 bad problem out of ubuntu one
i couldn't add my pc to the website after i
deleted it here is what i did to fix it in the
terminal type
> u1sync --authorize 
i think you need ubuntuone client tools installed
then the web page pops up asking you to add your
computer.After that it has been easy sailing.

---

### Post by Digital Hick on 2009-12-27
Well Andrea I tried the following...

Deleted syncdaemon settings
Deleted config settings
Cleaned out all entries in account of authorized computers
rebooted
did u1sync --authorize from command line
browser popped up
logged in
added computer to account
and at this point the terminal registered that the authentication failed
the browser moved to the tab where you would see your files...assuming it had worked.

Game set and match....digital hick loses again.:popcorn:

---

### Post by Digital Hick on 2009-12-28
I am just curious, and I hope someone can help answer this.  What exactly is going wrong with AUTHENTICATION_FAILED.  Really, think about it.  I am logged into the web site.  I am logged into my laptop.  The keyring was given permission.  So what is not authenticating?:confused:

---

