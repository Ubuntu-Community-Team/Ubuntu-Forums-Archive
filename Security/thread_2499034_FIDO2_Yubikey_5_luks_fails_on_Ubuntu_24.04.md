---
title: "FIDO2 Yubikey 5 luks fails on Ubuntu 24.04"
date: 2024-07-08
forum: Security
---

### Post by BatteryKing on 2024-07-08
I was looking to use FIDO2 keys to unlock a LUKS2 partition on a laptop.  The Ubuntu 24.04 installation makes it easy to do "whole drive encryption" with LUKS2 with LVM inside, however this defaults to using a passphrase.  Part of the use case is to make it easy to decrypt by someone else in the who has access to a FIDO2 key keyed to the laptop and do away with either insecure passphrases or complicated passphrases that nobody can seem to type in right, let alone remember / find when they need it.  The thought with the Yubikey is FIDO2 can be used with strong crypto such as ed25519 and if you don't have both the physical key and the simple pin that goes with the key, you can't unlock it. Plus if the physical key gets lost or stolen, 8 failed attempts and the FIDO2 function is locked out on the key.  So seems to be a good way to protect data at rest, granted the function to shut down a lost of stolen laptop remotely when it connects to the Internet next is "sold separately".  (Something you can do with ESET on Windows, at least for business users, which can be handy, granted that is a TPM2 based solution.)

So anyways what I am hitting with Ubuntu 24.04 specifically when I try to go down this route is:
1. When I generate key with the command:
```

systemd-cryptenroll --fido2-device=auto --fido2-credential-algorithm=eddsa --fido2-with-client-pin=yes /dev/nvme0n1p8

```
I see the luks2 headers in the cryptsetup luksDump command, but I don't see any keys on the Yubikey 5 with the ykman fido list command.  I know that fido u2f keys won't show, but this is supposed to be all fido2 here, so should show up.  I can see other fido2 keys on Yubikeys with known fido2 keys on them, so I am doing the listing right.
Something of note is I am not asked for the pin when adding.  Another thing that is bugging me is when I register on websites and with ssh, I can label each entry on the FIDO2 key, but I don't see any option to do this with the systemd-cryptenroll command.  (The Yubikey 5 keys are working great for FIDO2 based MFA on ssh on Ubuntu 22.04 by the way.  Quick and easy to setup and works just as it should and everything validates as correct when I check.)

2. To make sure I can see the prompt for the pin, I stripped out the splash screen from grub.  Thought I would point this out to show I am making sure I am seeing only text on boot and so am not missing anything.

3. initramfs does not recognize the fido2 option in /etc/crypttab.  So I cannot use the default initramfs command.  Other people trying this use dracut, so I gave that a whirl.

4. Dracut fails to boot the system after following all instructions including hacks to get it to include appropriate fido2 libraries.  It seems it doesn't even attempt to unlock the luks partition at boot, but instead goes straight to attempting to mount the LVM volume inside, so hangs and then fails.  I actually played with this some in Ubuntu 22.04 and this worked with the same instructions, but I failed on getting the FIDO2 key to unlock the drive.  Instead after prompting me for the FIDO2 key, it prompted me for the passphrase.  So this seems to be a regression as I made it further in Ubuntu 22.04 than I did in 24.04, granted there were other hoops I had to jump through for 22.04 such as converting the luks1 partition into a luks2 partition.

5. Booting off of a recovery drive (Ubuntu 24.04 installer image), I tried to open the luks partition with the FIDO2 key.  It prompts for the pin and has me do the presence detect, but then fails to unlock the partition.  I think this goes back to #1 where it apparently fails to put a key on the Yubikey 5 key, so how is it supposed to unlock anything without that key entry?  Of course unlocking with a passphrase works.  I tried dorking around with dracut, but cannot seem to get around the regression in #4.

6. The only way I seem to be able to get the system to boot on its own is to switch it back to using the default initramfs tool and regenerate the initramfs file from this on the recovery boot.  Granted, I was able to get the system to boot again.  It is just it doesn't recognize the fido option and so never prompts to even try to unlock with the fido2 key.

