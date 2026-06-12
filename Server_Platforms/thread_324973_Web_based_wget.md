---
title: "Web based wget"
date: 2006-12-24
forum: Server Platforms
---

### Post by mulligan.can on 2006-12-24
Is it possible to get a web based interface for wget? I would like to be able to get my headless server downloading stuff without having to have a ssh connection or similiar controlling it.

I guess I am thinking of something like torrentflux but for wget/normal http/ftp downloads rather then bittorrent downloads.

Am I making sense here?

---

### Post by kidders on 2006-12-24
Hi there,

Do you mean you would like to be able to use HTTP to instruct your box to start downloading something?

**Edit:** If so, you should be able to whip up a quick PHP script to do that for you fairly easily. One thing to check first though. I'm not 100% positive that a download triggered by a PHP script executed by Apache, say, would stay alive very long. You could test by writing a script to do something long and pointless, and see what happens:

```

<?php
echo "Trying to start a long, pointless process: ";
echo `cat /dev/random > /dev/null &`;
?>

```

If the page loads instantly, and the "cat" process stays in your process list for any longer than 30 seconds or so, you're in business :D You would be able to create a web page that prompts the user for a URL and sets a download in motion.

---

### Post by mulligan.can on 2006-12-24
Well, I really feel stupid now. Never thought about potentially writing something myself. Gosh. Ok, I guess I'll try and make something up in php.

However, I am still interested in finding out if there is anything like that available already. Just something similiar to torrentflus except for wget.

I read a mention of something called Web.get in an unrelated thread however I haven't been able to find anything further on it.

---

### Post by kjacks on 2006-12-25
webmin is a bit overkill for what your asking, but it is web based and can do it.  Under the "others" tab there's a field "upload and download" you can enter a URL for your server to download.  You can also schedule for when you'd like it to be download (i.e. when your not surfing the net)

Hope this helps.

---

### Post by mulligan.can on 2006-12-25
Well, considering had planned on installing webmin anyway...

Thanks, that sounds like it will do the trick. at least for the time being. Don't feel to comfortable opening webmin up to the greater internet though :)

Well, again, thanks a lot :D

---

