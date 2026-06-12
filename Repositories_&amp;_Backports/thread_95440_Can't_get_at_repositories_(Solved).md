---
title: "Can't get at repositories (Solved)"
date: 2005-11-26
forum: Repositories &amp; Backports
---

### Post by cy218 on 2005-11-26
Ok -so this is my first post, so please forgive any glaring errors and omissions.

Just to start, I got my laptop from ebay with no disks so I'm reliant on the repositories for any software -fortunately I've managed (thanks to WiKis and countless others' posts) to get an ethernet and intermittent WiFi connection to the internet via my router at work. (Although looking at some posts, the router could be part of the problem!)

I've been trying for days on end to update my repositories. I get numerous error reports both with Synaptic and apt-get. I'm really new to all this and pretty overwhelmed by all the information out there.

I've used the source-o-matic to get my source.list straight (I also used others' suggestions) but I suspect things are going wrong before then.

When I open synaptic I get:
```

W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```
If I try *sudo apt-get update* I get:
```

W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```
Any ideas?

This is starting to take over! But I'm enjoying the challenge.

Thanks in advance, it's good to be here

Cy

---

### Post by aysiu on 2005-11-26
See the first link in my sig.

---

### Post by cy218 on 2005-11-26
Thanks aysiu -but no dice

I've read your useful stuff and tried it before but I've just given it another go because I was getting pretty messed up! I even tried the [I]sudo apt-get update[I] with a blank sources.list just to clear everything out.

I'm wondering if the problem is with the ip address through my works router. Some of the posts suggested that but I started getting lost. The error output ip address (is it an ip address?) looks odd:

Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 **_(1.0.0.0)_**, connection timed out

Any other ouput required to clarify things?

Unfortunately I have no other working internet connection to compare with.

Thanks for the quick response.

---

### Post by aysiu on 2005-11-26
[QUOTE=cy218]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 **_(1.0.0.0)_**, connection timed out[/QUOTE] I read about this in some other threads. Something about firewalls or proxy servers. I don't know the solution, but it's not a repositories problem.

---

### Post by cy218 on 2005-11-26
Hmm, didn't think it was.

Unfortunately I'm that much of a newbie I don't even know if I'm connected via a proxy server -does going through a router on a network mean I'm using proxy.

I'm not even sure in which forum to ask the questions.  People are talking about various ip or DNS & I don't even know where to find them or what they mean!

It all seems a bit odd because firefox works fine.

I do know I'm connected with dhcp in "Networking".

Oh, I don't seem to have a etc/apt/apt.conf file, if that makes any difference.

Help! Man pages just fry my head...

---

### Post by cy218 on 2005-11-29
Good news!

Synaptic now works, without having to upgrade router firmware or complicated scripts.

This is how it worked for me:

1.[http://http://ubuntuforums.org/showthread.php?t=95350&highlight=router+synaptic]("http://ubuntuforums.org/showthread.php?t=95350&highlight=router+synaptic") thanks to mips' post #11

2.[http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router]("http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router") thanks to python's post #2

3.I got my nameserver DNS from [http://www.bryork.freeuk.com/text/dns.txt]("http://www.bryork.freeuk.com/text/dns.txt")

4.Made sure my *sources.list* was ok according to aysiu's excellent howto [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

I'm no expert at all. Just kept trawling around and trying stuff out (!) I'm not even sure what half of it means -hey ho.

Now I've got that out from under my skin, I can reconnect with the outside world for a bit before I start fretting about upgrading to Breezy!

---

