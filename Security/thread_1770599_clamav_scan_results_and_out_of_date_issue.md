---
title: "clamav scan results and out of date issue"
date: 2011-05-29
forum: Security
---

### Post by PeaceOcean on 2011-05-29
Hi,

I am a newbie in ubuntu. I did clamscan on my ubuntu /, and I got the result message as follow. it shows "486 errors" I am wondering if the result is OK or I need to do some action on it. 

"----------- SCAN SUMMARY -----------
Known viruses: 968595
Engine version: 0.96.5
Scanned directories: 28067
Scanned files: 131696
Infected files: 0
Total errors: 486
Data scanned: 9020.40 MB
Data read: 17800.31 MB (ratio 0.51:1)
Time: 1349.479 sec (22 m 29 s)"

Also, my engine is 0.96.5. The latest version is 0.97. But "aptitude upgrade" can not upgrade the engine to 0.97. I understand 0.97 is still on testing. I am wondering if I can just stay with 0.96.5 and wait for the 0.97 passing all tests. if so, does it cause any security issue?

thanks,

---

### Post by Joe of loath on 2011-05-29
Staying with 0.96.5 will be fine.

However, why are you scanning for viruses on Linux? It doesn't need virus scans, any vulnerabilities are patched within hours.

---

### Post by Larkspur on 2011-05-29
Were you scanning the entire filesystem from a normal account?  That might explain the errors: you don't have the permissions to scan them.  You shouldn't really have to scan anywhere other than /home, as the chances of false positives outweigh the chances of finding anything.  As for the engine, I think you'd have to get the new one from the clamav website (it won't appear in the repositories until the next version), though you shouldn't need to.

---

### Post by PeaceOcean on 2011-05-29
thanks for the replies. one thing I want to clarify: when scanning, my command is "sudo clamscan -r /". So it should be able to scan the files under /. 

Now I know I should mainly scan the /home. and I will stay with 0.96.5 as long as it does not cause security problem.

---

### Post by ajgreeny on 2011-05-29
Forget about the clamav version;  it's the signature version that matters, and that will be up to date, as freshclam will make sure it's checked regularly.

Also note the important line **Infected files: 0, **so nothing to worry about.  The 486 errors could be archive files which can not be scanned by clamav;  use the -v option (I think it is -v for verbose, ie all information printed to terminal) and you should see a lot more info scroll by.  ```
man clamscan
``` will tell you all the options.

---

### Post by PeaceOcean on 2011-05-29
thank you all!

---

