---
title: "General question regarding LXC.  Should I see individual guest processes in the host?"
date: 2016-04-22
forum: Virtualisation
---

### Post by hondaman on 2016-04-22
I'm still figuring LXC out, but should I see individual guest processes, by guests users found only in the guest while looking at "top" in the host?

Real world example.  I installed a LXC guest to play with zoneminder.  Zoneminder creates its own users.  However I can see those users in the host while looking at top.

I guess I thought the LXC guest and its processes would all be umbrella'd under a single LXC process in the host?

---

### Post by SoronZero on 2016-04-22
yes because lxc maps the guest uids to host uids, so typical mapping for the first user is 100000:65536 (or something like that in /etc/subuid) so if the guest has a user log in then it will show up on the host in between the range of 100000:65536

---

