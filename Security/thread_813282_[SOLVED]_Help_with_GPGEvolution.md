---
title: "[SOLVED] Help with GPG/Evolution"
date: 2008-05-30
forum: Security
---

### Post by belfasttim on 2008-05-30
Hi-- I am using GnuPG with Evolution. I hadn't had any issues til I installed Seahorse, then decided I didn't like it and removed it. Now when I try to send email with my GPG signature, I get the following error from evolution:

Because "gpg: problem with the agent - disabling agent use
gpg: writing to `-'
gpg: DSA/SHA1 signature from: "BAXXXXX My Key Name (this key) <myemail@email.com>"
", you may need to select different mail options.

I haven't found any info ont his specific error online. I tried purging Seahorse and re-installing gpg-agent, but it made no difference.

Any help much appreciated.

EDIT: on a GPG mailing list I found via Google, someone said they ran into this error and had to disable the gpg agent to get evolution to work. The downside is that this means you have to re-enter your passphrase every time you send an email.

---

### Post by belfasttim on 2008-06-04
Ok, update, I checked gpg.conf and it was basically deleted by Seahorse on uninstall. So I rewrote the gpg.conf file, reinstalled gpg-agent, then commented out the use-agent line in the gpg.conf. 

This appears to have fixed the issue. I thought when I commented out the use-agent line in gpg.conf it would insist that I enter passphrase on every use (each email), but it appears to save the passphrase session in evolution. So no problem.

---

