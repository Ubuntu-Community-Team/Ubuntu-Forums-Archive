---
title: "Installing Truecrypt on ubuntu 11.04"
date: 2012-05-01
forum: Security
---

### Post by emonti on 2012-05-01
Hi

Am attempting to follow the truecrypt install instructions on their site.

The problem I'm having is with GPG(I'm trying to verify the authenticity of the download). Seems I'm lacking a means to import a public key for signing. There was a thread([http://ubuntuforums.org/showthread.php?t=680292&highlight=FireGPG](http://ubuntuforums.org/showthread.php?t=680292&highlight=FireGPG)) describing how to import but it is a bit dated (2008) and thus none of the four methods suggested actually work.

FireGPG is no longer supported/available, GPA package cannot be located by apt-get, Seahorse doesn't seem to know about importing a public key and the terminal method returns a 'Total number processed 0' result.

Any help appreciated.

---

### Post by rookcifer on 2012-05-02
```
gpg --recv-keys --keyserver pgp.mit.edu F0D6B1E0
```

From there run:

```
gpg --verify <NameOfFile.sig.

```

Unless you sign the key it will say that the key can't be trusted.  All you care about is seeing if the signature matches the key and it will tell you whether it does or not.

---

### Post by emonti on 2012-05-02
Thanks for that. One question before I follow your instructions: What is 'F0D6B1E0'? What keys am I asking for?

The Truecrypt instructions I'm attempting to follow are as follows:

> **How to Verify PGP Signatures**

 To verify a PGP signature, follow these steps:
 
[LIST=1]
[*]Install any public-key encryption software that supports PGP signatures. Links to such software can be found [here]("http://www.truecrypt.org/links").
[*]Create a private key (for information on how to do so, please see the documentation for the public-key encryption software).
[*]Download our PGP public key from our server or from a trusted  public key repository, and import the downloaded key to your keyring  (for information on how to do so, please see the documentation for the  public-key encryption software).
[*]Sign the imported key with your private key to mark it as trusted   (for information on how to do so, please see the documentation for the  public-key encryption software).      
    Note: If you skip this step and attempt to verify any of our PGP  signatures, you will receive an error message stating that the signing  key is invalid.
[*]Download the digital signature by clicking the *PGP Signature* button  next to the  file you want to verify (on one of the [download pages]("http://www.truecrypt.org/downloads")).
[*]Verify the downloaded signature (for information on how to do so,  please see the documentation for the public-key encryption software).
[/LIST]
([http://www.truecrypt.org/docs/?s=digital-signatures](http://www.truecrypt.org/docs/?s=digital-signatures))

So I have done the first part of 3. in that I've downloaded two files... one is the actual truecrypt package and the other one being the .sig which I'm supposed to use to verify the download.

So it is saying I need to import what I have downloaded. I'm a bit lost, I'm afraid.

Thanks for your help

---

### Post by rookcifer on 2012-05-02
> **emonti said:**
> Thanks for that. One question before I follow your instructions: What is 'F0D6B1E0'? What keys am I asking for?

That is the key-ID of Truecrypt's public key.

> So I have done the first part of 3. 

You shouldn't need to install any public-key software since GPG already comes with Ubuntu.

> in that I've downloaded two files... one is the actual truecrypt package and the other one being the .sig which I'm supposed to use to verify the download.

After you import their key as I described above, open a terminal.  Do a "cd" until you get in the directory where the file is.  Then run:

```
gpg --verify truecrypt*.sig
```

---

### Post by emonti on 2012-05-03
Hi,

Thanks for your help.

When I said 'first part of 3', I meant first part of point 3. The source of my confusion was the use of the words 'download' and 'import', where Truecrypt documentation uses 'download', you were using 'import' and where Truecrypt docs use 'import', they mean import it into a local gui-accessible register of some kind (they say, 'import the downloaded key to your keyring'). 

Anyway, I get the gist of it, now, thanks. 

What about the site? Never having performed this verification process of the download before, how do I know pgp.mit.edu is a trustworthy key repository for Truecrypt?

---

### Post by rookcifer on 2012-05-03
> **emonti said:**
> What about the site? Never having performed this verification process of the download before, how do I know pgp.mit.edu is a trustworthy key repository for Truecrypt?

pgp.mit.edu is probably the largest keyserver in the world.  All it does is provide a directory lookup so you can find public keys.  It serves no other function and does nothing to verify the keys are legit.  Indeed, this is all a keyserver should do!  If the keyserver verified identities, then it would turn into a CA, and no longer be neutral.

It is *up to you* to verify the key is legit and belongs to who you think it does.  With truecrypt you will never be able to do this unless you meet the TC devs in person (or have a trusted third party) verify the key.  This is known as the ["web of trust."]("http://www.pgpi.org/doc/pgpintro/#p17")  It is a hard problem to solve when you do not know the person whose key you need to use.  This is why the web of trust is there.  It is designed so that you will find people you *do* know and have them sign your key.  Then those people will know people you don't know and if you trust your friends, then you can be pretty sure they have checked out their own friends well enough for you to also trust them.  They can vouch for those other keys for you.  It goes on down the line as far as you feel comfortable with. (friends of friends of friends of friends, etc.)

In the case of truecrypt, you can download the key I gave you and look at the signatures on it.  If you feel enough people signed their key, then you can be reasonably sure it probably is not a fake.  Also, you can check their website and get the key ID from there.  If that key ID matches the one I gave you, then you can be pretty sure it is the right key.  (It would take someone hacking their website and putting up a fake key ID).  Supposedly you can download their public key directly from their site, but I just used a keyserver.

Also, I think you are confusing the .sig file for their public key.  They are not the same!  The .sig file is just a file signed by their public key.  In order to check that file you first need the public key itself.

Unless we meet the TC devs face-to-face we never can be 100% sure of anything.  However, I feel that if the key you download from their site matches the .sig file, then you are probably good.  It would take someone hacking their website and putting up a fake key and fake packages.  While not impossible, this is unlikely.  It just depends on how paranoid you are.  

I hope this makes sense.

---

### Post by emonti on 2012-05-07
Hi,

Thank-you for that reply. Yes, some of it makes a lot of  sense but I'm afraid I don't get the overall picture of what is  happening. I think it may just be a case of 'can't see the forest for the  trees'. Looking at the finer details when I should be looking first at  the bigger picture of what is happening. I first need to zoom out and  then I can come back in.

Thanks, though :-)

---

### Post by rookcifer on 2012-05-07
> **emonti said:**
> Hi,

Thank-you for that reply. Yes, some of it makes a lot of  sense but I'm afraid I don't get the overall picture of what is  happening. I think it may just be a case of 'can't see the forest for the  trees'. Looking at the finer details when I should be looking first at  the bigger picture of what is happening. I first need to zoom out and  then I can come back in.

Thanks, though :-)

