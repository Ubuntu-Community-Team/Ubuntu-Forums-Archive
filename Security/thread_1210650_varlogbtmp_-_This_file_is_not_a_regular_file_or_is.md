---
title: "/var/log/btmp - This file is not a regular file or is not a text file"
date: 2009-07-11
forum: Security
---

### Post by risingsun on 2009-07-11
Hi, the above message recently appeared in my log file viewer - "This file is not a regular file or is not a text file" for /var/log/btmp. Now this is somewhat disconcerting since I've never seen it before, but also because I only just did a reinstall today and I believe this pertains to failed logins which worries me.

The other unusual thing about this file is that the time on it is incorrect, at the time of initial checking it was in the future  - 11:28 when the time was only about 10:48. Now I certainly don't recall any failed logins on my part at 10:28 either, which makes me worry as to what caused it. I should be behind a router firewall and since this is a fresh install I've not touched any ports, nor did I think I had installed an ssh server (this isn't installed  by default, correct?) the incorrect time could be because of Daylight savings or somesuch I guess, but I wouldn't know if this would cause the file properties to be incorrectly set.

Checking lastb seems to indicate the failed login was on tt7 :  0 as my username - is this a possible remote login or is this physically local login only (I assume tt7 is the default X server, in which case should I not have been using it at the time anyway? This isn't the remote desktop is it, I thought I had disabled it on startup.)

Any info anyone can shed on this is very very welcome - is it a glitch in log generation, a failed cron login or somesuch or something more serious? I am rather concerned about this since I've not seen it before and I don't relish the prospect of having to reinstall over again. If it is nothing, does anyone know the cause of the logfile viewer error.

---

### Post by strict on 2009-08-23
I have also been experiencing the same notice and file in /var/log.  I have been unable to track down what creates it.  It's been going on for a while on my server now and it is starting to bug me.   Is there nobody out there having the same problem?

---

### Post by cariboo on 2009-08-23
nevermind

---

### Post by bogdanf on 2009-09-03
this "/var/log/btmp" file is a log file.
there are saved every and each failed logins...
you can open it with "word" - and you will see every username which has been inserted when the login process hasn't been ok.

is a "root" file... so you have to do something like this
```

sudo -s
<your_password_account>
chown -R your_account:your_account /var/log/btmp

```
after that you should be able to delete the file... i never tried... and yes I have the same "error" in the "Log file viewer"... 

have a nice day

---

### Post by cariboo on 2009-09-03
> **bogdanf said:**
> this "/var/log/btmp" file is a log file.
there are saved every and each failed logins...
you can open it with "word" - and you will see every username which has been inserted when the login process hasn't been ok.

is a "root" file... so you have to do something like this
```

sudo -s
<your_password_account>
chown -R your_account:your_account /var/log/btmp

```
after that you should be able to delete the file... i never tried... and yes I have the same "error" in the "Log file viewer"... 

have a nice day

If you are using the gui log file viewer you will get the error, there is nothing wrong with your system. To view the conteents of the file, open a terminal and type:

```
last
```

Removing it, or changing ownership could compromise part of the security tools.

What type of system are you running where 'word' can open and read wtmp and btmp?

---

### Post by Rschnauzer on 2009-12-26
Use [COLOR=Blue]sudo last -f /var/log/btmp[/COLOR] to display the wrong/misspelled logons. [COLOR=Black]

How to get rid of the file? May I delete it?

I get the boring warning each time, if I display the loggings and have to accept the warning.

[/COLOR]

---

