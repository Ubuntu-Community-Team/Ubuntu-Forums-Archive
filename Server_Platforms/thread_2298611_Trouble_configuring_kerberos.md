---
title: "Trouble configuring kerberos"
date: 2015-10-12
forum: Server Platforms
---

### Post by y-tech on 2015-10-12
I've recently installed Ubuntu as a workstation client and am in the process of getting it to do authentication. One of my first step (according to [https://help.ubuntu.com/community/Samba/Kerberos](https://help.ubuntu.com/community/Samba/Kerberos)) is to install kerberos. I have downloaded and installed `apt-get install heimdal-clients`. Step one says:

1. Launch the kadmin utility as the realm administrator or as a user authorized to add principals: 

$ kadmin -p admin/admin

I'm new to kerberos and am stuck already. What are "admin/admin"? The link assumes one already knows this. According to other 
webdocs, "The format of a typical Kerberos V5 principal is primary/instance@REALM." How does this correlate with the dadmin 
example given?

---

