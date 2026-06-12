---
title: "PaperKey - A GnuPG key archiver"
date: 2009-01-26
forum: Security
---

### Post by kevdog on 2009-01-26
I ran across this utility perusing the GnuPG forums the other day: Paperkey.  It actually proposes keeping a copy of the GnuPG private key on print media.  PaperKey -- the utility to help make a paper key -- strips off all redundancy checks, the public key, and identifiers from the private key effectively only keeping the crucial parts of the private key (which would then allow reconstruction of the full private key later if you ever lost the digital copy of the private key and had to restore it!!).  I found this statement actually quite impressive (from the author of PaperKey):

For example, the regular DSA+Elgamal secret key I just tested comes out to 1281 bytes. The secret parts of that (plus some minor packet structure) come to only 149 bytes. It's a lot easier to re-enter 149 bytes correctly.

I never thought of keeping a paper copy of my GnuPG private keys, however I am definitely persuaded after seeing the arguments.

PaperKey Homepage: [http://www.jabberwocky.com/software/paperkey/](http://www.jabberwocky.com/software/paperkey/)

---

### Post by Dr Small on 2009-01-26
Say, now that's an idea. I really like this idea. I guess I'll be trying to get it installed before long to see if it will work on Arch :D

---

### Post by nubdora on 2009-01-26
Interesting!

---

### Post by adamlau on 2009-01-27
Nice, but not for me. A few hundred years? Shouldn't we be revoking and generating new keys every so often anyways :) ?

---

### Post by kevdog on 2009-01-27
If you protect your key with an appropriate password, what extra security is generating a new key going to give you?  If you are concerned about the password,  then just simply change the password.  In addition, if you keep generating multiple keys from time to time, you are going to have to keep the old private keys around if you ever at any time in the future want to decrypt data that has been previously encrypted using an old key.  That would be a pain -- like having multiple keys on your personal keyring, and then sitting on them -- way too bulky, not to mention a real pain in the butt!

---

### Post by Dr Small on 2009-01-27
> **kevdog said:**
> If you protect your key with an appropriate password, what extra security is generating a new key going to give you?  If you are concerned about the password,  then just simply change the password.  In addition, if you keep generating multiple keys from time to time, you are going to have to keep the old private keys around if you ever at any time in the future want to decrypt data that has been previously encrypted using an old key.  That would be a pain -- like having multiple keys on your personal keyring, and then sitting on them -- way too bulky, not to mention a real pain in the butt!
Exactly. The only reason I generated a new key, is because I was experimenting with uid's, and ruined the key at the keyserver. But I still keep the private key for it, since I still have all those old encrypted files from Michael Rash! :D

---

### Post by argie on 2009-01-30
This is...perfect. It is just what I've been looking for since yesterday. I was going to post on this forum asking how people back up their private keys and if printing them out was a good option. This is just perfect. Ha ha.

---

### Post by Dr Small on 2009-04-28
Sorry for reviving a several month old topic, but I've actually installed paperkey and generated a plaintext version of my secret key. I have it printed out and setting on my desk in front of me.

It has 11 rows of base16 data at the bottom of the file, with the CRC-24 block at the end of the line. Ok. So now my question is, what method do I use to regenerate my secret key? (no... I didn't actually delete my secret key, I just want to learn how to do this.)

Do I input all 11 lines into a file (in their exact format) and then run `paperkey --input-type=auto --secrets=/home/drsmall/secretkey.txt` ?

Also, will this regerate the public key also, or is there a another method to do this?

Best Regards,
Dr Small

---

### Post by kevdog on 2009-04-29
Dr. Small

I have never regenerated the key from paper, however according to the discussion, this paper copy contains all the essential parts of the private key -- every duplicate part and error checking parts have been deleted (including the public key portion of the private key).

You need to type these characters back into a text editor and save the file, and then regenerate the key as I believe you have specified.

To regenerate the public key from the private key the command is the following:

(This taken from the FAQ page):

I still have my secret key, but lost my public key. What can I do?

All OpenPGP secret keys have a copy of the public key inside them, and in a worst-case scenario, you can create yourself a new public key using the secret key.

A tool to convert a secret key into a public one has been included (it's actually a new option for gpgsplit) and is available with GnuPG versions 1.2.1 or later (or can be found in CVS). It works like this:

$ gpgsplit --no-split --secret-to-public secret.gpg >publickey.gpg

One should first try to export the secret key and convert just this one. Using the entire secret keyring should work too. After this has been done, the publickey.gpg file can be imported into GnuPG as usual. 

AND LASTLY!!!!

Trolling old threads!!! You should be ashamed!

---

### Post by Dr Small on 2009-04-29
> **kevdog said:**
> Dr. Small

I have never regenerated the key from paper, however according to the discussion, this paper copy contains all the essential parts of the private key -- every duplicate part and error checking parts have been deleted (including the public key portion of the private key).

You need to type these characters back into a text editor and save the file, and then regenerate the key as I believe you have specified.

To regenerate the public key from the private key the command is the following:

(This taken from the FAQ page):

I still have my secret key, but lost my public key. What can I do?

All OpenPGP secret keys have a copy of the public key inside them, and in a worst-case scenario, you can create yourself a new public key using the secret key.

A tool to convert a secret key into a public one has been included (it's actually a new option for gpgsplit) and is available with GnuPG versions 1.2.1 or later (or can be found in CVS). It works like this:

$ gpgsplit --no-split --secret-to-public secret.gpg >publickey.gpg

One should first try to export the secret key and convert just this one. Using the entire secret keyring should work too. After this has been done, the publickey.gpg file can be imported into GnuPG as usual. 

Well now. This truly sheds some light on things and what data I have collectively earned within the last 24 hours, I think we should have some conclusive evidence.

First off, I tried to copy all of the octaves back into a document (by reading and typing). I found out that the last block at each line is the sum of that line (used for error checking). The very last line is the sum of all the other lines. That's simple enough.

So, if there is an error, the paperkey program checks the sums and tells you on which line the error is. Very convenient. The problem with me was, I either couldn't read it or type it correctly. I kept getting errors on different lines. I eventually gave up on the thing (I'm dyslexic with numbers anyhow, by the way).

But, here is another interesting point that I discovered; paperkey can not regenerate the private key without the public key (either specify the public keyring or the path to the public keyfile). So, although it may be possible to regenerate the public key from the private key (if your key is in ASCII or binary format), you can not regenerate your keypair from paperkey. It just won't work.

Yes, paperkey is great for keeping a paper copy of the secret parts of your private key, but in order to use it you must have the public key along with it. (Not a problem if your public key is on a keyserver somewhere.) But don't think that you can regenerate the keypair (private and then public) just from the secret parts extracted by paperkey. I found out that it isn't possible!


> **kevdog said:**
> 
AND LASTLY!!!!

Trolling old threads!!! You should be ashamed!
Yes, yes... You don't know how nervous I was about contemplating the fact of reviving a dead old thread! ;)

Dr Small

---

