---
title: "Is it possible to install NON threaded version of Perl??"
date: 2007-05-15
forum: Repositories &amp; Backports
---

### Post by amesdaq on 2007-05-15
Hello Everyone,
Pretty new to Ubuntu but I love it so far. One of the best things about it (debian packages) is also starting to be one of my pains. What I want to do is install a non threaded version of Perl on the server. Why would I want that? Well I am in a high performance high availability enviorement and the threaded version of perl is not the best for the libraries we use. I uninstalled perl-base and perl and had to go through some prompts just to do it. Then I installed from source but then I had packages not working like deb-conf or something. 

So my question is what is the proper way to do this? Is there a way to install the non threaded version via packages? Is there a way to just gracefully replace it without breaking stuff?

Any help is welcome.
Thanks

---

### Post by mlind on 2007-05-16
Here's one way to do it

[LIST]
[*]Add source repository to */etc/apt/sources.list* for getting the perl source package (it's in the main component)
```

deb-src http://archive.ubuntu.com/ubuntu feisty **main**

```

[*]Get the source package
```

mkdir /tmp/perl
cd /tmp/perl
sudo aptitude update
apt-get source perl

```
[*]Remove -Dusethreads from the build flags (you probably want to do this manually with some editor like nano. Just comment out the line using # or remove it. I used sed to remove the line)
```

cd perl*
sed -i '/usethreads/d' debian/config.debian

```
[*]Bump the version a little
```

sudo aptitude install devscripts
dch -i

```

[*]sample changelog entry
> 
perl (5.8.8-7build1+custom1) feisty; urgency=low

  * Disable threads

 -- Firstname Lastname <youremail@somehost>  Wed, 16 May 2007 19:37:19 +0300


[*]Build the package
```

cd /tmp/perl
sudo aptitude install dpkg-dev
dpkg-source -b perl-5.8.8
sudo pbuilder build perl_5.8.8-7build1+custom1.dsc

```
[/LIST]

Use pbuilder or sbuild to build the binaries. You can check my sig for pbuilder howto.

I hope this helps a little. You basically just check out the Ubuntu's debianized source package for perl, modify the build flags and recompile it. Version bump allows you and package manager to distinguish packages easier. 

I didn't try this myself, and I'm not sure if -Dusethreads is the right option to remove, but it sounded like one (I just grepped the files in debian directory and found that entry).
You can easily downgrade the package using synaptic/aptitude/apt-get. Just bump the version so it's probably easier.

---

### Post by amesdaq on 2007-05-16
Hey this is great I will check this method out. It seems like exactly what I wanted. I assume that all dependencies will also be resolved with this method?

---

### Post by mlind on 2007-05-17
> **amesdaq said:**
> Hey this is great I will check this method out. It seems like exactly what I wanted. I assume that all dependencies will also be resolved with this method?

yes, pbuilder contains a script that automatically resolves all dependencies and does the build stuff in a sandbox.

---

### Post by ajbaerg on 2008-04-02
Thank you very much for these instructions. I have successfully built a non-threaded perl for ubuntu server 6.06

One problem I ran into was that some config scripts from the debconf package (adduser in my case) no longer worked and generated the following error:

[INDENT]/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/Locale/gettext/gettext.so: undefined symbol: Perl_Gthr_key_ptr[/INDENT]

I had to reinstall the following perl modules using cpan (force install):

[INDENT]Locale::gettext
Text::CharWidth
Text::Iconv
Text::WrapI18N[/INDENT]

This was due to the fact that the following are dependencies for debconf.

[INDENT]liblocale-gettext-perl
libtext-charwidth-perl
libtext-iconv-perl
libtext-wrapi18n-perl[/INDENT]

Hope this helps someone.

Thanks again.

---

