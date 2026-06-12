---
title: "euca-run-instances  is terminating"
date: 2011-01-19
forum: Ubuntu Cloud and Juju
---

### Post by shesha1 on 2011-01-19
Hi all,
 
sorry for my poor english.
 
I m trying to install cloud computing, I reffered below url
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)
 
in this after giving below command 
 
#euca-run-instances $EMI emi-DE8E105D -t m1.large
 
the result is 
 
RESERVATION r-50400936 admin admin-default
INSTANCE i-4B6708A8 emi-DE8E105D 0.0.0.0 0.0.0.0 pending 0 m1.large 2011-01-19T11:29:35.033Z SONATA eki-F4D210DE eri-094B1151
 
 
after some time pending will go to terminated
 
please help me for this.
 
Regards
shesha

---

### Post by kim0 on 2011-01-19
Can you please try creating a different user than admin, download credentials for that user, and try running your image using it ?

---

### Post by shesha1 on 2011-01-19
after giving this command 
euca-run-instances emi-DF1D1066 -k mykey -t c1.medium
the result is this
RESERVATION r-3AA705D3 admin default
INSTANCE i-369506BE emi-DF1D1066 172.23.200.21 172.19.1.2 terminated mykey 0 c1.medium 2011-01-20T04:10:04.3
94Z SONATA eki-F58D10F7 eri-09CD114C
but one thing i am not understanding my cloud server ip is 172.23.200.20
and node ips are 172.23.200.21 & 172.23.200.22 but why 172.19.1.2 is coming, 
Please help me to resolve this issue.

---

### Post by kim0 on 2011-01-20
Hi can you please post the result of "ifconfig" on the cloud controller and the node controller. Also did you use a different user than admin. What is the output of euca-describe-availability-zones

---

