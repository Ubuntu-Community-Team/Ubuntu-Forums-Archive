---
title: "Only some PHP files not being served"
date: 2012-02-08
forum: Server Platforms
---

### Post by monkeypigs on 2012-02-08
OK, I've had a play about with Airtime, and it wasn't doing the trick, so I removed i t, so far so good. 

Then Apache started screwing me around (could be pure coincidence, not sure) 

So, after much prattng around, Apache and PHP is now back, mod_php 5 is enabled, and phpinfo(); gives me the result I expect. 

However, my existing files, now refuse to display, just blank. Previous to this, they were fine, and I haven't removed my www direcotry so I think there should be no issue. 

So my file php.php contains 
<?
phpinfo();
?>

Which shows as normal, index.php, nothing. Thinking it might be permissions or owner issues, I've double checked them. 

I've even copied and pasted the contents of index.php into php.php - still no luck. 

I know that not everything is affected as Ajaxplorer still works - I've made sure that the owner / permissions are the same here too
I'm out of ideas now, so.... anyone able to help?

---

### Post by SeijiSensei on 2012-02-08
Make sure you have the **libapache2-mod-php5** package installed.

---

### Post by monkeypigs on 2012-02-09
Yeah, I can confirm that that's installed, been reinstalled, been purged and reinstalled and I'm still just as confused!

---

### Post by Azdour on 2012-02-10
Hi,

This is a really long shot, have you tried Ctrl+F5 to refresh the page in the browser?

---

### Post by monkeypigs on 2012-02-10
LOL Yes, tried that, multiple machines too!

---

### Post by Doug S on 2012-02-10
Another long shot - By default PHP does not work in user directories. The /etc/apache2/mods-available/php5.conf file needs to be edited (the file has a comment saying what to do). I don't know if you are trying to do some of these things out of your user public_html directory or not.

---

### Post by monkeypigs on 2012-02-10
Ah! I thought you might be onto something there!

Alas, I've tried it and still no further forward

---

### Post by SeijiSensei on 2012-02-12
First, what do you see in /var/log/error.log?  If you get purely a blank page, it's often because the script needs to load a require() or include() that it can't find and then crashes.  Restrictive permissions can also cause failures like these.  All PHP errors are logged to error.log, so it's the first place to look when troubleshooting.

---

