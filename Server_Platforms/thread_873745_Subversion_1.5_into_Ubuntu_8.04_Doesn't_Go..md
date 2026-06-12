---
title: "Subversion 1.5 into Ubuntu 8.04 Doesn't Go."
date: 2008-07-29
forum: Server Platforms
---

### Post by seffyroff on 2008-07-29
I can't find a solution to this, other than installing a different OS, which would appear simpler than any of the following:

* Building Subversion 1.5 from source.  I attempted this.  Incompatibilities with Apr and Apr-Utils required that they be compiled from source first.  They in turn required a bunch of other stuff to be compiled from source.  And so on.  I gave up at that point.

* Backporting the Intrepid packages.  I got as far as running pbuilder on the intrepid .dsc (which performed tests for almost an hour), it was unclear whether this action had succeeded or failed, and the next steps in the Ubuntu Packaging Guide documentation drifted off into the realms of theory, speculation and fantasy at this point.

* Downloading someone else's pre-built binaries.  There's a few folks out there who have performed whatever dark ritual is required to produce working .debs, but apparently only for i386.  I'm on amd64.

* Following half-suggestions from confusing posts to mailing lists and vague hand-waving on forums in response to the problem.

Am I being unreasonable to assume that a significant upgrade to an industry standard piece of software should integrate trivially with the leading Linux distro?  If anyone can suggest something I've missed which offers a solution to this I'm all ears.

---

### Post by Cylindric on 2008-07-29
I also eagerly await a constructive reply to this question!

"apt-get install subversion" would be nice, but any sort of compilable source or installable package would be awesome too...

---

### Post by seffyroff on 2008-07-29
I found someone else who had backported the Intrepid package on his own repository here:

[https://launchpad.net/~clazzes.org/+archive]("https://launchpad.net/~clazzes.org/+archive")

Add that repo to your /etc/apt/sources.list then apt-get install subversion works :)

---

### Post by tinny on 2008-07-29
Any reason why you are not happy with subversion 1.4? I think you would be more than happy with 1.4....

Another option could be to download the subversion 1.5 rpm and use alien to convert it to a deb...

