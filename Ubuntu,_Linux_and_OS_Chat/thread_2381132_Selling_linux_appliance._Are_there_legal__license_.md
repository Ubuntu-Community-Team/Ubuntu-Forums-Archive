---
title: "Selling linux appliance. Are there legal / license concerns with commercializing?"
date: 2017-12-27
forum: Ubuntu, Linux and OS Chat
---

### Post by ezmbo on 2017-12-27
Hi,

Hoping I have put this in the right forum section!

I am interested in developing a software appliance that is designed to run on Linux.

Basically, idea is to install base operating system (like Ubuntu) and then develop my own proprietary software to run on top of it, which I intend to sell for a fee.

I tried to look for this specific use case under the GNU/GPL license but am seeing conflicting responses on this.

Is it legal to sell proprietary software that have developed on top of Ubuntu?
If a consumer purchases the software appliance, do they have rights to redistribute the software to others?

Thanks in advance!

Kind Regards.

---

### Post by vasa1 on 2017-12-27
Take a look at [https://www.ubuntu.com/legal/terms-and-policies/intellectual-property-policy](https://www.ubuntu.com/legal/terms-and-policies/intellectual-property-policy) and they have a [Contact us link]("https://www.ubuntu.com/legal/terms-and-policies/contact-us") as well.

---

### Post by SeijiSensei on 2017-12-27
> **ezmbo said:**
> Is it legal to sell proprietary software that have developed on top of Ubuntu?
If a consumer purchases the software appliance, do they have rights to redistribute the software to others?

You'll need to supply a copy of the source code for all the GPL-licensed programs on the box except your own.  In practice you can direct the buyers to the Ubuntu website and link to the source-code repositories.

If you modify any GPL-licensed software, you are required to publish the changes.  

Some software may have further constraints. For instance, back when I was selling Linux servers, I could not include MySQL at the time because it was still under a commercial license.  (I solved the problem by using PostgreSQL and have never looked back.)

If your box will largely consist of the Linux kernel and ancillary GPL-licensed packages like gcc along with the software you write, you shouldn't have any licensing issues as long as you conform to the GPL.  I'd start with the most limited distribution you can find, like the [minimal Ubuntu distro]("https://help.ubuntu.com/community/Installation/MinimalCD"), and build up from there.

---

