---
title: "Apache disable read css js"
date: 2008-09-01
forum: Server Platforms
---

### Post by johan.alfa on 2008-09-01
Hello all,

Situation

Webserver has following directory stucture

/var/www/ as web root

/var/www/index.html
/var/www/foo.css
/var/www/foo.js
/var/www/foo.txt

If a user types /var/www/foo.css as URL in his browser then foo.css is readable.

Is it possible to disallow direct downloading of certain types of files in apache?

I dissabled directory reading but still people try to hack apache with trying all kind off guesses.

greetings,

---

### Post by James79 on 2008-09-01
I used to put something along these lines in my configuration file when I used to use an old version of Apache for Windows:

```
<Files ~ "*.inc">
    Order deny,allow
    Deny from all
</Files>
```

I'm sure the option is similar in modern Apache on Linux..

*However*, this won't solve your problem. You can't disable "direct" access to the .css file and still expect it to be usable "within" your site. You can't have it both ways.

Are you trying to protect your css code? You can't. The only way to prevent people from accessing your files is to not make them publically available in the first place :)

---

### Post by johan.alfa on 2008-09-02
Hello,

I do not want to protect those files.
I just would like it if hackers were not able to fish.

greetings,

---

### Post by mbeach on 2008-09-02
If you want the browser to be able to render your page correctly, you'll need to serve up the css files.  Its really just an extension of the html file, so its sort of like saying you don't want people to be able to view your page source - but without that, they can't view your page.

---

