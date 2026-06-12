---
title: "Using Fcrackzip?"
date: 2011-10-31
forum: Security
---

### Post by mr-woof on 2011-10-31
Evening all,

not really sure what section to put this, I'm posting at this is along the lines of security. So here goes, I've been looking at my backup plan and I'm thinking that I could incorporate into it some sort of online "Cloud" backup of my main important files etc.

Now ideally, I would like to zip them up, password them and send them off. Today, I've been reading about Fcrackzip and it's uses. Somehow I was under the impression that a compressed file with a password was very difficult to break, but reading about Fcrackzip, it's giving me the impression that it's not true.

Has anyone used this program before? I've been playing with it this afternoon in a vm and I couldn't get it to work properly. I had a zipped file with a password of 123456789 on it, I ran the following command:

fcrackzip -u -b -c aA1! test1.zip 

It kept saying it found a password, but not the right one. 

What are peoples thoughts about zip file security? Anyone had any good experiences with this program?

---

### Post by Dave_L on 2011-10-31
Rather than relying on zip's encryption, I would prefer to create a tarball (.tar.gz) and encrypt it with [gpg](http://manpages.ubuntu.com/manpages/lucid/man1/gpg.1.html), using a strong cipher such as AES256, and a strong password (16-32 characters, mixed uppercase/lowercase/numeric/symbols).

Or an alternative to gpg is a [Truecrypt](http://www.truecrypt.org/) container. That has the advantage that once mounted, you can drag files into or out of it with the file manager. The container, being an ordinary file, can be copied  online or to an external device.

---

### Post by mr-woof on 2011-11-01
I like the idea of using a truecrypt container, I would imagine that would be tough to crack?

I've just tried to install truecrpyt on 10.04 in a vm, to have a play about with it. I've downloaded the tar from the website and archive manager won't open it, I can't see any links to any deb files on their website. 

Anyone having this problem, or is this me just being thick? :)

---

### Post by Dave_L on 2011-11-02
Based on what I've read, a Truecrypt container is a very secure method for protecting data, provided that you use a strong password. The Truecrypt documentation includes some good tips on security.

But some people distrust Truecrypt because of the developers' lack of transparency.

These are my notes on installing Truecrypt on 10.04:

> Installed truecrypt 7.0a by downloading truecrypt-7.0a-linux-x86.tar.gz from <http://truecrypt.org>, extracting its contents truecrypt-7.0a-setup-x86, and running the command:
$ sudo sh ./truecrypt-7.0a-setup-x86

To run truecrypt:
$ truecrypt

To uninstall truecrypt:
$ sudo /usr/bin/truecrypt-uninstall.sh

When I double-click on the .tar.gz in Nautilus, the archive manager (File Roller 2.30.1.1) opens it without any problem. But you could also extract the contents with this command:
```
$ tar -xvf truecrypt-7.0a-linux-x86.tar.gz
```

---

### Post by mr-woof on 2011-11-02
Strange, I've downloaded it again and I still get the same error. 

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors

Wacky, I'll try it on my home pc tonight when I get home

---

