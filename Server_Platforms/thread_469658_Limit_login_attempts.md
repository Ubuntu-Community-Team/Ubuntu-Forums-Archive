---
title: "Limit login attempts"
date: 2007-06-10
forum: Server Platforms
---

### Post by bjerre on 2007-06-10
I'd like to limit the number of login attempts on Ubuntu 6 server.
How is this done?
I've been a victim of a brute force attack...

---

### Post by MJN on 2007-06-10
By 'limit' do you mean rate limit? Or are the attempts unauthorised? If the latter I'd suggest installing Fail2Ban - that'll ban a particular IP address from attempting to login for a certain period of time (configurable) if it fails authentication (invalid username, wrong password etc) a certain number of times (again configurable).

Mathew

---

