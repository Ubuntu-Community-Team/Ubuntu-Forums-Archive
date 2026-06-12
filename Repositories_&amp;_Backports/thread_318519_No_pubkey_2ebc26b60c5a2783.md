---
title: "No_pubkey 2ebc26b60c5a2783"
date: 2006-12-14
forum: Repositories &amp; Backports
---

### Post by sam_can on 2006-12-14
hello there, 

i just installed Ubuntu and i did chance the sources.list, but when i try to get update (sudo apt-get update)  i get the following errors: 

W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

any way to fix this 

many thx

---

### Post by antraxx on 2006-12-16
You have to run in terminal this command: 

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

---

### Post by mimimotor on 2008-06-01
> **antraxx said:**
> You have to run in terminal this command: 

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

Thanks very much for the suggestion. However, this does not work either. It gives 

gpg: no valid OpenPGP data found.

Could you please help me to get around this?

Henk

---

### Post by 449 on 2008-06-11
[http://ubuntuforums.org/showthread.php?t=713009](http://ubuntuforums.org/showthread.php?t=713009)

:p

---

### Post by PeonDevelopments on 2008-07-30
[B]How to remove the following error:

W: GPG error: [http://medibuntu](http://medibuntu)[...] Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783 W: You may want to run apt-get update to correct these problems[/B]

There should be a file in your :

```
/etc/apt/sources.list.d/ 
```

folder.

I had to remove the medibuntu.list file that was sitting there in order for my apt-get update to quit throwing me the error.
(This was after I had installed the libraries I needed. Remove the repository if it is included in your sources.list.)

---

### Post by keith_honk on 2008-10-11
"I had to remove the medibuntu.list file that was sitting there in order for my apt-get update to quit throwing me the error.
(This was after I had installed the libraries I needed. Remove the repository if it is included in your sources.list.)"

-> this surely works. but how is that useful if it is exactly the medibuntu stuff that u want? correct me if i'm wrong, but this error message does not seem to hinder the updating of packages related to other repositories.. so i decided to just leave the medibuntu.list where it is..

---

### Post by joao.trindade on 2008-12-08
> **sam_can said:**
> 
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

any way to fix this 


Just follow the instruction found here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Then accept the package medibuntu-keyring.

---

### Post by zoobuntoo on 2009-04-11
Download the gpg file at [http://packages.medibuntu.org/medibuntu-key.gpg]("http://packages.medibuntu.org/medibuntu-key.gpg") to your desktop or some local folder.
Go to *System -> Administration -> Software Sources*. in the Authentication tab hit the "Import Key File.." button and locate the gpg file. Close.

---

### Post by kastanedowski on 2009-05-03
> **zoobuntoo said:**
> Download the gpg file at [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) to your desktop or some local folder.
Go to *System -> Administration -> Software Sources*. in the Authentication tab hit the "Import Key File.." button and locate the gpg file. Close.

does work

 saving the public key is not a problem but when trying to import it ubuntu can not see the file....

any ideas why?

 thanks

---

### Post by neeteex on 2009-05-07
> **zoobuntoo said:**
> Download the gpg file at [http://packages.medibuntu.org/medibuntu-key.gpg]("http://packages.medibuntu.org/medibuntu-key.gpg") to your desktop or some local folder.
Go to *System -> Administration -> Software Sources*. in the Authentication tab hit the "Import Key File.." button and locate the gpg file. Close.

:popcorn::KS:KS:KS:guitar:):P

---

### Post by Andi_S on 2009-06-01
> **joao.trindade said:**
> Just follow the instruction found here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Then accept the package medibuntu-keyring.

thanks this worked :)

---

### Post by Don King on 2009-10-03
> **joao.trindade said:**
> Just follow the instruction found here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Then accept the package medibuntu-keyring.

worked for me too. 

Thanks a lot.

---

### Post by FrodeA on 2009-11-02
> **joao.trindade said:**
> Just follow the instruction found here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Then accept the package medibuntu-keyring.

That did the trick for me! Received error not being able to verify GPG signature for medibuntu, but it is working alright now :)

---

### Post by pguedes on 2009-11-14
> **zoobuntoo said:**
> Download the gpg file at [http://packages.medibuntu.org/medibuntu-key.gpg]("http://packages.medibuntu.org/medibuntu-key.gpg") to your desktop or some local folder.
Go to *System -> Administration -> Software Sources*. in the Authentication tab hit the "Import Key File.." button and locate the gpg file. Close.

Works like a charm ;)

---

### Post by freewaybear on 2010-03-19
> **Andi_S said:**
> thanks this worked :)

For me, as well :D

Thanks a bunch!

---

### Post by mickey57 on 2010-04-30
[SIZE="4"]**Thanks :guitar:**[/SIZE]

---

### Post by giannisfs on 2010-07-11
> **antraxx said:**
> You have to run in terminal this command: 

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

The correct key URI is [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg)

---

### Post by gitano on 2010-07-14
worked for me as well

---

### Post by .::welemski::. on 2010-09-04
> **giannisfs said:**
> The correct key URI is [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg)

Thanks, yours is correct:

This is how it should be : 

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

---

### Post by luckylucky on 2010-11-05
> **joao.trindade said:**
> Just follow the instruction found here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Then accept the package medibuntu-keyring.


hooked on phonics worked for me... as did the above code.  thanks
ubuntu 10.10

---

### Post by daviddwillson on 2010-11-10
does work

 saving the public key is not a problem but when trying to import it ubuntu can not see the file....

any ideas why?

 thanks

---

### Post by Wuxin on 2010-11-16
When you say "this worked"--what precisely did you do?  Was it just a matter of installing that command into a terminal, or was there something you did prior by following the previous link?  I'm having the same problem but everything I've tried to this point hasn't "worked."

---

### Post by Wuxin on 2010-11-16
Zoobuntu--you are one sharp cookie!  I have been agonizing for days trying to get my Update Manager up and working.  Your simple and powerful command finally helped me to accomplish the seemingly impossible!  Thank you!  Thank you!  Let me ask you: How did you come by your wonderfully skilled knowledge of Linux and how to make it work?  Are there any books that you would recommend to those of us who are new to this system?  Again, I say...thank you!

---

### Post by gnufan on 2010-12-03
> Originally Posted by **zoobuntoo** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7052463#post7052463") 				
 				[I]Download the gpg file at [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) to your desktop or some local folder.
Go to *System -> Administration -> Software Sources*. in the Authentication tab hit the "Import Key File.." button and locate the gpg file. Close.[/I]


works like a charm! :D
big thanks!

---

### Post by omelette on 2011-08-17
Old topic I know but having just come across the same problem with Ubuntu 10.04, I thought I'd add something.  A few have queried as to why when they try Importing into the keyring via 'Passwords and Encryption Keys' , the key isn't visible unless you then select "All files" rather than "All Keys" - well I don't have an answer either!  What I can say is that when I do import by this route, double-click the key & check the 'do you trust' tab - even setting the degree of trust to "Fully" - it still doesn't work!!!  Neither does the one-liner from the command-line - I continue to get the same error message.

The solution I found was to open up Synaptic Package Manager,  go to Settings->Repositories->Authentication and click the "Import Key File" button.  From here the gpg key that you downloaded is immediately visible and imports without a problem.  Click the 'Reload' button and you will find that the gpg error message no longer appears.

---

