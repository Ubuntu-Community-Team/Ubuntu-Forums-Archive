---
title: "Virtualbox issues! after cancel installation. on feisty (7.04)"
date: 2007-05-27
forum: Virtualisation
---

### Post by Grizzil on 2007-05-27
I get this message error when I start the ubuntu updater :
"Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.' "
I get this message error when I start the updater....
I cant reinstall it .

I try Automatix and I got this error when trying to install Virtualbox:
"FATAL ERROR: Virtualbox
An apt-based error occured and installation was unsuccessful"
:(

I try to install Virtualbox and I cancel the setup wizard and then this mess came up  Help plz....
Ps:sorry for my english I usually speak french.

---

### Post by chrisLACHCIK5084 on 2007-05-27
goto system->admin->synaptic 

(make sure terminal isn't running at this time)

click on status at the bottom (if it isn't already) and click on Not Installed (Local or Obsolete)

Find virtualbox or the command it uses and click in the box to the left of it and click "mark for complete removal"

hopefully that works if you haven't already tried that. then reinstall virtualbox. it's an awesome program and i love it! goes fast and smooth!

---

### Post by Grizzil on 2007-05-27
> **chrisLACHCIK5084 said:**
> goto system->admin->synaptic 

(make sure terminal isn't running at this time)

click on status at the bottom (if it isn't already) and click on Not Installed (Local or Obsolete)

Find virtualbox or the command it uses and click in the box to the left of it and click "mark for complete removal"

hopefully that works if you haven't already tried that. then reinstall virtualbox. it's an awesome program and i love it! goes fast and smooth!

I can't run the synaptic package manager everytime I try I get this error "E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

---

### Post by Medieval_Creations on 2007-05-27
You will have to remove the broken package in order to clear this up probably.

I don't know how automatix installs it, but I know you should be able to remove it from the CLI.  I'm pretty sure the command is:
```
sudo dpkg -r VirtualBox
```

Then try running synaptic or apt-get update see if that fixes it.
Virtual box isn't in the repositories yet.  Just download it from teh VBox site and try installing that deb.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by bodhi.zazen on 2007-05-27
I have seen this problem before with virtualbox and the only solution I have found is to complete the installation of virtualbox ...

I do not know why but this seems to happen when people abort the install ???

```
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_feisty_i386.deb
```

Complete the install and all should be good again.

After the install you can then remove virtualBox if you so desire.

---

### Post by Grizzil on 2007-05-28
The solution was "sudo dpkg --remove --force-remove-reinstreq virtualbox"
and then I was able to reinstall Virtualbox .

Tanks for your help.

---

### Post by meg23 on 2007-11-15
Thanks! That fixed my problem.

---

