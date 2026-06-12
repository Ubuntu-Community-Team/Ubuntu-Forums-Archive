---
title: "Pound not in bionic repositories"
date: 2018-06-05
forum: Ubuntu, Linux and OS Chat
---

### Post by allenjd2 on 2018-06-05
I did an `apt install pound` on Ubuntu 18.04 and received:

Package pound is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'pound' has no installation candidate

A package search ([https://packages.ubuntu.com/search?keywords=pound](https://packages.ubuntu.com/search?keywords=pound)) does not show a result for bionic or cosmic. Is the pound package being removed from the official repos or is it common for a delay before all packages are available?

---

### Post by PaulW2U on 2018-06-05
The [publishing history]("https://launchpad.net/ubuntu/+source/pound/+publishinghistory") for pound shows that the package was deleted from Ubuntu on 26th February 2018 while 18.04 was still in development. The package was not being maintained and was incompatible with other packages.

---

### Post by allenjd2 on 2018-06-05
Thanks. I'll use nginx instead.

---

### Post by deadflowr on 2018-06-05
> The package was not being maintained and was incompatible with other packages.
Somehow this latest release, and Debian it comes from, has seemed to have thrown quite (or not quite) a few of the orphans out the window.
Works for me though.
I'd rather have packages with some level of support than packages running on fumes alone.

---

