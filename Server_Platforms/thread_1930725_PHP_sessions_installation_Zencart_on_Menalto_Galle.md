---
title: "PHP sessions installation Zencart on Menalto Gallery v3.0"
date: 2012-02-24
forum: Server Platforms
---

### Post by bdfoto on 2012-02-24
Hi everyone

May I start by saying that my knowledge of messing around with server settings could easily be written on the back of a very small postage stamp with a very large marker pen.

Please treat me as a total dork in such matters.

I am trying to install Zencart v139h-110108 on a Menalto Gallery website using v 3.0

There is a version 3.2 but I back-tracked after suffering minor problems.

My installation cannot proceed because ... "In order to use Zen Cart™, you will need to be able to use the "session" capabilities of PHP. It could be that your server configuration is not currently allowing PHP sessions to start and interact properly. Also, if you have session cookies disabled in your browser, you will not be able to use PHP session support. Please turn off cookie-blocking tools in your browser and firewall as a precaution."

My ISP has confirmed that my required settings are correct, but won't / can't help me further as this is outside their remit.

On the subject of browsers I have the choice of Google Chrome and Mozilla Firefox current versions.  I also have Safari available to me bit never use it.

My first choice is Google Chrome.

In words of preferably slightly less than two syllables, could someone please explain what I have got to do please.

I have Putty available to me.

Thank you everyone in advance.

---

### Post by SeijiSensei on 2012-02-25
First, I'd ask the hosting provider where the access and error logs for your server are stored.  I've never worked in a shared hosting environment, so I haven't a clue where these would be.  PHP errors generally appear in the web server's error log.

Next, let's make sure your provider's PHP implementation has support for sessions.  In your web server's root directory (where index.html lives), create a file called info.php that contains just this code:

```
<?php
phpinfo();
?>

```

Now view info.php from a browser.  It will provide a detailed summary of the PHP implementation.  About three-quarters of the way down the page you should see a block of information marked "session" and "Session Support" should be "enabled."  If that's all correct, we'll need to see the errors being logged.

---

