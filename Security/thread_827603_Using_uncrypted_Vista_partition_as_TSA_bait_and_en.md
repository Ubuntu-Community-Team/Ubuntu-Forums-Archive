---
title: "Using uncrypted Vista partition as TSA bait and encrypting Hardy partition - how?"
date: 2008-06-12
forum: Security
---

### Post by Dynaflow on 2008-06-12
After reading recent [stories on Slashdot]("http://yro.slashdot.org/article.pl?sid=08/04/22/1733251") about TSA agents copying whole hard drives and impounding suspicious laptops at the (US) border, I've decided that, as someone running a less-common (i.e., suspicious) operating system, I should look into encrypting my trusty Compaq laptop.

My laptop is currently dual-boot with Vista and Ubuntu, with the Vista partition being used mainly to update Windows Vista.  

What I would like to do is leave the original, much-truncated, and mostly unused Vista partition intact and unencrypted so that I can turn my laptop on and let Homeland Security rifle through the rather boring files on the Windows partition, without there obviously being a second partition, with its own operating system, where all the juicy stuff is kept, like company files, bank info, personal e-mails, embarrassing attempts at short fiction, etc.

I could sort of do this now by reconfiguring Grub to automatically boot into Windows before I land, but that doesn't help if I happen to be selected for whole-hard-drive copying, if somebody pops in a BackTrack Linux LiveCD, or something like that.

I know it's possible to do this in Fedora 9 with relative ease, but I'm partial to Ubuntu.  Does anyone have some insight on how to pull this off?

Don't misunderstand my motives.  I don't have much of anything illegal on my computer (at least until the [Federal copyright police]("http://www.billboard.biz/bbbiz/content_display/industry/e3i4552e786232dd91baa8a825cc2f79780") get going).  I just don't feel like letting DHS celebrate the 4th Amendment's continuing coma by sifting through my personal stuff for traces of Evil.

---

### Post by niteshifter on 2008-06-13
Hi,

Frankly, that would be a waste of time and effort. In the vanishingly small chance that you do get tapped for imaging, how are you going to explain all the missing real estate on that drive?

It's not going to be some $16/hr TSA gate agent type that's going to be doing the forensics, it's going to be someone considerably better qualified, equipped with tools from both commercial sources (like Encase) and what the NSA/CIA/DIS have. When this person sees the structure ... you've clearly something to hide. That's like bleeding into a pool of sharks. They'll be all over you. Forever.

Setting GRUB to boot Vista is good enough. All the gate TSA type wants to see is a functioning computer.

---

### Post by hyper_ch on 2008-06-13
what do you actually want to do?

---

### Post by tubbygweilo on 2008-06-13
> Stories on Slashdot
IMHO not a good reason for baiting the TSA but you may well think otherwise. 

If you wish to make a stand on your principles about searches, encryption, censorship and other like causes then a trip over to [eff.org]("http://www.eff.org/press/archives/2008/06/12") may be time better spent.

---

### Post by Dynaflow on 2008-06-13
> **hyper_ch said:**
> what do you actually want to do?

Politics aside, I want to be able to create an encrypted logical volume at (re)install time to contain Ubuntu, while keeping the manufacturer-installed OS intact and unchanged (other than having much less real estate than it had originally) on its own partition, all on one hard drive.

Fedora 9 seems to have an automated process as part of its installer that does just this, and I'm wondering if I can manually get Ubuntu's installer to pull off a similar feat.

---

### Post by Scotty Bones on 2008-06-13
As it stands now the only way to create the encrypted volume at install time is through the command line installer (alternate cd), it may be possible to do after the fact but i'm not sure on that one.  I believe there is a how-to here in the forums.  I've never tried it myself as I keep all my important info in a true-crypt container.


EDIT: This might help out
[http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

---

### Post by niteshifter on 2008-06-14
@tubbygweilo:

I don't think the OP meant "bait" as in baiting or provoking. I believe he meant it as in something for the TSA to fixate upon. The link to the EFF was a good'un - wish I'd thought to do that.

@Dynaflow:

One last pass, then I let it rest. You're thinking emotionally. Don't. Think *tactically*, counter measure vs. measure. Encryption is not a viable tactical response either, they'll ask for the key - then what? Refuse, or tell 'em "I forgot" and they'll just wave you through?

Not. Going. To. Happen.  Delay of your travel and an interview with people who have had their sense of humor removed, cavity searches, seizure of the gear. That's what happens.

You've already hit on a sound tactic: Give them what they expect - Vista with some ordinary stuff. Better still, off-load anything that could be considered "suspicious" before travel. Placing confidential data on a server somewhere, access via VPN is what the experts recommend.

---

### Post by hyper_ch on 2008-06-14
if you haven't installed linux yet, you can do setup a dualboot device and with the alternate cd you can directly encrypt it during install....

however first you'd need to free some space on the partition and I'd use the vista partitioner for that.

---

### Post by Dynaflow on 2008-06-14
> **niteshifter said:**
> 

I don't think the OP meant "bait" as in baiting or provoking. I believe he meant it as in something for the TSA to fixate upon. ...

Correct.

> ...
One last pass, then I let it rest. You're thinking emotionally. Don't. Think *tactically*, counter measure vs. measure. Encryption is not a viable tactical response either, they'll ask for the key - then what? Refuse, or tell 'em "I forgot" and they'll just wave you through?

Not. Going. To. Happen.  Delay of your travel and an interview with people who have had their sense of humor removed, cavity searches, seizure of the gear. That's what happens. ...

The laptop was cheap, and I would rather have it seized, suffer a delay, and have it be known that I refused to give up a password than give those people a detailed, data-mineable, 80GB snapshot of my life and work to keep on file somewhere into perpetuity.  There are some things I just won't compromise on.  The VPN idea is a good one, though.

(I've been an ACLU member for years, and have been cheering for the EFF as a like-minded organization for quite a while now.  Maybe it's time I started sending *them* donations now too.)

> **hyper_ch said:**
> if you haven't installed linux yet, you can do setup a dualboot device and with the alternate cd you can directly encrypt it during install....

however first you'd need to free some space on the partition and I'd use the vista partitioner for that.

It's been dual booting Ubuntu and Vista since the day after I bought it last November.

From what I've understood in using the Ubuntu alternate CD, if I want Ubuntu fully contained within an encrypted filesystem, I would be limited (with the default options, at least) to doing full-disk encryption and a full-disk install.  Am I missing something obvious here?

What I want to do is reinstall Ubuntu in such a way that its partition is encrypted without having to encrypt the entire disk (which would entail paving over the Vista partition with the new, encrypted filesystem and then having to reinstall Vista within that, which I don't think my cruddy restore disks would deign to let happen anyway).

I have done this with Fedora 9 on a couple of computers using the automated tool in Fedora's installer (see [this]("http://docs.fedoraproject.org/install-guide/f9/en_US/sn-disk-druid.html") and [this]("http://docs.fedoraproject.org/install-guide/f9/en_US/sn-general-disk-setup.html")), and I'm wondering if and how I can do something similar, manually, with Ubuntu.

---

### Post by hyper_ch on 2008-06-14
No, it's a fully encrypted linux (or rather almos). You'll need an unencrypted /boot partition and then rest will be encrypted... this will not touch the windows partitions.

However, if you fully encrypt your partitions, you also need to ahve a backup somewhere...

---

