---
title: "how i can upgrade sendmail to the latest"
date: 2006-04-26
forum: Server Platforms
---

### Post by shumbola on 2006-04-26
hello,

i'm running ubuntu 5.10 and have sendmail 8.13.4 installed.
i want to upgrade sendmail to version 8.13.6. (that's what sendmail team
recommends) how i can do that? is there sendmail deb file for ubuntu?

thanks,
shum

---

### Post by hw-tph on 2006-04-26
If you have security updates enabled for the universe repository you will automatically get the latest available Ubuntu package when upgrading (**sudo apt-get update && sudo apt-get upgrade**). New versions of applications are not added to the stable distribution but security updates are backported so you should be safe if you do the above.


Håkan

---

### Post by shumbola on 2006-04-26
I've got security updates enabled fro the universe but apt-get says there is no sendmail update. Can you please check and tell if I'm mistaken and there is a sendmail bugfix release in ubuntu repositories? I'm new to ubuntu, I came from Slackware. I know how to install from tar.gz, but in this case I wanted to use automatic updates that comes with ubuntu via apt-get.

Btw, above sendmail version which was installed by apt-get update, apt-get install sendmail does not compile properly sendmail.cf. 

Thank you!

---

