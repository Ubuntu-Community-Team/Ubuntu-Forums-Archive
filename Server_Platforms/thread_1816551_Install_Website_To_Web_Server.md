---
title: "Install Website To Web Server"
date: 2011-08-02
forum: Server Platforms
---

### Post by Brooksy_FC on 2011-08-02
Hey All,

I've installed LAMP and I can now log into phpmyadmin.

I've been sent the website I need to work on, but I don;t know how to install it to the server. I need to put an RSS feed onto it.

I'm new to LAMP so bare with :)

Any Ideas?

---

### Post by Chiel92 on 2011-08-02
I suppose you want to copy that website to your local computer, so you can work on it offline? 
Then you probably want to copy that website to your www map. In your www map is /var/www (if you didnt change it)

If you want a database migrated, you can export it via phpmyadmin, and import it in the other phpmyadmin.

---

### Post by Brooksy_FC on 2011-08-02
Yeah, I've got the index.html file. I've saved it to my documents and i've copied it to the /var/www folder. 

I'm running it off WiFi

How do I access the website now so I can start editing it?

---

### Post by akakingess on 2011-08-02
You will need to edit it manually or with whatever design software you choose, if you just want to view if it is working and is up and running you should be able to enter "localhost" into your address bar in FireFox (for example) and see the index.html that is currently in the WWW directory.

---

### Post by Brooksy_FC on 2011-08-02
Ok man, cheers.

What software would you recommend? I need to add an RSS Feed and a calender (with a password protection)

---

### Post by WorMzy on 2011-08-02
A simple text editor, like gedit, should suffice. Assuming you know what you're doing.

---

### Post by 3rdalbum on 2011-08-02
1. Keep a copy of the original files you were sent.

2. Work with another copy that's in your home directory.

3. When you want to test your changes on the live server, copy them to /var/www.

In short, keep a backup and don't do your work on the live copy.

---

### Post by Brooksy_FC on 2011-08-02
In my var/www file, I've got an index.html and a testphp.php from when I was setting it up. Can I delete them?

If I do, what files do I need to copy over. The files I,ve been sent as a css, img and js in folders and an index.html

---

### Post by Brooksy_FC on 2011-08-02
I've dragged them in the folder and all I get is "It Works" when I type localhost. 

Also I can't view the pictures on the site, am I doing something wrong?

---

### Post by Wim Sturkenboom on 2011-08-02
The files that you received did not contain an index.html. So when you go to [http://localhost](http://localhost), it will still use the original file that was there already; it probably takes precedence over e.g. an index.php.

```

sudo mv index.html index.html.old

```
will move index.html out of the way.

As an alternative, you can figure out which file you 'have'. assuming it's called *abc.html*, use [http://localhost/abc.html](http://localhost/abc.html).

With regards to images
[LIST]
[*]filenames in Linux are case sensitive; so Img01.jpg is not the same file as img01.jpg; if the html refers to Img01.jpg but the file is img01.jpg, it will not work
[*]there might have been a separate directory where all images are supposed to be located and you copied them somewhere else; time to analyze the code and check the apache error logs (in /var/log/apache or /var/log/httpd; not sure which one exists)
[/LIST]

---

### Post by Brooksy_FC on 2011-08-02
Thanks for your help, I can now view the webpage, but I just can't see the images :confused:

---

### Post by Wim Sturkenboom on 2011-08-02
As I said, check the apache error logs. It should tell you exactly what can't be found.

Alternatively read the source of the webpage (in the browser). Search for an image tag, see to which image (complete path) that tag refers to and check if that image exists at the given location.

---

### Post by Brooksy_FC on 2011-08-03
I tried to open the error log, but it says it is unable to open. "gedit has not been able to detect the character encoding"

Also I can't see any tag lines in the browser.

---

### Post by Wim Sturkenboom on 2011-08-03
**With reagrds to the log**
Is that /var/log/apache2/error.log ? Or do you try to open another log. That log is plain ASCII text.

**With regards to the image tag**
What did you look for?
It's possible that it is the js files.

If you get a little symbol for the missing picture, right click it and check the properties. Your avatar is e.g. [noparse]http://ubuntuforums.org[/noparse]**/customavatars/avatar1294087_1.gif**; you will probably find something like the bold part

Another way to find where a known picture is used:
```

cd /var/www
grep -r -i picture.jpg *

```
This should list all files that contain 'picture.jpg'; just replace *picture.jpg* by the name of a picture that you know that exists.

---

### Post by Brooksy_FC on 2011-08-03
Ah I've figured it out. I just needed permissions.

"sudo chown" and "sudo chmod"

Thanks for your help guys!!! :D

---

### Post by lisati on 2011-08-03
*Thread moved to **Server Platforms**.*

---

