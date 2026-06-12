---
title: "Debian apt and packages broken after following tutorial"
date: 2022-01-23
forum: Ubuntu/Debian BASED
---

### Post by Lideln on 2022-01-23
Hi!

Sorry, I know this is a Ubuntu forum, but the two systems are close, and I got here because I found another topic with a similar issue.

I am using Debian Jessie (8). I followed [a tutorial]("https://blog.okturtles.org/2014/04/how-to-update-openssl-on-debian-testing-jessie-for-heartbleed/") to update OpenSSL (I was at version 1.0.1 and needed to upgrade to version 1.1.0 in order to use Zabbix)

So I added the two lines (for "sid main") in apt sources.list, and installed/updated openssl... But then I got an issue:

```

dpkg: error processing archive /var/cache/apt/archives/libc-l10n_2.33-3_all.deb (--unpack):
 trying to overwrite '/usr/share/locale/be/LC_MESSAGES/libc.mo', which is also in package locales 2.19-18+deb8u10

```

I found some other topic where people had success doing:

```

dpkg --force-overwrite --install /var/cache/apt/archives/libc-l10n_2.33-3_all.deb

```

So I did it.

But then I did:

```

apt-get -f install

```

And got:

```

dpkg: error processing archive /var/cache/apt/archives/init-system-helpers_1.61_all.deb (--unpack):
 trying to overwrite '/usr/sbin/invoke-rc.d', which is also in package sysv-rc 2.88dsf-59
Errors were encountered while processing:
 /var/cache/apt/archives/init-system-helpers_1.61_all.deb
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I stopped the attempt there...

But still, now everything is broken!

[LIST]
[*]I cannot restore packages to how they were before
[*]I cannot event use ```
apt update
```
[/LIST]


Error with "apt update" (after removing the "sid" lines in apt sources.list and trying an apt update as a desperate attempt to fix things...):

```

/usr/lib/apt/methods/https: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.27' not found (required by /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2)
/usr/lib/apt/methods/https: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2)
/usr/lib/apt/methods/https: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /usr/lib/x86_64-linux-gnu/libkrb5.so.3)
/usr/lib/apt/methods/https: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /usr/lib/x86_64-linux-gnu/libk5crypto.so.3)
/usr/lib/apt/methods/https: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /usr/lib/x86_64-linux-gnu/libkrb5support.so.0)
E: Method https has died unexpectedly!
E: Sub-process https returned an error code (1)
E: Method /usr/lib/apt/methods/https did not start correctly

```

And of course... This is a live server, and we have no slave/backup! &#55357;&#56881;&#55357;&#56877;

Could please a good soul help me here? Sys admin is not my job, I am just helping out because the budget is tight... But now I feel really bad...

I fear the only option would be to setup a new server... But we have everything on this one! Web server, mail server, redis, master DB, you name it!

Thank you all in advance for any help! &#55357;&#56911;

Best,

---

### Post by wildmanne39 on 2022-01-23
Thread moved to Ubuntu/Debian BASED sub-forum.

---

### Post by Lideln on 2022-01-23
Thanks! Sorry about this

---

### Post by guiverc on 2022-01-23
Debian Jessie (8) is EOL, see [https://www.debian.org/News/2020/20200709](https://www.debian.org/News/2020/20200709)

> **July 9th, 2020**
 The Debian Long Term Support (LTS) Team hereby announces that Debian 8 jessie support has reached its end-of-life on June 30, 2020, five years after its initial release on April 26, 2015.



A quick scan of what versions are available and I get

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   ssh de2900 -C 'rmadison openssl'
openssl    | 1.0.1t-1+deb8u8  | oldoldoldstable    | source, amd64, armel, armhf, i386
openssl    | 1.1.0l-1~deb9u1  | oldoldstable       | source, amd64, arm64, armel, armhf, i386, mips, mips64el, mipsel, ppc64el, s390x
openssl    | 1.1.0l-1~deb9u1  | oldoldstable-debug | source
openssl    | 1.1.1d-0+deb10u7 | oldstable          | source, amd64, arm64, armel, armhf, i386, mips, mips64el, mipsel, ppc64el, s390x
openssl    | 1.1.1d-0+deb10u7 | oldstable-debug    | source
openssl    | 1.1.1k-1+deb11u1 | stable             | source, amd64, arm64, armel, armhf, i386, mips64el, mipsel, ppc64el, s390x
openssl    | 1.1.1k-1+deb11u1 | stable-debug       | source
openssl    | 1.1.1m-1         | testing            | source, amd64, arm64, armel, armhf, i386, mips64el, mipsel, ppc64el, s390x
openssl    | 1.1.1m-1         | unstable           | source, amd64, arm64, armel, armhf, i386, mips64el, mipsel, ppc64el, s390x
openssl    | 1.1.1m-1         | unstable-debug     | source
openssl    | 3.0.1-1          | experimental       | source, amd64, arm64, armel, armhf, i386, mips64el, mipsel, ppc64el, s390x
openssl    | 3.0.1-1          | experimental-debug | source

```

so I'd have thought the smart thing would have been to upgrade to a *supported* release of Debian GNU/Linux; ie. old-old-stable Debian 9 Stretch, as there at least you'll be getting some security updates should your box be online.

All *supported* releases of Debian do have openssl 1.1.0

---

### Post by Lideln on 2022-01-23
Yeah it is live, and that's why I never did a `apt dist-upgrade` because of the theoretical risks, because we only have this very server.

"if it ain't broken, don't fix it"

Any idea how to fix things with apt?

I followed the discussion [here]("https://ubuntuforums.org/showthread.php?t=2359412") but it is not very positive... I also [tried this]("https://unix.stackexchange.com/questions/79050/can-i-rollback-an-apt-get-upgrade-if-something-goes-wrong") but to no avail.

