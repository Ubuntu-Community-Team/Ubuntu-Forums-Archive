---
title: "problem with sftp"
date: 2012-03-05
forum: Server Platforms
---

### Post by tapi0n on 2012-03-05
So I used an old computer I had around to set up a lamp. All good and well but when I try to upload files using filezilla I get an odd problem. Sometimes it connects without any problems and I can upload files like a crazy man. But in 50% of the cases I can't log in, and when I finally get logged in I can't upload due to 'connection lost to the server'. 

I tried looking in different logs but can't find anything related to the issue. 

Anyone who's got an idea as to where I could find a possible answer?

Cheers.

---

### Post by winh8r on 2012-03-05
Might be a problem with either firewall settings or timeouts. look here for further info:  [http://wiki.filezilla-project.org/Network_Configuration#Troubleshooting]("http://wiki.filezilla-project.org/Network_Configuration#Troubleshooting")

hope this points you in the right direction.

---

### Post by tapi0n on 2012-03-05
There is no firewall active whatsoever (it's just internal network, not connected to the outside) and I'm not really working with large files (avarage of like 15 kb per file).

But no harm in checking the entire page when I get home, thanks for the input.

---

### Post by spynappels on 2012-03-05
Is there any reason that the network connection could be being saturated sometimes? Is there other traffic on the network?

---

### Post by tapi0n on 2012-03-05
Nah I'm the only one using it.

Could the fact that the machine is very old have something to do with it?

---

