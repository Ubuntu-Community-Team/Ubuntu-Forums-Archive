---
title: "I broke something, but I don't know what."
date: 2011-10-07
forum: Server Platforms
---

### Post by pepsifx357 on 2011-10-07
I was working on a website using drupal.  I decided I would move all of my /var/www files to a spare hard drive and symlink the files to /var/www/.

That didn't work.  Now when I go to my website I get this download pop up:

```
You have chosen to open

which is a: PHTML file
from: http://localhost

What should Firefox do with this file?
```

Meanwhile in the background my website just looks like a blank sheet of paper.  White.

I have a music folder in there, so if I go to localhost/music it will go to that fine.  I must have messed up PHP or something.

Anyone........help?


Thanks

Edit: I moved everything back to the folder and it's still doing the same thing.

---

### Post by bbqroast on 2011-10-08
Nothing is badly broken, your just giving Firefox a '.PHTML' file, something that it does not know how to handle, so instead it just asks you if it wishes to download it. Try downloading the file and opening it in notepad to see what it is...

Most likely diagnosis:
Its a php-html file, firstly you should rename it to .php and secondly you should use:
> header('Type: text/html');
To tell Firefox that the file is a html file :).
I think that should fix that (I guessed the code above but it should work :));

---

### Post by pepsifx357 on 2011-10-08
Thanks for the quick reply.  I was about to go and do what you said, but when I went to localhost...It just all of the sudden decided to start working.

Weird.  I wonder why it was doing it yesterday and now it fixed itself?

Thanks anyways

---

