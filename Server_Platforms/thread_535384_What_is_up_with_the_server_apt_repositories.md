---
title: "What is up with the server apt repositories?"
date: 2007-08-26
forum: Server Platforms
---

### Post by antwerx on 2007-08-26
I have been having a total failure when I apt-get update on fresh installs for all the server versions. This does not make since. My laptop running feisty does not fail so this frustrates the he#! out of me. 

Anyone else having similar or same issues with the server apt repositories?

**Back ground:**
I have been using Ubuntu for several years now on my laptop at and at work with out many issues and consider my self a fairly experienced Ubuntu user.
[B]
Problem: [/B]
I decided to install an Ubuntu server. I started with Feisty server and all installed fine. Once I apt-get update with a virgin sources.list it fails to update. I get a bunch of errors etc. I can ping the internet, yahoo.com, and have tried from behind my firewall, outside my firewall, and using my laptop sources.list on the server all of which fails. I even installed all of the server versions with the same failed results. 

Help?

---

### Post by p_quarles on 2007-08-26
That's pretty strange. Can you be more specific about what errors you are getting when trying to update?

---

### Post by antwerx on 2007-08-26
This is an abbreviated example from [B]apt-get update.
[/B]This is a 6.04 LTS server install. The sources list has been edited to comment out the CD only.  The rest of the repositories are stock.

[B]Error:
[/B]Sub-process bzip2 returned error code (2)

**apt-get update:** 
At the very beginning of the the update process all looks normal and good until here -
[U][I]Get: 4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release 99% [4 Packes bzip2 0] [Waiting for headers] bzip2: (stdin) is not a bzip2 file
[/I][/U]- then all actions beyond this step fail with the _*Sub-process bzip2 returned error code (2)*_ error.

---

### Post by antwerx on 2007-08-26
This is an abbreviated example from [B]apt-get update.
[/B]This is a 6.04 LTS server install. The sources list has been edited to comment out the CD only.  The rest of the repositories are stock.

[B]Error:
[/B]Sub-process bzip2 returned error code (2)

**apt-get update:** 
At the very beginning of the the update process all looks normal and good until here -
[U][I]Get: 4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release 99% [4 Packes bzip2 0] [Waiting for headers] bzip2: (stdin) is not a bzip2 file
[/I][/U]- then all actions beyond this step fail with the _*Sub-process bzip2 returned error code (2)*_ error.

---

### Post by p_quarles on 2007-08-26
Okay. Which version of Ubuntu server are you using? Earlier you said Feisty (=7.04), and now you're saying Dapper (6.06 LTS).

---

### Post by antwerx on 2007-08-26
Sorry for any confusion on my part.

I am running Dapper 6.06 LTS.

---

### Post by p_quarles on 2007-08-26
Yeah, this is puzzling. The source list from the laptop woulnd't work (assuming it's Feisty), but it's indeed strange that the default list isn't working correctly. 

Does this happen only with update, or with all apt-get operations? 

My guess, here, is that something is wrong with gzip. According to the apt-get man page, Debian repositories store their package lists as with gzip compression, and the error message indicates that it's trying to read it as though it were a bzip2 file. 

Is it possible that you configured anything related to these protocols? Setting an alias, or anything? Beyond that, you could try reinstalling/fixing gzip.

You might also take a look at /var/log/dpkg.log to see if there's anything in there that sheds light on what's happening.

---

### Post by antwerx on 2007-08-26
Thanks for your help. I will look at the log and check out the gzip stuff. 

I gotta run for now put will post back with what I find.

---