7. The literature I have read and experiments I have done point to you cannot have 2 or more FIDO2 keys registered.  Apparently the FIDO2 option is just ignored if you have two or more FIDO2 entries.  This goes against the notion of redundancy and especially for the case of somebody else having a FIDO2 key to unlock the drive with.

---

### Post by currentshaft on 2024-07-09
> **BatteryKing said:**
> I was looking to use FIDO2 keys to unlock a LUKS2 partition on a laptop.

You never say why or what this process that is meant to solve. A true example of a solution seeking a problem. The fact this is so cumbersome, inconvenient and unreliable to use is reason enough to avoid it on its face.

---

### Post by 0f4d0335 on 2024-07-09
Interesting write up. Thanks for clarifying some aspects of the Yubikey for me that I've been wondering about. I had done a similar experiment, and like you noticed, my redundant key caused a problem with unlocking the partition once enrolled. Because I had deleted my passphrase, it caused a permanent lockout, which was not fun to fix after having setup my workstation. :) Therefore I haven't used Yubikeys to lock my system anymore; though, now I'm curious to try again with a test system. Having a passphrase however defeats the benefit of Yubikey, and without being able to enroll redundant keys, accessibility risk becomes rather high. Curious to think this is not an Ubuntu issue but either a Yubikey or LUKs one.

---

### Post by BatteryKing on 2024-07-09
To explain a little more of why I am trying to do this:
1. When adding more than one person to a computer using passphrases, maybe you can memorize a complex passphrase and don't mind, but maybe the next person puts in say abcd1234 and calls it a day.  Now, it is trivial to brute force the passphrase and get in with a password cracker.  My company has ended up turning things encrypted by other employees over to a security expert and he has been able to brute force his way in overnight.  Not good when you really need something secure.

2. I am pursuing business cases here.  Need to make sure a company laptop that gets lost or stolen can be secured.  Like I mentioned before remotely forcing a shutdown of a lost or stolen computer is "sold separately" here, but I do need the mechanism to protect data at rest.  As mentioned in #1, can't guarantee employees will do a strong passphrase as what was tested and failed the test.  I find overwhelmingly other employees hate high entropy passwords and passphrases.  So need something with a higher entropy than what employees generally use that should not be breakable.

3. The Yubikey with ED25519 will protect the private key the luks partition is encrypted with with high entropy cryptography.  The Yubikey itself is protected with a relatively simple pin, but you only get 8 tries and then it is locked out.  Even if the pin (or password) is leaked, you still need the physical key.  (Say someone gets a key logger running on the system early enough to capture this pin being typed in.)  Also, if the key is stolen, but they do not know the pin, then the key is worthless.  This passes muster as a secure solution.  Certainly more secure than other options.

4. Any company assigned laptop needs to at least have the primary user be able to unlock with a Yubikey as outlined in #3 and by the IT department.  There may be more who need access to unlock with their Yubikey.  The Yubikey provides a floor to the entropy used to protect the private key luks uses to encrypt the partition with.  Multiple people each with their own key (or company skeleton keys) provides redundant ways to get into the system.  At the same time none of these redundant ways will end up being the weak link that allows the partition to be decrypted by a malicious actor.

5. With each person having their own Yubikey, they can be easily revoked at any time by just removing their key.  At least if you can label things and create those labels wisely, it should be easy to do.

The problem with all of this is, at least with Ubuntu 24.04, I failed in multiple places to make this work.  So this is not a viable route until these issues get fixed.

---

### Post by currentshaft on 2024-07-09
> **BatteryKing said:**
> To explain a little more of why I am trying to do this:
1. When adding more than one person to a computer using passphrases, maybe you can memorize a complex passphrase and don't mind, but maybe the next person puts in say abcd1234 and calls it a day.  Now, it is trivial to brute force the passphrase and get in with a password cracker.  My company has ended up turning things encrypted by other employees over to a security expert and he has been able to brute force his way in overnight.  Not good when you really need something secure.


Then enforce a password policy for LUKS passphrase complexity.

