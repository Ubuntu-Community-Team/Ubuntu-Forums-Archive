---
title: "Help with decrypting PGP messages"
date: 2008-03-18
forum: Security Discussions
---

### Post by Apnu on 2008-03-18
I have my own keys set up and published in evolution and on the Ubuntu Keyserver (plus MIT).  When I encrypt a message to myself as a test, I get the following error after successfully entering my passphrase:

[COLOR="Red"]Could not parse PGP/MIME message
gpg: armor header: Version: GnuPG v1.4.6 (GNU/Linux)
gpg: public key is 7372A887
gpg: using subkey 7372A887 instead of primary key E593C309
gpg: using subkey 7372A887 instead of primary key E593C309
gpg: problem with the agent - disabling agent use
gpg: encrypted with 2048-bit ELG-E key, ID 7372A887, created 2008-01-11
"Christopher L (Key for [email]xxxxxx@xxxxxx.xxx[/email]) <xxxxxx@xxxxxx.xxx>"
gpg: AES256 encrypted data
gpg: original file name=''[/COLOR]


Can anybody help me figure out what the problem is?

Update:

When trying to send a message now I get this error in Evolution:
[COLOR="Red"]Because "gpg: problem with the agent - disabling agent use
gpg: writing to `-'
gpg: DSA/SHA1 signature from: "E593C309 Christopher Lamitie (Key for [email]xxxxxx@xxxxxx.xxx[/email]) <xxxxxx@xxxxxx.xxx>"
", you may need to select different mail options.[/COLOR]

---

### Post by kevdog on 2008-03-19
Have you tried just using gpg from the command line first to see if this works -- this would isolate its not a gpg executable problem rather the gui or third party interfacing with this program.

So assuming you have the keys on the keyring at the command line create a bogus file

echo test > test.txt

Then attempt to encrypt it to a recipient

gpg -e -a -r "EMAIL_ADDRESS"

The encrypted file should be seen in test.txt.asc

---

### Post by Apnu on 2008-03-19
kevdog, thank's for responding.  I found the issue.  For some reason the gpg-agent was not playing nicely with Evo.  I commented out "use-agent" in ~/.gnupg/gpg.conf  And now I can decrypt messages in Evo. 

I also checked that "update-notifier" was added to System->Preferences->Sessions, Startup programs

I found those tricks in this thread [http://ubuntuforums.org/showthread.php?t=193213](http://ubuntuforums.org/showthread.php?t=193213)  Its funny what you can find by changing your search parameters.

---