---

### Post by schragge on 2022-01-24
> **Lideln said:**
> So I added the two lines (for "sid main") in apt sources.list, and installed/updated openssl...
A very bad idea. Mixing repositories for different releases is always risky, but in this case...  The tutorial you followed is from 2014. Debian sid back then was quite different from what it is now. Probably the easiest way out of this mess is restoring from backup to a known working state.

---

### Post by Lideln on 2022-01-24
Yes, that's what I realized... Afterwards, unfortunately... I thought it was the "unstable" branch of the Jessie version, but it isn't. That's probably why the packages were that much different.

Again, admin sys is not my job. I am just lending a hand because the client budget is very tight.

We don't have backups of the "system" itself. Only backups of user-uploaded files + database.

Would it be possible to compile the version myself? But even if it works, it won't magically resolve the existing conflicts, I reckon...

I am studying the possibility to create brand new servers to migrate everything, but there is so much to migrate...

---

### Post by schragge on 2022-01-24
Do you have **aptitude** installed? Comment out the sid lines in **sources.list**, then **apt-get clean**, and show the output of
```
aptitude search '!~v!~Ajessie'
```
I'm not sure about **!~Ajessie** above. Perhaps, it should be **!~A^stable$** or **~Aunstable** instead. The idea is to list real (i.e. non-virtual) packages that originate not from Jessie.

If that doesn't work: using **/var/log/dpkg.log** try to figure out what packages were installed/upgraded during you failed attempt, then remove/revert all of them to their Jessie versions. Some of them may be in a broken state, so you might have to use **dpkg --force-remove-reinstreq** on them, or perhaps, even **--force-all**.

---

### Post by Lideln on 2022-01-24
Thank you for your help @schragge

I did apt-get clean, exited without any output.

Then I tried `[COLOR=#000000][FONT=&quot]aptitude search '!~v!~Ajessie'[/FONT][/COLOR]` but I got thousands of lines, are you sure you want to see them all?

An excerpt:

```

p   dietlibc-doc                    - diet libc documentation - a libc optimized
p   elks-libc                       - 16-bit x86 C library and include files
p   glibc-doc                       - GNU C Library: Documentation
p   glibc-doc-reference             - GNU C Library: Documentation
p   glibc-source                    - GNU C Library: sources
p   klibc-utils                     - small utilities built with klibc for early
p   libc++-dev                      - LLVM C++ Standard library (development fil
p   libc++-helpers                  - LLVM C++ Standard library - build helpers
p   libc++-test                     - LLVM C++ Standard library (test cases)
p   libc++1                         - LLVM C++ Standard library
p   libc++abi-dev                   - LLVM low level support for a standard C++
p   libc++abi-test                  - libc++abi test cases
p   libc++abi1                      - LLVM low level support for a standard C++
p   libc-ares-dev                   - asynchronous name resolver - development f
p   libc-ares2                      - asynchronous name resolver
i   libc-bin                        - GNU C Library: Binaries
i   libc-client2007e                - c-client library for mail protocols - libr
i   libc-client2007e-dev            - c-client library for mail protocols - deve
i A libc-dev-bin                    - GNU C Library: Development binaries
p   libc-icap-mod-clamav            - transitional dummy package

```

I am really fussed, because when I try to rsync files (for backup) I get this:

```

ssh: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.27' not found (required by /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2)
ssh: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2)
ssh: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /usr/lib/x86_64-linux-gnu/libkrb5.so.3)
ssh: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /usr/lib/x86_64-linux-gnu/libk5crypto.so.3)
ssh: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /usr/lib/x86_64-linux-gnu/libkrb5support.so.0)

```

Same thing when I try to send emails later using Redis (via a cron job). Maybe it's Redis that is bugging... Because sending emails directly still seems to work.

Regarding installed packets, output of recent **/var/log/dpkg.log**:

