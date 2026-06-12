---
title: "perl: warning: Setting locale failed."
date: 2009-12-05
forum: Server Platforms
---

### Post by ejmadar on 2009-12-05
All other threads were closed already, so i started a new one. It may spare some time for you. 

I have a virtual private server running Ubuntu 9.10 and got messages like this:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```To get rid of the messages I had to run this command:

```
# locale-gen en_US en_US.UTF-8 hu_HU hu_HU.UTF-8
```then

```
# dpkg-reconfigure locales
```The problem was solved. I didn't had to edit any files like /etc/environment
Hope it helps for you!

I found the solution here:
[http://www.linuxquestions.org/questions/showthread.php?p=3540541#post3540541](http://www.linuxquestions.org/questions/showthread.php?p=3540541#post3540541)

---

### Post by gerrywastaken on 2010-03-15
didn't fix the error for me

---

### Post by sneils on 2010-03-18
Worked fine for me, thx. :)

---

### Post by ajeje on 2010-05-03
Works for me as well! Thanks.

---

### Post by matthewboh on 2010-07-27
Didn't work for me either

---

### Post by Dafydd on 2010-09-23
> **matthewboh said:**
> Didn't work for me either

Worked perfectly for me (Ubuntu 10.04). I just ran:

sudo locale-gen en_US en_US.UTF-8 cy_GB.UTF-8


Replaced hungarian (hu) for Welsh (cy).

---

### Post by glendeni on 2011-01-30
Worked for a new install of 10.04 with added KDE desktop, for which running many applications (perl, firefox) gave "setting locale" error messages when run in Konsole. "sudo locale-gen en_US en_US.UTF-8" solved that problem for me.  I kiss the toes of [ejmadar]("http://ubuntuforums.org/member.php?u=971525") for saving me _much_ time and aggravation .

---

### Post by demauk on 2011-03-31
You need to pay attention to your error message and issue a command for your missing locale.

For example, this is the error I got:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_CA:en",
	LC_ALL = (unset),
	LANG = "en_CA"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

The LANG string is the one you need. So, in my case this command solved my problem:

```
$ sudo locale-gen en_CA
```

---

### Post by Heels on 2011-04-08
Hi all, 

I installed ubuntu 10.10 a week ago, and got my vodaphone mobile broadband up and running. then some update was installed (usb modeswitch something) and... I couldn't get vodaphone to start. I got the same issues a in this thread, and with your suggestions I've actually managed to get it running (even though I don't have a clue what I'm actually doing :D). So now the application starts up, says its connected, but then I STILL have no internet. 

The wierd thing is: when I left click on the internet icon, I can check enable mobile broadband, but as soon as I touch anything in firefox, the 'check mark' has disappeared... 

So: 1) thanks for all your help so far, and 2) has anyone got a clue what I can try now??

---

### Post by willPower on 2011-04-10
> **Heels said:**
> Hi all, 

I installed ubuntu 10.10 a week ago, and got my vodaphone mobile broadband up and running. then some update was installed (usb modeswitch something) and... I couldn't get vodaphone to start. I got the same issues a in this thread, and with your suggestions I've actually managed to get it running (even though I don't have a clue what I'm actually doing :D). So now the application starts up, says its connected, but then I STILL have no internet. 

The wierd thing is: when I left click on the internet icon, I can check enable mobile broadband, but as soon as I touch anything in firefox, the 'check mark' has disappeared... 

So: 1) thanks for all your help so far, and 2) has anyone got a clue what I can try now??

You could try starting a new thread.

---

### Post by Heels on 2011-04-11
gee, thanks! :D :D :D

---

### Post by stoof on 2011-04-16
> **demauk said:**
> You need to pay attention to your error message and issue a command for your missing locale.

For example, this is the error I got:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_CA:en",
	LC_ALL = (unset),
	LANG = "en_CA"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

The LANG string is the one you need. So, in my case this command solved my problem:

```
$ sudo locale-gen en_CA
```

THIS.

Thank you.

---

### Post by kuhnza on 2011-10-30
> **demauk said:**
> You need to pay attention to your error message and issue a command for your missing locale.

For example, this is the error I got:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_CA:en",
	LC_ALL = (unset),
	LANG = "en_CA"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

The LANG string is the one you need. So, in my case this command solved my problem:

```
$ sudo locale-gen en_CA
```
Great answer, did the trick for me. 

Thanks!

---

### Post by amd-64 on 2012-02-28
I found I needed to add 
```

