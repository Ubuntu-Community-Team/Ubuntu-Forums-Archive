---
title: "ssh into a chroot environment"
date: 2009-07-04
forum: Server Platforms
---

### Post by dr johnson on 2009-07-04
Would anybody please be kind enough to help me tightening up the list of commands on _[COLOR="Red"][this]("http://jonathanriley.net/jailkit.html")[/COLOR]_ web page. It was written by me, but i'm certainly no security expert. Please feel free to comment or copy and paste from the page :-)

---

### Post by windependence on 2009-07-04
I don't understand what you're trying to point out here. You can always ssh in to the main machine. The idea is to chroot the part of your machine you want inaccessible like your apache setup. Give me an idea of what concept you are trying to teach here and I can help you.

-Tim

---

### Post by dr johnson on 2009-07-04
hello windependence, and Thank You for your reply :p

the idea was to give third parties restricted ssh access to my machine so that they are able to do the stuff i want them to be able to do, but not more. In particular, i don't want third parties getting up to any mischief.

it seems to me that maybe you think ssh is too powerful a tool for the purpose. My machine should be safe if third parties have ssh access only to the chrooted environment though, should it not? Unfortunately, i don't have anything very specific in mind just yet, i'm just exploring possibilities.

btw, teaching is not really my thing; i'm definitely not qualified for that! I have altered to the page to reflect the fact, so thanks for the pointer.

---

### Post by windependence on 2009-07-05
OK, I get it now. You don't want to CHROOT the root directory (/) but EACH of their user directories and then give the user access to each of their home directories. Let me dig up some info for ya on this and post it.

-Tim

---

### Post by HermanAB on 2009-07-05
The newest versions of SSH has chroot capability built in.  Go to the snail web site and read up a bit:
[http://www.openssh.com/](http://www.openssh.com/)
[http://www.snailbook.com/](http://www.snailbook.com/)

---

