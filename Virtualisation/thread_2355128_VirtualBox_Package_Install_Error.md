---
title: "VirtualBox Package Install Error"
date: 2017-03-09
forum: Virtualisation
---

### Post by opulido on 2017-03-09
I am using VirtualBox on a Windows 10 Host machine. Cut and Paste is not working between the host and guess systems. I have enabled the share clipboard bidirectional. I am running the following command in order to fix the cut and paste issue based on a post I found over the internet.

sudo apt-get install virtualbox-*

and I am getting the following error:

```
omar@omar-VirtualBox:~$ sudo apt-get install virtualbox-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'virtualbox-source' for glob 'virtualbox-*'
Note, selecting 'virtualbox-guest-utils' for glob 'virtualbox-*'
Note, selecting 'virtualbox-ose' for glob 'virtualbox-*'
Note, selecting 'virtualbox-guest-modules' for glob 'virtualbox-*'
Note, selecting 'virtualbox-guest-additions-iso' for glob 'virtualbox-*'
Note, selecting 'virtualbox-guest-dkms' for glob 'virtualbox-*'
Note, selecting 'virtualbox-dkms' for glob 'virtualbox-*'
Note, selecting 'virtualbox-ext-pack' for glob 'virtualbox-*'
Note, selecting 'virtualbox-guest-source' for glob 'virtualbox-*'
Note, selecting 'virtualbox-ose-fuse' for glob 'virtualbox-*'
Note, selecting 'virtualbox-qt' for glob 'virtualbox-*'
Note, selecting 'virtualbox-2.0' for glob 'virtualbox-*'
Note, selecting 'virtualbox-2.1' for glob 'virtualbox-*'
Note, selecting 'virtualbox-2.2' for glob 'virtualbox-*'
Note, selecting 'virtualbox-modules' for glob 'virtualbox-*'
Note, selecting 'virtualbox-3.0' for glob 'virtualbox-*'
Note, selecting 'virtualbox-3.1' for glob 'virtualbox-*'
Note, selecting 'virtualbox-3.2' for glob 'virtualbox-*'
Note, selecting 'virtualbox-4.0' for glob 'virtualbox-*'
Note, selecting 'virtualbox-4.1' for glob 'virtualbox-*'
Note, selecting 'virtualbox-4.2' for glob 'virtualbox-*'
Note, selecting 'virtualbox-4.3' for glob 'virtualbox-*'
Note, selecting 'virtualbox-5.0' for glob 'virtualbox-*'
Note, selecting 'virtualbox-5.1' for glob 'virtualbox-*'
Note, selecting 'virtualbox-dbg' for glob 'virtualbox-*'
Note, selecting 'virtualbox-guest-x11' for glob 'virtualbox-*'
Note, selecting 'virtualbox-guest-additions' for glob 'virtualbox-*'
Note, selecting 'virtualbox-dkms' instead of 'virtualbox-modules'
virtualbox-dkms is already the newest version (5.0.32-dfsg-0ubuntu1.16.04.2).
virtualbox-dkms set to manually installed.
virtualbox-guest-dkms is already the newest version (5.0.32-dfsg-0ubuntu1.16.04.2).
virtualbox-guest-utils is already the newest version (5.0.32-dfsg-0ubuntu1.16.04.2).
virtualbox-guest-utils set to manually installed.
virtualbox-qt is already the newest version (5.0.32-dfsg-0ubuntu1.16.04.2).
virtualbox-qt set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 virtualbox-dbg : Depends: virtualbox (= 5.0.18-dfsg-2ubuntu1) but 5.0.32-dfsg-0ubuntu1.16.04.2 is to be installed or
                           virtualbox-guest-utils (= 5.0.18-dfsg-2ubuntu1) but 5.0.32-dfsg-0ubuntu1.16.04.2 is to be installed
 virtualbox-guest-x11 : Depends: xserver-xorg-core (>= 2:1.17.99.902)
E: Unable to correct problems, you have held broken packages.
```

I hope someone can guide me on this.

Regards, Omar

---

### Post by &amp;KyT$0P# on 2017-03-09
> **opulido said:**
> Cut and Paste is not working between the host and guess systems. I have enabled the share clipboard bidirectional. I am running the following command in order to fix the cut and paste issue based on a post I found over the internet.

sudo apt-get install virtualbox-*
That post gave you terrible advice.  It is installing *way* more stuff than necessary.

The best way to fix Cut and Paste is this.  Go to Devices > Insert Guest Additions CD Image.  Inside the Ubuntu guest, you should then see a CD icon.

If it doesn't prompt about automatically running something, open a Terminal in the CD's directory and run
```
sudo apt-get install build-essential dkms
sudo ./VBoxLinuxAdditions.run
```

If that's successful, reboot your guest and you should be good.

---

### Post by ajgreeny on 2017-03-09
I completely agree with halogen2; that advice and what it told you to do installed a gross overload of packages, and I would like to see that site where you found the recommendation to run that command, because frankly, it is the wrong way to do it.

What version of VBox have you installed and if you have installed the Guest Additions, which version of those, as it must be the same version of both.  I think you have 5.0.32 of both but I'm just checking.

You must also make sure that you, as user, are added to the **vboxsf** group in your guest Ubuntu OS with command ```
sudo adduser omar vboxsf
``` I assume you have username omar according to your first post.

---

### Post by opulido on 2017-03-09
Thanks Halogen2 and Ajgreeny. It is working now. Now, all the stuff that was installed with the advice given before (sudo apt-get install virtualbox-*) ... should I look for a way to remove it?

Regards

---

### Post by &amp;KyT$0P# on 2017-03-09
Sure, this should do -
```
sudo apt-get purge 'virtualbox-*'
```
Then reboot the guest.

Depending what had been installed, you may then have to repeat the steps we outlined above.

[HR][/HR]

Like ajgreeny, I too am curious where you saw the advice to run that install command.  If you still have the link, could you please share it?

---

### Post by ajgreeny on 2017-03-10
If you run ```
sudo apt-get purge 'virtualbox-*'
``` it will remove all your current virtualbox packages so you will then have to reinstall whichever version of the main package that you want.

I am using VBox 5.1.16 which I installed and update using the repository direct from the VBox website.
Scroll down to the Debian-based Linux distributions section of [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) for details of how to do that; it makes life easier and I have had no problems with the 5.1 versions.

---

### Post by &amp;KyT$0P# on 2017-03-10
> **ajgreeny said:**
> If you run ```
sudo apt-get purge 'virtualbox-*'
``` it will remove all your current virtualbox packages so you will then have to reinstall whichever version of the main package that you want.
What main package?  Their host is Windows, and in my experience an Ubuntu guest doesn't need any special virtualbox packages.

---

### Post by opulido on 2017-03-10
Thanks guys. Unfortunately, I do not have the link anymore. Regards

---

### Post by ajgreeny on 2017-03-11
> **halogen2 said:**
> What main package?  Their host is Windows, and in my experience an Ubuntu guest doesn't need any special virtualbox packages.
Whoops! You're right; there is no need to install anything from the repositories in your guest to get VBox to work for you.

That's what comes of forgetting that some people have Windows as host and Ubuntu as guest, along with my lack of knowledge of Windows any more.

---

