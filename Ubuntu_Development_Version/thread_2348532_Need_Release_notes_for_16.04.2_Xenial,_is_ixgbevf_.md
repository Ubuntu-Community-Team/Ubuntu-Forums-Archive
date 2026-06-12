---
title: "Need Release notes for 16.04.2 Xenial, is ixgbevf package version 2.16.4 included"
date: 2017-01-04
forum: Ubuntu Development Version
---

### Post by sara.jarjoura on 2017-01-04
Howdy, 

We are using 16.04.1 Xenial and are looking at enabling SR-IOV for AWS instances by updating the network driver ixgbevf from the default 2.12 to the recommended version 2.16.4 as described here [http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/sriov-networking.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/sriov-networking.html) .

However, we suspect that an updated package version might be coming in the January 19th point release for Xenial 16.04.2.

I am looking to get the release notes and package versions for 16.04.2 Xenial to find out whether the package version of SR-IOV network driver ixgbevf has been updated to or past the Amazon-recommended version.

Thanks!
Sara

---

### Post by mc4man on 2017-01-04
If you use the upcoming lts kernel for 16.04  you'll get version  3.2.2-k

---

### Post by sara.jarjoura on 2017-01-05
Beautiful - thank you!

---