Yes the whole concept can be a bit difficult to understand at first, which is unfortunate as it discourages people from using the system at all. Indeed, even expert cryptographers did not understand the system when Whitfield Diffie tried to explain it to them when he invented it back in the 70's.

Just remember that a public key is a key you give to everyone.  A private key is one you keep secret and allows you to make signatures that other people can verify by checking the sig against the public key.

So in the case of software like TC, since Ubuntu does not do the checking for you, you must do it yourself.  This means getting a hold of the TC public key.  You can download it from their site or get it from a keyserver (as I explained in my previous post).  The problem with this is you cannot be 100% sure it really is the correct key.  Anyone can make a GPG key and name it "Truecrypt Developers" and then upload it to the keyservers.  This is why it is recommended to never trust a key unless you have met the owner of the key in person and have verified it by checking his physical ID.

Another way to do this is to trust a third-pary to do the checking for you (this is what CA's in SSL are for, though they fail badly in practice.  That's a whole other story though.)  For instance, we all use Ubuntu as a third-party CA without realizing it.  We trust they have verified that the packages in the repos really did come from the legit author and not an imposter.  Once they have done that, they sign it with their own key which we all have a copy of in our distro.  I hope this makes sense.

So as for TC, it is doubtful you will ever be able to physically verify the key.  So all you can do is get the key from their website and then hope someone hasn't hacked their website and uploaded a fake key.  You can also check the signatures on their key and see if anyone trustworthy has signed off on it.  Once you get the key and feel relatively certain it is theirs, then you merely use that key to verify the software you download.  If it matches, then you can be fairly certain it is legit.

---

### Post by emonti on 2012-10-15
> Just remember that a public key is a key you give to everyone.  A  private key is one you keep secret and allows you to make signatures  that other people can verify by checking the sig against the public key.

Okay so let me get this straight...

If I want to verify that the Truecrypt archive is authentic, I need to check that it has been privately signed by Truecrypt. I do this by checking the .sig file against the public key they distribute. 

Correct?

---

### Post by rookcifer on 2012-10-15
> **emonti said:**
> Okay so let me get this straight...

If I want to verify that the Truecrypt archive is authentic, I need to check that it has been privately signed by Truecrypt. I do this by checking the .sig file against the public key they distribute. 

Correct?

Correct.

---

### Post by emonti on 2012-10-17
> **rookcifer said:**
> Correct.

Okay. And the following command achieves this:

gpg --verify truecrypt*.sig


i.e. gpg finds the public key for Truecrypt on my public keyring. 

Correct?

It seems to me the original Truecrypt archive is not being referenced here. What is gpg comparing to achieve authentication?

---

