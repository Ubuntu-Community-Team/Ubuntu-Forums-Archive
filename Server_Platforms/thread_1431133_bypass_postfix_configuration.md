---
title: "bypass postfix configuration"
date: 2010-03-16
forum: Server Platforms
---

### Post by cong06 on 2010-03-16
I'm trying to script some installs, all of which include postfix.

I have the postfix configuration already copied, so I would like to find a command so that on installation of postfix, it skips prompting me and just installs without any configurations.

Is there a way to set this with dpkg?

---

### Post by KB1JWQ on 2010-03-16
Could always try passing --refuse with a postinst argument; see man dpkg for examples of how this works.

---

### Post by cong06 on 2010-03-17
> **KB1JWQ said:**
> Could always try passing --refuse with a postinst argument; see man dpkg for examples of how this works.

I don't see any that would do it that aren't already disabled...
```

root@kimende-s:/# dpkg --force-help
dpkg forcing options - control behaviour when problems found:
  warn but continue:  --force-<thing>,<thing>,...
  stop with error:    --refuse-<thing>,<thing>,... | --no-force-<thing>,...
 Forcing things:
  all [!]                Set all force options
  downgrade [*]          Replace a package with a lower version
  configure-any          Configure any package which may help this one
  hold                   Process incidental packages even when on hold
  bad-path               PATH is missing important programs, problems likely
  not-root               Try to (de)install things even when not root
  overwrite              Overwrite a file from one package with another
  overwrite-diverted     Overwrite a diverted file with an undiverted version
  bad-verify             Install a package even if it fails authenticity check
  depends-version [!]    Turn dependency version problems into warnings
  depends [!]            Turn all dependency problems into warnings
  confnew [!]            Always use the new config files, don't prompt
  confold [!]            Always use the old config files, don't prompt
  confdef [!]            Use the default option for new config files if one
                         is available, don't prompt. If no default can be found,
                         you will be prompted unless one of the confold or
                         confnew options is also given
  confmiss [!]           Always install missing config files
  breaks [!]             Install even if it would break another package
  conflicts [!]          Allow installation of conflicting packages
  architecture [!]       Process even packages with wrong architecture
  overwrite-dir [!]      Overwrite one package's directory with another's file
  remove-reinstreq [!]   Remove packages which require installation
  remove-essential [!]   Remove an essential package

WARNING - use of options marked [!] can seriously damage your installation.
Forcing options marked [*] are enabled by default.

```


It could be a "--force-" option, but I don't see which one.
I'm already using "--force-confdef --force-confold"

---

### Post by cong06 on 2010-04-13
bump.

It's rather annoying since I managed to get it working for sun-java (auto-accepting the license) but I can't get it to default to "no configuration" on postfix...

---

### Post by KB1JWQ on 2010-04-13
Hmm.  If you set the debconf frontend to non-interactive, that SHOULD do it.  With apt-get, supposedly -y will do it.

Any luck?

---

### Post by cong06 on 2010-04-14
I'm not sure if I understand what you mean, but based off your second statement:
> 
With apt-get, supposedly -y will do it.

I think you might not understand what's going on...


So to clarify, I here are all the options I'm passing to aptitude:
```

aptitude --assume-yes \
    -o Dpkg::Options::--force-confdef \
    -o Dpkg::Options::--force-confold \
    -o Dpkg::Options::--auto-deconfigure \
    -o Dpkg::Options::--force-depends \
    -o Dpkg::Options::--refuse-downgrade \
    -o Dpkg::Options::--skip-same-version \
    install postfix

```
Note: Alot of these aren't needed, as Aptitude manages them. However, these dpkg options are also used for running dpkg by itself, so these options are used for both Aptitude and dpkg to make my script cleaner. (maybe later I'll clean it up a bit)

For Sun Java the fix was this:
```

echo "sun-java6-jre shared/accepted-sun-dlj-v1-1 select true" | /usr/bin/debconf-set-selections 

```

To more clearly understand the type of prompt I'm getting, please view the attached screenshot (from: [http://www.basicconfig.com/ubuntu/postfix_configuration](http://www.basicconfig.com/ubuntu/postfix_configuration))
Note that because of the size of my screen, this one prompt actually has two screens: 1 to read the explanations (and then an OK to go on), and then one to choose.

Also see the "install.txt" file. It is the bash script I use to install all the software that I'm using. You can attempt to run the script yourself and see what I'm talking about, though probably a simple:
```

aptitude install postfix

```
would do it too.

---

### Post by cong06 on 2010-04-19
Anyone have contact details for the person in charge of putting together the postfix deb?

Or will I have to compile?

---

