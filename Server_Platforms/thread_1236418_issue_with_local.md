---
title: "issue with local"
date: 2009-08-10
forum: Server Platforms
---

### Post by mansonthomas on 2009-08-10
Hi,

 I've installed a 'tunned' ubuntu server 9.04 which is host by a company. (I mean I don't have the hand on the installation process).

 When I do a aptitude update I get theses warning over and over : 


[PHP]Get:47 http://security.ubuntu.com jaunty-security/main ntpdate 1:4.2.4p4+dfsg-7ubuntu5.1 [66.3kB]
Get:48 http://security.ubuntu.com jaunty-security/main openssl 0.9.8g-15ubuntu3.2 [402kB]
Fetched 42.2MB in 3s (12.0MB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.ISO-8859-15"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Extracting templates from packages: 100%
Preconfiguring packages ..[/PHP]


running this didn't helped : 

[PHP]root@sd1:~# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.ISO-8859-15"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.ISO-8859-1... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.[/PHP]


any ideas ? 

Regards,
Thomas

---

### Post by samosamo on 2009-08-10
[http://lmgtfy.com/?q=perl%3A+warning%3A+Setting+locale+failed.+](http://lmgtfy.com/?q=perl%3A+warning%3A+Setting+locale+failed.+)

Oh, look what I have found

```
sudo locale-gen
```

---

### Post by mansonthomas on 2009-08-10
It doesn't works... i've googled too


[PHP]root@sd1:~# locale-gen
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.ISO-8859-1... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
root@sd1:~# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.ISO-8859-15"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.ISO-8859-1... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
[/PHP]

---

### Post by mansonthomas on 2009-08-11
Anybody? an idea?

---

