---
title: "gpg compression (and automation)"
date: 2015-10-04
forum: Security
---

### Post by maclenin on 2015-10-04
Does gpg compress the target file (by default) when used in this way?
```
$ gpg -c file.tar
```
```
$ gpg -c file.txt
```
If so, does gpg require the *--compress-level 0* option to ensure compression does not occur, no matter how gpg is deployed? For example:
```
$ gpg -c --compress-level 0 file.tar
```
I am looking to automate an encryption process and am endeavoring to suss the ground rules.

Thanks for any guidance.

---

### Post by Lars Noodén on 2015-10-04
The [-c option is short for the --symmetric option](http://manpages.ubuntu.com/manpages/trusty/en/man1/gpg.1.html), so it won't affect compression.  By default it gpg does not add compression.  But yes, setting *--compress* to 0 disables compression in GnuPG.  I'd use a separate compression tool anyway.

---

### Post by maclenin on 2015-10-04
Thanks for the reply.

I think I was just tossed a bit by the gpg man page (and wanted to be certain, as I do NOT want compression):

> *--compression-level n*
...

A value of 0 for n disables compression.

Why would you offer an option for disabling something if it wasn't enabled by default?

Perhaps, to allow for (easier) cycling through a variety of compression levels in an automated encryption process where diff. file types, archiving and compression algorithms are involved (...why not offer 0, too)?

---

### Post by Lars Noodén on 2015-10-04
Sorry.  I misread it.  

Also, after having tested it, it does look like gpg does compress by default.  A large text file encrypted with no compression options is much, much smaller than the same file encrypted with "-z 0"

---

### Post by sudodus on 2015-10-04
If I understand encryption correctly, it makes it harder to decrypt, if compression is used. I think compression is built into the gpg method.

---

### Post by Lars Noodén on 2015-10-04
It's also described in the specification itself:
[https://tools.ietf.org/html/rfc4880#section-2.3](https://tools.ietf.org/html/rfc4880#section-2.3)

Though it's a little unclear in the manual page, testing it shows a big difference in file size.  Here z is a copy of x
```

$ ls -l x z
-rw-rw-r-- 1 lars lars 10039 Oct  4 17:07 x
-rw-rw-r-- 1 lars lars 10039 Oct  4 17:08 z
$ gpg -c x; gpg -c -z 0 z
$ ls -l x.gpg z.gpg 
-rw-rw-r-- 1 lars lars   114 Oct  4 17:34 x.gpg
-rw-rw-r-- 1 lars lars 10077 Oct  4 17:34 z.gpg

```

---

### Post by maclenin on 2015-10-04
why does (1/2) the opposite seem true for me?
```
$ gpg -c test
$ ls -l
-rw-rw-r-- 1 user user 26 Oct  4 16:41 test
-rw-rw-r-- 1 user user 65 Oct  4 16:42 test.gpg
```

```
$ gpg -c - z 0 test0
$ ls -l
-rw-rw-r-- 1 user user 29 Oct  4 16:53 test0
-rw-rw-r-- 1 user user 69 Oct  4 16:54 test0.gpg
```

---

### Post by Lars Noodén on 2015-10-04
> **maclenin said:**
> why does the opposite seem true for me?


Probably because it is so small.  Try with a larger file.

---

### Post by maclenin on 2015-10-04
here's a more substantive example:
```
$ gpg -c test.xml.tar
289854636 test.xml.tar
290333201 test.xml.tar.gpg
```
as if a wrapper is being placed around the file - no compression here....

---

### Post by Lars Noodén on 2015-10-04
Yes, there is overhead in both encryption and compression.  Regular content is more easy to compress than more noisy, randomish data.  

> **maclenin said:**
> here's a more substantive example:
```
$ gpg -c test.xml.tar
289854636 test.xml.tar
290333201 test.xml.tar.gpg
```
as if a wrapper is being placed around the file - no compression here....

Then try making a copy of 'test.xml.tar' and encrypting it with compression level 0 in gpg.

---

### Post by maclenin on 2015-10-04
I think I understand what may be happening. Do I need sudo to run gpg (properly)?

---

### Post by Lars Noodén on 2015-10-04
Each account has its own keyring(s).  sudo is not desirable, it would point gpg at the root account's keyring instead of the one for your account.

---

### Post by maclenin on 2015-10-04
the gpg config file has root permissions, though it's sitting in my user's ~/ folder.... How should I modify? By the way - I did a re-run of the same tests sudo (on a larger file) and the normal -c process cut the file size in 1/2, whereas the -z 0 placed a wrapper around....

---

### Post by Lars Noodén on 2015-10-04
> **maclenin said:**
> the gpg config file has root permissions, though it's sitting in my user's ~/ folder.... How should I modify? 

You mean the ones in ~/.gnupg right?  You can change ownership of a file with [chown](http://manpages.ubuntu.com/manpages/trusty/en/man1/chown.1.html).

```

sudo chown maclenin:maclenin *somefile*

```

Same for directories.  The gnupg files in your account should be owned by your account and in your group.

---

### Post by maclenin on 2015-10-05
I was thinking chown - however, shouldn't /root also have its own .gnupg configuration files (in /root, created after first sudo-invoked gpg)?

.gnupg appeared in ~/ after the first non-sudo invocation of gpg - but with root permissions. Hmm.

Perhaps, the question is how does one configure gpg for multiple users?

---

### Post by Lars Noodén on 2015-10-05
root should have it's own but...

sudo leaves some of the environment variables unchanged.  The variable $HOME is one of them.  Compare the output from these:
```

env
sudo env
sudo -H env
sudo -i env

```

So if you start a program for the first time with sudo instead of plain, some of the configuration files will end up in the right place but owned by root by mistake.  If you really want root with no leftovers from the old account, then [sudo -i](http://manpages.ubuntu.com/manpages/trusty/en/man8/sudo.8.html) is the way to go.  There are a lot of options you can set in [/etc/sudoers/](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) in regards to handling of environment variables.

So to use GnuPG with another account, log in (fully) to that other account and things should work.  [gpg](http://manpages.ubuntu.com/manpages/trusty/en/man1/gpg.1.html) also has some options in regards to pointing to other home directories or keyrings, but it probably better to do a full login.

---

### Post by maclenin on 2015-10-05
I think the issue may lie buried in this "re-enactment":

1. user logged into user@user*
2. user@user invoked gpg for the first time ever on the system (root or non-root) - and without sudo
3. user home directory was populated with a root-privileged .gnupg directory

*can you clarify what you mean by "fully" logged-in?

---

### Post by Lars Noodén on 2015-10-05
Fully, by using "su -l" or "sudo -i" followed by the username for a non-root user or left blank for root.  

Step #3 should not (could not) happen without using sudo, as far as I understand.  When I've had new accounts, running gpg for the first time does not create anything owned by root unless I use sudo with it.

---

### Post by maclenin on 2015-10-05
thanks for sticking with this....

The issue does seem permissions-related. As I recall errors similar to [these]("http://ubuntuforums.org/showthread.php?t=1236084") when "user" first ran gpg (from within the user@user "env").

However, I am still stumped as to why user (having logged into user@user) would NOT enjoy the permission(s) to run gpg?

As I read it, according to this [link]("https://wiki.archlinux.org/index.php/GnuPG#GNUPGHOME") and excerpt... > Only the owner has permissions to read, write and access (r, w, x)....user (within user@user) IS the "owner", by definition? No?

I see what you mean re: "sudo env", which was probably the issue re: ~/.gnupg ending up in the user home directory, with root permissions....

However - still stumped. Why would this command (within env)...```
user@user$ gpg -c test
```...give user (the owner) permissions errors?

---

### Post by Lars Noodén on 2015-10-05
> **maclenin said:**
> 
However - still stumped. Why would this command (within env)...```
user@user$ gpg -c test
```...give user (the owner) permissions errors?

Probably some file or directory still needs to be changed to have the right owner.  Can you give more details about the error?  It will probably tell which one is the problem.

---

### Post by maclenin on 2015-10-05
Here are the error and permissions details - reproduced on a different machine (14.04)....

NB: The .gnupg folder on this different machine - prior to my first-ever run of gpg - was (is) also located in the "user" folder and also owned by root - see "ll" below.... Perhaps this is the default setting?

```
user@user:~/Desktop/gpg_test$ gpg -c test
gpg: failed to create temporary file `/home/user/.gnupg/.#lk0x162df90.user.9603': Permission denied
gpg: keyblock resource `/home/user/.gnupg/pubring.gpg': general error
gpg: can't open `/home/user/.gnupg/random_seed': Permission denied
gpg: note: random_seed file not updated
user@user:~/Desktop/gpg_test$ 
```
```
root@user:~/.gnupg# ll
drwx------  2 root   root 4096 ./
drwxr-xr-x 68 user user 4096 ../
-rw-------  1 root   root  9398 gpg.conf
-rw-------  1 root   root  0 secring.gpg
-rw-------  1 root   root  1200 trustdb.gpg

```
P.S. The other machine - about which I originally posted is 12.04....

---

### Post by Lars Noodén on 2015-10-05
Ok.  The inability to make a file in the directory shows that even the directory has the wrong permissions.  It looks like it might be ownership.  That can be set back to the right user and group with chown, recursively.  

```

sudo chown -R user:user /home/user/.gnupg/

```

Then "user" should be able to use that accounts OpenPGP keyring and stuff.

---

### Post by maclenin on 2015-10-05
Yep - chown is a solution - however, the lingering fact that root is set up by default (in both 12.04 and 14.04) as the .gnupg owner in the user directory - strikes me as odd - and could be a [bug]("http://support.gpgtools.org/discussions/problems/10490-gnupg-created-by-root")? Though I am having difficulty finding any substantive discussion on the matter....

---

### Post by Lars Noodén on 2015-10-05
If it happens consistently with all your new accounts, without using sudo, then it might be a bug.  I'm not able to find a way to duplicate your problem here though and so am not much help in getting to the root of the problem, no pun intended.

---

### Post by maclenin on 2015-10-05
enough sed...thanks!

UPDATE: third time was the strange charm, for some reason. Managed to scrape together a third machine - running 14.04 - man page indicated the presence of gpg, but there was no .gnupg in the user home directory. So, I ran gpg - in the usual way:
```
user@user:~/Desktop/gpg_test$ gpg -c test
gpg: directory `/home/user/.gnupg' created
gpg: new configuration file `/home/user/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/user/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/user/.gnupg/pubring.gpg' created
Enter passphrase: 

```
...lo and behold the following .gnupg directory then appeared:
```
user@user:~/.gnupg# ll
drwx------  2 user   user 4096 ./
drwxr-xr-x 68 user  user 4096 ../
-rw-------  1 user   user 9398 gpg.conf
-rw-------  1 user   user  0 pubring.gpg
-rw-------  1 user   user  1200 randomo_seed
```

The second time I ran gpg with the -c option a gui dialog popped-up to ask me for a passphrase - no output in the terminal - and the file was encrypted.

I was also able to delete .gnupg and then rebuild it with a fresh run of gpg - perhaps, this is the solution to the previous two enigmas?

Curiouser and curiouser....

---

### Post by Lars Noodén on 2015-10-05
> **maclenin said:**
> 
I was also able to delete .gnupg and then rebuild it with a fresh run of gpg - perhaps, this is the solution to the previous two enigmas?


That works, but just as a backup it is often better to just rename the directory to not.gnupg or something else.  Also, your key(s) are in the keyrings so if you want to save them, you'll need to export them before moving or deleting the directory.  But if you've not got any keys, go for it.

---

### Post by maclenin on 2015-10-05
...gpg and ssh are separate animals?

---

### Post by Lars Noodén on 2015-10-05
> **maclenin said:**
> ...could the state of the (root) permissions of .gnupg have anything to do with the fact that I've [generated ssh keys]("http://ubuntuforums.org/showthread.php?t=1791213&p=10997411#post10997411") on this machine (12.04)? This may be the answer....

If you copied the whole .gnupg directory as root, that might do it.  Permissions and ownership can change when copying if you don't set -p for cp and -a for rsync. But OpenSSH is very separate from GnuPG and there is no overlap in the configurations or data.  So the keys of one would have no effect on the keys of the other.

---

### Post by maclenin on 2015-10-05
...ok - so removing the .gnupg folder and "resetting gpg" - as I describe earlier - should have no impact on ssh.... I am just wondering what other processes might have affiliated themselves with gpg - to "raise" the .gnupg permission level.... Thanks, again, for sticking with this....

---

### Post by Lars Noodén on 2015-10-05
Removing the .gnupg folder and "resetting gpg" should have no impact on opensssh.  The only two packages that I know of that use ~/.gnupg would be gnupg and gnupg2.  There can be others, like Enigmail, that call one of those but even then once the directory and files are created they aren't going to change owner.  So if they are root, it is most likely happening during the first run for that  account.

---

### Post by maclenin on 2015-10-06
I will test the purge and rebuild - and report back....

In the meantime - still wondering re: permissions - as all other directories in ~/ remain friendly to its user!

UPDATE: the purge and rebuild worked on the other 14.04 machine (where .gnupg had been root previously). Permissions were (re)set to those of user at rebuild. I also ran a sudo gpg (from user@user) which did NOT change the permissions profile of ~/.gnupg - but did give me an "unsafe ownership on configuration file" warning - which makes sense, because user is now the rightful owner (in this "env")!

...still...still wondering how root got control of .gnupg lo those many posts ago....

Thanks, again.

---

