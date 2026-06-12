---
title: "A question about nss-ldap.conf"
date: 2011-11-28
forum: Server Platforms
---

### Post by MetalORB on 2011-11-28
Hello,

I want to ask a question about nss-ldap.conf syntax. I couldn't understand how to configure pam_member_attribute property. In the configuration the property was setup like:

pam_member_attribute uniquemember

However, I haven't configured a "uniquemember" in the groups OU. I have uid, uidNumber, gidNumber defined. In example configurations, this "pam_member_attribute" property is always set, but they do not explain what it means or how to configure properly.  I have googled already, but couldn't find any reasonable explanation about this property. Do you have any idea about configuring "pam_member_attribute"?  Thanks :)

EDIT: Anyway, I have solved what "pam_member_attribute" means and how it behaves.

---

