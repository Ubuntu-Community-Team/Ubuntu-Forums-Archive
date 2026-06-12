---
title: "AD-&gt;Samba+LDAP migration"
date: 2009-10-14
forum: Server Platforms
---

### Post by kuda on 2009-10-14
Hi all!

Only one question: is it possible to only obtain Active directory users from old domain (AD) to new domain (SMB+LDAP) such that one can continue to use the old Windows domain and i can work on the new domain with new name and users can choose (testing) if they would like to join old or new one?
in other words how to obtain such stuff without acting samba as bdc(member) of old domain first.....
we have almost unusable and partly broken AD domain but i need some info like users may be groups etc ...., i have read rather much regarding to migration but in all documents it's mentioned how to migrate and begin with new samba+ldap domain with the old domain down but it is actually not what i need.
Thnx for reply in advance! k.

this is what i want:

old win.(AD) domain ----> new linux domain (SMB+LDAP)
****** (old SID)---> (users)--->(other SID)********
******************* (groups) ***********************

---

