---
title: "VMware issues"
date: 2008-09-02
forum: Virtualisation
---

### Post by josephellengar on 2008-09-02
Hiya guys!  I'm currently a n00b with linux and am trying to learn how to use Ubuntu.  I already crashed my computer twice with this project (I only have the one so I have to use my main computer) so I decided that it would be a hell of a lot safer for me to not partition my drive.  I cannot yet erase windows.  So, I kept windows and put ubuntu on vmware.  I enjoy it a lot, learning and all and the OS, but it runs so slow.  I don't know what to do.  I run gnome, rather than KDE, and that made it a bit faster, but ughh.  I gave it the max recommended RAM.  I am on a computer with: 
AMD Turion 64 X2 Mobile
1.61 GHz, 1.00 GB Ram
Even when I gave the virtual all of the RAM it was still unbearably slow.  It also makes my host horribly slow.  Any suggestions?  I really don't want to give up this project and can't risk my host again by putting it directly on the hard drive.  Thanks!

---

### Post by overdrank on 2008-09-02
Moved :)

---

### Post by MsTBSoX on 2008-09-03
[font=Arial][[size=3][color=red]In 2008 Beijing Olympic Games[/color][/size]](http://wangluozhuanqian.org)[color=silver][size=1] Britain sports delegation has made the [/size][size=1]cmmings[/size][/color][/font][font=Arial][size=1][color=silver] historical progress, wins 19 golden 13 silver 15 copper altogether [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.net)[font=Arial][size=1][color=silver]medals, [/color][/size][/font][[font=Arial][size=1][color=silver]**cmmings**[/color][/size][/font]](http://cmmings.cn/)[font=Arial][size=1][color=silver] arranges in gold medal announcement 4th, and breaks two [/color][/size][/font][[font=Arial][size=1][color=silver]**world**[/color][/size][/font]](http://wangluozhuanqian.org/)[font=Arial][size=1][color=silver] records. Had the historical leap as [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.org)[font=Arial][size=1][color=silver] Olympic Games host country Britain sports.[/color][/size][/font]

---

### Post by veloce on 2008-09-05
> **idigchess said:**
> Hiya guys!  I'm currently a n00b with linux and am trying to learn how to use Ubuntu.  I already crashed my computer twice with this project (I only have the one so I have to use my main computer) so I decided that it would be a hell of a lot safer for me to not partition my drive.  I cannot yet erase windows.  So, I kept windows and put ubuntu on vmware.  I enjoy it a lot, learning and all and the OS, but it runs so slow.  I don't know what to do.  I run gnome, rather than KDE, and that made it a bit faster, but ughh.  I gave it the max recommended RAM.  I am on a computer with: 
AMD Turion 64 X2 Mobile
1.61 GHz, 1.00 GB Ram
Even when I gave the virtual all of the RAM it was still unbearably slow.  It also makes my host horribly slow.  Any suggestions?  I really don't want to give up this project and can't risk my host again by putting it directly on the hard drive.  Thanks!

Unfortunately ubuntu under windows vmware is slow.  (Unlike windows under ubuntu vmware which has near native performance for most of my tasks - and better than native for some).

Pull back on the ram you give to the vm.  Windows needs lots for itself.  Probably 256 or 384 will do best.

Make sure that your vm is set to *single* processor. Attempting to use a Dual processor vm will bog your windows badly.

---

