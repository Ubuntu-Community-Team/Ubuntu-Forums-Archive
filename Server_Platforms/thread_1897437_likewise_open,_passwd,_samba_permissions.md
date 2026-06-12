---
title: "likewise open, passwd, samba permissions"
date: 2011-12-19
forum: Server Platforms
---

### Post by linux.girl on 2011-12-19
Hello everyone,

I have ubuntu 11.10 and I use likewise-open to authenticate my user with the windows active directory of my company - the user has sudo pass and admin rights on the computer.

Everything works fine, but I have a few questions:

1 - I noticed that my user doesn't appear in the passwd file. It wasn't a local user on the computer, it was a user that was added via likewise-open. SHOULD my likewise open authenticated user appear on passwd? If yes, how do I do it?

2 - When I log out with my user and try to login again, ubuntu remembers my username. But - if I shut down the computer, it doesnt remember my likewise-open user, I have to enter the full domain again under "other", i.e., domain.com\myuser. Is there a way to make sure ubuntu remembers the likewise-open user?

3 - Samba shares: if I go to the GUI option and ask connect to share, choose windows share, enter the server and type, etc, it connects to the windows share and I can do with the files the same things I would if I were on a windows computer (i.e., delete, etc). BUT, if I mount the samba share on startup by adding it to /etc/fstab - then I can access the share, but I cant do much with the files (i.e., cant delete them, etc). Any ideas why the difference in the permissions (?) when using different ways to connect to this share? And how can I fix it?

4 - And still with the issue of likewise-open - I tried to do chown on this windows share mount, chown to my likewise-open username, but it tells me invalid user...and back to questions 1 and 2 :-(

Any ideas?

Thanks a lot!

linux.girl

---

### Post by linux.girl on 2011-12-19
Update:

If I do sudo chown -R user@domain /folder, it enables me to do it - but it is only "lookalike", meaning, it gives the impression that it gave me ownership over the shared folder, but de facto it did not, i.e., I still cannot create folders in the share, nor delete folders, etc.

---

