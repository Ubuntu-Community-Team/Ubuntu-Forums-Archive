---
title: "Ubuntu 8.04 Postfix + Amavis + Clamd problem"
date: 2008-06-06
forum: Server Platforms
---

### Post by JarekJ on 2008-06-06
Hi all,

I've decided to install my new mail serwer on Ubuntu Hardy. I know that this is rather fresh but - why not. ;)

Unfortunetly I found some problems with amavis and clamav.
I folowed instructions from here: 
[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

I met problem with 

amavis[30807]: (30807-01) (!!) ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/amavis-20070615T125025-30807/parts: lstat() failed. ERROR\n

I did try solutions given in above URL (changing permissions on /var/lib/amavis/tmp) - but no success.

I found that everything is OK when I change (in amavis conf) primary AV scanner from clamd to clamscan but I would like to have primary scanner set to clamd, because I think it is more robust then clamscan.

I don't know if disabling of apparmor would help...

If you have any suggestions - please share with me.

---

### Post by gtdaqua on 2008-06-06
Sure you want to build everything yourself? 

Try Zimbra or Citadel?

---

### Post by JarekJ on 2008-06-06
> **gtdaqua said:**
> Sure you want to build everything yourself? 

Try Zimbra or Citadel?

Yes, I'm sure. :)

Zimbra or Citadel are very nice web additions but I want to setup mail server with antivirus and antispam. After that I will look for WebMail client.

Jarek

---

### Post by kuam on 2008-07-01
I ran into this issue today after following the installation instruction found on [http://help.ubuntu.com](http://help.ubuntu.com). Here's what I did to resolve the problem:

1) As stated in the install doc, I issued this from the command line:

sudo chmod -R 775 /var/lib/amavis/tmp

2) In /etc/group, make sure that your setup is similar to this:

clamav:x120:amavis
amavis:x121:clamav

For me, "clamav" was not in the "amavis" group.

Note: the ubuntu forum replaced the colon ( and "x" as an angry face.

---

### Post by windependence on 2008-07-02
> **JarekJ said:**
> Yes, I'm sure. :)

Zimbra or Citadel are very nice web additions but I want to setup mail server with antivirus and antispam. After that I will look for WebMail client.

Jarek

You didn't read much about either of these did you? If you did, you wouuld see that they are not just webmail but full fledged mail servers with AV and antispam built right in. This is the point gtdqua was trying to make.

Anyway if you are interested, here is the Zimbra tutorial:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

-Tim

---

