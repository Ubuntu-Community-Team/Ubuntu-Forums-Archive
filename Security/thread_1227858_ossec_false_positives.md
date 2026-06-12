---
title: "ossec false positives"
date: 2009-07-31
forum: Security
---

### Post by noway2 on 2009-07-31
I recently installed Snort and Ossec (Thanks to Bodhi.Zazen for the excellent How To).  For over a week, I wasn't getting any Snort alerts which was caused by a typo in the configuration file: I had the protected network as 192.168.0.0/2444 - a few extra 4's.

After fixing this error, everything seemed fine, until I attempted to remotely access my email server via Squirrelmail.  It would allow me to log on and when I would attempt to read one of the messages, OSSEC would declare an attack and ban the IP.  In an attempt to figure out what was going wrong, I attempted to SSH into my server and that too caused alerts.

From the logs, I received the following from the IP address I was attempting to access from:
1- WEB-PHP read_body.php access attempt.  This is an exploit for Squirrelmail that was apparently fixed several versions earlier than the one I am using.  Squirrelmail uses read_body.php which is the offending item.

2 - WEB-CGI redirect access.  I have been attempting to research this one and I am still not sure exactly what triggered it.  This alert only showed up 1 time whereas the others triggered several as I would re-attempt to access my mail.

3 -  WEB-MISC SSLv2 openssl get shared ciphers overflow attempt.  From what I can tell, this rule applies to a vulnerability in OpenSSL that was fixed around revision 0.9.8B (I am on 0.9.8K).  One interesting thing about this one is that the PC I was using uses an RSA key instead of a password and I had been accessing it just fine via password access.

Clearly, some tweaking of the Snort rules is required.  My question is: is the appropriate response to disable these rules (override them in the local rules) as they apply to versions that have long been patched or is there a better option?

Also, what about trigger rules that are not applicable to your system.  For example, number 2 above supposedly applies to an Allaire ColdFusion Server, which I am not running.  Would one normally disable these rules or allow them on the basis that they may catch something?

---

### Post by bodhi.zazen on 2009-07-31
yes, disable those snort rules until you are able to tweak them.

ossec watches snort, so the "problem" is false positives in snort and not ossec.

You will be able to log in after 10 minutes (ossec band ip fo r10 min, which is more then sufficient to deter most people.)

---

### Post by noway2 on 2009-08-01
Bodi.zazen, I owe you another thanks :P

It didn't dawn on me at first what you meant by being a Snort rule, not an OSSEC rule and needing to disable it in Snort.  At first, I tried to add a rule to the OSSEC local rules to override these and got surprised by the unknown SID response.  It then dawned on me what you meant and I located the Snort rules and commented those out.  Restarted Snort and OSSEC and have my remote email access back.

You also raised a good point about the 10 minute lockout.  When I installed these programs, I planned a back door entry by allowing SSH connection on a non standard port to another PC which I could then use to shell into the server from the LAN address.  I first attempted this at work and got a "connection refused", which I have since determined was caused by port blocking from the company, ARGH!  The lesson here is the need to balance between security and functionality.

---

### Post by bodhi.zazen on 2009-08-02
Glad you got it straightened out =)

And you are absolutely correct, these tools almost always need a few adjustments out of the box. The general rule is that these tools will lock down oyur box, and then you select what you wish to allow.

---

