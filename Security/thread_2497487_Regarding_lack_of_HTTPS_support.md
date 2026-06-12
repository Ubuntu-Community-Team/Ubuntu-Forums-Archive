---
title: "Regarding lack of HTTPS support"
date: 2024-05-07
forum: Security
---

### Post by karthikeyan-sankar on 2024-05-07
Regarding the lack of HTTPS support for Ubuntu, how can we address security concerns and ensure the integrity of downloaded files from the "http://archive.ubuntu.com/" domain? Is there a recommended verification process in such cases?

---

### Post by ian-weisser on 2024-05-07
One assumes you are trying to complain about vulnerability to a man-in-the-middle attack from an http (not https) apt mirror.

1. There are https mirrors. You are welcome to use one of those. See [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) for the list.

2. The "recommended verification process" is to use apt. Apt will warn you if a package has unexpected size, wrong hash, or other suspicious characteristics. The Debian apt+repository system of **automatically** verifying each downloaded package is over 25 years old. It existed *before* https. It was (and is) secure without https.

---

