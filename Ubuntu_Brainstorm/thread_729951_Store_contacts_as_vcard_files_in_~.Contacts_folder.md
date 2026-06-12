---
title: "Store contacts as vcard files in ~/.Contacts folder"
date: 2008-03-20
forum: Ubuntu Brainstorm
---

### Post by Bou on 2008-03-20
I submitted this as an idea at [http://brainstorm.ubuntu.com/idea/5213/](http://brainstorm.ubuntu.com/idea/5213/)

> One of the few things I don't like about Ubuntu is the way contacts are stored. I never know where Evolution is supposed to save them and I always end up losing the whole list every time I reinstall.

I would like contacts to be stored as Vcards in ~/.Contacts. Every one of your friends should be a file, and this file should contain all available info about him: mail address, IM address, phone number, even physical address.

This procedure would help consider contacts as "physical" items that you can copy and move, and would make the process of backing them up much more intuitive.

Hope you guys like it.

---

### Post by chrisccoulson on 2008-03-21
As you are asking to change the way that Evolution stores contacts, you might be better off asking this upstream. Nevertheless, I don't think you'd get much support. For example, Evolution can already export contacts as VCards. You also don't consider the effects on performance of the addressbook, for example - time taken to load contacts (especially when there are 100's or 1000's of contacts). Would it be faster or slower (would it cause Evolution to grind to a halt for several seconds to read the addressbook)? My guess would be that a flat individual-file-per-contact back-end would reduce performance with high numbers of contacts.

Also, you shouldn't lose the whole address list each time you reinstall, because the addressbook is stored in ~/.evolution/addressbook/local. If you have a separate /home partition, then you get to keep all of your personal data if you reinstall (including the addressbook). If not, then you can back up /home before you reinstall, and keep all your contacts

---

