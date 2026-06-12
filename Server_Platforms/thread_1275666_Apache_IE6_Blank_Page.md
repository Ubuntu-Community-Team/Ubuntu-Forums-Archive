---
title: "Apache IE6 Blank Page"
date: 2009-09-26
forum: Server Platforms
---

### Post by jcortes on 2009-09-26
Hopefully I can describe my problem well enough. 

I have a script that requires the browser to refresh when a list item is changed to populate the second list. 

The problem I am having that relates to Ubuntu is that when this script is used in Internet Explorer 6 hosted on my Ubuntu server it refreshes fine about 2-3 times then goes to a blank page on the next try. 

I have a XAMPP server running on Windows and it does not have this problem with the same script in Internet Explorer 6. 

Is there a parameter I need to set to allow multiple requests or something that could be preventing it from requesting the page. I'm at a loss here, If anyone can help they would be a god. I really want to implement a Linux server on my network and get rid of this windows server.

---

### Post by jcortes on 2009-09-26
Bump

---

### Post by gali98 on 2009-09-26
Okay... First things first, You would probably find a lot more help at the apache forums:
[http://www.apacheforum.com/](http://www.apacheforum.com/)

Second, Could you provide us a link so we can see what exactly you mean? (I am having trouble following your description.)

Okay after that spiel, I have a few ideas...
First, you might check in IE in the bottom left hand corner if it shows any errors on the page.
Second, is this an ssl site or what?

Third, looking through the apache config, (/etc/apache2/apache2.conf)
these options looked like they might be something you could play with.

```
#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15
```

But your best bet would really be the apache forums.
Cheers,
Kory

---

### Post by jcortes on 2009-09-27
I appreciate the reply this appears to be a really hard problem to pin point I will check out the forums for Apache. 

I will describe it in more detail for any one else that my have ideas. 

I have a time clock script that pulls a list of classes from the MySQL database then based on the class selection it refreshes using a document.location.href to add veriables to the URL that PHP uses to populate the second list from MySQL. 

The issue is that on the linux server on specific classes that i select from the list, when it refreshes it displays a blank page like the request didn't go through. However it works fine on the windows server not to mention it only fails in IE6. 

I would provide a link however it is a site on the intranet. I will provide screenshots in a seprate post.

---

### Post by jcortes on 2009-09-27
[IMG]http://jcortesweb.com/images/timeclock.jpg[/IMG]
Selections 1,3,6,8 and 9 produce blank page when the JavaScript redirects them.

as described above this issue only happens on Linux Server under IE6 not when used in any other browser or when running off of the windows server running XAMPP.

---

### Post by bb002 on 2009-09-27
Would it be possible for you to paste the HTML for the page in the screenshot and the source to the script on the webserver? Minus anything confidential, of course.

Otherwise I'm afraid I'll just be grasping at straws and I'm sure everyone else will be, too.

---

### Post by jcortes on 2009-09-27
```
Class<br />
<select  name="ClassName" onchange="document.location.href='sml_index.php?classid=' + this.value + '&id=' + document.getElementById('IdNumber').value">
  <option value="select">= Select Class =</option>
  <option selected="selected" value="3">Dictionary Build</option>
  <option  value="9">Media Lab Practice</option>
  <option  value="6">Multi-Voice Tutorial</option>
  <option  value="1">Realtime Accuracy</option>
  <option  value="2">Realtime Concepts</option>
  <option  value="5">Steno Legal</option>
  <option  value="4">Steno Medical</option>
  <option  value="7">StenoMaster Homework</option>
  <option  value="8">StenoMaster Theory</option>
</select>
Lesson Number<br />
<select name="LessonNumber">
  <option value="select">= Select Lesson =</option>
  <option value="301">Time IN/OUT</option>
</select>
```

This is the part of the script that controls refreshing and redirecting of the page based on selection. Let me know if you need any more than that, thanks for being patient.

---

### Post by bb002 on 2009-09-27
Would it be possible to see the php source? The HTML you post looks good. Since you only copy-n-pasted part of it. where is the HTML for "IdNumber"?
I see it referenced here ```
onchange="document.location.href='sml_index.php?classid=' + this.value + '&id=' + document.getElementById('IdNumber').value"
```
but the HTML for it isn't in your post.


also one of the things i do when running into wierd problems like this is and i'm trying to debug my script i do the following. It is probably silly way of doing it but on every other line i put:```
print("|".__FILE__"|".__LINE__."|<br>\n");
```
That way I know exactly what file I need to examine and what line as well. Almost always gets me exactly where i need to look for the problem. and later on you can easily remove all instances of that line as long as you text editor support expressions in the find & replace dialog
FIND:```
print("|".__FILE__"|".__LINE__."|<br>\\n");\n
```
REPLACE with blank field. :P ie: nothing, /dev/null, "", ''.


[EDIT]
oh and is IE6 the only browser you have tested your script in or is it it the only one giving you issues?

If it is the only one giving you problems try replacing ```
onchange="document.location.href='sml_index.php?classid=' + this.value + '&id=' + document.getElementById('IdNumber').value"
```
with ```
onchange="document.location.href='sml_index.php?classid=' + this.options[this.selectedIndex].value + '&id=' + document.getElementById('IdNumber').value"
``` They are techincally the same thing and it shouldn't change anything but IE is a weird beast.

[EDIT #2]
corrected some typos that stood out to me today... :P

---

### Post by jcortes on 2009-09-27
Thanks for the reply, IdNumber simply refers to the student ID number however that is giving me no issues even if I leave it out.

Here is where it gets weirder. After extensive testing I have found that only certain list items are producing the blank pages and *only when I use numbers as the option values* if I use the names of the items in the URL it works fine.

EDIT:
This only happens in IE6 unfortunately the computers that run the time clock cannot handle IE7+

---

### Post by bb002 on 2009-09-27
Ok since the problem only appears in IE6 my guess is you are running into one of the many bugs in IE6.

follow this KB article here, see if that helps any: [http://support.microsoft.com/default.aspx/kb/555027](http://support.microsoft.com/default.aspx/kb/555027)

Are you using mod_deflate on the apache server? IE6 doesn't support gzip content properly and loves to display blank pages at random because of it. "apache2 -l" should tell you modules used by apache2.

Try adding these at the start of your script. Then clear IE's cache. see if that makes a difference.
```
header('Cache-Control:private');
header('Cache-Control:no-cache');
```

Beyond this I can't help any. :/

[edit]
> only when I use numbers as the option values if I use the names of the items in the URL it works fine.
That tells me you have a issue in your php script then.

---

### Post by jcortes on 2009-09-27
I installed XAMPP on the linux server and it worked fine which leads makes me think there is just a setting in apache or php im missing. Thanks for all the help I will try your suggestions.

---

### Post by jcortes on 2009-09-27
> **bb002 said:**
> Ok since the problem only appears in IE6 my guess is you are running into one of the many bugs in IE6.

follow this KB article here, see if that helps any: [http://support.microsoft.com/default.aspx/kb/555027](http://support.microsoft.com/default.aspx/kb/555027)

Are you using mod_deflate on the apache server? IE6 doesn't support gzip content properly and loves to display blank pages at random because of it. "apache2 -l" should tell you modules used by apache2.

Try adding these at the start of your script. Then clear IE's cache. see if that makes a difference.
```
header('Cache-Control:private');
header('Cache-Control:no-cache');
```

Beyond this I can't help any. :/

[edit]

That tells me you have a issue in your php script then.

By adding that to the top of my script it FIXED IT !!!!!!! is there any way to make that permanent since the problem has been isolated? is there a setting in apache or php that I could change?

EDIT: 
I am using mod_deflate

---

### Post by jcortes on 2009-09-27
**SOLUTION: **

I found a fix thanks to your suggestion I was able to narrow it down to the **mod_deflate** module. First I edited the **/etc/apache2/mods-enabled/deflate.conf** and replaced the contents of it with the following. 

```
<IfModule mod_deflate.c>
          AddOutputFilterByType DEFLATE text/html text/plain text/xml text/css text/javascript application/x-javascript
	  BrowserMatch ^Mozilla/4 gzip-only-text/html
	  BrowserMatch ^Mozilla/4\.[0678] no-gzip
	  BrowserMatch \bMSIE\s7Â !no-gzip !gzip-only-text/html
</IfModule>

```

Restarted apache and it worked. 

This limits gzip in IE6 

Thank you for all your time and suggestions and special thanks to **bb002** thanks to your help I can sleep again :)

---

### Post by bb002 on 2009-09-27
Your welcome. I was really hoping you would say you were using mod_deflate. The only thing I had left was if you really were using that mod and that was to post this like here and to give it a shot.
[http://www.robertswarthout.com/2007/05/ie-6-apache-mod_deflate-blank-pages/](http://www.robertswarthout.com/2007/05/ie-6-apache-mod_deflate-blank-pages/)

but it seems you already found that link or a different one that gave you the same info :) Glad you got it all straightened out.

---

### Post by jcortes on 2009-09-27
yup, that's the one I used. Thanks again for leading me in the right direction.

---

