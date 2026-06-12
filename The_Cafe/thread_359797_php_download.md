---
title: "php download"
date: 2007-02-12
forum: The Cafe
---

### Post by highneko on 2007-02-12
I just downloaded a file from the ubuntu forums and it was php code. I think it's called "unparsed". Anyways, I'm wondering if that's a security issue and I should report this? I was always told that it this kinda thing is a security problem. Maybe vbulletin is secure tho?

---

### Post by Steveire on 2007-02-12
I'm sure it's fine.

You probably downloaded a file like showthread.php or something? It's probably just the same html that you see when you look at view > source, or whatever it is in firefox. Send the file to a moderator or admin if you're concerned. 

Have you been able to recreate it?

---

### Post by ubuntu-geek on 2007-02-12
If you have this issue please clear your browser sessions.

---

### Post by kebes on 2007-02-12
Yes I experienced the same thing. For about 10 seconds all the forum pages were not being parsed. I'm guessing they were in the middle of doing some kind of upgrade or switchover that momentarily broke the server.


Depending exactly what happened, this could be a security breach. (Sometimes the raw PHP contains passwords.) Is the forum staff aware that this happened? (Perhaps now would be a good time to change the database access passwords?)

---

### Post by highneko on 2007-02-12
> **Steveire said:**
> I'm sure it's fine.

You probably downloaded a file like showthread.php or something? It's probably just the same html that you see when you look at view > source, or whatever it is in firefox. Send the file to a moderator or admin if you're concerned. 

Have you been able to recreate it?
Yes, it was the showthread.php. I was just surfing the forum then pressed the refresh button and it asked me if I wanted to save the php file. I knew this was most likely gonna be the unparsed file. So I thought it was be fun to download it and take a look, especially since I have been curious about vbulletin. It has the licence number and version info. I think that alone can't be a good thing. I have no idea what a licence number is tho.

---

### Post by Steveire on 2007-02-12
Things like this and a whole lot more? 
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html dir="ltr" lang="en">
<head>
	<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<meta name="generator" content="vBulletin 3.6.4" />

<meta name="keywords" content="php download, ubuntu forums,ubuntu linux,ubuntu,linux fourm,ubunut forum,linux ubuntu,ubuntu support,ubuntu help,ubuntu linux help" />
<meta name="description" content="php download Ubuntu Cafe" />


<!-- CSS Stylesheet -->
<link rel="stylesheet" type="text/css" href="clientscript/vbulletin_css/style-7a7f7573-00032.css" id="vbulletin_css" />

<!-- / CSS Stylesheet -->

<script type="text/javascript">
<!--
var SESSIONURL = "";
var IMGDIR_MISC = "http://ubuntuforums.org/images/uf/misc";
var vb_disable_ajax = parseInt("0", 10);
function jabberwindow(userid, width, height)
{
 return openWindow('sendmessage.php?' + SESSIONURL + 'do=jabber&u=' + userid, width, height);
}
// -->
</script>
<script type="text/javascript" src="clientscript/vbulletin_global.js?v=364"></script>
<script type="text/javascript" src="clientscript/vbulletin_menu.js?v=364"></script>

<link rel="alternate" type="application/rss+xml" title="Ubuntu Forums RSS Feed" href="external.php?type=RSS2" />

<link rel="alternate" type="application/rss+xml" title="Ubuntu Forums - Ubuntu Cafe - RSS Feed" href="external.php?type=RSS2&amp;forumids=11" />


<script src="http://www.google-analytics.com/urchin.js" type="text/javascript">
</script>
<script type="text/javascript">
_uacct = "UA-361826-1";
urchinTracker();
</script>
	<title>php download - Ubuntu Forums</title>
	<script type="text/javascript" src="clientscript/vbulletin_post_loader.js?v=364"></script>
</head>

```
It's the html source code which firefox evaluates to build what you see on screen. Hit view > page source to see more.

---

### Post by ~LoKe on 2007-02-12
PHP is serverside and will never be served in a format that you can actually download.  Anything written between the <?php and ?> tags will never be printed.

---

### Post by Crashmaxx on 2007-02-12
Oh good, so I'm not the only one getting that today. I was messing with my squid config and thought I must have broke something. I was changing settings then all the sudden, I click on ubuntuforums.org and its like "Save As" and I'm sitting here thinking I broke something. Especially since I had a similar problem with Webmin doing that for no apparent reason.

Good to know its your server and not mine. :lol:

---

