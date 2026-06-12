---
title: "How do I specify what gpg private key to sign with?"
date: 2012-05-03
forum: Security
---

### Post by nrundy on 2012-05-03
I have two private keys in my keyring (let's call them PrivateKey#1 and PrivateKey#2). I need to sign a friend's public key that I imported. I want to sign the public key with PrivateKey#2. But when using Terminal and inputting

gpg --sign-key 0xFriendsPublicKey

It always tries to sign with PrivateKey#1.

How do I specify that I want to sign with PrivateKey#2?

---

### Post by rookcifer on 2012-05-03
```
gpg --default-key <yourKeyID> --sign-key <YourFriendsKeyID>
```

Also

```
man gpg 
```

is a good resource.  It's long but it should explain anything you need to know.

---

### Post by nrundy on 2012-05-03
> **rookcifer said:**
> ```
gpg --default-key <yourKeyID> --sign-key <YourFriendsKeyID>
```Also

```
man gpg 
```is a good resource.  It's long but it should explain anything you need to know.

Do I HAVE to make it my "default" key? Is there a way to sign a public key by specifiying what key to sign with instead of having to make that key the default-key?

Also. I did look at the man gpg but I find it real hard to navigate. I tried to print it off but couldn't figure out how. I also couldn't figure out how to FIND words. Like in a web browser I can hit CTRL+F to find stuff. Is there something similar in Terminal?

How do I more effectively navigate the pages of output when I use man gpg? like how would I zero in on the sections that talk about signing?

Thanks rookcifer :)

---

### Post by rookcifer on 2012-05-03
> **nrundy said:**
> Do I HAVE to make it my "default" key? Is there a way to sign a public key by specifiying what key to sign with instead of having to make that key the default-key?

Try this:

```
gpg --local-user <YourkeyID> --sign-key <yourFriendID>
```

This acts the same as --default-key but does not change it permanently (if I am reading man gpg correctly).  At any rate, if it does change it, you can change it back with the same command later.

---

### Post by nrundy on 2012-05-03
the --local-user command does nothing far as I can tell. Not sure how to use this one. But using --default-key works AND it doesn't change the previous default-key. Is there a way to change the default key?

Do you have any advice on how to effectivively navigate Man pages?

---

### Post by ottosykora on 2012-05-03
go to:

[http://www.gnupg.org/documentation/manuals.en.html](http://www.gnupg.org/documentation/manuals.en.html)


you will find the manuals there in all sorts of navigable formats.
The man pages are sometimes difficult to use, but one could open them in text editor and then few things might be better.

The default key is set in the gpg.conf which can be found in yout home dir.

from man

--default-key *name*
    Use name as the default key to sign with. If this option is not used, the default key is the first key found in the secret keyring. Note that -u or --local-user overrides this option.


that means, just add a line (example)
deafult-key DEADBEEF

and from then on this is the default key

---

### Post by nrundy on 2012-05-04
> **ottosykora said:**
> go to:

[http://www.gnupg.org/documentation/manuals.en.html](http://www.gnupg.org/documentation/manuals.en.html)


you will find the manuals there in all sorts of navigable formats.
The man pages are sometimes difficult to use, but one could open them in text editor and then few things might be better.

The default key is set in the gpg.conf which can be found in yout home dir.

from man

--default-key *name*
    Use name as the default key to sign with. If this option is not used, the default key is the first key found in the secret keyring. Note that -u or --local-user overrides this option.


that means, just add a line (example)
deafult-key DEADBEEF

and from then on this is the default key

Thanks otto. Good stuff.

How do I open Man page in a Text editor? I'm assuming I pipe it over to Gedit? 

man gpg | gedit  (this opened gedit but it was empty)


I'm not following you w/ the --local-user bit. You say "default-key DEADBEEF"  When I run this with my key ID I get this: 

usage: gpg [options] [filename]


Is there a simple command to input that makes a key that is not the first one on the keyring the default? This is what it sounded like to me from reading your "DEADBEEF" line.

---

### Post by ottosykora on 2012-05-05
>I'm not following you w/ the --local-user bit. You say "default-key DEADBEEF" When I run this with my key ID I get this:

usage: gpg [options] [filename]


Is there a simple command to input that makes a key that is not the first one on the keyring the default? This is what it sounded like to me from reading your "DEADBEEF" line.<


you do not have to run it.
You include the line at the end of the text in the gpg.conf file which is in your home under .gnupg

that is all

---