```

2022-01-23 22:11:34 startup archives unpack
2022-01-23 22:11:34 install libmodule-find-perl:all <none> 0.12-1
2022-01-23 22:11:34 status half-installed libmodule-find-perl:all 0.12-1
2022-01-23 22:11:34 status triggers-pending man-db:amd64 2.7.0.2-5
2022-01-23 22:11:34 status unpacked libmodule-find-perl:all 0.12-1
2022-01-23 22:11:34 status unpacked libmodule-find-perl:all 0.12-1
2022-01-23 22:11:34 install libmodule-scandeps-perl:all <none> 1.16-1
2022-01-23 22:11:34 status half-installed libmodule-scandeps-perl:all 1.16-1
2022-01-23 22:11:34 status unpacked libmodule-scandeps-perl:all 1.16-1
2022-01-23 22:11:34 status unpacked libmodule-scandeps-perl:all 1.16-1
2022-01-23 22:11:34 install libproc-processtable-perl:amd64 <none> 0.51-1
2022-01-23 22:11:34 status half-installed libproc-processtable-perl:amd64 0.51-1
2022-01-23 22:11:35 status unpacked libproc-processtable-perl:amd64 0.51-1
2022-01-23 22:11:35 status unpacked libproc-processtable-perl:amd64 0.51-1
2022-01-23 22:11:35 install libsort-naturally-perl:all <none> 1.03-1
2022-01-23 22:11:35 status half-installed libsort-naturally-perl:all 1.03-1
2022-01-23 22:11:35 status unpacked libsort-naturally-perl:all 1.03-1
2022-01-23 22:11:35 status unpacked libsort-naturally-perl:all 1.03-1
2022-01-23 22:11:35 install libterm-readkey-perl:amd64 <none> 2.32-1+b1
2022-01-23 22:11:35 status half-installed libterm-readkey-perl:amd64 2.32-1+b1
2022-01-23 22:11:35 status unpacked libterm-readkey-perl:amd64 2.32-1+b1
2022-01-23 22:11:35 status unpacked libterm-readkey-perl:amd64 2.32-1+b1
2022-01-23 22:11:35 install needrestart:all <none> 1.2-8+deb8u1
2022-01-23 22:11:35 status half-installed needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:35 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:35 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:35 trigproc man-db:amd64 2.7.0.2-5 <none>
2022-01-23 22:11:35 status half-configured man-db:amd64 2.7.0.2-5
2022-01-23 22:11:37 status installed man-db:amd64 2.7.0.2-5
2022-01-23 22:11:37 startup packages configure
2022-01-23 22:11:37 configure libmodule-find-perl:all 0.12-1 <none>
2022-01-23 22:11:37 status unpacked libmodule-find-perl:all 0.12-1
2022-01-23 22:11:37 status half-configured libmodule-find-perl:all 0.12-1
2022-01-23 22:11:37 status installed libmodule-find-perl:all 0.12-1
2022-01-23 22:11:37 configure libmodule-scandeps-perl:all 1.16-1 <none>
2022-01-23 22:11:37 status unpacked libmodule-scandeps-perl:all 1.16-1
2022-01-23 22:11:37 status half-configured libmodule-scandeps-perl:all 1.16-1
2022-01-23 22:11:37 status installed libmodule-scandeps-perl:all 1.16-1
2022-01-23 22:11:37 configure libproc-processtable-perl:amd64 0.51-1 <none>
2022-01-23 22:11:37 status unpacked libproc-processtable-perl:amd64 0.51-1
2022-01-23 22:11:37 status half-configured libproc-processtable-perl:amd64 0.51-1
2022-01-23 22:11:37 status installed libproc-processtable-perl:amd64 0.51-1
2022-01-23 22:11:37 configure libsort-naturally-perl:all 1.03-1 <none>
2022-01-23 22:11:37 status unpacked libsort-naturally-perl:all 1.03-1
2022-01-23 22:11:37 status half-configured libsort-naturally-perl:all 1.03-1
2022-01-23 22:11:37 status installed libsort-naturally-perl:all 1.03-1
2022-01-23 22:11:37 configure libterm-readkey-perl:amd64 2.32-1+b1 <none>
2022-01-23 22:11:37 status unpacked libterm-readkey-perl:amd64 2.32-1+b1
2022-01-23 22:11:37 status half-configured libterm-readkey-perl:amd64 2.32-1+b1
2022-01-23 22:11:37 status installed libterm-readkey-perl:amd64 2.32-1+b1
2022-01-23 22:11:37 configure needrestart:all 1.2-8+deb8u1 <none>
2022-01-23 22:11:37 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 status unpacked needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 status half-configured needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 status installed needrestart:all 1.2-8+deb8u1
2022-01-23 22:11:37 startup packages configure
2022-01-23 22:15:26 startup archives unpack
2022-01-23 22:15:26 install gcc-11-base:amd64 <none> 11.2.0-14
2022-01-23 22:15:26 status half-installed gcc-11-base:amd64 11.2.0-14
2022-01-23 22:15:26 status unpacked gcc-11-base:amd64 11.2.0-14
2022-01-23 22:15:26 status unpacked gcc-11-base:amd64 11.2.0-14
2022-01-23 22:15:26 startup packages configure
2022-01-23 22:15:26 configure gcc-11-base:amd64 11.2.0-14 <none>
2022-01-23 22:15:26 status unpacked gcc-11-base:amd64 11.2.0-14
2022-01-23 22:15:26 status half-configured gcc-11-base:amd64 11.2.0-14
2022-01-23 22:15:26 status installed gcc-11-base:amd64 11.2.0-14
2022-01-23 22:15:26 startup archives unpack
2022-01-23 22:15:26 install libgcc-s1:amd64 <none> 11.2.0-14
2022-01-23 22:15:26 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:15:26 status half-installed libgcc-s1:amd64 11.2.0-14
2022-01-23 22:15:26 status unpacked libgcc-s1:amd64 11.2.0-14
2022-01-23 22:15:26 status unpacked libgcc-s1:amd64 11.2.0-14
2022-01-23 22:15:26 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:15:26 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:15:26 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:15:26 startup packages configure
2022-01-23 22:15:26 configure libgcc-s1:amd64 11.2.0-14 <none>
2022-01-23 22:15:26 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:15:26 status unpacked libgcc-s1:amd64 11.2.0-14
2022-01-23 22:15:26 status half-configured libgcc-s1:amd64 11.2.0-14
2022-01-23 22:15:26 status installed libgcc-s1:amd64 11.2.0-14
2022-01-23 22:15:26 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:15:26 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:15:26 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:15:26 startup archives unpack
2022-01-23 22:15:26 install libc-l10n:all <none> 2.33-3
2022-01-23 22:15:26 status half-installed libc-l10n:all 2.33-3
2022-01-23 22:15:26 status not-installed libc-l10n:all <none>
2022-01-23 22:15:26 upgrade locales:all 2.19-18+deb8u10 2.33-3
2022-01-23 22:15:26 status half-configured locales:all 2.19-18+deb8u10
2022-01-23 22:15:26 status unpacked locales:all 2.19-18+deb8u10
2022-01-23 22:15:26 status half-installed locales:all 2.19-18+deb8u10
2022-01-23 22:15:29 status triggers-pending man-db:amd64 2.7.0.2-5
2022-01-23 22:15:29 status half-installed locales:all 2.19-18+deb8u10
2022-01-23 22:15:29 status unpacked locales:all 2.33-3
2022-01-23 22:15:29 status unpacked locales:all 2.33-3
2022-01-23 22:15:29 install libcbor0.8:amd64 <none> 0.8.0-2
2022-01-23 22:15:29 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:15:29 status half-installed libcbor0.8:amd64 0.8.0-2
2022-01-23 22:15:29 status unpacked libcbor0.8:amd64 0.8.0-2
2022-01-23 22:15:29 status unpacked libcbor0.8:amd64 0.8.0-2
2022-01-23 22:15:29 install libfido2-1:amd64 <none> 1.10.0-1
2022-01-23 22:15:29 status half-installed libfido2-1:amd64 1.10.0-1
2022-01-23 22:15:29 status unpacked libfido2-1:amd64 1.10.0-1
2022-01-23 22:15:29 status unpacked libfido2-1:amd64 1.10.0-1
2022-01-23 22:15:29 trigproc man-db:amd64 2.7.0.2-5 <none>
2022-01-23 22:15:29 status half-configured man-db:amd64 2.7.0.2-5
2022-01-23 22:15:29 status installed man-db:amd64 2.7.0.2-5
2022-01-23 22:15:29 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:15:29 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:15:29 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:06 startup archives install
2022-01-23 22:19:07 install libc-l10n:all <none> 2.33-3
2022-01-23 22:19:07 status half-installed libc-l10n:all 2.33-3
2022-01-23 22:19:07 status unpacked libc-l10n:all 2.33-3
2022-01-23 22:19:07 status unpacked libc-l10n:all 2.33-3
2022-01-23 22:19:07 configure libc-l10n:all 2.33-3 2.33-3
2022-01-23 22:19:07 status unpacked libc-l10n:all 2.33-3
2022-01-23 22:19:07 status half-configured libc-l10n:all 2.33-3
2022-01-23 22:19:07 status installed libc-l10n:all 2.33-3
2022-01-23 22:19:57 startup archives unpack
2022-01-23 22:19:57 upgrade comerr-dev:amd64 2.1-1.42.12-2+deb8u1 2.1-1.46.5-2
2022-01-23 22:19:57 status half-configured comerr-dev:amd64 2.1-1.42.12-2+deb8u1
2022-01-23 22:19:57 status unpacked comerr-dev:amd64 2.1-1.42.12-2+deb8u1
2022-01-23 22:19:57 status half-installed comerr-dev:amd64 2.1-1.42.12-2+deb8u1
2022-01-23 22:19:57 status triggers-pending man-db:amd64 2.7.0.2-5
2022-01-23 22:19:57 status half-installed comerr-dev:amd64 2.1-1.42.12-2+deb8u1
2022-01-23 22:19:57 status unpacked comerr-dev:amd64 2.1-1.46.5-2
2022-01-23 22:19:57 status unpacked comerr-dev:amd64 2.1-1.46.5-2
2022-01-23 22:19:57 trigproc man-db:amd64 2.7.0.2-5 <none>
2022-01-23 22:19:57 status half-configured man-db:amd64 2.7.0.2-5
2022-01-23 22:19:59 status installed man-db:amd64 2.7.0.2-5
2022-01-23 22:19:59 startup packages remove
2022-01-23 22:19:59 status installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 remove libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5 <none>
2022-01-23 22:19:59 status half-configured libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 status config-files libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status config-files libkadm5clnt-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:19:59 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 startup archives unpack
2022-01-23 22:19:59 upgrade libgssapi-krb5-2:amd64 1.12.1+dfsg-19+deb8u5 1.18.3-7
2022-01-23 22:19:59 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 status half-configured libgssapi-krb5-2:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libgssapi-krb5-2:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libgssapi-krb5-2:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libgssapi-krb5-2:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libgssapi-krb5-2:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libgssapi-krb5-2:amd64 1.18.3-7
2022-01-23 22:19:59 upgrade libkrb5-3:amd64 1.12.1+dfsg-19+deb8u5 1.18.3-7
2022-01-23 22:19:59 status half-configured libkrb5-3:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libkrb5-3:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libkrb5-3:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libkrb5-3:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libkrb5-3:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libkrb5-3:amd64 1.18.3-7
2022-01-23 22:19:59 upgrade libk5crypto3:amd64 1.12.1+dfsg-19+deb8u5 1.18.3-7
2022-01-23 22:19:59 status half-configured libk5crypto3:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libk5crypto3:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libk5crypto3:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libk5crypto3:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libk5crypto3:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libk5crypto3:amd64 1.18.3-7
2022-01-23 22:19:59 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:19:59 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 startup packages remove
2022-01-23 22:19:59 status installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 remove libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5 <none>
2022-01-23 22:19:59 status half-configured libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 status config-files libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status config-files libkadm5srv-mit9:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:19:59 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 startup archives unpack
2022-01-23 22:19:59 upgrade libkrb5support0:amd64 1.12.1+dfsg-19+deb8u5 1.18.3-7
2022-01-23 22:19:59 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:19:59 status half-configured libkrb5support0:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libkrb5support0:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libkrb5support0:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libkrb5support0:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libkrb5support0:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libkrb5support0:amd64 1.18.3-7
2022-01-23 22:19:59 upgrade libgssrpc4:amd64 1.12.1+dfsg-19+deb8u5 1.18.3-7
2022-01-23 22:19:59 status half-configured libgssrpc4:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libgssrpc4:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libgssrpc4:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libgssrpc4:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libgssrpc4:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libgssrpc4:amd64 1.18.3-7
2022-01-23 22:19:59 install libkdb5-10:amd64 <none> 1.18.3-7
2022-01-23 22:19:59 status half-installed libkdb5-10:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libkdb5-10:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libkdb5-10:amd64 1.18.3-7
2022-01-23 22:19:59 install libkadm5srv-mit12:amd64 <none> 1.18.3-7
2022-01-23 22:19:59 status half-installed libkadm5srv-mit12:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libkadm5srv-mit12:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libkadm5srv-mit12:amd64 1.18.3-7
2022-01-23 22:19:59 install libkadm5clnt-mit12:amd64 <none> 1.18.3-7
2022-01-23 22:19:59 status half-installed libkadm5clnt-mit12:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libkadm5clnt-mit12:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libkadm5clnt-mit12:amd64 1.18.3-7
2022-01-23 22:19:59 upgrade libkrb5-dev:amd64 1.12.1+dfsg-19+deb8u5 1.18.3-7
2022-01-23 22:19:59 status half-configured libkrb5-dev:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libkrb5-dev:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed libkrb5-dev:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status triggers-pending man-db:amd64 2.7.0.2-5
2022-01-23 22:19:59 status half-installed libkrb5-dev:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked libkrb5-dev:amd64 1.18.3-7
2022-01-23 22:19:59 status unpacked libkrb5-dev:amd64 1.18.3-7
2022-01-23 22:19:59 upgrade krb5-multidev:amd64 1.12.1+dfsg-19+deb8u5 1.18.3-7
2022-01-23 22:19:59 status half-configured krb5-multidev:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status unpacked krb5-multidev:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:19:59 status half-installed krb5-multidev:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:20:00 status half-installed krb5-multidev:amd64 1.12.1+dfsg-19+deb8u5
2022-01-23 22:20:00 status unpacked krb5-multidev:amd64 1.18.3-7
2022-01-23 22:20:00 status unpacked krb5-multidev:amd64 1.18.3-7
2022-01-23 22:20:00 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:20:00 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 trigproc man-db:amd64 2.7.0.2-5 <none>
2022-01-23 22:20:00 status half-configured man-db:amd64 2.7.0.2-5
2022-01-23 22:20:00 status installed man-db:amd64 2.7.0.2-5
2022-01-23 22:20:00 startup packages remove
2022-01-23 22:20:00 status installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 remove libcomerr2:amd64 1.42.12-2+deb8u1 <none>
2022-01-23 22:20:00 status half-configured libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status half-installed libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 status config-files libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 status config-files libcomerr2:amd64 1.42.12-2+deb8u1
2022-01-23 22:20:00 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:20:00 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 startup archives unpack
2022-01-23 22:20:00 install libcom-err2:amd64 <none> 1.46.5-2
2022-01-23 22:20:00 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 status half-installed libcom-err2:amd64 1.46.5-2
2022-01-23 22:20:00 status unpacked libcom-err2:amd64 1.46.5-2
2022-01-23 22:20:00 status unpacked libcom-err2:amd64 1.46.5-2
2022-01-23 22:20:00 install libpcre2-8-0:amd64 <none> 10.39-3
2022-01-23 22:20:00 status half-installed libpcre2-8-0:amd64 10.39-3
2022-01-23 22:20:00 status unpacked libpcre2-8-0:amd64 10.39-3
2022-01-23 22:20:00 status unpacked libpcre2-8-0:amd64 10.39-3
2022-01-23 22:20:00 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:20:00 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 startup packages configure
2022-01-23 22:20:00 configure libpcre2-8-0:amd64 10.39-3 <none>
2022-01-23 22:20:00 status triggers-pending libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 status unpacked libpcre2-8-0:amd64 10.39-3
2022-01-23 22:20:00 status half-configured libpcre2-8-0:amd64 10.39-3
2022-01-23 22:20:00 status installed libpcre2-8-0:amd64 10.39-3
2022-01-23 22:20:00 trigproc libc-bin:amd64 2.19-18+deb8u10 <none>
2022-01-23 22:20:00 status half-configured libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 status installed libc-bin:amd64 2.19-18+deb8u10
2022-01-23 22:20:00 startup archives unpack
2022-01-23 22:20:00 upgrade init-system-helpers:all 1.22 1.61
2022-01-23 22:20:00 status half-configured init-system-helpers:all 1.22
2022-01-23 22:20:00 status unpacked init-system-helpers:all 1.22
2022-01-23 22:20:00 status half-installed init-system-helpers:all 1.22
2022-01-23 22:20:00 status unpacked init-system-helpers:all 1.22
2022-01-23 22:20:00 status installed init-system-helpers:all 1.22
2022-01-23 22:26:16 startup archives unpack
2022-01-23 22:26:16 upgrade init-system-helpers:all 1.22 1.61
2022-01-23 22:26:16 status half-configured init-system-helpers:all 1.22
2022-01-23 22:26:16 status unpacked init-system-helpers:all 1.22
2022-01-23 22:26:16 status half-installed init-system-helpers:all 1.22
2022-01-23 22:26:16 status unpacked init-system-helpers:all 1.22
2022-01-23 22:26:16 status installed init-system-helpers:all 1.22

```


