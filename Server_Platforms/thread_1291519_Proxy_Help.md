---
title: "Proxy Help"
date: 2009-10-14
forum: Server Platforms
---

### Post by akross6966 on 2009-10-14
Hello everyone.  I am running 9.04 desktop 32-bit and have a question.  I have a need at my church to allow teenagers and young adults internet access but need to filter what they have access to.  

Here is what i am wanting to do and you tell if this is doable or not.  I want people to be able to login to the network so they would have internet access.  I was thinking the ubuntu box would act like a proxy and filter sites they had access to.  The box  would also send an email to a specified address if certain sites were accessed.  I would like a web interface to where someone could administer usernames and pass' to access the internet when i am not around.  I have seen wifidog, but didn't know if this would be appropriate.  

Any help is most appreciated.  Thanks.

---

### Post by BQAggie2006 on 2009-10-14
It is totally doable. You can run either Squid or DansGuardian as a proxy and use LDAP or NIS as a central authentication service so everyone could have their own account. You can use Webmin which is a web-based administration GUI to administer all these services.
 
If you don't want to set all that up, you can check out Ubuntu Christian Edition. It already has DansGuardian installed with an administration GUI and you can just create individual accounts for all the users on the local machine.

---

