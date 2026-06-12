---
title: "introducing zuluMount,an alternative to udisks and friends for mounting solution."
date: 2013-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by mhogomchungu on 2013-05-18
Greetings to all members of this community.I hope my post will not be taken as spamming the forum as that is not my intent,my intent is to introduce my project in a hope that it will be useful to members of this community.

Permission to introduce myself,i am the founder and current maintainer of a project called "zuluCrypt" hosted at: [http://code.google.com/p/zulucrypt/](http://code.google.com/p/zulucrypt/)

The link to zuluMount-gui screenshots are at the end of page.

zuluMount is a front end to zuluCrypt and its purpose is to give a  simple to use CLI and GUI Desktop environment/file manager independent  solution for mounting of encrypted as well as unencrypted volumes.Currently supported encrypted volumes are truecrypt volumes and cryptsetup's plain and luks volumes.

It does not use polkit authorization mechanism and does not require  d-bus to work and hence can be a good alternative for those who do not  like these two components for whatever reason.

It can be used as an alternative to GUI application to manage  truecrypt volumes.Truecrypt application is released under questionable  license and some distributions prefer not to include it[1][2]

It has a command line component that is better suited for third party  developers than udisks as udisks prefers it not to be used by third  party developers whose work is not tied up to desktop environments[3]

It being independent of Desktop environments or file managers makes  it an ideal single solution for those who constantly switch DE or file  managers as the same tool can be in across them.

It being about to deal with encrypted volumes as well as non encrypted volumes makes it a "one stop mounting solution" 

  I am the founder and current maintainer of the project just though i  should mention it here to increase its awareness as i think there need  to be more tools like it.All tools that have the same functionality are  usually bolted on file managers or desktop environment making them not  easily accessible outside of them.

  A tool with the same independence is udevil[5] but the independence  is only at the CLI since its GUI frontend is tied to SpaceFM[6]

  [1][https://fedoraproject.org/wiki/Forbidden_items?rd=ForbiddenItems#TrueCrypt](https://fedoraproject.org/wiki/Forbidden_items?rd=ForbiddenItems#TrueCrypt)

  [2][https://tails.boum.org/todo/provide_a_migration_path_from_truecrypt/](https://tails.boum.org/todo/provide_a_migration_path_from_truecrypt/)

  [3][http://udisks.freedesktop.org/docs/latest/udisks.8.html](http://udisks.freedesktop.org/docs/latest/udisks.8.html)

  [4][http://ignorantguru.github.io/udevil/](http://ignorantguru.github.io/udevil/)

  [5][http://ignorantguru.github.io/spacefm/](http://ignorantguru.github.io/spacefm/)

  
Will appreciate any comment you may have and thanks for giving me this opportunity to discuss my project with this community.

---

### Post by mhogomchungu on 2013-06-01
just thought i should drop a line to inform of a new version.

interesting features added in this version is more support for truecrypt volumes.
It is now possible to create normal as well as hidden truecrypt volumes using a "naked" key or a keyfile
It is now possible to open either a normal or a truecrypt hidden volume using a "naked" key or a keyfile

The download page is at:
[http://code.google.com/p/zulucrypt/downloads/list]("http://code.google.com/p/zulucrypt/downloads/detail?name=zuluCrypt-4.6.3.tar.bz2&can=2&q=#makechanges")

For the curious among us on how the GUI components look like,screenshots are at:
[http://code.google.com/p/zulucrypt/wiki/zuluMount_screenshots](http://code.google.com/p/zulucrypt/wiki/zuluMount_screenshots)
[http://code.google.com/p/zulucrypt/wiki/zuluCrypt_screenshots](http://code.google.com/p/zulucrypt/wiki/zuluCrypt_screenshots)

For the curious among us on how the backend,CLI components interact with one another,an overview explanation is at:
[http://code.google.com/p/zulucrypt/wiki/backend_achitectural_over_view](http://code.google.com/p/zulucrypt/wiki/backend_achitectural_over_view)

One of those "nice to have features" is that its now possible to start mounting a volume residing in a file simply by dragging and dropping the file in the GUI component.

---

