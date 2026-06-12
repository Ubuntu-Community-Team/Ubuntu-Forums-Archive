---
title: "SELinux: implementation."
date: 2009-07-22
forum: Security
---

### Post by steffff on 2009-07-22
Hello guys!

I would like to ask you experts if you can recommend some documentation about the SELinux implementation. I have already looked through the NSA website (papers, technical reports, presentations) and some books chapters unsuccessfully, in the sense that they are, let me say, high-level. I didnt get any answer from the NSA mailing list. I also tried to have a look at the code, but it's not that easy :D

The questions I m looking for an answer to are about how a policy is managed, accessed and searched in SELinux. I understood that SELinux first searches the AVC (a short list of rules) for it, then if it's not there somewhere else... in the access vector table (a hash-table in avtab.h/c)? Finally, the policy is stored in a binary file... is it managed as a database? What is the link between the binary file and the avtab?

Thank you i advance for any help! 

Stefano

---

### Post by ibutho on 2009-07-22
Take a look at [http://www.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5/html/Deployment_Guide/selg-overview.html]("http://www.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5/html/Deployment_Guide/selg-overview.html") and [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/selinux-guide/]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/selinux-guide/").

---

### Post by bodhi.zazen on 2009-07-22
No offense, but the Fedora and Centos forums are better to ask as very few here at Ubuntu use selinux.

The Centos redhat fedora documentation is all good. If you want more google is your friend.

---

### Post by The Tronyx on 2009-07-22
SELinux is like network access control, it sounds really good in theory, but in practice it just kind of sucks to implement properly.

---

