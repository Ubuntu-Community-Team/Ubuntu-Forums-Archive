---
title: "What should we users do immediately about the heartbleed heartbeet openssl saucy flaw"
date: 2014-04-08
forum: Security
---

### Post by Damico on 2014-04-08
I just belatedly found out about the heartbeat openssl bug ([http://heartbleed.com](http://heartbleed.com)).

Affected versions: OpenSSL versions from 1.0.1 to 1.0.1f.
The vulnerability has been fixed in OpenSSL 1.0.1g.

$ uname -a
Linux desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

$ openssl
OpenSSL> version
OpenSSL 1.0.1e 11 Feb 2013

$ sudo apt-get remove openssl
$ sudo apt-get install openssl

$ openssl
OpenSSL> version
OpenSSL 1.0.1e 11 Feb 2013

Drat.

QUESTION:
**As a user, who is decidedly not a security expert, what do the security experts suggest we users immediately do about this vulnerability?**

---

### Post by CharlesA on 2014-04-08
Run this:

```
openssl version -a
```

It should say build date: April 7 or April 8 if you have the patched version.

---

### Post by mainmeister on 2014-04-08
Set "Check for certificate revocation" on in all browsers. Even after servers have installed the 1.0.1g fix, they then need to revoke their current certificate and issue a new one.

---

### Post by 23dornot23d on 2014-04-09
Has anyone here seen this

[http://techrights.org/2014/04/08/howard-schmidt-codenomicon/](http://techrights.org/2014/04/08/howard-schmidt-codenomicon/)

---

### Post by CharlesA on 2014-04-09
> **mainmeister said:**
> Set "Check for certificate revocation" on in all browsers. Even after servers have installed the 1.0.1g fix, they then need to revoke their current certificate and issue a new one.

The latest version of Firefox should be set to automatically check ssl certs for validity.

> **23dornot23d said:**
> Has anyone here seen this

[http://techrights.org/2014/04/08/howard-schmidt-codenomicon/](http://techrights.org/2014/04/08/howard-schmidt-codenomicon/)

Reads exactly like a tabloid. :rolleyes:

---

### Post by 23dornot23d on 2014-04-09
mmm ..... sometimes wonder about the reasoning ........ but as long as its fixed .......

and we all know our systems are uptodate .....

I upgrade to OpenSSL [COLOR=#ff0000][B]1.0.1f 6 Jan 2014

from what I have read so far this is a check to do[/B][/COLOR]

Finding what version you have ..... cheers Charles A

openssl version -a

Downloads$ openssl version -a
OpenSSL [COLOR=#ff0000]**1.0.1f 6 Jan 2014**[/COLOR]
built on: Fri Jan 10 12:40:28 UTC 2014
platform: debian-amd64
options:  bn(64,64) rc4(16x,int) des(idx,cisc,16,int) blowfish(idx) 
compiler: cc -fPIC -DOPENSSL_PIC -DOPENSSL_THREADS -D_REENTRANT  -DDSO_DLFCN -DHAVE_DLFCN_H -m64 -DL_ENDIAN -DTERMIO -g -O2  -fstack-protector --param=ssp-buffer-size=4 -Wformat  -Werror=format-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions  -Wl,-z,relro -Wa,--noexecstack -Wall -DMD32_REG_T=int  -DOPENSSL_IA32_SSE2 -DOPENSSL_BN_ASM_MONT -DOPENSSL_BN_ASM_MONT5  -DOPENSSL_BN_ASM_GF2m -DSHA1_ASM -DSHA256_ASM -DSHA512_ASM -DMD5_ASM  -DAES_ASM -DVPAES_ASM -DBSAES_ASM -DWHIRLPOOL_ASM -DGHASH_ASM
OPENSSLDIR: "/usr/lib/ssl"


From what I am reading in the latest report - the older ones were more secure ......... can someone clarify if we are better
off with older systems ........ or upgraded ones ........ as its not clear in this thread ...... !!!

Fixed in OpenSSL       1.0.1g (Affected 1.0.1f, 1.0.1e, 1.0.1d, 1.0.1c, 1.0.1b, 1.0.1a, 1.0.1)

Time to log off and go back to a older install again ..... until the repos have something I can use thats safe

[http://www.openssl.org/news/vulnerabilities.html](http://www.openssl.org/news/vulnerabilities.html)

---

### Post by Bashing-om on 2014-04-09
@ 23dornot23d; Don't know ?

I ran :
```

sudo apt-get update
sudo apt-get upgrade

```
and a updated openssl was available, I did "upgrade" and ->
```

sysop@1310mini:~$ openssl version -a
built on: Mon Apr  7 20:33:19 UTC 2014

```

Your result is not the same ?

---

### Post by 23dornot23d on 2014-04-09
Cheers for doing that check ..... maybe its something to do with the download server I use then
I pointed it to UK ..... and maybe there lies the problem .......

Will change servers and see if it changes things - thank you for doing that ......
as I checked again before posting in Synaptic and reloaded the same result came up saying I was
uptodate ......

Will get back to you later - as I swapped into a different OS for the time being ...... have many to choose from
so at least I can jump around a bit ...... confuses me at times - so might confuse anyone trying to get into my
system .... not that it makes a lot of difference here ..... have nothing of real value  - so long as they do not
get in and trash anything ........ even then - so many systems now it probably would not disrupt me too much.

Ok back to doing things again to relax ... ;)

Will let you know later on when I go back in if it will upgrade ok .....

---

### Post by Bashing-om on 2014-04-09
k

---

### Post by CharlesA on 2014-04-09
It could be the mirror didn't have the latest version, but unlikely. When you do boot into Ubuntu, run updates again and it should give you the newest version.

As it stands now, that update is more geared toward servers and people using imaps/pop3s/https/openvpn than desktop users, but it's still a good thing to have updated.

---

### Post by 23dornot23d on 2014-04-09
Cheers am uptodate now and after changing servers - did a safe-upgrade  ....... 
its giving me the same build though but the build date has changed now .........

# openssl version -a
OpenSSL [COLOR=#ff0000]**1.0.1f 6 Jan 2014**[/COLOR]
built on: [COLOR=#ff0000]**Mon Apr  7 21:22:23 UTC 2014**[/COLOR]
platform: debian-amd64
options:  bn(64,64) rc4(16x,int) des(idx,cisc,16,int) blowfish(idx) 
compiler: cc -fPIC -DOPENSSL_PIC -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -m64 -DL_ENDIAN -DTERMIO -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro -Wa,--noexecstack -Wall -DMD32_REG_T=int -DOPENSSL_IA32_SSE2 -DOPENSSL_BN_ASM_MONT -DOPENSSL_BN_ASM_MONT5 -DOPENSSL_BN_ASM_GF2m -DSHA1_ASM -DSHA256_ASM -DSHA512_ASM -DMD5_ASM -DAES_ASM -DVPAES_ASM -DBSAES_ASM -DWHIRLPOOL_ASM -DGHASH_ASM
OPENSSLDIR: "/usr/lib/ssl"

Latest Ubuntu 14.04 - 64 bit and the kernel is now at 3.13.0-23-generic ........

screenshot here of my desktop as I rebooted and just ran it again to check for any changes
[http://i.minus.com/iqFlyZe3NiEOZ.png](http://i.minus.com/iqFlyZe3NiEOZ.png)

Is that as upto date as I can go now ?

ok going back to what was said earlier - seems I am ok now

> 
It should say build date: April 7 or April 8 if you have the patched version. 				


---

### Post by CharlesA on 2014-04-09
That's fine, there was another update to openssl that forced services depending on it to restart.

---

### Post by 23dornot23d on 2014-04-09
Ok thank you - am happy again ;) things are starting going well again today .......

---

### Post by joelgsf on 2014-04-09
I've did an update/upgrade, changed repository to "main server", did an update/upgrade again, but I'm still getting

> 
OpenSSL 1.0.1 14 Mar 2012


both in my desktop and server. In time, I'm using Ubuntu 12.04 LTS on both systems.
How can I get the new version of OpenSSL?
TIA

---

### Post by CharlesA on 2014-04-09
> **CharlesA said:**
> Run this:

```
openssl version -a
```

It should say build date: April 7 or April 8 if you have the patched version.

Run that ^.

---

### Post by cogset on 2014-04-10
> **CharlesA said:**
> 
As it stands now, that update is more geared toward servers and people using imaps/pop3s/https/openvpn than desktop users, but it's still a good thing to have updated.

If you don't mind,I'd like to understand a bit more about this thing:this openssl vulnerability,as far as I can tell from reading of it in "tech" websites
[http://www.zdnet.com/heartbleed-security-patches-coming-fast-and-furious-7000028216/](http://www.zdnet.com/heartbleed-security-patches-coming-fast-and-furious-7000028216/)
[http://arstechnica.com/security/2014/04/heartbleed-vulnerability-may-have-been-exploited-months-before-patch/](http://arstechnica.com/security/2014/04/heartbleed-vulnerability-may-have-been-exploited-months-before-patch/)
does actually affect the server side of things,in other words there's really not much that an average desktop user can do/is supposed to do.Is that correct?
Furthermore,assuming that it has been actually going on since november as some observers are claiming,we can only guess that data has indeed been taken from compromised servers,and there's nothing to be done about it.
Is there anything that desktop users should be aware of,anything unusual to check?

On a side note,as you point out at  imaps/pop3s/https/openvpn,do you mean that folks using a mail client on their desktop could be more at risk then the ones accessing the same services by regular webmail?I don't think so,but just to be sure.

---

### Post by Gustav_Toppa on 2014-04-10
> **cogset said:**
> I'd like to understand a bit more about this thing:this openssl vulnerability. 

 In a heartbeat, Robin Seggelmann < seggelmann at fh-muenster.de > submitted this line of code which was committed an hour before midnight on New Year's Eve, 2011 by Stephen Henson  < steve at openssl.org >.  
[ ** buffer = OPENSSL_malloc(1 + 2 + payload + padding); **]("http://git.openssl.org/gitweb/?p=openssl.git;a=commit;h=4817504d069b4c5082161b02a22116ad75f822b1")

That line of code is only present in OpenSSL versions between 1.0.1 and 1.0.1f, including betas; anything older or newer and the bug isn&#8217;t present.  

[The fix]("https://github.com/openssl/openssl/commit/96db9023b881d7cd9f379b0c154650d6c108e9a3#diff-2") was simply to limit the payload plus padding to 16 bytes
```

[TABLE="class: file-code file-diff tab-size-8 hide-line-numbers line-number-attrs"]
[TR="class: file-diff-line js-file-line gd"]
[TD="class: diff-line-code"]-    /* Read type and payload length first */[/TD]
[/TR]
[TR="class: file-diff-line js-file-line gd"]
[TD="class: diff-line-code"]                    -    hbtype = *p++;[/TD]
[/TR]
[TR="class: file-diff-line js-file-line gd"]
[TD="class: diff-line-code"]                    -    n2s(p, payload);[/TD]
[/TR]
[TR="class: file-diff-line js-file-line gd"]
[TD="class: diff-line-code"]                    -    pl = p;[/TD]
[/TR]
[/TABLE]

```
And, to not allow the heartbeat to exceed its maximum length:
```

unsigned int write_length = 1 /* heartbeat type */ +
 +					    2 /* heartbeat length */ +
 +					    payload + padding;
  
 +		if (write_length > SSL3_RT_MAX_PLAIN_LENGTH)
 +			return 0;

```


Of course,  if the attacker went to the effort to save previous pcaps of traffic (*are you listening GCHQ, NSA, FIS, MPS, etc?*), that attacker  could just pull the private key from the site and decrypt all *saved* communications. 

The user needs to do a few things themselves.
For example, **most users' web browsers are set, by default, to NOT check for revoked certificates!**
[ATTACH=CONFIG]251896[/ATTACH]

---

### Post by 23dornot23d on 2014-04-10
Does anyone know what these 2 lines mean - they are the only things I get warnings about in my authentication logs ........

> 
09/04/2014 17:54:47    keith-K53SV    dbus[721]    [system] Rejected  send message, 7 matched rules; type="method_return", sender=":1.14"  (uid=0 pid=1254 comm="/usr/sbin/dnsmasq --no-resolv  --keep-in-foreground") interface="(unset)" member="(unset)" error  name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=941  comm="NetworkManager ")

09/04/2014 20:11:43    keith-K53SV    systemd-logind[877]    Failed to issue method call: Unknown unit: [EMAIL="autovt@tty6.servic"]autovt@tty6.servic[/EMAIL]e 				 			


the first line of text is repeated a few times in my logs but the second one only appeared once - not sure if its related or not ....... but its the first time I have
seen the second one and it has a yellow triangle against it .........  

( I am on a laptop 14.04 development edition 64 bit latest kernel as of yesterday and fully uptodate as far as I can tell now )

Just for peace of mind if anyone knows if they are anything to worry about or just a bug or something else.

---

### Post by CharlesA on 2014-04-10
> **cogset said:**
> 
On a side note,as you point out at  imaps/pop3s/https/openvpn,do you mean that folks using a mail client on their desktop could be more at risk then the ones accessing the same services by regular webmail?I don't think so,but just to be sure.

No, just that this bug affects anything that uses OpenSSL, which means mail servers in addition to web servers and vpn servers are affected until they have the patch applied.

I created a sticky about this yesterday with some more user-oriented information:
[http://ubuntuforums.org/showthread.php?t=2216096](http://ubuntuforums.org/showthread.php?t=2216096)

---

### Post by dad2 on 2014-04-10
after following the update/upgrade advice in this thread i have the following info on my pc

OpenSSL 1.0.1e 11 Feb 2013
built on: Mon Apr  7 20:31:43 UTC 2014
platform: debian-i386



seeing the build being 1.0.1 e i'm wondering if i have a safety issue here?

---

### Post by 23dornot23d on 2014-04-10
See Post #2, Post #11 and Post #15  - as the build date seems important - for when a patch was applied.

Your build date is in the second line

> 
OpenSSL 1.0.1e 11 Feb 2013
[COLOR=#ff0000]**built on: Mon Apr  7 20:31:43 UTC 2014**[/COLOR]
platform: debian-i386


---

### Post by dad2 on 2014-04-10
> **23dornot23d said:**
> See Post #2, Post #11 and Post #15  - as the build date seems important - for when a patch was applied.

Your build date is in the second line

Good advice but what has confused me is this from post #1

Affected versions: OpenSSL versions from 1.0.1 to 1.0.1f.
The vulnerability has been fixed in OpenSSL 1.0.1g.

---

### Post by CharlesA on 2014-04-10
All the affected versions are still running 1.0.1e, even on CentOS, so they probably just rebuild that version with the patch instead of upgrading to the newer version.

---

### Post by von Corax on 2014-04-10
> **dad2 said:**
> Good advice but what has confused me is this from post #1

Affected versions: OpenSSL versions from 1.0.1 to 1.0.1f.
The vulnerability has been fixed in OpenSSL 1.0.1g.

Again, dad2, read the earlier responses, particularly:

> **23dornot23d said:**
> See Post #2, Post #11 and Post #15  - as the build date seems important - for when a patch was applied.

Your build date is in the second line

This means that even though 1.0.1e contained the heartbleed vulnerability *when it was first released,* the package maintainers have since applied a code patch which closes the vulnerability, and uploaded the patched binaries to the repository. As long as your *build date* is after this happened (on April 7) you're safe.

---

### Post by ajhdk87 on 2014-04-22
I suppose you could use this PPA: **ppa:george-edison55/openssl-heartbleed-fix **to update your openssl package.
I really have no clue if this would help end users, I did this since i run a development server which uses some SSL certs.

$ sudo apt-add-ppa-repository [B]ppa:george-edison55/openssl-heartbleed-fix
[/B]$ sudo apt-get update
$ sudo apt-get upgrade

Done..
Hope this helps.

---

### Post by SeijiSensei on 2014-04-22
It's not necessary to use a PPA. The current repository version contains the patch.

Security patches are often "backported" and applied to the current release version of a package without a major version change.  That's what happened here.

---

### Post by cdysthe on 2014-05-08
Hi,

As someone using Ubuntu and concerned about security I have of course tried to understand the true implications of Heartbleed. There's been a lot of hype and misinformation, so I was really pleased to come across a piece on Hearbleed that went a little deeper and explains what is really going on and suggest solutions:


[https://vivaldi.net/blogs/entry/heartbleed-status-upgrading-to-heartbreak](https://vivaldi.net/blogs/entry/heartbleed-status-upgrading-to-heartbreak)

---

### Post by cariboo on 2014-05-08
Merged two similar threads.

---

