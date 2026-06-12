---
title: "Nutty to Oneiric server upgrade risk factors"
date: 2012-01-10
forum: Server Platforms
---

### Post by CapnKirk on 2012-01-10
I'm preparing to 'do-release-upgrade' on a Nutty box to upgrade to 11.10. I've googled around, and found [**this advice**]("http://library.linode.com/troubleshooting/upgrade-to-ubuntu-11.10-oneiric").

The server mostly runs Apache (LAMP) web services, including some that I have installed independently of apt (Plone, bugzilla, civiCRM, WordPress).

Besides doing a backup of all affected data, configuration and apt-independent software, are there any other known "risk factors" to keep in mind and prepare for?

TIA!

Kirk

---

### Post by CharlesA on 2012-01-10
I'd clone the whole drive just to be safe, after backups are made.

That way if something gets really messed up, you can restore the image and be back up and running.

Are you upgrading for a specific reason? Natty is supported until October of this year.

---

### Post by CapnKirk on 2012-01-10
I don't have any specific reason to upgrade. I just noticed the MOTD when I log in:
> New release 'oneiric' available.
Run 'do-release-upgrade' to upgrade to it.

It's good to know about the October date. I don't currently have the resources to do a disk image; I'll put that into the budget for this year...

Thanks for your response!

Kirk

---

### Post by CharlesA on 2012-01-10
> **CapnKirk said:**
> I don't have any specific reason to upgrade. I just noticed the MOTD when I log in:

It's good to know about the October date. I don't currently have the resources to do a disk image; I'll put that into the budget for this year...

Thanks for your response!

Kirk

Gotcha. Upgrading isn't mandatory. ;)

If this is for a business, I'd suggest waiting until a few months after 12.04 is released and maybe think about upgrading to that one, as it is a LTS (long term support) release.

---

