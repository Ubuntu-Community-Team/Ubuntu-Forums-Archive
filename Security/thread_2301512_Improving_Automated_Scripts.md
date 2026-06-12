---
title: "Improving Automated Scripts"
date: 2015-11-02
forum: Security
---

### Post by branau on 2015-11-02
In an effort to teach myself a bit more about Linux and the many programs available, I wrote up a PHP script that grabs a random man page, saves the text into a file, and then sends that file to the web server that hosts my personal website. I don't own the server, I just pay monthly for access so I don't have sudo access or any elevated privileges really. Anyways, I then added a cron job to automatically run my script for me once a week. On the server, I wrote up a separate script that posts the man page into my website as a blog post for easy reference, which I also set up on a cron job, and I set up another cron job to send the text of the man page to myself in an email once a week so that I would be sure to see it. I'm still relatively new to Linux, so I'm hoping that I can find some ways to improve the security of these scripts. Any help would be greatly appreciated.


On my computer: 

get-random-man-page.php
```

<?php
// Get a list of all available man pages
$man_pages = shell_exec('/usr/bin/man -k .');
$man_pages = explode("\n", $man_pages);


// Grab a random one, and then separate its name from the details
$random_man_page = $man_pages[rand(0, count($man_pages))];
$random_man_page = explode(' ', $random_man_page);


// Get the week number (used in file naming)
$week = "week-" . date('W');


// Get the text from the random man page
$data = shell_exec("/usr/bin/man {$random_man_page[0]}");


// Set up the file name and the link for later
$new_file = "$week-" . str_replace(".", "-", $random_man_page[0] . ".txt";
$link_to_new_file = "http://me.com/" . strtolower(str_replace(array("(", ")", ":", ".txt"), "", $new_file));


// Remove white space from each line
$paragraphs = explode("\n\n", $data);
$paragraphs = array_map(function($paragraph) {
  $paragraph = explode("\n", $paragraph);
  $paragraph = array_map(function($line) {
    if(strlen($line) > 0) {
      if (substr($line, 0, 7) == "       ") {
        $line = substr($line, 7);
      }
    }
    return $line;
  } , $paragraph);
  return implode("\n", $paragraph);
}, $paragraphs);


// Save the newly-formatted man page to a file
file_put_contents("/home/me/Documents/PersonalWebsite/public_html/mpotw/$new_file", array("Having trouble reading this? Check it out on my site: $link_to_new_file \n\n" . implode("\n\n", $paragraphs)));


// Sync my local files with the web server
shell_exec("/usr/bin/rsync -vrutze ssh /home/me/Documents/PersonalWebsite/ me@me.com:");

```

crontab
```

0 9 * * 0 /usr/bin/php /home/billy/Documents/get-random-man-page.php

```

On the web server:

post-random-man-page.php
```

<?php


// The blog is built using WordPress and calls for a WP function
require 'wp-blog-header.php';


// Get the latest file in the directory where the man pages are stored
$latestFile = str_replace("\n", '', shell_exec('/bin/ls -tp public_html/mpotw/ | /bin/grep -v /$ | /usr/bin/head -1'));
$file = dirname($_SERVER['PHP_SELF']) . "/mpotw/$latestFile";
$data = file_get_contents("$file");




// Various formatting fixes to make the man page more readable
// on the web site.
$paragraphs = explode("\n\n", $data);


$paragraphs[1] = "<h2 style=\"text-align: center; max-width:565px; width:95%; margin:auto;\">" . $paragraphs[1] . "</h2>";


unset($paragraphs[0]);
$paragraphs = array_map(function($paragraph) {
  $paragraph = explode("\n", $paragraph);
  $paragraph = array_map(function($line) {
    if(strlen($line) > 0) {
      if (preg_match("/^[A-Z]+\s*[A-Z]*\s*$/", $line)) {
        $line = "<h3 style=\"max-width:565px; width:95%; margin:20px auto 5px;\">{$line}</h3>";
      } 
      if (strpos($line, "Linux Programmer's Manual") !== false) {
        $line = "<h2 style=\"text-align: center; max-width:565px; width:95%; margin:auto;\">$line</h2>";
      }
      if (strlen($line) > 3) {
        if ($line[strlen($line) - 1] == "&#8208;") {
          $line[strlen($line) - 1] = '';
        }
        if ($line[strlen($line) - 2] == "&#8208;") {
          $line[strlen($line) - 2] = '';
          $line[strlen($line) - 1] = '';
        }
      }
    }
    return $line;
  } , $paragraph);
  if (strpos($paragraph[0], "<h3") === false && strpos($paragraph[0], "<h2") === false && strlen($paragraph[0]) > 2) {
    $paragraph[0] = "<pre style=\"white-space:pre-wrap; max-width:565px; width:95%; margin:auto;\">" .$paragraph[0];
  } else if (strpos($paragraph[1], "<h3") === false && strpos($paragraph[1], "<h2") === false && count($paragraph) >= 2) {
    $paragraph[1] = "<pre style=\"white-space:pre-wrap; max-width:565px; width:95%; margin:auto;\">" . $paragraph[1];
  } else if (count($paragraph) == 1) {
    $paragraph[0] = "<pre style=\"white-space:pre-wrap; max-width:565px; width:95%; margin:auto;\">" .$paragraph[0];
  } 
  $paragraph[count($paragraph) -1] = $paragraph[count($paragraph) -1] . "</pre>";
  return implode("\n", $paragraph);
}, $paragraphs);


// Info for posting the man page into the WP site
$post_slug = str_replace(".txt", "", $latestFile);
$post_name = str_replace("-", " ", $post_slug);


$post = array(
  'post_content'   => implode("\n", $paragraphs),
  'post_name'      => $post_slug,
  'post_title'     => $post_name,
  'post_status'    => 'publish',
  'post_author'    => 1,
  'post_excerpt'   => $paragraphs[0],
  'post_date'      => date("Y-m-d H:i:s"), // The time post was made.
  'post_date_gmt'  => gmdate("Y-m-d H:i:s"), // The time post was made, in GMT.
  'post_category'  => array(2, 3) // Default empty.
);  


wp_insert_post($post);

```