Subversion 1.5 rpm
[http://www.collab.net/downloads/subversion/redhat.html](http://www.collab.net/downloads/subversion/redhat.html)

Ubuntu Alien
[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

---

### Post by Cylindric on 2008-07-30
> **tinny said:**
> Any reason why you are not happy with subversion 1.4? I think you would be more than happy with 1.4....What?  I don't see that as a valid answer to "how do I get 1.5 working?" The question wasn't "should I?", so we should assume the need was already determined.

There are lots of reasons.  Such as Merge Tracking,  Sparse checkouts and all the other stuff at [http://subversion.tigris.org/svn_1.5_releasenotes.html](http://subversion.tigris.org/svn_1.5_releasenotes.html) testing, or maybe just plain old curiosity.

> **tinny said:**
> Another option could be to download the subversion 1.5 rpm and use alien to convert it to a deb...Unfortunately it's just not that easy.  And anyway, how is that easier than adding a repository and just using "apt-get install subversion"?

---

### Post by tinny on 2008-07-30
> **Cylindric said:**
> What?  I don't see that as a valid answer to "how do I get 1.5 working?" The question wasn't "should I?", so we should assume the need was already determined.

There are lots of reasons.  Such as Merge Tracking,  Sparse checkouts and all the other stuff at [http://subversion.tigris.org/svn_1.5_releasenotes.html](http://subversion.tigris.org/svn_1.5_releasenotes.html) testing, or maybe just plain old curiosity.

Unfortunately it's just not that easy.  And anyway, how is that easier than adding a repository and just using "apt-get install subversion"?

Sorry for trying to help.... > exit

---

### Post by tinny on 2008-07-30
But before I do go heres the answer to your question.

You need "Pinning":

[http://aldeby.org/blog/index.php/mixing-hardy-stable-and-intrepid-testing-repositories.html](http://aldeby.org/blog/index.php/mixing-hardy-stable-and-intrepid-testing-repositories.html)

Once you have the intrepid repository setup you will have access to the version 1.5 intrepid build of Subversion.

---

### Post by Alex Dinamo on 2008-08-04
> **tinny said:**
> Sorry for trying to help.... > exit

I hope you don't take this personal, but I have also ran into this kind of trouble previously on Ubuntu IRC, for instance, where people try to change my mind into using what Ubuntu offers right out of the box instead of a newer version I need.

And it is sometimes ridiculous trying to explain. Or plain complex. And sometimes you have to trust people when they say they need something. Not all Ubuntu users are young kids coming from Windows.

---

### Post by m4c0 on 2008-08-06
> **Alex Dinamo said:**
> I hope you don't take this personal, but I have also ran into this kind of trouble previously on Ubuntu IRC, for instance, where people try to change my mind into using what Ubuntu offers right out of the box instead of a newer version I need.

And it is sometimes ridiculous trying to explain. Or plain complex. And sometimes you have to trust people when they say they need something. Not all Ubuntu users are young kids coming from Windows.

+1

Why I must give reasons to use SVN 1.5? It is like explaining American Airlines why I want to buy the flying ticket and, after buying, I still need to configure my b*** to fit to the seat (maybe build the seat, too).

I only want to download SVN 1.5 and use. I followed the instructions posted by tinny, but it didn't worked for subversion. I added the archive repository to services.list. After a lot of trial-and-error, I put intrepid with all packages (*) and priority 2000. But it didn't work. I've lost 2 hours to do I've done in 5 minutes on Windows.

BTW, I use Linux since 1999 - a RedHat 5.3 downloaded with a 28800bps dial-up modem - I'm not a newbie, but I only want to fly - no explanations, no configurations, no compiling.

---

### Post by tinny on 2008-08-06
> **m4c0 said:**
> +1

Why I must give reasons to use SVN 1.5? It is like explaining American Airlines why I want to buy the flying ticket and, after buying, I still need to configure my b*** to fit to the seat (maybe build the seat, too).

I only want to download SVN 1.5 and use. I followed the instructions posted by tinny, but it didn't worked for subversion. I added the archive repository to services.list. After a lot of trial-and-error, I put intrepid with all packages (*) and priority 2000. But it didn't work. I've lost 2 hours to do I've done in 5 minutes on Windows.

BTW, I use Linux since 1999 - a RedHat 5.3 downloaded with a 28800bps dial-up modem - I'm not a newbie, but I only want to fly - no explanations, no configurations, no compiling.

People are just trying to help around here, by donating their free time to answer threads. You would be surprised how many times you get a noob who just blindly wants the least version without actually knowing what is going on.

Kicking people for trying to help is not the way things are done around here.

---

### Post by Imaginationac on 2008-08-11
> **seffyroff said:**
> I found someone else who had backported the Intrepid package on his own repository here:

[https://launchpad.net/~clazzes.org/+archive]("https://launchpad.net/~clazzes.org/+archive")

Add that repo to your /etc/apt/sources.list then apt-get install subversion works :)
Exactly what I was looking for!

---

### Post by jturner on 2008-08-11
> **tinny said:**
> Sorry for trying to help.... > exit

Harsh-mellows... everyone needs to chill for a minute. That being said, here's a strong use-case for Subversion 1.5: Eclipse support for SVN is provided by a plugin called Subclipse. The current version of Subclipse requires Subversion 1.5.

---

### Post by cronos6 on 2008-08-12
> **seffyroff said:**
> I found someone else who had backported the Intrepid package on his own repository here:

[https://launchpad.net/~clazzes.org/+archive]("https://launchpad.net/~clazzes.org/+archive")

Add that repo to your /etc/apt/sources.list then apt-get install subversion works :)

Hi,

 I added this 2 lines in my [FONT="Courier New"]/etc/apt/sources.list[/FONT]
[COLOR="Gray"]deb [http://ppa.launchpad.net/clazzes.org/ubuntu](http://ppa.launchpad.net/clazzes.org/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/clazzes.org/ubuntu](http://ppa.launchpad.net/clazzes.org/ubuntu) gutsy main[/COLOR]

then, [FONT="Courier New"]aptitude update && aptitude install subversion[/FONT]
[COLOR="Gray"]Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[/COLOR]

  How force it to install subversion 1.5? It will also update my SVN Apache module?

  Thanks by advance

---

### Post by robadob on 2008-08-15
Added to my apt repo sources list:

```
deb http://ppa.launchpad.net/clazzes.org/ubuntu gutsy main
```

And did:

```
apt-get update

apt-get dist-upgrade
```

Confirm that you want to use the unsigned/trusted packages for subversion/svn

Tada, 1.5 successfully installed.

Note:
It wouldn't install the 1.5 subversion when I tried just doing an apt-get update subversion.

---

### Post by cronos6 on 2008-08-16
Allright, I will try this ;)

 Thanks you

---

### Post by felixtz on 2008-08-28
Many thanks to clazzes.org. The backport worked here on Ubuntu 64, Hardy Heron.

To summarize and update the instructions for installing subversion svn 1.5 on Ubuntu Hardy Heron 64-bit:


Add to the end of /etc/apt/sources.list:

[INDENT][FONT="Courier New"]deb [http://ppa.launchpad.net/clazzes.org/ubuntu](http://ppa.launchpad.net/clazzes.org/ubuntu) hardy main[/FONT]
[/INDENT]

[FONT="Courier New"]sudo apt-get update
sudo apt-get dist-upgrade
[/FONT]

Confirm that you want to use the unsigned/trusted packages for subversion/svn.


If you are using a WinDOS "file:///" repository to store the working copy, cd to the working copy's directory and, for example:

[INDENT][FONT="Courier New"]svn switch --relocate file:///X:/subversion_repositories/this_project      file:///home/me/linux_path_to_X_colon/subversion_repositories/this_project[/FONT]
[/INDENT]

(That's all on one command line.)

To update or commit (or whatever) the same working copy under WinDOS you will need to "svn switch" the working copy's (.svn/entries) repository URL back to the WinDOS path.

Which is all by way of answering the earlier question in this thread of "Why go to svn 1.5?" Answer: Because the working copy is being managed with TortoiseSVN, which is currently at 1.5.

---

### Post by devman on 2008-09-02
Just wanted to report the clazzes.org repository worked for me as well, I got SVN 1.5 up and running in Hardy Server 64-bit.

---

### Post by tone77 on 2008-09-04
clazzes.org worked great on Hardy 32-bit...yea subversion 1.5

---

### Post by tinny on 2008-09-11
Subversion 1.5 is now available in the hardy backports repository.

[http://packages.ubuntu.com/hardy-backports/subversion](http://packages.ubuntu.com/hardy-backports/subversion)

---

### Post by daveappendix on 2008-09-18
As a backports newbie, I was a bit lost at first, but got this working finally by:

1. enabling hardy-backports in /etc/apt/sources.list

2. pinning backports to a lower priority of 400 by writing the following in /etc/apt/preferences

```

Package: *
Pin: release a=hardy-backports
Pin-Priority: 400
```

3. install subversion 1.5

```
sudo apt-get -t hardy-backports install subversion
```

The -t is the key, it temporarily boosts the priority of backports repository so that apt looks there first for this particular installation.

---

### Post by justifiedandancient on 2008-09-26
Having installed subversion 1.5.1 from the hardy backports into AMD 8.04 it should be noted that there is a known bug that it doesn't work with SSL certificates. There is documented workaround posted here: [https://lists.ubuntu.com/archives/ubuntu-backports/2008-September/009158.html](https://lists.ubuntu.com/archives/ubuntu-backports/2008-September/009158.html). I used solution 2. that involves swapping the libraries around. I am about to attempt a similar thing on 7.10 i386.

---

### Post by corvi42 on 2009-01-28
> **cronos6 said:**
> Hi,

 I added this 2 lines in my [FONT="Courier New"]/etc/apt/sources.list[/FONT]
[COLOR="Gray"]deb [http://ppa.launchpad.net/clazzes.org/ubuntu](http://ppa.launchpad.net/clazzes.org/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/clazzes.org/ubuntu](http://ppa.launchpad.net/clazzes.org/ubuntu) gutsy main[/COLOR]

  How force it to install subversion 1.5? It will also update my SVN Apache module?

  Thanks by advance

This does not work for gutsy. I tried, and it failed, and I poked around in the ppa.launchpad.net repo - there are no subversion 1.5 packages for gutsy. They only have them for hardy. 
Note to all others: this solution does not work for gutsy!
This is a severe pain!

---

### Post by msnel on 2009-02-09
> Note to all others: this solution does not work for gutsy!

Same here, I get:

[FONT="Courier New"]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 35CC62D2200CBE07[/FONT]

when running [FONT="Courier New"]sudo apt-get update[/FONT]

---

### Post by chriscohen on 2009-10-15
daveappendix's instructions in post #20 worked for me. Notably, I didn't have /etc/apt/preferences at all, so I just created a new file. Also, if it's not working, double-check you have typed everything into /apt/get/preferences correctly. A typo could prevent the proper source being used and prevent the update to 1.5.

---

