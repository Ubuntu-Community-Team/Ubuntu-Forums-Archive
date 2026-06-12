---
title: "upgraded from karmic to lucid and now irssi won't run"
date: 2011-11-06
forum: Server Platforms
---

### Post by dinonet on 2011-11-06
I get this:

irssi: symbol lookup error: irssi: undefined symbol: g_malloc0_n

any ideas?

thanks!

---

### Post by clrg on 2011-11-06
I'm no expert, but it might be missing a library or the correct version of a library.

Are you sure irssi's dependencies are met? What happens when you 

```
sudo dpkg-reconfigure irssi
```?

---

### Post by dinonet on 2011-11-07
Hmm it doesn't seem to do anything. It just goes back to a prompt. Searching google I don't see too much on this problem. Is this a rare screw on my upgrade? :(

---

### Post by clrg on 2011-11-07
Hmm.

```
sudo apt-get install --reinstall irssi
```

---

### Post by dinonet on 2011-11-07
> **clrg said:**
> Hmm.

```
sudo apt-get install --reinstall irssi
```

It reinstalled it and supposedly replaced it but this stupid error keeps coming up when trying to start it up 

"irssi: symbol lookup error: irssi: undefined symbol: g_malloc0_n"

---

### Post by andrew.46 on 2011-11-08
I see that lucid backports has a newer version, have you enabled this? Looks like a library mismatch and perhaps install newer version might help...

---

### Post by dinonet on 2011-11-08
> **andrew.46 said:**
> I see that lucid backports has a newer version, have you enabled this? Looks like a library mismatch and perhaps install newer version might help...

No luck after doing that either :(

---

### Post by andrew.46 on 2011-11-08
> **dinonet said:**
> No luck after doing that either :(

Hmmm... that is a pity :(. Can you post the contents of your /etc/apt/sources.list? There could be a repository scramble and this will hopefully be seen there.

---

### Post by dinonet on 2011-11-08
> **andrew.46 said:**
> Hmmm... that is a pity :(. Can you post the contents of your /etc/apt/sources.list? There could be a repository scramble and this will hopefully be seen there.

Sure here it is. Sorry if I left the commented stuff. I guess this is after the upgrade from jaunty. Not sure if that even helps. 

# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

---

### Post by andrew.46 on 2011-11-08
Looks like all lucid repositories there although I don't see the lucid backports? Clean install rather than upgrade has always been  my choice I will have to admit and this usually gets around odd problems like this...

Perhaps compile your own copy? This will not solve any underlying problems but will certainly get irssi running. First back up your configuration files for irssi by running:

```

cp -rv $HOME/.irssi $HOME/.irssi_bak

```

Then remove irssi by using synaptic, then try the following single command:

```

sudo apt-get install build-essential checkinstall && \
sudo apt-get build-dep irssi && \
wget http://irssi.org/files/irssi-0.8.15.tar.bz2 && \
tar xjvf irssi-0.8.15.tar.bz2 && cd irssi-0.8.15 && \
./configure && make && \
sudo checkinstall --pkgname irssi --pkgversion 0.8.15 --default

```

Hopefully this will at least get you online with irssi...

---

### Post by dinonet on 2011-11-08
I had added lucid backports maybe it didnt paste here. I had: 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main universe multiverse restricted

You are right about doing a clean install. I guess it was part laziness and part having success with earlier versions in the past. I'm still sort of a newbie so I really appreciate the help. So I can understand what this command is doing are you basically downloading the latest version and compiling/installing again? I had done the apt-get remove and then reinstall which made no difference.

Thanks again!

---

### Post by andrew.46 on 2011-11-09
The commands I gave install compilers and a packaging utility called checkinstall. Also download the source from the irssi website and compile + install.

---

### Post by tr333 on 2011-11-09
[http://packages.ubuntu.com/search?keywords=irssi](http://packages.ubuntu.com/search?keywords=irssi) shows the current version of irssi in lucid-backports repository.
```
apt-cache policy irssi
``` will show the installed version of the irssi package and which repository it was installed from.

You can search the current bug reports for irssi in Launchpad (Ubuntu's bug tracking system) at [https://launchpad.net/ubuntu/+source/irssi/+bugs](https://launchpad.net/ubuntu/+source/irssi/+bugs). If your problem isn't already reported you might want to consider filing a bug report for irssi by running the command ```
ubuntu-bug irssi
``` in a terminal or the Run... dialog (alt+F2).

---

### Post by dinonet on 2011-11-09
Thanks. Of course I was using bitlbee too and that's broken. Could I do something similar for that? Maybe a clean install is in order.

---

### Post by tr333 on 2011-11-09
"g_malloc0_n" is from GLib, which is where I'm guessing the problem lies.

Try running "[ldd](http://manpages.ubuntu.com/manpages/lucid/en/man1/ldd.1.html) $(which irssi)" to find out which shared libraries the irssi binary is linking to.  You might have accidentally installed a separate copy of glib somewhere?  Maybe in /usr/local/lib/?  The system-installed glib should be in /lib/ not /usr/local/lib/.

This is what I get when running it from Ubuntu 11.10 (some version numbers might be different):
```
$ ldd $(which irssi)
        linux-vdso.so.1 =>  (0x00007fffd6eda000)
        libperl.so.5.12 => /usr/lib/libperl.so.5.12 (0x00007fabebbd2000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fabeb9b5000)
        libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007fabeb7b0000)
        libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007fabeb4ba000)
        libssl.so.1.0.0 => /lib/x86_64-linux-gnu/libssl.so.1.0.0 (0x00007fabeb269000)
        libcrypto.so.1.0.0 => /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 (0x00007fabeaeb9000)
        libncurses.so.5 => /lib/libncurses.so.5 (0x00007fabeac98000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fabea8f9000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fabea6f4000)
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fabea470000)
        libcrypt.so.1 => /lib/x86_64-linux-gnu/libcrypt.so.1 (0x00007fabea237000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fabebf4e000)
        libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007fabe9ffa000)
        librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fabe9df2000)
        libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fabe9bda000)
        libtinfo.so.5 => /lib/libtinfo.so.5 (0x00007fabe99b2000)

```

---

### Post by tr333 on 2011-11-09
Just found **[this bug report](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/591743)** for a different package, but with the same error.  The problem was resolved by finding and removing a separate copy of libglib-2.0 that had somehow found its way into /usr/local/lib/, which was causing incompatibilities with the normal libglib-2.0 from /lib/.

---

### Post by tr333 on 2011-11-09
> **dinonet said:**
> Thanks. Of course I was using bitlbee too and that's broken. Could I do something similar for that? Maybe a clean install is in order.

bitlbee also links to libglib which is probably why you're getting errors for that too.

---

### Post by dinonet on 2011-11-10
That helped fix everything. Thanks to all of you guys for helping me out!

---

### Post by tr333 on 2011-11-10
Don't forget to go to "Thread Tools" -> "Mark Thread Solved" when your problem is resolved :)

---

### Post by dinonet on 2012-01-19
Is upgrading from karmic to lucid that problematic? I keep getting this problem and now I get:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://us.archive.ubuntu.com/ubuntu/...86/Packages.gz) Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_multiverse_binary-i386_Packages - open (22: Invalid argument)

I keep having to remove libglib but it keeps coming back.

---

