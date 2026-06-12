---
title: "Install mutt"
date: 2019-03-29
forum: Server Platforms
---

### Post by tomdf on 2019-03-29
Hi Guys,

i want to install mutt on ubuntu 18.04 but i get errors that it is not installable.

```

[COLOR=#202124][FONT=Roboto]root@server1:~# apt-get install mutt[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Building dependency tree       [/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Reading state information... Done[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Some packages could not be installed. This may mean that you have[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]requested an impossible situation or if you are using the unstable[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]distribution that some required packages have not yet been created[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]or been moved out of Incoming.[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]The following information may help to resolve the situation:[/FONT][/COLOR]

[COLOR=#202124][FONT=Roboto]The following packages have unmet dependencies:[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto] mutt : Depends: libgpgme11 (>= 1.2.0) but it is not installable[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]        Depends: libtokyocabinet9 (>= 1.4.47) but it is not installable[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]E: Unable to correct problems, you have held broken packages.[/FONT][/COLOR]

```

I want to use mutt for sending me an email daily with the postfix report errors.
Does anyone have an idea how i can install mutt or ist there an alternative for that?

thanks for your kind help
Tom

---

### Post by Bashing-om on 2019-03-29
tomdf; Hummmm ...

A packaging error ??

what shows:
```

apt policy libgpgme11 libtokyocabinet9

```

As reference - my system:
> 
sysop@x1804mini:~$ apt list libgpgme11
Listing... Done
libgpgme11/bionic-updates,now 1.10.0-1ubuntu2 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

sysop@x1804mini:~$ apt list libtokyocabinet9
Listing... Done
libtokyocabinet9/bionic 1.4.48-11 amd64

sysop@x1804mini:~$ apt depends mutt
mutt
  Depends: libc6 (>= 2.15)
  Depends: libgnutls30 (>= 3.5.6)
  Depends: libgpgme11 (>= 1.2.0)
  Depends: libgssapi-krb5-2 (>= 1.14+dfsg)
  Depends: libidn11 (>= 1.13)
  Depends: libncursesw5 (>= 6)
  Depends: libsasl2-2
  Depends: libtinfo5 (>= 6)
  Depends: libtokyocabinet9 (>= 1.4.47)
  Breaks: <mutt-kz>
  Breaks: <mutt-patched>
  Recommends: locales
  Recommends: mime-support
  Recommends: libsasl2-modules
 |Suggests: <default-mta>
    postfix
  Suggests: <mail-transport-agent>
    citadel-server
    courier-mta
    esmtp-run
    exim4-daemon-light
    lsb-invalid-mta
    masqmail
    msmtp-mta
    nullmailer
    opensmtpd
    qmail-run
    sendmail-bin
    ssmtp
    dma
    dma:i386
    exim4-daemon-heavy
    postfix
  Suggests: urlview
 |Suggests: aspell
    aspell:i386
  Suggests: ispell
    ispell:i386
  Suggests: gnupg
    gnupg:i386
  Suggests: <mixmaster>
  Suggests: openssl
    openssl:i386
  Suggests: ca-certificates
  Replaces: <mutt-kz>
  Replaces: <mutt-patched>

sysop@x1804mini:~$ apt policy libgpgme11 libtokyocabinet9
libgpgme11:
  Installed: 1.10.0-1ubuntu2
  Candidate: 1.10.0-1ubuntu2
  Version table:
 *** 1.10.0-1ubuntu2 500
        500 [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.10.0-1ubuntu1 500
        500 [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic/main amd64 Packages
libtokyocabinet9:
  Installed: (none)
  Candidate: 1.4.48-11
  Version table:
     1.4.48-11 500
        500 [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic/main amd64 Packages
sysop@x1804mini:~$ 


[INDENT][INDENT]did someone drop the ball ?
[/INDENT][/INDENT]

---

### Post by tomdf on 2019-03-30
Thanks so much for your kind help 
have a great day

---

