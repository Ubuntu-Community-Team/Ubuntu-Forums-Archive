---
title: "Any experience with CentOS?"
date: 2011-12-23
forum: The Cafe
---

### Post by trivialpackets on 2011-12-23
I'm pushing for the funding for a Red Hat certification at work, so I'm going to be installing CentOS 6.2 this weekend and was curious if anyone has any experience with it or any of the Red Hat/CentOS releases?  

I have to say that over the years, I've run a number of distros, but never CentOS, so this should be different.

---

### Post by CharlesA on 2011-12-23
*raises hand*

Have you used Fedora at all? It's the same basic thing - package management and architecture is the same between the two.

---

### Post by trivialpackets on 2011-12-23
I used Fedora for a short stint, but that was quite a few years ago.  We run Red Hat on some of our servers at work, so I'm hoping I can push and get this paid by the company.  At least it's more interesting to me than Windows certs.

---

### Post by CharlesA on 2011-12-23
Haha. Grab the netinstall ISO and check it out.

They seem to have quite a bit in their repos, but not as much as Debian, or so it seems.

---

### Post by collisionystm on 2011-12-23
I have a CentOS Server at work. It runs 5.2? I think

It is very stable and I have had ZERO issues with it. ( knocks on wood )

The Repo's are pretty bare ( for me ) and you cannot add fedora repo's.

I do not play with it much because its the heart of our business. There are always atleast 30 people on it at any moment between 6:00 a.m. -5:00 lol. Good luck

---

### Post by snowpine on 2011-12-23
I use it daily. For server use it is one of the best. For desktop use you have to really like slightly outdated software and/or have the skills to update applications from outside the official repos.

I've never taken the Red Hat certs but I've heard CentOS is totally interchangeable as an educational tool.

---

### Post by collisionystm on 2011-12-23
> **snowpine said:**
> 

I've never taken the Red Hat certs but I've heard CentOS is totally interchangeable as an educational tool.

I think it is. From my understanding it is an exact copy of Red Hat...or at least everything that could be copied under the GNU which I am pretty sure is 99%

Red Hat just offers their official support and repo's for updates, which to a lot of companies makes it worth the bucks.

---

### Post by trivialpackets on 2011-12-23
The only absolute NEED I have for my linux box is for rails development, so if I can get the necessary files on there to run RVM then I'll be good to go.

---

### Post by Dangertux on 2011-12-23
If you're used to RHEL or Fedora. CentOS should be a breeze. We use RHEL where I work and it's pretty straight forward. 

The RedHat documentation also applies and is VERY thorough - [http://docs.redhat.com/docs/](http://docs.redhat.com/docs/)

Also good luck with RHCE it's a great cert to have. It's actually on my todo list, at my employers demand not my own. 

Hope this helps.

---

### Post by trivialpackets on 2011-12-23
Yeah, although I was totally wrong.  The one thing I can't go without is wireless...so I'll be digging a bit to get it working.  :D  Is it too early to say, "I miss you ubuntu"?  ;)

---

### Post by snowpine on 2011-12-23
> **eric.proctor said:**
> Yeah, although I was totally wrong.  The one thing I can't go without is wireless...so I'll be digging a bit to get it working.  :D  Is it too early to say, "I miss you ubuntu"?  ;)

You asking for help or just sayin'?

If the former then a good first step would be to tell us your wireless chipset. :)

---

### Post by 3Miro on 2011-12-23
Red Hat and Centos == Lots of Stable but Outdated Software.

Had CentOS at work and I was upset because not only the software was old compared to Ubuntu, but I also didn't have root access and couldn't install additional things. Other than that, it was rock solid.

As other people said, try both CentOS and Fedora under both standalone and/or VirtualBox.

---

### Post by snowpine on 2011-12-23
> **3Miro said:**
> Had CentOS at work and I was upset because not only the software was old compared to Ubuntu...

Comparable to Ubuntu LTS.

---

### Post by 3Miro on 2011-12-23
> **snowpine said:**
> Comparable to Ubuntu LTS.

The CentOS Software is older than Ubuntu LTS. Look at distrowatch.com

Currently CentOS comes with Gnome 2.28, while Ubuntu 10.04 comes with 2.30. Some packages are more recent, like Xorg 1.10, and the kernel is the same version for both, but overall CentOS is behind Ubuntu LTS (not to mention that we are 4 months away from the next LTS that would be pretty current).

---

### Post by collisionystm on 2011-12-24
> **3Miro said:**
> Red Hat and Centos == Lots of Stable but Outdated Software.

Had CentOS at work and I was upset because not only the software was old compared to Ubuntu, but I also didn't have root access and couldn't install additional things. Other than that, it was rock solid.

As other people said, try both CentOS and Fedora under both standalone and/or VirtualBox.


