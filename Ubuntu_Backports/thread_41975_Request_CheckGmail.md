---
title: "Request: CheckGmail"
date: 2005-06-15
forum: Ubuntu Backports
---

### Post by jasplund on 2005-06-15
Since mail-notification works with gmail for me i've been looking at som alternatives.
I came across [http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/) which I'd love to see in the backports.


Johan

---

### Post by m0biu5 on 2005-06-15
I'll second that. That looks like what I've been searching for!

---

### Post by McQuaid on 2005-06-15
I just put in a request for mail notification 1.1 which is in breezy.  This looks kind of cool.  Any first hand experience with both? Curious if this is better.  

Btw, I'm not sure if this is still official policy but I believe the backports project only backports existing debs from breezy preferably and in some cases debian sid.  If this package doesn't exist in either I don't think requests like this get filled.  Which is a shame really if all the lib requirements are currently satisfied in hoary.

---

### Post by jasplund on 2005-06-15
[QUOTE=McQuaid]I just put in a request for mail notification 1.1 which is in breezy.  This looks kind of cool.  Any first hand experience with both? Curious if this is better.  

Btw, I'm not sure if this is still official policy but I believe the backports project only backports existing debs from breezy preferably and in some cases debian sid.  If this package doesn't exist in either I don't think requests like this get filled.  Which is a shame really if all the lib requirements are currently satisfied in hoary.[/QUOTE]

I don't think mail-notification 1.1 works any better with gmail than 1.0 does

---

### Post by jasplund on 2005-06-16
Has anyone seen a deb of CheckGmail? or has anyone tried it?

---

### Post by jasplund on 2005-06-20
Is there really no way we can get this backported? Or any other gmail notifier for that matter

---

### Post by foxy123 on 2005-06-20
just for your info, there is a good FIrefox extension for it: GMail Notifier, I used in in WinXP, though have never tried in Linux...

[http://nexgenmedia.net/extensions/#gm-notifier](http://nexgenmedia.net/extensions/#gm-notifier)

---

### Post by jasplund on 2005-06-20
Yes I know, thanks for the info though. However i don't really see the need for a notifier if I need to have firefox open to use it.

---

### Post by foxy123 on 2005-06-20
I guess you're right. I just have FF always opened. :)

---

### Post by jasplund on 2005-07-11
There's a new version out for checkgmail now. Maybe someone could backport it to extra? [http://checkgmail.sourceforge.net](http://checkgmail.sourceforge.net)

---

### Post by dcraven on 2005-07-11
It's just a single file script in the tarball. Just drop it into ~/bin or something and it's installed. The problem is this:

```

dcraven@sigma:~/Sandbox/src/checkgmail-1.1.2 $ ./checkgmail
CheckGmail v1.1.2
Copyright \uffff 2005 Owen Marshall

Hmmmm ... Crypt::Simple doesn't seem to be working!
Not using Debian or Ubuntu, are you??

Your best bet is to download the Crypt::Simple module from CPAN
(http://search.cpan.org/~kasei/Crypt-Simple/) and install it manually.  Sorry!

```

Cute.. haha :D. This is in breezy though and I can't even read man pages here. It might work fine in Hoary. Give it a shot!

~djc

---

### Post by bhound89 on 2005-07-23
Ive been able to run version 1.3 of CheckGmail, but I can't save the password because I can't figure out how to install Crypt::Simple.

---

### Post by plutoprime on 2005-07-23
[QUOTE=bhound89]Ive been able to run version 1.3 of CheckGmail, but I can't save the password because I can't figure out how to install Crypt::Simple.[/QUOTE]
 I'm using the latest checkgmail and it works great. In order to install crypt::simple you have to run a  make , make install after extracting the source file. There is a tar.gz source file on the website you can download. I understand you are having problems because there are absolutely no installation instructions supplied with the source file :)

P.S. I forgot to mention before you can run make there is a "perl" script in the souces directory. You have to run ```
perl scriptname.pl
```    in the terminal before you can do a ```
make && make install
```

---

### Post by anders on 2005-08-10
> I'm using the latest checkgmail and it works great. In order to install crypt::simple you have to run a make , make install after extracting the source file. There is a tar.gz source file on the website you can download.

I can't find it. Has it been removed? Or alternatively, is there any deb package for it somewhere? 

I would really like to be able to use checkgmail because mail-notification doesn't seem to work with gmail accounts (using the gmail account option crashes the program and using POP doesn't work because SSL is disabled in the Ubuntu package).

---

### Post by cutOff on 2005-08-14
[QUOTE=dcraven]It's just a single file script in the tarball. Just drop it into ~/bin or something and it's installed. The problem is this:

```

dcraven@sigma:~/Sandbox/src/checkgmail-1.1.2 $ ./checkgmail
CheckGmail v1.1.2
Copyright \uffff 2005 Owen Marshall

Hmmmm ... Crypt::Simple doesn't seem to be working!
Not using Debian or Ubuntu, are you??

Your best bet is to download the Crypt::Simple module from CPAN
(http://search.cpan.org/~kasei/Crypt-Simple/) and install it manually.  Sorry!

```

Cute.. haha :D. This is in breezy though and I can't even read man pages here. It might work fine in Hoary. Give it a shot!

~djc[/QUOTE]

You need the following packages

libgtk2-perl
libgtk2-trayicon-perl
libwww-perl
libcrypt-ssleay-perl
libxml-simple-perl

> In addition, for the ability to save passwords, you'll need these modules:

        Crypt-Simple
        Crypt-Blowfish
        FreezeThaw
        Compress-Zlib
        Digest-MD5
        MIME-Base64

---

### Post by rune on 2006-03-17
to get rid of the make failure I did:
apt-get install make automake1.9 autoconf
sudo rm -rf .cpan
sudo perl -MCPAN -e 'install Crypt::Simple'

I think that maybe one or more of the packages (make automake1.9 autoconf) aren't required, give it a try and report back.

---

