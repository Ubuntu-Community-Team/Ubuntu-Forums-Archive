---
title: "Interview with Dustin Kirkland"
date: 2008-10-26
forum: The Fridge Discussions
---

### Post by TheFridge on 2008-10-26
This is the first in a series of interviews with Ubuntu developers about their work, and features that will be available in future versions.

 Dustin Kirkland is a developer on Canonical&#8217;s Ubuntu Server Team, working from Austin, Texas, USA. He is the author of the highly anticipated encrypted private directories feature in the upcoming Ubuntu 8.10 release. Previously, Dustin worked for IBM in various capacities, including as an on-site employee at Red Hat. There he discovered his interest in working with Linux at the distribution level, which eventually led him to Canonical.

 Dustin was also interviewed separately for [Ubuntu Weekly Newsletter #114]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue114").

 **One thing you have worked on for Intrepid is Encrypted Private directories. Could you tell us a little about what they are, and why they might be useful to someone?**

 If you have sensitive, personal data on a laptop computer, and you travel anywhere with it, you should seriously consider some form of encryption to protect that data.

 Perhaps you have used a LiveCD to recover data off of a broken system before&#8230;  Did you have to enter any passwords to access that data?  What&#8217;s to prevent someone from &#8220;borrowing&#8221; your computer for a few minutes (or stealing the whole thing), booting a LiveCD, reading your documents, mail, and keys?  Encryption can protect your data&#8230;if you have it!

 **From a server perspective, many machines today have hot-swappable disks.  A thief can flip a latch, yank a disk out, and be on his way.  That is perhaps a bit far fetched, but it happens.  And if your server is running a RAID, it might be many hours or days before you notice a disk is missing.  Again, without encryption, a thief has transparent access to all of your data.**

 There are many different ways you can use encryption to protect your data.  You can use gpg [1] to individually encrypt/decrypt individual files, but that would get cumbersome if you need to encrypt a lot of data.  

 Ubuntu supports encrypting the entire disk using LVM+LUKS [2], however there can be a performance penalty for encrypting *everything*, it&#8217;s not easy to conduct incremental backups of the encrypted data, and you have to enter a password just to boot the system.  The latter point is a show-stopper in most server environments, where the system is required to boot unattended in a data center or lab.

 Ideally (at least in my mind), each user&#8217;s entire home directory would be encrypted using a key that&#8217;s unique to them.  It would be mounted when the user logs in, and unmounted when the user logs out.  That was my original proposal for Intrepid, but this was deemed a bit too ambitious to accomplish within a single release.  The compromise was to provide a single encrypted location inside of each user&#8217;s home directory, ~/Private.

 Then, each time the user logs in (graphically, on the console, or via ssh), their &#8220;login passphrase&#8221; is used to decrypt the second &#8220;mount passphrase&#8221;.  This &#8220;mount passphrase&#8221; is used to establish the ~/Private mountpoint, where the user can read and write their most sensitive data.  This merely a mountpoint, though.  The data, when written to disk, is stored in ~/.Private.  Try reading any file in there and you&#8217;ll find that data is encrypted!  You can incrementally backup ~/.Private using rsync [4] (or some other backup program) to remote, untrusted storage, without giving the administrators of that remote system access to your data.

 **Do they provide complete security of the data that is stored in them?  What technologies does this feature make use of?**

 As with any good encryption scheme, the security of the data stored within an encrypted ~/Private directory is only as strong as long as your passphrases are secret and hard to guess.  By default, a 128-bit random mount passphrase is generated, which should be considered relatively strong.  This mount passphrase is then encrypted using your login passphrase, and so your login passphrase must be strong as well.  

 [INDENT]N.B. It is *essential* that you record your mount passphrase and store it somewhere safe.  If you ever have to manually recover your data, you will need this passphrase, rather than your login passphrase.

[/INDENT] Encrypted ~/Private directories in Ubuntu use eCryptfs as the cryptographic filesystem scheme.  eCryptfs first appeared as a filesystem module in the Linux kernel in November of 2006, in the 2.6.19 release.  eCryptfs uses the vetted cryptographic algorithms in the Linux kernel (AES, by default in Ubuntu), as well as the kernel keyring for per-user key management. Thus, I would argue that eCryptfs is built on top of established technologies.

 The biggest current shortcoming is that while all file contents are encrypted, filenames are not (Bug #264977).  The upstream kernel developer responsible for ecryptfs, Michael Halcrow if IBM, is currently pursuing this at a high priority, and has some working code that should make it into the Linux kernel soon.  I think Jaunty is a realistic timeframe, for Ubuntu.

 If you&#8217;re logged out, and the ~/Private directory is not mounted, it impossible for even the root user to mount your encrypted data without the appropriate passphrases.  However, when ~/Private is mounted, normal filesystem permissions apply.  The ~/Private directory is set up so that other non-privileged users should not be able to read the data. However, the root user may be able to.  To solve this problem, eCryptfs needs integration with technology that provides Mandatory Access Controls, such as AppArmor and/or SELinux (Bug #278290).

 **Are my passwords from Firefox stored in there for example?**

 Ubuntu doesn&#8217;t put any data in ~/Private automatically.  We felt that most people would have taken offense at any forced migration of data into ~/Private.

 On the other hand, I&#8217;ve blogged about some of the data that I store in my encrypted ~/Private [5]. Basically, I&#8217;ve moved my user data directories of Evolution, GPG, Firefox, Pidgin, SSH, and XChat to ~/Private, and established symbolic links in their usual locations.  I think this is a pretty sensible setup, but I recommend each user consciously choose what goes into their ~/Private directory.

 **How do I set up an encrypted private directory for myself?**

 Install ecryptfs-utils
 $ sudo apt-get install ecryptfs-utils

 Setup your private directory
 $ ecryptfs-setup-private

 Enter your login password, and either choose a mount pass phrase or generate one.  Record both pass phrases in a safe location!!!  They will be required if you ever have to recover your data manually.

 [[IMG]http://fridge.ubuntu.com/files/setup-private.png[/IMG]]("http://people.ubuntu.com/~jamesw/setup-private.png")

 Logout, and Log back in to establish the mount
 $ mount | grep Private

 Make sure that the application whose data you want to protect (e.g.  Firefox or Evolution) is not running
 $ ps -ef | grep firefox

 Move the application&#8217;s data directory (e.g. ~/.mozilla or ~/.evolution) into your ~/Private directory
 $ mv ~/.mozilla ~/Private

 Establish a symbolic link from the old location to new location
 $ ln -s ~/Private/.mozilla ~/.mozilla

 [[IMG]http://fridge.ubuntu.com/files/private-nautilus.png[/IMG]]("http://people.ubuntu.com/~jamesw/private-nautilus.png")

 Repeat for each of your most sensitive data directories.

 [INDENT]N.B. If you put all of .ssh in ~/Private, you won&#8217;t be able to ssh into the system using public key authentication.  In this case, you might want to only put your private key in ~/Private, and leave the rest in the clear.

[/INDENT] [INDENT]N.B. DO NOT PUT ~/.ecryptfs/ in ~/Private!  There&#8217;s a bootstrapping issue.  ~/.ecryptfs/* are required to establish the mount.  If those are not readable prior to establishing the mount, ~/Private cannot be mounted.

[/INDENT] We have also added an option to the alternate and server installer, just after choosing a username and password, to optionally setup an encrypted ~/Private directory.

 **What did you as an Ubuntu developer have to do to bring this feature to Ubuntu users?**

 First, I created a Blueprint in Launchpad [6].  Then, I created a Specification design document in the wiki [7].  I used this to fuel a discussion at the Ubuntu Developer Summit in Prague in May of 2008.  I refined the design document according to the feedback I got at UDS.

 Next, I discussed the design thoroughly with a number of people, both on the Ubuntu side, as well as with the upstream eCryptfs project.  I used IRC and the mailing lists to hash out some issues.  And I started implementing it incrementally and in stages.  I tracked the progress on the wiki page, and actively responded to questions in the wiki and in Launchpad bugs.

 I posted all changes as patches to the eCryptfs mailing list, and worked all of my code into the eCryptfs upstream git tree [8].  As soon as each batch of patches was accepted, I would request a new release tarball of ecryptfs-utils from the upstream maintainer (Michael Halcrow).  Then I&#8217;d request the Debian ecryptfs-utils maintainer (Daniel Baumann) sync the Debian unstable ecryptfs-utils package to the new upstream release.  Finally, I&#8217;d merge the Debian package into Ubuntu and request sponsorship.

 Also, I filed Main Inclusion Reports [9] for ecryptfs-utils and a number of its dependencies, in order to be in main and used in the installer.  As a prerequisite, some of the source code was reviewed by various Ubuntu developers, including Kees Cook, Jamie Strandboge, Steve Langasek, and Martin Pitt.  My thanks to them for their careful review.  Colin Watson helped integrate the questions into the alternate and server installers.  

 It was about this time I discovered planet.ubuntu.com and &#8220;blogging&#8221;.  Using my blog, I was able to generate some publicity around the feature and call for testing.  The feedback was almost overwhelming, but with the help of the outstanding Ubuntu community, we did shake out and fix some interesting bugs.

 Based on my contributions to Ubuntu through ecryptfs-utils (as well as a number of other packages), I was able to apply for and attain MOTU privileges in the Ubuntu community.

 And as a result to my active contribution to ecryptfs-utils upstream, I was added as a maintainer to the ecryptfs project.

 **You say you were accepted as a MOTU due in part to your work on this feature, that implies that you implemented this without having upload rights to Ubuntu. Is that correct?**

 Correct.  At the beginning of the Intrepid development cycle, ecryptfs-utils was in Universe, and I did not have upload privileges.  Jamie Strandboge, Kees Cook, and Chuck Short sponsored many uploads of ecryptfs-utils.

 Just about the time that I was granted upload rights to Universe, ecryptfs-utils was moved to Main, where I do not (yet) have upload privileges.  So I still need to push my changes to the Ubuntu package through an Ubuntu Core Developer.  I hope to apply for Core Dev in the coming months.

 On the other hand, I am now an upstream co-maintainer of eCryptfs, and I have commit privileges against the upstream git repository.

 **Did you examine any other approaches to solving this? Why did you pick this particular one?**

 Among the other options I reviewed, I considered eCryptfs to be the most promising.  It&#8217;s a filesystem in the Linux kernel, giving optimal performance, thorough peer review, and standard implementation.  The development community is active and established.  I have been privy to the overall design of eCryptfs since 2004, from my previous role as a security developer in the IBM Linux Technology Center.  

 A more comprehensive review of eCryptfs against other implementations (albeit biased) is available at [10].

 I will note that it would be possible for a motivated Ubuntu developer to modify my Encrypted Private implementation to use a different underlying encryption scheme for ~/Private.  I would actually encourage more development in this space, as I think choice is good for the Ubuntu community.  I could easily see an Encrypted Private directory that uses, say, EncFS instead of eCryptfs.  I wouldn&#8217;t necessarily work on it myself, but I would encourage such development.

 **Where can people go if they want to find out more? Are there any tasks that they can help with?**

 Start with the design specification [7].  Join the ecryptfs-users community in Launchpad [11].  Consider helping with upstream eCryptfs development [8,12].

 I&#8217;ve focused mainly on the server space, and on the command-line only.  I would love to get some help from more desktop oriented developers for better integration with the Gnome and KDE desktops.  Nautilus, Konqueror, etc.  There&#8217;s an effort to create a graphical interface for setting up an encrypted private directory.  I would love to see something under System->Preferences->Encryption and Keyrings that allowed a user to setup their private directory right there.

 **Do you have any plans to improve this feature in future releases?**

 Upstream ecryptfs kernel development is working on encrypted filenames.  We&#8217;ll want to help integrate and test that in Ubuntu.  I expect this should make it into Jaunty.

 I mentioned above that more graphical setup tools would be useful, for configuration and setup, and integration directly into the file managers.  I&#8217;d like to see a similar option in the graphical installer for what we have in the alternate and server installers.

 I plan on pitching encrypted home directories again at UDS.  I hope to use the relative success of encrypted ~/Private to bolster my case.  There will be problems to solve, of course.  But that&#8217;s what discussions are for.

 Finally, we really need encrypted swap by default.  Swap can be a treasure trove of passphrases and keys on a system.  I would like to see swap encrypted by default, with a randomly generated key every boot.  This should be relatively easy to do, with most of the work needing to be done in the installers.  Resuming from suspend and hibernate might take some new new magic, but I think it should be doable.

 Otherwise, I&#8217;m open to suggestions.  Please file wishlist bugs appropriately against:

 
[LIST] 
[*]Upstream ecryptfs: [https://bugs.launchpad.net/ecryptfs](https://bugs.launchpad.net/ecryptfs) 
[*]Ubuntu&#8217;s ecryptfs-utils: [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils) 
[/LIST]
 References:

 [1] [http://manpages.ubuntu.com/manpages/intrepid/en/man1/gpg.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/gpg.html)
[2] [https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)
[3] [http://manpages.ubuntu.com/manpages/intrepid/en/man1/ecryptfs-setup-private.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/ecryptfs-setup-private.html)
[4] [http://manpages.ubuntu.com/manpages/intrepid/en/man1/rsync.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/rsync.html)
[5] [http://blog.dustinkirkland.com/2008/10/what-in-my-encrypted-private-directory.html](http://blog.dustinkirkland.com/2008/10/what-in-my-encrypted-private-directory.html)
[6] [https://blueprints.launchpad.net/ubuntu/+spec/encrypted-private-directories](https://blueprints.launchpad.net/ubuntu/+spec/encrypted-private-directories)
[7] [https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)
[8] [http://git.kernel.org/?p=linux/kernel/git/mhalcrow/ecryptfs-utils.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/mhalcrow/ecryptfs-utils.git;a=summary)
[9] [https://wiki.ubuntu.com/MainInclusionReportEcryptfsUtils](https://wiki.ubuntu.com/MainInclusionReportEcryptfsUtils)
[10] [http://ecryptfs.sourceforge.net/ecryptfs-faq.html#compare](http://ecryptfs.sourceforge.net/ecryptfs-faq.html#compare)
[11] [https://launchpad.net/~ecryptfs-users](https://launchpad.net/~ecryptfs-users)
[12] [https://launchpad.net/ecryptfs](https://launchpad.net/ecryptfs)

 

[More...](http://fridge.ubuntu.com/node/1701)

---

