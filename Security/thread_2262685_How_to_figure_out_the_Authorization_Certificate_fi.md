---
title: "How to figure out the Authorization Certificate file been used"
date: 2015-01-26
forum: Security
---

### Post by deme2 on 2015-01-26
I can log in successfuly to certain Citrix Virtual Machine from Ubuntu. But I want to add this functionality to my smartphone running Android. Unfortunetlly I can not log in because I don't have the correct CA file in my Android.  Citrix receiver is properly installed in Android and I know how add an extra CA in Android but I have no idea how figure which one is been used when I log from Firefox/Ubuntu.

---

### Post by Habitual on 2015-01-27
Possible help in identifying which CA is being used:
Open a terminal on a system that has access to the Citrix VM and issue
```
echo | openssl s_client -connect <IP_or_dns_name_of_host>:<port> | grep -i subject
```

or  run it without the "| grep -i subject" take the entirety of the certificate  from
```
-----BEGIN CERTIFICATE----- 
```to 
...
```
-----END CERTIFICATE-----
``` including those certificate markers to [https://www.sslshopper.com/certificate-decoder.html](https://www.sslshopper.com/certificate-decoder.html) and enter the contents.
They should match the output of the command used with the "grep -i subject" above.

Hope that helps.

---

