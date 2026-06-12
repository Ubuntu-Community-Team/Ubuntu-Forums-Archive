---
title: "Ubuntu upgrade from 12.04 beta1 to beta2 ?"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dharmavir on 2012-03-29
Hello All,

I need help, I have installed Ubuntu server 12.04 beta1 and now I want to upgrade to beta2 release but I am not able to do that.

Will it available after sometime or it won't be possible to do this upgrade?

I know beta2 is just released today and I am curious to get it on my test-bed pool of servers now.

When I say "do-release-upgrade -d" or "do-release-upgrade -d -m server" it says "No new release found".

Thanks in Advance.
Urgent help is appreciated.

---

### Post by dharmavir on 2012-03-29
Can someone please reply? I am badly in need of this upgrade..!

---

### Post by CharlesA on 2012-03-29
It should be upgraded automatically via apt-get upgrade or apt-get dist-upgrade.

---

### Post by philinux on 2012-03-29
> **dharmavir said:**
> Hello All,

I need help, I have installed Ubuntu server 12.04 beta1 and now I want to upgrade to beta2 release but I am not able to do that.

Will it available after sometime or it won't be possible to do this upgrade?

I know beta2 is just released today and I am curious to get it on my test-bed pool of servers now.

When I say "do-release-upgrade -d" or "do-release-upgrade -d -m server" it says "No new release found".

Thanks in Advance.
Urgent help is appreciated.

Those commands would be looking for 12.10

Just keep your system up to date as normal and you're good.

---

### Post by dharmavir on 2012-03-29
Thank you Charles. Thanks a bunch.

 "apt-get dist-upgrade -d" really worked for me, somehow "do-release-upgrade -d" didn't work.

Anyways I got my purpose served.

Regards,
DJ

---

### Post by dharmavir on 2012-03-29
Thanks Phil,

Basically I was not aware about "apt-get dist-upgrade -d". But now I know and understood what you're saying.

---

### Post by CharlesA on 2012-03-29
> **dharmavir said:**
> Thanks Phil,

Basically I was not aware about "apt-get dist-upgrade -d". But now I know and understood what you're saying.
Looks like -d just downloads the packages, but doesn't install them.

Not sure if that was what you wanted to do or not.

---

### Post by dharmavir on 2012-03-29
Yeah, I just realized that. Actually I wanted to upgrade not just download.
But somehow it did upgrade system after confirmation.

Cheers.

---

### Post by CharlesA on 2012-03-29
Awesome.

Thanks.

---

### Post by cariboo on 2012-03-29
keep in mind, despite what the news sites have said, Beta 2 has not been officially released yet. Please wait for Kate Stewart's official notice.

---

### Post by Irihapeti on 2012-03-29
> **cariboo907 said:**
> keep in mind, despite what the news sites have said, Beta 2 has not been officially released yet. Please wait for Kate Stewart's official notice.

That's interesting. It's already on my local mirror (citylink.co.nz) - or at least Ubuntu i386 desktop and alternate are, and were of about two hours ago.

---

### Post by PaulW2U on 2012-03-29
> **Irihapeti said:**
> That's interesting. It's already on my local mirror (citylink.co.nz) - or at least Ubuntu i386 desktop and alternate are, and were of about two hours ago.

ISOs are always available a few hours before release.

Kate Stewart's email was sent about 15 minutes ago so beta 2 has now been officially released.

---

### Post by cariboo on 2012-03-29
I know the topic of this thread is upgrade from Beta 1 to Beta 2, but I just upgraded a system from Alpha 2 to Beta 2, it went off without a hitch. The big thing was having to download over 1600 packages to do the upgrade. Everything worked as it should, even dual monitors.

---