setenv LANG "en_CA"
setenv LANGUAGE "en_CA.UTF8"

```
The quotation marks are absolutely necessary. I inserted these in my .tcshrc source file and now everything is fine. Not sure if it is dependent on CSH/TCSH. 

Hope this helps

---

### Post by 2uRcJQ34G1 on 2012-10-07
Worked for me thanks!

---

### Post by Magnificent 7 on 2012-12-09
Thanks ejmadar, solution still working on a Virtual Private Server running 12.04 Server.

```

root@vps:/# locale-gen en_GB.UTF-8
Generating locales...
  en_GB.UTF-8... done
Generation complete.

```

Before:

```

root@vps:/# locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB.utf8
LANGUAGE=
LC_CTYPE="en_GB.utf8"
LC_NUMERIC="en_GB.utf8"
LC_TIME="en_GB.utf8"
LC_COLLATE="en_GB.utf8"
LC_MONETARY="en_GB.utf8"
LC_MESSAGES="en_GB.utf8"
LC_PAPER="en_GB.utf8"
LC_NAME="en_GB.utf8"
LC_ADDRESS="en_GB.utf8"
LC_TELEPHONE="en_GB.utf8"
LC_MEASUREMENT="en_GB.utf8"
LC_IDENTIFICATION="en_GB.utf8"
LC_ALL=

```

After:
```

root@vps:/# locale
LANG=en_GB.utf8
LANGUAGE=
LC_CTYPE="en_GB.utf8"
LC_NUMERIC="en_GB.utf8"
LC_TIME="en_GB.utf8"
LC_COLLATE="en_GB.utf8"
LC_MONETARY="en_GB.utf8"
LC_MESSAGES="en_GB.utf8"
LC_PAPER="en_GB.utf8"
LC_NAME="en_GB.utf8"
LC_ADDRESS="en_GB.utf8"
LC_TELEPHONE="en_GB.utf8"
LC_MEASUREMENT="en_GB.utf8"
LC_IDENTIFICATION="en_GB.utf8"
LC_ALL=

```

---

### Post by studiogrynn on 2013-02-11
Worked great! Thank you!!

---

### Post by wesswei on 2013-02-20
Sweet, fixed for me!

---

### Post by epasha on 2013-03-15
Thank's you. For russuan
```
# sudo locale-gen ru_RU ru_RU.UTF-8 ru_RU ru_RU.UTF-8
```

---

### Post by CritiKaster on 2013-11-16
This was in the right direction, but unfortunately, didn't fix it for me. What did, however, was this:

[http://bookmarks.honewatson.com/2009/05/30/perl-warning-please-check-that-your-locale-settings-ubuntu/](http://bookmarks.honewatson.com/2009/05/30/perl-warning-please-check-that-your-locale-settings-ubuntu/)

**EDIT**:

Further investigation shows the fix in my case was even easier than I thought, before:

```
$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE=UTF-8
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

So I set LC_TYPE and LC_ALL manually like so:

```
$ export LC_TYPE="en_US.UTF-8"
$ export LC_ALL="en_US.UTF-8"
```

The result is a fix:

```
$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8
```

**SECOND EDIT:**

.. Unfortunately, the above  'solution' only worked for that terminal session. As soon as I reconnected, locale errors rained down on me again..

Delving furhter into this issue, I came across:
[http://stackoverflow.com/questions/2499794/how-can-i-fix-a-locale-warning-from-perl](http://stackoverflow.com/questions/2499794/how-can-i-fix-a-locale-warning-from-perl)

What permanently fixed it for me is commenting out the following directive in my /etc/ssh/sshd_config (on the remote host):

```
AcceptEnv LANG LC_*
```

Having eliminated that line, and reloading my ssh daemon, this issue was resolved.

---

