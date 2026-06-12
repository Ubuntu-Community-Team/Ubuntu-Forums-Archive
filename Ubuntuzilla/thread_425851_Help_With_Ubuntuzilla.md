---
title: "Help With Ubuntuzilla"
date: 2007-04-28
forum: Ubuntuzilla
---

### Post by SexiiJessi on 2007-04-28
I Put In The right codes in the terminal, but this is what it says,  it cant connect to download it then it says its exiting i dont know whats wrong 

HELP

---

### Post by aysiu on 2007-04-28
Instead of summarizing the output, can you copy and paste the exact error? Actually, just copy and paste everything you can from the terminal (the error and everything surrounding it).

---

### Post by pseudo_nz on 2007-05-02
> **aysiu said:**
> Instead of summarizing the output, can you copy and paste the exact error? Actually, just copy and paste everything you can from the terminal (the error and everything surrounding it).

I'm not sure if I'm stuck at the same point, but I've downloaded and run the script, which has downloaded the latest firefox - it's verifying the GPG signature that grinds everything to a halt.

This is what I've got:

> 20:48:30 (2.59 KB/s) - `firefox-2.0.0.3.tar.gz' saved [9651693/9651693]

The next step will verify the GPG signature for the Firefox archive to assure its integrity. This step is important for your security. However, if you have problems getting this to work right, you may choose 'no' and proceed to installation without signature verification. Do you want to verify the signature [y/n]?y

Downloading Firefox signature from the Mozilla site

--20:49:10--  [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc)
           => `firefox-2.0.0.3.tar.gz.asc'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc) [following]
--20:49:17--  [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc)
           => `firefox-2.0.0.3.tar.gz.asc'
Resolving releases.mozilla.org... 130.239.18.158, 130.239.18.159, 64.50.236.214
Connecting to releases.mozilla.org|130.239.18.158|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 186 [text/plain]

100%[====================================>] 186           --.--K/s

20:49:26 (16.13 MB/s) - `firefox-2.0.0.3.tar.gz.asc' saved [186/186]


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net. Trying again...
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net. Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu. Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu. Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu. Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu. Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.


How can I restart the verification process, or skip it altogether and get firefox 2.0 installed?

---

### Post by nanotube on 2007-05-02
> **pseudo_nz said:**
> I'm not sure if I'm stuck at the same point, but I've downloaded and run the script, which has downloaded the latest firefox - it's verifying the GPG signature that grinds everything to a halt.

This is what I've got:



How can I restart the verification process, or skip it altogether and get firefox 2.0 installed?

well, you could 
1. try running the script again, and see if it retrieves the gpg key this time (the script is smart enough not to try downloading the firefox archive again, if it's already present), or 
2. say "no" when it asks you "would you like to verify the gpg signature (not recommended, unless the gpg key retrieval keeps failing even after multiple runs - which it shouldn't be doing...)

---

### Post by pseudo_nz on 2007-05-03
> **nanotube said:**
> well, you could 
1. try running the script again, and see if it retrieves the gpg key this time (the script is smart enough not to try downloading the firefox archive again, if it's already present), or 
2. say "no" when it asks you "would you like to verify the gpg signature (not recommended, unless the gpg key retrieval keeps failing even after multiple runs - which it shouldn't be doing...)

Thanks, I wasn't sure if starting again from scratch would mean another download or not.  The gpg verification didn't work the second time either, but I installed it anyway, on the assumption that if it was vital, I wouldn't be given the option to skip it, lol.

---

### Post by nanotube on 2007-05-03
> **pseudo_nz said:**
> Thanks, I wasn't sure if starting again from scratch would mean another download or not.  The gpg verification didn't work the second time either, but I installed it anyway, on the assumption that if it was vital, I wouldn't be given the option to skip it, lol.

well, i'm glad it worked out for you. but it is mighty strange that you weren't able to retrieve the key. i just tried again myself, and had no problems - maybe it's some kind of a network problem specific to your location...?
well anyway, enjoy your software. :)

---

