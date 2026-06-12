---
title: "OpenSSL version Issue"
date: 2014-04-14
forum: Security
---

### Post by actionmystique on 2014-04-14
Hello guys,

You must have heard about the so called "heartbleed" problem all over the internet. This issue has been affecting Ubuntu 13.10 as well.

I have noticed that OpenSSL and libssl have been updated to release 1.0.1_**e**_. When you take a look at the latest release on the official site, it's 1.0.1_**g**_: [http://www.openssl.org/news/](http://www.openssl.org/news/)

Can this discrepancy be fixed on the official repository or do we have to manually compile the sources?

---

### Post by buzzingrobot on 2014-04-14
For 13.10, 'e' has been patched.  If you've updated, you have it. See: [http://www.ubuntu.com/usn/usn-2165-1/](http://www.ubuntu.com/usn/usn-2165-1/).

---

### Post by actionmystique on 2014-04-14
If you take a careful look at the link I've posted, the "e" version ha&s been uploaded weeks **before** the "Heartbeat overflow issue" was discovered... Woops!

I suspect the "e" release does not include patches for this issue.

---

### Post by buzzingrobot on 2014-04-14
> **actionmystique said:**
> If you take a careful look at the link I've posted, the "e" version ha&s been uploaded weeks **before** the "Heartbeat overflow issue" was discovered... Woops!

I suspect the "e" release does not include patches for this issue.

Then you think Ubuntu's security notice lied? You can follow the links in that notice and read the patch yourself.

---

### Post by actionmystique on 2014-04-14
They must have overlooked the last OpenSSL sources; otherwise, they would have mapped their package version to the original sources release number.

---

### Post by actionmystique on 2014-04-14
I've asked the same question in their launchpad forum; let's wait and see their answer.

---

### Post by coffeecat on 2014-04-14
[http://ubuntuforums.org/showthread.php?t=2215886](http://ubuntuforums.org/showthread.php?t=2215886)

---

### Post by actionmystique on 2014-04-14
@[**[COLOR=#990303][B]coffeecat**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=129087"): Thanks for the link; now I'm sure that _**my up-to-date Ubuntu 13.10 has NOT been patched with the latest OpenSSL 1.0.1g patch of April 7th**_:

[ATTACH=CONFIG]252055[/ATTACH]
[https://docs.google.com/document/d/1UaYD0IhZdpeZydJ8MA1h5nOjTBbFLlW8VSI3LSoKTY4/edit?usp=sharing](https://docs.google.com/document/d/1UaYD0IhZdpeZydJ8MA1h5nOjTBbFLlW8VSI3LSoKTY4/edit?usp=sharing)

Build date and version are 2 separate things!

Someone took the 1.0.1e OpenSSL sources that were uploaded on the official site on the 11th of February and compiled them.

Wake up call!

---

### Post by buzzingrobot on 2014-04-14
Have you updated?

The package for 13.10 in the repo ([http://packages.ubuntu.com/saucy/openssl](http://packages.ubuntu.com/saucy/openssl)) is tagged 1.0.1e-3ubuntu1.2 and the changelog ([http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_1.0.1e-3ubuntu1.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_1.0.1e-3ubuntu1.2/changelog)) shows the patch was applied on 7 April.

The previous version for Saucy was 1.0.1e-3ubuntu1.1. 

Here on 14.04, openssl is tagged 1.0.1f-1ubuntu2 and the changelog shows the same patch was applied on the same day.

Distributions do not necessarily adhere to upstream numbering conventions.

---

### Post by actionmystique on 2014-04-14
You cannot say that you've not been warned. 
It's up to you to stick with the old OpenSSL release.
I'm going to build the last 1.0.1g on my system from the sources.

---

### Post by buzzingrobot on 2014-04-14
Warned about what?  The openssl package on my system has been patched.

---

### Post by SeijiSensei on 2014-04-14
> **actionmystique said:**
> You cannot say that you've not been warned. 
It's up to you to stick with the old OpenSSL release.
I'm going to build the last 1.0.1g on my system from the sources.

You need to learn how packages are maintained.

It's quite common for developers to "backport" security patches into existing versions without a change in the major version number.  That's true for both RedHat and Debian flavors like Ubuntu.  The only way to know what it is included in a specific package is to read its changelog as buzzingrobot observes.

---

### Post by actionmystique on 2014-04-14
THIS is the last OpenSSL release:

[ATTACH=CONFIG]252058[/ATTACH]
Also available here: [https://docs.google.com/document/d/1_G6SUkuz6-Vq2ECDeKt4wLMz9VeH28zMDWtfoEA8_IA/edit?usp=sharing](https://docs.google.com/document/d/1_G6SUkuz6-Vq2ECDeKt4wLMz9VeH28zMDWtfoEA8_IA/edit?usp=sharing)

For those who want to update their system with this last version (the sources are here: [http://www.openssl.org/source/](http://www.openssl.org/source/)), the PATH environment variable needs to be updated too in /etc/environement with /usr/local/ssl/bin; I suggest to put it in first position.

---

### Post by matt_symes on 2014-04-14
> **buzzingrobot said:**
> Have you updated?

The package for 13.10 in the repo ([http://packages.ubuntu.com/saucy/openssl](http://packages.ubuntu.com/saucy/openssl)) is tagged 1.0.1e-3ubuntu1.2 and the changelog ([http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_1.0.1e-3ubuntu1.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_1.0.1e-3ubuntu1.2/changelog)) shows the patch was applied on 7 April.

The previous version for Saucy was 1.0.1e-3ubuntu1.1. 

Here on 14.04, openssl is tagged 1.0.1f-1ubuntu2 and the changelog shows the same patch was applied on the same day.

Distributions do not necessarily adhere to upstream numbering conventions.

^^^ this.

---

### Post by cariboo on 2014-04-14
See t[his]("http://www.ubuntu.com/usn/usn-2165-1/"), there instructions on how to update libssl.

---

### Post by CharlesA on 2014-04-14
> **actionmystique said:**
> THIS is the last OpenSSL release:

[ATTACH=CONFIG]252058[/ATTACH]
Also available here: [https://docs.google.com/document/d/1_G6SUkuz6-Vq2ECDeKt4wLMz9VeH28zMDWtfoEA8_IA/edit?usp=sharing](https://docs.google.com/document/d/1_G6SUkuz6-Vq2ECDeKt4wLMz9VeH28zMDWtfoEA8_IA/edit?usp=sharing)

For those who want to update their system with this last version (the sources are here: [http://www.openssl.org/source/](http://www.openssl.org/source/)), the PATH environment variable needs to be updated too in /etc/environement with /usr/local/ssl/bin; I suggest to put it in first position.

Why would you need to bother building openssl from source when the patch has already been backported? RedHat, CentOS, Ubuntu, and Debian all have patches released for the current version of openssl, which means they are not susceptible to the heartbleed bug.

---

### Post by actionmystique on 2014-04-14
Whatever

---

### Post by actionmystique on 2014-04-14
I suggest you read this thread carefully from the beginning...

---

### Post by Elfy on 2014-04-14
Given the last post - thread closed.

---

