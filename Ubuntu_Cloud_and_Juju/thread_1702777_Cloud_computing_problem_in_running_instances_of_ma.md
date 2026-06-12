---
title: "Cloud computing :problem in running instances of machine images"
date: 2011-03-08
forum: Ubuntu Cloud and Juju
---

### Post by MIGHTY_ALCHEMIST on 2011-03-08
hi,
I AM DONE WITH THE SEVER-NODE INSTALLATION AND CONNECTIVITY AND IS ABLE TO ACESS THE INTERFACE USING
 HTTPS://<CLOUD-CONTROLLER'S IP ADDRESS>:8443 
IS ALSO ABLE TO LOGIN AND DO ALL SORTS OF OTHER STUFF...
AFTER DOWNLOADING IMAGES I FOLLOWED STEP 7 GIVEN IN BELOW LINK

 [https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)

BUT WHEN I AM TRYING TO RUN THE FOLLOWING COMMANDS 
euca-authorize default -P tcp -p 22 -s 0.0.0.0/0

IT GIVES [ERRNO 113]no route to host

and, euca-run-instances $EMI -k mykey -t m1.smallIT GIVES [ERRNO 113]no route to host

please let me know if i am missing something important
 i am novice in cloud computing..

---

### Post by kim0 on 2011-03-09
Hi,
Can you pass the --debug option to the command and paste the full command and its output

---

