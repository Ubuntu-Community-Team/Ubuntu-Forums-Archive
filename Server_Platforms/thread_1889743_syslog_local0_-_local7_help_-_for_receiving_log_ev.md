---
title: "syslog local0 - local7 help - for receiving log event from cisco asa"
date: 2011-12-01
forum: Server Platforms
---

### Post by e24ohm on 2011-12-01
Folks,
I am trying to understand the local0 - local7 facility usage. I understand that daemons use these to log events; however, what local0 - local7 facility do I pick to receive my ASA events?

I believe local7 is boot events - does anyone have a list of what the default local0 - level7 are used for? Which one do I select to receive my ASA events?

thanks.

---

### Post by jonobr on 2011-12-02
Do the old PIX pages on the cisco pages help 

[Levels]("http://www.cisco.com/en/US/products/hw/vpndevc/ps2030/products_tech_note09186a0080094030.shtml") shown halfway down
Given the description, I would have figured boot events would be 4 or 5?



> emergency
	

0

alert
	

1

critical
	

2

error
	

3

warning
	

4

notification
	

5

informational
	

6

debug
	

7

---

### Post by cdukes on 2011-12-06
Jonobr, those aren't Facilities, they are Severities.

E24ohm,
The Facility is an integer from 0-23 that indicates the sending facility such as kernel, mail, etc. Back in the old days, people would use them to sort on (like send mail to mail.log, kernel to kernel.log). The protocol was designed to allow for locally assigned values, meaning, you can put whatever you want there - over the years, many devices would just use local7 (which is int 23).

All that said, none of it *really* matters, because today's logging systems are capable of much better filtering :)

Here's a whitepaper I published on Cisco's website a while back that explains this, and more, if you are interested:
[http://www.cisco.com/en/US/technologies/collateral/tk869/tk769/white_paper_c11-557812.html](http://www.cisco.com/en/US/technologies/collateral/tk869/tk769/white_paper_c11-557812.html)

---

### Post by jonobr on 2011-12-06
cdukes , sweet .... its a sad day you dont leanr something, and I have had a few days recently..:-)

---

### Post by SeijiSensei on 2011-12-06
Applications that log to the local facilities usually have to be configured as to which of the facilities to use.  I run a couple of applications that log to local facilities; I have to specify which one to use (e.g., "local3") in a configuration file, then add an entry to rsyslog.conf for "local3.*".  You can define it in a separate file in /etc/rsyslog.d/.  Follow the example for user.* in /etc/rsyslog.d/50-default.conf.

---

### Post by e24ohm on 2011-12-10
> **cdukes said:**
> Jonobr, those aren't Facilities, they are Severities.

E24ohm,
The Facility is an integer from 0-23 that indicates the sending facility such as kernel, mail, etc. Back in the old days, people would use them to sort on (like send mail to mail.log, kernel to kernel.log). The protocol was designed to allow for locally assigned values, meaning, you can put whatever you want there - over the years, many devices would just use local7 (which is int 23).

All that said, none of it *really* matters, because today's logging systems are capable of much better filtering :)

Here's a whitepaper I published on Cisco's website a while back that explains this, and more, if you are interested:
[http://www.cisco.com/en/US/technologies/collateral/tk869/tk769/white_paper_c11-557812.html](http://www.cisco.com/en/US/technologies/collateral/tk869/tk769/white_paper_c11-557812.html)

Thanks for the link - that sucker is good.

cheers mate.

---

### Post by e24ohm on 2011-12-10
Folks,
thank you for all the posts and suggestions.

---