crontab
```

0 9 * * 1 /bin/cat /home/wbrawner/public_html/mpotw/"`/bin/ls -tp /home/wbrawner/public_html/mpotw/ | /bin/grep -v /$ | head -1`" | /usr/bin/mail -v -s "Man Page of the Week" "me@gmail.com,a_friend@gmail.com"
45 8 * * 1 /usr/local/bin/php /home/me/public_html/post-newest-man-page.php


```




Thanks in advance for any help!

---

### Post by TheFu on 2015-11-03
Using 'ls' in a script is a bad idea--unexpected output is common.
There are very few reasons to use 'cat'; usually it is a wasted process and pipe. That entire line would be better inside a script... IMHO.

For php:  [https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)

---

### Post by Lars Noodén on 2015-11-03
One finesse would be to validate or sanitize your *$random_man_page[0]* data before sending it out to the system again.  

```

...
$man_pages = shell_exec('/usr/bin/man -k .');
...
$data = shell_exec("/usr/bin/man {$random_man_page[0]}");
...

```

It's not a big risk in this particular case but more a situation of dotting i's and crossing t's and one should never trust input from outside the program.

---

### Post by branau on 2015-11-04
> **TheFu said:**
> Using 'ls' in a script is a bad idea--unexpected output is common.

I came up a different technique to get the file I'm looking for. Since I always save them to a specific folder and follow a specific naming convention, I used this command:

```
find home/me/public_html/mpotw/ -name "week-`date +%W`*"
```

How is that?

> **TheFu said:**
> There are very few reasons to use 'cat'; usually it is a wasted process and pipe. That entire line would be better inside a script... IMHO.

I went ahead and dropped the cat command and wrote up a script for the rest of it. How does this look?

```
#!/bin/bash
MAIL=/bin/mail
FIND=/usr/bin/find
DATE=/bin/date
WEEK=`$DATE +%W`


# Get the latest man page of the week
FILE=`$FIND /home/wbrawner/public_html/mpotw/ -name "week-$WEEK*"`


# Send it via mail
$MAIL -v -s "Man Page of the Week" "me@gmail.com" < $FILE
```

> **TheFu said:**
> For php:  [https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)

That's quite a bit of info there, definitely a few weeks worth of reading. I'll take a look at it though, thanks!

> **Lars Noodén said:**
> One finesse would be to validate or sanitize your *$random_man_page[0]* data before sending it out to the system again. 

I modified the script as so:
```
$man_pages = shell_exec('/usr/bin/man -k .');
$man_pages = filter_var_array($man_pages, "FILTER_SANITIZE_STRING");


$data = shell_exec("/usr/bin/man {$random_man_page[0]}");
$data = filter_var_array($data, "FILTER_SANITIZE_ENCODED");
```

I figured a simple string filter for the titles would be good, since I'm only going to be getting alphanumeric titles for the man pages, and an encoded filter for the actual text, since I've seen that they sometimes have code in them.

---

