---
title: "Remote Access a Windows Computer from Ubunntu, How?"
date: 2010-02-06
forum: Server Platforms
---

### Post by Sugi on 2010-02-06
Can anyone send me a link or a guide to remote access graphical a windows 7 box from ubuntu karmic. So pretty much, I need to setup the ssh server on the windows 7 box and get my ubuntu karmic to view it.

Thanks,
Sugi

---

### Post by noway2 on 2010-02-06
Are you having some specific trouble?  Is there something that you are running into that is different with windows 7?

Normally, for Windows the program putty works pretty well.  I assume it works under Windows 7. It can be a little tricky to get it to work with password-less authentication (rsa key).  Basically to do that, you need to generate the public / private key pair on the Linux box and import it into putty, which expects it in a certain format, rather than generate it on Windows.  There may be an intermediate step in there too so I would consult the wiki pages.

---

### Post by Sugi on 2010-02-06
I am actually following this guide right now.

[http://www.techmalaya.com/2009/08/05/setup-ssh-server-for-windows-freesshd/](http://www.techmalaya.com/2009/08/05/setup-ssh-server-for-windows-freesshd/)

I am stuck at RSA key fingerprint.

When, I enter yes. It ask for a password.  When I input the (password I think is correct), it doesn't go through.  On the openshhd server, I am using the same password as the one I am inputting into the RSA key fingerprint.  Am I doing something wrong on the linux end of this?

Sugi

---

### Post by noway2 on 2010-02-06
This might also be of interest to you: [http://www.freesshd.com/index.php?ctt=forum&action=view&topic=1102011017&p=5](http://www.freesshd.com/index.php?ctt=forum&action=view&topic=1102011017&p=5)

---

### Post by noway2 on 2010-02-06
This one too.  It looks like others have had problems with modern versions, but had success with an older one: [http://www.freesshd.com/index.php?ctt=forum&action=view&topic=1193682263#1193757267](http://www.freesshd.com/index.php?ctt=forum&action=view&topic=1193682263#1193757267)

---

### Post by Sugi on 2010-02-06
Thanks for the link, but I am still getting errors.  New one at least.

warning: remote host identification has changed!

Huh?

Sugi

---

### Post by Sugi on 2010-02-06
I still can't get pass the darn key thing :S

Sugi

---

### Post by noway2 on 2010-02-06
> warning: remote host identification has changed!

That sounds like the certificate for the server has changed.  You may need to "clean things out" and try again.  Were you able to get it working with password only and not rsa key?

---

### Post by Bachstelze on 2010-02-06
@Sugi: don't bother with SSH on Windows, it's a royal pain. Just use the built-in Windows remode desktop thing, and install the rdesktop client.

---

### Post by Sugi on 2010-02-06
Bachstelze, Ha!  I am finding this out the hard man.  It's causing some much issues.  If I just the default remote control access on the windows front and then use this "rdeskop".  Is it going to as secured?  That's what I am worried about.

Edit:  Ok, So I installed rdesktop, and grdesktop.  If I "rdesktop -f ipaddress", is that all I need?  I can't really test anything else, because my friend is still asleep. XD  There's also a lot of settings if I click "Down" on grdesktop, there's a lot of options in there. :S

Thanks,
Sugi

---

