---
title: "Samba - Trash not Delete"
date: 2007-11-09
forum: Server Platforms
---

### Post by kdkirsch on 2007-11-09
Hi. Background: My system is a Dell PowerEdge 840 with RAID 1 via 3ware 9650. It's running Ubuntu 7.10 with samba, ssh, and webmin (which is awesome). It's deployed in a small business environment with 4 windows clients. I only want to use it (for now) as a file server.

Scenario: Files are created by many users to be consumed (read/edited) by everyone else. e.g. Jill may create document PI and Bill needs to edit PI. There is only one samba group (office), and each person is a distinct samba user.

Problem: In this situation, my understanding is that I need to grant permissions of 775 (though I don't think other privileges are relevant to my issue). My concern is what happens *when *a file/directory gets accidentally deleted. I have backup procedures in place, but what I am really interested in is a trash can.

Question: Can I set it up so that when a windows user deletes a file/directory via the network share, the file/directory is NOT deleted but is transparently moved to a trash can (.trash, perhaps)? Additionally, the trash can could be configured to auto-purge every 30 days or something, or manually.

I look forward to reading the thoughts, suggestions or answers you may have. Thanks for your help!

---

### Post by ViRMiN on 2007-11-10
[http://www.redhat.com/advice/tips/sambatrash.html](http://www.redhat.com/advice/tips/sambatrash.html)

Okay, so it's for RedHat but, the config might still be of use?  Hope it works (I have not tested this, just posting a reply blindly) :)

---

### Post by kdkirsch on 2007-11-15
This worked great. Thanks so much (and I apologize for my delay).

-kdkirsch

---

### Post by ViRMiN on 2007-11-20
For some reason I only just got the notification of an update on this thread!  Glad it worked out, and you're welcome :)

---