I also tried using the script [found here]("https://unix.stackexchange.com/questions/79050/can-i-rollback-an-apt-get-upgrade-if-something-goes-wrong") :

```

root@ns529099:~# apt-get -s install $(apt-history rollback | tr '\n' ' ')
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Version '2.1-1.42.12-2+deb8u1' for 'comerr-dev' was not found

```

Before trying to update openssl:

```

root@ns529099:~# apt-cache policy openssl
openssl:
  Installed: 1.0.1t-1+deb8u12
  Candidate: 1.0.1t-1+deb8u12
  Version table:
     1.0.2l-1~bpo8+1 0
        100 http://archive.debian.org/debian/ jessie-backports/main amd64 Packages
 *** 1.0.1t-1+deb8u12 0
        500 http://security.debian.org/ jessie/updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.0.1t-1+deb8u8 0
        500 http://debian.bhs.mirrors.ovh.net/debian/ jessie/main amd64 Packages

```

Then I did this (which might explain some of the first lines of the dpkg.log):

```

apt-get install debhelper needrestart

```

Then this:

```

# adding sid lines
nano /etc/apt/sources.list
apt update

```

But then I got this:

```

W: GPG error: http://ftp.debian.org sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 648ACFD622F3D138 NO_PUBKEY 0E98404D386FA1D9

```

