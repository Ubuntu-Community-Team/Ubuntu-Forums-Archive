---
title: "GnuPG help needed..."
date: 2010-07-02
forum: Security
---

### Post by pepsifx357 on 2010-07-02
Is there a way to add the Serpent encrytion to GnuPG?  I really like using this program but I don't trust AES, merely because I don't trust the NSA.

I saw where you could add different encryption software to it, but I had no idea where to get the files, or how to install them.

Also, the tutorial I was using said to encrypt using this method:
```
gpg -c filename
```

Is there a better, more secure way to implement this software?  I've read the manual, but I don't know what half of that stuff does...](*,)

Thanks,

Ben

---

### Post by anomie on 2010-07-02
Hi there - AES was developed by two non-NSA cryptographers, and it's been *thoroughly* tested and vetted by very smart people. 

If you still do not want to use AES for some reason, the gpg(1) option --pgp7 includes TWOFISH as a cipher. I recommend that as an alternative. 

(No, I don't know the answer to your question about how to add Serpent.)

---

### Post by pepsifx357 on 2010-07-03
> **anomie said:**
> Hi there - AES was developed by two non-NSA cryptographers, and it's been *thoroughly* tested and vetted by very smart people. 

If you still do not want to use AES for some reason, the gpg(1) option --pgp7 includes TWOFISH as a cipher. I recommend that as an alternative. 

(No, I don't know the answer to your question about how to add Serpent.)

Is AES an open source code?  The reason I picked Serpent, is because is was next in line and I read somewhere, that is was open source.  I could be wrong.

---

### Post by rookcifer on 2010-07-03
> **pepsifx357 said:**
> Is there a way to add the Serpent encrytion to GnuPG?  I really like using this program but I don't trust AES, merely because I don't trust the NSA.

Paranoid much?  

I am with you on not trusting the NSA, as I think asking them to design a public algorithm is like asking a fox to guard the hen house; it's only natural that they aren't going to supply the world with something that makes their job (signals intelligence) more difficult.  On the other hand, I doubt they care much about you and would never reveal their (alleged) ability to break AES for something on your hard drive.  The fact that they could break AES (which I doubt) would be worth much more than your data.  The ability to break AES would almost certainly be classified at the highest levels of TOP SECRET.  Think of how many potential terrorists they could lure into their trap by giving them a false sense of security.

All that said, NSA had nothing to do with the design of AES.  While it's true that NSA was asked for input during the AES competition (because NSA is the best in the world at cryptology), they didn't make the final decision and they certainly didn't design the algorithm.  Of course, a conspiracy theorist might say that the two Belgian researchers who designed the Rijndael cipher were somehow secretly working for NSA in a devious scheme to supply the world with an incredibly elegant looking cipher that really contains a secret trapdoor accessible by no one but NSA.  I will apply Occam's razor here and assert this is hogwash.

> I saw where you could add different encryption software to it, but I had no idea where to get the files, or how to install them.

There are several other symmetric ciphers that are already available within the program.  Twofish is probably the best candidate (it finished third in the competition behind Rijndael and Serpent) and is as fast as Rijndael and much faster than Serpent.  If you don't like it, then there's CAST5 and Camellia (I recommend Camellia-128 out of those two).

> Also, the tutorial I was using said to encrypt using this method:
```
gpg -c filename
```

Yeah, but I recommend putting it into armor output with the -a flag.  Here's an example:

```
gpg -ca --cipher-algo aes128 file
```

The --cipher-algo flag allows you to pick whichever algorithm GPG supports.  You can see those algos by looking at the output of gpg --version and looking at those in the "cipher" category.

Another option is to simply right click the file and encrypt it with your public key (but you first have to generate a public key).  

Or, you can use another library all together like openssl, tomcrypt, libmcrypt, Crypto++ or others.  Some of those libs contain the Serpent cipher if you are really set on using it.

---

### Post by anomie on 2010-07-03
[QUOTE=pepsifx357]Is AES an open source code?[/QUOTE]

There are many open source implementation of AES, if that's what you're asking. 

If you're asking whether AES (Rijndael) itself is "open", then yes - it's "public domain". If it wasn't, it would not have been so widely adopted.

---

### Post by pepsifx357 on 2010-07-04
Paranoid much?  Yeah you could say that.

Looking at the list of potential algorithms that were tested, the one called "serpent" caught my eye for several different reasons, ones that would take days for me to type.  The secret is in the name.

I'll just say this...I would bet my body parts, that the NSA and ALL Government agencies use Serpent encryption.  Just based on their writings and the people that were a part of the creation of the NSA.

I need to get serpent encryption to work with GPG at whatever cost.

Thanks for the helps guys.

Ben

> Or, you can use another library all together like openssl, tomcrypt, libmcrypt, Crypto++ or others. Some of those libs contain the Serpent cipher if you are really set on using it.

Just by going to synaptic and installing one of these libraries will give gpg the serpent algorithm?

---

### Post by rookcifer on 2010-07-05
> **pepsifx357 said:**
> Just by going to synaptic and installing one of these libraries will give gpg the serpent algorithm?

No, you will have to use a program that uses these libraries.  I know of no program, off the top of my head, that uses Serpent for encrypting single files.  However, if you want to encrypt a container, you can use Serpent with LUKS, which is already built-in.  Just specify serpent instead of aes, and you're good to go.  You can follow this tutorial [here.]("http://www.lylebackenroth.com/blog/2008/08/29/encrypting-containers-or-partitions-with-cryptsetup-and-luks/")

---

### Post by anomie on 2010-07-05
[QUOTE=pepsifx357].I would bet my body parts, that the NSA and ALL Government agencies use Serpent encryption.[/QUOTE]

Please do not say that. I'd argue that the NSA probably uses ciphers that it has not shared with the world. They are in a rather unique position to do so. 

On something of a tangent, you might want to check this distro out: [http://tinfoilhat.shmoo.com/](http://tinfoilhat.shmoo.com/)

The best password/key coupled with the best cipher in the world won't save you from a keystroke logger.

---

### Post by pepsifx357 on 2010-07-05
> **anomie said:**
> Please do not say that. I'd argue that the NSA probably uses ciphers that it has not shared with the world. They are in a rather unique position to do so. 

On something of a tangent, you might want to check this distro out: [http://tinfoilhat.shmoo.com/](http://tinfoilhat.shmoo.com/)

The best password/key coupled with the best cipher in the world won't save you from a keystroke logger.

LMAO, Tinfoil hat linux...That's just too funny.  I like it. \\:D/

---

### Post by rookcifer on 2010-07-07
After finding a little time to experiment with various encryption options in Ubuntu, I found mcrypt.  It uses the libmcrypt libraries, which have more ciphers to choose from 
of any crypto library I have seen.  If you want Serpent, you need to install mcrypt.

```
sudo apt-get install mcrypt
```

To encrypt a file with serpent, move to the directory of the file, then:

```
mcrypt -a serpent -s 32 -h sha512 -m cbc -r secret_file
```

This will encrypt the file with Serpent-256 using SHA-512 and cbc mode.  The -s flag provides the desired size of the key in **bytes** (not bits, which explains why I used 32.  Take your desired bit length and divide by 8 ).

It will then ask for your password.  In order to match the strength of the 256 bit key, you will need a truly random password of around 40 ASCII characters (assuming 94 possible characters).  If you don't use a password as strong as the key length, then there is no point in using such a large key since the attacker will merely brute-force your password instead of the key itself.

I wrote a password generator (shameless plug for myself) that I put in my PPA.  It will allow you to create pseudo and "truly" random passwords of up to 63 chars in length (yes, I am aware that computers are finite state machines and cannot do truly random things, but /dev/random does complicate that a bit since it uses human input).  My password generator has a tkinter front-end so you will have a GUI and not need the terminal.  

Anyway, to install my PPA and password generator type the following command:

```
sudo add-apt-repository ppa:rookcifer/pypass && sudo apt-get update && sudo apt-get install pypass
```

To run my program look in:

Applications --> Accessories --> pypass password generator

Create your password, memorize it or write it down and put it in a safety deposit box or something.  Enter the password into mcrypt when it asks for it during encryption.

That's it.  The file should be encrypted to the same directory with a *.nc extension.

For more info about mcrypt or to see a list of ciphers, you can:

```
man mcrypt
```

or 

```
mcrypt --help

```

Good luck.

---

### Post by pepsifx357 on 2010-07-07
> **rookcifer said:**
> After finding a little time to experiment with various encryption options in Ubuntu, I found mcrypt.  It uses the libmcrypt libraries, which have more ciphers to choose from 
of any crypto library I have seen.  If you want Serpent, you need to install mcrypt.

```
sudo apt-get install mcrypt
```

To encrypt a file with serpent, move to the directory of the file, then:

```
mcrypt -a serpent -s 32 -h sha512 -m cbc -r secret_file
```

This will encrypt the file with Serpent-256 using SHA-512 and cbc mode.  The -s flag provides the desired size of the key in **bytes** (not bits, which explains why I used 32.  Take your desired bit length and divide by 8 ).

It will then ask for your password.  In order to match the strength of the 256 bit key, you will need a truly random password of around 40 ASCII characters (assuming 94 possible characters).  If you don't use a password as strong as the key length, then there is no point in using such a large key since the attacker will merely brute-force your password instead of the key itself.

I wrote a password generator (shameless plug for myself) that I put in my PPA.  It will allow you to create pseudo and "truly" random passwords of up to 63 chars in length (yes, I am aware that computers are finite state machines and cannot do truly random things, but /dev/random does complicate that a bit since it uses human input).  My password generator has a tkinter front-end so you will have a GUI and not need the terminal.  

Anyway, to install my PPA and password generator type the following command:

```
sudo add-apt-repository ppa:rookcifer/pypass && sudo apt-get update && sudo apt-get install pypass
```

To run my program look in:

Applications --> Accessories --> pypass password generator

Create your password, memorize it or write it down and put it in a safety deposit box or something.  Enter the password into mcrypt when it asks for it during encryption.

That's it.  The file should be encrypted to the same directory with a *.nc extension.

For more info about mcrypt or to see a list of ciphers, you can:

```
man mcrypt
```

or 

```
mcrypt --help

```

Good luck.


WOW, great post.  I too, found mcrypt but had no idea how to use it.  Using your methods of encrypting the file, what would be the method to decrypt it?

---

### Post by rookcifer on 2010-07-07
> **pepsifx357 said:**
> WOW, great post.  I too, found mcrypt but had no idea how to use it.  Using your methods of encrypting the file, what would be the method to decrypt it?

Easy.

```
mcrypt -d file
```

---

