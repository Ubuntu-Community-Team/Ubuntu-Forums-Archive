---
title: "External Hard drive security"
date: 2010-08-14
forum: Security
---

### Post by WiReIs on 2010-08-14
Hi, i have just recently purchased a SeaGate 1TB External Hardrive.. i have very sensitive information on this storage unit that i only want certain people to have access to.. is there any way of password protecting the hardrive? preferably using linux or what are my options?

Thanks in advance, WiReIs.

---

### Post by CharlesA on 2010-08-14
Encrypt it if it has sensitive data on it.

---

### Post by bodhi.zazen on 2010-08-14
> **CharlesA said:**
> Encrypt it if it has sensitive data on it.

+1

LUKS and Truecrypt are both cross platform (Linux and windows).

---

### Post by jflaker on 2010-08-14
TrueCrypt full disk encryption.  Passwords can be hacked, but encryption can not with current technology.

Truecrypt also allows for encrypted volume containers which are just files on the disk that can be mounted which allows you to keep your music and other non-critical files in plain view.

---

### Post by FuturePilot on 2010-08-14
LUKS. It integrates very nicely with the Gnome desktop.

---

### Post by scorp123 on 2010-08-14
I use LUKS + eCryptFS on top of each other, with different long + complicated passwords.

What happens when I connect the disk to one of my Linux systems is that I first get asked the LUKS password to get the volume mounted. When successfully mounted there is the second barrier: the directories on that volume are eCryptFS-encrypted.

You could of course do something like this:

LUKS for the filesystem, and on the filesystem a TrueCrypt-container, and in that container eCryptFS-encrypted directories.

The likelihood that within the next 10 years exploits and weaknesses will be found in all three encryption-mechanisms is extremely small. So your data should be safe ... for now.

BTW, all these mechanisms are worth nothing if you choose a weak password. So I'd recommend to use a tool such as "pwgen" and generate super-strong passwords. "pwgen" isn't installed by default but you can easily get it via Synaptic or the command line:
```
sudo apt-get update && sudo apt-get install pwgen
```

Let's assume you want a 32-character long password that is very very hard to crack you'd give your system a command such as:
```
pwgen -s 32
```

Result (output reduced):
```
roQDkld5Gnml9hKD0eqfNBPkHQlch3jE 4pELliQPBF7fwwV0L8bthP6bnhMnTjey
I808PF7ocZs4DFfI3G9fmqMgN3WyLEwp KLXhRZD4KDhFJx0WRo5cCX4e4BDRkMnf
sooUmikTSGZXm8ijhLSEC3aterfudjcI fCRhcYTSBUqiKu9fXiCQE7lliScB1OD4
sTQHi0fHWPpW557ZBJlMcAF7040hxFrE LMJ1xcCil8YIADGitpOMe9AobCJPiGlc
sEV4cS9GHl4aLzw5TMG3HnQ0AyXlVsjI E371mo12PICp8zv0iCM6lCJQ29W5RUSw
RkH1koURs9jnWpchJvHE7X7nsY5rG4DB J1ANhEzaL6h63ZDm0sztkHqI2Lg20dAY
7WqPBe2PGbvW67Vt6vxXQVv2jcjJYuKB jb4t1iiPlGnKdp1YpXveo0JApp0cBoKt
noWspX087WeP6LKkiwJxdTOsYDn7xXxT 1qRUnHmUXTQ73T9DKVHbO8t3OqYYWzmb
hjeoADbm7gwKpOMhxQqSDonVgOnVtdWV EyrHKVaaOQrBiFF5edqqHJ1aCjFroHqw
... 
```

Voila, all these passwords are 32 characters long and very very hard to crack in any way.

You can even create weirder passwords by telling "pwgen" to use special characters (*,!,?,[,],+,@,#, ...) too:
```
pwgen -s -y 32
```

New result (output length reduced):
```
@En:_j#^6}1'hx9<iz)]-rk2sNY3^)o0 FS]X.r0ce`1w/A-+MV%gILMj$MA1#gF5
+Q0:npn@^'@hY:6t[F;@CrYWMhy9Ui<O X`~dWDoP=uPK=]p[?mOl/o.*%ol'GK5!
7iLN?[)YVD.EDZn<_F^c6:)|]}Ef&>:O 0bx&[f&`<mYO5_T]BiTtE\<v4rlp8~<|
hvXF|10bEzuIK`^Z/x!hqRWkVBqk0_[Q VvP<)v6j>+35}9@In^EIhEdg~@A`Ax>Z
~^O;AO{.wwBwkZ~ATd">D:8t?=ajS_r^ Ha>_TXHALd.$}Q_R[kih.NQf"]N7!mP{
]Ukg45~Uvh5oyj@&9|M5j!XDQvggn6~V S8tlw!.iS|rvZe/_r}c/-Kpse)ec.C>?
;~RJ5@bp.AqSvV,;i|31Mt7cyNqkc,w3 N"pZdNX"P$wQb)+tYcoXl#mWNr2#Ys<R
}*K/":~g5tHW?aWeV;D2:w\p);i41W{W y]8e|rX.)uFBlyzgg'.{0jO5cV?1"$u_
<%{k|86;8VQJ!!eA>88CW^6D}m?b[;ml l^8.2.pp0g#M.v.Abgt)3[W^F=?a}9%6
'.Dr@9BAybK+vbfYjJSp|0kSoo#ZsJX1 /(I/6()UkM\wN0Eo$Tao':1dW@mbPzq[
!r$E7QiZ#kP!E"tY{9Q4K2ml4$lqWC1P P{n(H5KbUh0:cg8.3-/7I.G]^"!hKeb8
@D"%O8{VIki.`PvYbq{9A-PlOp='^}(" ^L_e./gZyT3)3QvhK;AS+9zEr(Y.NNb8

```

If you use such passwords with at least 32 characters then whatever you encrypt should be safe for years to come ... Unless there are monstrously giant leaps in computing trying to crack the AES encryptions that LUKS, eCryptFS and TrueCrypt use should take millions of years.

So your data should really be safe. There is a far bigger chance that you might forget your passwords or that it is so complex that you will have to write it down somewhere ... which is dangerous as someone else might find it then.

---

### Post by conmat on 2010-09-03
I like to use Hotbits for password generation:

[https://www.fourmilab.ch/hotbits/secure_generate.html](https://www.fourmilab.ch/hotbits/secure_generate.html)

IMHO, the only way to use these passwords successfully is to save them under some master password/passphrase.  There is NO way a human can remember these passwords.

I hope no tells me there is a security flaw in downloading these passwords.

---

### Post by rookcifer on 2010-09-03
Or you can use my password generator.  I recently ported it to GTK.  You can get it from my PPA.

OP, I agree with the others -- encrypt that drive.  You can do it with dm-crypt/LUKS, or if you're not comfortable with the command line, then use Truecrypt.

---

### Post by BkkBonanza on 2010-09-04
Truecrypt and KeepassX for password storage. Both in the Ubuntu repos.

---

### Post by ottosykora on 2010-09-04
> **bodhi.zazen said:**
> +1

LUKS and Truecrypt are both cross platform (Linux and windows).

the only thing one has to mention, that such things need root rights, which is not a problem in ubuntu, but can be on windows systems or others with separate root pw.

---

