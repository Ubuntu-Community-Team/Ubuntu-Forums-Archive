---
title: "Virtualbox - Ubuntu - LAMP stack"
date: 2021-06-12
forum: Virtualisation
---

### Post by drhiii on 2021-06-12
Anyone recommend a Virtualbox/Ubuntu/LAMP stack running an older Ubuntu or similar, as in 2018 or preferable, 2016?

I am needing to restore a CMS site and am having to revert back to a version of PHP, MySql and related.  Am searching but figure folks here have their finger on the pulse of this kind of bundled knowledge.

tx for any recommendations..

---

### Post by TheFu on 2021-06-12
I would never recommend using virtualbox for running any Linux server.

Standard support for all versions of Ubuntu prior to 18.04 has ended, so you won't get much help.

For stuff like you seem to want, most people would deploy a Linux Container, not a VM.  Read up on LXD/lxc.  [https://linuxcontainers.org/lxd/introduction/](https://linuxcontainers.org/lxd/introduction/)

Whatever you do, don't put any webapp that old onto the internet unless the goal is to be hacked.  Automated tools seek out those sites and use exactly the necessary problems to gain complete control - totally pwn'ing the system in a few minutes.

---

### Post by drhiii on 2021-06-12
> **TheFu said:**
> I would never recommend using virtualbox for running any Linux server.

Standard support for all versions of Ubuntu prior to 18.04 has ended, so you won't get much help.

For stuff like you seem to want, most people would deploy a Linux Container, not a VM.  Read up on LXD/lxc.  [https://linuxcontainers.org/lxd/introduction/](https://linuxcontainers.org/lxd/introduction/)

Whatever you do, don't put any webapp that old onto the internet unless the goal is to be hacked.  Automated tools seek out those sites and use exactly the necessary problems to gain complete control - totally pwn'ing the system in a few minutes.


I am rescuing, for someone else who has passed away but their web site and body of newsletters are very important, an older CMS install that was last updated in 2017.  I need to run an older PHP and MySql environment to get the system up and running, then upgraded to current standards, then place it back on the internet.  After serious hardening.  Of which I know well.  And well aware of not putting older installs onto a live site... which would be insane.  I once managed the security for 2600 *nix servers deployed worldwide.  Incl intrusion/detection.  Well aware of what you speak.  VirtualBox is fine for this purpose.  Never going live anywhere.

No prob.  I already have 2/3rds of a virtual machine built.  Just was hoping to save some time.  tx for the response.

---

### Post by TheFu on 2021-06-12
Bringing up an LXD 18.04 system is about 5 minutes.  Then you can login and treat it like any other 18.04 system. Being dependent on someone else's backups with little understand of their methods would be tough.  Where I've worked, we always had run-books to explain everything.  A home, restoring backups begins with a fresh installation of whatever OS is needed.  It can be the same release or newer most of the time.  Before moving to a new release, having a solid, normal backup is part of the process.  Also would create an LVM snapshot before starting anything to make reverting back a few seconds, so trying again is easy.  The snapshot needs to be sized sufficiently to hold whatever new storage will be required. On a system with tight storage, that can be hard.

Of course, if you are stuck on Windows as the hostOS, not much choice. LXD doesn't work on Windows - linux containers don't unless a Linux VM is run, then the containers are placed nested inside.  This is a best practice for all container use - 1 VM that hosts X number of containers.

As for installing a pre-configured LAMP, ubuntu has a meta-package that will do that in about 45 seconds.  lamp-server^ is the name, I think.  It should be offered as a package when using any "Server" installation media the last 5 yrs.  If you missed that, 
```
sudo apt install lamp-server^
```
should do it. Here's the packages to be installed:
```
The following additional packages will be installed:
  libevent-pthreads-2.1-7
Suggested packages:
  apache2-doc apache2-suexec-pristine | apache2-suexec-custom php-pear libipc-sharedcache-perl tinyca
The following NEW packages will be installed:
  apache2 apache2-bin apache2-data apache2-utils libapache2-mod-php libapache2-mod-php7.4 libapr1
  libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libcgi-fast-perl libcgi-pm-perl
  libevent-core-2.1-7 libevent-pthreads-2.1-7 libfcgi-perl libhtml-template-perl libmecab2 mecab-ipadic
  mecab-ipadic-utf8 mecab-utils mysql-client-8.0 mysql-client-core-8.0 mysql-server mysql-server-8.0
  mysql-server-core-8.0 php-common php-mysql php7.4-cli php7.4-common php7.4-json php7.4-mysql
  php7.4-opcache php7.4-readline
```
If you would prefer mariadb over mysql, just install that first. For dependency reasons, those are considered the same.

If the title had a specific CMS listed, might find that people who use that could respond.  I use Perl and Ruby CMS tools, not php. Sorry.

---

### Post by MAFoElffen on 2021-06-12
No disrespect to anyone... 

What I suspected from the first post last night, and the OP confirmed (later), was that he had an old orphaned site, that had no documentation, nor a live person to pass on what the logic of the site was, and how it worked. (Though, the OP was not specific to what he wanted to do, and where he wants to end up at, in that original post.) That is the basic jist right?

The OP just needed to run it "temporarily", to figure it out, to be able to update it to whatever, using whatever. I respect TheFu, his knowledge and experience. The OP is setting up a temporary test environment, and probably a parallel dev environment. Then the OP will dispose of the outdated. In it's form, it will never leave that test environment. 

For a test environment on, TheFU or I would probably host it using KVM or LXD, but the OP might know more,  be more comfortable and have more confidence using what he has or knows. I understand that... For all we know, the Host to his VirtualBox may be running on a 32bit Windows OS. (He never said.) AS a Dev, he may also being using a Graphical Desktop to use GUI tools such as an editor and browser to step through it and see what it is doing. You would never do that on a live public web host either, but so is such for personal realms. It makes it quick and easy in a test environment.

Now, the DEV environment or where it ends up as? TheFu has some great ideas for that. Infrastructure wise, that makes all the sense in the world, if the OP was hosting it (in the end). Though that depends on who and where it will be hosted. "That" dictates a few things. I can understand that the OP may not be the Hosting Entity. What the OP is "doing" is a Web Site update,  with a web app, which will fit to the Hosting Entity's infrastructure and security. Right?

I can also see the OP's passion in his posts to take this on (personally) as a project, and may not even be paid for this. My Kudo's to him, if that is the case.

Reminds me of the adage that "*Communications is a mutual understanding of all involved...*" Just saying that there is common ground here. On both sides.

---

### Post by drhiii on 2021-06-12
No disrespect taken. 

100% what you said.  I could repeat your take but it would be, repeating.  That is all I want to do.  Rescue, upgrade to current, harden, place back onto the internet.  IOW, exactly how you laid it out.

The gent who passed away was remarkable in that he wrote newsletters, for years.  Understood global internet and its top shelf players better than almost anyone.  He had in the truest sense, a photographic mind.  Recalling the tiniest bits of information He ran a maillist too that had not some of the top movers and shakers in creation and build of the internet, THE top movers and shakers.  I migrated it to a variant and many are still in it.  A who's who.  For privacy reasons, mums that.

The site tho had fallen into disrepair.  That simple.  Resurrecting it will open up access to historical archives.  I feel duty bound to this as he was a close friend.  Very sad to not be able to pick up the tele...

And you are correct.  It is a bit of a forensical archeological dig to see what happened.  Appears the CMS was upgraded while PHP was not within the hosting environment.  The site broke apart when unsupported calls were being made in old PHP.  So, need to establish a temp environment, bring it back to life, methodically upgrade to new... harden the hell out of it, and get on.

I appreciate all ya'll's injection into this.  Everything is understood, especially the energy and enthusiasm towards just knowing your stuff.  For sure.  When I get the site answering again, will post it.  To most it is dry as a desert.  But to some, this is a historical archives that in terms of the build out of the internet and related, it matters.

tx  




> **MAFoElffen said:**
> No disrespect to anyone... 

What I suspected from the first post last night, and the OP confirmed (later), was that he had an old orphaned site, that had no documentation, nor a live person to pass on what the logic of the site was, and how it worked. (Though, the OP was not specific to what he wanted to do, and where he wants to end up at, in that original post.) That is the basic jist right?

The OP just needed to run it "temporarily", to figure it out, to be able to update it to whatever, using whatever. I respect TheFu, his knowledge and experience. The OP is setting up a temporary test environment, and probably a parallel dev environment. Then the OP will dispose of the outdated. In it's form, it will never leave that test environment. 

For a test environment on, TheFU or I would probably host it using KVM or LXD, but the OP might know more,  be more comfortable and have more confidence using what he has or knows. I understand that... For all we know, the Host to his VirtualBox may be running on a 32bit Windows OS. (He never said.) AS a Dev, he may also being using a Graphical Desktop to use GUI tools such as an editor and browser to step through it and see what it is doing. You would never do that on a live public web host either, but so is such for personal realms. It makes it quick and easy in a test environment.

Now, the DEV environment or where it ends up as? TheFu has some great ideas for that. Infrastructure wise, that makes all the sense in the world, if the OP was hosting it (in the end). Though that depends on who and where it will be hosted. "That" dictates a few things. I can understand that the OP may not be the Hosting Entity. What the OP is "doing" is a Web Site update,  with a web app, which will fit to the Hosting Entity's infrastructure and security. Right?

I can also see the OP's passion in his posts to take this on (personally) as a project, and may not even be paid for this. My Kudo's to him, if that is the case.

Reminds me of the adage that "*Communications is a mutual understanding of all involved...*" Just saying that there is common ground here. On both sides.

---

### Post by TheFu on 2021-06-12
> **drhiii said:**
> No disrespect taken. 
None meant or taken on my side either.  Never know who we are talking with in these forums. Just never know.

 ...
> **drhiii said:**
> 
I appreciate all ya'll's injection into this.  Everything is understood, especially the energy and enthusiasm towards just knowing your stuff.  For sure.  When I get the site answering again, will post it.  To most it is dry as a desert.  But to some, this is a historical archives that in terms of the build out of the internet and related, it matters.

If you have a clone of the prior system, I'd bring that up, then use CMS transition tools to migrate the entire CMS over to a newer version. Often, the RSS feeds can accomplish that for the most popular CMS tools.

Better help can happen with more details.  The CMS name would be key.  The old versions of each dependent tool would help.  The actual format of the backup/image/VM you started with could make it easier too. For example, with an image, it might be easiest to just use QEMU to run it for the time to use RSS cloning tools to get all the data out and over to a system that might be more comfortable or more secure.

Lots of ways to skin this raccoon.
[ATTACH=CONFIG]288648[/ATTACH]

---

### Post by drhiii on 2021-06-13
100% on not knowing who you are dealing with.  I was surprised, and not a little thankful, that I got any response at all.  Oft questions languish, usually because they are not framed well, too long, etc.  

I have in my hands backups going back to 2013.  'tis Joomla.  So several versions to deal with.  I finally got an Ubuntu 2018 LTS installed, PHP 5.5, APache2 and MySql.  And PhpMyAdmin.  LAMP is easy.  I had to mess with mainly various versions of PHP, to match the particular backup date.  Some of the backups may have been corrupted.   I had to throw several environments and backups to finally gain a match.  PHP 5.2 did not work, as did PHP 7.*.  Ended up being particular with PHP 5.5, tho am sure another version may have worked.  In another lifetime.

No matter, finally in.  Cleaning up, hardening, securing (my wheelhouse).  And a few words you can't say on national TV.  If anyone is curious, will post the resurrected site.  Gordon left me with his wishes that everything become public domain.    Endeavoring towards that.  

I appreciate all ya'll's input.  Way more than I had hoped...

And skinning raccoons is no joke.  We are inundated here.  Front range Colorado.  Pikes Peak straight out my back door.  My brother who lives close by is in an endless battle to catch the next and next and next litters.  Couldn't resist spinning up on the raccoon reference.  



> **TheFu said:**
> None meant or taken on my side either.  Never know who we are talking with in these forums. Just never know.

 ...


If you have a clone of the prior system, I'd bring that up, then use CMS transition tools to migrate the entire CMS over to a newer version. Often, the RSS feeds can accomplish that for the most popular CMS tools.

Better help can happen with more details.  The CMS name would be key.  The old versions of each dependent tool would help.  The actual format of the backup/image/VM you started with could make it easier too. For example, with an image, it might be easiest to just use QEMU to run it for the time to use RSS cloning tools to get all the data out and over to a system that might be more comfortable or more secure.

Lots of ways to skin this raccoon.
[ATTACH=CONFIG]288648[/ATTACH]

---