So I did this:

```

apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0E98404D386FA1D9
apt update

```

Then this (to check the available version of openssl):

```

root@ns529099:~# apt-cache policy openssl
openssl:
  Installed: 1.0.1t-1+deb8u12
  Candidate: 1.1.1m-1
  Version table:
     1.1.1m-1 0
        500 http://ftp.debian.org/debian/ sid/main amd64 Packages
     1.0.2l-1~bpo8+1 0
        100 http://archive.debian.org/debian/ jessie-backports/main amd64 Packages
 *** 1.0.1t-1+deb8u12 0
        500 http://security.debian.org/ jessie/updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.0.1t-1+deb8u8 0
        500 http://debian.bhs.mirrors.ovh.net/debian/ jessie/main amd64 Packages

```

Then this to follow the tutorial:

```

root@ns529099:~# apt-cache show openssl
Package: openssl
Version: 1.1.1m-1
Installed-Size: 1465
Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
Architecture: amd64
Depends: libc6 (>= 2.33), libssl1.1 (>= 1.1.1)
Suggests: ca-certificates
Description-en: Secure Sockets Layer toolkit - cryptographic utility
 This package is part of the OpenSSL project's implementation of the SSL
 and TLS cryptographic protocols for secure communication over the
 Internet.
 .
 It contains the general-purpose command line binary /usr/bin/openssl,
 useful for cryptographic operations such as:
  * creating RSA, DH, and DSA key parameters;
  * creating X.509 certificates, CSRs, and CRLs;
  * calculating message digests;
  * encrypting and decrypting with ciphers;
  * testing SSL/TLS clients and servers;
  * handling S/MIME signed or encrypted mail.
Description-md5: 9b6de2bb6e1d9016aeb0f00bcf6617bd
Multi-Arch: foreign
Homepage: https://www.openssl.org/
Tag: implemented-in::c, interface::commandline, protocol::ssl, role::program,
 scope::utility, security::cryptography, security::integrity,
 use::checking
Section: utils
Priority: optional
Filename: pool/main/o/openssl/openssl_1.1.1m-1_amd64.deb
Size: 852380
MD5sum: 6ca8e92b80d478dc6e6986ea74156fe2
SHA256: 8db6458f2a39ec4f0d2dd20ec217200c3e73aa429f2f0cb0564e42227cfacc72


Package: openssl
Version: 1.0.2l-1~bpo8+1
Installed-Size: 1069
Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
Architecture: amd64
Depends: libc6 (>= 2.15), libssl1.0.0 (>= 1.0.2~beta3)
Suggests: ca-certificates
Description-en: Secure Sockets Layer toolkit - cryptographic utility
 This package is part of the OpenSSL project's implementation of the SSL
 and TLS cryptographic protocols for secure communication over the
 Internet.
 .
 It contains the general-purpose command line binary /usr/bin/openssl,
 useful for cryptographic operations such as:
  * creating RSA, DH, and DSA key parameters;
  * creating X.509 certificates, CSRs, and CRLs;
  * calculating message digests;
  * encrypting and decrypting with ciphers;
  * testing SSL/TLS clients and servers;
  * handling S/MIME signed or encrypted mail.
Description-md5: 9b6de2bb6e1d9016aeb0f00bcf6617bd
Section: utils
Priority: optional
Filename: pool/main/o/openssl/openssl_1.0.2l-1~bpo8+1_amd64.deb
Size: 687064
MD5sum: 4156c961dc190455597afdfe6656e886
SHA1: c70edca6939bf3736f145af17f2da616be96c930
SHA256: 9fa739acaf52cfc6513ba549a52b3fee9542daebb97dd6df92d5d610e5dffc12


Package: openssl
Version: 1.0.1t-1+deb8u12
Installed-Size: 1094
Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
Architecture: amd64
Depends: libc6 (>= 2.15), libssl1.0.0 (>= 1.0.1k-3+deb8u3)
Suggests: ca-certificates
Description-en: Secure Sockets Layer toolkit - cryptographic utility
 This package is part of the OpenSSL project's implementation of the SSL
 and TLS cryptographic protocols for secure communication over the
 Internet.
 .
 It contains the general-purpose command line binary /usr/bin/openssl,
 useful for cryptographic operations such as:
  * creating RSA, DH, and DSA key parameters;
  * creating X.509 certificates, CSRs, and CRLs;
  * calculating message digests;
  * encrypting and decrypting with ciphers;
  * testing SSL/TLS clients and servers;
  * handling S/MIME signed or encrypted mail.
Description-md5: 9b6de2bb6e1d9016aeb0f00bcf6617bd
Section: utils
Priority: optional
Filename: pool/updates/main/o/openssl/openssl_1.0.1t-1+deb8u12_amd64.deb
Size: 665592
MD5sum: 8b7208445c97d3304ed3bade428201bb
SHA1: 716061433b38fdca4fa1bb035ff5a30bdb16690c
SHA256: e8cee7b0ab8898812499bbb24d2a6b5755d8b5982595beb6c2d87583f51a2c97


Package: openssl
Version: 1.0.1t-1+deb8u8
Installed-Size: 1020
Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
Architecture: amd64
Depends: libc6 (>= 2.15), libssl1.0.0 (>= 1.0.1k-3+deb8u3)
Suggests: ca-certificates
Description-en: Secure Sockets Layer toolkit - cryptographic utility
 This package is part of the OpenSSL project's implementation of the SSL
 and TLS cryptographic protocols for secure communication over the
 Internet.
 .
 It contains the general-purpose command line binary /usr/bin/openssl,
 useful for cryptographic operations such as:
  * creating RSA, DH, and DSA key parameters;
  * creating X.509 certificates, CSRs, and CRLs;
  * calculating message digests;
  * encrypting and decrypting with ciphers;
  * testing SSL/TLS clients and servers;
  * handling S/MIME signed or encrypted mail.
Description-md5: 9b6de2bb6e1d9016aeb0f00bcf6617bd
Tag: implemented-in::c, interface::commandline, protocol::ssl, role::program,
 scope::utility, security::cryptography, security::integrity,
 use::checking
Section: utils
Priority: optional
Filename: pool/main/o/openssl/openssl_1.0.1t-1+deb8u8_amd64.deb
Size: 663812
MD5sum: f141c2d14f6eee7c4c82e828b8497aa4
SHA1: 08ee7cc3a3a0bfad73ec6dcac3a0478e574cc7c5
SHA256: a7b2fef9503098381bcb75c6c1b6d63c0c7222e34dec65340967cb64ee1299b0

```

