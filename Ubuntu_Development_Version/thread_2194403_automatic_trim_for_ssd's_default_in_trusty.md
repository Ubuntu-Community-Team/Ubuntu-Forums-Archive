---
title: "automatic trim for ssd's default in trusty"
date: 2013-12-18
forum: Ubuntu Development Version
---

### Post by fooman on 2013-12-18
saw this over at the discourse site....great news!  :D  i have been adding different options to set trim since using ssd's over the last year or so (cron job, adding discard to fstab, etc...).  nice to know it will be enabled by default without having to edit anything after install!  \\:D/

[http://discourse.ubuntu.com/t/ssds-are-now-trimmed-by-default/1346](http://discourse.ubuntu.com/t/ssds-are-now-trimmed-by-default/1346)

[https://plus.google.com/107564545827215425270/posts/D2SB1zxb9Z9](https://plus.google.com/107564545827215425270/posts/D2SB1zxb9Z9)

[https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11](https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11)

---

### Post by VinDSL on 2013-12-18
Yeah, I saw that -- very encouraging!

I bought my first SSD, last week.

First thing I did was invoke TRIM.

This seems to work out pretty well...

[http://www.techrepublic.com/blog/linux-and-open-source/make-the-solid-state-drive-ssd-plunge-with-linux/](http://www.techrepublic.com/blog/linux-and-open-source/make-the-solid-state-drive-ssd-plunge-with-linux/)

I was wondering why they couldn't add something like this to +1 for testing.

Since you've been into this for awhile, what do you think of this guy's twist?!?!?

---

### Post by ventrical on 2013-12-18
I have been running my ssd on SandyBridge since 13.04 (without TRIM). Ahhh .. but Trusty will be set for TRIM by Default.

 I don't see any performance issues at current. It runs instantaneously! Closest to a super-computer that Iv'e seen. My ssd is SATA 3 Gen. I am going to replace a 13.04 partition with Trusty. I read the  link you posted. Are there any cautions about using TRIM with partitions?

---

### Post by VinDSL on 2013-12-18
> **ventrical said:**
> I read the  link you posted. Are there any cautions about using TRIM with partitions?Only thing that concerns me is the 'discard' option in the fstab drive entry.

On several sites, I've read that whole blocks of data can magically disappear without warning, when you run this option.

Heh!  I'll be using this SSD in my 'road warrior'.  I don't need to puke a drive 3000 miles from home, you know?

---

### Post by mc4man on 2013-12-18
I wouldn't bother with discard in fstab, just let the new script do what it does (currently set to run weekly in cron
( I only use noatime in fstab here for my current  ssd

---

### Post by VinDSL on 2013-12-18
> **mc4man said:**
> I wouldn't bother with discard in fstab, just let the new script do what it does [...]
pitti (I assume Pitt) script?!?!?

[http://people.canonical.com/~pitti/scripts/fstrim](http://people.canonical.com/~pitti/scripts/fstrim)

---

### Post by ventrical on 2013-12-19
It says I have to enter the first LBA adress.

hdparm --read-sector [ADDRESS] /dev/sdX

and I get ..

```

root@ventrical-MS-7798:~# hdparm --fibmap tempfile

tempfile:
 filesystem blocksize 4096, begins at LBA 2048; assuming 512 byte sectors.
 byte_offset  begin_LBA    end_LBA    sectors
           0    9516032    9520127       4096
     2097152    9582592    9586687       4096
     4194304    9439232    9447423       8192
     8388608    9472000    9504767      32768
    25165824    9635840    9689087      53248
root@ventrical-MS-7798:~# hdparm --read-sector [2048] /dev/sdX
  read-sector: bad/missing sector value
root@ventrical-MS-7798:~# hdparm --read-sector [9516032] /dev/sdX
  read-sector: bad/missing sector value
root@ventrical-MS-7798:~# 

```


So what did I do wrong?

Note. This is a fresh install of Trusty daily (seamless) so I am just testing to see if TRIM is running by default..

How to here :
[URL="https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking"]https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking

[/URL]

---

### Post by ventrical on 2013-12-19
I assume now that TRIM was not set by default in trusty daily-current install because there is no fstab directory.

---

### Post by fooman on 2013-12-19
> **ventrical said:**
> It says I have to enter the first LBA adress.

hdparm --read-sector [ADDRESS] /dev/sdX

and I get ..

```

root@ventrical-MS-7798:~# hdparm --fibmap tempfile

tempfile:
 filesystem blocksize 4096, begins at LBA 2048; assuming 512 byte sectors.
 byte_offset  begin_LBA    end_LBA    sectors
           0    9516032    9520127       4096
     2097152    9582592    9586687       4096
     4194304    9439232    9447423       8192
     8388608    9472000    9504767      32768
    25165824    9635840    9689087      53248
root@ventrical-MS-7798:~# hdparm --read-sector [2048] /dev/sdX
  read-sector: bad/missing sector value
root@ventrical-MS-7798:~# hdparm --read-sector [9516032] /dev/sdX
  read-sector: bad/missing sector value
root@ventrical-MS-7798:~# 

```


So what did I do wrong?
[URL="https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking"]

[/URL]

ventrical,  in your example above (/dev/sdX)  the "X" in sdX needs to be changed to reflect you ssd drive (sda, sdb, sdc...ect).  also the read-sector should be the number directly under "begin LBA" but WITHOUT the brackets.  so your hdparm --read-sector line should be as follows (assuming your drive is sda):

```
sudo hdparm --read-sector 9516032 /dev/sda 
```

hope that helps

---

### Post by Mateusz Stachowski on 2013-12-19
> **ventrical said:**
> I assume now that TRIM was not set by default in trusty daily-current install because there is no fstab directory.

This automatic TRIM in Trusty isn't achieved by adding discard to /etc/fstab but by running a weekly cron job and it was already pointed out by mc4man.

Read the changelog for util-linux that was linked in first post it has all that information.

[https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11](https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11)

---

### Post by fooman on 2013-12-19
> **Mateusz Stachowski said:**
> This automatic TRIM in Trusty isn't achieved by adding discard to /etc/fstab but by running a weekly cron job and it was already pointed out by mc4man.

correct...just have a look in /etc/cron.weekly and you should see the fstrim script.  which btw is a reason why the example above of checking if trim is working may not execute correctly....after running all the commands to check trim,  the final result should be all zeros....but that will not be the case until the fstrim script kicks in.  which is only weekly :(

hope that makes some sense

---

### Post by ventrical on 2013-12-19
> **fooman said:**
> ventrical,  in your example above (/dev/sdX)  the "X" in sdX needs to be changed to reflect you ssd drive (sda, sdb, sdc...ect).  also the read-sector should be the number directly under "begin LBA" but WITHOUT the brackets.  so your hdparm --read-sector line should be as follows (assuming your drive is sda):

```
sudo hdparm --read-sector 9516032 /dev/sda 
```

hope that helps

Okay.

Thanks.

TRIM is not working on my system

```

root@ventrical-MS-7798:~# rm tempfile
root@ventrical-MS-7798:~# sync
root@ventrical-MS-7798:~# sudo hdparm --read-sector 9516032 /dev/sda

/dev/sda:
reading sector 9516032: succeeded
cee0 493f 4711 8aae 8686 574d 693e 6ee3
e72c c0c4 9bd8 b67e 64d8 2f69 9377 0b2f
0599 edc7 76a9 d65e b704 d3b5 31bc 13cb
a4df 01fa 04b7 00d4 10a7 a742 b572 758e
a65b 6b54 313f dde5 3dc8 fec8 2f8d bd5c
1b59 839c 0f65 3af5 8c1e 07e8 86e3 fa8d
bc67 a5df e036 e82b de56 69ac 0922 0483
1f43 3dbf 486f c75d c0c8 20a9 f68c 3a19
8c02 63e8 3697 cdbe 65e4 9c1f a6ff a412
8265 af3d 1f97 4231 d563 50f4 2d97 b120
517c b628 524b 8de4 fa0f b5df 7fb8 ae93
129f 8d50 d95a 4435 6f59 8c43 8107 8891
37fd eb7f 5f7d e269 564c c68d 93c6 a0e2
f65c 9154 b06c cc44 2303 3372 7a4d c6ac
a12d eba0 0eb0 9c7d d693 108a afd8 a9e6
9264 ba1c 574f e1e1 c789 2055 2633 709d
d0c2 5d73 3174 afae 47c1 eaa7 2067 6db9
63e6 9c28 b0a3 1a58 8fa7 d343 ef2f b71e
87a0 2967 6d0f 0fcf f025 30cf 49ba 5854
9cb7 5929 2f6d d32b 7371 5efc a8cc 9ee6
5e10 6baf 9de2 8dbc a4f1 a7af e696 9932
5dc9 d168 b58e 2278 3339 81bf f526 8873
9cce 3b4a c9b5 f910 3e7b d4f4 795a 65e4
c9ab dfbc 3b3e b746 4fce 76d2 e7ca a17c
ff6f c5d4 b356 bcdc 889e 43df 4f9f 2c98
c668 59a1 2ee8 859e 7dc2 2f00 eb5b ee21
ff06 3e96 908c 88ca 0126 5773 9e31 2951
80e2 cf66 2133 73fc 33b5 e0da 112b d57a
e310 8186 1d3b 59b5 8410 f518 9bf5 23ae
a644 b7ae 9d3c 185b dd8a 5383 ea09 9b12
0fc2 0f2f 4e49 3edf 146c 6c2c a9dd ee06
8092 e2e4 1fe7 fdd1 d212 2482 cc69 5561
root@ventrical-MS-7798:~# 

```

---

### Post by ventrical on 2013-12-19
I tried to set it manually and it seemed to work but  no go.

```

root@ventrical-MS-7798:~# set -e
root@ventrical-MS-7798:~# exec fstrim-all
ventrical@ventrical-MS-7798:~$ sudo hdparm --read-sector 9516032 /dev/sda

/dev/sda:
reading sector 9516032: succeeded
cee0 493f 4711 8aae 8686 574d 693e 6ee3
e72c c0c4 9bd8 b67e 64d8 2f69 9377 0b2f
0599 edc7 76a9 d65e b704 d3b5 31bc 13cb
a4df 01fa 04b7 00d4 10a7 a742 b572 758e
a65b 6b54 313f dde5 3dc8 fec8 2f8d bd5c
1b59 839c 0f65 3af5 8c1e 07e8 86e3 fa8d
bc67 a5df e036 e82b de56 69ac 0922 0483
1f43 3dbf 486f c75d c0c8 20a9 f68c 3a19
8c02 63e8 3697 cdbe 65e4 9c1f a6ff a412
8265 af3d 1f97 4231 d563 50f4 2d97 b120
517c b628 524b 8de4 fa0f b5df 7fb8 ae93
129f 8d50 d95a 4435 6f59 8c43 8107 8891
37fd eb7f 5f7d e269 564c c68d 93c6 a0e2
f65c 9154 b06c cc44 2303 3372 7a4d c6ac
a12d eba0 0eb0 9c7d d693 108a afd8 a9e6
9264 ba1c 574f e1e1 c789 2055 2633 709d
d0c2 5d73 3174 afae 47c1 eaa7 2067 6db9
63e6 9c28 b0a3 1a58 8fa7 d343 ef2f b71e
87a0 2967 6d0f 0fcf f025 30cf 49ba 5854
9cb7 5929 2f6d d32b 7371 5efc a8cc 9ee6
5e10 6baf 9de2 8dbc a4f1 a7af e696 9932
5dc9 d168 b58e 2278 3339 81bf f526 8873
9cce 3b4a c9b5 f910 3e7b d4f4 795a 65e4
c9ab dfbc 3b3e b746 4fce 76d2 e7ca a17c
ff6f c5d4 b356 bcdc 889e 43df 4f9f 2c98
c668 59a1 2ee8 859e 7dc2 2f00 eb5b ee21
ff06 3e96 908c 88ca 0126 5773 9e31 2951
80e2 cf66 2133 73fc 33b5 e0da 112b d57a
e310 8186 1d3b 59b5 8410 f518 9bf5 23ae
a644 b7ae 9d3c 185b dd8a 5383 ea09 9b12
0fc2 0f2f 4e49 3edf 146c 6c2c a9dd ee06
8092 e2e4 1fe7 fdd1 d212 2482 cc69 5561
ventrical@ventrical-MS-7798:~$


```

  I'll try reboot and then try again.

---

### Post by ventrical on 2013-12-19
> **fooman said:**
> correct...just have a look in /etc/cron.weekly and you should see the fstrim script.  which btw is a reason why the example above of checking if trim is working may not execute correctly....after running all the commands to check trim,  the final result should be all zeros....but that will not be the case until the fstrim script kicks in.  which is only weekly :(

hope that makes some sense


 Yes .. makes perfect sense . Thanks for the pointers.

---

### Post by ventrical on 2013-12-19
> **fooman said:**
> ventrical,  in your example above (/dev/sdX)  the "X" in sdX needs to be changed to reflect you ssd drive (sda, sdb, sdc...ect).  also the read-sector should be the number directly under "begin LBA" but WITHOUT the brackets.  so your hdparm --read-sector line should be as follows (assuming your drive is sda):

```
sudo hdparm --read-sector 9516032 /dev/sda 
```

hope that helps

Ahhhh ...

Thanks again all.

---

### Post by ventrical on 2013-12-19
Ahhhh... :)

[https://blueprints.launchpad.net/ubuntu/+spec/core-1311-ssd-trimming](https://blueprints.launchpad.net/ubuntu/+spec/core-1311-ssd-trimming)

'Note that only 2 SSDs have been tested. The results may vary wildly with
other firmware on different SSD devices.  There is a risk that some
poorly designed devices may have a larger fstrim performance impact.'

---

