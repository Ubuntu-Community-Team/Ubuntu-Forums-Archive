---
title: "apt-get broken after manually upgrading trac"
date: 2007-03-28
forum: Server Platforms
---

### Post by bluefossil on 2007-03-28
Hi,

I had manually upgraded Trac to version 0.10.3-1 since Dapper Drake only came with 0.9.x. But after doing that, I realised that my apt-get is broken. For example, when I try to install sendmail, I get this error:

```
The following packages have unmet dependencies:
  python-support: Depends: python (>= 2.4.3-10) but 2.4.2-0ubuntu3 is to be installed
  sendmail: Depends: sendmail-base (= 8.13.5-3ubuntu1) but it is not going to be installed
            Depends: sendmail-bin (= 8.13.5-3ubuntu1) but it is not going to be installed
            Depends: sendmail-cf (= 8.13.5-3ubuntu1) but it is not going to be installed
            Depends: sensible-mda (= 8.13.5-3ubuntu1) but it is not going to be installed
            Depends: rmail (= 8.13.5-3ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I know trac and python and all the stuff are working fine right now, so I have searched around and found that I could probably use Fake-Provides in order to get apt-get to work like this:

```

RPM
{
Fake-Provides {"package version";};
}

```

The problem is, I don't know what exactly to indicate within those braces. Anyone can help me out here? Or has anyone got a better solution to this?

Any help would be very much appreciated. Thanks!

---

### Post by huygens on 2007-03-30
why don't you try what apt-get is suggesting you? I-e: execute:
```
sudo apt-get -f install
```

It should clean up your database.

---

### Post by bluefossil on 2007-04-02
Yes, that would clear up the database, but would also cripple the new Trac installation, which is something I'm trying to avoid.

---

### Post by az on 2007-04-02
> **bluefossil said:**
> Yes, that would clear up the database, but would also cripple the new Trac installation, which is something I'm trying to avoid.

You are not using a version of that package that is build for your version of Ubuntu.  It *is* broken and you just haven't noticed it yet.

Find the source packages for that package and build it using your version of Ubuntu's toolchain and dependencies and you are good to go.  That's the correct way to solve the problem.  The package manager is trying to solve the problem - making the package manager ignore the problem is not the correct solution.

---

