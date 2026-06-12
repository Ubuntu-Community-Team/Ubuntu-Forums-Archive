---
title: "Web File Manager UI"
date: 2010-04-30
forum: The Cafe
---

### Post by JasonClint on 2010-04-30
Hi everybody,

I am using Ubuntu on a NAS / HTPC box at home, and would really like to make my files available through a simple web interface (as you would see with a lot of dedicated NAS boxes). I am not looking for anything particularly powerful or fancy, just a nice simple web interface which I can log into and download files over the web.

It would be nice if it could allow you to specify which folders are available through the web interface too, but that is not a necessity.

Does anyone have any suggestions?

Thanks

---

### Post by undecim on 2010-04-30
usermin has a file browser. That's the only way I know of doing it over HTTP. Most other solutions like phpfm will run as the www-data user and won't be able to access your home directory.

---

### Post by EarthMind on 2010-04-30
Why not just install Apache? You can set it to show nice directory trees and filter some out if necessary, using .htaccess files.

---

