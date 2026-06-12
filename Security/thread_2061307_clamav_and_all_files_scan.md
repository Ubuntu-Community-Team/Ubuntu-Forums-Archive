---
title: "clamav and all files scan"
date: 2012-09-22
forum: Security
---

### Post by sganaway on 2012-09-22
hey guys,

 i have to scan all files in a directory, and so i have used the follows command:
 
  clamscan -r /path

but after the scan i have seen that, in the scan report, there is a different between 'data read' and 'data scanned' values.

in my opinion this means that some files are excluded by default, so i have searched and tried many options to include all possible files (like pdf, avi, mkv and so on), but the two data value remain different.

have you some idea?!...

---

### Post by Ms. Daisy on 2012-09-22
Clamav can only read files that the user running it can read. 

Try running the same command with sudo.

```
sudo clamscan -r /path
```
(FYI I learned that from here [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV) , perhaps that link will be useful for you)

---

### Post by sganaway on 2012-09-23
> **Ms. Daisy said:**
> Clamav can only read files that the user running it can read. 

Try running the same command with sudo.

```
sudo clamscan -r /path
```
(FYI I learned that from here [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV) , perhaps that link will be useful for you)


Thanks a lot, but it doesn&#8216;t work.

in fact clamav are able to read the files but
(like report suggests) it doesn&#8216;t scan some 
particular files (pdf,mkv,avi,...) that are owned
by the user.

any other ideas?!...

---

### Post by cwsnyder on 2012-09-23
Are you sure that you need to scan directory tree listings (. & ..), hidden directories, hidden files usable only by Linux, etc.?

If so, you probably need to remove the full stop (.) in front of the files, and even that won't get the . & .. directories.

Remember, Linux/Unix views *everything* as a file.

---

### Post by sganaway on 2012-09-23
Hey cwsnyder, thanks for your help but it&#8216;s not my situation!

My problem is that clamav seems to exclude some files from scan. Clamscan is able to read that files (because the value of &#8216;data read&#8216; increase), but it seems that the antivirus doesn&#8216;t search virus in that files(the value of &#8216;data scanned&#8216; remains the same).

Some files that i can&#8216;t scan, are: pdf,avi,mkv,...and some other no-executable files!

For example,if i scan a pdf of 5Mb, the &#8216;data read&#8216; tell me 5Mb
while the &#8216;data scanned&#8216; is 0 Mb.

Ideas?!...

---

### Post by cwsnyder on 2012-09-24
Read **man clamscan**.  There may be a configuration file which excludes certain type of files.  There are clamscan CLI options to include pdf files.

---

### Post by sganaway on 2012-09-24
> **cwsnyder said:**
> Read **man clamscan**.  There may be a configuration file which excludes certain type of files.  There are clamscan CLI options to include pdf files.

These are two options that i've already checked.

Before to post my question, I have tried the option --scan-pdf with clamscan, but i have had the same result (data read=SIZE_OF_THE FILE, data scanned=0).

After that I've searched into the configuration file (clamd.conf) if the ScanPDF option is set to false, but it isn't!

I haven't found any other option about!...

---

### Post by sganaway on 2012-09-24
Perhaps i have found the problem (and, i hope, the solution)!

ClamAV should have a size-file limit: so the files over a certain size are excluded by the engine!

If i add this option:

            --max-filesize=100M

everything goes good.
(in this example i have set the new limit to 100 Megabyte)

Now i play some tests to verify the solution.
(apparently the --max-scansize=100M is useless for this problem...)

I let you know...

---

### Post by Kinstonian on 2012-09-24
I think Clam may only scan certain objects in a PDF.  There may not be any suspicious objects in the PDF you're scanning so it's reporting nothing was scanned.  You will probably also see a difference in the data read and data scanned if you scan compressed files.

---

### Post by sganaway on 2012-09-28
Ok, it's work!

The problem was that clamav has a 2 limit:
- the first limit is relative to the size of the file. If the file is too large, clamav exclude it.
- the second limit is about the amount of data to scan per single file. if the file is too large, clamav read it but don't scan it.

So, during a scan with a wide variety of files, is good to set the two option (mentioned before):
--max-filesize=#n 
--max-scansize=#n 
otherwise some file may be excluded.

There are other two point that i would clarify (because these are mentioned during the discussion):

- the clamd.conf file is the configuration file for the clamd service, and not for the clamscan tool. (so if you apply some changes to that file, you won't have effect during the clamscan execution)
- for some file the information to scan is extracted for the file itself ( like files contained in a tar), so there may be difference between data read and data scan. Anyway the data extracted have to be scanned.

I can consider the post closed,
thanks to everybody for your precious and helpful suggestions.

Thanks a Lot!!

---

