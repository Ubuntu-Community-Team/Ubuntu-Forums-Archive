---
title: "Your Distro is Insecure: Ubuntu"
date: 2009-04-14
forum: The Cafe
---

### Post by sulekha on 2009-04-14
Hi all,

see this :- [http://www.linux-mag.com/id/7297/1/]("http://www.linux-mag.com/id/7297/1/")

---

### Post by Mehall on 2009-04-14
I facepalm'd when I saw the title.

And I facepalm'd reading the article.

yes, yes, there were actual security concerns there, but most of them being "If someone cracks into your system, you're vulnerable"

That's right up on the list with "if someones heart stops working he's gonna DIE if he;s nowhere near a hospital!"

If your system is insecure, which is largely easy to avoid, then no amount of file permissions is going to stop anything from happening.

Granted, the other issue is a bit more serious but still.

---

### Post by original_jamingrit on 2009-04-14
I guess it should be mentioned that this article seems to be targeted at Server installs, rather than desktop installs.

This article talks about system hardening, cutting excess services, and encrypting everything on the home directory.  This stuff, I think, should be obvious to anyone running a server that *needs* security.

If you're running a webserver that stores a bunch of cat pictures, on the other hand, how secure you want it is your own call.

---

### Post by bp1509 on 2009-04-14
d

---

### Post by wolfen69 on 2009-04-14
> **bp1509 said:**
> everyone should read (and partially memorize) the following:

[http://www.nsa.gov/ia/_files/os/redhat/rhel5-guide-i731.pdf](http://www.nsa.gov/ia/_files/os/redhat/rhel5-guide-i731.pdf)

It can apply to any distro.

you can take off your tinfoil hat now. :rolleyes:

---

### Post by Dragonbite on 2009-04-14
It's actually not bad of an article, but doesn't do anything to help alleviate any of the issues.

Servers are opposite desktops. 

You want the desktop to just work and it doesn't matter as much if extra things had to be set up so when you click your IM it goes out an open port instead of screaming at you to open-the-door!

Servers should be locked down to a secure platform so the people that make it less secure are the people that have an idea WHY they are making it less secure (and that they ARE making it less secure).

My server is behind a 2 firewalls (one built-in the router, the other a firewall/router/content filter system in an old CPU) so I may have a little more room to play safely.

---

### Post by cb951303 on 2009-04-14
[http://blog.init.hr/?p=41](http://blog.init.hr/?p=41)

---

### Post by jumpstreet on 2009-04-14
Ronald McCarty sounds a little inexperienced

---

### Post by HammerOfDoubt on 2009-04-14
> **wolfen69 said:**
> you can take off your tinfoil hat now. :rolleyes:

Did you read the link or did you automatically assume "any government link = LOL CONSPIRACY NUT"?

I think it's a good thing to look at things and then judge them.

---

### Post by SomeGuyDude on 2009-04-14
If you are irresponsible with your computer, you will suffer the consequences. There's no news there. I didn't get any viruses on my Windows machine despite not having an antivirus for a year, because I'm not an idiot who just opens everything willy-nilly.

---

### Post by gnomeuser on 2009-04-14
I remember arguing my face blue with the Ubuntu developers to have security be taken seriously since the very first release. Slowly they started to avail themselves of things like propolice over the years.

I am still frightened by AppArmor, trusting my security to a large system that hasn't yet gotten accepted upstream meaning it's a huge patch. This seems like an epic miscalculation akin to that of distros who desperately wanted to offer virtualization and thus patched their kernels with Xen thinking it would go upstream any minute. They have been forced to invest countless manhours on this folly, it has for years and will continue for quite some time yet.

---

### Post by Seq on 2009-04-14
If you make your home directory not world readable, then many daemons will have issues reading data within.

[LIST]
[*]Apache won't be able to access ~/public_html
[*]Mail might not be delivered to ~/Mail, if you have mail configured to deliver to the user's home.
[/LIST]

There are probably many, many more. That is probably a decent reason for why 755 is the default mode for home directories.

Granted, encrypted home directories I think are targetted more at laptops than servers I thought. You lose all of the above capabilities right off the start with an encrypted homedir...

EDIT: I'm only commenting on the readable/encrypted homedir issue. The system accounts having shell access and such should be fixed, though.

---

### Post by bp1509 on 2009-04-14
d

---

### Post by gnomeuser on 2009-04-14
> **Seq said:**
> If you make your home directory not world readable, then many daemons will have issues reading data within.

[LIST]
[*]Apache won't be able to access ~/public_html
[*]Mail might not be delivered to ~/Mail, if you have mail configured to deliver to the user's home.
[/LIST]

There are probably many, many more. That is probably a decent reason for why 755 is the default mode for home directories.

Granted, encrypted home directories I think are targetted more at laptops than servers I thought. You lose all of the above capabilities right off the start with an encrypted homedir...

EDIT: I'm only commenting on the readable/encrypted homedir issue. The system accounts having shell access and such should be fixed, though.

If the encrypted homedirs are more targetted towards laptops the problem of the content being root readable would be even worse than useless since it would directly give a false impression of security. I am not up on the latest for encryptfs though I don't know if this has been addressed and I would love some more insight.

My own laptop runs dm-crypt as well as a fully encrypted homedir using encryptfs as provided by the alternative installer image. The overhead cost is low and the desktop remains fully usable. I am quite pleased with my belts and suspenders approach.

---

### Post by Daisuke_Aramaki on 2009-04-14
Looks like the Original Poster's threads follow a similar pattern of late.

[http://ubuntuforums.org/search.php?searchid=57987381]("http://ubuntuforums.org/search.php?searchid=57987381")

---

### Post by john_spiral on 2009-04-14
How different is a Debian server install from Ubuntu 8.1 server? Do they also have the same security pitfalls?

---

