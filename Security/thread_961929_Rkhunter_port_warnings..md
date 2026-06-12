---
title: "Rkhunter port warnings."
date: 2008-10-28
forum: Security
---

### Post by Dave_Connor on 2008-10-28
Awhile ago I had rkhunter flash up port 2128 and now it is flashing 60922 from python-2.5. I know deluge uses python (right ?) so would it just be my torrents making connections through that port with deluge ?

---

### Post by OpenSourceFuture on 2008-10-28
Have you tried running it without any server software (bittorrent) running at the same time?

Try turning off everything to the bare bones then run your scan.

---

### Post by Dave_Connor on 2008-10-28
I did a scan a few days ago when I just logged in and gnome loading up all my settings and it didn't show anything. When I killed python it stoped. Is there a way to reboot the python process again to see if rkhunter will re-pop up the warning ?

---

### Post by OpenSourceFuture on 2008-10-28
If downloading torrents set it off before, it should again right? I would think the same torrenting program that uses python would do that.

---

### Post by Dave_Connor on 2008-10-28
I guess I should just edit /etc/rkhunter.conf to allow proc python since it is just Deluge setting rkhunter off. Since I did netstat -pa --tcp 60922 and it showed python even when ps -A | grep python didn't show anything so I think it is just a false flag. Sucks when that happens.

---

