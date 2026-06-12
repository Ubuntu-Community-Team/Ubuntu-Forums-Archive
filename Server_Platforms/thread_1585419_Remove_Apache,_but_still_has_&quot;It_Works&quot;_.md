---
title: "Remove Apache, but still has &quot;It Works&quot; page ?"
date: 2010-09-30
forum: Server Platforms
---

### Post by bangrobe on 2010-09-30
I have 2 questions :
1. I installed lamp, and it work well. I build some website with Joomla and Wordpress, and try to make the link more friendly (SEF) . But when I clicked on the link, It only appeared 404 page. With normal link, that problem didn't happen. So I uninstall lamp, followed by this link : [http://tuxtweaks.com/2010/01/how-to-uninstall-lamp-in-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2010/01/how-to-uninstall-lamp-in-ubuntu-9-10-karmic-koala/) ( I use Lucid 10.04, but they are the same) . The question is : Why did SEF link broke?

2. After removing lamp, I downloaded and used Xampp for Linux. All things work well, too. But It has a problem which make me discomfortable : It still has "It works" page, when I type address [http://localhost](http://localhost). It's so annoying. It shoud be display a homepage of Xampp.
So the question is : what thing still left after removing Lamp, and how to completely delete the It works page to display homepage of Xampp ?
Thank you for your help.

---

### Post by sanderd17 on 2010-09-30
If you place an index.html page in the directory /var/www, any lamp server will display that page.

EDIT: you probably need to adapt the user rights to make that file or make the file as root.

---

