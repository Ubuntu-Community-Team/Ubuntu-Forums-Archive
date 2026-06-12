---
title: "Signing A File/String/Message"
date: 2011-03-07
forum: Security
---

### Post by shoot2kill on 2011-03-07
Hi, I have had a look around Google, with no luck, I'm hoping someone here can help me better.

I have a String that I would like to sign using a given RSA Private key. I thought this would be relatively easy but I have not been able to find out how to do it, unless I'm looking to far into a simple problem.

Do i have to put the string into a file, and sign the file, or can i just sign the string/message?

any help would be greatly appreciated.. thanks!

-----

String = "Ubuntu"
Private Key File = private.key

---

### Post by rookcifer on 2011-03-07
I have never tried to sign a string of text within the terminal without that text first being saved to a file.  It might be possible, but I've never had a need.

If you want to sign a string of text, first save it to a file and then sign it like this:

```
gpg -s file
```

If you want to "clearsign" the message, do this:

```
gpg --clearsign file
```

(Clear signing means the signature will be in a text readable format).

GPG will automatically choose your default key to sign with, but you can adjust this to use any key on your ring.

From GPG man page:


> -s     Make a signature. This command may be  combined  with  --encrypt
              (for  a signed and encrypted message), --symmetric (for a signed
              and symmetrically encrypted message), or --encrypt and --symmet&#8208;
              ric  together  (for a signed message that may be decrypted via a
              secret key or a passphrase).  The key to be used for signing  is
              chosen  by  default  or  can  be  set  with the --local-user and
              --default-key options.

       --clearsign
              Make a clear text signature.  The content in a clear text signa&#8208;
              ture  is readable without any special software. OpenPGP software
              is only needed to verify the signature.  Clear  text  signatures
              may  modify end-of-line whitespace for platform independence and
              are not intended to be reversible.  The key to be used for sign&#8208;
              ing is chosen by default or can be set with the --local-user and
              --default-key options.


---

### Post by shoot2kill on 2011-03-08
Hi, thanks for the info, but i was given a CA private key with which to sign the text/file and this is the part i am unable to figure out, how to sign the data with a separate given key, or how to import the key.

the key is in format:

```

-----BEGIN RSA PRIVATE KEY----- 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
-----END RSA PRIVATE KEY-----

```

---

### Post by rookcifer on 2011-03-08
```
gpg --import key.asc
```

Where "key.asc" is your private key file.

Then to make sure it got imported, do:

```
gpg --list-secret-keys
```

---

### Post by shoot2kill on 2011-03-09
This is what i thought, but i keep getting an error.

```

gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

the key is the same as above (obviously not all x's)
and its saved as private.key.asc

---

### Post by rookcifer on 2011-03-09
Do you have a public key that goes with this?  

Also, how was this key created?  Did you use GnuPG?

---

### Post by shoot2kill on 2011-03-10
I was given the private key by a friend, I'm not too sure how it was created.

I have been given a CA private key, and have been asked to sign a string (which I presume I can put in a text file and sign the file)

---

### Post by BkkBonanza on 2011-03-10
If the key you have is for a certificate (CA) then it's likely X.509 type. I think you'd be better off trying to use **openssl** to sign the text then. There is likely some way to convert it to gpg format but I can't recall now. Google would let you know but nonetheless most Ubuntu systems have openssl installed so using that should be easier.

I think with openssl you can pipe text directly in and sign it using S/MIME format and output it to a file or even to sendmail as an email message. Most email clients (thunderbird etc) have S/MIME support as well.

**man smime** for the smime manual.

Note - you can only sign a message if you have the private key. If you have just a certificate then you can sign it with your key for that entity as recipient, but you can't sign as that entity. If you have both then you can do anything of course. The S/MIME format ensures that the recipient gets a standard format that can be understood and verified with any X.509 compatible tool.

---

### Post by rookcifer on 2011-03-10
Let me add, that if you are still wanting to get this to work with GPG, you might want to ask at their official forum.  The GnuPG developers post over there and should be able to help.  The forum is [here.]("http://old.nabble.com/GnuPG-f951.html")

---

### Post by iiiears on 2011-03-14
BSIGN for binaries,

---

### Post by BkkBonanza on 2011-03-14
I came across this handy page for converting keys between various systems.

[http://www.sysmic.org/dotclear/index.php?post/2010/03/24/Convert-keys-betweens-GnuPG%2C-OpenSsh-and-OpenSSL](http://www.sysmic.org/dotclear/index.php?post/2010/03/24/Convert-keys-betweens-GnuPG%2C-OpenSsh-and-OpenSSL)

If you convert your ssl key to gpg then presumably you could sign with gpg. I'm not sure that does much good if the recipient doesn't have gpg to verify the signature. But then, who doesn't have gpg handy...

Anyway, just a bit more info that may help.

---

### Post by shoot2kill on 2011-03-15
This problem has now been solved using openssl.

```

openssl rsautl -sign -inkey private.key -in plain.txt -out signed.txt

```

---

### Post by BkkBonanza on 2011-03-15
I believe that will only work if the text is small. Over a certain size determined by the ley length it will fail. If your text is too long you can create a digest of the text and sign that instead.

---

