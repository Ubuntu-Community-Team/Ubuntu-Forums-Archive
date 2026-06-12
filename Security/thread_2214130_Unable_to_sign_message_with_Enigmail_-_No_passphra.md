---
title: "Unable to sign message with Enigmail - No passphrase prompt"
date: 2014-03-30
forum: Security
---

### Post by pfthizzz on 2014-03-30
I have Thunderbird 24.4.0 and Enigmail 1.5.2 installed.  
My OS is Kubuntu 13.10 x64. 
gnupg 1.4.14-1ubuntu2.1 
pinentry-qt4 0.8.1-1ubuntu2 
kgpg 4.4.11.5-0ubuntu0.1
gpg-agent 2.0.20-1ubuntu3
gpgsm 2.0.20-1ubuntu3


  I have only one profile in Thunderbird. One email account. 
I created a new key pair using kgpg. 

When trying to sign and send an email, I get an error: Send operation aborted. Error - bad passphrase. 
Tried kmail, and got the same error. 

  I never get prompted to enter a passphrase.  gpg.conf is configured to "use-agent" but commenting that out doesn't seem to change anything. I have no idea what I have to do to get a passphrase prompt.
Doing [FONT=courier new]gpg --list-secret[/FONT] shows the sec/uid/ssb of the key I am trying to use. No other keys.

Since it appears I am using gpg 1.4, do I have to use pinentry? What are  the pros/cons of using it/not using it? Should I upgrade to gpg 2.0? 


  Any assistance is appreciated.


  Thanks

---

### Post by Dave_L on 2014-03-30
Is the sender address for the email associated with the right gpg key?

---

