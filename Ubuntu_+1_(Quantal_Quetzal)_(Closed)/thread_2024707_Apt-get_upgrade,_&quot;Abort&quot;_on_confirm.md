---
title: "Apt-get upgrade, &quot;Abort&quot; on confirm?"
date: 2012-07-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-07-14
It's a minor glitch and not a new one. I was not gonna say anything, but it's getting on my nerves today, happening a lot. See pic. 

[ATTACH]221232[/ATTACH]

Is there a known fix?

Regards,
Effenberg

---

### Post by ~!geek!~ on 2012-07-14
> **effenberg0x0 said:**
> It's a minor glitch and not a new one. I was not gonna say anything, but it's getting on my nerves today, happening a lot. See pic. 

[ATTACH]221232[/ATTACH]

Is there a known fix?

Regards,
Effenberg

Doesn't entering Y (capital y)  instead of y (small y) work?

---

### Post by QIII on 2012-07-14
Odd.  Updated not two hours ago and it went fine.

Ain't this stuff fun?

---

### Post by philinux on 2012-07-14
Not seeing any issues with apt-get.

---

### Post by jerrylamos on 2012-07-14
> **philinux said:**
> Not seeing any issues with apt-get.

Since 2006 (Dapper Drake) I've had quite a number of installs destroyed by "sudo apt-get dist-upgrade".  Well, I'm backed up, and recovery installs are a good way to show up bugs.

However, the last couple days my preferred
sudo aptitude update && sudo aptitude -y full-upgrade
have not been able to complete the upgrade.

So I'm back to a[t-get expecting destruction any time.

Jerry

---

### Post by effenberg0x0 on 2012-07-14
> **~!geek!~ said:**
> Doesn't entering Y (capital y)  instead of y (small y) work?

Nope... y or Y gives me "Abort"... I have tried the Brazilian  Portuguese localized version (S/s) with same results. 

The good thing is that simply invoking apt again generally works. It's an annoying bug anyway.

Regards,
Effenberg

---

### Post by zika on 2012-07-14
> **effenberg0x0 said:**
> Nope... y or Y gives me "Abort"... I have tried the Brazilian  Portuguese localized version (S/s) with same results. 

The good thing is that simply invoking apt again generally works. It's an annoying bug anyway.

Regards,
EffenbergDid You try „z“... ;)

---

### Post by philinux on 2012-07-14
> **jerrylamos said:**
> Since 2006 (Dapper Drake) I've had quite a number of installs destroyed by "sudo apt-get dist-upgrade".  Well, I'm backed up, and recovery installs are a good way to show up bugs.

However, the last couple days my preferred
sudo aptitude update && sudo aptitude -y full-upgrade
have not been able to complete the upgrade.

So I'm back to a[t-get expecting destruction any time.

Jerry

As long as you read what dist-upgrade wants to do and say no if unsure then stick to just upgrade till the repos settle down there should be no destruction.

Also as mentioned last cycle aptitude is not recommended.

---

### Post by effenberg0x0 on 2012-07-14
> **zika said:**
> Did You try „z“... ;)

I think I even tried &#960; Zika :)
By the way, apt-... yadayada **{-y | --yes | --assume-yes}** works.

Regards,
Effenberg

---

### Post by screaminj3sus on 2012-07-14
I've actually been seeing this issue occasionally on precise as well (and its a clean install), its not just 12.10.

---

### Post by effenberg0x0 on 2012-07-14
> **screaminj3sus said:**
> I've actually been seeing this issue occasionally on precise as well (and its a clean install), its not just 12.10.

I agree. It just got more frequent and annoying now.
Do you get some output we can debug? I get nothing.

Regards,
Effenberg

---

### Post by ventrical on 2012-07-14
Works ok here Al.

```
]
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal/main bash i386 4.2-4ubuntu1 [617 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ quantal/main dpkg i386 1.16.7ubuntu3 [1,746 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ quantal/main libitm1 i386 4.7.1-5ubuntu1 [35.5 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ quantal/main libgomp1 i386 4.7.1-5ubuntu1 [29.7 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ quantal/main gcc-4.7-base i386 4.7.1-5ubuntu1 [15.5 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ quantal/main libstdc++6 i386 4.7.1-5ubuntu1 [335 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ quantal/main libgfortran3 i386 4.7.1-5ubuntu1 [332 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ quantal/main cpp-4.7 i386 4.7.1-5ubuntu1 [5,206 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ quantal/main libquadmath0 i386 4.7.1-5ubuntu1 [198 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ quantal/main libstdc++6-4.7-dev i386 4.7.1-5ubuntu1 [1,725 kB]
..etc..

```

---

### Post by philinux on 2012-07-14
```

```> **effenberg0x0 said:**
> I agree. It just got more frequent and annoying now.
Do you get some output we can debug? I get nothing.

Regards,
Effenberg

Not extremely helpful but.
> -y, --yes, --assume-yes
    Automatic yes to prompts. Assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such as changing a held package or removing an essential package, occurs then apt-get will abort. 

Try the V switch for verbose as well.

There must be an undesirable something going on.

Also double check your sources.

```
sudo apt-get upgrade -Vy
```

---

### Post by screaminj3sus on 2012-07-14
> **ventrical said:**
> Works ok here Al.

```
]
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal/main bash i386 4.2-4ubuntu1 [617 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ quantal/main dpkg i386 1.16.7ubuntu3 [1,746 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ quantal/main libitm1 i386 4.7.1-5ubuntu1 [35.5 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ quantal/main libgomp1 i386 4.7.1-5ubuntu1 [29.7 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ quantal/main gcc-4.7-base i386 4.7.1-5ubuntu1 [15.5 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ quantal/main libstdc++6 i386 4.7.1-5ubuntu1 [335 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ quantal/main libgfortran3 i386 4.7.1-5ubuntu1 [332 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ quantal/main cpp-4.7 i386 4.7.1-5ubuntu1 [5,206 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ quantal/main libquadmath0 i386 4.7.1-5ubuntu1 [198 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ quantal/main libstdc++6-4.7-dev i386 4.7.1-5ubuntu1 [1,725 kB]
..etc..

```
works fine for me like 95% of the time, but sometimes it randomly happens. when it does I just repeat the same command and it updates fine.

---

### Post by effenberg0x0 on 2012-07-14
> **screaminj3sus said:**
> works fine for me like 95% of the time, but sometimes it randomly happens. when it does I just repeat the same command and it updates fine.

Exactly. I have some cron'd update scripts. The unexpected return is killing them, which is why this thing is bothering me. I'll post back if I find something useful. Now that I'm actively trying to debug the thing, the error won't happen (of course).

Regards,
Effenberg

---

### Post by MacUntu on 2012-07-15
Happened a couple of times here, seemingly randomly, but tends to happen when I leave the screen alone for a while. Definitely seen this happen before 12.04.

---

### Post by effenberg0x0 on 2012-07-15
> **MacUntu said:**
> Happened a couple of times here, seemingly randomly, but tends to happen when I leave the screen alone for a while. Definitely seen this happen before 12.04.

MacUntu, I think you got it right. It does happen out of nothing when I press 'Y' immediately when prompted. But it seems like it happens more frequently if I wait a couple minutes before pressing 'Y'. 

Regards,
Effenberg

---

