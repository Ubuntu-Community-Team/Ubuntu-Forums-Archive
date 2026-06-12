---
title: "Great stuff..."
date: 2009-11-01
forum: Ubuntu One (CLOSED)
---

### Post by Clove7 on 2009-11-01
Alrightey, I'm using ubuntu 9.10. I got ubuntu one working great...what I wish I had was, when I right click something to have the option to send it to my ubuntu one folder. How would I accomplish this? Cheers :popcorn:.

---

### Post by lidex on 2009-11-02
That should be possible with Nautilus Actions. Menu system>preferences>nautilus actions configuration.

info:
[http://www.grumz.net/?q=node/260]("http://www.grumz.net/?q=node/260")
[http://www.techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/]("http://www.techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/")
[http://www.grumz.net/index.php?q=node/8]("http://www.grumz.net/index.php?q=node/8")

---

### Post by Clove7 on 2009-11-02
Here is what I've got...
 
 
[http://img267.imageshack.us/img267/7052/screenshotclove7.png](http://img267.imageshack.us/img267/7052/screenshotclove7.png)
 
It doesn't work. I guess I can't put the raw command in there, but there is no path that I know of for the mv command. It's not in /usr/bin/ like the other commands that I know of are placed. :???:

---

### Post by m4tic on 2009-11-02
Can we sync bookmarks?

---

### Post by zekopeko on 2009-11-02
> **Clove7 said:**
> Here is what I've got...
 
 
[http://img267.imageshack.us/img267/7052/screenshotclove7.png](http://img267.imageshack.us/img267/7052/screenshotclove7.png)
 
It doesn't work. I guess I can't put the raw command in there, but there is no path that I know of for the mv command. It's not in /usr/bin/ like the other commands that I know of are placed. :???:

Try something like this for the command:

```
mv 
```

and for the parameters:
 
```
%d%M ~/Ubuntu\ One
```

Try it on some test files before.
This is the above [link]("http://www.techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/") from which I took the %d%M part. Click the Legend button for more options to try instead of %d%M part if it doesn't work.

---

### Post by zekopeko on 2009-11-02
> **m4tic said:**
> Can we sync bookmarks?

Wrong thread. Install the bindwood package from synaptic for firefox.

---

### Post by lidex on 2009-11-02
> **Clove7 said:**
> Here is what I've got...
 
 
[http://img267.imageshack.us/img267/7052/screenshotclove7.png](http://img267.imageshack.us/img267/7052/screenshotclove7.png)
 
It doesn't work. I guess I can't put the raw command in there, but there is no path that I know of for the mv command. It's not in /usr/bin/ like the other commands that I know of are placed. :???:

Once you import the schema, the only thing you should have to edit is the location of your One folder. ie: "%M /your_custom_dir/%m" where "your_custom_dir" is path to destination folder...I think#-o

---

