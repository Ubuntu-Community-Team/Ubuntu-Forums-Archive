---
title: "Why there are no OOorg 2 and MySQL 5?"
date: 2005-11-26
forum: Repositories &amp; Backports
---

### Post by Fipaj on 2005-11-26
Hi!

Packages in Ubuntu repository are not up-to-date...
When can I get MySQL 5 or OOorg 2?

Best regards,
Fipaj

---

### Post by `GooZ´ on 2005-11-26
That's because ubuntu ddoesn't update the seperate programs during its release cycles. you could enable backports (see the backports subforum) for mysql, and OOo you can get by adding this line to your /etc/apt/sources.list:
#OpenOffice 2.0 final, not beta like ubuntu repos
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

---

### Post by Fipaj on 2005-11-26
Thanks for answer...

I don't add your source, I don't really need this packages... I will wait for new release...

But I think that software update in one Ubuntu release will be good :)

---

### Post by dudus on 2005-11-27
I fund that the best way to have mysql5 i to compile it from source. You could follow my how to here

[http://www.ubuntuforums.org/showthread.php?t=93725](http://www.ubuntuforums.org/showthread.php?t=93725)

---

### Post by Teo on 2005-11-29
[QUOTE=`GooZ´]That's because ubuntu ddoesn't update the seperate programs during its release cycles.[/QUOTE]
This mean no Firefox 1.5 in official Breezy repos? :confused:

---

### Post by lcg on 2005-11-29
[QUOTE=Teo]This mean no Firefox 1.5 in official Breezy repos? :confused:[/QUOTE]
Most probably not, perhaps in the backports once it is released and reaches Dapper Drake. You will have to wait for the 6.04 release. BTW, most people consider it "A good thing"(TM) that the software in one release is tested and stable and not updated immediately with an upstream release.
If you want to have the latest bleeding edge software, go with Gentoo ~arch, Debian unstable or FreeBSD current. You might, however, experience the occasional breakage and instability this way.

Lars

---

### Post by dudus on 2005-11-29
I found that ubuntu isn't realy fast packaging new verssions. Almost every program I had issues I could resolving compiling new verssions.

I should learn how to package things so I could manage them more easyly

---

### Post by Teo on 2005-11-29
[QUOTE=lcg]Most probably not, perhaps in the backports once it is released and reaches Dapper Drake. You will have to wait for the 6.04 release. BTW, most people consider it "A good thing"(TM) that the software in one release is tested and stable and not updated immediately with an upstream release.[/QUOTE]
I realize that Canonical's software revision control approach is really good thing for Ubuntu Support Theme, I understand that FF1.5 won't be aval via official Ubuntu repos, but in Breezy repos is still **bugy** OOo2 **beta** :/.

[QUOTE=lcg]If you want to have the latest bleeding edge software, go with Gentoo ~arch, Debian unstable or FreeBSD current.[/QUOTE]
Gentoo? No way. Compiling my OS from source code? I'm not a programmer, I'm an end user ;).
Debian... Well, I prefer Ubuntu's community :).

---

### Post by lcg on 2005-11-29
> **Teo]I realize that Canonical's software revision control approach is really good thing for Ubuntu Support Theme, I understand that FF1.5 won't be aval via official Ubuntu repos, but in Breezy repos is still **bugy** OOo2 **beta** :/.[/QUOTE]
Agreed. That should be updated. Or they shouldn't have shipped a beta version as default in the first place, but it's a moot point arguing about that now. Anyway, I don't think it will be updated before 6.04 except maybe via backports.

[QUOTE=Teo]Gentoo? No way. Compiling my OS from source code? I'm not a programmer, I'm an end user  said:**
> 
But Gentoo is pretty bleeding edge. If you rely on others to compile and package software for you, I'm afraid you will have to live with a certain time cycle for releases.

[QUOTE=Teo]Debian... Well, I prefer Ubuntu's community :).
Well, AFAIK, the reputation of the Debian community is not the best. I don't know how well earned it is, though. ;)

Lars

---

### Post by dudus on 2005-11-30
[QUOTE=lcg]
Well, AFAIK, the reputation of the Debian community is not the best. I don't know how well earned it is, though. ;)[/QUOTE]

In the time I used Debian I never had issues with the community. There are many maillists and the bugs are all reported very clearly.

[this thread]("http://ubuntuforums.org/showthread.php?t=96595") says it's gonna take a while until firefox 1.5 hits the repos. But they'll do their best to make it official and not just in the backports.

---

### Post by Teo on 2005-11-30
[QUOTE=dudus][this thread]("http://ubuntuforums.org/showthread.php?t=96595") says it's gonna take a while until firefox 1.5 hits the repos. But they'll do their best to make it official and not just in the backports.[/QUOTE]
They don't have to rush. I think ther's some bug in FF1.5 Final:
When turning off autoscrolling (middle mouse button) FF is trying to open [www..com](www..com) page, sometimes goes to "Home page". Strange :|.

---

### Post by dudus on 2005-12-01
[QUOTE=Teo]They don't have to rush. I think ther's some bug in FF1.5 Final:
When turning off autoscrolling (middle mouse button) FF is trying to open [www..com](www..com) page, sometimes goes to "Home page". Strange :|.[/QUOTE]

It's a very hard package to update as a lot of other packages depends on firefox and gecko. A bad upgrade could lead to a total buggy system

---

### Post by wzzrd on 2005-12-02
You could always just download a binary tarball from mozilla.com and install it in ~/local or something. Upgrading too soon the 'official' way will break liferea (at least) and probably a lot more programs. But still, I'm off compiling it on my gentoo install anyway :)

---

### Post by jdong on 2005-12-03
[QUOTE=Teo] but in Breezy repos is still **bugy** OOo2 **beta** :/.
[/quote]
Not entirely true. MANY patches that are a part of 2.0 final have already been merged in Breezy's. To entirely rebase to 2.0 final might have actually made the package more unstable.

If there are specific bugs that you find, file a bugreport and you may get breezy-updates for it :)

> 

Gentoo? No way. Compiling my OS from source code? I'm not a programmer, I'm an end user ;).
Debian... Well, I prefer Ubuntu's community :).

The instability associated with Gentoo and Debian Sid is often due to the in-place version updates.... Backports provides a certain level of these updates that are SAFE.... There is good reason for what Ubuntu does.

---