> **BatteryKing said:**
> 
2. I am pursuing business cases here.  Need to make sure a company laptop that gets lost or stolen can be secured.  Like I mentioned before remotely forcing a shutdown of a lost or stolen computer is "sold separately" here, but I do need the mechanism to protect data at rest.  As mentioned in #1, can't guarantee employees will do a strong passphrase as what was tested and failed the test.  I find overwhelmingly other employees hate high entropy passwords and passphrases.  So need something with a higher entropy than what employees generally use that should not be breakable.


LUKS already secures data at rest well. You don't get "higher entropy" with a Yubikey. What you get is a physical token which will be stolen with the laptop to completely compromise security instead.

> **BatteryKing said:**
> 
3. The Yubikey with ED25519 will protect the private key the luks partition is encrypted with with high entropy cryptography.


Frankly this makes no sense. It's just a jargon word salad with no meaning. LUKS keys are already high entropy because they are derived from passphrases using a KDF.

> **BatteryKing said:**
> 
The Yubikey provides a floor to the entropy used to protect the private key luks uses to encrypt the partition with


It does no such thing. I don't know where you get this idea, but it is not based in any objective facts you have cited.

> **BatteryKing said:**
> 
5. With each person having their own Yubikey, they can be easily revoked at any time by just removing their key.  At least if you can label things and create those labels wisely, it should be easy to do.


Revocation is fixed with LUKS key escrow. This is already a solved problem. You are experiencing so much difficulty implementing this because it is unnecessary and does not add any tangible security.

You should start with a threat model - not a solution. Without one, all efforts like these are in vain, and may even worsen overall security posture.

---

### Post by 0f4d0335 on 2024-07-10
> **BatteryKing said:**
> To explain a little more of why I am trying to do this:

. . .

The problem with all of this is, at least with Ubuntu 24.04, I failed in multiple places to make this work.  So this is not a viable route until these issues get fixed.

I don't think that needs to be the case. Here are a few alternative options.

