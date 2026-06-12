---
title: "Dependencies errors."
date: 2005-07-12
forum: Repositories &amp; Backports
---

### Post by Umbra on 2005-07-12
I got mostly the same following erros when trying to install packages with apt-get:

```
The following packages have unmet dependencies:
  gaim: Depends: gaim-data (= 1:1.3.1~5.04ubp1) but it is not going to be installed
        Depends: libatk1.0-0 (>= 1.9.0) but it is not going to be installed
        Depends: libgtk2.0-0 (>= 2.6.0) but it is not going to be installed
        Depends: libgtkspell0 (>= 2.0.2) but it is not going to be installed
        Depends: libpango1.0-0 (>= 1.8.1) but it is not going to be installed
  kdepim: Depends: karm (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
          Depends: korganizer (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
          Depends: kpilot (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
``` 


I have already updated my sources.list with the one specified in obuntuguide.org

---

### Post by scoon on 2005-07-12
Hey there, 

Have you tried apt-get check ?


regards. 

scoon

---

### Post by codejunkie on 2005-07-12
[QUOTE=Umbra]I got mostly the same following erros when trying to install packages with apt-get:

```
The following packages have unmet dependencies:
  gaim: Depends: gaim-data (= 1:1.3.1~5.04ubp1) but it is not going to be installed
        Depends: libatk1.0-0 (>= 1.9.0) but it is not going to be installed
        Depends: libgtk2.0-0 (>= 2.6.0) but it is not going to be installed
        Depends: libgtkspell0 (>= 2.0.2) but it is not going to be installed
        Depends: libpango1.0-0 (>= 1.8.1) but it is not going to be installed
  kdepim: Depends: karm (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
          Depends: korganizer (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
          Depends: kpilot (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
E: Unmet dependencies. Try '[COLOR=Blue]apt-get -f install[/COLOR]' with no packages (or specify a solution).
``` 


I have already updated my sources.list with the one specified in ubuntuguide.org[/QUOTE]

do what apt-get suggested ```
sudo apt-get -f install
``` that should fix the problem it will download and install the dependencies automatically.

---

### Post by Umbra on 2005-07-12
With -f intall or --fix-broken i got the same result.

---

### Post by Umbra on 2005-07-12
Same with apt-get check, i got the same missing dependencies as a diagnostic.

What can i do.

---

### Post by beko on 2005-07-12
I have the same problem & I thnk that always happend when apt start getting somthing from Us archives mirror like this (Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/li](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/li) bsndfile1_1.0.10-2_i386.deb  MD5Sum mismatch)
That always happend nowadays I don't know why although I just installed a clean installation. ](*,)

---

### Post by scoon on 2005-07-12
Hey there, 

There are posts about that.  Try removing the us. on all of  your sources. 

regards, 

scoon

---

### Post by Umbra on 2005-07-12
[QUOTE=beko]I have the same problem & I thnk that always happend when apt start getting somthing from Us archives mirror like this (Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/li](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/li) bsndfile1_1.0.10-2_i386.deb  MD5Sum mismatch)
That always happend nowadays I don't know why although I just installed a clean installation. ](*,)[/QUOTE]

Clean install of what?

Help me.

---

### Post by beko on 2005-07-12
[QUOTE=Umbra]Clean install of what?

Help me.[/QUOTE]
 yesterday b4 I know this way by removing the US from the addresses I tried many ways I even add Repository from Debian sources but this didn't fix that so I decided to make a clean installmaybe something wrong with the system but the problem was still there, but now when I tried to remove the US from the addresses like that ( [http://us.archive.ubuntu](http://us.archive.ubuntu)  TO BE  [http://archive.ubuntu](http://archive.ubuntu)) it worked fine so thanks for who descover that way

---

### Post by huh? on 2005-07-16
sure am glad this forum exists...been having the md5sum mismatch errors for the last several days...maybe this will solve the problems...will delete the "us" portion of sources.list and see what happens...been driving me crazy for the last several days...but, figured it had some thing to do with sources.list, cuz the same problem kept cropping up in 2 different boxes, and both boxes had worked in the past...I just keep changing back and forth between ubuntu and kubuntu...
 thanks to whoever came up with the fix...

---

### Post by huh? on 2005-07-16
ok, just changed the sources.list and everything that I wanted is now running....many thanks to all who contribute to this forum

---

