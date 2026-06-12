---
title: "What's the best way to go from 1.5 to 2.0 CE ?"
date: 2006-12-05
forum: Ubuntu Christian Edition
---

### Post by glenn69 on 2006-12-05
I currently run CE 1.5 (Dapper)

What is the best way to upgrade to 2.0 (Edgy) without losing any user files in our /home directories ?

Thanks

---

### Post by mhancoc7 on 2006-12-05
> **glenn69 said:**
> I currently run CE 1.5 (Dapper)

What is the best way to upgrade to 2.0 (Edgy) without losing any user files in our /home directories ?

Thanks

In theory you could:

1. Backup your /home directory.
2. Upgrade to Edgy. ([https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades))
3. Run the convert_me script for Ubuntu CE Edgy. ([http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/convert_to_ubuntu_christian_edition_edgy.tar.gz)]("http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/convert_to_ubuntu_christian_edition_edgy.tar.gz")

Now let me say that I have not been successful in getting this to work. If you search the forum you will find lots of users having issues upgrading from Dapper to Edgy. In fact I have never personally been successful in upgrading from Dapper to Edgy.

I would suggest that you do this.

1. Backup your /home directory.
2. Do a fresh install of Ubuntu CE v2.0 (Edgy).

I know that is not the ideal, but like I said upgrading from any Ubuntu to release to the next has been an issue for many users. I have always found it best to do a fresh install. Since Automatix is included in Ubuntu CE it is a lot easier to get your system up and running quickly.

Just let me know if you have any questions.

Thanks, Jereme

---

### Post by glenn69 on 2006-12-05
Well that's what I will be doing...a fresh new version of CE 2.0.  Thanks for the advice.

---

### Post by mhancoc7 on 2006-12-05
> **glenn69 said:**
> Well that's what I will be doing...a fresh new version of CE 2.0.  Thanks for the advice.

Sounds great. Be sure to let us know how it goes. Don't forget that there are some Edgy specific issues like wifi support that may cause you some trouble.

Jereme

---

### Post by Fully216 on 2006-12-05
I personally tried upgrading, gave up because of problems just to do a clean install.  Might as well save you the heart ache by doing so from the get go, which sounds like you will do.  :-)

---

### Post by Darrious on 2006-12-05
I actually had problems doing the clean install too.

---

### Post by mhancoc7 on 2006-12-05
> **Darrious said:**
> I actually had problems doing the clean install too.

Could you elaborate. I believe most of the issues with installing Ubuntu CE v2.0 (Edgy) are Edgy related.

Thanks, Jereme

---

### Post by mysticrider92 on 2006-12-06
I had been using the v1.5 when I did the dist-upgrade to Edgy, then ran the v2.0 script and everthing is working fine.

---

### Post by Darrious on 2006-12-06
> Could you elaborate. I believe most of the issues with installing Ubuntu CE v2.0 (Edgy) are Edgy related.
Yes, my only problems have been with Edgy, not Dapper.

Well there is only one problem that I had with Ubuntu CE v2.0

Although I have already figured it out.

I could not do sudo apt-get install <package>
 It had something to do with GnomeSword, Evince, and Planner. All I did was reinstall them and now everything works fine.

So that was really not such a big problem. Also, I think that there is a big problem, not with CE, but with Edgy. I've read a lot of posts complaining that they could not get Edgy to recognize there wireless card.

---

