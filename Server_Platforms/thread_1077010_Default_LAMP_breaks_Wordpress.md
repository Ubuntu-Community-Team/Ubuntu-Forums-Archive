---
title: "Default LAMP breaks Wordpress"
date: 2009-02-21
forum: Server Platforms
---

### Post by rage9 on 2009-02-21
Just set up my first Ubuntu Server on a VPS (8.10) following the instructions [here]("http://www.howtoforge.com/perfect-server-ubuntu-8.10"). 

The major problems is I can't add plugins to wordpress for some odd reason, and I wonder if it has something to do with the default LAMP setup.

Hopefully someone has run into this before:

```
Warning: include_once(/home/brad/www/wp/wp-content/plugins/all-in-one-seo-pack/) [function.include-once]: failed to open stream: Success in /home/brad/www/wp/wp-settings.php on line 473

Warning: include_once() [function.include]: Failed opening '/home/brad/www/wp/wp-content/plugins/all-in-one-seo-pack/' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /home/brad/www/wp/wp-settings.php on line 473
```

I'm not sure how you can fail yet have Success.  folder permissions are set to 755 not any reason they can't be read.

I have also tried it on my 8.10 desktop and it doesn't work there either, which makes me think it's some kind of config issue.

Thoughts?

---

### Post by tubezninja on 2009-02-22
It might be a config issue, but I can say that I've installed Wordpress on my own setups, and helped install wordpress for others on ubuntu servers using the default LAMP package, without issues.  I don't use the wordpress package that's in the ubuntu repos, though; I always go with a fresh isntall of the current version on wordpress' download page.  But the LAMP package is stock ubuntu.

Who's your VPS provider?  Maybe their setup has some quirk.  I know most forgo the kernel that comes with ubuntu for a custom-compiled version that works with Xen or whichever VM engine they're using.

---

### Post by rage9 on 2009-02-22
It's actually looking like the auto install is just fubared, which is what I was using.  Manually installing plugins seems to work.  Anyone else run into this issue?

---

### Post by rage9 on 2009-02-22
> **scaredpoet said:**
> It might be a config issue, but I can say that I've installed Wordpress on my own setups, and helped install wordpress for others on ubuntu servers using the default LAMP package, without issues.  I don't use the wordpress package that it's in the repos, though; I always go with what's on wordpress' download page.  But the LAMP package is stock ubuntu.

Who's your VPS provider?  Maybe their setup has some quirk.  I now most forgo the kernel that comes with ubuntu for a custom-compiled version that works with Xen or whichever VM engine they're using.

I'm using VPSville.com

---

### Post by tubezninja on 2009-02-22
> **rage9 said:**
> I'm using VPSville.com

Never heard of 'em, but you're probably right that auto-install is the issue.   I choose not to auto-install, myself.  Not because I've had problems, but because I've been handling wordpress installations since before auto-install existed, and it's just force of habit.

---

### Post by rage9 on 2009-02-22
I typically always install plugins by hands too, figured they have an auto install I'd give it a try.  Guess not, wish I had figured that out 4 hours ago.

---

