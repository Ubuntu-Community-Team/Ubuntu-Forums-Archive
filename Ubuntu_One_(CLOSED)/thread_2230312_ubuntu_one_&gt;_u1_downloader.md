---
title: "ubuntu one &gt; u1_downloader"
date: 2014-06-18
forum: Ubuntu One (CLOSED)
---

### Post by wwwtii on 2014-06-18
Hello, lovely ubuntu fans :-)

I am trying to install the ubuntu one, u1 downloader. (where you can download all content from ubuntu one)

But i ran into this problem: ```
bash: ./u1_downloader: cannot execute binary file
```


Whats up with that?

btw.
I am running ubuntu 12.04 (32bit)

---

### Post by markus-werthfamily on 2014-06-18
Hello!  I run ubuntu 14.04 and I got the same error.

---

### Post by finger51 on 2014-06-18
I tried it with sudo and without. without sudo I get permission denied. with sudo I get the prompt for email and password but then:
```

Traceback (most recent call last):
  File "<string>", line 336, in <module>
  File "<string>", line 308, in main
  File "<string>", line 150, in get_session
  File "<string>", line 129, in _get_token
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.api", line 88, in post
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.api", line 44, in request
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.sessions", line 383, in request
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.sessions", line 486, in send
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.adapters", line 385, in send
requests.exceptions.**SSLError: [Errno 185090050**] _ssl.c:344: error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib

```

I've got hundreds of pics from my camera on this thing... would be a bummer to have to DL them one by one.

---

### Post by wwwtii on 2014-06-18
I got this result with sudo:
```
./u1_downloader: 1: ./u1_downloader: Syntax error: word unexpected (expecting ")")

```

---

### Post by Pazit on 2014-06-18
Having the same problem on Ubuntu 12.04 LTS

```
bash: ./u1_downloader: cannot execute binary file
```

---

### Post by fergalm on 2014-06-19
I can repeat all of the above. Run as user I get 
```

 bash: ./u1_downloader: cannot execute binary file

```

Run as sudo I get
```

 ./u1_downloader: 1: ./u1_downloader: Syntax error: word unexpected (expecting ")")

```

```

$ file ./u1_downloader 
u1_downloader: ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, stripped

```

Given that I'm on a 32 bit system (12.04 I think), I'm guessing the 64bit is my problem.

---

### Post by GunnarØ on 2014-06-19
Same problem on 14.04 LTS
~/Nedlastinger/u1-downloader$ ./u1_downloader
bash: ./u1_downloader: cannot execute binary file: Ugyldig format på eksekverbar fil

---

### Post by slickymaster on 2014-06-20
[http://ubuntuforums.org/showthread.php?t=2230409&p=13054249&viewfull=1#post13054249](http://ubuntuforums.org/showthread.php?t=2230409&p=13054249&viewfull=1#post13054249)

---

### Post by Pazit on 2014-06-20
> **slickymaster said:**
> [http://ubuntuforums.org/showthread.php?t=2230409&p=13054249&viewfull=1#post13054249](http://ubuntuforums.org/showthread.php?t=2230409&p=13054249&viewfull=1#post13054249)

Thank you!!! Solved the problem for me..):P

---

### Post by katjoy06 on 2014-06-28
thanks

---

