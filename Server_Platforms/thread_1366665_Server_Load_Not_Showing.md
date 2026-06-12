---
title: "Server Load Not Showing?"
date: 2009-12-28
forum: Server Platforms
---

### Post by Kiwi76 on 2009-12-28
A short while after a boot on my server (Ubuntu 8.04LTS 32-bit), the server load fails to show. The MyBB forums I have show "unknown" and "0" values. Doing a command to get the values via command line always return straight 0s (and yes, I'm positive those arenlt really the values). For the first minute or so the server is on, the server load does shows correctly, but then after a minute or so, it just stops working. I'm not sure when, exactly, it started happening, or what I changed between then and now. The OS install is relatively new, as are the forums and such running on it. What could be causing this not to show? I'm assuming more information is needed, so sorry if it's lacking, but I'm not sure what specifically is needed.

I originally reported this in the MyBB support forums as a follow up to another OP who reported the same problem (they never followed back up), but since a command returns no results, they say it's the server (OS), and not the forum software, which makes sense.

Edit: I just discovered while doing some FTP transfers that once I do a transfer, the server load starts working again, but only for a minute at most. It seems like very odd behavior to me for that to trigger it to work again. I'm not sure if that lends to a clue for what could be causing this or not.

---

### Post by Kiwi76 on 2010-01-01
Bump?

So nobody has any ideas as to why the get_server_load() function stops working (falsely returns all zeros) after a few minutes?

---

