---
title: "What's worng with it?"
date: 2010-06-15
forum: Security
---

### Post by abdusamed on 2010-06-15
When ever i update.. i get this message :

```

W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0F678A01569113AE
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D725E4885719E347

```

what should i do? is ubuntu tweak the problem? Also i don't seem to get ubuntu maverick upgrade option although i have set from the preferences to get normal releases not only LTS releases....

---

### Post by an0dos on 2010-06-15
> **abdusamed said:**
> Also i don't seem to get ubuntu maverick upgrade option although i have set from the preferences to get normal releases not only LTS releases....

Maverick is not due to be released until October 2010 (or later) hence you cannot upgrade to it yet.

---

### Post by abdusamed on 2010-06-17
I'm talking about the Beta release, alpha 1.

---

### Post by abdusamed on 2010-06-17
also..i can't find those keys on synaptic authenticated keys!

---

### Post by cariboo on 2010-06-17
You can go to the ppa page an manually add the keys you need. All the pages have a link called **Technical details about this PPA**, just click the link and follow the instructions.

---

### Post by abdusamed on 2010-06-17
oh wait i have to add them not delete them?

---

### Post by abdusamed on 2010-06-17
i guess the solution is here i knew ubuntu tweak probably caused it.. 

```

https://answers.launchpad.net/ubuntu-tweak/+question/112289
```

---

### Post by cariboo on 2010-06-17
Yes, that way you know what you are getting is what the developer intended, and not something else.

---

### Post by wojox on 2010-06-17
Run these two commands

```

gpg --keyserver pgpkeys.mit.edu --recv-key  0F678A01569113AE
gpg -a --export 0F678A01569113AE | sudo apt-key add -

```

Then these two

```

gpg --keyserver pgpkeys.mit.edu --recv-key  D725E4885719E347 
gpg -a --export D725E4885719E347 | sudo apt-key add -


```

---

### Post by abdusamed on 2010-06-17
thanks.. no more error.. :).. before after following the thread which i  posted earlier.. i tried running this command:-
 ```
   W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY D725E4885719E347
  
sudo apt-get --yes --quiet --allow-unauthenticated  install  medibuntu-keyring; gpg --keyserver subkeys.pgp.net --recv  D725E4885719E347; gpg --export --armor D725E4885719E347
  After running in terminal.. i get this..
Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package medibuntu-keyring
gpg: requesting key 5719E347 from hkp server subkeys.pgp.net
gpg: key 5719E347: "Launchpad Songbird Daily Builds" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.10 (GNU/Linux)
 mI0ESjrCxwEEALcgfZWPmc1wIQ4t1t7MqFSm6YZ4hIehqeS93notnHBJpUg9wTMa
5ebb2aKyafwWYpY/NjwK/N69VEhOqf/5FfROX6YfDb4Nxk/b8IvMFlTM6MukSy07
ouv60oiI4X1kKmodZ3dBdYyGP33Up0nqwSI8+UFvOayregcATRdCqGiTABEBAAG0
H0xhdW5jaHBhZCBTb25nYmlyZCBEYWlseSBCdWlsZHOItgQTAQIAIAUCSjrCxwIb
AwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJENcl5IhXGeNHZx0D/RLbD4uiQVUg
lxsTcOjVByNf7R7oeh135cKQeCpJdlI5urfQS6Bs/svy5QzFtPq4V2prwouCvYs7
8dvbImMWgXIOVJjLCJq8TneoXL/vNbXcJZQQvQjCWs4f8hdYM8unt8j1e3N4NIic
XF4IymILkFtFzLNAAqpYhJNU3ErWwneT
=H8k3
-----END PGP PUBLIC KEY BLOCK-----

```
 But if i run this after above commad finishes, nothing seems to  happen..like it freezes
```
sudo apt-key add -; gpg --keyserver subkeys.pgp.net --recv  D725E4885719E347; gpg --export --armor D725E4885719E347

  
``` But still faced the prob... wojox's command did the trick

