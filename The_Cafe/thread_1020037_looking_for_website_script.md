---
title: "looking for website script"
date: 2008-12-23
forum: The Cafe
---

### Post by trash on 2008-12-23
I've been searching but can't find anything that will do what i need so I figured I ask here.

My brother has a business that is open or closed depending on the weather, so on his website I stuck one of those weather.com banners that shows the weather and states if below -15 we're probably closed.

However, it's not perfect as if it's sunny and no wind but -15 we might be open lol.

So what i am looking for is a simple open/closed button that when clicked will present a password dialog box and allow my brother to change the status from the website... does such a thing exsist and where can i find it?

---

### Post by jonabyte on 2008-12-27
I doubt something that specific exists, you may need the services of a web developer.
What technologies are you using for the site?

---

### Post by trash on 2008-12-27
Ah thanks, I didn't think it would be that complicated. Nothing special for the site but I assumed something cgi would exsist. I was going to use ICQ messenger since they have an online notifier but figured i would at least check to see if what i wanted exsisted.
I'll keep looking aroung for something that could work.. thanks.

---

### Post by klange on 2008-12-27
I'm assuming the server has PHP, right? There are number of easy ways to do this. I'll edit one into this post (let me write it out first).

First up is the open indicator. You can edit the HTML to suit your needs:
[php]
<?php
   $open_indicator = file_get_contents("are_we_open"); // Replace this if you want, it's a file name.
   if (strlen($open_indicator) < 1) {
       echo "Error collecting business operation status."; // The indicator has not been set.
   } else {
       if ($open_indicator == "y") {
           echo "We are OPEN"; // Or whatever you want, maybe an image?
       } elseif ($open_indicator == "n") {
           echo "We are CLOSED";
       } else {
           echo "Business operation status could not be determined."; // (the file contains something, but not what we expected.
       }
   }
?>
[/php]
If the server is set up to parse regular HTML documents with PHP, you can just stick this somewhere, otherwise you may need to use an <IFRAME> to get the job done.

Next we have to have a way to change this. The best bet is to just make a new directory, say "admin" or something to that effect, and put an .htaccess and .htpasswd in it:
**.htaccess**:
```

AuthUserFile  */path/to/.htpasswd*
AuthName  "*Some page title you want to use*"
AuthType Basic
require user *username*

```
**.htpasswd**:
```

*username*:*encrypted password*

```
(Use something like [this](http://www.askapache.com/online-tools/htpasswd-generator/) to automatically generate a .htpasswd, as you need to have a properly encrypted password)

Also in this directory should be an index.php which allows us to change the status:
[php]
<?php
    // Status changer
    if (isset($_POST['status'])) {
        echo "Setting status to {$_POST['status']}...";
        file_put_contents("../are_we_open",$_POST['status']);
    } else {
        $status = file_get_contents("../are_we_open");
        echo "<form action=\"index.php\" method=\"post\">\n";
        echo "<input type=\"text\" id=\"status\" value=\"$status\" /> (y or n)\n";
        echo "<input type=\"submit\" value=\"Set Status\" /></form>";
    }
?>
[/php]

---

### Post by trash on 2008-12-27
AWESOME! thank you!!
I'll give it a try this weekend, sounds pretty straight forward but i'll get back to you with results:)

---

### Post by trash on 2008-12-29
it's going to take me a bit longer than i thought to get to testing it... over the weekend we had 100km winds and it blew my old tin roof off! lol.
I'll post back as soon as i get around to it. Thanks!

---

