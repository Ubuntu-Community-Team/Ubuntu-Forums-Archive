---
title: "TrueCrypt - Dangerous License ?"
date: 2011-04-04
forum: Security
---

### Post by mathgeek2000 on 2011-04-04
For a few applications, involving security, I've found cross platform tools very handy. -- As I find Windows to be useful, for a few applications. -- Thus for example Lastpass, & Password Gorilla come in handy. TrueCrypt is another one of those apps, as I can take a TrueCrypt Encrypted Portable HDD and mount it on either my Windows Desktop or Linux Laptop.

As a simple user, who sometimes just wants 'things to work' - I read : (on Fedora's Site) And Worry..

> The TrueCrypt software is under a poor license, which is not only  non-free, but has the potential to be actively dangerous to end users...

I reviewed the license, and can understand how it's considered non-free, not Open Source, in a FSF/ Open Source Initiative sense, and can understand TrueCrypt's reasoning. But what I don't understand is how is it 'Actively Dangerous to End Users'?

I get the software from TrueCrypt, I use it to encrypt sensitive files, etc. Exactly what is the problem? By contrast :
  PeaZip - Free / Open Source?
  WinZip - Commercial/Proprietary
  PowerArchiver - Commercial/Proprietary

Can all produce and read each others AES256 Encrypted Zip files. So if you had a complete aversion to any Commercial/Proprietary software, you could use PeaZip. But that doesn't make WinZip, or PowerArchiver 'Actively Dangerous' any more than Windows 7, or MS Office.

So what's the deal?

---

### Post by bodhi.zazen on 2011-04-04
I would imagine the "dangerous" part is referring to the lack of openess to the source code, but you should as the author of the information for clairfication as we would be speculating.

If truecrypt works for you, no reason to change.

If you wish, however, there are open source options for encryption.

One would be FreeOTFE

[http://www.freeotfe.org/](http://www.freeotfe.org/)

gpg would be another (for single files), or use zip and then encrypt it with gpg. ;)

---

### Post by mathgeek2000 on 2011-04-04
> **bodhi.zazen said:**
> I would imagine the "dangerous" part is referring to the lack of openness to the source code, but you should as the author of the information for clarification as we would be speculating.

If truecrypt works for you, no reason to change.

TrueCrypt does release the source code to their software, but not with a license that meets the Open Source Initiative's rules. And as you've commented - TrueCrypt works for me. While researching the Fedora distribution I came across their comments about Truecrypt on their 'Forbidden Software' list, but while the TrueCrypt License is apparently too restrictive for Open Source / Free Software developers, I'm not clear on how it's 'dangerous' to end users, any more than any other software limits it's liabilities. Yes their may be unique issues:

  - Anonymous developers, of the product for one.
  - Encryption methods may not be allowed in all countries.

But Fedora's caution made it sound like one could be unwittingly breaking the law by using the application, without giving any concrete examples.

---

### Post by SeijiSensei on 2011-04-04
> **mathgeek2000 said:**
> But Fedora's caution made it sound like one could be unwittingly breaking the law by using the application, without giving any concrete examples.

The best recent summary I could find was this:
[http://rechten.uvt.nl/koops/cryptolaw/cls2.htm](http://rechten.uvt.nl/koops/cryptolaw/cls2.htm).

Some countries, like Iran and Russia, apparently require a government license to use cryptography.  Other countries enforce "key escrow" laws that essentially require you to give up the key to a government agency upon demand.

RSA's products carry a generalized disclaimer that "many countries prohibit or restrict the use, import, or export of encryption technologies" without naming names.

---

### Post by rookcifer on 2011-04-05
> **mathgeek2000 said:**
> As a simple user, who sometimes just wants 'things to work' - I read : (on Fedora's Site) And Worry..

I reviewed the license, and can understand how it's considered non-free, not Open Source, in a FSF/ Open Source Initiative sense, and can understand TrueCrypt's reasoning. But what I don't understand is how is it 'Actively Dangerous to End Users'?

I use Truecrypt and like it.  However, I do have a few issues with the development process:

1) The authors are anonymous

2) The changelogs posted with each new version are very generic and contain zero details.  For instance, in the 7.0a changelog we see this stunning revelation: "Other minor improvements  (Windows, Mac OS X, and Linux)."  Very detailed indeed. :confused:

3) The authors wont accept patches from anyone.

4) The authors keep all bug reports secret.

5) They use no revision control system like Git, SVN, Mercurial, etc., which makes it exceedingly difficult to find out exactly what has been changed.

That said, there's no reason for me to believe there's anything technically wrong with TC.  There have been a few reputable people help write some of the encryption routines (optimized assembly routines for AES, etc.) which means the project has some merit.  It does have a few detractors as well, but no one, to my knowledge, has specifically pointed out any flaws with the code.  Sure, some people may not like the coding style, but everyone has their own opinions on things like that.

---

