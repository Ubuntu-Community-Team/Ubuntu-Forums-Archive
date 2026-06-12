---
title: "What I don't understand about gpg, pgp etc"
date: 2008-11-11
forum: Security
---

### Post by Jimmy9pints on 2008-11-11
I have read quite a lot of documentation on this subject so far and a few things are clear:

[LIST=1]
[*]There are very few easily understandable HowTos on this subject which include gui related instructions. If somebody wants to lend their knowledge, I will assist in the writing of such a HowTo (by putting it into newbie-speak).
[*]Encryption is a really complex subject which you could study for ever (it seems)
[/LIST]

Anyway, the gap in my knowledge is this: 

If somebody is snooping on you, so you decide to start using gpg for all your email then how can you tell your recipients where your key is? If you tell them where it is in an uncoded mail, pidgin message or other such electronic method, then the snooper would know also. Then he could easily intercept and decipher all your emails. In this case, doesn't this render the whole thing useless? 
I am sure it doesn't! And this is just a misunderstanding of the system on my part. 

james

---

### Post by randy78 on 2008-11-11
As far as I know, you need their Public Key to send them an encrypted email and they would need your Public Key to send you an encrypted email.

You've probably already seen a bunch of public keys before... they start out like this: -----BEGIN PGP PUBLIC KEY BLOCK-----

NEVER give out your private key!

---

### Post by Jimmy9pints on 2008-11-11
If you're right, that clears things up... but it doesn't make it so practical if you have friends who are not so tech-converstant.

Cheers.

---

### Post by randy78 on 2008-11-11
Right, but as with anything else in this life, there's always a compromise.
:guitar:

---

### Post by ProgramErgoSum on 2008-11-11
And, with encryption, it is always a matter of policy and *then* technology. Meaning, it is an organisation/individual's policy to decide who gets to see/do what. Until this 'security clearance' is in place, any security system is bound to fail.

---

### Post by kevdog on 2008-11-11
Here are a couple of quick notes on the topic you may want to check out:

Dr Small's excellent beginner's guide to GnuPG:
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)

My advanced concept guide to Gnupg (which is never completed -- sorry about that -- I'm always adding more as I am discovering more.)
[http://ubuntuforums.org/showthread.php?t=687173](http://ubuntuforums.org/showthread.php?t=687173)

The GUI's available for gpg in Ubuntu really depend on how you are going to use it.  Seahorse is probably the most well known.  If you are using Gmail and want gnupg capabilities, there is a firefox extension plugin available known as firegpg.  I'm not aware of any other Gui's available.  If you are using Windows there is a free product known as WinPT.  I would stay away from another free windows product known as PGP ckt -- not that it doesn't work, its just outdated and not maintained.  PGP makes GnuPG compatible software, of course this software isn't free.

Lastly don't upload your key to a keyserver prematurely.  You can always email your public key to the recipient.  

As far as others known that you are sending encrypted email b/c its advertised -- its OK!!!! The encryption schemes used with GnuPG as NSA level encryption mechanisms, and there is some speculation that they are currently unbreakable -- No one really knows for sure.

Are far as encrypting pigdin or IM messages -- it depends on the platform and programs your friends are using.  If you are using a mixture of linux, widows, Mac machines, there are two plugins known as OTR (Off-the-Record) Messaging and Pidgin Encryption.  These don't use GnuPG strictly to provide the encryption but use much the same algorithms.  Dr. Small informed me the other day that a plugin known as Gajim -- which strictly uses GnuPG for encryption, is a Python based client only for the Jabber protocol (which is Gmail and a handful of others), and requires GTK libraries for the GUI.  This seems to be an excellent product.  A recent small thread about the possibilities of encryption with IM or pidgin is here: [http://ubuntuforums.org/showthread.php?t=968815](http://ubuntuforums.org/showthread.php?t=968815)

---

### Post by gtmikey on 2008-11-12
> **Jimmy9pints said:**
> If you're right, that clears things up... but it doesn't make it so practical if you have friends who are not so tech-converstant.

Cheers.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

You notice that all you need to send to your non-technical friends is your PUBLIC key.  The easiest way(s) to do that is 1. Send them a signed but unencrypted message.  The message could be how to save your attached public key.  2.  I think this would be the preferred method.  Put your public key in a public keyserver such as ldap://keyserver.pgp.com.  (The public keyservers share this information.  At least when I put my public key on pgp.com it was also on mit's server the next day.)  You can do that by going to [https://keyserver2.pgp.com/vkd/GetWelcomeScreen.event](https://keyserver2.pgp.com/vkd/GetWelcomeScreen.event) and following their directions.  I include both the http information for manual key retrieval and the ldap information for automatic retrieval as part of my human readable signature file so the information shows at the bottom of each e-mail I send. Here is my human readable signature:

GT Mikey Carter

public key available manually at

[https://keyserver2.pgp.com/vkd/GetWelcomeScreen.event](https://keyserver2.pgp.com/vkd/GetWelcomeScreen.event)

or automatically at

ldap://keyserver.pgp.com

You can send a signed (in both e-mail senses) message to your friends explaining how to set up automatic retrieval if their GPG installation supports it.  I use Thunderbird which supports a list of servers.  My actual usage has been limited so others may be able to comment on the automatic server effectiveness. 

Part two and the largest part of your problem is getting your friends to generate keys and send them to you.  The procedure is the same but much simplified if they post their public keys on a server.  All the friends can retrieve them from there.
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEARECAAYFAkkbXEQACgkQ+noqypbDKF+qrQCfbEDllgcOOrav2Q9drkKHoJp2
GPQAoIIlgLn3D3qKJx7x1Mxr17yBLJTb
=fxrc
-----END PGP SIGNATURE-----

---

### Post by Gamma746 on 2008-11-12
> **Jimmy9pints said:**
> If somebody is snooping on you, so you decide to start using gpg for all your email then how can you tell your recipients where your key is? If you tell them where it is in an uncoded mail, pidgin message or other such electronic method, then the snooper would know also. Then he could easily intercept and decipher all your emails. In this case, doesn't this render the whole thing useless? 

That's known as a man-in-the-middle attack.  The best way to stop that would be to establish a web of trust ([http://en.wikipedia.org/wiki/Web_of_trust](http://en.wikipedia.org/wiki/Web_of_trust)) or contact your friends by a secure medium (via telephone, or a face-to-face meeting) and compare key fingerprints.

---

