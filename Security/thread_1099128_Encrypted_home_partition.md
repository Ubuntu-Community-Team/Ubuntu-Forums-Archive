---
title: "Encrypted /home partition"
date: 2009-03-17
forum: Security
---

### Post by kaledev on 2009-03-17
I am completely new to Linux and come from a Windows background so I am hoping someone will have some insight. I normally have full disk encryption with truecrypt at all times on my system disk but I decrypted to attempt a dual boot of Ubuntu/Vista. Well after 8 hours of hair pulling mission complete.

I am about to encrypt the full disk again, however I placed my /home partition on a secondary hard drive so that I would have room if I ever wanted to extend it. But I would also like to have the /home partition encrypted. If I encrypt /home will I be able to login to Ubuntu as normal, run truecrypt, mount, and decrypt home? Or does Ubuntu rely on /home to be able to boot/login/function? Excuse me if it is a stupid question, I know just about zero when it comes to Linux :D

---

### Post by bodhi.zazen on 2009-03-18
to be honest you are probably best off either :

1. using the new feature to encrypt /home at installation. 

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

2. Using the alternate CD and encrypting your entire system.

or

3. Rather then encrypting home with truecrypt, encrypt a shared data partition . You can then access it from windows or ubuntu.

---

### Post by dusan.saiko on 2009-03-18
I was following this howto, which was perfectly working for me

[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu)

---

### Post by mrsteveman1 on 2009-03-18
> **bodhi.zazen said:**
> 

1. using the new feature to encrypt /home at installation. 

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)



That URL describes an encrypted private directory, not all of /home or even your user home dir itself. They should really do that though, like FileVault on OS X.

---

### Post by bodhi.zazen on 2009-03-18
> **dusan.saiko said:**
> I was following this howto, which was perfectly working for me

[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu)

WOW, that is the hard way.

I suggest you use the alternate CD:

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

> **mrsteveman1 said:**
> That URL describes an encrypted private directory, not all of /home or even your user home dir itself. They should really do that though, like FileVault on OS X.

no, I think you misunderstand.

When you select this option it encrypts your home directory (/home/user/name) but not all of /home.

This makes sense if you have multiple users (each user can encrypt his or her /home/user_name).

---

### Post by kaledev on 2009-03-18
Since it's already installed I would rather not try to install another version. I don't mind setting up a shared drive, but does /home contain anything by default that I should be worried about not being encrypted? Or are things put automatically into /home over time that are sensitive? I was told that /home is similar to my documents in windows, which I never use anyway because I have a seperate drive for all my files. If it doesn't truely matter I can just leave it unencrypted and set up a shared partition that is.

---

### Post by bodhi.zazen on 2009-03-18
/home contains both data and config files.

There really is nothing in the config files that *needs* encryption, with the possible exception of .bashrc and similar user modified config files.

So in your case, as I suggested, just use an encrypted (data) partition.

---

### Post by Soul-Sing on 2009-09-09
> **kaledev said:**
> Since it's already installed I would rather not try to install another version. I don't mind setting up a shared drive, but does /home contain anything by default that I should be worried about not being encrypted? Or are things put automatically into /home over time that are sensitive? I was told that /home is similar to my documents in windows, which I never use anyway because I have a seperate drive for all my files. If it doesn't truely matter I can just leave it unencrypted and set up a shared partition that is.

Example?: .xchat2 in your /home. It shows (with autologin enabled
) your password for xchat in the serverlist_.conf. That pass could be sensitive...

---

