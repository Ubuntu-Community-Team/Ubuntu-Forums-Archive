---
title: "Ossec - monitor file integrity of Nas folder"
date: 2014-07-30
forum: Security
---

### Post by Brian975 on 2014-07-30
As we are attempting to move Ossec into production, I have run into a major hurdle. Our IIS that need to be monitored are residing on a Nas share so they may be accessed by a IIS server farm. For PCI compliance, we must monitor the files for any changes. The Nas is a Netapp Filer with a Cifs share. 
As of yet, I have been unable to find a way to monitor these files.

Some of the options I have looked into include:
Using Agentless monitoring via ssh - I could not find a path to the cifs share via ssh
Mounting the unc to a windows box and monitoring the drive share - Requires a user to always be logged on and does not seem very "clean".

I am sure that I am not the first person to have the need to monitor a cifs share. What are others doing in these circumstances?

---

### Post by frankmorris2 on 2014-08-01
Hello,

I would suggest to post this question to the OSSEC mailing list, you might get more answers there:
[https://groups.google.com/forum/#!forum/ossec-list](https://groups.google.com/forum/#!forum/ossec-list)

Have a nice day.

---

### Post by Brian975 on 2014-08-01
Thank you for the link. That will be helpful in the future. I was able to figure out my problem last night. I added the unc of the files I need to monitor to one of the agent ossec.conf files. The alerts come in as being associated with that machine, however for IIS files, that is preferred anyway.

---

