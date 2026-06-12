---
title: "apt instead of apt-get"
date: 2015-12-15
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-12-15
I get that *apt* commands may be briefer or less confusing and that there's a progress bar but is there any substantial reason to prefer *apt* to *apt-get*?

---

### Post by Bucky Ball on 2015-12-15
I hope not! Anything that cuts down typing is good by me. ;)

Curious to find out. Never heard you could use it without '-get'. Just tried an update and worked fine. Or seemed to.

---

### Post by vasa1 on 2015-12-15
> **Bucky Ball said:**
> I hope not! Anything that cuts down typing is good by me. ;)

Curious to find out. Never heard you could use it without '-get'. Just tried an update and worked fine. Or seemed to.
Well, I guess many users have made aliases to reduce typing :)

```
alias acde='apt-cache depends'
alias acpo='apt-cache policy'
alias acrd='apt-cache rdepends'
alias acse='apt-cache search'
alias acsh='apt-cache show'
```So that's something up to each user.

Here's a link from a while ago: [http://mvogt.wordpress.com/2014/04/04/apt-1-0/](http://mvogt.wordpress.com/2014/04/04/apt-1-0/)

Edit: the *apt* alternative was introduced in 14.04. So users of 12.04 won't see it.

---

### Post by howefield on 2015-12-15
Perhaps a few "extra" commands, like ...

```
sudo apt edit-sources
```

---

### Post by ian-weisser on 2015-12-15
Nice rundown of the changes at [http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/](http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/)

It will take me a while to adapt. I am thoroughly conditioned to reach for dpkg and apt-get.

---

### Post by slickymaster on 2015-12-15
> **ian-weisser said:**
> Nice rundown of the changes at [http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/](http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/)

It will take me a while to adapt. I an thoroughly conditioned to reach for dpkg and apt-get

Thanks for the link ian-weisser

---

### Post by PaulW2U on 2015-12-15
> **vasa1 said:**
> Here's a link from a while ago: [http://mvogt.wordpress.com/2014/04/04/apt-1-0/](http://mvogt.wordpress.com/2014/04/04/apt-1-0/)
I think I saw that and thought "Nothing here for me". :(
> **ian-weisser said:**
> It will take me a while to adapt. I an thoroughly conditioned to reach for dpkg and apt-get
Me too. :)

---

### Post by sudodus on 2015-12-15
> **slickymaster said:**
> Thanks for the link ian-weisser

+1

---

### Post by Bucky Ball on 2015-12-15
Cheers all. Thanks for the info.

---

### Post by Bucky Ball on 2015-12-15
> **vasa1 said:**
> Well, I guess many users have made aliases to reduce typing :)

```
alias acde='apt-cache depends'
alias acpo='apt-cache policy'
alias acrd='apt-cache rdepends'
alias acse='apt-cache search'
alias acsh='apt-cache show'
```So that's something up to each user.

Excellent. Bit of a dunce when it comes to coding terminal things (as I don't put the time into it) but I can get my head around that. Cool, thanks for that.

Useful info here. :)

---

### Post by QDR06VV9 on 2015-12-15
Nice! Thanks To All..
Cheers:D

---

### Post by SantaFe on 2015-12-15
Neat!  Here's hoping Ubuntu will follow Mints lead & add the extra apt commands as well.  I'd like to use apt autoremove. ;)

But come to think of it:
```

alias DUpdate='sudo apt update && sudo apt upgrade && sudo apt dist-upgrade'
alias Update='sudo apt update && sudo apt upgrade'
alias Clean='sudo apt-get autoremove && sudo apt-get autoclean'
alias Beta='cd mozilla-beta && make -f client.mk build && cd DragonFox-release && make package && shutdown -r now'
alias Release='cd mozilla-release && make -f client.mk build && cd DragonFox-release && make package&& shutdown -r now'

```
Clean IS shorter than get autoremove. ;)

Funny thing about Aliases, if you are editing the .bash_aliases file around midnight and accidentally add the && shutdown -r now command on the right side of the ending ' mark, hilarity ensues with an endless  reboot after login. :D

---

### Post by ian-weisser on 2015-12-15
> **SantaFe said:**
> Neat!  Here's hoping Ubuntu will follow Mints lead & add the extra apt commands as well.  I'd like to use apt autoremove.

I believe Mint didn't add on to apt, but that Mint simply happened to use a newer version at the time of writing.
Xenial uses the newer version (1.1), too.

---

### Post by mikodo on 2015-12-15
Cool.

"Dispersed Documentation Hell" Boy that's true. When I was dual-booting Xubuntu and Debian Stable, I was following aptitude which was the supposed way for Debian at the time. It got confusing with Ubuntu apt-get documentation as the commands may look the same but have different consequences.

apt update worked. so did apt dist-upgrade on 14.04.

I'll check the updated version in 16.04.

Thanks.

---

