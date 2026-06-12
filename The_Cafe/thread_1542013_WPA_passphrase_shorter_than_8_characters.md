---
title: "WPA passphrase shorter than 8 characters?"
date: 2010-07-29
forum: The Cafe
---

### Post by Mr. Picklesworth on 2010-07-29
First of all, this isn't my router and I don't need to be told that passwords should be long :)
This isn't a discussion about best practices. We can't always control these things.


So, I was helping someone yesterday who needed to connect to a wireless network (with Ubuntu), and he was sure it had a 7 character WPA passphrase. As you may have encountered, it's accepted that a WPA passphrase should be between 8 and 63 characters. Indeed, NetworkManager goes out of its way to make it impossible to enter a passphrase shorter than that.

Following one discussion, I looked at [the IEEE spec]("http://standards.ieee.org/getieee802/download/802.11i-2004.pdf") and there's a reference implementation. Again, they say the passphrase should be "between 8 and 63 ASCII-encoded characters," but they never actually state why it should be at least 8. (The 63 character upper limit is to differentiate a PSK from a passphrase).
Their reference implementation doesn't seem to enforce that lower limit. (Although the wpa_passphrase command line tool with wpasupplicant in Ubuntu does).

So, is this lower limit an actual technical limitation, or an opinion imposed by geeks on power trips who have worked in corporate IT for too long?

For example, is that lower limit reliable to the extent that a user interface should strongly enforce it, rendering short passphrases completely unusable? (Is there no way at all that any wireless network in the entire world will have a 7 character WPA passphrase?).


Or, more to the point: have you ever seen a WPA passphrase shorter than 8 characters?

---

### Post by jerenept on 2010-07-29
no, dd-wrt refuses to allow it (on my linksys).

---

