---
title: "making directories through PHP as normal shell user"
date: 2008-06-05
forum: Server Platforms
---

### Post by orrie on 2008-06-05
I have an Ubuntu 8.04 server that is very good configured.
But, I'm wondering of something.

When I'm trying to create an folder with an PHP-script requested through http, it just gives me permission denied.
```
<?php mkdir("test",0751); ?>
```
And, I know that chmod the parent directory to 777 or changing owner of the parent directory to www-data should fix it.

But I'm wondering how I can create an folder as orrie:orrie without chmod/chown the parent directory and requesting the script through http.

Let's say that I have an folder called "parent", and I'm going in to the directory.
In this folder I have an index.php-file with the command mkdir("test",0751);
Then I don't want the "Permission denied"-error, but I want an folder called "test" created with the permissions: orrie:orrie.

I can try to illustrate this:
```

orrie@host: ~/www $ cd parent
orrie@host: ~/www/parent $ cat test.php
<?php
mkdir("test",0751);
?>
orrie@host: ~/www/parent $ php test.php
NOTICE! This will create the folder since I'm orrie:orrie logged in to my shell,
but I want it to be orrie:orrie just when I requests mywebhost.com/~orrie/parent.

```


How can I fix this?

---

### Post by molotov00 on 2008-06-05
Apache runs as user www-data. www-data is not allowed to create a folder with "permissions orrie:orrie" Only orrie can do that. Doesn't that make sense?

You should explain why this is important to you.

An approach you should consider is to make orrie and www-data members of the same usergroup. Then, you can assign read/write permissions to your php-created folders on a group level. That way both orrie and www-data would be able to have the same permissions, but other users would not.

---

### Post by hyper_ch on 2008-06-06
if you have virtual hosts and use system accounts you might want to use suPHP. That can then run apache as the according user and hence create dirs and files as that user.

---

