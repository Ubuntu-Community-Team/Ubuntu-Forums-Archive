---
title: "What happens to configuration when doing automatic update"
date: 2005-12-13
forum: Server Platforms
---

### Post by diebels on 2005-12-13
I'm running a daily script to keep my server updated:
"apt-get dist-upgrade -y"

What does debconf do here? :
Setter opp courier-base (0.47-3ubuntu1.4) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype

I guess it installs the package with the default answers to questions. If there are new config files they don't get installed.

I'd like to run a diff between new and old config files, to see if there are important changes. Is the new config file that doesn't get installed unpacked somewhere, or do I have to extract it from the deb in /var/cache/apt/archives/ ?

---

### Post by jim1960 on 2006-04-15
I have the same problem too.
If have update services like postfix/apache...,
then these services dead, won't restart,
and have to restart in the console.

---

### Post by az on 2006-04-15
Why do you use the -y switch?

---

### Post by LordHunter317 on 2006-04-15
You can't do what you want that way, so don't even try.  You must manually do upgrades.

---

### Post by jim1960 on 2006-04-15
So ubuntu can't do auto upgrade by cron? It's too bad.

---

### Post by fdoving on 2006-04-16
This is how it works:

If no modification has been done to the config file, dpkg will simply replace the old config file from the old package, with the new config file, from the new package.

If you have made changes to the config file you will be asked what to do. Unless you use -y or something similar to go with the default. If you use -y and later want to know what has been done, you can figure it out by looking at the extensions of the config files.

As an example: /etc/pbuilderrc.dpkg-dist is the 'distribution' config file for pbuilder. .dpkg-dist files are the default config files from the package. If you choose not to replace the existing modified one. This is the result. 'configfile.dpkg-dist'

If I choose to replace my old config with the new one from the package. The old one gets the extension .dpkg-old. 
Example: hdparm.conf.dpkg-old is my old and manually modified hdparm.conf. 


- Frode

---

### Post by LordHunter317 on 2006-04-16
[QUOTE=fdoving]This is how it works:

If no modification has been done to the config file, dpkg will simply replace the old config file from the old package, with the new config file, from the new package.[/quote]Nope, you're talking about a different situation, using UCF.  This can be *somewhat* automated.

Debconf cannot be trivially automated due to it's design.  It asks generic questions and runs generic scripts in response to the answers.  It is not a configuration file mechanism.

Debian and Ubuntu lack a generic mechanism (AFAIK) to create an answer file to replay on installation, or a way to defer questions in all situations (since for many packages, the questions must be answered for the package to function.

---

### Post by fdoving on 2006-04-16
[QUOTE=LordHunter317]Nope, you're talking about a different situation, using UCF.  This can be *somewhat* automated.

Debconf cannot be trivially automated due to it's design.  It asks generic questions and runs generic scripts in response to the answers.  It is not a configuration file mechanism.

Debian and Ubuntu lack a generic mechanism (AFAIK) to create an answer file to replay on installation, or a way to defer questions in all situations (since for many packages, the questions must be answered for the package to function.[/QUOTE]
You must be talking about installation and configuration during installation. I'm talking about upgrading installed packages. The question was: 
[QUOTE=diebels] 
I'd like to run a diff between new and old config files, to see if there are important changes. Is the new config file that doesn't get installed unpacked somewhere, or do I have to extract it from the deb in /var/cache/apt/archives/ ? 
[/QUOTE]

That is what I answered.

---

### Post by LordHunter317 on 2006-04-16
[QUOTE=fdoving]You must be talking about installation and configuration during installation. I'm talking about upgrading installed packages.[/quote]Debconf can and will run on upgrades.

> That is what I answered.Yes, you answered that, but the problem is that question has nothing to do with the error he encountered, which is my point; people often get the two confused, and it is important to understand the difference.  debconf has nothing to do with configuration files per se, and you cannot automate APT because there's  no practical way to automate debconf.

---