[LIST]
[*]Use a file key stored in a USB [[https://www.cyberciti.biz/hardware/cryptsetup-add-enable-luks-disk-encryption-keyfile-linux/]](https://www.cyberciti.biz/hardware/cryptsetup-add-enable-luks-disk-encryption-keyfile-linux/]). This isn't as good as Yubikey, but you can make it complex. The problem is if you have access to the USB, you can decrypt the hard disk without a pin. 
[*]Automate a backup for each system using bash. Create a high entropy passphrase and store it in a vault. That way you can always restore the hard drive. You cannot delete this key without knowing it unless you reformat the drive. 
[/LIST]

---

### Post by BatteryKing on 2024-07-10
While it looks like some here either want to attack what I set out to do or at least try to convince me that I need to forget about FIDO2, I have considered all of the above and have drawn different conclusions.  I see no technological reason why these things couldn't be made to work.  I see no technological reason why what I set out to do is "a bad idea" or "doesn't solve anything".  I have done research.  I have consulted experts.  I have done testing.  It is like I said the Earth is round and now people are trying to tell me the Earth is flat.  I didn't say what I originally said because of a gut feel.  I came here after gathering a considerable body of evidence and that body of evidence led me down attempting this particular path.

I came here hoping someone could see what I was trying to do and maybe provide some thoughts of what I could be doing to get closer to the goals set out.  I actually had considered various things brought up in the replies above before ever posting, but the body of evidence gathered pointed me down a particular path and away from what the commentary says.  If not help now, at least it is known that someone wants to do this, but cannot make it work.  After all, if a problem is not known, why would anybody try to fix it?

---

### Post by BatteryKing on 2024-07-10
Maybe to cover one point as it may be a bit less obvious, a device you use for MFA is not a device in constant use.  There is a thing called MFA fatigue and this refers to the mechanism you use to better secure the mechanism that keeps failing people being used too much leads to that mechanism ultimately failing in the same sorts of ways.  In other words, your FIDO2 key is usually something you keep stowed somewhere; it is not continuously connected up to your computing device.  If it is, then you are doing it wrong.  When it comes to adding encrypting data at rest, if you are constantly rebooting the computer you are trying to protect, then you are probably doing something wrong.  The normal case is you only reboot when you have to.

So now you get into a laptop computer getting stolen.  Especially if the computer is at a lock screen or ends up at a lock screen, a would be thief might think, well just bring it up off of a boot disk and get in.  This quickly fails with data at rest.  And with the ESET example, you can remote kill the computer and then encrypted data at rest can be super handy at protecting your data.  With a properly used FIDO2 key, it is not at the computer and even if it also gets stolen, 8 attempts and it is worthless to anybody.  There are also things like if you end up with the wrong significant other and it seems more often than not even getting as far as marriage ends in divorce.  And with people like Hans Rieser, who had his own Linux file system, his ex was a real piece of work to the point where he just lost it one day and has been in jail for a long time because of that.  I mean data at rest can be a very useful thing, especially if you know what is up.

---

### Post by 0f4d0335 on 2024-07-10
> **BatteryKing said:**
> ...

I don't doubt that you've done planning and research. It's pretty obvious. Yubikey is a good tool, but you mention its shortcomings. I'm then unsure why you're writing this thread, because if you want application development done, it's probably better to speak with the application teams for LUKS and Yubikey. You may also see if the Ubuntu project might respond to a feature request [[https://launchpad.net/ubuntu]](https://launchpad.net/ubuntu]).

I've provided alternatives you can pursue with USB and a backup system (which could be used with Yubikey). How the backup system works is that with your automated install script, you generate a password, send that password to backup vault, and then register the Yubikey before deleting the initial key that is easy to guess. Therefore you will have a complex key that meets password complexity. You can rotate that key with IoC and keep backups of the vaulted key stored in case a rotation fails.

You shouldn't rely only on disk encryption. This is a pretty small control in the long run. If a device is stolen, you should regardless of controls consider the asset loss as a breach of confidentiality. There should be other controls preventing direct access to higher privilege data, like storing PII in servers rather than workstations and deleting caches of PII or source code routinely. 

Edit: I don't think remote deletion is a reliable control.

---

### Post by currentshaft on 2024-07-10
> **BatteryKing said:**
>  I see no technological reason why these things couldn't be made to work.


Just because something is "made to work" does not mean it is a worthwhile thing to do.

> **BatteryKing said:**
>  
I see no technological reason why what I set out to do is "a bad idea" or "doesn't solve anything".


Really? You listed 7 reasons why it doesn't work in your initial post.

> **BatteryKing said:**
>  
I have done research.  I have consulted experts.  I have done testing.  It is like I said the Earth is round and now people are trying to tell me the Earth is flat.

It's actually the opposite: you are clamoring on that the earth is flat, while people have clearly told you it is round. Yet you cling to the false notion because ... you have consulted experts?

> **BatteryKing said:**
>  
I came here hoping someone could see what I was trying to do and maybe provide some thoughts of what I could be doing to get closer to the goals set out

What are you trying to do? We still don't know. The only thing you have described is a complicated, unnecessary authentication flow which actually creates more risk than it sets out to solve.

So I will ask again: what problem are you solving?

---

### Post by currentshaft on 2024-07-10
> **BatteryKing said:**
> your FIDO2 key is usually something you keep stowed somewhere; it is not continuously connected up to your computing device.  If it is, then you are doing it wrong.


Just complete and total nonsense. You must have a very creative imagination or have been seriously misinformed. FIDO2/Webauthn tokens are meant to remain plugged in to computers at all times, that is why Yubico makes a slim form factor.

> **BatteryKing said:**
> 
When it comes to adding encrypting data at rest, if you are constantly rebooting the computer you are trying to protect, then you are probably doing something wrong.  The normal case is you only reboot when you have to.


What? I mean, just what? This is such a silly unqualified statement which honestly does not even logically follow this conversation. And it is also wrong, because a computer turned off with full volume encryption is much more secure than one powered on.

> **BatteryKing said:**
> 
So now you get into a laptop computer getting stolen.  Especially if the computer is at a lock screen or ends up at a lock screen, a would be thief might think, well just bring it up off of a boot disk and get in.  This quickly fails with data at rest.

Exactly. You got it. LUKS prevents adversaries from accessing data at rest. That's it - that problem is solved. Move on to other security risks.

> **BatteryKing said:**
> 
  And with the ESET example, you can remote kill the computer and then encrypted data at rest can be super handy at protecting your data

No, you can't. That requires networking, which does not exist in preboot environment, nor in fadaday bags professional criminals use.

> **BatteryKing said:**
> 
 With a properly used FIDO2 key, it is not at the computer and even if it also gets stolen, 8 attempts and it is worthless to anybody. 

You've just created a risk of a user forgetting their PIN and their disk becoming worthless, which is tenfold greater than an attacker trying to decrypt the same.

> **BatteryKing said:**
> 
 There are also things like if you end up with the wrong significant other and it seems more often than not even getting as far as marriage ends in divorce.

What on earth does this bizarre social commentary have to do with ANYTHING?

> **BatteryKing said:**
> 
  And with people like Hans Rieser, who had his own Linux file system, his ex was a real piece of work to the point where he just lost it one day and has been in jail for a long time because of that.  I mean data at rest can be a very useful thing, especially if you know what is up.

Seriously, stop the FUD.

Sit down and make a threat model. You are allowing yourself to be carried away by silly ideas which are not based in objective reality, and actually may have negative impacts on your security and privacy in spite of your stated goals. Come back down to the earth, clearly and objectively state what data you are trying to protect, from whom, and what the adveraries capabilities are to justify particular defenses.

---

### Post by BatteryKing on 2024-07-10
Just with the statement of the Yubikey is supposed to be left in at all times, have you actually used one?
All of this commentary, it is a waste of my time to reply any more really.  Someone is obviously out to get me and I don't want to play these games and it is not what I came here for.

---

### Post by currentshaft on 2024-07-10
> **BatteryKing said:**
> Just with the statement of the Yubikey is supposed to be left in at all times, have you actually used one?
All of this commentary, it is a waste of my time to reply any more really.  Someone is obviously out to get me and I don't want to play these games and it is not what I came here for.

From the official Yubico website:

[https://www.yubico.com/product/yubikey-5-nano/](https://www.yubico.com/product/yubikey-5-nano/)

"The &#8220;nano&#8221; form-factor is designed to stay in your device"

Like I said, please stop the FUD.

---

### Post by 0f4d0335 on 2024-07-10
> **currentshaft said:**
> From the official Yubico website:

[https://www.yubico.com/product/yubikey-5-nano/](https://www.yubico.com/product/yubikey-5-nano/)

"The &#8220;nano&#8221; form-factor is designed to stay in your device"

Like I said, please stop the FUD.

Sorry -- I know this topic is pretty much done. But to add, I agree with user currentshaft that Yubikey's primary use is for MFA auth on (primarily web, like Google) applications, not necessarily LUKS. Which is why you'd likely have the device connected to your workstation at all times. So you'd need to convince those teams it's worthwhile to improve. I don't think the security forums for general use Ubuntu is a productive arena for that debate. Though it's great fun to consider...

You're not the first person to think of this use case, and I think it's worthwhile. I just don't think the applications reliant on this process are mature enough to be reliable.

From my perspective, I think a combination of data classification, restricting data exfiltration to workstations, and DLP are better methods of securing data than relying on workstation encryption alone. I could do research to back this one up, but who has time. :-k

I think the best solution would feature a Yubikey-like solution with LUKS. LUKS would ask for the pin from Yubikey, and they have k attempts until the key is destroyed. On top of this, the sensitive data would be secured on a centralized server that requires MFA to access. You could have the Yubikey be that MFA. And then the solution would be budget efficient and quite effective with the pin timeout for LUKS. The single point of failure of course is the Yubikey and stealing the workstation while its online. Then your DLP would need to somehow lockout access to the sensitive data.

---

### Post by currentshaft on 2024-07-10
> **0f4d0335 said:**
> I think the best solution would feature a Yubikey-like solution with LUKS. LUKS would ask for the pin from Yubikey, and they have k attempts until the key is destroyed.

How is that better or even different than LUKS encryption with the same PIN?

It's the same level of security for an exponentially greater amount of effort and reliability risk. It makes no sense.

---

### Post by 0f4d0335 on 2024-07-10
> **currentshaft said:**
> How is that better or even different than LUKS encryption with the same PIN?

It's the same level of security for an exponentially greater amount of effort and reliability risk. It makes no sense.

Yubikey has the feature to lockout after a number of attempts of the pin and can be managed.

[https://support.yubico.com/hc/en-us/articles/360013779219-Smart-Card-PIN-Unlock-Reset-Operational-Approaches](https://support.yubico.com/hc/en-us/articles/360013779219-Smart-Card-PIN-Unlock-Reset-Operational-Approaches)

Therefore, having the Yubikey can provide minimal interaction from the user (small pin) and require them to have the physical key when decrypting. Therefore, you can have a process to keep the key away from the workstation during normal operations and or even include the Yubikey as part of the employee's identity.

It's better than simply remembering a password in that the Yubikey can lock itself and manage its access. You don't have those controls with just a memory pass key.

---

### Post by currentshaft on 2024-07-10
So the adversary you're worried about is going to steal a laptop AND try to brute-force LUKS (unlike 99% of criminals who will just format the PC and sell it abroad).

The adversary is extremely skilled and highly motivated to go through all that trouble. But they are too inept to also steal the Yubikey and guess or phish the simple PIN needed to unlock the volume. 

This narrative borders on ludicrous. It is security theater. All it does is reduce the reliability of the platform.

Not a single Fortune 500 company uses this method of encrypting their employees' laptops. Do you have something more important than them to protect - and think you know more than their security teams?

---

### Post by 0f4d0335 on 2024-07-11
> **currentshaft said:**
> So the adversary you're worried about is going to steal a laptop AND try to brute-force LUKS (unlike 99% of criminals who will just format the PC and sell it abroad).

The adversary is extremely skilled and highly motivated to go through all that trouble. But they are too inept to also steal the Yubikey and guess or phish the simple PIN needed to unlock the volume. 

This narrative borders on ludicrous. It is security theater. All it does is reduce the reliability of the platform.

Not a single Fortune 500 company uses this method of encrypting their employees' laptops. Do you have something more important than them to protect - and think you know more than their security teams?

Please see my previous posts [[6]("https://ubuntuforums.org/showthread.php?t=2499034&p=14196889#post14196889"), [9]("https://ubuntuforums.org/showthread.php?t=2499034&p=14196935#post14196935"), and [14]("https://ubuntuforums.org/showthread.php?t=2499034&p=14196958#post14196958")] on better mitigation controls. I'm explaining what Yubikey provides that is different from USB with key file (same method just less management, less cost).

Standard full disk encryption is either required or recommended in GPDR, PCI - DSS, NIST, and CIS. All these frameworks are due process for corporations, and their security teams will deploy workstations with some version of encryption. But the stronger controllers were mentioned in my earlier posts.

Edit. I really dislike the idea of security theater in terms of vendor options. I think it's fine that security is done however, but it has its use cases. When people say "security theater," I think of writers sensationalizing the mundane and frustrating airport security, not Yubikeys. Yubikeys are well-used. I don't need to speak about personal experiences to know this. But if I were running a small dev team on Ubuntu workstations, I don't think my go-to would be to install Yubikeys just because I don't think the support for the device is mature enough. Concerning threat modeling, Yubikey is fine to use as MFA and disk encryption. In a production environment, I would be sure to have a SME configure it. Justifying the cost should be done in the BIA and ALE.

---

### Post by currentshaft on 2024-07-11
> **0f4d0335 said:**
>  Yubikeys are well-used. 

Not for full volume encryption, it's not.

Perhaps this is a "fun" research project, but as I'd already stated, no security professional is doing this because it's unreliable and adds nothing to security.

---

### Post by QIII on 2024-07-13
I doubt 0f4d0335 is interested in breaking out flame throwers.  Given that their previous posts discussed other methods, I think we can safely assume that they are not making a personal recommendation here.

Let's not turn this into a flame war.

---

### Post by Robert Baptista on 2024-08-04
It doesn't sound like you are making it as far as where this would have an  effect, but what version of CTAP is your yubikey using? For this setup  you will want to make sure your key is using 2.1. It's possible 2.1 PRE  will work, but I can't confirm. For digging further into your troubleshooting, you will probably want to look at sites that are security focused as I don't think security at the level you desire has made it's way to this type environment/forum yet.

---

