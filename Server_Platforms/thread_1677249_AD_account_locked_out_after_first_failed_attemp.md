---
title: "AD account locked out after first failed attemp"
date: 2011-01-28
forum: Server Platforms
---

### Post by Rendawg on 2011-01-28
After joining the client machine (running 10.10) to the windows 2003 domain  we are finding that on the first failed login attempt (passwd spelled wrong for example) the AD Domain account is locked out despite the Group Policy security setting on the Windows server set to lock out after 5 failed attempts.  

Any suggestions on how to apply the Domain lock out policy over to the Ubuntu client?  And/or an explanation as to why the authentication of a Windows domain account from the Linux machine is being treated differently then from a windows box?

Much appreciated

---

