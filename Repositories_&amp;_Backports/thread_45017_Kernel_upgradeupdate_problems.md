---
title: "Kernel upgrade/update problems"
date: 2005-06-28
forum: Repositories &amp; Backports
---

### Post by blaylock on 2005-06-28
Hi, I was wondering if anyone is having an issue with updating the kernel from the default install kernel. 2.6.10-5 i think.

So far, I have had updates for the kernel "supposedly" installed via the ubuntu update program and synaptic. But uname still shows 2.6.10-5 running, and there are no other entries in Grub to choose from at boot. 

I have rebooted a few times after an update but there is no new kernel. Synaptic says that 2.6.10-7 is the Installed and Latest version of linux-386, and 2.6.10-34.3 is the Installed and Latest version of linux-image.

Im used to using yum in Fedora and when there is a kernel upgrade it automatically updates Grub to show this. 

Is there something extra i need to do to make the new kernel available or are the updates applied to the existing kernel as patches?

Im not new to Linux but i am new to debian so Im probably missing something.

Any help is appreciated.

Oh, btw uname -a gives me this:
Linux methane 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux

I noticed the Jun 24 compile date which is well after the date of installation so maybe the updates have been applied?

---

### Post by Xian on 2005-06-28
I know this is a little confusing but it is just the way that the kernel packages are named that is causing this misconception. I am confident that you have successfully installed the newest version.

To illustrate this let's assume that we have a package in Synaptic that is named foo-2.6.10-5. The developers have decided that this package name will stay the same even though there are small version bumps. If there were to be a major version change then the package name would be modified as well, but only under those circumstances. 

Which means you can have the following possibilities:
```

_Package Name_      _Installed Version_        _Latest Version_
foo-2.6.10-5           foo-2.6.10-34             foo-2.6.10-34
```
And then a month later...
Notice the version change with no alteration to the package name.
```

_Package Name_      _Installed Version_        _Latest Version_
foo-2.6.10-5           foo-2.6.10-42             foo-2.6.10-42
```
Then you have the corresponding meta-pkg that has another name which seems to be unrelated to its own dependent packages. For example, assume we have a meta-package named foo-386 in Synaptic that corresponds to foo-2.6.10-5 and has a version number of 2.6.10-7. The setup would look something like this:
```

_Meta-Package Name_     _Dependent Package_       _Latest Version_
 foo-386                          foo-2.6.10-5                     2.6.10-7
```
So, basically what we want to see is that when we click to install foo-386 it will call upon version 2.6.10-7, and this should in turn pull the package foo-2.6.10-5 which refers to version 2.6.10-34. If all this takes place then everything is in order.

Let's test this idea. Find the package 'linux-image-686' in Synaptic.
Note that the version number of this package is 2.6.10-7.
Right click on it and select 'Mark For Installation'
A window will appear showing that linux-image-2.6.10-5-686 will be installed.
Click 'Cancel' to abort the install.

Next let's go to the package 'linux-image-2.6.10-5-686'
Note that the version number of this package is 2.6.10-34.3
Right click on it and select 'Properties'.
Notice that the 'Latest Available Version' doesn't match the pkg version name.
But they are one and the same.

Let's now check the vmlinuz link which will always refer to the latest kernel.
Navigate to the '/' directory in your file browser.
Find the file named 'vmlinuz'.
Right-Click on it, select properties.
You can see that it refers to the 2.6.10-5 name.
This in turn matches the 'kernel 2.6.10-5' notation in your menu.lst.

---

### Post by blaylock on 2005-06-29
Thanks Xian, I understand now.

Looks like the original name stays and it becomes a pointer to the newest image file.

Kinda weird but I guess i can live.

 :)

---

### Post by ajgreeny on 2005-11-24
OK Thanks Xian.

Certainly confusing for us new linux users, but now you have spelled it out it starts to make sense.

Double confusion for me as I have two separate partitons with Hoary and breezy on them, (I'd got Hoary working brilliantly and didn't trust an upgrade so put Breezy separate) and of course that means two versions of menu.lst, hence my edit of one of them.  Not a disaster as I can always put things right but certainly means I have to keep my wits about me whenever I do a kernel upgrade.

Thanks again for the explanation.

---

