---
title: "Forgot PGP private key passphrase"
date: 2009-05-18
forum: Security
---

### Post by tr333 on 2009-05-18
I setup a PGP key for myself a few years ago, and I have now forgotten the passphrase I set for the private key.  Is there any way to revoke the key without the passphrase, or do I just have to keep trying to remember it?

---

### Post by tubbygweilo on 2009-05-18
tr333, The [Gnu Privacy Guard Howto]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") may offer some help but I fear you will need the passphrase or at the very least the revocation certificate before you can revoke your key. It is often recommended that you create a revocation certificate when you create your key pair.

---

### Post by tr333 on 2009-05-18
Thanks.  Looks like I'm up for creating a new PGP key :(

---

### Post by tubbygweilo on 2009-05-20
> **tr333 said:**
> Thanks.  Looks like I'm up for creating a new PGP key :(

It happened to me when I started using gnupg with enigmail. I expect you and I are not the only ones on this forum to have suffered this fate;)

---

### Post by Bachstelze on 2009-05-20
Hence why you should *always* create the revocation certificate right after you crzeate your key. ;)

---

### Post by amarendra on 2010-02-05
Me too. However I am still struggling to remember my passphrase. Some 5-6 days. I will give it one more week before I create a new one. However, I have got a revocation certificate. 

One lesson learnt - Whatever is being said for the safety, but just don't create a so tough passphrase that it's tough or almost impossible to remember, as you are not supposed to write it anywhere. Better keep it relatively easy (not easy). 
After all there's no point in changing keys every 6 months or so.

At one point the frustration told me to write it down for the next time which is bad :)

---

### Post by BkkBonanza on 2010-02-05
Or use Keepassx. I have hundreds of passwords and I could never remember them all. I don't see how people can use different passwords on all the sites they use without a password safe. Well, I suppose there are derivation schemes and such but for me it just seems a lot easier to use the password safe.

There is a PPA for Keepassx, which makes it easy to install and keep current,

[https://launchpad.net/~keepassx/+archive/ppa](https://launchpad.net/~keepassx/+archive/ppa)

---

### Post by Sarmacid on 2010-02-05
I remember this happening to me. To be able to decrypt my files again I had make a script to bruteforce GPG with the most likely combination of the passphrase I had that was about 12 characters, luckily enough it worked :)

---

### Post by BkkBonanza on 2010-02-05
@Sarmacid,
How long did that take? 
I guess you had a good idea what it looked like before coding it.

---

### Post by amarendra on 2010-02-05
@BkkBonanza, then KeePassX will get me one more password to remember and even that can be compromised. I use weave for Firefox but there I couldn't have saved my passphrase, could I?

@Sarmacid, Can you share the script or tell me how to bruteforce my own passphrase? I also have a fair idea of what is it.. e.g. say my passphrase was: 
> AbCdEf123 or > AeBfCd123 or sth like that,
Then I just don't remember whether the CAPITALIZATION alteration was starting with a capital or small. And a digit or two's confusion in the end digit. 
However the passphrase was more than 10 characters..

Any other good tool or method will be highly appreciated. I just don't want to revoke the key and start all over again.
And, I think I should learn what features KeePassX does have. I have always assumed that it's another thing like weave.

---

### Post by BkkBonanza on 2010-02-05
KeepassX reduces all your passwords to just one. You enter the master password and it has a record of all your others that you can copy/paste or have auto type for you. I can't imagine going online without it and have been using it for years. It uses Blowfish encryption to store the passwords and as far as I know I haven't heard any exploits that make it unsafe. I guess you never know though. 

The main thing is that it allows me to use long fully random passwords without having to remember them and that's a huge advantage when you have dozens of accounts on forums and other places. Of course, I keep several backups in various places. You can use a usb key as well if you want to protect the safe so that just knowing the master password is not enough.

It's not the only password safe of course but it happens to be cross platform so can be used on linux and windows with the same file. If you build it into your process then it becomes habitual. When I register for a new forum the first thing I do is pop it up and have it generate a 12 char random password and then paste that into the register form.

The reason I use it instead of a firefox add-on is this is more universal. It has keys, shell accounts and various tidbits of info i don't want to forget, like addresses and passport numbers etc. It would really suck if it was shown to be vulnerable though.

---

### Post by Sarmacid on 2010-02-05
Actually I had 2 scripts. The first one generated all the possible combinations for the password, the second one tried to decrypt using each line produced by the second one as a passphrase.

the thing is, I had narrowed down each of the 12 characters in my password to 3 possibilites max, lowercase letter, uppercase letter and number. So the output would be something like this

secret
Secret
5ecret
sEcret
SEcret
5Ecret
s3cret

And so on.

I don't have the scripts here, they're sitting comfortably at home, send me a pm if you need it and I'll send them to you later. However if it can't wait, the script to decrypt is almost trivial to do, the other one is a bit tougher, but I just modified one I found around (was made in perl) that tried every combination of letters and numbers to adjust to my combinations, dunno how hard it would be to find the original again since it was about a year and a half ago.

The hard part was getting the first script to generate the right combinations, after that I ran the second and just had to wait maybe 2-3 hours for it.

---

