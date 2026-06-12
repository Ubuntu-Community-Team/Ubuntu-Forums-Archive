---
title: "php5-gd not working"
date: 2008-01-25
forum: Server Platforms
---

### Post by xrvjorn on 2008-01-25
I've installed php5-gd (sudo apt-get install php5-gd) on Ubuntu Server 6.06 LTS. If I cd to /usr/lib/cgi-bin and type "./php -m", then "gd" shows up in the output list.

If I start php interactively (./php -a) and type "<? var_dump(function_exists('imagerotate'));", I get the answer "bool(false)". 

So, it seems gd is among the modules, but not working. Clues, anyone?

(BTW, I searched the forum for "gd", but found nothing.)

---

### Post by James79 on 2008-01-26
imagerotate() is [not included]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/39719") in the default ubuntu GD package.

Try displaying this script in your browser:
[HTML]
<pre>
<?
print_r(get_defined_functions());
?>
</pre>
[/HTML]

You should see other image* functions listed. Your GD is probably working just fine as intended :)

---

### Post by Dr Small on 2008-01-26
I never could get php5-gd to work, so that's why I use XAMPP.

---

### Post by xrvjorn on 2008-01-27
> **James79 said:**
> imagerotate() is [not included]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/39719") in the default ubuntu GD package.

Try displaying this script in your browser:
[HTML]
<pre>
<?
print_r(get_defined_functions());
?>
</pre>
[/HTML]

You should see other image* functions listed. Your GD is probably working just fine as intended :)

You're right, lots of other GD functions show up. Unfortunately, Captcha in the gallery software I use, which is Photopost, doesn't work. According to the Photopost guys, this happens when GD is not working. I guess that means that some of the functions that are omitted from 6.06LTS's php variant, are needed by Photoposts captcha.

---

### Post by James79 on 2008-01-28
Perhaps you can implement the routines you need yourself?

[If you look in the imagerotate() page in the php docs]("http://ca.php.net/manual/en/function.imagerotate.php"), there is a Ubuntu user there (look for username "crymsan") who worked around the issue by creating his own imagerotate() function... and provided the source code.

---

### Post by xrvjorn on 2008-01-28
> **James79 said:**
> Perhaps you can implement the routines you need yourself?

[If you look in the imagerotate() page in the php docs]("http://ca.php.net/manual/en/function.imagerotate.php"), there is a Ubuntu user there (look for username "crymsan") who worked around the issue by creating his own imagerotate() function... and provided the source code.

Hmmm... He rotates the image by calling imagecolorat (gets one pixel) and imagesetpixel in a loop, which is the slowest possible method. Doing that in an interpreted language doesn't improve things, so if the CPU hasn't been hogged before, it sure will be with that method ;).

Anyway, I'm not sure which GD functions Photopost might use, so I'd better include them all. That means that I have to try to recompile php myself. That'll be interesting since I've never compiled under Linux before, and the printout of the list of cli switches for php's configure is 6 full pages. Most of those options are quite incomprehensible to me, so I expect a steep learning curve.

---

### Post by James79 on 2008-01-28
I realize it's terribly inefficient, but if it's just for a catcha as you mentionned then it shouldn't really matter.

I would give it a try, you have little to loose and it's certainly a lot simpler than recompiling everything!

Good luck!

---

### Post by xrvjorn on 2008-01-29
> **James79 said:**
> I realize it's terribly inefficient, but if it's just for a catcha as you mentionned then it shouldn't really matter.
It's for the entire Photopost gallery software, so there are most likely more functions missing, which Photopost would need. Your link to bugs.launchpad was most helpful, since that's where I found out that several GD functions aren't included in 6.06 Server.

---

