---
title: "Replacing Windows 2008R2 SBS with Ubuntu Server/SMB(2)"
date: 2011-10-02
forum: Server Platforms
---

### Post by almnahal on 2011-10-02
I am seriously considering replacing a Windows 2008R2 SBS PDC system with Ubuntu server 64 bit and Samba.  To do this I will need to migrate the AD information from the 2008R2 to the Ubuntu/SMB2 server before shutting it down.  The question as to why, is that the original server was installed, IMHO, badly and with several serious disadvantages.  Attempting to replace it with another 2008R2 SBS machine created even more disastrous issues, again the details of which I'm not going into.  My ONLY questions are "has anyone successfully replaced a 2008R2 SBS PDC with Ubuntu/SMB(2) and is there a step by step or serious set of hints for the successful replacement?" Before I spend any more time on trying to do it, I would like to know if it HAS been done.  If its a no, then that will tell me I will have to do some very time consuming and painful steps on each individual client to make these servers go away without losing local data/configurations when the 'domain' logins disappear.  Any help will be appreciated.  Thanks.

---

### Post by headvampyre@hotmail.co.uk on 2011-10-02
Are you storing files (Such as roaming profiles, home directories, etc.) on the server aswell? If you are, you might want to have a look at samba franky (It's basically running Samba3 and Samba4 on the same machine, I haven't tested it, but it should be stable). Otherwise, it should be fairly easy with Samba4. 

[http://wiki.samba.org/index.php/Samba4/HOWTO#Joining_a_Windows_domain_controller_as_an_additional_DC_in_a_domain](http://wiki.samba.org/index.php/Samba4/HOWTO#Joining_a_Windows_domain_controller_as_an_additional_DC_in_a_domain)

^^ I would read that first.

So basically you'll need a second machine and install Linux, samba4 and bind9 on it. Then:
> 
1) Join Samba4 to the domain:
[http://wiki.samba.org/index.php/Samba4/HOWTO/Join_a_domain_as_a_DC](http://wiki.samba.org/index.php/Samba4/HOWTO/Join_a_domain_as_a_DC)

2) Check that Samba4 has replicated properly with dsa.msc
3) Leave the machine with Linux on running, then on the machine with windows server, install Linux on that
4) Install Samba4+Bind9 on the old windows server
5) Join the domain the replicated server is hosting
6) Uninstall bind9 on the temporary machine
7) Replicate AD onto the old windows server
8) Check the replication ran fine
9) Demote the temporary server


Sorry if it's a little difficult to understand, but it should work :) And Samba4 is pretty stable :)

---

### Post by koenn on 2011-10-02
> **almnahal said:**
> I am seriously considering replacing a Windows 2008R2 SBS PDC system with Ubuntu server 64 bit and Samba. 
... 
My ONLY questions are "has anyone successfully replaced a 2008R2 SBS PDC with Ubuntu/SMB(2) and is there a step by step or serious set of hints for the successful replacement?".
Wrong question.
ADS has is a combination of many roles and features, and SBS adds some more. Even if someone somewhere replaced a a Windows 2008R2 SBS AD envoronment by Linux, Samba, and some other stugg, that would be no guerantee the same migration steps would work for your environment


>  ... then that will tell me I will have to do some very time consuming and painful steps on each individual client to make these servers go away without losing local data/configurations when the 'domain' logins disappear. Any help will be appreciated. Thank

Read Microsoft's guides and papers on domein migration, and/or look into scripted solutions to collect configuration data in one domain and apply it in another.

---

### Post by Vegan on 2011-10-02
you can use Linux and the server 2008r2 machine side by side fine

---

### Post by Alan5127 on 2011-10-25
Hi Almnahal,
 
Just wondering how you got on?
 
If you have, or are still planning to proceed, I would love to leverage off your efforts to date :-)
 
Thanks,
 
Alan.

---

