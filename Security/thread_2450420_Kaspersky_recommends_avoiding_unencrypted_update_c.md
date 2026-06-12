---
title: "Kaspersky recommends avoiding unencrypted update channels"
date: 2020-09-13
forum: Security
---

### Post by Paddy Landau on 2020-09-13
Virtually everything has moved, or is in the process of moving, to encrypted channels. Even the smallest and poorest websites now use https instead of http, thanks to the free certificates available from [Let's Encrypt]("https://letsencrypt.org/").

According to a [recent article in Techradar]("https://www.techradar.com/uk/news/linux-users-beware-you-could-be-facing-more-cyber-threats-than-ever-before"), we're facing increased cyber risks. Among other advice, it says, "Kaspersky recommends maintaining a list of trusted software sources and avoid using unencrypted update channels, and not running binaries and scripts from untrusted sources."

Now that a number of apps are available via snaps or flatpak, I have managed to reduce the number of PPAs to just seven, but only one of them ([SpiderOakONE]("https://spideroak.com/one/")) uses https. The others, including Canonical, use http, and if you attempt to use https, they return errors.

With a little care, it's relatively easy to restrict yourself to trusted sources, but why are their PPAs still on unencrypted channels? Linux has grown in government, business, finance and other organisations, and not just for web servers. With malicious people after our money (and worse with malicious government interference), haven't http PPAs become an important security risk?

I'm puzzled how such a fundamental security measure has been ignored. Or am I missing something?

---

### Post by TheFu on 2020-09-13
APT uses cryptographic  signed packages. These are validated just prior to installation, so the risks in using HTTP only downloads isn't for normal APT.   It is a Windows issue and perhaps an issue for non-APT packages.  I don't know.  I'd hope that snaps are also cryptographic signed.  Can't say about AppImages or Flatpaks.  I get the feeling that AppImages don't have any signatures, but I don't know.

---

### Post by Paddy Landau on 2020-09-13
Thanks for the info.

The article was specifically about Linux, not Windows.

I know that AppImages are at least downloaded over https, not http, but I can't comment about snaps and flatpak.

---

### Post by TheFu on 2020-09-13
[https://wiki.myriadrf.org/Snap_Packaging](https://wiki.myriadrf.org/Snap_Packaging) claims that snaps are signed.  That usually means gpg signed.
[https://docs.flatpak.org/en/latest/flatpak-builder.html?highlight=gpg#signing](https://docs.flatpak.org/en/latest/flatpak-builder.html?highlight=gpg#signing) claims that Flatpaks support gpg signing.
[https://docs.appimage.org/packaging-guide/optional/signatures.html?highlight=gpg](https://docs.appimage.org/packaging-guide/optional/signatures.html?highlight=gpg) claims that AppImages support gpg signing.

So ... HTTPS isn't needed, assuming those signatures would be validated some time after the download, perhaps at the first run or at every run of the program inside the environment.

gpg is usually 4000x more secure than HTTPS.  No, that isn't true.  It is exponential ... so 2^4000 times more secure is more correct.

---

### Post by EuclideanCoffee on 2020-09-13
APT signs with GPG. So if someone were to insert their own package during transit, our computer likely would detect it unless your GPG key ring has been modified in some way to accept the faulty package. APT can support HTTPS, but it's not used yet because mirroring technology runs on very old scripts that sometimes do not accommodate HTTPS. I know this from using debmirror to copy Docker's APT repository. I can't unless I modify the script because it's HTTPS.

---

### Post by Paddy Landau on 2020-09-13
All of that information is interesting. If I understand the system correctly, in order to modify the keys, a malfeasant would have to have access to your computer anyway, at which point all bets would be off. Using https, then, would be icing on a rather large cake.

Thank you for clearing it up and laying my mind to rest. I still feel that the systems should gradually move over to https, in order to stay current with evolving standards and security, especially with the pending advent of quantum computing. It's good to know that Ubuntu already supports PPAs on https (as shown by its acceptance of the SpiderOakONE https PPA).

I'll mark this thread as solved.

---

### Post by TheFu on 2020-09-13
HTTPS is about privacy much more than security, if I remember my security training from decades ago.
These aren't "new" standards by any stretch. Both have been around 20+ years.

Eventually, MSFT will start signing packages, but signatures without automatic validation aren't exactly useful. Perhaps their new package manager does? I don't keep up with them. Sorta like how some browsers support HTTPS, but don't actually check for an invalidated certificate. Sad, but true.

Have you ever noticed that some PPAs refuse to load because the gpg keys are unavailable?  I see this mostly with Debian-based repos.  That should scare you.

---

### Post by SeijiSensei on 2020-09-13
> **Paddy Landau said:**
> All of that information is interesting. If I understand the system correctly, in order to modify the keys, a malfeasant would have to have access to your computer anyway, at which point all bets would be off.
Actually the bigger problem is if the evil-doer has access to the repositories and can sign packages containing malware. RedHat may have had a breach of this sort in 2008, though the company said the attackers did not manage to obtain the private key needed to sign packages.

[https://www.computerworld.com/article/2532769/red-hat-admits-breach-of-its-servers--fedora.html](https://www.computerworld.com/article/2532769/red-hat-admits-breach-of-its-servers--fedora.html)

---

### Post by EuclideanCoffee on 2020-09-14
> 
I still feel that the systems should gradually move over to https, in  order to stay current with evolving standards and security, especially  with the pending advent of quantum computing.


Doesn't really hurt to use HTTPS. I think we don't because why bother? As Fu said, there are many privacy reasons to use HTTPS but if encryption already exists, not too many security reasons. Double encryption. :)

If you're super curious about HTTPS or privacy configuration for APT, I believe Debian supports a repository in tor.

> 
Actually the bigger problem is if the evil-doer has access to the repositories and can sign packages containing malware.


Yes, certainly! But I think this is a limitation in a lot of encryption: keys can be lost and stolen.

> 
Have you ever noticed that some PPAs refuse to load because the gpg keys  are unavailable?  I see this mostly with Debian-based repos.  That  should scare you.


Ack! I know. PPA security really is the pits. I bet most of it is not the developer behaving badly. It's just difficult to do things securely.

---

