---
title: "how do i install graphic driver(VGA) on guest(Windows XP)"
date: 2012-10-06
forum: Virtualisation
---

### Post by iyasin on 2012-10-06
hi all, i installed Ms Windows XP as guest in VBox, but as i shown i below picture VGA or Video Controller isn,t installed..how do i can install it?

[IMG]http://i.imgur.com/zgGp1.png?1[/IMG]

tnx all.

---

### Post by sonnet on 2012-10-06
you need to install vbox additions.
Keep in mind that you can't install real hardware drivers in VM as normally VM do not have direct access to the vga.

For better performance with 3d , best option is to use Vmware Player 5.0 and install vmware tools. Many games are playable with that and you can get between 80%-95% of native performances depending on the game.

---

