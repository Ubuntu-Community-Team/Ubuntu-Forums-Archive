---
title: "Benefits of LTS realease and how to make full use of it?"
date: 2010-10-06
forum: The Cafe
---

### Post by soulitude on 2010-10-06
I've been using Ubuntu for a while. Just thought i would write on something i've very limited knowledge or rather incomplete. I am using Lucid Lynx and it is LTS long term support release of Ubuntu. Read that ubuntu provides security updates for 3 years for LTS version.

What features does LTS actually provide you other than normal ones? how do they do that? I would like to know all the benefits of LTS and the way to make full use of it. Is it just the normal update-manager alerts for updated packages and or something more than that.

Perhaps most of you guys will have the same question. Please write on. Thanks in advance.

---

### Post by snowpine on 2010-10-06
LTS releases get 36 months of bug fixes and security patches (60 months for the server version!), compared with 18 months for normal releases. This means that you can deploy Ubuntu LTS in mission-critical situations such as business, government, education, e-commerce, etc. Testing, deploying, and training your employees in a new release is expensive (I know a lot of businesses who are still using Windows XP, which is 9 years old!) and so the 2-year LTS release cycle is more suitable than the 6-month cycle for these users.

No special actions on your part are necessary to "take advantage" of an LTS release, just keep current with your Update Manager and you'll be up-to-date. :)

---

### Post by soulitude on 2010-10-06
Thanks snowpine for writing. So thats how it works. Does that mean we get some extra packages and updates while listing as current in update-manager? much more than what is listed in normal Ubuntu releases?

---

### Post by cariboo on 2010-10-06
All Ubuntu releases are a snapshot of the Debian unstable/testing repositories at the start of a development cycle. Basically what is in that repository at that time is what is in that release. 

In an LTS version, unless there is a very compelling reason, the package versions stay the same with only bug fixes and security updates for the life of the release.

---

### Post by snowpine on 2010-10-06
> **soulitude said:**
> Thanks snowpine for writing. So thats how it works. Does that mean we get some extra packages and updates while listing as current in update-manager? much more than what is listed in normal Ubuntu releases?

The updates are exactly the same as any other Ubuntu release (mostly minor updates such as bug fixes and security patches) the only difference being the *duration* of support (36 months vs. 18 ).

---

### Post by TBABill on 2010-10-06
You don't get anything "extra" by being on the LTS. What happens is the updates are provided for a longer period of time on the LTS than on, say, Ubuntu 10.10. After the 18 month period where 10.10 is receiving updates ends, 10.04 will still be receiving support for another year. So you get an OS with a longer support period, which is supposed to keep you from needing to reinstall (or upgrade) a new OS frequently.
 
And you can go into update manager and set it to alert you to new LTS availability, or to update you ever time the new release comes out on a 6 month basis.

---

### Post by soulitude on 2010-10-06
Thank you guys. Got it. Good luck and wishin happy ubuntu days ahead.

---

### Post by bodhi.zazen on 2010-10-06
> **soulitude said:**
> I've been using Ubuntu for a while. Just thought i would write on something i've very limited knowledge or rather incomplete. I am using Lucid Lynx and it is LTS long term support release of Ubuntu. Read that ubuntu provides security updates for 3 years for LTS version.

What features does LTS actually provide you other than normal ones? how do they do that? I would like to know all the benefits of LTS and the way to make full use of it. Is it just the normal update-manager alerts for updated packages and or something more than that.

Perhaps most of you guys will have the same question. Please write on. Thanks in advance.

Moved to the café, this is not a security question.

The "benefit" of LTS is the length of support. 

I prefer a cutting edge release and tolerate bugs, my wife does not care about the latest release of package foo,  she wants stable, reliable, and no need to reinstall.

When you use Debian, do you use stable or sid ? Centos or Fedora ?

---