---

### Post by cariboo on 2010-06-18
Copy the public key block to a text file and save it, then open System->Administration->Software Sources->Authentication, then click **Import Key File**, navigate to the text file you saved and open it. You should be good to go after importing the key file.

---

### Post by rookcifer on 2010-06-18
Just thought I'd jump in and berate the OP for such a non-descriptive thread title.  ):P

---

### Post by abdusamed on 2010-06-29
OKay.. now I have even worse

```

GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D6B6DB186A68F637GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FCBFDF60D7BFC706Failed to fetch http://deb.opera.com/opera/dists/lenny/Release.gpg  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

```

now what?

---

### Post by abdusamed on 2010-06-29
I did copy paste the key code and saved it on a gedit file and imported that. But I got a error saying it's an invalid GPG key

```


D6B6DB186A68F637GPG
```

---

### Post by cariboo on 2010-06-30
The key should look like this:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.9 (GNU/Linux)

mI0ESdEXWgEEAN/397aa5ZL/O5Dip8DzRySROjTWJJneTN6c2NDIlm9U+T+jaYCP
kkUTVONI3PrynkW1yRCouSYyw32WRf4hm8J0JwKY1NdLge4vsFmFNk+issEBs3Cb
h4PRtUOGK3iIt7LQwfVbY7KxSPYQw7rG+OAdcc0TXXwIHNHdg9cBUmgVABEBAAG0
FkxhdW5jaHBhZCBQUEEgZm9yIFJpY2+ItgQTAQIAIAUCSdEXWgIbAwYLCQgHAwIE
FQIIAwQWAgMBAh4BAheAAAoJEHXP0xyeXbDIOW0D/iEL32MPcC3qseQ8sHgdgzxr
/b2fVEuWyM0ETIxMIMN+S2RHZ4xJ1yUEmfxF0zGtKqHv2MLzWXuV5DCerD+K+D2u
TSX7ePemi/eGW71E2aJrjiTuGiD2Ikbnvv6zhx7Rf1I7UoXHYdV7ns4lCGU05gNP
ynIfbtw0lnPCCG4+rwMs
=tvSX
-----END PGP PUBLIC KEY BLOCK-----
```

I'm not sure what the number you quoted is.

---

### Post by abdusamed on 2010-06-30
how did u make that key? I need to make the key for the following
```

NO_PUBKEY D6B6DB186A68F637

```
&
```

NO_PUBKEY FCBFDF60D7BFC706

```

---

### Post by cariboo on 2010-06-30
It's up to the producer of the program to provide a key, that is the only way you know the package hasn't changed. Creating a key of your own is not going to help. If the package doesn't have a key, either don't use that package, contact the producer or use it as is. The choice is yours to make.

---

### Post by abdusamed on 2010-06-30
> **cariboo907 said:**
> It's up to the producer of the program to provide a key, that is the only way you know the package hasn't changed. Creating a key of your own is not going to help. If the package doesn't have a key, either don't use that package, contact the producer or use it as is. The choice is yours to make.

How do uncheck the repository which is giving me the key problem? Like i unchecked the latest PPA which I haded recently but I still face the same message. :confused:

---

### Post by abdusamed on 2010-07-01
Need to fix it!! I can't even install any apps from Ubuntu Software

---

### Post by abdusamed on 2010-07-01
Yes.. finally found a universal solution to all NO_PUBKEY XXXXXXXXX!

[http://www.stefanoforenza.com/solve-your-no_pubkey-ppas-in-a-snap-or-a-script/](http://www.stefanoforenza.com/solve-your-no_pubkey-ppas-in-a-snap-or-a-script/)

:)

though tar file sudo command didn't work for me, i was trying this the whole time but didn't work:-
```


sudo .~/Downloads/Launchpad-update.tar


```

don't know what's wrong with it.. but in the end.. i had to type in sudo and drag the extracted gedit file into the terminal and hit enter

---

