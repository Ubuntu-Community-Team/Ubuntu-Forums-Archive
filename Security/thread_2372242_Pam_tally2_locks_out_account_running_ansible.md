---
title: "Pam_tally2 locks out account running ansible"
date: 2017-09-22
forum: Security
---

### Post by mark.constant on 2017-09-22
I am trying to run an ansible script that applies the CIS security benchmark's to 16.04. The second it puts auth required pam_tally2.so onerr=fail audit silent deny=5 unlock_time=900 into /etc/pam.d/common-auth 
I get locked out from the account running the Ansible script. Says it can't sudo anymore and I can't SSH to the machine. I have found some places that state that possibly the sudo command increments failed login before the password
gets typed in for some reason. Is there a way to put this statement in and still run Ansible?

---