Then this:

```

apt install openssl

```

It returned this:

```

Preconfiguring packages ...
Selecting previously unselected package gcc-11-base:amd64.
(Reading database ... 54362 files and directories currently installed.)
Preparing to unpack .../gcc-11-base_11.2.0-14_amd64.deb ...
Unpacking gcc-11-base:amd64 (11.2.0-14) ...
Setting up gcc-11-base:amd64 (11.2.0-14) ...
Selecting previously unselected package libgcc-s1:amd64.
(Reading database ... 54367 files and directories currently installed.)
Preparing to unpack .../libgcc-s1_11.2.0-14_amd64.deb ...
Unpacking libgcc-s1:amd64 (11.2.0-14) ...
Replacing files in old package libgcc1:amd64 (1:4.9.2-10+deb8u1) ...
Processing triggers for libc-bin (2.19-18+deb8u10) ...
Setting up libgcc-s1:amd64 (11.2.0-14) ...
Processing triggers for libc-bin (2.19-18+deb8u10) ...
Selecting previously unselected package libc-l10n.
(Reading database ... 54369 files and directories currently installed.)
Preparing to unpack .../libc-l10n_2.33-3_all.deb ...
Unpacking libc-l10n (2.33-3) ...
dpkg: error processing archive /var/cache/apt/archives/libc-l10n_2.33-3_all.deb (--unpack):
 trying to overwrite '/usr/share/locale/be/LC_MESSAGES/libc.mo', which is also in package locales 2.19-18+deb8u10
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../locales_2.33-3_all.deb ...
Unpacking locales (2.33-3) over (2.19-18+deb8u10) ...
Selecting previously unselected package libcbor0.8:amd64.
Preparing to unpack .../libcbor0.8_0.8.0-2_amd64.deb ...
Unpacking libcbor0.8:amd64 (0.8.0-2) ...
Selecting previously unselected package libfido2-1:amd64.
Preparing to unpack .../libfido2-1_1.10.0-1_amd64.deb ...
Unpacking libfido2-1:amd64 (1.10.0-1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for libc-bin (2.19-18+deb8u10) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc-l10n_2.33-3_all.deb
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

That's when I did the "--force-overwrite", with the sad ending you know...

Does that help figuring out what I should do to revert things to normal?

I am really fussed if I cannot perform a backup (because automatic backup failed as soon as I tried this, last night)

Thank you again, sincerely, for your help!

Best,

---

### Post by Lideln on 2022-01-24
PS: I cannot update my post to change a few words, the forum shows me a completely blank textarea... So I'm leaving it as it is, sorry if there are mistakes in it.
When I say "[COLOR=#000000]Before trying to update openssl:"[/COLOR] it is not related to the previous comment. I actually meant "this below is the output before I even tried to update openssl"

---

### Post by Lideln on 2022-01-24
> **schragge said:**
> 
If that doesn't work: using **/var/log/dpkg.log** try to figure out what packages were installed/upgraded during you failed attempt, then remove/revert all of them to their Jessie versions. Some of them may be in a broken state, so you might have to use **dpkg --force-remove-reinstreq** on them, or perhaps, even **--force-all**.

You think **dpkg --force-remove-reinstreq ****--force-all** will not break the server further? If so then I am willing to try. I have to first remove the two sid lines from sources.list, right? (which I already did, but just to be sure)

Because I don't have a backup of the files uploaded since last night, because rsync fails.

---

### Post by Lideln on 2022-01-24
Database replication still seems to be working though, this is at least some relief!!

Only rsync is bugged, but I may be able to find a way to manually download/backup files using scp in MobaXterm. Clearly not ideal, but I least I won't lose files.

---

### Post by Lideln on 2022-01-24
Does it mean I should do **dpkg --force-remove-reinstreq [B]--force-all**[/B] for every package below?

Is there a way to revert them all at once?

I compiled the list below by analysing the ouput of apt install, the two times I called it last night. Some packages were installed, others were removed.

```

