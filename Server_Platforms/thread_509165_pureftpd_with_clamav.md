---
title: "pureftpd with clamav"
date: 2007-07-25
forum: Server Platforms
---

### Post by stefandebacker on 2007-07-25
For the past 2 days I have been trying to make an ftp server that scans the uploaded files for virussen on upload. 

First with proftpd that claimed to have something like that. And indeed, after some work it scanned and deleted te infected files (eicar-test-virus). The sad thing was, that it also deleted all the not-infected files that were uploaded after the infected on... bummer.
 
So today i tried my luck with pure-ftpd. This seems to have an even better feature: the pure-uploadscript... pure genius! But I can't get it to work proper. I compiled the pure-ftpd with "--with-uploadscript". That seems to work fine. The file /var/run/pure-ftpd.upload.lock was created, but the file /var/run/pure-ftpd.upload.pipe was not. Of course I got an error. Then I created it myselve, as root with the mod 600
 
When I give the command: pure-uploadscript -r /var/run/antivirus.sh I get an error: "Insecure permissions on /var/run/pure-ftpd.upload.pipe"
I think thats the reason why, when I ftp something to my server, I see the size of  /var/run/pure-ftpd.upload.pipe increese, but my script pure-uploadscript -r /var/run/antivirus.sh isn't executed.
 
Can anyone please give golden tip, that wil make pure-ftpd on my ubuntu-server work with clamav?

---

