---
title: "Ubuntu server on Amazon's EC2 -- security issues?"
date: 2011-05-27
forum: Server Platforms
---

### Post by garfonzo on 2011-05-27
Hey Folks:

I need to set up a website for a business and host confidential data that the staff/management will be accessing from various geographical locations (ie: not from within a LAN). I plan to lock down the site as much as possible using SSL and require passwords yadda yadda yadda. 

From a security perspective, are there any differences between doing all of the above on my own purchased server which physically sits in my office versus purchasing an Amazon EC2 machine instance and doing it all in the cloud? Someone in a different thread mentioned the issue with EC2 is a lack of encryption on your data. However, can't that also be an issue with my own server and, to solve the issue for both scenarios (EC2 and my own server) I would just need to encrypt the data on the Hard Drives? 

What else would be a factor that would make the EC2 route inherently less secure in comparison to having my own box?

Your thoughts?

---

### Post by doas777 on 2011-05-27
Rule #1 of technology security:

Physical Access = Root Access. Period.

with a server in your office, you can probably count on one hand how many folks have access to the box. on an EC2 instance, you have thousands of Amazon employees, and anyone who manages to hack their management systems.

---

### Post by garfonzo on 2011-05-27
> **doas777 said:**
> Rule #1 of technology security:

Physical Access = Root Access. Period.

with a server in your office, you can probably count on one hand how many folks have access to the box. on an EC2 instance, you have thousands of Amazon employees, and anyone who manages to hack their management systems.

That is a terrifying good point.

---

### Post by spynappels on 2011-05-28
> **doas777 said:**
> Rule #1 of technology security:

Physical Access = Root Access. Period.

with a server in your office, you can probably count on one hand how many folks have access to the box. on an EC2 instance, you have thousands of Amazon employees, and anyone who manages to hack their management systems.

While this is true, you need to balance that with the fact that these employees have had to sign NDA/Confidentiality agreements and are unlikely to be very interested in small individual servers in any case.

Local is probably more secure, but unless you are extremely paranoid, the difference is negligible. You need to weigh the costs against the benefits for both options, but don't feel that all the Amazon employees are just waiting to compromise the security of YOUR instance.

If it was so insecure, enterprise would not use it....

---

