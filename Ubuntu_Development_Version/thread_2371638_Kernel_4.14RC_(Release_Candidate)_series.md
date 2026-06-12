---
title: "Kernel 4.14RC (Release Candidate) series"
date: 2017-09-16
forum: Ubuntu Development Version
---

### Post by Doug S on 2017-09-16
Kernel 4.14-rc1 is available from [kernel.org]("https://www.kernel.org/"), and on the [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14-rc1/"). A day early again.

EDIT: I have been running 4.14-rc1 for a couple of hours now, without any issue.

---

### Post by Doug S on 2017-10-02
I missed [kernel 4.14-rc2 ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14-rc2/")last week.
I have been running [kernel 4.14-rc3]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14-rc3/") (compiled myself, using the Ubuntu kernel configuration) for a short time. No issues so far.

---

### Post by DougieFresh4U on 2017-10-05
Running kernel 4.14rc3 I have no internet, wifi/wired.
If I boot back to 4.13 all is good.
Hopefully an update in the near future will solve this issue.

---

### Post by Doug S on 2017-10-05
> **DougieFresh4U said:**
> Running kernel 4.14rc3 I have no internet, wifi/wired.
If I boot back to 4.13 all is good.
Hopefully an update in the near future will solve this issue.Did you try 4.14-rc1? There are kernel configuration file differences between -rc1 and -rc3. Unlikely to be the problem, but worth a try.

EDIT: See my post below. The "no network" issue is due to the same root cause.

---

### Post by Doug S on 2017-10-05
With kernel 4.14-rc3 running on my main test server host, mysql and libvirtd do not start. This was all fine with -rc1. Since I missed -rc2 and after reading the notes about -rc2, this in particular:

> Anyway, the only unusual thing worth noting here is that the security subsystem pull request that came in during the merge window got rejected due to problems, and so rc2 ends up with most of that security pull having been merged in independent pieces instead.
 I tried -rc2 and indeed they don't work on it either.

I get:

```
doug@s15:~$ [COLOR="#FF0000"]systemctl status mysql.service[/COLOR]
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: activating (start-post) (Result: exit-code) since Thu 2017-10-05 15:12:28 PDT; 3s ago
  Process: 3165 ExecStart=/usr/sbin/mysqld [COLOR="#FF0000"](code=exited, status=1/FAILURE)[/COLOR]
  Process: 3150 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 3165 (code=exited, status=1/FAILURE);         : 3166 (mysql-systemd-s)
    Tasks: 2
   Memory: 2.2M
      CPU: 237ms
   CGroup: /system.slice/mysql.service
           &#9492;&#9472;control
             &#9500;&#9472;3166 /bin/bash /usr/share/mysql/mysql-systemd-start post
             &#9492;&#9472;3204 sleep 1

Oct 05 15:12:28 s15 systemd[1]: Starting MySQL Community Server...
Oct 05 15:12:31 s15 systemd[1]: mysql.service: Main process exited, code=exited, status=1/FAILURE
doug@s15:~$ [COLOR="#FF0000"]systemctl status libvirtd.service[/COLOR]
&#9679; libvirt-bin.service - Virtualization daemon
   Loaded: loaded (/lib/systemd/system/libvirt-bin.service; enabled; vendor preset: enabled)
   Active: inactive (dead) (Result: exit-code) since Thu 2017-10-05 15:09:30 PDT; 3min 15s ago
     Docs: man:libvirtd(8)
           http://libvirt.org
  Process: 2268 ExecStart=/usr/sbin/libvirtd $libvirtd_opts (code=exited, status=6)
 Main PID: 2268 (code=exited, status=6)

Oct 05 15:09:30 s15 systemd[1]: libvirt-bin.service: Unit entered failed state.
Oct 05 15:09:30 s15 systemd[1]: libvirt-bin.service: Failed with result 'exit-code'.
Oct 05 15:09:30 s15 systemd[1]: libvirt-bin.service: Service hold-off time over, scheduling restart.
Oct 05 15:09:30 s15 systemd[1]: Stopped Virtualization daemon.
Oct 05 15:09:30 s15 systemd[1]: libvirt-bin.service: Start request repeated too quickly.
Oct 05 15:09:30 s15 systemd[1]: [COLOR="#FF0000"]Failed to start Virtualization daemon.[/COLOR]

```And a ton of apparmor="DENIED" messages in the dmesg output.

EDIT: The problem commit is:

79444df4e7f03843be78e4b9188d095931648842 Merge tag 'apparmor-pr-2017-09-22' of git://git.kernel.org/pub/scm/linux/kernel/git/jj/linux-apparmor

However, that commit is a collection of 17 commits. After bisecting the kernel, the culprit is:

> commit 651e28c5537abb39076d3949fb7618536f1d242e
Author: John Johansen <john.johansen@canonical.com>
Date:   Tue Jul 18 23:18:33 2017 -0700

    apparmor: add base infastructure for socket mediation

See also [this thread]("https://lkml.org/lkml/2017/10/3/2").

---

### Post by Doug S on 2017-10-07
As a temporary workaround to all the apparmor issues, I have simply deleted it entirely:

```
scripts/config --disable SECURITY_APPARMOR
```

---

### Post by Doug S on 2017-10-09
Kernel 4.14-rc4 has been available from [kernel.org]("https://www.kernel.org/") for at least 8 hours now. However, it is still not yet available in [the Ubuntu PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") (I don't know why).

I have only been running it for a few minutes, and still with apparmor not included.

---

### Post by dino99 on 2017-10-09
Artful is a LTS release, should be good to get also the LTS 4.14 kernel (6 maintenance years); but seems too short before final release. :o

Oops, with actual Canonical quality, i'm seeing LTS everywhere :lolflag:

---

### Post by Doug S on 2017-10-09
> **dino99 said:**
> Artful is a LTS release, should be good to get also the LTS 4.14 kernel (6 maintenance years); but seems too short before final release. :ono, artful is not an LTS, the next one, 18.04 is LTS. But yes, an LTS kernel in an LTS ubuntu is a good idea.

---

### Post by jbicha on 2017-10-09
> **dino99 said:**
> Artful is a LTS release, should be good to get also the LTS 4.14 kernel (6 maintenance years)

Please don't assume that all LTS kernels will get 6 years of support.

See [https://www.kernel.org/releases.html](https://www.kernel.org/releases.html)

---

### Post by DougieFresh4U on 2017-10-16
> **Doug S said:**
> Did you try 4.14-rc1? There are kernel configuration file differences between -rc1 and -rc3. Unlikely to be the problem, but worth a try.

EDIT: See my post below. The "no network" issue is due to the same root cause.

4.14-rc5 no internet, wired/wifi.
Back to 4.14-rc1

---

### Post by lonniehenry-gmail on 2017-10-17
I have the same problem with the rc not being able to use wifi.  rc1 works and the rest fail to connect.  The sparky linux work fine.  Not sure what to try next.  Zenbook ux305ua running Ubuntu 17.10, Budgie 17.10 and Sparky Linux

---

### Post by Doug S on 2017-10-18
see also [this bug report]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1721278").

---

### Post by rrnbtter on 2017-10-23
Greetings,
RC6 Kernel still no WIFI, RTL card.

---

### Post by Doug S on 2017-10-27
With respect to the apparmor issues (stuff not working), this entry from [the bug report]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1721278") is important:

> The kernel patch causing the issue has been reverted. So 4.14-rc7 should work as pre 4.14-rc2

EDIT: Additionally, [the related e-mail thread]("https://marc.info/?l=linux-kernel&m=150903938103642&w=2") is rather interesting/entertaining.

---

### Post by Doug S on 2017-10-29
[Kernel 4.14-rc7 is available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14-rc7/"). As per the above posts, the troubles should be fixed.

EDIT: My issues with mysql and libvirtd not starting are indeed fixed.

---

### Post by lonniehenry-gmail on 2017-10-30
Kernel 4.14-rc7 did fix my network problem.

---

### Post by mörgæs on 2017-10-30
> **Doug S said:**
> Additionally, [the related e-mail thread]("https://marc.info/?l=linux-kernel&m=150903938103642&w=2") is rather interesting/entertaining.

Whoa... but good to see that someone takes regressions seriously.

---

### Post by rrnbtter on 2017-10-30
Greetings,
Working fine here.  No need to install the Git/RTL drivers for WIFI with this one. It has been since the near end of 17.04 that I have had default WIFI with RTL. 
In addition, all of the information in this thread is much appreciated. Thanks

---

### Post by Doug S on 2017-11-05
Kernel 4.14-rc8 is available (but not yet from the Ubuntu PPA). It reverts the change to the MHz line of /proc/cpuinfo that was introduced in kernel 4.13-rc1.

---

### Post by Doug S on 2017-11-12
> **Doug S said:**
> Kernel 4.14-rc8 is available (but not yet from the Ubuntu PPA). It reverts the change to the MHz line of /proc/cpuinfo that was introduced in kernel 4.13-rc1.Kernel 4.14 is available. The reversion to the MHz line of /proc/cpuinfo stuff from 4.14-rc8 has been reverted.

---

