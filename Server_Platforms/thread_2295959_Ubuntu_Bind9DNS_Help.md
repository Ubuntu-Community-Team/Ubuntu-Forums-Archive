---
title: "Ubuntu Bind9/DNS Help"
date: 2015-09-22
forum: Server Platforms
---

### Post by jeff145 on 2015-09-22
Hey Ubuntu Forums,

The name is Jeff145.  And I am new to setting up DNS and Bind9 by myself.  I have been following ubuntu's own documentation page (found here: [https://goo.gl/vtycJJ](https://goo.gl/vtycJJ)).  And tried my best to get it working.  However when I do I get the following error:

[IMG]http://i.imgur.com/MZT5zt5.png[/IMG]

I am unsure how to fix the "file not found error."  Below is a list of all configurations that I thing are, well, necessary to get this resolved.  If there is anything else that you thing I should provide then please let me know, I am more than happy to help.

[IMG]http://i.imgur.com/Ul0Jj5x.png[/IMG]
[IMG]http://i.imgur.com/QhuDpu1.png[/IMG]
[IMG]http://i.imgur.com/pkoDvJU.png[/IMG]
[IMG]http://i.imgur.com/pkoDvJU.png[/IMG]

Jeff

---

### Post by papibe on 2015-09-22
Hi Jeff. Welcome to the forum ):P

I didn't take a deep look, but at first look that the path for the files is missing the root '/':
Instead of:
```
file "etc/bind/....."
```
It should be an absolute path, usually:
```
file "**[COLOR="#FF0000"]/[/COLOR]**etc/bind/....."
```
Hope it helps. Let us know how it goes.
Regards.

BTW, it'll be less wait of your time if you copy/paste the text and wrap it in code tags, instead of taking screenshots. If you are using putty, maximize your terminal, select the text, and then paste it in browser, or other window, by pressing the mouse's middle button.

---

### Post by darkod on 2015-09-22
Yes, it looks like your leading / is the only error. Don't forget, in linux ALL starts at /. :)

Another suggestion: You used 1 for the Serial value in the db file. While that can work, good practice is to use the date and additional serial value, like yyyymmddss. Where ss is two digit serial that you increment each time you do changes the same day. When doing changes on another date, the complete serial value will be changed by the yyyymmdd anyway. Note that this Serial has to be higher after each change, you can only increment it.

---

### Post by jeff145 on 2015-09-22
Damn, I can't believe I missed that :) .  Now I'm a little embarrassed.  Haha.  Anyway, thanks for the help.  I greatly appreciate it.

Jeff

---

