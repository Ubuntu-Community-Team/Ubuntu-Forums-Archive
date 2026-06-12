---
title: "Password Generator"
date: 2009-07-29
forum: Security
---

### Post by argos3016 on 2009-07-29
Hey , anybody knows about an a password generator? I want one to put in the Hydra and test my FTP server, ( no for malicious plans!!) , that put the calculated passwords in a text file. 
Thanks.

---

### Post by r+9 on 2009-07-29
I'm not sure what you're asking for but...

If you just want to make good random-passwords it doesn't take much to write a program to do that, I got sick of having to invent all the passwords with 2 of each type of character and so many characters so I create random ones.

The other thing I'm thinking you're trying to do is test your existing passwords for strength with some sort password-guesser.  That would be more fun to put together, but realistically you'd want to research the popular methods for cracking so that you're "practicing like you play".

That's how I'd approach it.

---

### Post by argos3016 on 2009-07-29
Thanks , I will make an script!:)(is minus dangerous)?

---

### Post by Jatchie on 2009-12-23
sudo apt-get install pwgen

---

### Post by rookcifer on 2009-12-23
You don't need to write a script or install anything.  All you need to do is type one command:

```
echo `< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c6`
```

Change "-c6" to the length of password you want.

There are various other ways to generate passwords on the command line.  For instance, you can use the md5 hash for password generation with the following command:

```
dd if=/dev/urandom count=128 bs=1 2>&1 | md5sum | cut -b-10
```

[Here]("http://foolab.org/node/1436") is a good site that discusses several of these commands.

---

### Post by Jimtheplanner on 2009-12-24
Hi Folks,

I use a neat little tool called revelation. It can hold your password details in an encrypted file. It also has a good random password generator...

Recommended 

Jim

---

### Post by BkkBonanza on 2009-12-24
If you're really trying to test your ftp then you may want to use one of tools that others will use, John the Ripper or Openwall containing it. With Openwall you could start a VirtualBox machine to run tests on your ftp server. Or if you want to do further more extended pen testing then perhaps Backtrack would be better.

---

### Post by Soul-Sing on 2009-12-25
> **Jimtheplanner said:**
> Hi Folks,

I use a neat little tool called revelation. It can hold your password details in an encrypted file. It also has a good random password generator...

Recommended 

Jim

Or KeePassX, which has a great pass generator.

---

### Post by Andrey Jivsov on 2010-02-26
Another idea is to use browser-only password generator, for example, "Calculated Passwords" at [http://calculatedpass.com]("http://calculatedpass.com/"). I would not trust any server with my secrets, yet I want to be able to re-create them.

While you can generate a random password based on /dev/urandom, you now have new issue of backing it up and restoring it. It is not convenient for long-term secrets. 

Calculated Passwords applet works by combining your secret master passphrase with additional [public] portion, which is Seed + Target Domain. You may choose to store public information online, memorize, or write down on a piece of paper. The resulting password can be made as secure as a random one, while the input is easier to remember. The password guessers are thwarted because Calculated Passwords uses iterated KDF, Seed, and Target Domain.

---

### Post by Bachstelze on 2010-02-26
[font=monospace]makepasswd[/font] is another option.

---

### Post by FuturePilot on 2010-02-26
.

---

### Post by Bachstelze on 2010-02-26
> Last edited by FuturePilot; 8 Minutes Ago at 12:21 AM.. Reason: Oops. Didn't see that 

[img]http://farm4.static.flickr.com/3057/2367515373_515ff7a325.jpg[/img]

---

### Post by FuturePilot on 2010-02-26
lol :lol:

---

### Post by SecretCode on 2010-02-27
> **FuturePilot said:**
> .

Your post does not meet minimum complexity rules in place for this system. It should be at least 8 characters long. Please try another post.

---

