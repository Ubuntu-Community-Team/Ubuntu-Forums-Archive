---
title: "Couldn't find package - Webmin"
date: 2011-03-27
forum: Server Platforms
---

### Post by boldford on 2011-03-27
When entering 

**sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl **

as part of the Webmin istall process I'm getting the return

**Couldn't find package libnet-ssleay-perl**

can anyone show me where I'm going wrong or what the prolem might be please?

****

---

### Post by BkkBonanza on 2011-03-27
It should be there. **aptitude search libnet-ssleay-perl** shows package for me.
What release are you using? 10.10?

Check your sources.list and make sure you have correct repos & versions for your release. For some reason it's not seeing the package.

less /etc/apt/sources.list

---

### Post by boldford on 2011-03-27
10.04 64bit less

---

### Post by BkkBonanza on 2011-03-27
Also be sure to do a **sudo apt-get update** first in case a repo has changed and it's gotten out of sync.

I did a simulation run here (with -s) and it worked ok. I'm on 10.10.

---

### Post by boldford on 2011-03-27
It's not keen on that either

---

### Post by BkkBonanza on 2011-03-27
I gather you mean that **apt-get update** also has problems? 
Post the output of that here if possible.

---

### Post by mw4jet on 2011-03-27
Edit: Missread the package that was needed, my response does not apply.
 
Mark

---

### Post by boldford on 2011-03-27
I managed to get it going again after a complete reinstall of 10.04SE plus the procedure on webmin.com. It works OK now but I'm still unsure why it didn't before.

---

### Post by R.Bucky on 2011-03-27
Next time:

things to check before you reinstall: 
1.make sure that you have all of the basic repos enabled in your sources.list
2.check your /var/log/dpkg.log for potential clues

---

