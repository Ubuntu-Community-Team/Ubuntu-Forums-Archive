---
title: "dpkg-paranoia"
date: 2010-02-14
forum: Ubuntu Dev Link Forum
---

### Post by segooon on 2010-02-14
Hi folks.

I've written simple scripts to control installing  process.

From README:

> 
dpkg-paranoia

This little program sets hook on pre-installing  package. It
unpacks .deb file to /tmp/ and checks wether it satisfies
specified  rules (requirements of local policy). Already
created rules include  checks on:
   * setuid/setgid bit on executables
   * cron jobs
   * apparmor profiles
   * scripts those are executed on  install/remove
     (preinst/postinst, prerm/postrm)
   * changing  sysctl settings.

Run "chmod a-x /etc/dpkg-paranoia.d/checkXXX"  to disable checkXXX.

If installation is launched in  non-interactive mode and any of
above checks is failed then  installation fails.
If installation is launched in interactive mode  and any of
above checks is failed then user is given a prompt what to
do  with this suspicious package.

What it is and what it is not.
------------------------------
This  is NOT an anti-virus or anti-malware or smth like that.
Such type of  program cannot guarantee 100% protection.
Opposite, this program  audits downloaded packages on
matching _concrete_ policies. It report  admin that some
package doesn't satisfy local rules and that it  should be
verified manually. E.g. in case of using nonnative  distribution
repository (Ubuntu PPA or upstream) you are able to meet
with  such situation. Some maintainers think that they may
add their own  repositories to repos list or add their PGP
keys to trusted list.  Sometimes such actions are OK for
system, however, admin should be  noticed about them. Also
admin should know all system changes made by  installed
packages: adding users through install scripts, sysctl
settings,  etc.
I think it can be a good base for smth like repository checker or  checker on testing system.
Please, anybody who has an opinion - post  it here [IMG]http://forums.debian.net/images/smilies/icon_smile.gif[/IMG]

---

### Post by Linuxforall on 2010-02-16
Thank you, much needed at the institute where I deploy Ubuntu.

---

### Post by arrange on 2010-02-17
It's great, thanks.

I've put some more lines into the *scripts* script so that I can see the contents of the post*/pre* scripts and check their validity.```
...
for F in $SCRIPTS; do
    if [ -x DEBIAN/$F ]; then
        $WARN_CMD "Found $F script in $DEB_PACKAGE"
        echo -------------------------------
        cat DEBIAN/$F
        echo
        FOUND=1
    fi
done

[ $FOUND = 0 ]
```  
I have one problem though: if I choose **abort**, I get this error message```
Aborted.
E: Sub-process su -s `which dpkg-paranoia-hook` nobody returned an error code (1)
E: Failure running script su -s `which dpkg-paranoia-hook` nobody
```

When running out of paranoia, I get```
arrange@lean:/etc/dpkg-paranoia.d$ which dpkg-paranoia-hook
/usr/bin/dpkg-paranoia-hook
arrange@lean:/etc/dpkg-paranoia.d$ su -s /usr/bin/dpkg-paranoia-hook
Password: 
su: Authentication failure
arrange@lean:/etc/dpkg-paranoia.d$ su -s /usr/bin/dpkg-paranoia-hook nobody
Password: 
su: Authentication failure
arrange@lean:/etc/dpkg-paranoia.d$ grep nobody /etc/passwd
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
```

---

### Post by segooon on 2010-02-17
> **arrange said:**
> It's great, thanks.

I've put some more lines into the *scripts* script so that I can see the contents of the post*/pre* scripts and check their validity.
...

I thought that it would be more convenient to use (S)hell and explore DEBIAN/* by hands as it can be rather large.

> **arrange said:**
> I have one problem though: if I choose **abort**, I get this error message```
Aborted.
E: Sub-process su -s `which dpkg-paranoia-hook` nobody returned an error code (1)
E: Failure running script su -s `which dpkg-paranoia-hook` nobody
```When running out of paranoia, I get```
arrange@lean:/etc/dpkg-paranoia.d$ which dpkg-paranoia-hook
/usr/bin/dpkg-paranoia-hook
arrange@lean:/etc/dpkg-paranoia.d$ su -s /usr/bin/dpkg-paranoia-hook
Password: 
su: Authentication failure
arrange@lean:/etc/dpkg-paranoia.d$ su -s /usr/bin/dpkg-paranoia-hook nobody
Password: 
su: Authentication failure
arrange@lean:/etc/dpkg-paranoia.d$ grep nobody /etc/passwd
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
```
Unless you run "su" being root, it will demand your password. User nobody has no password, so even if you are allowed to run su, you are not able to enter its password.

You can freely run dpkg-paranoia-hook as common user. Script /etc/apt/apt.conf.d/... uses "su" to drop root privileges. Then it uses fakeroot to be able to create fake setuid/setgid files being nonroot. You can see it executing "touch /etc/x" - you will get "permission denied".

---

### Post by arrange on 2010-02-17
Hmm, I think I understand, but partially :)

[COLOR="Silver"]You can freely run dpkg-paranoia-hook as common user.[/COLOR]
I run the *apt-get install* from a root terminal. Still I get the error message. But the install aborts anyway, so I don't care really much...

---

### Post by segooon on 2010-02-18
> **arrange said:**
> 
I have one problem though: if I choose **abort**, I get this error message
```
Aborted.
E: Sub-process su -s `which dpkg-paranoia-hook` nobody returned an error code (1)
E: Failure running script su -s `which dpkg-paranoia-hook` nobody
```

If you enter "abort" then it aborts =) command abort == "stop it, i don't trust this package!".

Checks of all packages occur before the first "dpkg -i", so if there is an error in a single package then the rest won't be even checked - the "global" installation will fail. So, if you don't want to install a single package, not all, then you have to rerun "apt-get install" without this package.

---

### Post by arrange on 2010-02-18
OK. Thanks a lot for the clarification.

---

