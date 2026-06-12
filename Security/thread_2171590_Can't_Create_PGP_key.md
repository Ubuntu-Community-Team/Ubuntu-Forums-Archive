---
title: "Can't Create PGP key"
date: 2013-08-31
forum: Security
---

### Post by alain4 on 2013-08-31
Hello ,

I initiated the process of creating a pgp key in TERMINAL , all was going 
find until the moment of the passphrase definition when a GUI window appeared on desktop
to define it. after typing th passwd the Terminal returned a message that the key
was not created because it needs 284 more bytes (something like that).

Any Comments or solution for it ??

Thankx for helping ...

UBUNTU 13.04

---

### Post by Doug S on 2013-08-31
The PGP key generation needs random entropy bytes to make a good key. The terminal message should have mentioned that you need to type characters and/or move your mouse around and such, so that eventually it will get enough bytes to make the key. It can take a surprisingly long time, and even need more bytes than a previous message, but eventually it should finish.
Try again, and if your troubles continue (and even if you succeed), please post back here.

---

### Post by alain4 on 2013-09-01
> **Doug S said:**
> The PGP key generation needs random entropy bytes to make a good key. The terminal message should have mentioned that you need to type characters and/or move your mouse around and such, so that eventually it will get enough bytes to make the key. It can take a surprisingly long time, and even need more bytes than a previous message, but eventually it should finish.
Try again, and if your troubles continue (and even if you succeed), please post back here.


Thanks Doug, It worked fine , but now I Wonder where it is stored , should I use the command 'find' ???
Can't find it anywhere .


alain4

---

### Post by Doug S on 2013-09-01
There should be files located in the hidden directory ~/.gnupg
Example:```
doug@s15:~/sguide-1310/cg01$ [COLOR=#ff0000]ls -l ~/.gnupg[/COLOR]
total 32
-rw------- 1 doug doug 9364 Feb 29  2012 gpg.conf
-rw------- 1 doug doug 1194 Feb 29  2012 pubring.gpg
-rw-rw-r-- 1 doug doug 1194 Feb 29  2012 pubring.gpg~
-rw-rw-r-- 1 doug doug  600 Feb 29  2012 random_seed
-rw------- 1 doug doug 2572 Feb 29  2012 secring.gpg
-rw-rw-r-- 1 doug doug 1280 Feb 29  2012 trustdb.gpg
```

---

### Post by alain4 on 2013-09-02
Nope , The key was not there...

---

### Post by sudodus on 2013-09-02
You should not expect to 'see' the key. But you should be able to list it, and the export or send it. For example, I can list the key that I use to sign uploaded software

```
gpg -k sudodus
pub   2048R/EB0FC2C8 2012-04-08
uid                  Nio Sudden Wiklund (sudodus) <myaddress@myhost.com>
sub   2048R/4FC1D9E7 2012-04-08

```

See the manual ```
man gpg
``` for more details.

```

       -k

       --list-public-keys
              List  all keys from the public keyrings, or just the keys given on the command line.  -k
              is slightly different from --list-keys in that it allows only for one argument and takes
              the  second  argument  as the keyring to search.  This is for command line compatibility
              with PGP 2 and has been removed in gpg2.

              Avoid using the output of this command in scripts or other programs as it is  likely  to
              change  as  GnuPG changes. See --with-colons for a machine-parseable key listing command
              that is appropriate for use in scripts and other programs.

       --list-secret-keys

       -K     List all keys from the secret keyrings, or just the ones given on the command line. A  #
              after  the  letters  sec means that the secret key is not usable (for example, if it was
              created via --export-secret-subkeys).

       --export
              Either  export  all  keys  from  all keyrings (default keyrings and those registered via
              option --keyring), or if at least one name is given, those of the given  name.  The  new
              keyring  is  written  to  STDOUT or to the file given with option --output. Use together
              with --armor to mail those keys.

       --send-keys key IDs
              Similar to --export but sends the keys to a keyserver.  Fingerprints may be used instead
              of  key  IDs.  Option --keyserver must be used to give the name of this keyserver. Don't
              send your complete keyring to a keyserver --- select only those keys which  are  new  or
              changed by you.  If no key IDs are given, gpg does nothing.

```

---

### Post by Dennis N on 2013-09-02
To view public key in ascii:

View in terminal:

**gpg --armor --export UID**

UID is your email address you gave when creating the key.

Export to a file (to send to someone else)

**gpg --armor --output <filename> --export UID**

---

### Post by alain4 on 2013-09-04
Thanks to all for helping me out , my problems were all solved !!

alain4

---

