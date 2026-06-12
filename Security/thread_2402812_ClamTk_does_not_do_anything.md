---
title: "ClamTk does not do anything"
date: 2018-10-04
forum: Security
---

### Post by artist-wavenet on 2018-10-04
My OS is Ubuntu 16.04. When I do a search for "ClamTk" in the Dash I get two instances of "ClamTk" in the search results. Should this be?

I opened one of the instances to do a viral scan for the entire hard drive drive. I clicked on the "Scan a directory" and navigated to the root directory. I did not see an option to scan recursively. When the root directory was selected I got the message:

Files scanned: 0
Possible threats: 0

How is a recursive scan done in ClamTk?

---

### Post by deadflowr on 2018-10-04
*Thread moved to **Security***

Isn't scan recursive set in Preferences or something.

---

### Post by artist-wavenet on 2018-10-04
In ClamTk's window I do not see a way to navigate to its preferences. Where would these preferences be?

One more question:
Although I would sill like to know how to do a recursive scan in ClamTk, 
I started such a scan in the Terminal Emulator by using the command:

clamscan -r -i /

While running it sends messages to the Terminal Emulator that it finds malware in old Thunderbird email files. What does clamscan do with malware or viruses it finds? Will it remove them? Or is it up to me to remove what it finds?
It shows which email file the malware is in, but not which email it is in. Is there a way to get clamscan to indicate which emails to delete?

---

### Post by deadflowr on 2018-10-04
> What does clamscan do with malware or viruses it finds? Will it remove them? Or is it up to me to remove what it finds?
It does nothing by default
You need to use either the --move or --remove option which will either move the infected files to a specified directory or remove the files wholesale.
Usually move is the better choice, as then you can review the files, clam is renown for false positives  so removing the files without first seeing what they are might actually be misguided.
(since the files marked as infections may actually be normal and fine)

A general thread at askubuntu on it here:
[https://askubuntu.com/questions/250290/how-do-i-scan-for-viruses-with-clamav/]("https://askubuntu.com/questions/250290/how-do-i-scan-for-viruses-with-clamav/")

---

### Post by artist-wavenet on 2018-10-05
When it finds a virus, or malware, in a Thunderbird email file, and it is told to remove, or move, will it do this only to the email message in the file, or will it do this to the entire file?

---

