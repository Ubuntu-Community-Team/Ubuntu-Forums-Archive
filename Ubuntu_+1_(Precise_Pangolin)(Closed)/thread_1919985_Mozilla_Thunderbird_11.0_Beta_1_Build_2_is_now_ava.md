---
title: "Mozilla Thunderbird 11.0 Beta 1 Build 2 is now available."
date: 2012-02-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2012-02-03
I wonder if we will be seeing Mozilla Firefox 11.0 Beta 1 as well in 12.04?

---

### Post by jbicha on 2012-02-03
Yes, the Ubuntu development release runs the beta version of Firefox and Thunderbird (which is basically equivalent to RCs in pre-Firefox 4 days) which gives it a good amount of testing so that the stable Mozilla release can get pushed to all of the Ubuntu stable releases (Lucid, Maverick, Natty, Oneiric at the moment) as soon as possible (since it is a security update too).

---

### Post by kevpan815 on 2012-02-03
> **jbicha said:**
> Yes, the Ubuntu development release runs the beta version of Firefox and Thunderbird (which is basically equivalent to RCs in pre-Firefox 4 days) which gives it a good amount of testing so that the stable Mozilla release can get pushed to all of the Ubuntu stable releases (Lucid, Maverick, Natty, Oneiric at the moment) as soon as possible (since it is a security update too).

Thanks for the info, I was unaware that Ubuntu is now updating Firefox and Thunderbird for previous releases as well, there used to be a time period back in 7.10 and so forth where we had to wait for a new release to get updated versions of Mozilla Firefox and Mozilla Thunderbird.

---

### Post by pressureman on 2012-02-04
You might want to hold back your Thunderbird packages if you use the Lightning calendar extension, as it barfs on the TBird v11.

I presume that the xul-ext-lightning package will be updated accordingly in the next few days, but until then I've pinned my TBird at v10. Add this to your /etc/apt/preferences if you also wish to do so:

```

Package: thunderbird*
Pin: version 10.0+build1-0ubuntu1
Pin-Priority: 1001

```

---

### Post by kevpan815 on 2012-02-04
> **pressureman said:**
> You might want to hold back your Thunderbird packages if you use the Lightning calendar extension, as it barfs on the TBird v11.

I presume that the xul-ext-lightning package will be updated accordingly in the next few days, but until then I've pinned my TBird at v10. Add this to your /etc/apt/preferences if you also wish to do so:

```

Package: thunderbird*
Pin: version 10.0+build1-0ubuntu1
Pin-Priority: 1001

```

Thanks for the info, but I don't use that plugin, as I currently have no need for it as I get a free online calendar with my Microsoft Office 365 Subscription and I get another one with my Apple ICloud Login. :-)

---

### Post by pressureman on 2012-02-04
> **kevpan815 said:**
> Thanks for the info, but I don't use that plugin, as I currently have no need for it as I get a free online calendar with my Microsoft Office 365 Subscription and I get another one with my Apple ICloud Login. :-)

I use Lightning in conjunction with the gdata plugin so that I can manage my Google calendar via Thunderbird... with automatic syncing via Google on my Android phone :-)

I remember first trying Lightning / Sunbird back around 2004... it's taken a long time to get there, but it's quite usable now (although the appointment edit dialog is perhaps not so intuitive or user friendly).

---

### Post by cariboo on 2012-02-04
@kevpan815, out of curiosity, does Office 365 work when running Ubuntu?

---

### Post by SushiR on 2012-02-05
> **pressureman said:**
> You might want to hold back your Thunderbird packages if you use the Lightning calendar extension, as it barfs on the TBird v11.

I presume that the xul-ext-lightning package will be updated accordingly in the next few days, but until then I've pinned my TBird at v10. Add this to your /etc/apt/preferences if you also wish to do so:

```

Package: thunderbird*
Pin: version 10.0+build1-0ubuntu1
Pin-Priority: 1001

```

Any idea where I can find the version 10 package? I've already updated because I wasn't aware of it.

---

### Post by VMC on 2012-02-05
I haven't used Thunderbird in years, but just yesterday I tried the default install - 11.0, and was surprised that it works on Hotmail account.

The only caveat is on Hotmail TB creates a POP folder, and when I deleted stuff from TB it goes into that folder instead of deleted. Also, I can't see any junk mail from Hotmail through TB. At least I can read my incoming mail, which I didn't think Live Hotmail would allow that.

---

### Post by mc4man on 2012-02-05
> **SushiR said:**
> Any idea where I can find the version 10 package? I've already updated because I wasn't aware of it.

take your pick
[https://launchpad.net/ubuntu/precise/+source/thunderbird](https://launchpad.net/ubuntu/precise/+source/thunderbird)

---

### Post by pressureman on 2012-02-07
Lightning extension packages just got updated. Removed my apt-pin of Thunderbird, and upgraded. Lightning packages are now compatible with Thunderbird 11.

---

