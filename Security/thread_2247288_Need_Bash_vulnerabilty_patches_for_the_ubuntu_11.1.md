---
title: "Need Bash vulnerabilty patches for the ubuntu 11.10 server"
date: 2014-10-07
forum: Security
---

### Post by srinet on 2014-10-07
Hi All,

I know that it is not a good practise to work on the server which has already going dead. My some of server OS version is 
ubuntu 11.10 and I know that it is not supported by ubntu any more but these servers having some critical data and I can not update it easily.
So can any one let me knoe how can I patch bash of this version or any one have any solution then please let me know the steps of bash update 
with ubutu 11.10.

Thank you in advance!!!!!!!!!!!!!

---

### Post by ajgreeny on 2014-10-07
This will be very difficult as 11.10 is no longer supported, therefore the repos do not exist any more where they were but are now moved to EOL addresses.  However, the packages themselves are not being updated any more so even if you do get a connection to the repos it will not help with your problem.

I think you will either have to compile your own package with the patches, or bite the bullet and update the whole system to a version which has those vulnerabilities already patched, ie 12.04.5 or 14.04.1.

---

### Post by Elfy on 2014-10-07
I've got to ask - if > these servers having some critical data why wait for 16 months to deal with them?

If you need help compiling bash - start a new thread.

Closed

---

