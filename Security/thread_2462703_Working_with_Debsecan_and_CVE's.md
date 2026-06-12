---
title: "Working with Debsecan and CVE's"
date: 2021-05-26
forum: Security
---

### Post by civilpolisen on 2021-05-26
I've installed Debsecan and weekly I check for new updates. I have a whitelist for issues not related to our infrastructure or in our case.

Are there more admins out there doing these things on a weekly basis? How do you work? How do you solve all issues?

My greatest problem at the moment is that my current setup is very labor intensive... I would prefer a more autonomous process! :-)  I need inspiration!

---

### Post by CharlesA on 2021-05-26
Are you running the scan because you are building stuff against those packages or so you can make sure your systems are secure?

If you are worried about keeping your system up-to-date, you can install the unattended-upgrades package and set it to automatically install security updates.

---

### Post by civilpolisen on 2021-05-27
We are working with a big organization where security is an issue. Of-course... We make pods of virtual servers and the current pod is based on an older version of Ubuntu. 
I monitor the CVE's and I need to report when there are CVE's that affects our current set up and infrastructure.
Maybe there are other admins out there with a similar approach?
If so, what tools do you use to keep track of the CVE's that may do harm to your infrastructure and / or extra jobb for the organization you represent?

---

### Post by CharlesA on 2021-05-27
> **civilpolisen said:**
> We are working with a big organization where security is an issue. Of-course... We make pods of virtual servers and the current pod is based on an older version of Ubuntu. 
I monitor the CVE's and I need to report when there are CVE's that affects our current set up and infrastructure.
Maybe there are other admins out there with a similar approach?
If so, what tools do you use to keep track of the CVE's that may do harm to your infrastructure and / or extra jobb for the organization you represent?

There are several scanners out there that will scan your entire environment for vulnerabilities so you can address them. The one I've used is Nessus, but there are others like OpenVAS as well.

If you are dead set on using debscan instead of one of those applications, you might want to look into automating it via Ansible/Puppet/Chef/etc, so you don't have to manually run it on the machines.

Also, it should be noted that everything can give you a false positive or flag something that isn't really a vulnerability in your environment - that means it isn't a "run and done" tool. You still need to know enough about your environment to determine what is and what is not a legitimate vulnerability, but they should give you a place to start.

---

### Post by civilpolisen on 2021-05-28
Thank you! I'm sort of familiar with Puppet and Chef. At least, I know what they do... The issue for me, at the moment, is that I do all work manually. 

Maybe I'll build a tool myself, where I can paste the limited log and all the CVE's in this list will be linked to the actual info page for each CVE...!
This is a such a demanding task, copy / paste, that I was hoping someone would have made such solution!

But maybe I was wrong! It happens! :-)

---

### Post by deadflowr on 2021-05-28
> I was hoping someone would have made such solution!

Is this something you could try
[https://snapcraft.io/cvescan]("https://snapcraft.io/cvescan")

---