gcc-11-base_11.2.0-14_amd64.deb
libgcc-s1_11.2.0-14_amd64.deb
libc-l10n_2.33-3_all.deb
locales_2.33-3_all.deb
libcbor0.8_0.8.0-2_amd64.deb
libfido2-1_1.10.0-1_amd64.deb


comerr-dev_2.1-1.46.5-2_amd64.deb
libkadm5clnt-mit9 (= 1.12.1+dfsg-19+deb8u5) (removed)
libc-bin (2.19-18+deb8u10)
libgssapi-krb5-2_1.18.3-7_amd64.deb
libkrb5-3_1.18.3-7_amd64.deb
libk5crypto3_1.18.3-7_amd64.deb
libkadm5srv-mit9:amd64 (removed)


libkrb5support0_1.18.3-7_amd64.deb
libgssrpc4_1.18.3-7_amd64.deb
libkdb5-10_1.18.3-7_amd64.deb
libkadm5srv-mit12_1.18.3-7_amd64.deb
libkadm5clnt-mit12_1.18.3-7_amd64.deb
libkrb5-dev_1.18.3-7_amd64.deb
krb5-multidev_1.18.3-7_amd64.deb
libcomerr2:amd64 (1.42.12-2+deb8u1) (removed)


libcom-err2_1.46.5-2_amd64.deb
libpcre2-8-0_10.39-3_amd64.deb
init-system-helpers_1.61_all.deb

