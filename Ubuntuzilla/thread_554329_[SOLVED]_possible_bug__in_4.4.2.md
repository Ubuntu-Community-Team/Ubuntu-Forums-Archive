---
title: "[SOLVED] possible bug  in 4.4.2?"
date: 2007-09-18
forum: Ubuntuzilla
---

### Post by the.phantom on 2007-09-18
doing the update that just came out today for firefox (2.0.0.7


on my older 6.10 i did the update the "old school way" with a old script that installed
gksudo firefox &
and all worked

i have a new box i installed 7.04 on and i used the new ( latest script_
4.4.2

i get this as a error ( and tried 3 times)


gpg: Signature made Sun 16 Sep 2007 04:11:03 AM PDT using DSA key ID 17785FE8
gpg: Can't check signature: public key not found
Key verification failed. This is most likely due to a corrupt download. You should delete files ' firefox-2.0.0.7.tar.gz.asc ' and ' firefox-2.0.0.7.tar.gz ' and run the script again.

i updated all the boxes to the latest firefox but this one

any ideas?
or a work around?

mitch

update

i tried it using 4.1.1 that i had on one of the systems and this is the same error but a bit more details
hope this helps?


there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: key 0E3606D9: "Mozilla Software Releases <releases@mozilla.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Successfully retrieved Mozilla Software Releases Public key from subkeys.pgp.net .


Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Sun 16 Sep 2007 04:11:03 AM PDT using DSA key ID 17785FE8
gpg: Can't check signature: public key not found
Key verification failed. This is most likely due to a corrupt download. You should delete files ' firefox-2.0.0.7.tar.gz.asc ' and ' firefox-2.0.0.7.tar.gz ' and run the script again.

Would you like to delete those two files now? [y/n]? 
Please enter 'y' or 'n':

---

### Post by nanotube on 2007-09-18
it looks like they signed the binary with a different key this time... that's why gpg fails to verify signature. don't know why they did that. let me investigate and see what's up. maybe i'll have to make a new update release....

---

### Post by VoyeurOne on 2007-09-18
I am having the same problem with the upgrade, I did my last upgrade with ubuntuzilla and it worked fine.

---

### Post by nanotube on 2007-09-19
update:
yes, mozilla did change their pgp key to a new one... so i'll update the script and put out version 4.4.3. :)
wait for it! :)

---

### Post by VoyeurOne on 2007-09-19
Ops I hit the post button too soon....

I get the exact same script except for : the line before the key warning

**gpg: WARNING: unsafe ownership on configuration file `/home/pierre/.gnupg/gpg.conf'**

gpg: Signature made Sun 16 Sep 2007 08:11:03 AM ADT using DSA key ID 17785FE8
gpg: Can't check signature: public key not found
Key verification failed. This is most likely due to a corrupt download. You should delete files ' firefox-2.0.0.7.tar.gz.asc ' and ' firefox-2.0.0.7.tar.gz ' and run the script again.

Would you like to delete those two files now? [y/n]? 
Please enter 'y' or 'n':

---

### Post by nanotube on 2007-09-19
> **VoyeurOne said:**
> Ops I hit the post button too soon....

I get the exact same script except for : the line before the key warning

**gpg: WARNING: unsafe ownership on configuration file `/home/pierre/.gnupg/gpg.conf'**

gpg: Signature made Sun 16 Sep 2007 08:11:03 AM ADT using DSA key ID 17785FE8
gpg: Can't check signature: public key not found
Key verification failed. This is most likely due to a corrupt download. You should delete files ' firefox-2.0.0.7.tar.gz.asc ' and ' firefox-2.0.0.7.tar.gz ' and run the script again.

Would you like to delete those two files now? [y/n]? 
Please enter 'y' or 'n':

about your "warning unsafe ownership", that's a different problem. you have to chmod your .gnupg directory so that others can't have access. issue the following command at the prompt:

```
chmod -R go-rwx ~/.gnupg
```

about the key - just wait until i make the new release - it's about to be up on sourceforge. :)

---

### Post by nanotube on 2007-09-19
ok, release 4.4.3 is up on sourceforge - should take care of the new gpg key issue.

please download and test and let me know if there are any problems. :)

---

