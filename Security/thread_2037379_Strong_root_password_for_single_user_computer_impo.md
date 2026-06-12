---
title: "Strong root password for single user computer important?"
date: 2012-08-04
forum: Security
---

### Post by codell on 2012-08-04
I am the only one who uses my machine. Luks/dmcrypt is used to encrypt the whole hdd. If it gets stolen while powered off, no one can access my data.

What if someone steals it while I am sitting at it? That's worst case, he can access all my data.

And what if someone break into my user account over internet? That's also worst case, he can access all my data.

Why should I use a strong root password? Is that necessary if I am the only user?

I understand that a strong root password may help in a multi user environment. One compromised account won't lead into compromising all others as well.

But in as a single user? Do I have to use a strong root password or doesn't it matter for me?

---

### Post by ranger1021994 on 2012-08-04
Boot password is used to login your account and authorise changes relating to your system.
So strong boot password is advisable.
Yes if you are logged in then he/she can access all your data since data is decrypted after you login.

You can use Truecrypt double volume and encrypt only the necessary data.
Here is Truecypt FAQ : [http://www.truecrypt.org/faq](http://www.truecrypt.org/faq)

---

### Post by codell on 2012-08-04
> **ranger1021994 said:**
> Boot password is used to login your account and authorise changes relating to your system.
Who talked about boot password? Root password!

> **ranger1021994 said:**
> So strong boot password is advisable.
I have a strong one for luks/dmcrypt. Not a strong one for root. Whats the point?

> **ranger1021994 said:**
> You can use Truecrypt double volume and encrypt only the necessary data.
I could also use truly free software and use luks/dmcrypt to create file containers. Double encryption. But whats the point?

Against physical theft while powered on, thats snake oil. I never know if a copy of my file is still in tmp or swap.

Against someone putting a trojan over the internet on my computer no amount of encryption layers will help. Keylogger seeing all.

Whats the motivation for a strong root password?

---

### Post by robtygart on 2012-08-04
You need your root password to install software or make changes. If someone was attacking you and could guess your password they could do some damage. 

But unless they are directly attacking YOU and if your not trying to protect something I would not worry about a strong root password.


I sould add you can access other user accounts /root/home

---

### Post by thnewguy on 2012-08-04
Ubuntu doesn't use the root account by default so I'm not sure why you're concerned about it. Just leave the root account disabled.
If you're talking about your own personal user account then, assuming you don't have any network services running and assuming your encryption password is different than your user password and assuming you never leave your computer lying around in sleep mode (or locked), then you don't really need a strong password on your account. However, if any of the above assumptions are false then you should protect your user account with a strong, complex password.

---

### Post by cryptotheslow on 2012-08-04
The root account is used when you boot into recovery mode from GRUB so setting a password on it can slow down that way in to your system. But as you say, an attacker would have had to get past your LUKS passphrase first.

In normal running the root account is disabled.

You should consider having a strong password on your own account if it has sudo access.

As for attacks "over the internet" - look at the AppArmor sticky thread in this forum for how to confine application processes to only the files they really need.

---

### Post by Hungry Man on 2012-08-04
Because if I hack a service and you have a weak root account I can guess/bruteforce it and gain admin rights.

---

### Post by Scott Harrison on 2012-08-04
I fail to understand why anybody would come up with and use a password that they would consider weak?

I use numerous passwords for different situations and all of them are more than 6 characters, all of them contain capitals and either/both numbers and symbols. It's really not difficult to remember a quality password, so long as you're clever in making it up.

For example, "This is a strong root password for Ubuntu 12.04!"
- **71aSRP4u12.04! **- you now have a 14 character password that is almost impossible to bruteforce in a reasonable amount of time... Unless 1000 years is reasonable to you... lol

---

### Post by CharlesA on 2012-08-06
> **Scott Harrison said:**
> 
For example, "This is a strong root password for Ubuntu 12.04!"
- **71aSRP4u12.04! **- you now have a 14 character password that is almost impossible to bruteforce in a reasonable amount of time... Unless 1000 years is reasonable to you... lol
It is also impossible to remember.

[http://xkcd.com/936/](http://xkcd.com/936/)

---

### Post by robtygart on 2012-08-06
> **CharlesA said:**
> It is also impossible to remember.

[http://xkcd.com/936/](http://xkcd.com/936/)

Not at all, my wifi password is over 30 with letters numbers and symbols, I still remeber it, no dictionary words, nothing personal that can be figured out.

---

### Post by Hungry Man on 2012-08-06
An easy way to make a simple and memorable password is to pad it.

Take any decent password:

PaintItBlack062063

And pad it:

!@#PaintItBlock062063!@#

Padding is easy to remember. So is a song title + random date (not your birthday, my personal choice is an exgfs birthday) and that password is very very easily to remember, very very difficult to guess, and impossible to bruteforce.

---

### Post by CharlesA on 2012-08-06
Good one, Hungry Man. ;)

I think XKCD sorta went into that, minus the padding.

---

### Post by DanR01 on 2012-08-06
I use pwgen which uses /dev/urandom to generate key files.

I've set the password length to 64 characters and there are 30,000 or so lines.

Choose a line and decide where to start the password at.

```
6R~]#?VU|:zgRr8|O:Aq-&zJ<tbeSf1,dN'\vguB@OpLbyPm=L0L<T$GE8>U(SSR
Z[_xK#(tF!S[eBc>~x7P+yU/a2q8.j^*5f\vXWzc&0Q8av*#z,TQ,R)`t(nk,4qA
]rG19EG=a61lYfq*zx%Za,}2EIbyc;\Rh!6_jP3<@9fZi<zt\}T9CCqm@h'JQ{<%
HJj*7Oissji%Esp|;LwSx*y)mV~X*WSD\@Y)gvdJ$6#&+:%`FNfs\aUpA+<%cUNv
I15`@TC5h{L3H`8&X5+j%-`{>XEK(2C=/Fe]ES:ixr*QrU;|cAx<B07yvLz%}ItU
u:|,ThN;B1t|+byVd0q|T4uHHi1+5<@_hzNWU`qUeTE:s0S~dZ>9J84`E:]Bq/Bg
matg<;N6^+<\(Xmgz]`S72Pf"]83o`MMxoDCT(IlGRe""!EMO">q=}*MQ!boS].\
!s)4{o.iNh1/'yF+9#ZpXmi348wQ#uO},hn{5qrg'v[vDuo^~yZ|mT|[n:dZx`It
WY,=s.46Ivdgxq.xn0WqO1t05JA,KTO(UrI4XgwKg%AH}xV|KQhM/YA%-.'UO2G2
X&8n[Jc6C({SY{O$'o(i8"<j`~;LPFn9=_*%P`}2({z&01e=ZXD@:xl9/Un3A^G&

```Should be pretty hard to bruteforce if the file is big enough!

---

