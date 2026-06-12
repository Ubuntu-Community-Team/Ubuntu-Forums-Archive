---
title: "Multiple alias in apache2"
date: 2010-07-14
forum: Server Platforms
---

### Post by mattc9305 on 2010-07-14
Hi,
    I'm trying to set up a website using apache2 and when I add the line 'Alias' it will work fine.  But if I add any more then they refuse to either work or be detected because I get the 'Not Found' page.  (Only the first alias works.)

Grateful for any help :).

Thanks.

---

### Post by ruffEdgz on 2010-07-14
In your apache configuration, you should be able to have multiple 'Alias' lines but they must be different URL PATH (which is the first part of the 'Alias' directive).

Good way to use 'Alias':
```

Alias /images /var/www/images
Alias /test /var/www/test
```

Bad way to use 'Alias':
```

Alias /images /var/www/images
Alias /images /usr/local/images
```

I have a apache configuration which has different URL paths pointing to different DIR paths but I don't see why you couldn't have different URL paths point to similar DIR paths.

Example:
```

Alias /images /var/www/images
Alias /imagestest /var/www/images
```

If this isn't want you are talking about, please provide a small snippet of code of what you are trying to accomplish.

---

### Post by mattc9305 on 2010-07-14
Thanks for that :).  The problem just seemed to fix itself on its own.

Now I have a different one... joy of joys...  I have a link on a page to a different page on my website.  If I type the URL in directly into the address bar of the site then it will work fine, but if I use the link that I have placed on a different page then the page will appear but it will be simple text and no colour without any pictures and everything will be misaligned.

This one has be stumped :S

---

### Post by ruffEdgz on 2010-07-14
When you are on the page that has the link and click on it, does the URL at the top show the desired location or something different?

If you use Firefox, you might want to download the extension called 'Firebug' ([https://addons.mozilla.org/en-US/firefox/addon/1843/](https://addons.mozilla.org/en-US/firefox/addon/1843/)) to see if all your tags are pointing to the correct location, etc... When I can't see images or a template I want to use, its because I needed to point my webpage to the correct CSS file, etc...

The problem you are experiencing sounds more of a coding thing then a systems thing :D

Hope this helps and please update again if you can give more information of what you find.

---

### Post by mattc9305 on 2010-07-14
Yup, it shows exactly what I and the link is exactly what is being typed into the address bar.

---

### Post by ruffEdgz on 2010-07-14
Can you update your next post with just the snippet of code that you have configured for this website?

You might also want to show the code for the page that has the link and the code for the page it should display (HTML code that is).

I still don't see this problem as an apache service thing but to make sure what it might be, check the directory /var/log/apache2 and see if the 'error.log' file has anything on there that shows your problem as well. If none of the log files help, then lets take a look at the apache configuration and HTML code some and see if we can get this.

---

### Post by mattc9305 on 2010-07-14
I didn't write the code but I think this might have something to do with it.  This is part of the index.php file.

```
$path = GalleryUrlGenerator::getCurrentRequestUri();
if (preg_match('|^(/(?:[^?#/]+/)*)(.*)|', $path, $matches)) {
    $path = $matches[1] . GALLERY_MAIN_PHP;
    if (!empty($matches[2]) && ($pos = strpos($matches[2], '?')) !== false) {
        $path .= substr($matches[2], $pos);
    }
}

$configBaseUri = @$gallery->getConfig('baseUri');

$urlGenerator = new GalleryUrlGenerator();
$urlGenerator->init(!empty($configBaseUri) ? $configBaseUri : null);

$phpVm = $gallery->getPhpVm();
$phpVm->header('Location: ' . $urlGenerator->makeUrl($path));
?>

```

---

### Post by mattc9305 on 2010-07-15
Bump! :D

---

