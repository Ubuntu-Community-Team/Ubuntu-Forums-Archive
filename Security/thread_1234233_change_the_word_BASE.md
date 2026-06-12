---
title: "change the word BASE"
date: 2009-08-07
forum: Security
---

### Post by TUDORS on 2009-08-07
daer all 
dear all how can i change the word base in the top of page to any other word such as in this picture [http://bodhizazen.net/img/IDS/base_1.JPG](http://bodhizazen.net/img/IDS/base_1.JPG) 
best regards

---

### Post by ajgreeny on 2009-08-07
I don't understand exactly what you mean, unless you mean you want to edit the html code of the web-page linked to change the word.  If so, you can do so with a text editor if you know how to do it the hard way, or with a wysiwyg, eg kompozer if you need a GUI.

---

### Post by TUDORS on 2009-08-08
i want to change term (basic analysis and security engine) BASE to 
(TUDORS)
and change kevin johnson to TUDORS 

best regards

---

### Post by TUDORS on 2009-08-08
up

---

### Post by TuckLive on 2009-08-09
You'll need to change the html code that is located in /var/www/base.  I don't remember the filename, but look in that directory.

---

### Post by TUDORS on 2009-08-09
thank you for your help but can you locate exaxtly wich file because i couldnot find it

---

### Post by TuckLive on 2009-08-10
To change the footer edit the file /var/www/base/base_conf.php.  Look at line 59 and edit this entry:

```
    /* Custom footer addition.  The below variable, if set, will cause
           *  base_main.php to include what ever file is specified.
           *  A sample custom footer file is in the contrib directory
           */
          $base_custom_footer = '';

```

You should leave recognition for the developers somewhere on the page though.

---

