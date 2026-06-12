---
title: "Ubuntu dapper ClamaAV"
date: 2006-09-13
forum: Server Platforms
---

### Post by dregan on 2006-09-13
HI,

when I run "apt-get install clamav clamav-base clamav-freshclam clamtk libclamav1 clamav-daemon" (installing clamav on its own does not seem to install any conf files or daemons)

I get an error message:

The following packages have unmet dependencies:
  clamav-daemon: Depends: clamav-base (= 0.88.2-1ubuntu1) but 0.88.4-0volatile1 is to be installed
  clamav-freshclam: Depends: clamav-base (= 0.88.2-1ubuntu1) but 0.88.4-0volatile1 is to be installed
E: Broken packages

I am not sure of interpretation of error messages - but nothing seems to be installed.

I have spent at least 7+ working days and nights on this - please help if you can?

---

### Post by apjone on 2006-09-13
> **dregan said:**
> HI,

when I run "apt-get install clamav clamav-base clamav-freshclam clamtk libclamav1 clamav-daemon" (installing clamav on its own does not seem to install any conf files or daemons)

I get an error message:

The following packages have unmet dependencies:
  clamav-daemon: Depends: clamav-base (= 0.88.2-1ubuntu1) but 0.88.4-0volatile1 is to be installed
  clamav-freshclam: Depends: clamav-base (= 0.88.2-1ubuntu1) but 0.88.4-0volatile1 is to be installed
E: Broken packages

I am not sure of interpretation of error messages - but nothing seems to be installed.

I have spent at least 7+ working days and nights on this - please help if you can?

have you tried 

apt-get install -f                ?

---

### Post by dregan on 2006-09-13
Thank you for your reply,

I hadn't - so I did - unfortunately, it had the same results.

I then tried apt-get --purge remove clamav

then apt-get -f install .....

Makes no difference.  Thanks anyway.

Danny

---

### Post by dregan on 2006-09-14
Yes - no luck - very perplexing!

---

