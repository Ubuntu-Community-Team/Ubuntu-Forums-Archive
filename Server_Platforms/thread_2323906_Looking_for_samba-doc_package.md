---
title: "Looking for samba-doc package"
date: 2016-05-09
forum: Server Platforms
---

### Post by Joff_Derluyn on 2016-05-09
I have installed Ubuntu 16.04 server to be used as domain controller. 
I have LDAP running and want to import the schema for Samba, which should be in the package samba-doc (according to the offical documentation).
I tried to apt install it, but I get the error 'E: package Samba-doc has no installation candidate'...

Any ideas how to fix this?

---

### Post by chrisott9628 on 2016-05-09
I'm having this exact issue. Have you made any progress? I can't seem to find any documentation regarding this issue...

---

### Post by bab1 on 2016-05-09
> **Joff_Derluyn said:**
> I have installed Ubuntu 16.04 server to be used as domain controller. 
I have LDAP running and want to import the schema for Samba, which should be in the package samba-doc (according to the offical documentation).
I tried to apt install it, but I get the error 'E: package Samba-doc has no installation candidate'...

Any ideas how to fix this?
What LDAP package are you using?  What documentation are referring to when you mention "according to the offical documentation"?  

There is no **samba-doc** package for Ubuntu 16.04 according to [**this listing**]("http://packages.ubuntu.com/search?keywords=samba-doc&searchon=names") for that package for each version of Ubuntu.

I have no idea why the package was dropped.  My guess is that using the *[COLOR="#9900CD"]**samba-tool**[/COLOR]* utility to configure LDAP means you don't need the information in the **samba-doc** package.

---

### Post by chrisott9628 on 2016-05-10
> **bab1 said:**
> What documentation are referring to when you mention "according to the offical documentation"?  



They are probably using this: [URL="https://help.ubuntu.com/lts/serverguide/samba-ldap.html"]https://help.ubuntu.com/lts/serverguide/samba-ldap.html
[/URL]

---

### Post by bab1 on 2016-05-10
> **chrisott9628 said:**
> They are probably using this: [URL="https://help.ubuntu.com/lts/serverguide/samba-ldap.html"]https://help.ubuntu.com/lts/serverguide/samba-ldap.html
[/URL]
The OP should answer the question.  We don't really know, do we?  That link is not the "official documentation" for any Samba server.  Certainly not for a Samba AD/DC installation.  The description clearly states: "The Samba server's role will be that of a "standalone" server"  Samba servers come in many flavors.

To provision Samba as a AD/DC you should use samba-tool.  A [**Google search**]("https://www.google.com/search?q=openldap+samba+v4.2&btnG=Go!#q=provision+ubuntu+samba+v4.2") of these keywords: **provision ubuntu samba v4.2** reveals all you need to know on how to create a Samba AD/DC domain controller.

---

