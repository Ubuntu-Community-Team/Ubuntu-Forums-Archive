---
title: "Please discuss encrypted home - is it useful or not?"
date: 2015-03-04
forum: Security
---

### Post by sudodus on 2015-03-04
***Encrypted home with cryptswap works again in 15.04 ***:KS

***Cryptswap works in Wily*** (to become 15.10), in a system with both encrypted disk and encrypted home.

See this bug report, [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

[HR][/HR]
The current test-cases for encrypted disk and encrypted home inside it

[Alternate Install (Encryption) in Lubuntu Alternate amd64 for Vivid Daily        ]("http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/90074/testcases/1439/results")
[Alternate Install (Encryption) in Lubuntu Alternate i386 for Vivid Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/90075/testcases/1439/results")

do not work, but can be modified to work by removing encrypted home, which I suggest in ***post #2*** of the following link (in the Ubuntu Development Forum)
[URL="http://ubuntuforums.org/showthread.php?t=2266912"]
LVM encrypted disk & encrypted home in Lubuntu Vivid complicated or buggy[/URL]                 
                 
Lubuntu is the only flavour with an  'encrypted test-case' that has both encrypted disk with LVM and inside  that encrypted home with cryptswap. In Vivid (maybe earlier, but it was  discovered now) there are problems with encrypted home inside encrypted  disk with LVM. And there are extra big problems with cryptswap inside  encrypted disk with LVM.

All other Ubuntu flavour test-cases have encrypted disk with LVM, but not encrypted home.

I think it is important

1. to test if it works like I suggested

[I][B]2. to discuss if it would be worthwhile to make it work with encrypted  disk with LVM and inside that encrypted home with cryptswap. (In that  case it would involve more debugging and maybe advanced contributions by  a developer.

3. to discuss the good and bad points of the two encryption methods (and typical cases where to use them).
[/B][/I]
4. I guess that we need also test that encrypted home works properly by  itself, when not inside encrypted disk with LVM. (Try also after  rebooting, because I managed to get cryptswap work inside encrypted disk  with LVM once. After reboot it vanished, but I could create a 'normal'  swap that survived reboots and update/dist-upgrades.)

I post in this forum because I think that is it the right place to reach ***you***, who are interested in security issues. I hope to get a good discussion about the different methods to encrypt the Ubuntu flavours (encrypted disk and encrypted home). And of course it is valuable that ***you***, who know what is important, also take part in testing.

---

### Post by sudodus on 2015-03-05
***I found that 'Encrypted home' does not even work as a standalone feature*** (without 'Encrypted disk with LVM). Cryptswap works the first time I run the installed system but does not survive after reboot.

John Hupp helped me find more information about the cryptswap bug. See comment #37 of the bug report [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

I can confirm that it works as a work-around, and there should be enough information in the bug report [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/) to squash that bug.

We are also getting help from ventrical at the Ubuntu Forums to test various encrypted systems. See the following link [http://ubuntuforums.org/showthread.php?t=2266912](http://ubuntuforums.org/showthread.php?t=2266912)

I try to sum it up in post #35 of that Ubuntu Forums thread.

-o-

We should not be surprised that 'Encrypted home' is no longer part of any [other] Ubuntu flavour test-case. It does not work. 

I can think of user cases, where it would be useful, but 'Encrypted home' has been buggy since March 2012 when Alan Pope reported bug #953875.

   
[LIST]
[*]Would encrypted home be valuable for ***you***?
[*]Do you use a work-around in order to run 'Encrypted home'?
[*]Is it worthwhile to raise opinion to squash the bug(s) affecting 'Encrypted home'?
[*]Or should we let it rest in peace?
[/LIST]

---

### Post by sudodus on 2015-03-06
The tests are finished and a new version of the iso-testing test-case for Lubuntu alternate with LVM encrypted disk is being created.

Now I'm looking forward to your experience of and opinion about 'Encrypted home' :-P

It is worthwhile to debug it, or can it rest in peace?

You have been silent, but there is no risk to get involved in any testing now, so you dare reply ;-)

---

### Post by cogset on 2015-03-07
I'm sorry you didn't get much attention, I'm by no means an expert on this (literally..) but I would keep Encrypted home (in a working state, of course) if  possible, because it would probably be easier to set up than  full disk encryption and less intimidating (maybe?) for beginners . Sorry if I (probably) missed what this was about.

---

### Post by sudodus on 2015-03-07
Thanks, *cogset*, for your reply! I agree that Encrypted home (in a working state, of course) might be less intimidating for beginners. There are also other differences. Encrypted disk is for computers with one user, encrypted home is for computers with many users, where each home directory can be encrypted and not available for the other users, while the root partition is not encrypted.

Are you using any of the encryption methods in your own computer(s)?

If you are affected by the bug, please browse to the bug report [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1310058]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058") and click on **[[COLOR=#006400]This bug affects around 100 people. Does this bug affect you?[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/+affectsmetoo")** :smile: Every new user (who is affected by it) increases the chance that the bug will get priority and get squashed.

---

### Post by sudodus on 2015-03-07
This link at Arch Linux discusses different aspects of encryption in computers, disk encryption and data encryption (with the special case home encryption).

[https://wiki.archlinux.org/index.php/disk_encryption](https://wiki.archlinux.org/index.php/disk_encryption)

My conclusion after reading that link is that 'Encrypted disk' is better than 'Encrypted home', so we need not push very hard to revive 'Encrypted home'.

> 
...
**Data encryption vs system encryption**

  Data encryption Defined as encrypting only the user's data itself (often located within the /home  directory, or on removable media like a data DVD), data encryption is  the simplest and least intrusive use of disk encryption, but has some  significant drawbacks. In modern computing systems, there are many background processes  that may cache/store information about user data or parts of the data  itself in non-encrypted areas of the hard drive, like

 
[LIST]
[*] swap partitions
[LIST]
[*] [COLOR=#555]*(potential remedies: disable swapping, or use [encrypted swap]("https://wiki.archlinux.org/index.php/Dm-crypt/Swap_encryption") as well)*[/COLOR] 
[/LIST]
  
[*] /tmp (temporary files created by user applications)
[LIST]
[*] [COLOR=#555]*(potential remedies: avoid such applications; mount /tmp inside a [ramdisk]("https://wiki.archlinux.org/index.php/Ramdisk"))*[/COLOR] 
[/LIST]
  
[*] /var (log files and databases and such; for example, mlocate stores an index of all file names in /var/lib/mlocate/mlocate.db) 
[/LIST]
 
In addition, mere data encryption will leave you vulnerable to  offline system tampering attacks (e.g. someone installing a hidden  program that [records]("http://en.wikipedia.org/wiki/Keystroke_logging")  the passphrase you use to unlock the encrypted data, or waits for you  to unlock it and then secretly copies/sends some of the data to a  location where the attacker can retrieve it).  
[I][B]
System encryption[/B][/I]

Defined as the encryption of the operating system *and* user data, system encryption helps to address some of the inadequacies of data encryption.

 Benefits: 
[LIST]
[*] prevents unauthorized physical access to (and tampering with) operating system files *(but see warning above)* 
[*] prevents unauthorized physical access to private data that may cached by the system 
[/LIST]
 Disadvantages: 
[LIST]
[*] unlocking of the encrypted parts of the disk can no longer happen during or after user login; it must now happen at boot time 
[/LIST]
 
In practice, there's not always a clear line between data encryption  and system encryption, and many different compromises and customized  setups are possible. 

In any case, disk encryption should only be viewed as an adjunct  to the existing security mechanisms of the operating system - focused on  securing offline physical access, while relying on *other* parts of the system to provide things like network security and user-based access control. 
...


---

### Post by kromaz on 2015-03-23
This day and age data encryption is a must whether its /home or full disk encryption (LVM). I prefer both for double layer of security. Everyone **should** use /home encryption in multi-user environments to protect their personal data. Would like to see /home encryption default on Ubuntu installs. Full disk encryption **should** especially be used with laptops for protecting their personal data when traveling. I decide to make the switch to GNU/Linux due to the development with security in mind. I hope all those with the knowledge take priority in fixing the cryptswap bug. Please also includes all the LTS that are effected. Any update on the progress with squishing this bug? Thanks

---

### Post by sudodus on 2015-03-24
I think the bug is still there. Cryptswap does not survive rebooting, and cryptswap is a vital part of 'Encrypted home'. The bug report [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1310058]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058") is now considered a duplicate of       [bug report #953875.]("https://bugs.launchpad.net/bugs/953875")

In order to communicate with the developers, who can edit the program code and fix bugs, please focus on the [bug report #953875]("https://bugs.launchpad.net/bugs/953875"). If the bug affects you, please click on [**[COLOR=#006400]This bug affects more than 140 people. Does this bug affect you?[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875/+affectsmetoo") :smile: Every new user (who is affected by it) increases the chance that the bug will get priority and get squashed.

---

### Post by kromaz on 2015-03-24
> **sudodus said:**
> I think the bug is still there. Cryptswap does not survive rebooting, and cryptswap is a vital part of 'Encrypted home'. The bug report [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1310058]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058") is now considered a duplicate of       [bug report #953875.]("https://bugs.launchpad.net/bugs/953875")

In order to communicate with the developers, who can edit the program code and fix bugs, please focus on the [bug report #953875]("https://bugs.launchpad.net/bugs/953875"). If the bug affects you, please click on [**[COLOR=#006400]This bug affects more than 140 people. Does this bug affect you?[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875/+affectsmetoo") :smile: Every new user (who is affected by it) increases the chance that the bug will get priority and get squashed.

Thanks for the link to report the bug does effect me. I noticed that [bug report #953875]("https://bugs.launchpad.net/bugs/953875") status shows **Fix Released**. Why if the cryptswap still does not survive rebooting? It's important to mention that /home encryption is a must have security feature. It's concerning how long this bug has been around with no fix.

---

### Post by sudodus on 2015-03-25
It seems that the developer thinks that his fix has solved the problem, and he has not yet received enough feedback to understand, that the bug is still there. He might think that I have some very special installation, and that it works for everybody else.

So please write a comment (at the end of the bug report), where you describe your system (version and flavour of Ubuntu and the computer hardware) and that cryptswap does not survive reboots (and what other symptoms you might have).

---

### Post by sudodus on 2015-04-19
***Encrypted home with cryptswap works again.***

See this bug report, [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

ISO testing result for Lubuntu Vivid

 [http://iso.qa.ubuntu.com/qatracker/milestones/338/builds/92211/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/338/builds/92211/testcases/1439/results)
 step 1 OK: cryptswap works when rebooting after installation.
step 2 OK: no long delay when rebooting again.
step 3 OK: cryptswap works when rebooting again. I provoked using swap, and it seems to work correctly.
step 4 OK: cryptswap works when rebooting again. I provoked using swap, and it seems to work correctly.

 Encrypted home with cryptswap works again. Thank you Martin Pitt :-)

---

### Post by kromaz on 2015-04-20
This is great news! Does this also apply to 14.04 LTS?

---

### Post by sudodus on 2015-04-21
It should arrive there via updating and upgrading, but the released iso files are what they are. We can expect the next point release Ubuntu 14.04.3 LTS to come with an ISO file with a working system for encrypted home with cryptswap.

---

### Post by HermanAB on 2015-04-22
An encrypted home is not useful at all.  It makes your computer useless to whoever steals it...

---

### Post by sudodus on 2015-04-23
@ HermanAB

Which encryption method do you consider worse for the thief?

- Encrypted home with cryptswap
- Encrypted disk (with LVM)

Do you think it is meaningful to install with both 'Encrypted disk' and 'Encrypted home'? In that case why?

---

### Post by HermanAB on 2015-04-23
I use AES256, CBC, with ESSIV and SHA256, which happens to be the default for LUKS.

This is also the default for government use up to the level of Secret.

---

### Post by sudodus on 2015-05-12
Cryptswap does not work in Lubuntu ***Wily***. I tested a system with both both encrypted disk and encrypted home according to the following test-case.

[http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/93160/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/93160/testcases/1439/results)[URL="http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/93160/testcases/1439/results"]
[/URL]
But cryptswap works in a system with 'only' encrypted home. See the bug report

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

---

### Post by sudodus on 2015-05-12
There was only a temporary glitch in yesterday's build. Cryptswap works again in today's daily build, that arrived a short time ago  :-)

The Lubuntu test-case with encrypted disk and encrypted home with cryptswap works again.

---

