---
title: "adding ubuntu server to microsoft active directory domain"
date: 2010-03-11
forum: Server Platforms
---

### Post by cihan.dogan on 2010-03-11
When i try to join my Ubuntu server to Microsoft Active Directory domain, i get the error message below.

Kinit failed: Clock skew too great
Failed to join domain: Time difference at domain controller

I know the reason is because of the time difference between my domain controller and the Ubuntu server. But what i want to know is that possible to join a domain without time synchronisation? Because my domain controller is working for another time zone, for another Country, so i can not synchronise it with my Ubuntu server.

---

### Post by HermanAB on 2010-03-11
The clocks must be within 5 minutes of each other - sorry - that is how kerberos works.

---

### Post by dasunsrule32 on 2010-03-11
You will need to use UTC then.

---

### Post by TwoWordz on 2010-03-11
ntpdate server.domain.com

will sync your clock with the server.

---

### Post by cihan.dogan on 2010-03-11
I know that ntp is required and also how to configure it. The only issue in my situation is that i can not set the same clock of my Ubuntu Server with Microsoft Directory Server. Because one of them is located in Seattle, other is in Turkey. And each machine serves for local users. So they must work at their own local time.

Therefore, my question is that, is it possible to join an active directory domain with different time zone?

Thank you.

---

### Post by wgarider on 2010-03-13
> **cihan.dogan said:**
> I know that ntp is required and also how to configure it. The only issue in my situation is that i can not set the same clock of my Ubuntu Server with Microsoft Directory Server. Because one of them is located in Seattle, other is in Turkey. And each machine serves for local users. So they must work at their own local time.

Therefore, my question is that, is it possible to join an active directory domain with different time zone?

Thank you.

Behind the scenes, in Windows, everything based on UTC.  The time is then converted for your local time zone, that you specify.  Having the DC in a different time zone is not a problem, but if the clocks on both systems are more than 5 minutes off, you'll get errors like the one you are asking about.

---

### Post by cihan.dogan on 2010-03-14
got it. 

Thanks.

---

### Post by cihan.dogan on 2010-03-17
i found how to handle it at [http://technet.microsoft.com/en-us/library/cc780011%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc780011%28WS.10%29.aspx)  



To set Maximum tolerance for computer clock synchronization Kerberos policy by using Active Directory Users and Computers

   1. Click Start, click All Programs, click Administrative Tools, and then click Active Directory Users and Computers.
   2. Right-click the domain whose policy you wish to change, and then click Properties.
   3. Click the Group Policy tab, select the Default Domain Policy, and then click the Edit button to launch the Group Policy Object Editor.
   4. Open Computer Configuration, open Windows Settings, and then open Security Settings.
   5. Click Account Policies, double-click Kerberos Policy, and then double-click Maximum tolerance for computer clock synchronization.
   6. Increase the value in the Maximum tolerance box, and then click OK.
   7. You can wait for the policy change to propagate or you can run gpupdate /force on the client computers to force propagation immediately.


Maybe anybody else have the same issue can use it once needed.

---

### Post by mwray on 2011-04-17
Man, changing the limits on kerberos time difference is asking for man in the middle attacks. 
I think you lack understanding of NTP. The real solution is to set the Machine clocks to UTC, and set the local time zone in the OS and check the option that states that the machine time is UTC.

---

