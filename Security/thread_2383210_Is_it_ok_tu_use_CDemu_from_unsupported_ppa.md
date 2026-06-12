---
title: "Is it ok tu use CDemu from unsupported ppa?"
date: 2018-01-22
forum: Security
---

### Post by smith73 on 2018-01-22
Is it ok to use CDemu from unsupported ppa [https://launchpad.net/~cdemu/+archive/ubuntu/ppa](https://launchpad.net/~cdemu/+archive/ubuntu/ppa)  ?

---

### Post by cruzer001 on 2018-01-22
I don't know what it does, but its been maintain since 12.04 (last update 7 weeks ago).  I would feel good about it.

---

### Post by smith73 on 2018-01-22
CDemu is an .iso image mounting software to mount .isos at a virtual cd/dvdrom. 
As it is not supported in Ubuntu repositories it can't be removed by autoremove function, but the aforementioned site says © 2004-2018 Canonical Ltd,
so I don't understand how a software is not supported by Ubuntu repositories and is supported by Canonical for such a long time.
I'm new to Ubuntu software.

I was successfully using CDemu for mounting .iso images in Virtualbox in Ubuntu-Mate 16.04.3, until I noticed unusual browser activity
and got a terrific Tiger security suite report containing Ebory Windigo, linux image inconsistencies, etc. (taking into account that I enabled ufw, installed clamav, etc)

[URL="http://canonical.com/"]
[/URL]

---

### Post by coffeecat on 2018-01-22
> **smith73 said:**
> 
As it is not supported in Ubuntu repositories it can't be removed by autoremove function, but the aforementioned site says © 2004-2018 Canonical Ltd,
so I don't understand how a software is not supported by Ubuntu repositories and is supported by Canonical for such a long time.


CDemu isn't supported by Canonical. It's not in one of the Canonical supported repositories. That's why it's in a PPA - PPA standing for **personal** package archive.

The © 2004-2018 Canonical Ltd copyright notice refers to the launchpad.net website, not that particular PPA page. Launchpad does a lot more than just host PPA pages. You can get an idea of the scope and range of Launchpad from its home page: [https://launchpad.net/](https://launchpad.net/)

---

### Post by QIII on 2018-01-22
launchpad.net does not support nor does it bear any responsiblity for any particular PPA or its contents, either.

---

### Post by deadflowr on 2018-01-22
Unsupported means the PPA maintainer is only uploading the packages.
So the packages will be as is and any problems it has the maintainers won't do anything about.
Is it safe or okay to use? I'd have to say indeterminate. That would be something only you can tell.
Though I do not think I have seen anyone complain about any malicious activity related to cdemu from the PPA.
So in that regard you could probably at least trust it's a clean package.

---

### Post by Habitual on 2018-01-22
I posted the method I'm familiar with in your other post. :)

I left [https://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/](https://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/)

Good luck, but Have fun.

You don't need CDEmu to install Windows in VBox.

---

### Post by smith73 on 2018-01-22
So Canonical hosts a page with CDemu ppa's for several years and during this time CDemu is still proclaimed unsupported. How to interpret that? Is there something to the ppa that prevents its support by Canonical or Ubuntu community and incorporation into apt-cache search? CDemu performed its function ok.

---

### Post by QIII on 2018-01-22
Let me recapitulate coffeecat's statement with some emphasis:  "That's why it's in a PPA - PPA standing for ***personal*** package archive."

Neither Canonical, Ltd., nor the Ubuntu community, are under any obligation, implied or expressed, to take up support of the contents of someone's PPA.

---

### Post by deadflowr on 2018-01-22
> Is there something to the ppa that prevents its support by Canonical or Ubuntu community and incorporation into apt-cache search?
It would need an Ubuntu/Debian developer to take on the role of a maintainer and so far none have.
They've tried here:
[https://bugs.launchpad.net/ubuntu/+bug/105452]("https://bugs.launchpad.net/ubuntu/+bug/105452")
But it's telling that a developer gave up from this comment:
[https://bugs.launchpad.net/ubuntu/+bug/105452/comments/10]("https://bugs.launchpad.net/ubuntu/+bug/105452/comments/10")

FTR: once any repository is added to your system it is automatically added to the apt search function.
So if you have the ppa, the packages in the ppa will be searchable.

---

### Post by coffeecat on 2018-01-22
@smith73, concerning PPAs let me direct you to a rather old Ubuntu documentation page, but one that I believe is still accurate:

[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)

To save you having to click on that link, here is the text as it stands at the moment. Please read it:

> A PPA is a Personal Package Archive, and is a method of distributing software to users, without requiring developers to undergo the full process of distribution in the main ubuntu repositories.

PPAs can be used to extend the available software in ubuntu to both programs that are not otherwise available in ubuntu, as well as to allow newer versions, such as beta programs, that have not yet undergone sufficient testing to be imported into the main archive.

Security

PPAs have not undergone the same process of validation as regular ubuntu packages. End users install PPAs at their own risk. Although each key is cryptographically signed, in order to confirm an uploader, keys are not matched to specific individuals, except via their "launchpad" accounts.

Subsequently, installing a PPA should be considered to be a low-security alternative as compared to the main repository, but marginally higher security than simply installing software at random from the internet. As part of adding a PPA, you trust the developer to not only install packages, but also to allow them to provide ongoing updates. 

I believe that goes some way towards answering your original question, as well as addressing your misunderstanding of where PPAs lie within the Ubuntu ecosystem.

---

### Post by smith73 on 2018-01-24
> **deadflowr said:**
> 

FTR: once any repository is added to your system it is automatically added to the apt search function.
So if you have the ppa, the packages in the ppa will be searchable.

After installing CDemu ppa and typing sudo apt-get autoremove cdemu (or gcdemu) it does nothing. It doesn't autoremove CDemu.
While installing anything from the repositories it notifies that you can autoremove the package installed.

---

### Post by smith73 on 2018-01-24
> **coffeecat said:**
> 

I believe that goes some way towards answering your original question, as well as addressing your misunderstanding of where PPAs lie within the Ubuntu ecosystem.

Ok, thanks. I'm new to Ubuntu. I wouldn't care about this CDemu ppa if I'd just install Windows and Ubuntu 16.04.3 on Virtualbox in Ubuntu-Mate 16.04.3.

---

### Post by slickymaster on 2018-01-24
> **smith73 said:**
> After installing CDemu ppa and typing sudo apt-get autoremove cdemu (or gcdemu) it does nothing. It doesn't autoremove CDemu.
While installing anything from the repositories it notifies that you can autoremove the package installed.
To remove a PPA from your system you use the **--remove** flag, similar to how the PPA was added```
sudo add-apt-repository --remove ppa:ppa_name
```
You can alternatively use the package **ppa-purge** and then remove the PPA, and downgrade the packages it provided to packages provided by official repositories
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa_name
```This will uninstall the packages provided by ppa_name, but won't uninstall those provided by the official repositories.

Regarding the apt-get options, you used, they do work but only for packages installed via the package manager which wasn't the case in point since CDemu was installed through a PPA. I'd recommend a read at the man pages for apt-get, which you can access by issuing the following command in a terminal window```
man apt-get
```

---