In CentOS, Debian, OpenSuse and other distro's that are not built around the 'sudo' command, the method to obtain root access is quite simple.

Login as root.
Or from a terminal, su root

If you choose to use sudo

su root
yum install sudo

add your user account to the sudoers file /etc/sudoers

Keep in mind, you cannot lock the root account like Ubuntu because it is needed to run synaptic in debian, yast in opensuse and synaptic in CentOS.


CentOS 6 has very recent software and it should detect wireless and ethernet just fine. A good rule of thumb with any server is to run Intel hardware because Intel packs their drivers into the linux kernels. They are, in my experience, the providers of the best linux compatible hardware.

Cheers

---

### Post by snowpine on 2011-12-24
> **3Miro said:**
> The CentOS Software is older than Ubuntu LTS. Look at distrowatch.com

Currently CentOS comes with Gnome 2.28, while Ubuntu 10.04 comes with 2.30. Some packages are more recent, like Xorg 1.10, and the kernel is the same version for both, but overall CentOS is behind Ubuntu LTS (not to mention that we are 4 months away from the next LTS that would be pretty current).

I don't need to look at distrowatch because I use CentOS every day for work. 

Many package versions are shared between CentOS and Ubuntu LTS; some are 0-6 months newer in CentOS and some are 0-6 months newer in Ubuntu LTS. 

On a long-term-support distro with 5-7 years' support, 0-6 months is pretty darn close. That is why I said:

> **snowpine said:**
> Comparable to Ubuntu LTS.

and not

> **snowpine said:**
> Exactly the same as Ubuntu LTS.

My intention was to give an Ubuntu user who's never used CentOS before a general impression of what to expect. It was not my intention to encapsulate the entirety of distrowatch.com, the distros' own documentation, and the actual experience of using said distros into a single 4-word sentence. :)

---

### Post by CharlesA on 2011-12-24
> **collisionystm said:**
> In CentOS, Debian, OpenSuse and other distro's that are not built around the 'sudo' command, the method to obtain root access is quite simple.

Login as root.
Or from a terminal, su root

If you choose to use sudo

su root
yum install sudo

add your user account to the sudoers file /etc/sudoers

Keep in mind, you cannot lock the root account like Ubuntu because it is needed to run synaptic in debian, yast in opensuse and synaptic in CentOS.

Yep. I've been debating on installing sudo, since it would make it easier for me to install stuff/do updates as a normal user, but maybe that's just me being lazy. :p

I suppose tip #1 would be to have a super strong root password (Isn't that a given?) and to not allow root logins via ssh since you can always su to root or use sudo if you have that set up.

---

### Post by collisionystm on 2011-12-24
> **CharlesA said:**
> Yep. I've been debating on installing sudo, since it would make it easier for me to install stuff/do updates as a normal user, but maybe that's just me being lazy. :p

I suppose tip #1 would be to have a super strong root password (Isn't that a given?) and to not allow root logins via ssh since you can always su to root or use sudo if you have that set up.


lol I install sudo.

The good part about ssh is you can easily restrict its access with hosts.allow/deny.

---

### Post by 3Miro on 2011-12-24
> **collisionystm said:**
> In CentOS, Debian, OpenSuse and other distro's that are not built around the 'sudo' command, the method to obtain root access is quite simple.

Login as root.
Or from a terminal, su root

If you choose to use sudo

su root
yum install sudo

add your user account to the sudoers file /etc/sudoers

Keep in mind, you cannot lock the root account like Ubuntu because it is needed to run synaptic in debian, yast in opensuse and synaptic in CentOS.

I know that, it is just that I wasn't given root access to the machine in my office. This means no su or sudo or even yum.

> 
CentOS 6 has very recent software and it should detect wireless and ethernet just fine. A good rule of thumb with any server is to run Intel hardware because Intel packs their drivers into the linux kernels. They are, in my experience, the providers of the best linux compatible hardware.

Cheers

CentOS 6 and Ubuntu LTS will not run with Intel Sandy Bridge graphics. You will need a more recent kernel than 2.6.32. Wireless would probably be fine, but depending on the model that may cause trouble too.

---

### Post by CharlesA on 2011-12-24
> **collisionystm said:**
> lol I install sudo.

The good part about ssh is you can easily restrict its access with hosts.allow/deny.

That's true. I usually just set PermitRootLogin to either "no" or "without-password" and set AllowUsers to whoever should have ssh access.

TCPwrappers is a good way to do it too. :)

---

### Post by cap10Ibraim on 2011-12-24
currently I'm using Scientific Linux 6.1 on my laptop another RedHat based distro , feels good, calm and solid 
I always follow the tutorials and docs targeted for Redhat and CentOS because it's the same
most major software I use such as servers you can add a repo 
for firefox I just download it from their website and setup a launcher , eclipse too 
java.rpm so easy to install 
it comes with support for non-free codecs

---

