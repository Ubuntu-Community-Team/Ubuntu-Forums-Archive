---
title: "Entering correct password for sudo results in segfault after 2 attempts."
date: 2011-02-02
forum: Server Platforms
---

### Post by blegh on 2011-02-02
I cannot sudo nor log into a second ssh session on my Ubuntu 10.10 server edition headless
 setup. Entering an incorrect password works as expected but the correct password gives 
errors, and on the second attempt a segfault.
I recently changed my password as the old one was about to expire, that was 3 days ago, I can't 
find evidence that I have sudo'ed or logged in a second session since, I have been logged
 into it via ssh throughout all of it and I am still currently logged in.

What should I do to correct this problem? I'm worried that by turning it off I will lose 
all access. Is the only option using a live cd to change the password?

> ### Correct password ##
mooman@PlanetExpress:~$ sudo usermod -U mooman
[sudo] password for mooman: 
sudo: pam_acct_mgmt: 7
Sorry, try again.
## Correct password again ##
[sudo] password for mooman: 
Segmentation fault
## Another correct password attempt, this happens with anything to do with sudo ## 
mooman@PlanetExpress:~$ sudo apt-get update 
[sudo] password for mooman: 
sudo: pam_acct_mgmt: 7
Sorry, try again.
[sudo] password for mooman: 
Segmentation fault
## Incorrect password ##
mooman@PlanetExpress:~$ sudo apt-get update 
[sudo] password for mooman: 
Sorry, try again.

## Trying to login with incorrect password ##
mooman@VOYAGER:~$ ssh 192.168.1.10
mooman@192.168.1.10's password: 
Permission denied, please try again.
## Trying to login with correct Password ##
mooman@192.168.1.10's password: 
Your account has expired; please contact your system administrator
Connection closed by 192.168.1.10

---

### Post by blegh on 2011-02-02
I had set my accounts to be disabled 4 days after the passwords expire, I'm not sure what it was that I did but after changing the password in that time the accounts were still disabled 4 days after the expiration date of the original password.

I still think it's strange that trying to sudo with a disabled account gives that error and then segfaults on the next attempt when you are using the correct password for that account, and have been logged in from before the time the account is disabled.

I fixed it by chrooting into the install, unlocking the accounts and setting new passwords.

I'll put this one down to RTFM N00b.

---