```

Thank you for your kind help!

Best,

---

### Post by schragge on 2022-01-24
> **Lideln said:**
> Does it mean I should do **dpkg --force-remove-reinstreq [B]--force-all**[/B] for every package below?
No. It's not both **--force** options, it's either&#8212;or. And only use them if the dpkg command without **--force** fails. So, first try
```
apt-get remove libfido2
```
Note the packages that will be removed. E.g. openssh-client may depend on libfido2, so it will be removed as well. You'll have to reinstall it later if you need it. Only if the command above doesn't work, proceed with
```
dpkg -r libfido2
```
If that doesn't work either, try
```
dpkg -r --force-remove-reinstreq libfido2
```
And finally, as the last resort
```
dpkg -r --force-all libfido2
```
Actually, always check what is going to be removed on each step so that you won't end up in a worse state than you're in now.

---

### Post by Lideln on 2022-01-24
Wow it is scary, tedious, and requires great precautions!

And I have to do this for each of the 25 packages listed above?

Just to be clear, if **`[COLOR=#000000][FONT=&amp]apt-get remove {package}[/FONT][/COLOR]`** works, I have to do an install just after? Or do I have to wait to have removed them all before begin reinstalling?

Not sure this is gonna work though, since some packages are required by almost everything on the server... Don't you think?
How can I keep using the server if I uninstall libc or gcc oor locales or things like that?

Wouldn't it be best to **`[COLOR=#000000][FONT=&amp]dpkg -r --force-remove-reinstreq {package}[/FONT][/COLOR]`** directly so that the package gets reinstalled properly in one single command? (if I understand correctly)

Thanks @schragge!

---

### Post by Lideln on 2022-01-24
Or even [COLOR=#000000] [/COLOR]**`[COLOR=#000000]dpkg -r --force-remove-reinstreq {package1} {package2} {package3}...[/COLOR]`** if it is possible?

---

### Post by schragge on 2022-01-24
> **Lideln said:**
> Just to be clear, if **`[COLOR=#000000][FONT=&amp]apt-get remove {package}[/FONT][/COLOR]`** works, I have to do an install just after? Or do I have to wait to have removed them all before begin reinstalling?
It depends. Better first remove all of them. But that may be too tedious, or even unrealistic, if some of them are required by a lot of other packages. I'd start with the packages that probably have only a few dependencies like **libfido2** and **libcbor0.8**.

> Not sure this is gonna work though, since some packages are required by almost everything on the server... Don't you think?
How can I keep using the server if I uninstall libc or gcc oor locales or things like that? What you are going to do is not unlike downgrading a system. Thus, [SystemDowngrade](https://wiki.debian.org/SystemDowngrade) @Debian Wiki probably applies here. So, you may try the procedure outlined there.

> Wouldn't it be best to **`[COLOR=#000000][FONT=&amp]dpkg -r --force-remove-reinstreq {package}[/FONT][/COLOR]`** directly so that the package gets reinstalled properly in one single command? (if I understand correctly)
No, **[FONT=monospace]--force-remove-reinstreq[/FONT]** wouldn't reinstall anything. It's meant to remove broken packages that require reinstall and cannot be removed normally because of that. I don't think **dpkg** is able to reinstall packages in one command. For that, you'll have to use **apt-get install --reinstall**. The problem is what's going to be reinstalled if **apt update** failed before that?

---

### Post by Lideln on 2022-01-24
> **schragge said:**
> It depends. Better first remove all of them. But that may be too tedious, or even unrealistic, if some of them are required by a lot of other packages. I'd start with the packages that probably have only a few dependencies like **libfido2** and **libcbor0.8**.

 What you are going to do is not unlike downgrading a system. Thus, [SystemDowngrade]("https://wiki.debian.org/SystemDowngrade") @Debian Wiki probably applies here. So, you may try the procedure outlined there.


No, **[FONT=monospace]--force-remove-reinstreq[/FONT]** wouldn't reinstall anything. It's meant to remove broken packages that require reinstall and cannot be removed normally because of that. I don't think **dpkg** is able to reinstall packages in one command. For that, you'll have to use **apt-get install --reinstall**. The problem is what's going to be reinstalled if **apt update** failed before that?

Oh, so sad, I thought **reinstreq** meant "please reinstall"... So gullible of me ^^

Thanks for the "systemdowngrade" link, it does not give much hope though.

Next time I try to update a lib, I will do a "system restore point" like in Windows.

I think the safest route might be to just give up. Install a new infrastructure somewhere else, migrate everything, and drop this server...

Thank you for your help though! Maybe, when the sky is clear blue again, I will try your reinstreq method before dropping the server, just out of curiosity :)

Even if it worked, I would need to dist-upgrade anyway, which is still risky...

I'll keep you posted! Thank you again for your kind help!! :) :) :)

---

### Post by Lideln on 2022-01-24
Well... My wifi connection got reset, and now I can no longer log into the server (using SSH)...

This is becoming a nightmare!

I'll try to find another solution, like the hosting provider console.

---

