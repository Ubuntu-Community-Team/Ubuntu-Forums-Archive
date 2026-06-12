---
title: "google under attack?"
date: 2020-06-18
forum: The Cafe
---

### Post by Skaperen on 2020-06-18
for the past couple of days i've been getting occasional failure to connect to gmail.  today it was worse.  6 failures to connect in a row.  so i did an AAAA query to get the IPv6 address and put that in front of "mail.google.com" and appended that to /etc/hosts an tried again.  it pops right up and runs just fine.  it seems like maybe their IPv4 is under attack.  i cannot imagine a failure at google lasting more than a couple hours.

anyone else seeing any network problems with google?

---

### Post by poorguy on 2020-06-18
No problems here with gmail or Firefox.

---

### Post by VMC on 2020-06-18
I'm not seeing it either using Firefox and Gmail.

---

### Post by Skaperen on 2020-06-19
i could guess that you guys are connecting over IPv6.  i was told there was a way to have Firefox try IPv6 first and fall back to IPv4 if there is no IPv6 address or the connection is refused or does not succeed within a time frame, but i never got an answer when i asked how.  all the answers i got from Google used IPv6 exclusively.

but i have no idea at all if you guys are doing IPv6.

too bad most web sites don't try to make things work by IP address.

---

### Post by VMC on 2020-06-19
i disable ipv6

---