### Post by VoyeurOne on 2007-09-19
Alllright replying to you with my new Firefox/2.0.0.7 , thanks, the patch did the trick.

And thank you for the reply to my safe ownership.   I am trying very hard to like Linux  but I have a long way to go be as comfortable with it as I am with XP ...

Oh well, a month and a half of exclusive use and I can safely say that I spend more time enjoying it than trying to make it work even if I did a few things that I probably will regret later.

Pierre

---

### Post by the.phantom on 2007-09-19
think you should have a name change ;-D

how about Saint Nanotube patron saint of Linux Lightweights ;-D


worked like a charm , thanks for the quick reply 
THANK YOU !!!!

---

### Post by nanotube on 2007-09-19
> **the.phantom said:**
> think you should have a name change ;-D

how about Saint Nanotube patron saint of Linux Lightweights ;-D


worked like a charm , thanks for the quick reply 
THANK YOU !!!!

haha :)

to both of you, the.phantom and voyeurone: thank you for reporting the bug, and for testing the new version!

---

### Post by EnlistedSquire on 2010-02-01
Really old thread I know, but this error has raised its head again today. I'm trying to install Thunderbird 3.0.1 and I'm getting this error:

> gpg: Signature made Tue 12 Jan 2010 21:34:54 GMT using RSA key ID 6CE2996F
gpg: Can't check signature: public key not found
Key verification failed. This is most likely due to a corrupt download. You should delete files ' thunderbird-3.0.1.tar.bz2.asc ' and ' thunderbird-3.0.1.tar.bz2 ' and run the script again.

Would you like to delete those two files now? [y/n]? 
Please enter 'y' or 'n': y

Maybe Mozilla changed their key again.

---

### Post by nanotube on 2010-02-01
> **EnlistedSquire said:**
> Really old thread I know, but this error has raised its head again today. I'm trying to install Thunderbird 3.0.1 and I'm getting this error:



Maybe Mozilla changed their key again.

hi
you're probably using an old version of the ubuntuzilla script. get the newest version that knows about this thunderbird signing key.

note also that if you're on 32bit ubuntu, you can do one better, and use the new ubuntuzilla ppa repository, rather than the script.

for new info, see project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by EnlistedSquire on 2010-02-01
> **nanotube said:**
> hi
you're probably using an old version of the ubuntuzilla script. get the newest version that knows about this thunderbird signing key.

note also that if you're on 32bit ubuntu, you can do one better, and use the new ubuntuzilla ppa repository, rather than the script.

for new info, see project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)


Hi nanotube. Thanks for the tip. You might be right as this particular PC hasn't been booted up for a couple of months now. I thought the ubuntuzilla script was actually self-updating though :S

---

### Post by nanotube on 2010-02-01
> **EnlistedSquire said:**
> Hi nanotube. Thanks for the tip. You might be right as this particular PC hasn't been booted up for a couple of months now. I thought the ubuntuzilla script was actually self-updating though :S

well, it is - but not if you don't boot up the computer! :)

---

### Post by EnlistedSquire on 2010-02-02
> **nanotube said:**
> well, it is - but not if you don't boot up the computer! :)

lol

---

### Post by eMcE on 2010-09-09
Today I have that same bug with ubuntuzilla 4.8.3 and Thunderbird 3.1.3 :(

--
Key verification failed. This is most likely due to a corrupt download. You should delete files ' thunderbird-3.1.3.tar.bz2.asc ' and ' thunderbird-3.1.3.tar.bz2 ' and run the script again.

Would you like to delete those two files now? [y/n]? 
Please enter 'y' or 'n':
--

---

### Post by nanotube on 2010-09-14
> **eMcE said:**
> Today I have that same bug with ubuntuzilla 4.8.3 and Thunderbird 3.1.3 :(

--
Key verification failed. This is most likely due to a corrupt download. You should delete files ' thunderbird-3.1.3.tar.bz2.asc ' and ' thunderbird-3.1.3.tar.bz2 ' and run the script again.

Would you like to delete those two files now? [y/n]? 
Please enter 'y' or 'n':
--

Hi,
The mozilla messaging team has changed their signing key again.
Seeing as how this script is no longer maintained, you should either (a) start using the ubuntuzilla repository, or (b) manually import the new thunderbird singing key from a keyserver of your choice.

---

