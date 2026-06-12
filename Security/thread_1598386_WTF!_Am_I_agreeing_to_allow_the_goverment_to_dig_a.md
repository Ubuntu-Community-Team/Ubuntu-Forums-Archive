---
title: "WTF?! Am I agreeing to allow the goverment to dig around in my server?"
date: 2010-10-16
forum: Security
---

### Post by Onryo on 2010-10-16
I have a rather secure server that I have hardened. Only allow ssh non stranded port and the port 80 for my LAMP. Use aa for everything. The server uses Snort as an IDS and PSAD (port scan attack detection). The firewall is a custom in-line IPT using fwSnort rules.   This one was off the chain! As I was upgrading from the 10.04 LTS to 10.10 I was reading ever new file that was being put on my disk with &quot;D&quot; Ubuntu asked me if I wanted to replace the old file with this one! WTF?!?!?!   Could somebody who knows what they are talking about tell me what this is all about. I am seriously considering going back to OpenBSD.     

cat /etc/issue    

*************************************************************************** 
                            NOTICE TO USERS   
This computer system is the private property of Onryo (blanked out), Norrkoping Sweden, whether  individual, corporate or government.  It is for authorized use only.  Users (authorized or unauthorized) have no explicit or implicit  expectation of privacy.    Any or all uses of this system and all files on this system may be  intercepted, monitored, recorded, copied, audited, inspected, and  disclosed to your employer, to authorized site, government, and law  enforcement personnel, as well as authorized officials of government  agencies, both domestic and foreign.    By using this system, the user consents to such interception, monitoring,  recording, copying, auditing, inspection, and disclosure at the  discretion of such personnel or officials.  Unauthorized or improper use  of this system may result in civil and criminal penalties and  administrative or disciplinary action, as appropriate. By continuing to  use this system you indicate your awareness of and consent to these terms  and conditions of use. LOG OFF IMMEDIATELY if you do not agree to the  conditions stated in this warning.    **************************************************************************** 

All the best

---

### Post by CharlesA on 2010-10-16
That's just the motd deal when you login via SSH.

That file on my machine says:

```
charles@atlantis:~$ cat /etc/issue
Ubuntu 10.04.1 LTS \n \l
```

Same on my maverick machine:

```
charles@maverick:~$ cat /etc/issue
Ubuntu 10.10 \n \l


```

EDIT: Check [here]("http://www.cyberciti.biz/faq/howto-change-login-message/") for some info on the /etc/issue file.

---

