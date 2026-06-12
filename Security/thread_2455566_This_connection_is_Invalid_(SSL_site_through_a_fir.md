---
title: "This connection is Invalid (SSL site through a firewall with SSL inspection)"
date: 2020-12-22
forum: Security
---

### Post by dbrown9018 on 2020-12-22
Hi everyone,
I'm running Ubuntu 20.04 and have issues connecting to some internal SSL web sites.  For our firewall, we are using Fortigate with SSL deep inspection enabled.  I have copied the Fortigate certificate to a folder in /usr/local/share/ca-certificates/ and after sudo update-ca-certificates I got feedback that 2 new certs were added.  However, I have tried Chrome, Firefox and Gnome Web and receive the IDENTICAL message in all three browsers.  Here is one example.  In all cases the certificates are self-signed.  There was no issue with my prior version of Ubuntu (19).  I'm a little new to Linux.  Probably know enough to get into trouble, but does anyone have any ideas as to how I can enable the browsers to connect?  Thank you

Error message:

[TABLE="width: 0"]
[TR]
[TD][/TD]
[TD="align: right"][/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]**This Connection is Invalid**
[/TD]
[/TR]
[/TABLE]


[FONT=&amp]A secure connection to ehpsvcs.ci.east-hartford.ct.us cannot be established.[/FONT]
[FONT=&amp]Normally, when you try to connect securely, sites will present trusted identification to prove that you are going to the right place. However, this site's identity can't be verified.[/FONT]
[TABLE="width: 0"]
[TR]
[TD]Site:[/TD]
[TD]ehpsvcs.ci.east-hartford.ct.us[/TD]
[/TR]
[TR]
[TD]Certificate CN:[/TD]
[TD]ehpsvcs.ci.east-hartford.ct.us[/TD]
[/TR]
[TR]
[TD]Certificate Authority:[/TD]
[TD]ehpsvcs[/TD]
[/TR]
[TR]
[TD]Certificate Validity:[/TD]
[TD]Not Before: Apr 27 17:35:23 2018 GMT
Not After: Apr 21 17:45:23 2028 GMT[/TD]
[/TR]
[/TABLE]

---

### Post by &amp;KyT$0P# on 2020-12-22
Firefox has its own certificate database and I think Chrome does too.  Did you try importing your certificate into Firefox using Firefox's own settings page? (Edit > Preferences > Privacy & Security > Certificates > View Certificates, import as an authority.)

---

### Post by dbrown9018 on 2020-12-30
I did try that, but I get an error from Firefox telling me it's not an authority certificate.  However, it did work in Windows.

---

