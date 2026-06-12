---
title: "Virtualbox oracle repository fails when running upgrades."
date: 2019-04-28
forum: Virtualisation
---

### Post by ajgreeny on 2019-04-28
Users who have added the virtualbox repositories to their system, and who have seen the error about the repos being unavailable
> The repository 'https://download.virtualbox.org/virtualbox/debian bionic Release' no longer has a Release file. please note that this is a result of the website certification of Vbox site having lapsed, hopefully temporarily.

See the thread at the Vbox forum [https://forums.virtualbox.org/viewtopic.php?f=7&t=92880](https://forums.virtualbox.org/viewtopic.php?f=7&t=92880) where this is discussed at some length.
I have also tried, but it is also impossible to download the installation files for Windows or Linux using a direct download in a web browser as the certification error stops this being done. Even trying the "Advanced" button in the error window and clicking the "Accept the risk and continue" does not help as the browser (firefox in my case) simply does not move on any further.

There is a suggestion from some posters about replacing the https:// suffix of the website with http:// which some have used with success though I have not tried this either as I already have the current latest 6.0.6 version installed and running well.

With luck the new working week will mean that the site certification is updated and renewed quickly, leading to the disappearance of this error.

---

### Post by DuckHook on 2019-04-29
Thanks for the update ajgreeny.

I can confirm that plain-Jane http (sans TSL/SSL) does work.

---

### Post by adrianvg on 2019-04-29
Thanks for the confirmation. I've been having this problem for the last two weeks or so.
Replacing https with http did it.

Sounds strange though it should take this long to replace the certificates on the servers though...

---

### Post by ajgreeny on 2019-04-30
Problem now seems fixed; presumably Oracle have updated their certification.

---

