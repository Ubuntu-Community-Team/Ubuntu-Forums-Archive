---
title: "Could not perform immediate config on exim4-daemon-light"
date: 2011-01-20
forum: Server Platforms
---

### Post by bennie91 on 2011-01-20
I'm more of a CentOS person, but after some issues on my new box I switched to Ubuntu server. 
I am working on getting it setup as a mail server (mainly for testing at the moment and soon be live). I performed apt-get install sendmail then apt-get install exim4 and got the message:

Could not perform immediate configuration on 'exim4-daemon-light'. Please see man 5 apt.conf under APT:: Immediate-Configure for details. 

I have Ubuntu Server 10.10 32-bit  on a Dell Intel Poweredge.

---

### Post by bennie91 on 2011-01-21
Anyone can help?

---

### Post by koenn on 2011-01-21
> 
       Immediate-Configure
           Defaults to on which will cause APT to install essential and
           important packages as fast as possible in the install/upgrade
           operation. This is done to limit the effect of a failing dpkg(1)
           call: If this option is disabled APT does treat an important
           package in the same way as an extra package: Between the unpacking
           of the important package A and his configuration can then be many
           other unpack or configuration calls, e.g. for package B which has
           no relation to A, but causes the dpkg call to fail (e.g. because
           maintainer script of package B generates an error) which results in
           a system state in which package A is unpacked but unconfigured -
           each package depending on A is now no longer guaranteed to work as
           their dependency on A is not longer satisfied. The immediate
           configuration marker is also applied to all dependencies which can
           generate a problem if the dependencies e.g. form a circle as a
           dependency with the immediate flag is comparable with a
           Pre-Dependency. So in theory it is possible that APT encounters a
           situation in which it is unable to perform immediate configuration,
           errors out and refers to this option so the user can deactivate the
           immediate configuration temporarily to be able to perform an
           install/upgrade again. Note the use of the word "theory" here as
           this problem was only encountered by now in real world a few times
           in non-stable distribution versions and was caused by wrong
           dependencies of the package in question or by a system in an
           already broken state, so you should not blindly disable this option
           as the mentioned scenario above is not the only problem immediate
           configuration can help to prevent in the first place. Before a big
           operation like dist-upgrade is run with this option disabled it
           should be tried to explicitly install the package APT is unable to
           configure immediately, but please make sure to report your problem
           also to your distribution and to the APT team with the buglink
           below so they can work on improving or correcting the upgrade
           process.



questions ?

---

### Post by Dleonard0 on 2011-01-30
> **koenn said:**
> questions ?

Yes. WTF?

I hit the same problem uninstalling sendmail and trying to install exim4-daemon-light.

[indent]E: Could not perform immediate configuration on 'exim4-daemon-light'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)[/indent]

The solution turned out to be to first
[indent]# apt-get install exim4-base exim4-config[/indent]
then
[indent]# apt-get install exim4-daemon-light[/indent]

---

### Post by koenn on 2011-01-30
looks like the dependencies are not handled correctly

---

### Post by ergosteur on 2011-02-11
Thanks for this.
Had the same problem on my new 10.10 server. I wonder if a bug should be filed?

---

### Post by pehden on 2011-06-10
FOUND FIX 

sudo apt-get install sendmail




it will remove postfix and it works for reinstalling it
im not trying to use exim4 though so if you are then my fix might not work for you.

---

### Post by xeorex on 2011-07-10
I fixed it doing this:

$ apt-get purge mail*
This shows the packages that are going to be removed
Now it is a matter of removing these packages without installing exim4.

$ dpkg --force-all -r sendmail-cf
$ dpkg --force-all -r sendmail-bin
$ dpkg --force-all -r sendmail-base

After this I was able to run this again:

$ apt-get purge mail*
$ apt-get -f install

That removed the packages left and installed exim4 in place.
rkhunter was the package causing problem to me.

Reconfigure exim4:

$ dpkg-reconfigure exim4-config

But got this message:

Stopping MTA for restart:.
Restarting MTA: exim4.
ALERT: exim paniclog /var/log/exim4/paniclog has non-zero size, mail system possibly broken ... failed!

Fixed this by deleting paniclog:

$ rm /var/log/exim4/paniclog

Then again:

$ dpkg-reconfigure exim4-config

And finally got this:

Stopping MTA for restart:.
Restarting MTA: exim4.

This was on a Debian 6 squeeze though but I hope it helps.

---

### Post by eode on 2012-09-28
I don't know if this will work for Ubuntu, but this problem was killing me.  I finally found that installing exim4-base first works.  It took me a long time to find.  Since I found this thread early in my search, and I use Ubuntu a lot, I figured I'd post it here for anyone who needs it.

```
sudo apt-get install exim4-base
sudo apt-get install exim4
```

Credit:
[http://forum.linode.com/viewtopic.php?p=39352](http://forum.linode.com/viewtopic.php?p=39352)

---

