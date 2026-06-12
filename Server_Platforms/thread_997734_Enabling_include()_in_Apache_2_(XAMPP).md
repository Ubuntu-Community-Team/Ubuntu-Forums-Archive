---
title: "Enabling include() in Apache 2 (XAMPP)"
date: 2008-11-30
forum: Server Platforms
---

### Post by sim_thomas96 on 2008-11-30
Im not sure if this is the exacly right category but, its still a server issue. I have a beta of new version of my blog on a localhost server. I tried to include() a php file but it came with that error in a place where I tried to include it.

```

Warning: include() [function.include]: URL file-access is disabled in the server configuration in /opt/lampp/htdocs/blogv2/wp-content/themes/devart/sidebar.php on line 42

Warning: include(http://www.localhost/blogv2/wp-content/themes/devart/ads.php) [function.include]: failed to open stream: no suitable wrapper could be found in /opt/lampp/htdocs/blogv2/wp-content/themes/devart/sidebar.php on line 42

Warning: include() [function.include]: Failed opening 'http://www.localhost/blogv2/wp-content/themes/devart/ads.php' for inclusion (include_path='.:/opt/lampp/lib/php') in /opt/lampp/htdocs/blogv2/wp-content/themes/devart/sidebar.php on line 42

```

Can anyone help me. I guess that I need to enable include() in server config, but how?

---

### Post by Dr Small on 2008-11-30
What is your php code?
You should not be including a **URL** but rather a relative address to the file on your system.

---

### Post by sim_thomas96 on 2008-11-30
True, one error removed. Code:
```

    <div class="block">
        <?php
        include '/blogv2/wp-content/themes/devart/ads.php';
        ?>
    </div>

```

---

