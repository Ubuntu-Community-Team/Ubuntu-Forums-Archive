---
title: "[SOLVED] User and root"
date: 2008-12-12
forum: Security
---

### Post by cr4nk on 2008-12-12
Hi, I got couple questions.

I installed ubuntu 8.10 recently and during installation I created a user name, lets call it 'user1' and a password 'pass1'. Why didn't it ask me for the root pass? is user1 the root?

When i am logged in under user1 and i open up the terminal and say 'sudo ...' it asks me for the super user's pass aka the root, but during the installation I entered only user1's pass, and this pass works for the sudo.

Can someone explain this or point me to an information page about how the users work under ubuntu.

One last thing. For the sake of security should I login in normally as this user1.

Thanx guys in advance

---

### Post by kerry_s on 2008-12-12
in ubuntu root is locked. you use sudo and your password. you have root privileges but you have to use sudo,gksudo or gksu. to become root it would be "sudo su". but shouldn't be needed.
gksudo and gksu is graphical, for example say you press alt+f2 to bring up the run command, to launch a root program> gksu nautilus /
will give you a root nautilus(filemanager)

---

### Post by sisco311 on 2008-12-12
link:[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Authorized users (users in the *admin* group) are allowed to run programs as root.

The first user is added by default to the admin group.

---

### Post by cr4nk on 2008-12-12
thanx guys thats what i was looking for

---

### Post by fghi906 on 2008-12-15
[align=left][align=left]*[size=9pt]Pearlove Jewelry Inc. lauches many fine pearl jewelries ?C pearl necklaces, pearl bracelets, pearl earrings, and fine Swarovski crystal jewelry for wedding bridal party, Christmas Eve, and other occasions. Detailed products lists are at [[color=#800080]http://www.pearlove.com/christmas-gift-jewelry-cl-49.html[/color]](http://www.pearlove.com/christmas-gift-jewelry-cl-49.html) . [/size]*[/align][/align][align=left][align=left][size=9pt] [/size][/align][/align][align=left][align=left][size=9pt]Pearlove.com, one of the most swiftly developing cultured pearl jewelry wholesalers in China, launches many new styles of freshwater pearl necklaces, bracelets, cultured pearl earrings and pearl jewelry sets, which can be worn in wedding parties, grand dinners, and etc.In the past few months, Pearlove.com specializes in designing fashion pearl jewelry, especially for Christmas. The styles of pearl necklaces include single-row simple necklaces, illusion necklaces, tin cup necklaces, lariat necklaces, multi-strand, twisted necklaces, rope necklaces and more.  Materials used are including various shapes and colors of freshwater pearls, Chinese semi-precious stones, Swarovski crystals, Chinese natural crystals and etc. [/size][/align][/align][align=left][align=left][size=9pt]The jewelries made for formal occasions are usually used with good quality pearls and stones, and light colors. For example, 925 silver chains & clasps, round or near round pearls are used for bridal jewelry styles, and the colors are usually white, pink or lavender. Most of these styles are simple and beautiful. Usually, pearl colors are changeable, according to buyers&#8217; own design.Pearl jewelry sets are popular with most clients. Consumers like more to wear a set jewelry which can match their clothes, hair and shoes perfectly. Pearlove&#8217;s jewelry sets are usually including necklaces and earrings, bracelets according clients request. The jewelry sets styles contain formal set, good quality set and fashion style, to meet different market. Clients can easily choose equal prices and styles on [[color=#0000ff]http://www.pearlove.com/pearl-jewelry-c-5.html[/color]](http://www.pearlove.com/pearl-jewelry-c-5.html) .[/size][/align][/align][align=left][align=left][size=9pt]About Pearlove.comPearlove Jewelry ([http://www.pearlove.com](http://www.pearlove.com)), freshwater pearl jewelries online wholesale store, mainly focused in Chinese natural colors of cultured freshwater pearls; Pearlove Jewelry also does some dyed pearls basing clients&#8217; requests. In addition, the company wholesale coral jewelry, turquoise, shell beaded jewelry, crystal and other gemstone jewelry. Customized requests are accepted as well. [/size][/align][/align]

---

